
# API 调用代码
```python
def call_baichuan2_7B(prompt, history=[]):
    """baichuan_7B_chat_v2"""
    url = ""
    header = {"content-type": "application/json"}
    data = {"prompt": prompt, "history": history}

    response = requests.post(url, json=data, headers=header)
    reply = response.json()['response']
    history.append({'role': 'user', 'content': prompt})
    history.append({'role': 'assistant', 'content': reply})
```

# 服务部署代码
```python

import torch
from transformers import AutoModelForCausalLM, AutoTokenizer
from transformers.generation.utils import GenerationConfig

ckpt = "/cos_data/hf/Baichuan2-7B-Chat"
tokenizer = AutoTokenizer.from_pretrained(ckpt, use_fast=False, trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained(ckpt, device_map="auto", torch_dtype=torch.float16, trust_remote_code=True)
model.generation_config = GenerationConfig.from_pretrained(ckpt)


import torch
from transformers import AutoModelForCausalLM, AutoTokenizer
from transformers.generation.utils import GenerationConfig
from fastapi import FastAPI, Request
import uvicorn
app = FastAPI()


messages = []
messages.append({"role": "user", "content": "从现在开始你每次回答前面都要加“喵～”"})
messages.append({"role": "assistant", "content": "喵～好的。"})
messages.append({"role": "user", "content": "1+1=?"})
response = model.chat(tokenizer, messages)
print(response)

@app.post("/api/baichuan2_7b")
async def create_item(request: Request):
    data = await request.json()
    prompt = data['prompt']
    messages = data['history']

    messages.append({"role": "user", "content": f"{prompt}"})
    response = model.chat(tokenizer, messages)
    return {'response': response}


if __name__ == '__main__':
    uvicorn.run(app, host='0.0.0.0', port=6004, workers=1)

```

# 参考
https://huggingface.co/baichuan-inc/Baichuan2-7B-Chat