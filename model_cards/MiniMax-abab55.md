
# API 调用代码
```python
@register_model('MiniMax_Abab55')
def call_MiniMax_abab55(prompt, history=[]):
    url = 'https://api.minimax.chat/v1/text/chatcompletionXXXXXXX'
    headers = {
        "Authorization": "Bearer ",
        "Content-Type": "application/json"
    }
    request_body = {
        "model": "abab5.5-chat",
        "tokens_to_generate": 2048,
        'messages': []
    }

    for i in range(0,len(history),2):
        old_prompt = history[i]['content']
        old_reply = history[i+1]['content']


        request_body['messages'].append({"sender_type": "USER", "text": old_prompt})
        request_body['messages'].append({"sender_type": "BOT", "text": old_reply})
    

    request_body['messages'].append({"sender_type": "USER", "text": prompt})
    response = requests.post(url, headers=headers, json=request_body)
    #print(response.json())
    if response.json().get('base_resp',{}).get('status_code',0)==1027:
        reply='由于问题或答案违反相关政策规定或道德伦理，拒绝回答本次问题'
    else:
        reply = response.json()['reply']
    history=history+[{"role": "user","content":prompt}]+[{"role": "assistant","content":reply}]
```

# 服务部署代码
```python
```