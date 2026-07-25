---
title: seq2seq(use Transformer)
date: 2026-07-25 20:33:54
layout: post
comments: false
math: true
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**同一用例下的 Seq2Seq，骨干为 Transformer（自注意力 + 跨注意力）。** 中文句子 → Encoder → Decoder 逐词生成英文。完整 notebook：[06_pytorch_transformer.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/06_pytorch_transformer.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

同用例对照：[seq2seq(use rnn)](/card_posts/llm-notes/seq2seq-rnn/) · [seq2seq(use lstm)](/card_posts/llm-notes/seq2seq-lstm/)

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
Transformer
├── Encoder: Embedding → PositionalEncoding → N×(Self-Attn + FFN)
└── Decoder: Embedding → PositionalEncoding → N×(Self-Attn + Cross-Attn + FFN) → projection
```
