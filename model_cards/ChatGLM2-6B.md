
# API 调用代码
```python
def call_ChatGLM2_6B(prompt, history=[]):
    url = ""
    headers = {'Content-Type': 'application/json'}

    _h=[]
    if history:
        for i in range(0,len(history),2):
            _h.append(
                [history[i]['content'],history[i+1]['content']]
            )
    # print(_h)
    data = {"prompt": prompt, "history": _h}
    response = requests.post(url, json=data, headers=headers)

```

# 服务部署代码
```python
import torch
from fastapi import FastAPI, Request
from transformers import AutoTokenizer, AutoModel
import uvicorn, json, datetime



device='cuda'
def torch_gc():
    if torch.cuda.is_available():
        with torch.cuda.device(device):
            torch.cuda.empty_cache()
            torch.cuda.ipc_collect()


app = FastAPI()


@app.post("/api/chatglm2_6b")
async def create_item(request: Request):
    global model, tokenizer
    json_post_raw = await request.json()
    json_post = json.dumps(json_post_raw)
    json_post_list = json.loads(json_post)
    prompt = json_post_list.get('prompt')
    history = json_post_list.get('history')
    max_length = json_post_list.get('max_length')
    top_p = json_post_list.get('top_p')
    temperature = json_post_list.get('temperature')
    response, history = model.chat(tokenizer,
                                   prompt,
                                   history=history,
                                   max_length= 2048,
                                   top_p=top_p if top_p else 0.7,
                                   temperature=temperature if temperature else 0.95)
    now = datetime.datetime.now()
    time = now.strftime("%Y-%m-%d %H:%M:%S")
    answer = {
        "response": response,
        "history": history,
        "status": 200,
        "time": time
    }
    log = "[" + time + "] " + '", prompt:"' + prompt + '", response:"' + repr(response) + '"'
    print(log)
    torch_gc()
    return answer


if __name__ == '__main__':
    tokenizer = AutoTokenizer.from_pretrained("../pretrained/ChatGLM2-6B/chatglm2-6b", trust_remote_code=True)
    model = AutoModel.from_pretrained("../pretrained/ChatGLM2-6B/chatglm2-6b", trust_remote_code=True).cuda()
    model.eval()
    uvicorn.run(app, host='0.0.0.0', port=9605, workers=1)
```