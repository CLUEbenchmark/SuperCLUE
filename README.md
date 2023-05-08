# SuperCLUE
全球首个中文通用大模型综合性基准SuperCLUE

SuperCLUE: A Benchmark for Foundation Models in Chinese


<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/superclue.jpeg"  width="72%" height="72%"></img>

SuperCLUE基准计划按照月度进行更新，纳入更多可用中文大模型，欢迎联系与交流；数据集和进一步信息计划在下一次更新时公开，敬请期待。

## SuperCLUE是什么
中文通用大模型基准（SuperCLUE），是针对中文可用的通用大模型的一个测评基准。

它主要要回答的问题是：在当前通用大模型大力发展的情况下，中文大模型的效果情况。包括但不限于：这些模型不同任务的效果情况、相较于国际上的代表性模型做到了什么程度、
这些模型与人类的效果对比如何？

它尝试在一系列国内外代表性的模型上使用多个维度能力进行测试。SuperCLUE是中文语言理解测评基准（CLUE）基准是在通用人工智能时代的进一步发展。


## SuperCLUE的构成与特点
着眼于综合评价大模型的能力，使其能全面的测试大模型的效果，又能考察模型在中文上特有任务的理解和积累，我们对能力进行了划分。
SuperCLUE从三个不同的维度评价模型的能力：基础能力、专业能力和中文特性能力。
<img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/score.jpg"  width="85%" height="85%"></img>

#### 基础能力:

包括了常见的有代表性的模型能力，如语义理解、对话、逻辑推理、角色扮演、代码、生成与创作等10项能力。

#### 专业能力:

包括了中学、大学与专业考试，涵盖了从数学、物理、地理到社会科学等50多项能力。

#### 中文特性能力:

针对有中文特点的任务，包括了中文成语、诗歌、文学、字形等10项多种能力。


#### SuperCLUE的特点：
1）多个维度能力考察（3大类70+子能力）：从三个不同角度对中文大模型进行测试，以考察模型的综合能力；并且每一个子能力又含有十项或以上不同的细分能力。

2）自动化测评（一键测评）：通过自动化测评方式以相对客观形式测试不同模型的效果，可以一键对大模型进行测评。

3）广泛的代表性模型（9个模型）：选取了多个国内外有代表性的可用的模型进行测评，以反映国内大模型的发展现状并了解与国际领先模型的差距或相对优劣势。

4）人类基准：在通用人工智能发展的情况下，也提供了模型相对于人类效果的指标对比。


## SuperCLUE的数据集
1.基础能力（10项能力）：语义理解、生成与创作、闲聊、对话、百科与知识、逻辑与推理、计算能力、代码、角色模拟、对话安全
    
    示例：
    语义理解：
        她说话不算数，经常食言。她的说话不算数是什么意思？
         A. 她讲的话很含糊不清。
         B. 她说话不信守承诺
         C. 她说话很有说服力。
         D. 她的话很有条理。
         
    逻辑与推理：
        小明有一个兄弟，但是没有姐姐。以下哪个推论是正确的？
         A. 小明的兄弟有一个哥哥
         B. 小明的兄弟有一个弟弟
         C. 小明是独生子
         D. 无法确定小明的兄弟是哥哥还是弟弟
 
     

2.中文特性能力（10项能力）：成语、诗词、文学、字义理解、汉语句法分析、汉字字形和拼音理解、歇后语和谚语、对联、方言、古文
    
    示例：
    成语：
    选出下列句子中成语使用正确的一项
     A. 在北方剧场，蒙古国艺术团来哈演出，热情的观众袖手旁观。
     B. 他想得很多，办事非常周全，真是匠心独运。
     C. 他们同学三年，关系一直很好，两人相敬如宾，互相尊重。
     D. 人生的航船不会一帆风顺，我们要正视困难，敢与风浪搏击，就一定会达到胜利的彼岸。
     
    文学：
    下列有关名著的表述有误的一项是
     A. 《水浒传》给我们留下许多脍炙人口的故事，例如拳打镇关西、智取生辰纲、三打祝家庄、三调芭蕉扇等。
     B. 《西游记》中，孙悟空面对妖怪有时也会遇到麻烦。例如青牛怪有一个白森森的"金刚琢"，能把金箍棒一股脑儿套去，让孙悟空不得不另行设法。
     C.  鲁迅先生称《世说新语》为“一部名士底（的）教科书”。其中的“谢女咏雪”、“子猷访戴”等故事，成为后世诗文常用典故。
     D. 《朝花夕拾》中，鲁迅回忆那个具有人情味的鬼----无常时，时不时加进几句对现实所谓正人君子的讽刺，虚幻的无常给予当时鲁迅寂寞悲凉的心些许的安慰。
         
     
3.专业能力（50+能力）：抽象代数、天文学、临床知识、大学生物学、大学计算机科学、大学数学、高中化学、高中物理、机器学习、营养、专业会计、职业心理学等
    
    示例：
    物理：
    一个质量为2千克的物体受到三个外力的作用，每个外力的大小都是4牛。下列哪一个不可能是物体的加速度?
     A. 0米/秒^2
     B. 2米/秒^2
     C. 4米/秒^2
     D. 8米/秒^2
     
    天文学：
    什么定义了恒星周围的宜居带？
     A. 恒星周围的区域，在行星表面上液态水可能存在的区域。
     B. 恒星周围的区域，人类可以生存的区域。
     C. 恒星周围的区域，紫外线辐射不会破坏行星表面上的生物体。
     D. 恒星周围的区域，生命存在的区域。
    
## SuperCLUE全自动测评过程：
    1、统一prompt：针对每一个题目，构造了统一的prompt供模型和人类使用；
    2、预测：系统使用模型进行预测，要求模型选取ABCD中一个唯一的选项；
    3、打分：如果模型的回答不是标准的答案，而是一段文字，系统会采取特定的策略自动提取出模型的答案。该策略结合模型的表现进行优化和完善。
       （注：当无法提取有效答案的时候，则表明模型没有按照人类做题的要求，未正确理解指令，则认为模型回答错误。）
       
   由于此次为SuperCLUE首次全自动测评，为了谨慎起见，全部答案事后已由多位人类进行交叉复核，与自动测评结果基本一致。

## 人类基准测评
针对所有主任务和子任务题目，都会有三位独立的人类测评员根据题目做答。人类测评结果，采用多数投票方式进行汇总，作为人类基准分数。

## 实验分析

#### 人类与模型的对比

从人类测评角度看，基础能力（98%）+中文特性（95%），都达到了非常高的水平。除GPT-4外，大幅超过了其他的大模型（如在基础能力上超过其他模型20多个点）。
 AI虽然进展很快，但人类还是有相对优势的。 比如，在计算方面，人类超过最强的模型GPT-4达到30个点

   
#### 模型层面，宏观分析：

一句话点评：国际先进模型效果具有较大的领先性；同时国产GPT模型也有不俗的表现，有差距但可追赶

1）中文大模型的必要性

 在国际上效果非常棒的Vicuna-13B模型，在中文领域效果是众多模型中比较一般的模型（排名靠后）。而国内的研发的大模型或在中文任务上进行训练后的模型，都大幅超过了Vicuna-13B的效果。比如，星火认知大模型在总分上超过了Vicuna-13B 20个点。BELLE-13B，基于国际基础模型并在中文上训练和微调过的模型总分也超过了Vicuna-13B 10多个点。
    
2）国内大模型与OpenAI GPT之间的差距较大，但在逐渐逼近

 可以看到在本次SuperCLUE上效果国内最好的模型（星火认知大模型），比GPT-4有23个点的差距，与ChatGPT-3.5总分上也有13个点的差距。但是我们更应该看到，
 不断涌现和迭代的国内大模型也在逐步的缩小与OpenAI GPT模型模型的差距。
 
3）ChatGPT与GPT-4之间也有明显差距

   比如，GPT-4在所有的参与测评的模型中是独一档的存在，超过了ChatGPT3.5近10个点。它的逻辑推理能力、生成与创作能力方面，远远优于其他模型（超过其他模型20个点或以上）。
   

#### 能力角度分析

1） 当前模型在基础能力普遍表现不错，但中文、专业能力还比较差。

   说明当前国内大模型已经有不错的基础（60-70%），但要适应专业领域、中文任务表现一般（如30-60%直接）。说明在专业领域或中文任务上还需要继续努力，或者说进行针对性的训练。
   
2）当前模型通常在逻辑推理、计算方面能力较差。

  除GPT-4外，其他模型多数在这两项能力通常在仅在30-50分之间。

3）角色模拟，AI模型比较擅长。
  这方面可以是非常有用的。被可以让AI根据场景和角色设定帮忙人类来完成多种不同的任务，从市场营销策划，心理咨询，客户服务，到提供创意或想法等。

#### 国内大模型点评

本次测评中，国内大模型中近期发布的星火模型最好，MinMax模型也有不错表现。它们都在具有工作和生成中具有应用价值的基础能力方面获得了较好的成绩。


## SuperCLUE的测试结果
四个表格：汇总表、基础能力表、专业能力表、中文特性表

#####  排行榜会定期更新           数据来源: www.CLUEbenchmarks.com              

#### 总榜单(v1.0版)

| 模型         | 总分   | 基础能力+中文特性 | 基础能力 | 学术与专业能力 | 中文特性 |
|--------------|-------|--------------|--------|------------|-------|
| 人类         | -     | **96.50%**       | **98.00%**  | -          | **95.00%** |
| GPT-4        | 76.77%| 79.00%       | 90.00%  | **72.32%**     | 68.00% |
| ChatGPT      | 66.21%| 72.00%       | 85.00%  | 54.64%     | 59.00% |
| 星火          | 53.42%| 59.00%       | 74.00%  | 42.27%     | 44.00% |
| MiniMax      | 46.35%| 50.50%       | 72.00%  | 38.04%     | 29.00% |
| BELLE-13B    | 43.70%| 46.00%       | 69.00%  | 39.11%     | 23.00% |
| ChatGLM-6B   | 42.13%| 46.50%       | 60.00%  | 33.39%     | 33.00% |
| MOSS-16B     | 36.51%| 39.50%       | 52.00%  | 30.54%     | 27.00% |
| Vicuna-13B   | 34.49%| 37.50%       | 45.00%  | 28.46%     | 30.00% |
| 文心一言     | 32.44%| 32.00%       | 40.00%  | 33.33%     | 24.00% |


#### 基础能力表(v1.0版)

| 基础能力     | 人类 | ChatGLM-6B | MOSS-16B | Vicuna-13B | GPT-3.5 | GPT-4 | BELLE-13B | 星火 | 文心一言 | MiniMax |
|-------------|------|------------|----------|------------|---------|-------|-----------|------|---------|---------|
| Accuracy    | Accuracy| Accuracy  | Accuracy | Accuracy   | Accuracy|Accuracy| Accuracy  |Accuracy| Accuracy|Accuracy |
| 代码         | 0.90 | 0.40       | 0.70      | 0.60        | 0.90     | 0.90  | 0.80       | 0.50  | 0.40     | 0.60    |
| 安全         | 1.00 | 0.30       | 0.50      | 0.60        | 0.90     | 0.80  | 0.70       | 0.80  | 0.30     | 0.80    |
| 对话         | 1.00 | 0.70       | 0.50      | 0.30        | 0.90     | 1.00  | 0.80       | 0.90  | 0.20     | 0.90    |
| 生成与创作    | 0.90 | 0.50       | 0.40      | 0.30        | 1.00     | 0.80  | 0.40       | 0.50  | 0.20     | 0.50    |
| 百科与知识   | 1.00 | 0.50       | 0.50      | 0.30        | 0.90     | 1.00  | 0.70       | 0.90  | 0.70     | 1.00    |
| 角色模拟     | 1.00 | 1.00       | 0.70      | 0.70        | 1.00     | 1.00  | 0.80       | 1.00  | 0.50     | 0.80    |
| 计算能力     | 1.00 | 0.50       | 0.30      | 0.40        | 0.60     | 0.70  | 0.40       | 0.60  | 0.20     | 0.60    |
| 语义理解     | 1.00 | 0.90       | 0.50      | 0.40        | 1.00     | 0.90  | 0.80       | 1.00  | 0.30     | 0.70    |
| 逻辑与推理    | 1.00 | 0.40       | 0.10      | 0.40        | 0.30     | 0.90  | 0.50       | 0.30  | 0.30     | 0.40    |
| 闲聊         | 1.00 | 0.80       | 1.00      | 0.50        | 1.00     | 1.00  | 1.00       | 0.90  | 0.90     | 0.90    |
| 总分         | 0.98 | 0.60       | 0.52      | 0.45        | 0.85     | 0.90  | 0.69       | 0.74  | 0.40     | 0.72    |



#### 中文特性能力表(v1.0版)

| 子能力           | 人类 | ChatGLM-6B | MOSS-16B | Vicuna-13B | GPT-3.5 | GPT-4 | BELLE-13B | 星火 | 文心一言 | MiniMax |
| ---------------- | ---- | --------- | ------- | --------- | ------ | ---- | -------- | ---- | ------ | ------- |
| 成语             | 0.80 | 0.30      | 0.10    | 0.30      | 0.70   | 0.70 | 0.30     | 0.70 | 0.40   | 0.30    |
| 文学             | 1.00 | 0.50      | 0.50    | 0.10      | 0.40   | 0.40 | 0.40     | 0.30 | 0.10   | 0.40    |
| 诗词             | 1.00 | 0.20      | 0.20    | 0.20      | 0.30   | 0.60 | 0.00     | 0.50 | 0.30   | 0.20    |
| 字义理解         | 0.80 | 0.10      | 0.30    | 0.70      | 0.70   | 0.70 | 0.20     | 0.20 | 0.30   | 0.20    |
| 古文             | 1.00 | 0.30      | 0.10    | 0.30      | 0.30   | 0.60 | 0.20     | 0.40 | 0.20   | 0.20    |
| 对联             | 1.00 | 0.20      | 0.30    | 0.40      | 0.60   | 0.60 | 0.30     | 0.30 | 0.30   | 0.20    |
| 方言             | 1.00 | 0.30      | 0.30    | 0.20      | 0.70   | 0.80 | 0.10     | 0.50 | 0.20   | 0.20    |
| 歇后语和谚语     | 1.00 | 0.40      | 0.30    | 0.40      | 0.70   | 0.80 | 0.10     | 0.40 | 0.30   | 0.30    |
| 汉字字形和拼音理解 | 0.90 | 0.50      | 0.40    | 0.40      | 0.60   | 0.80 | 0.20     | 0.40 | 0.10   | 0.40    |
| 汉语句法分析     | 1.00 | 0.50      | 0.20    | 0.00      | 0.90   | 0.80 | 0.50     | 0.70 | 0.20   | 0.50    |
| 平均             | 0.95 | 0.33      | 0.27    | 0.30      | 0.59   | 0.68 | 0.23     | 0.44 | 0.24   | 0.29    |




## SuperCLUE的不足与局限
1. 基础能力、中文特性能力：虽然每一部分都包含了10类子能力，但这两个能力的总数据量比较少，可能存在需要扩充数据集的问题。
2. 选取模型的不完全：我们测试了9个模型，但还存在着更多的可用中文大模型。需要后续进一步添加并测试；有的模型由于没有广泛对外提供服务，我们没能获取到可用的测试版本。
3. 选取的能力范围：我们尽可能的全面、综合衡量模型的多维度的能力，但是可能有一些模型能力没有在我们的考察范围内。后续也存在的扩大考察范围的可能。

## SuperCLUE的讨论与交流
SuperCLUE交流群
