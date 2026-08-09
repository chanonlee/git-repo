---
title: LLM 相关笔记（Side Project 入口）
date: 2026-05-04 12:00:00
layout: post
comments: false
banner_img: /img/44d47d503b09e7879b9788cdcc98082.jpg
---

本页是 Side Project 入口：按[问题空间分层](/2026/07/25/20260725-%E4%B8%8D%E8%A6%81%E8%AE%B0%E5%BF%86%20AI%20%E5%90%8D%E8%AF%8D%EF%BC%9A%E5%A4%A7%E6%A8%A1%E5%9E%8B%E6%97%B6%E4%BB%A3%E9%97%AE%E9%A2%98%E7%A9%BA%E9%97%B4%E7%9A%84%E6%BC%94%E5%8C%96/)挂笔记与 Jupyter 实验；**不进首页列表**。站内已发文见 [阅读地图](/guide/)。完整 notebook 仓库：[chanon-data-lab](https://github.com/chanonlee/chanon-data-lab)。

## 模型问题空间的持续扩展

### 模式识别

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/multi-linear-regression/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">多元线性回归（OLS）</div>
          <div class="link-intro">手算 OLS 对照 sklearn；用模拟数据验证闭式解与 LinearRegression 是否同系数。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/lda-multi-feature/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">线性判别分析（LDA）</div>
          <div class="link-intro">手算 SW/SB 对照 sklearn；小样本多类投影方向与 scalings_ 对照。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/knn/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">K 近邻（KNN）</div>
          <div class="link-intro">距离投票；手算欧氏距离对照 KNeighborsClassifier；尺度敏感。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/decision-tree/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">决策树（DT）</div>
          <div class="link-intro">一层基尼分裂手算对照 DecisionTreeClassifier；在已有特征上选规则。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/svm-linear/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">支持向量机（SVM）（不展开核技巧）</div>
          <div class="link-intro">线性最大间隔；与 LDA 对照；仅 LinearSVC / 线性核。</div>
        </div>
      </div>
    </a>
  </div>
</div>

### 特征工程

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/bag-of-words/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">词袋模型（Bag-of-Words）</div>
          <div class="link-intro">稀疏计数向量与 one-hot 对照；通向 Word2Vec 稠密表示之前的手工特征。</div>
        </div>
      </div>
    </a>
  </div>
</div>

### 深度学习

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/word2vec-skip-gram/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Word2Vec Skip-gram</div>
          <div class="link-intro">通向语言模型的过渡：Skip-gram 用神经网络学稠密词向量。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/word2vec-skip-gram-train/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Word2Vec Skip-gram 训练</div>
          <div class="link-intro">Skip-gram 的 MLE 与梯度下降；逐步可视化训练过程。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/seq2seq-rnn/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Seq2Seq（RNN）</div>
          <div class="link-intro">同用例中译英；骨干 nn.RNN，无 Attention。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/seq2seq-lstm/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Seq2Seq（LSTM）</div>
          <div class="link-intro">同用例中译英；骨干 nn.LSTM，无 Attention。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/seq2seq-transformer/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Seq2Seq（Transformer）</div>
          <div class="link-intro">同用例中译英；骨干 Transformer（自注意力 + 跨注意力）。</div>
        </div>
      </div>
    </a>
  </div>
</div>

### 大模型

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/langchain-demo/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">LangChain 入门 demo</div>
          <div class="link-intro">Prompt / Memory / Chain 入门；本地 LM Studio（OpenAI 兼容）。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/langchain-agents/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">LangChain Agents demo</div>
          <div class="link-intro">工具 + ReAct Agent；load_tools + initialize_agent，本地 LM Studio。</div>
        </div>
      </div>
    </a>
  </div>
</div>

## 大模型时代问题空间如何变迁

### 持续对话

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/conversational-retrieval/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Conversational RAG demo</div>
          <div class="link-intro">带记忆的 Conversational RAG；Chroma 检索 + ConversationBufferMemory。</div>
        </div>
      </div>
    </a>
  </div>
</div>

### 图像与声音

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/local-vision-minimal/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">本地视觉识别</div>
          <div class="link-intro">本地 VL 识别图像；图片转 base64 经 OpenAI 兼容接口调用。</div>
        </div>
      </div>
    </a>
  </div>
</div>

### 固定目标（Agent）

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/local-text-tools/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">本地文本 Prompt + Tool</div>
          <div class="link-intro">Prompt 驱动的多轮 tool calling（mock）；@tool + bind_tools。</div>
        </div>
      </div>
    </a>
  </div>
</div>

### 用法优化

### Harness

## 问题空间收敛：从 AI 系统设计到代码实现

## 工程落地

### 基础工具

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/pytorch-autograd/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">PyTorch autograd</div>
          <div class="link-intro">计算图与自动求导；requires_grad、backward、autograd.grad。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/pydantic/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Pydantic 校验</div>
          <div class="link-intro">用模型约束结果结构与范围；BaseModel / EmailStr 等。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/langchain-chroma/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Chroma 向量数据库</div>
          <div class="link-intro">向量库入库与检索；HuggingFaceEmbeddings + Chroma.from_documents。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="/card_posts/llm-notes/langchain-chroma-summarize/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">Chroma 检索摘要</div>
          <div class="link-intro">检索后 stuff 摘要；Chroma + RetrievalQA（stuff 链）。</div>
        </div>
      </div>
    </a>
  </div>
</div>

### 模型 Runtime

<div class="row links links-span-full">
  <div class="card col-12">
    <a href="/card_posts/llm-notes/mlx-runtime/" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">MLX Runtime</div>
          <div class="link-intro">MLX 系统五层：数据 · 资源 · 执行 · 通信 · 优化；先拆层再串一次训练步。</div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="#" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">vLLM Runtime</div>
          <div class="link-intro"></div>
        </div>
      </div>
    </a>
  </div>
  <div class="card col-12">
    <a href="#" class="card-body hover-with-bg">
      <div class="card-content">
        <div class="link-text">
          <div class="link-title">PyTorch Runtime</div>
          <div class="link-intro"></div>
        </div>
      </div>
    </a>
  </div>
</div>
