---
title: 多元线性回归：手算 OLS 对照 sklearn
date: 2026-07-25 15:57:00
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

用模拟数据验证多元线性回归：手工闭式解与 `sklearn.LinearRegression` 是否得到同一组系数。完整 notebook：[01_Linear_Regression_multi_feature.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/01_Linear_Regression_multi_feature.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 公式

带截距的设计矩阵 $X$（首列全 1），OLS 闭式解：

$$\beta = (X^\top X)^{-1} X^\top y$$

真值设定为 $y = 3 + 2 x_1 - 1.5 x_2 + 0.8 x_3 + \varepsilon$。

## 关键代码

造数（`seed=42`）：

```python
np.random.seed(42)
n_samples = 100
x1 = np.linspace(0, 10, n_samples)
x2 = np.random.rand(n_samples) * 5
x3 = np.random.randn(n_samples) * 2
noise = np.random.randn(n_samples) * 1.5
y = 3 + 2*x1 - 1.5*x2 + 0.8*x3 + noise
X = np.column_stack((np.ones(n_samples), x1, x2, x3))
```

手算系数：

```python
beta_manual = np.linalg.inv(X.T.dot(X)).dot(X.T.dot(y))
```

与 sklearn 对照（拟合时去掉截距列）：

```python
model = LinearRegression()
model.fit(X[:, 1:], y)
# model.intercept_ 与 model.coef_ 应对齐 beta_manual
```

## 图

残差相对预测值（应大致落在零线附近）：

![残差散点](/img/llm-notes-lr-residuals.png)

固定 $x_3$ 为均值时，$x_1$–$x_2$–$y$ 上的回归平面：

![回归平面](/img/llm-notes-lr-plane.png)
