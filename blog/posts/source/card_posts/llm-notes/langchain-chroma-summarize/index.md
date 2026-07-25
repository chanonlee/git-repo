---
title: Chroma 检索摘要
date: 2026-07-25 17:07:43
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**检索后 stuff 摘要。** Chroma 检索 + `RetrievalQA`（`chain_type="stuff"`）。**仅占位 key。** 完整 notebook：[11_langchain_chroma_summarize.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/11_langchain_chroma_summarize.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 关键代码

```python
llm = ChatOpenAI(
    base_url="http://127.0.0.1:1234/v1",
    api_key="lm-studio",  # 本地占位，勿写真实密钥
    temperature=0,
    model="local",
)
# RetrievalQA(..., chain_type="stuff")
```
