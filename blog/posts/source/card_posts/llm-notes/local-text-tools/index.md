---
title: 本地文本 Prompt + Tool
date: 2026-07-25 17:07:43
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**Prompt 驱动的多轮 tool calling（mock）。** `@tool` + `bind_tools`；本地 LM Studio。**仅占位 `api_key="lm-studio"`。** 完整 notebook：[21_local_text_tools_minimal.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/21_local_text_tools_minimal.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 关键代码

```python
BASE_URL = "http://127.0.0.1:1234/v1"
API_KEY = "lm-studio"  # 本地占位，勿写真实密钥

@tool
def get_mock_weather(region: str) -> str: ...

llm = ChatOpenAI(base_url=BASE_URL, api_key=API_KEY, model=MODEL)
llm_with_tools = llm.bind_tools(tools)
# 多轮：模型发 tool_calls → ToolMessage → 再 invoke
```
