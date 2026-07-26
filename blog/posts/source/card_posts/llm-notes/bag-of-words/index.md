---
title: 词袋模型（Bag-of-Words）
date: 2026-07-26 13:15:46
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**特征工程：稀疏计数向量。** 把文本变成文档–词矩阵；对照 one-hot。与 Word2Vec 对照——这里是手工表示，Skip-gram 学稠密词向量。完整 notebook：[26_bag_of_words.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/lab/simple_example/notebooks/26_bag_of_words.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 公式

词表 \(\mathcal{V}\)，文档 \(d\) 的 BoW 向量第 \(i\) 维为词 \(w_i\) 在 \(d\) 中的出现次数。文档 BoW 等于文档内各词 one-hot 之和。

## 关键代码

与 Word2Vec 同款小语料：

```python
corpus = [
    "我 喜欢 学习 机器 学习",
    "机器 学习 很 有趣",
    "我 喜欢 编程",
]
```

文档–词矩阵：

```python
X_bow = np.vstack([bow_vector(d, w2i) for d in docs])
# 形状 (文档数, |V|)
```

