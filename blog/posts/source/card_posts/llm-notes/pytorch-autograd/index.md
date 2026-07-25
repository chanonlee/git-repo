---
title: PyTorch autograd
date: 2026-07-25 17:07:43
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**计算图与自动求导用法。** `requires_grad`、非标量 `backward(gradient=...)`、`torch.autograd.grad`。完整 notebook：[04_pytorch_autograd.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/04_pytorch_autograd.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 要点

- 计算图：有向无环图，节点是操作
- `requires_grad=True` 把张量纳入图，反向按链式法则回传
- 对向量求梯度时需 `gradient` / `grad_outputs`，或先收成标量

## 关键代码

```python
a = torch.tensor([2., 3.], requires_grad=True)
b = torch.tensor([6., 4.], requires_grad=True)
Q = 3 * a**3 - b**2
Q.backward(gradient=torch.tensor([1., 1.]))
# 或：ag.grad(outputs=Q, inputs=(a, b), grad_outputs=torch.ones_like(Q))
```
