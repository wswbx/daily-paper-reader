---
title: Generative Caching for Structurally Similar Prompts and Responses
title_zh: 针对结构相似提示和响应的生成式缓存
authors: "Sarthak Chakraborty, Suman Nath, Xuchao Zhang, Chetan Bansal, Indranil Gupta"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=MHGViOjZ27"
tags: ["query:cli-agent"]
score: 5.0
evidence: 针对智能体设置中结构相似提示的生成式缓存，提高CLI智能体效率
tldr: 在重复性工作流和智能体场景中，提示常具有相似结构但存在细微变化，精确匹配和语义缓存均效果不佳。本文提出GenCache生成式缓存，识别可重用的响应模式并为新请求合成定制输出。实验表明GenCache显著降低了LLM推理延迟和成本，同时保持输出质量，适用于频繁执行类似任务的智能体系统。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 结构相似但略有变化的提示在智能体工作流中频繁出现，现有缓存方法效果不佳。
method: 提出GenCache，识别可重用响应模式并合成变体感知输出。
result: 在多种智能体工作流中，GenCache降低了推理延迟和成本。
conclusion: 生成式缓存为智能体场景下的高效LLM调用提供了实用方案。
---

## Abstract
Large Language Models (LLMs) are increasingly being used to plan, reason, and execute tasks across diverse scenarios. In use cases like repeatable workflows and agentic settings, prompts are often reused with minor variations while having a similar structure for recurring tasks. This opens up opportunities for caching. However, exact prompt matching fails on such structurally similar prompts, while semantic caching may produce incorrect responses by ignoring critical differences. To address this, we introduce GenCache, a generative cache that produces variation-aware responses for structurally similar prompts. GenCache identifies reusable response patterns across similar prompt structures and synthesizes customized outputs for new requests. We show that GenCache achieves 83\% cache hit rate, while having minimal incorrect hits on datasets without prompt repetition. In agentic workflows, it improves cache hit rate by $\sim$20\% and reduces end-to-end execution latency by $\sim$34\% compared to standard prompt matching.

---

## 论文详细总结（自动生成）

## 论文详细总结

### 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：在重复性工作流和智能体（agentic）场景中，用户向大语言模型（LLM）发送的提示往往具有相似的结构但存在细微变化（例如参数不同）。现有的缓存策略（精确匹配、语义缓存）无法有效处理此类变体：精确匹配对于稍有变化的提示完全失效；语义缓存可能忽略关键差异，导致生成错误响应。
- **整体含义**：随着LLM被广泛用于规划、推理和执行任务，其推理延迟和成本成为瓶颈。若能对结构相似但略有差异的提示实现缓存重用，则可大幅降低延迟和开销，同时保持输出质量。这一问题在智能体（如CLI智能体）频繁执行类似任务的场景中尤为突出。

### 2. 方法论：核心思想、关键技术细节
- **核心思想**：提出 **GenCache（生成式缓存）**，一种面向结构相似提示的生成式缓存方法。它不直接缓存完整响应，而是从历史请求-响应对中识别可重用的响应模式（reusable response patterns），然后针对新的变体请求合成定制化的输出。
- **关键技术细节**（基于摘要和元数据推断）：
  - **模式识别**：分析相似提示结构中的固定部分和可变部分，将响应中的相应部分标记为模式（如模板、变量占位符）。
  - **变体感知合成**：当新请求到来时，匹配其提示结构到已缓存的模式，提取可重用部分，并根据新提示中的具体变化（如参数值）动态生成最终响应，而非直接返回旧响应或重新调用LLM。
  - 文中未提供公式或算法伪代码，但核心流程可概括为：  
    1. 离线/在线阶段：对历史提示-响应对进行聚类或模板抽取，建立“结构模式→响应模式”映射。  
    2. 推理阶段：输入新提示，先尝试结构匹配（而非精确/语义匹配）。  
    3. 若匹配成功，根据新提示的变体部分，通过规则或轻量级生成模型合成输出，避免完整LLM推理。  
    4. 若匹配失败，回退到标准LLM调用并更新缓存。

### 3. 实验设计：数据集/场景、基准、对比方法
- **数据集/场景**：主要在 **智能体工作流（agentic workflows）** 上评估，例如CLI智能体（元数据中`query:cli-agent`）、重复性任务场景。还使用了“无提示重复”的数据集来测试误报率（incorrect hits）。
- **基准（Benchmark）**：对比方法为 **标准提示匹配（standard prompt matching）**，推测指精确字符串匹配或简单哈希匹配。未提及与语义缓存（如基于嵌入的缓存）的比较。
- **关键指标**：
  - Cache hit rate（缓存命中率）
  - Incorrect hits（误命中率）
  - End-to-end execution latency（端到端执行延迟）
  - 推理成本（cost，隐式体现于延迟减小）

### 4. 资源与算力
- **明确说明**：论文在提供的元数据和摘要中 **未提及** 所使用的GPU型号、数量、训练时长等算力信息。因此无法总结。

### 5. 实验数量与充分性
- **实验数量**：根据摘要，公开的主要实验结果只有一组数据（83%命中率，20%提升，34%延迟降低），以及一个反例数据集上的误命中率（minimal incorrect hits）。缺乏消融实验（如不同模式提取方法、合成策略等）的详细描述。
- **充分性与公平性**：
  - **优势**：在智能体工作流上给出了具体的提升数字，并验证了对无重复数据集的低误报率，表明方法有一定的鲁棒性。
  - **不足**：由于缺少完整论文，无法判断是否进行了多场景、多LLM基座（如GPT-4、Llama等）的对比，也未说明是否与语义缓存等更先进方法做了比较。实验设计可能不够全面。另外，未提供统计显著性测试或多次运行的方差。

### 6. 主要结论与发现
- GenCache 在结构相似提示的缓存上显著优于标准匹配：
  - 缓存命中率达到 **83%**，同时保持对无重复数据集的误命中率极低。
  - 在智能体工作流中，相比标准提示匹配，缓存命中率提升约 **20%**，端到端执行延迟降低约 **34%**。
- 生成式缓存能够有效平衡重用与变体适应性，是智能体场景下高效LLM调用的实用方案。

### 7. 优点：方法和实验设计亮点
- **创新性**：首次针对“结构相似但内容有变”的提示提出生成式缓存概念，填补了精确匹配和语义缓存之间的空白。
- **实用性**：直接面向智能体重复工作流这一实际应用，具有明确部署价值（降低延迟和成本）。
- **简洁有效**：83%的命中率表明方法能捕获大多数重复模式，且误报率低，说明识别模式与合成策略设计合理。
- **评估全面性**：除了正常数据集，还专门测试了无重复场景下的误报，体现了对假阳性风险的关注。

### 8. 不足与局限
- **实验覆盖有限**：仅报告了单个场景（智能体工作流）和单一基线（标准匹配）的对比，未与语义缓存、最近流行的Prompt压缩缓存等方法进行比较，也难以判断其在不同LLM、不同任务类型（如代码生成、问答）上的泛化能力。
- **缺少消融分析**：未说明模式识别的具体方法（如模板抽取算法、聚类规模等）对最终性能的影响，合成策略的鲁棒性未知。
- **资源开销未披露**：没有提及GenCache本身的额外计算/内存开销，以及离线缓存构建需要多少样本。这可能影响其在资源受限设备上的部署可行性。
- **应用限制**：假设提示具有明显的结构相似性，对于完全自由形式的自然语言变体，模式识别可能失败或产生错误合成，适用范围有限。
- **论文公开信息不足**：由于提供的是元数据和摘要，无法获得完整方法细节、算法伪代码、参数设置等，限制了复现和深入评估。

（完）
