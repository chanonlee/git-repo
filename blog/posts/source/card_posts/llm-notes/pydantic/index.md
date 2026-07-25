---
title: Pydantic 校验
date: 2026-07-25 17:07:43
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**用模型约束结果结构与范围。** `BaseModel` / `EmailStr` 等校验输入或 LLM 结构化输出。完整 notebook：[16_pydantic.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/16_pydantic.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 关键代码

```python
class UserInput(BaseModel):
    name: str
    email: EmailStr
    query: str

user_input = UserInput(
    name="Joe User",
    email="joe.user@example.com",
    query="I forgot my password.",
)
```
