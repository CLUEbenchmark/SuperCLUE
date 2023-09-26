
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
# 参考
https://console.bce.baidu.com/tools/#/api?product=AI&project=%E5%8D%83%E5%B8%86%E5%A4%A7%E6%A8%A1%E5%9E%8B%E5%B9%B3%E5%8F%B0&parent=%E9%89%B4%E6%9D%83%E8%AE%A4%E8%AF%81%E6%9C%BA%E5%88%B6&api=oauth/2.0/token&method=post