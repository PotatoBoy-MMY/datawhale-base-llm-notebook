# 第五章 预训练模型
## 第一节 BERT 结构及应用

Bert  
![alt text](src/image.png)

仅利用了编码器结构，使用双向自注意力机制，同时运用预训练+微调训练反噬，实现了强大的语义理解能力

### Bert是怎么训练的
- **接受的输入**
    $$
    Input_{embedding} = Token_{embedding} + Position_{embedding} + Segment_{embedding}
    $$
    其中$Token_{embedding}$为词元的嵌入，$Position_{embedding}$为片段嵌入，用于区分输入中的不同句子，$Segment_{embedding}$为位置嵌入，额外引入位置信息，弥补Transformer 的自注意力机制本身不包含位置信息的问题

- **预训练阶段的任务**  
    Bert的成功离不开其再预训练阶段定义的两项全新任务  
    1. 掩码语言模型 (Masked Language Model, MLM)：随机遮掩或者替代一些词元，对其预测  
    2. 下一句预测 (Next Sentence Prediction, NSP)：预测一句话是不是另一句话的下一句（*在更大规模的预训练中表现不佳，但在其原始论文的实验环境下确实更好*）

- **怎么微调**
    1. 文本分类任务：使用CLS对文本分类
    2. 词元分类任务：针对每个词元输出一个最终向量，然后用一个全连接层学习出来
   
##  第二节 GPT 结构及应用

Bert完全的编码器  
GPT完全的解码器

感觉资料这部分讲的比较粗糙，还是朝圣吧（[GPT原始论文](https://cdn.openai.com/research-covers/language-unsupervised/language_understanding_paper.pdf?utm_source=chatgpt.com)）

## 第三节 T5 结构及应用
第一次知道这个，没什么特殊的，只不过完整利用了Encoder-Decoder架构