
# API 调用代码
```python

def call_gpt_4(prompt,history=[]):
    while not api_key:
        api_key = get_avaliable_api_key()
        print('等待apikey.....')
    openai.api_key = api_key
    messages = [
        {"role": "system", "content": "You are a helpful assistant."},
    ] +history +[{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=messages
        )
    response_text=response.choices[0].message["content"]
```
# 服务部署代码
```python
```

# 参考
openai