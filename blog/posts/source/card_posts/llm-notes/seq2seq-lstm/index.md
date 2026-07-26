---
title: Seq2Seq（LSTM）
date: 2026-07-25 20:33:54
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**同一用例下的 Seq2Seq，骨干为 `nn.LSTM`（无 Attention）。** 中文句子 → Encoder 的 (h, c) → Decoder 逐词生成英文。完整 notebook：[25_lstm_seq2seq.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/lab/simple_example/notebooks/25_lstm_seq2seq.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

同用例对照：[Seq2Seq（RNN）](/card_posts/llm-notes/seq2seq-rnn/) · [Seq2Seq（Transformer）](/card_posts/llm-notes/seq2seq-transformer/)

## 用例（三篇共用）

```python
sentences = [
    ['我 是 教 师 P', 'S I am a teacher', 'I am a teacher E'],
    ['我 喜 欢 教 学', 'S I like teaching P', 'I like teaching P E'],
    ['我 是 厨 师 P', 'S I am a cook', 'I am a cook E'],
]
```

## 本篇骨干

```
Seq2Seq
├── Encoder: Embedding → nn.LSTM → 最终 (h, c)
└── Decoder: Embedding → nn.LSTM(初态=h,c) → Linear → 词表
```
