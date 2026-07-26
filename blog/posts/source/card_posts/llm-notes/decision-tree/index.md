---
title: 决策树（DT）
date: 2026-07-26 13:15:46
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**模式识别：在已有特征上选分裂。** 手算一层基尼增益，对照 `DecisionTreeClassifier`。不是自动提特征；集成（随机森林等）不展开。完整 notebook：[28_decision_tree.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/lab/simple_example/notebooks/28_decision_tree.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 公式

基尼不纯度 \(G=1-\sum_c p_c^2\)。分裂后加权基尼下降量即为增益，取增益最大的特征与阈值。

## 关键代码

```python
tree = DecisionTreeClassifier(criterion="gini", max_depth=1, random_state=0)
tree.fit(X, y)
print(export_text(tree, feature_names=["x0", "x1"]))
```

