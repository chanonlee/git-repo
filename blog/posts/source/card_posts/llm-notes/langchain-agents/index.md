---
title: LangChain Agents demo
date: 2026-07-25 17:07:43
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**工具 + ReAct Agent。** `load_tools` + `initialize_agent`；本地 LM Studio。**仅占位 `api_key="lm-studio"`，勿写真实密钥。** 完整 notebook：[08_langchain_agents.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/08_langchain_agents.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 关键代码

```python
LM_STUDIO_BASE = "http://127.0.0.1:1234/v1"
llm = ChatOpenAI(base_url=LM_STUDIO_BASE, api_key="lm-studio", temperature=0, model="local")
tools = load_tools(["llm-math", "wikipedia"], llm=llm)
agent = initialize_agent(
    tools, llm,
    agent=AgentType.CHAT_ZERO_SHOT_REACT_DESCRIPTION,
    verbose=True,
)
```
