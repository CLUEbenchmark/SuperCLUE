
# API 调用代码
```python
def call_qwen_7b_chat(prompt, history=[]):
    url = ''
    header = {"content-type": "application/json"}

    _h=[]
    if history:
        for i in range(0,len(history),2):
            _h.append(
                [history[i]['content'],history[i+1]['content']])
    # print(_h)
    data = {"prompt": prompt, 'history': _h}
    response = requests.post(url, json=data, headers=header)
    reply = response.json()['response']
    history = response.json()['history']

```

# 服务部署代码
```python

import os 
os.environ['TRANSFORMERS_CACHE'] = './weight/'
from fastapi import FastAPI, Request
import uvicorn
import torch
from transformers import AutoModelForCausalLM, AutoTokenizer
from transformers.generation import GenerationConfig

app = FastAPI()

@app.post('/api/qwen_7b')
async def chat_completion(request: Request):
    data = await request.json()
    prompt = data['prompt']
    print(prompt)
    history = data['history']
    if len(history) == 0:
        print('First time to chat...')
        history = None
    response, history = model.chat(tokenizer, prompt, history=history)
    return {'response': response, 'history': history}


if __name__ == '__main__':
    tokenizer = AutoTokenizer.from_pretrained("Qwen/Qwen-7B-Chat", trust_remote_code=True)
    ## 打开bf16精度，A100、H100、RTX3060、RTX3070等显卡建议启用以节省显存
    # model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-7B-Chat", device_map="auto", trust_remote_code=True, bf16=True).eval()
    ## 打开fp16精度，V100、P100、T4等显卡建议启用以节省显存
    # model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-7B-Chat", device_map="auto", trust_remote_code=True, fp16=True).eval()
    # 默认使用fp32精度
    model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-7B-Chat", device_map="auto", trust_remote_code=True).eval()
    model.generation_config = GenerationConfig.from_pretrained("Qwen/Qwen-7B-Chat", trust_remote_code=True) # 可指定不同的生成长度、top_p等相关超参
    print(model.generation_config)
    # print(f'temperature: {model.generation_config.temperature}')
    # print(f'max_length: {model.generation_config.max_length}')
    # print(f'max_new_tokens: {model.generation_config.max_new_tokens}')
    uvicorn.run(app, host='0.0.0.0', port=9602)

  
```

# 参考
https://huggingface.co/Qwen/Qwen-7B-Chat