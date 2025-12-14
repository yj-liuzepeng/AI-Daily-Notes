# AI-Daily-Notes

1. 大模型推理/生成阶段的两个参数 temperature 和 top-p：大模型在推理生成时，其实就是根据概率预测下一个词，模型输出的是一组原始分数（Logits），在转化为概率（Softmax）之前，会把这些分数除以 temperature (T)，从而**控制输出概率**，temperature越小，输出相对越稳定，temperature越大，输出相对就会发散 ，就如这个词意温度一样，水低温时稳定成固态，高温时不稳定会挥发。top-p控制的也是输出的概率，越小，输出越保守，越稳定，越大输出的答案越发散。推荐只用一种即可，一句话描述： temperature 熵增熵减，top-p 去尾。（8.97 复制打开抖音，看看【马克的技术工作坊的作品】Temperature & Top-p：大模型的创... https://v.douyin.com/GgkLeHOHKXI/ r@E.uF 12/05 OKw:/ ）
2. Context Engineering：一个token大概0.75个单词，或者1.5个汉字，大语言模型面对的三个问题 1.Context Window非常有限2.输入太杂乱会影响模型输出3.输出阅读，成本越高  ----> 解决就是Context Engineering，目的是精心设计给模型输入的内容，让模型在有限的Context Window中回答的更好，核心思想是不改变模型结构，而是改变模型看到什么。
   四部分：1.保存Context，把输入进行筛选总结，进行保存，一般是内存/硬盘；2.选择Context，在存下来的记忆库中精准找到需要的信息，分为静态选择和动态选择，静态选择就是把一些永远重要的信息始终放在Context中，比如cursor这种编辑器中的rules文件，动态选择，就是选择与用户最相关的内容放到Context中，有很多实现方式比如RAG；3.压缩Context，Context中最占空间的两类数据一般是模型的输出文本和工具的执行结果，对历史消息进行压缩，例如claude编辑器，当历史内容过多时，会调用auto-compact对之前内容进行总结，记录重要内容，进行体积压缩；4.隔离Context，不同模块之间的Context相互隔离，互不干扰，如一些subagent互相隔离。
