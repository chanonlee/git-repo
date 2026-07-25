---
title: LangChain 入门 demo
date: 2026-07-25 17:07:43
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**Prompt / Memory / Chain 入门。** 本地 LM Studio（OpenAI 兼容）；**示例仅用占位 `api_key="lm-studio"`，勿写入真实云端密钥。** 完整 notebook：[07_langchain.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/07_langchain.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 关键代码

PromptTemplate：

```python
prompt = PromptTemplate(
    input_variables=["product"],
    template="What is a good name for a company that makes {product}?",
)
prompt.format(product="colorful socks")
```

本地模型（占位 key）：

```python
LM_STUDIO_BASE = "http://127.0.0.1:1234/v1"
llm = ChatOpenAI(
    base_url=LM_STUDIO_BASE,
    api_key="lm-studio",  # 本地占位，勿写真实密钥
    temperature=0,
    model="local",
)
```

Memory 三种思路见 notebook：BufferWindow / SummaryBuffer / TokenBuffer。
