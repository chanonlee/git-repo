---
title: Word2Vec Skip-gram
date: 2026-07-25 17:07:43
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**通向语言模型的过渡：词向量。** Skip-gram 用神经网络学稠密表示，对应「自动提取特征」这一层。完整 notebook：[14_word2vec_skip_gram.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/14_word2vec_skip_gram.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 公式

给定中心词 \(w_c\) 与上下文词 \(w_o\)：

<div>
\[
P(w_o \mid w_c) = \frac{\exp(\mathbf{u}_o^\top \mathbf{v}_c)}{\sum_{i \in \mathcal{V}} \exp(\mathbf{u}_i^\top \mathbf{v}_c)}
\]
</div>

## 关键代码

小语料 + 窗口构造中心–上下文对：

```python
corpus = [
    "我 喜欢 学习 机器 学习",
    "机器 学习 很 有趣",
    "我 喜欢 编程",
]
window_size = 2
```
