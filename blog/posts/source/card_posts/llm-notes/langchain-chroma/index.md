---
title: Chroma 向量数据库
date: 2026-07-25 17:07:43
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**向量库入库与检索。** HuggingFaceEmbeddings + `Chroma.from_documents`（内存模式）+ 检索问答。若接 LLM，**仅用 `api_key="lm-studio"` 占位。** 完整 notebook：[10_langchain_chroma.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/10_langchain_chroma.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 关键代码

```python
vectorstore = Chroma.from_documents(
    documents,
    embedding=HuggingFaceEmbeddings(model_name="sentence-transformers/all-MiniLM-L6-v2"),
)
# 可选：接本地 LLM 做 RetrievalQA（api_key 只用 lm-studio 占位）
```
