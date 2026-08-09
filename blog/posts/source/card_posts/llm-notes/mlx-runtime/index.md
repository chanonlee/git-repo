---
title: MLX Runtime
date: 2026-08-09 15:27:34
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**MLX 系统心智模型：数据 · 资源 · 执行 · 通信 · 优化。** 先把五层拆开，再看一次训练步如何穿过各层。完整 notebook：[05_mlx_device_stream.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/lab/simple_example/notebooks/runtime/05_mlx_device_stream.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 五层

- **数据**：Dataset / Shard — 哪些样本由谁处理
- **资源**：Device — 算子落在哪（cpu / gpu）
- **执行**：Stream / kernel — 任务如何入队与跑完
- **通信**：distributed / `all_sum` — 多路如何同步与归约
- **优化**：Optimizer / Parameter Update — 如何根据梯度更新参数

正交关系：`shard ≠ device`，`device ≠ stream`；通信（归约）≠ 优化（用归约后的梯度改参数）。

## 关键代码

```python
# 资源：同一切片可换 Device 重算（数据对象不变，只改 runtime mapping）
shard0 = mx.arange(6).astype(mx.float32)
r_cpu = mx.multiply(shard0, 2, stream=mx.cpu)
r_gpu = mx.multiply(shard0, 2, stream=mx.gpu)
mx.eval(r_cpu, r_gpu)

# 执行：同 Device 两条 Stream，可重叠入队
dev = mx.gpu
s1, s2 = mx.new_stream(dev), mx.new_stream(dev)
c = mx.matmul(a, b, stream=s1)
d = mx.matmul(a, b, stream=s2)
mx.eval(c, d)
```
