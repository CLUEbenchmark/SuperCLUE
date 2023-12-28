# SuperCLUE

中文通用大模型综合性基准SuperCLUE

<a href='https://www.superclueai.com' target="__blank">SuperCLUE中文大模型测评基准12月榜单发布</a>

官网地址：<a href='https://www.cluebenchmarks.com/superclue.html' target="__blank">www.cluebenchmarks.com/superclue.html</a>

技术报告：<a href='https://arxiv.org/abs/2307.15020' target="__blank">SuperCLUE: A Comprehensive Chinese Large Language Model Benchmark</a>

【2023-12-27】 <a href='https://mp.weixin.qq.com/s/PycSpCCREBgB0tEy3csPKQ'>《中文大模型基准测评报告2023年度报告》发布</a>

【2023-12-28】 发布SuperCLUE-2023年12月榜单


【2023-10-19】 <a href='https://www.cluebenchmarks.com/superclue_agent.html' target="__blank">SuperCLUE-Agent：Agent智能体中文原生任务评估基准</a>


【2023-9-12】 <a href='https://github.com/CLUEbenchmark/SuperCLUE-safety' target="__blank">SuperCLUE-Safety：中文大模型多轮对抗安全基准</a>


【2023-9-26】，SuperCLUE发布中文大模型9月榜单。

SuperCLUE是一个综合性大模型评测基准，本次评测主要聚焦于大模型的四个能力象限，包括语言理解与生成、专业技能与知识、Agent智能体和安全性，进而细化为12项基础能力。

相比与上月，新增了AI Agent智能体

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/superclue_idea2.png"  width="90%" height="90%"></img>

### SuperCLUE能力评估结构图
<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/category09.png"  width="60%" height="60%"></img>

### SuperCLUE多维度测评方案
<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/superclue_mlitisystem.png"  width="90%" height="90%"></img>


### 为什么新增AI Agent智能体能力？

AI agent（智能体）是当前与大语言模型相关的前沿研究热点，拥有类似贾维斯等科幻电影中人类超级助手的能力，可以根据需求自主的完成任务。
然而，面向AI agent智能体，缺乏针对中文大模型的广泛评估。为了解决这一问题，我们在SuperCLUE新的榜单中新增了AI agent智能体能力的测评。
这个榜单将重点评估AI agent在【工具使用】和【任务规划】两个关键能力上的表现，这项工作旨在为评估中文大模型作为智能体的表现提供一个基础和可能。

### SuperCLUE总排行榜（2023年12月）

| 排名 | 模型 | 机构 | 总分 | OPEN<br/>多轮开放问题 | OPT<br/>三大能力客观题 | 使用 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|  
| -|GPT4-Turbo | OpenAI | 90.63 | 90.89 | 90.03 | API |
| -|GPT4(网页) | OpenAI | 83.92 | 80.76 | 91.28 | 网页 |
| -|GPT4(API) | OpenAI | 79.84 | 76.24 | 88.24 | API |
| 🏅️ | 文心一言4.0(API) | 百度 | 79.02 | 75.00 | 88.38 | API |
| 🥈 | 通义千问2.0 | 阿里巴巴 | 76.54 | 71.78 | 87.64 | API |  
| 🥉 | AndesGPT | OPPO | 75.04 | 70.01 | 86.76 | API |
| 4 | 智谱清言 | 清华&智谱 | 74.11 | 69.91 | 83.92 | 网页 |
| 5 | Moonshot(KimiChat) | 月之暗面 | 71.92 | 67.25 | 82.81 | 网页 |
| - | 文心一言4.0(网页) | 百度 | 70.28 | 62.59 | 88.22 | 网页 |
| 6 | Qwen-72B-Chat | 阿里巴巴 | 69.69 | 62.31 | 86.90 | API |  
| 7 | 序列猴子 | 出门问问 | 68.98 | 61.01 | 87.59 | API |
| 8 | Yi-34B-Chat | 零一万物 | 68.46 | 61.99 | 83.56 | 模型 |
| 9 | PCI-TransGPT | 佳都科技 | 68.33 | 60.41 | 86.81 | API |
| 9 | 360GPT_Pro | 360 | 68.32 | 61.36 | 84.56 | API |
| - | Claude2 | Anthropic | 67.43 | 65.14 | 72.77 | API |
| 11 | 云雀大模型(豆包) | 字节跳动 | 66.35 | 58.53 | 84.60 | 网页 | 
| - | Gemini-pro | Google | 65.29 | 59.33 | 79.20 | API |
| - | GPT3.5-Turbo | OpenAI | 61.44 | 55.63 | 74.98 | API |
| 12 | Qwen-14B-Chat | 阿里巴巴 | 61.27 | 52.04 | 82.81 | API |
| 13 | Baichuan2-13B-Chat | 百川智能 | 61.12 | 54.45 | 76.67 | 模型 |
| 14 | XVERSE-13B-2-Chat | 元象科技 | 60.46 | 53.00 | 77.87 | 模型 |
| 15 | 讯飞星火V3.0 | 科大讯飞 | 59.33 | 51.74 | 77.03 | API |
| 16 | Minimax(应事) | 稀宇科技 | 58.91 | 50.00 | 79.69 | 网页 |
| 17 | ChatGLM3-6B | 清华&智谱 | 49.50 | 42.30 | 66.31 | 模型 |
| 18 | Chinese-Alpaca-2-13B | yiming cui | 45.36 | 38.91 | 60.40 | 模型 |
| - | Llama_2_13B_Chat | Meta | 37.36 | 34.91 | 43.09 | 模型 |

注：处于前列的模型，如果分数比较接近（小于0.03分），在排名时会被记为并列的名称。

### SuperCLUE-OPEN多轮开放问题排行榜（2023年12月）

### SuperCLUE-OPT三大能力客观题排行榜（2023年12月）


### SuperCLUE十大基础能力排行榜（2023年12月）


### SuperCLUE开源模型排行榜（2023年12月）


### 23-11月测评改进

    1. 本次测评中SuperCLUE-Open的超级模型（裁判模型）由10月的GPT4升级为能力更强的GPT4-Turbo，进一步提升开放主观题评估的精确性。
    
    2. 本次SuperCLUE-Open测评集总量由10月的3754道题扩展至4265道题。
    
    3. 与10月相比，本次测评新增了腾讯的混元、阿里云的通义千问2.0(v1030)、零一万物的Yi-34B-Chat、清华&智谱AI的ChatGLM3-Turbo和ChatGLM3-6B、
    元象科技的XVERSE-13B-2-Chat。

### 示例
#### 能力1：语义理解与抽取

这是一种语言能力，能够理解并解析输入的文字信息的含义。模型需要能够识别短语、句子、段落的含义，同时还要能从更大的文本块中抽取关键信息和主题。

##### 多轮对话示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_nlp.png"  width="100%" height="100%"></img>

注：本示例中可同时评测多轮对话能力

#### 能力2：AI agent（智能体）能力

AI agent（智能体）是当前与大语言模型相关的前沿研究热点，拥有类似贾维斯等科幻电影中人类超级助手的能力，可以根据需求自主的完成任务。

重点评估AI agent在【工具使用】和【任务规划】两个关键能力上的表现

##### 示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_agent.png"  width="100%" height="100%"></img>


#### 能力3：上下文对话

这是一种语言能力，需要理解并记住前面的对话信息，以便在回答中保持连贯性。这涉及到理解对话的整体流程和上下文环境，或生成相应的对话。

##### 示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_dial.png"  width="100%" height="100%"></img>

#### 能力4：生成与创作

这是一种语言能力，能够创造新的文本内容，如文章、文案、短故事、诗歌。这涉及到创造性地运用语言，同时还要考虑到风格、语境和目标读者。

##### 示例
<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_generate.png"  width="100%" height="100%"></img>


#### 能力5：知识与百科

这是一种知识能力，能够像百科全书一样提供知识信息。这涉及到理解和回答关于广泛主题的问题，以及提供准确、详细和最新的信息。

##### 示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_knowledge.png"  width="100%" height="100%"></img>


#### 能力6：代码

这是一种专业能力，能够理解和生成编程代码。这涉及到理解多种编程语言的语法、结构和习惯，以及如何解决编程问题。

##### 多轮对话示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_code.png"  width="100%" height="100%"></img>

注：本示例中可同时评测多轮对话能力

#### 能力7：逻辑与推理

这是一种专业能力，能够理解和应用逻辑原则进行推理。这涉及到分析问题、识别问题及推理。

##### 示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_logic.png"  width="100%" height="100%"></img>


####  能力8：计算

这是一种专业能力，使其能够执行数学运算，如加法、减法、乘法和除法，甚至更复杂的数学问题。这涉及到理解数学问题的表述，以及如何步骤地解决这些问题。

##### 多轮对话示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_compute.png"  width="100%" height="100%"></img>

注：本示例中可同时评测多轮对话能力

####  能力9：角色扮演

这是一种感知能力，使其能够在特定的模拟环境或情景中扮演一个角色。这涉及到理解特定角色的行为、说话风格，以及在特定情境下的适当反应。

##### 示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_roleplay.png"  width="100%" height="100%"></img>


####   能力10：安全

这是一种安全能力，防止生成可能引起困扰或伤害的内容。这涉及到识别和避免可能包含敏感或不适当内容的请求，以及遵守用户的隐私和安全政策。

##### 示例

<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/r2309/image_safety.png"  width="100%" height="100%"></img>

### 8月榜单更新情况
1.综合性：将OPEN多轮开放问题与OPT三大能力客观题进行了结合起来，作为8月榜单；

2.模型细节：Baichuan-13B-Chat使用了是最新的模型权重，具体见huggingface的权重；文心一言，OPT三大能力客观题使用的是API（Ernie-3.5-turbo）；
  360使用的是api版本；

3.模型更新：去除了一些前期大家比较关注但当前活跃度不高的模型，如MOSS，BELLE等；加入了一些如Qwen-7B-Chat和3个Llam2相关模型。
