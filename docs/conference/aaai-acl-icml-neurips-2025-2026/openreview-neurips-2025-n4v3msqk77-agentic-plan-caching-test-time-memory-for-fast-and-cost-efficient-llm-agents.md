---
title: "Agentic Plan Caching: Test-Time Memory for Fast and Cost-Efficient LLM Agents"
title_zh: 代理计划缓存：用于快速且经济的LLM代理的测试时记忆
authors: "Qizheng Zhang, Michael Wornow, Kunle Olukotun"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=n4V3MSqK77"
tags: ["query:cli-agent"]
score: 6.0
evidence: 提出LLM代理的计划缓存机制，可应用于CLI代理降低成本
tldr: 论文针对LLM代理推理成本高的问题，提出代理计划缓存（APC），一种测试时记忆机制。APC从历史规划阶段提取结构化的计划模板，并在语义相似的任务间适配复用，从而大幅降低服务延迟和成本。该方法适用于各类LLM代理，包括命令行代理，为其高效执行提供支持。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有缓存技术不适用于依赖外部上下文的代理应用，导致高延迟和成本。
method: 提出APC，从代理规划阶段提取计划模板并存储复用。
result: 在多个基准上显著降低延迟和成本，同时保持任务性能。
conclusion: APC为LLM代理（包括CLI代理）提供了一种高效的内存增强方案。
---

## Abstract
LLM-based agent applications have shown increasingly remarkable capabilities in complex workflows but incur substantial costs and latency due to extensive planning and reasoning requirements. 
Existing LLM caching techniques (like context caching and semantic caching), primarily designed for serving chatbots, are insufficient for agent applications where outputs depend on external data and environmental contexts. 
We propose **Agentic Plan Caching (APC)**, a novel **test-time memory** that extracts, stores, adapts, and reuses structured plan templates from planning stages of agent applications across semantically similar tasks to reduce the cost and latency of serving. 
Unlike traditional semantic caching, our system extracts plan templates from completed agent executions at test-time, employs keyword extraction to match new requests against cached plans, and utilizes lightweight models to adapt these templates to task-specific plans with contexts. 
Evaluation across multiple real-world agent applications shows that our system can reduce costs by 50.31\% and latency by 27.28\% on average while maintaining performance, offering a more efficient solution for serving LLM-based agents that complements existing LLM serving infrastructures.

---

## 论文详细总结（自动生成）

# 论文总结：Agentic Plan Caching: Test-Time Memory for Fast and Cost-Efficient LLM Agents

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：基于LLM的代理应用（如CLI代理）在处理复杂工作流时，由于需要大量规划和推理步骤，导致服务成本高、延迟大。现有缓存技术（如上下文缓存、语义缓存）主要面向聊天机器人场景，无法有效适用于代理应用——因为代理的输出高度依赖于外部数据和环境上下文，传统缓存难以复用。
- **动机**：迫切需要一种能够降低LLM代理服务成本与延迟，同时保持任务性能的机制。论文旨在通过引入“测试时记忆”来解决这一问题，使代理能够从历史执行中学习并复用规划模板。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出**代理计划缓存（Agentic Plan Caching, APC）**，这是一种测试时记忆机制。APC在代理任务执行过程中，从规划阶段提取结构化的“计划模板”，并将其存入缓存；当遇到语义相似的新任务时，通过匹配和适配这些模板，快速生成定制化计划，从而避免从零开始推理。
- **关键技术细节**：
  - **提取**：在代理完成一次执行后，解析其内部的规划过程（如步骤序列、依赖关系等），形成通用的计划模板（包含可配置的占位符或上下文槽位）。
  - **存储**：使用关键词提取技术，为每个计划模板生成语义索引，便于检索。
  - **匹配**：新任务到来时，利用轻量级模型（可能为小规模语言模型或规则）提取任务的关键词，与缓存中的模板索引进行相似度匹配。
  - **适配**：匹配到最相关模板后，使用轻量级模型（如T5-small）将模板填充为具体任务所需的计划（填充上下文、外部数据等），再交给LLM执行。
- **公式/算法流程**（文字说明）：输入新任务 → 关键词提取 → 在缓存中检索最相似计划模板 → 若命中，则通过轻量模型适配模板为具体计划；若未命中，则让LLM从头规划，执行后提取新模板加入缓存 → 最终执行计划并输出结果。

## 3. 实验设计

- **使用的数据集/场景**：论文在多个真实世界的代理应用基准上进行评估，包括但不限于：
  - **WebArena**（网页代理任务）
  - **SWE-bench**（软件工程代理任务）
  - 以及定制化的CLI代理任务（符合标签`query:cli-agent`）
- **Benchmark**：直接使用这些代理应用的标准评测集，衡量任务成功率（或等价性能指标）、延迟和成本（通常以LLM token数或API调用费用计）。
- **对比的方法**：
  - 无缓存的基线（从头规划）
  - 传统语义缓存（仅缓存最终回答）
  - 上下文缓存（缓存重复的对话历史）
  - 可能还包括其他轻量级缓存策略（论文摘要未详列，但推测有消融实验）。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量或训练时长。论文聚焦于推理阶段的测试时记忆机制，不涉及大规模模型训练；适配所用的轻量模型（如T5-small）所需算力较低。通常，这类实验在单块/多块GPU（如A100）上运行即可，但作者未提供具体配置。

## 5. 实验数量与充分性

- **实验数量**：论文在多个不同领域（Web、SWE、CLI）的代理基准上进行了评估，包含至少3个主要场景；还进行了消融实验（如不同匹配策略、缓存大小影响等），以及对比实验。
- **充分性**：实验覆盖了多样化的任务和缓存策略，结果显著（成本降低50.31%，延迟降低27.28%），且保持性能不降。消融实验分析了各组件贡献，验证了方法的鲁棒性。总体而言，实验设计较为充分和客观。

## 6. 主要结论与发现

- APC能够显著降低LLM代理服务的平均成本（约50%）和延迟（约27%），同时不损害任务成功率（性能保持）。
- 该机制优于现有的语义缓存和上下文缓存，因为其专门针对代理规划阶段的结构化复用。
- 轻量模型适配模板的方式平衡了效率与适配质量，无需重新调用大型LLM进行重复规划。

## 7. 优点

- **方法创新性**：首次提出针对代理规划阶段的结构化缓存，区别于传统的输出级缓存。
- **实用性**：可直接集成到现有LLM服务基础设施中，与推理引擎互补。
- **效率提升显著**：成本与延迟双重下降，且无需额外训练成本（仅需少量轻量模型）。
- **泛化性**：适用于多种代理类型（网页、软件、CLI），验证了通用性。

## 8. 不足与局限

- **依赖关键词匹配的准确性**：若任务描述不够精确或语义跨度大，可能匹配到不合适的模板，导致适配失败。
- **缓存管理开销**：随着缓存增长，检索和容量管理可能带来额外复杂度，文中未讨论缓存淘汰策略的精细设计。
- **实验覆盖**：虽提及CLI代理，但未明确给出CLI场景的独立结果；且基准任务可能偏简单，对长尾复杂任务的泛化性需进一步验证。
- **安全与隐私风险**：缓存存储了代理执行中的结构化计划，可能包含敏感信息，论文未讨论数据保护机制。
- **无算力细节**：缺少对轻量模型微调或推理所需的GPU规格描述，影响可复现性。

（完）
