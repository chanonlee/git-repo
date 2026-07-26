---
title: SVM（不展开核技巧）
date: 2026-07-26 13:15:46
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**模式识别：线性最大间隔分类。** 仅线性 SVM；**不展开核技巧**（不讲核函数 / RBF）。与 LDA 对照：都找线性分界，SVM 强调间隔。完整 notebook：[29_svm_linear.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/lab/simple_example/notebooks/29_svm_linear.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 范围

`LinearSVC` / `SVC(kernel="linear")`。正文不涉及核映射与非线性核。

## 关键代码

```python
clf = LinearSVC(C=1.0, dual="auto", random_state=0)
clf.fit(X, y)
w, b = clf.coef_[0], clf.intercept_[0]
```

