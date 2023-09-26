
# API 调用代码
```python

def call_Chinese_Alpaca_2_13B(prompt,history=[]):
    try:
        url = ''
        header = {"content-type": "application/json"}

        if history:
            messages = history+[
            {"role": "user", "content": prompt}
        ]
        else:
            messages=prompt
        data = {"messages": messages}
        response = requests.post(url, json=data, headers=header)
        # print(response.json())
        reply = response.json()['choices'][-1]['message']['content']

        return reply,history+[{"role": "user", "content": prompt}]+ [{"role": "assistant", "content": reply}]
    except:
        traceback.print_exc()
        return None,None

```

# 服务部署代码
```python
import argparse
import os
os.environ["TRANSFORMERS_CACHE"] = "./weights/"
from fastapi import FastAPI
import uvicorn

parser = argparse.ArgumentParser()
parser.add_argument('--base_model', default="ziqingyang/chinese-alpaca-2-13b", type=str)
parser.add_argument('--lora_model', default=None, type=str, help="If None, perform inference on the base model")
parser.add_argument('--tokenizer_path', default=None, type=str)
parser.add_argument('--gpus', default="0", type=str)
parser.add_argument('--load_in_8bit', action='store_true', help='Load the model in 8bit mode')
parser.add_argument('--only_cpu', action='store_true', help='Only use CPU for inference')
parser.add_argument('--alpha', type=str, default="1.0", help="The scaling factor of NTK method, can be a float or 'auto'. ")
args = parser.parse_args()

load_in_8bit = args.load_in_8bit
if args.only_cpu is True:
    args.gpus = ""
os.environ["CUDA_VISIBLE_DEVICES"] = args.gpus

import torch
import torch.nn.functional as F
from transformers import LlamaForCausalLM, LlamaTokenizer, GenerationConfig
from peft import PeftModel

import sys
parent_dir = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
sys.path.append(parent_dir)

from attn_and_long_ctx_patches import apply_attention_patch, apply_ntk_scaling_patch
apply_attention_patch(use_memory_efficient_attention=True)
apply_ntk_scaling_patch(args.alpha)

from openai_api_protocol import (
    ChatCompletionRequest,
    ChatCompletionResponse,
    ChatMessage,
    ChatCompletionResponseChoice,
)

load_type = torch.float16
if torch.cuda.is_available():
    device = torch.device(0)
else:
    device = torch.device('cpu')
if args.tokenizer_path is None:
    args.tokenizer_path = args.lora_model
    if args.lora_model is None:
        args.tokenizer_path = args.base_model

tokenizer = LlamaTokenizer.from_pretrained(args.tokenizer_path, legacy=True)
base_model = LlamaForCausalLM.from_pretrained(
    args.base_model,
    load_in_8bit=load_in_8bit,
    torch_dtype=load_type,
    low_cpu_mem_usage=True,
    device_map='auto' if not args.only_cpu else None,
    )

model_vocab_size = base_model.get_input_embeddings().weight.size(0)
tokenzier_vocab_size = len(tokenizer)
print(f"Vocab of the base model: {model_vocab_size}")
print(f"Vocab of the tokenizer: {tokenzier_vocab_size}")
if model_vocab_size != tokenzier_vocab_size:
    print("Resize model embeddings to fit tokenizer")
    base_model.resize_token_embeddings(tokenzier_vocab_size)
if args.lora_model is not None:
    print("loading peft model")
    model = PeftModel.from_pretrained(base_model, args.lora_model,torch_dtype=load_type,device_map='auto',)
else:
    model = base_model

if device==torch.device('cpu'):
    model.float()

model.eval()

DEFAULT_SYSTEM_PROMPT = """你是一个乐于助人的助手。"""

TEMPLATE_WITH_SYSTEM_PROMPT = (
    "[INST] <<SYS>>\n"
    "{system_prompt}\n"
    "<</SYS>>\n\n"
    "{instruction} [/INST]"
)

TEMPLATE_WITHOUT_SYSTEM_PROMPT = "[INST] {instruction} [/INST]"

def generate_prompt(instruction, response="", with_system_prompt=True, system_prompt=None):
    if with_system_prompt is True:
        if system_prompt is None:
            system_prompt = DEFAULT_SYSTEM_PROMPT
        prompt = TEMPLATE_WITH_SYSTEM_PROMPT.format_map({'instruction': instruction,'system_prompt': system_prompt})
    else:
        prompt = TEMPLATE_WITHOUT_SYSTEM_PROMPT.format_map({'instruction': instruction})
    if len(response)>0:
        prompt += " " + response
    return prompt

def generate_completion_prompt(instruction: str):
    """Generate prompt for completion"""
    return generate_prompt(instruction, response="", with_system_prompt=True)


def generate_chat_prompt(messages: list):
    """Generate prompt for chat completion"""

    system_msg = None
    for msg in messages:
        if msg.role == 'system':
            system_msg = msg.content
    prompt = ""
    is_first_user_content = True
    for msg in messages:
        if msg.role == 'system':
            continue
        if msg.role == 'user':
            if is_first_user_content is True:
                prompt += generate_prompt(msg.content, with_system_prompt=True, system_prompt=system_msg)
                is_first_user_content = False
            else:
                prompt += '<s>'+generate_prompt(msg.content, with_system_prompt=False)
        if msg.role == 'assistant':
                prompt += f" {msg.content}"+"</s>"
    return prompt

def predict(
    input,
    max_new_tokens=2048,
    top_p=0.75,
    temperature=0.1,
    top_k=40,
    num_beams=4,
    repetition_penalty=1.0,
    do_sample=True,
    **kwargs,
):
    """
    Main inference method
    type(input) == str -> /v1/completions
    type(input) == list -> /v1/chat/completions
    """
    if isinstance(input, str):
        prompt = generate_completion_prompt(input)
    else:
        prompt = generate_chat_prompt(input)
    inputs = tokenizer(prompt, return_tensors="pt")
    input_ids = inputs["input_ids"].to(device)
    generation_config = GenerationConfig(
        temperature=temperature,
        top_p=top_p,
        top_k=top_k,
        num_beams=num_beams,
        do_sample=do_sample,
        **kwargs,
    )
    generation_config.return_dict_in_generate = True
    generation_config.output_scores = False
    generation_config.max_new_tokens = 2048
    generation_config.repetition_penalty=float(repetition_penalty)
    with torch.no_grad():
        generation_output = model.generate(
            input_ids=input_ids,
            generation_config=generation_config,
        )
    s = generation_output.sequences[0]
    output = tokenizer.decode(s, skip_special_tokens=True)
    output = output.split("[/INST]")[-1].strip()
    return output

app = FastAPI()

@app.post("/api/api_server_03")
async def create_chat_completion(request: ChatCompletionRequest):
    """Creates a completion for the chat message"""
    msgs = request.messages
    if isinstance(msgs, str):
        msgs = [ChatMessage(role='user', content=msgs)]
    else:
        msgs = [ChatMessage(role=x['role'], content=x['content']) for x in msgs]
    output = predict(
        input=msgs,
        max_new_tokens=request.max_tokens,
        top_p=request.top_p,
        top_k=request.top_k,
        temperature=request.temperature,
        num_beams=request.num_beams,
        repetition_penalty=request.repetition_penalty,
        do_sample=request.do_sample,
    )
    choices = [ChatCompletionResponseChoice(index = i, message = msg) for i, msg in enumerate(msgs)]
    choices += [ChatCompletionResponseChoice(index = len(choices), message = ChatMessage(role='assistant',content=output))]
    return ChatCompletionResponse(choices = choices)


if __name__ == "__main__":
    log_config = uvicorn.config.LOGGING_CONFIG
    log_config["formatters"]["access"]["fmt"] = "%(asctime)s - %(levelname)s - %(message)s"
    log_config["formatters"]["default"]["fmt"] = "%(asctime)s - %(levelname)s - %(message)s"
    uvicorn.run(app, host='0.0.0.0', port=9103, workers=1, log_config=log_config)

```


# 参考
https://huggingface.co/ziqingyang/chinese-alpaca-2-13b