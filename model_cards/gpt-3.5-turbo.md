
# API 调用代码
```python

def call_GPT_3point5_turbo(prompt,history=[]):
    
    while not api_key:
        api_key = get_avaliable_api_key()
        print('等待apikey.....')
    openai.api_key = api_key
    messages = [
        {"role": "system", "content": "You are a helpful assistant."},
    ] +history +[{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        # model="gpt-3.5-turbo-16k",
        messages=messages
        )
    response_text=response.choices[0].message["content"]

```

# 服务部署代码
```python
```

# 参考
openai