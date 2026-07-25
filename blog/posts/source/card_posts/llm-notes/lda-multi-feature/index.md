---
title: 线性判别分析（LDA）
date: 2026-07-25 17:07:43
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**手算 \(S_W/S_B\) 对照 sklearn。** 小样本多类数据上求投影方向，与 `LinearDiscriminantAnalysis.scalings_` 对照（尺度/符号可不同，看分量比）。完整 notebook：[02_LDA_multi_feature.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/02_LDA_multi_feature.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 公式

类内散度 \(S_W\)、类间散度 \(S_B\)。最优投影满足广义特征值问题：

<div>
\[
S_W^{-1} S_B \, w = \lambda w
\]
</div>

取最大特征值对应的特征向量作为投影方向。

## 关键代码

造数（`seed=42`，小样本便于手算）：

```python
X, y = make_classification(
    n_samples=8, n_features=4, n_redundant=0, n_informative=4,
    n_clusters_per_class=1, n_classes=4, random_state=42, hypercube=True,
)
X = np.round(X).astype(int)
```

手算投影与 sklearn 对照：

```python
w_manual = manual_lda(X, y)  # eig(inv(S_W) @ S_B)
lda = LinearDiscriminantAnalysis()
lda.fit(X, y)
w_sklearn = lda.scalings_[:, 0]
# 用 w[0]/w[1] 等比对照方向
```
