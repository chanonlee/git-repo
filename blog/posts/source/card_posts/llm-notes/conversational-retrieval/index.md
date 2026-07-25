---
title: Conversational Retrieval 聊天 demo
date: 2026-07-25 17:07:43
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**带记忆的检索问答（聊天 demo）。** Chroma + `ConversationBufferMemory` + `ConversationalRetrievalChain`。本地 embedding + LM Studio；**仅占位 key。** 完整 notebook：[09_langchain_conversational_retrieval.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/09_langchain_conversational_retrieval.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 关键代码

```python
embeddings = HuggingFaceEmbeddings(model_name="sentence-transformers/all-MiniLM-L6-v2")
vectorstore = Chroma.from_documents(documents, embeddings)
memory = ConversationBufferMemory(memory_key="chat_history", return_messages=True)
qa = ConversationalRetrievalChain.from_llm(
    llm, vectorstore.as_retriever(), memory=memory,
)
result = qa({"question": "我该怎么阅读transformer模型？"})
```
