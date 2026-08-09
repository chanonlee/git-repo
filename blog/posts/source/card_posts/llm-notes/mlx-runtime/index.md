---
title: MLX Runtime
date: 2026-08-09 15:27:34
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

目标：建立 MLX 的**系统心智模型**——先把五层拆开，再看一次训练步如何穿过各层。完整 notebook：[05_mlx_device_stream.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/lab/simple_example/notebooks/runtime/05_mlx_device_stream.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

假设：本机同时可用 `mx.cpu` 与 `mx.gpu`（Apple Silicon / Metal）。无 GPU 环境请勿直接跑本笔记。

```text
                 MLX System Model

                   数据世界
                   Data World
                        |
                        v
                   资源世界
                   Resource World
                        |
                        v
                   执行世界
                   Execution World
                        |
                        v
                   通信世界
                   Communication World
                        |
                        v
                   优化世界
                   Optimization World
```

| 世界 | 回答的问题 | 本层对象 | 本层不负责 |
| --- | --- | --- | --- |
| **数据世界 Data** | 哪些样本由谁处理？ | Dataset、Shard | 设备、队列、归约、更新策略 |
| **资源世界 Resource** | 有哪些计算资源？算子落在哪？ | Device（cpu / gpu） | 数据怎么切、队列怎么排 |
| **执行世界 Execution** | 任务如何入队与跑完？ | Stream、kernel | 跨进程归约、Optimizer 策略 |
| **通信世界 Communication** | 多路如何同步/归约？ | `distributed` group、`all_sum` / average_gradients | 参数更新公式、数据切分本身 |
| **优化世界 Optimization** | 如何根据梯度更新参数？ | Optimizer、Parameter Update | Device 枚举、collective 语义 |

## 正交关系

- `shard ≠ device`（Data ≠ Resource）——中间是 **runtime mapping**
- `device ≠ stream`（Resource ≠ Execution）
- `stream ≠ hardware`
- 通信（归约）≠ 优化（用归约后的梯度改参数）
- Optimizer **不属于** Execution 的一条 Stream 身份；它是 Optimization 层的步骤（其内部 update 仍会再变成 Execution 里的 kernels）

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
