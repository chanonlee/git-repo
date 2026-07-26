---
title: K 近邻（KNN）
date: 2026-07-26 13:15:46
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**模式识别：距离投票。** 几乎无训练；预测时取最近 K 个点多数表决。手算欧氏距离对照 `KNeighborsClassifier`；强调特征尺度敏感。完整 notebook：[27_knn.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/lab/simple_example/notebooks/27_knn.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 公式

查询点 \(x\)，训练点 \(\{x_i\}\)，欧氏距离 \(d(x,x_i)=\|x-x_i\|_2\)；取最小的 K 个标签多数投票。

## 关键代码

```python
dists = np.linalg.norm(X - x_query, axis=1)
order = np.argsort(dists)
y_neighbors = y[order[:k]]
```

```python
clf = KNeighborsClassifier(n_neighbors=k, metric="euclidean")
clf.fit(X, y)
```

