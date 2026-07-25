---
title: Word2Vec Skip-gram 训练
date: 2026-07-25 17:07:43
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**Skip-gram 的 MLE 与梯度下降。** 在 14 的概率模型上做极大似然估计，并逐步可视化训练。完整 notebook：[https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/15_word2vec_skip_gram_train copy.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/15_word2vec_skip_gram_train%20copy.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 要点

- 似然：\(\mathcal{L}(\theta)=\prod P(w_o\mid w_c)\)，对数似然便于求导
- 单样本损失：\(J=-\log \hat{y}_o\)（Softmax + 交叉熵）
- 初始化中心/上下文嵌入，迭代更新

## 关键代码

```python
embed_dim = 4
np.random.seed(42)
V_center, U_outside = init_embeddings(V, embed_dim)
```
