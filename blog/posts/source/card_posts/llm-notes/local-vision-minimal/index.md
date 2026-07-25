---
title: 本地视觉识别
date: 2026-07-25 17:07:43
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← LLM 相关笔记](/card_posts/llm-notes/)

**大模型识别图像（本地 VL）。** OpenAI 兼容接口（如 LM Studio）；本地图片读成 base64 再放进 `data:` URL。**`api_key="lm-studio"` 仅为本地占位，勿写真实密钥；本页不嵌大图。** 完整 notebook：[19_local_vision_minimal.ipynb](https://github.com/chanonlee/chanon-data-lab/blob/main/notebooks/19_local_vision_minimal.ipynb)（仓库 [chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)）。

## 关键代码

```python
BASE_URL = "http://127.0.0.1:1234/v1"
API_KEY = "lm-studio"  # 本地占位，勿写真实密钥
client = OpenAI(base_url=BASE_URL, api_key=API_KEY)

b64 = base64.standard_b64encode(IMAGE_PATH.read_bytes()).decode("ascii")
image_url = f"data:{mime};base64,{b64}"
# messages 中带 type=image_url 的 content
```
