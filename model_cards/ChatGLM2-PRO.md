
# API 调用代码
```python
def call_ChatGLM_130B(prompt, history=[]):
    zhipuai.api_key = ''

    # Make prompt
    history.append({"role": "user", "content": prompt})
    response = zhipuai.model_api.invoke(
        # model="chatglm_130b",
        model="chatglm_pro",
        prompt=history,
    )
    # print(response)
    if response['code']==1301:
        reply=response['msg']
    else:
        reply = response['data']['choices'][0]['content']
    history.append({"role": "assistant", "content": reply})

```

# 服务部署代码
```python
```

# 参考
https://open.bigmodel.cn/dev/api#chatglm_pro