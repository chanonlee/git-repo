---
title: Inventory What-If Lab
date: 2026-08-17 23:43:40
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

[← 库存](/card_posts/business-domains/inventory/)

**门店库存 What-If 试验台。** 同一套订货 / FEFO / 生产规则下，只改一个局部变量，把 Control 与 Experiment 从 Day 0 各自跑满 N 天，对照库存、报废、流水与盈利。代码在 [chanon-data-lab · src/inventory-what-if-lab](https://github.com/chanonlee/chanon-data-lab/tree/lab/simple_example/src/inventory-what-if-lab)。

## 机制

- BaseConfig 深拷贝为两组；实验层只 patch 一个变量（保质期、提前期、订货点、再订货量、期初、产品开关、配方增减、单价、售价）。
- 价格只进入统计层：流水 = 销售额 − 采购支出；真实盈利 = 销售额 − COGS − 报废成本。订货决策不读价格。
- 当前模型按销售上限生产即售出，日销售量 ≡ 日产量。

## 对比试验：芒果再订货量 60 → 300

默认芒果订货量=60、日销上限=20 时，原料往往当日周转完，保质期拉长几乎看不出报废差异。要观察「多订一点」的系统后果，把再订货量从 60 提到 300，跑 365 天。

### 总库存

![总库存双曲线](/img/inventory-what-if-stock.png)

实验组能支撑更多高复杂度配方（芝芝芒芒），总销量约 +16.8%；平均在库库存反而略降（约 −1.4%）——多订带来的是**更高周转与更多报废**，不是简单的「库存在高水平趴着」。

### 每日报废

![每日报废双曲线](/img/inventory-what-if-waste.png)

对照组报废为 0；实验组累计报废约 2960（主要是芒果），报废成本约 888。局部「多补一点」把短保物料推过了消耗窗口，报废从无到有。

### 每日流水

![每日流水双曲线](/img/inventory-what-if-cashflow.png)

总收入约 +24.6%，总流水与总盈利约 +14.7%。收入涨幅高于流水/盈利：多采多卖的同时，采购支出与报废成本一起上来；流水与盈利同向，但口径仍不同——采购进流水、报废进盈利。

## 本地启动

```bash
cd src/inventory-what-if-lab
pip install -r requirements.txt
streamlit run app.py
```

也可导出本页用的对比图：`python scripts/export_compare_charts.py`。
