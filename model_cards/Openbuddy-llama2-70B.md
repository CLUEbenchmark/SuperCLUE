
# API 调用代码
```python
def call_openbuddy_llama2_70b(prompt,history=[]):

    url=''
    headers={
    'content-type':'application/json',
    'authorization':""
    }
    messages = history + [{"role":"user", "content": prompt}]
    data = {"messages": messages,
            "model": "llama2-70b-latest",
            "stream": False, 
            "temperature": 0.01}
    response = requests.post(url=url,data=json.dumps(data),headers=headers,timeout=600)
    print(response.json())
    reply = response.json()["choices"][-1]['message']['content']
    history = messages + [{"role": "assistant", "content": reply}]
    return reply, history
    
```

# 服务部署代码
```python
```