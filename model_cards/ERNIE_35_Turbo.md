
# API 调用代码
```python
@register_model('ERNIE_35_Turbo')
def call_ernie_35(prompt, history=[]):

    url = "https://aip.baidubce.com/rpc/2.0/ai_custom/v1/wenxinworkshop/chat/eb-instant?access_token=" + ""

    messages =history+ [{"role": "user", "content": prompt}]
    payload = json.dumps({"messages": messages})
    headers = {
        'Content-Type': 'application/json'
    }
    response = requests.request("POST", url, headers=headers, data=payload)
    print(response.json())
    reply = response.json()["result"]
    history += [{"role": "assistant", "content": reply}]
    return reply, history
```

# 服务部署代码
```python
```