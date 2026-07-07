---
title: On Effectiveness and Efficiency of Agentic Tool-calling and RL Training
title_zh: 论代理工具调用和强化训练的有效性与效率
authors: "Tong Liu, Cheng Qian, Matej Cief, Yuan He, Daniele Dan, Nikolaos Aletras, Gabriella Kazai"
date: 2026-04-30
pdf: "https://openreview.net/pdf/7792384ad86a35d260ce65e1638a93475119a93f.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: LLM代理工具调用的效率与RL训练
tldr: 工具调用是现代LLM代理的核心能力，但其评估结果极易受随机种子、提示模板等实现细节影响。本文系统分析了这些敏感性，并研究了RL训练对工具调用效率的影响，为构建更稳健的LLM代理提供了指导。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有工具调用评估标准不统一，结果对实现细节高度敏感。
method: 通过控制变量实验系统分析评估管线敏感性，并对比不同RL训练策略的效率。
result: 发现了多个导致评估结果显著差异的实现因素，并展示了RL训练对工具调用效率的提升。
conclusion: 需要标准化工具调用评估，RL训练可提升工具调用效率。
---

## Abstract
Tool-calling is a central component of modern large language model (LLM) agents, equipping them with skills beyond their parametric knowledge.
This paper studies tool-calling along two complementary axes: **effectiveness**, i.e., how this capability is *measured*, and **efficiency**, i.e., how it is *learned*.
On effectiveness, we systematically analyze tool-calling evaluation pipelines and show that results can be highly sensitive to seemingly minor, often undocumented implementation choices including the *random seed*, *system prompt*, *multi-turn template construction*, and how *prior interaction/reasoning history* is carried forward. 
These choices can lead to substantial differences in reported performance, especially in multi-turn settings where without rigorous standardization, leaderboard rankings are unreliable. 
On efficiency, we examine standard reinforcement learning (RL) for tool-calling and identify two sources of computational waste: (i) during rollouts, many prompts produce no learning signal, and (ii) during policy updates, optimization incurs high computational cost.
Guided by these findings, we introduce two techniques that accelerate RL-based tool-calling training, achieving substantial wall-clock speedup without degrading performance.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：工具调用（Tool-calling）是现代大型语言模型（LLM）代理的核心能力，使代理超越其参数化知识。然而，现有工具调用的评估标准不统一，性能结果对随机种子、系统提示、多轮模板构造、历史交互传递等实现细节高度敏感，导致排行榜排名不可靠。同时，使用强化学习（RL）训练工具调用存在显著的计算浪费：rollout阶段许多提示不产生学习信号，策略更新阶段优化成本高昂。
- **整体含义**：本文从**有效性**（如何测量工具调用能力）和**效率**（如何学习工具调用能力）两个互补维度系统研究，旨在推动评估标准化并加速RL训练，为构建更稳健、高效的LLM代理提供指导。

---

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：  
  1. 对工具调用评估管线进行系统性敏感性分析，识别出导致评估结果差异的关键实现细节。  
  2. 针对RL训练中的计算浪费，设计两种加速技术，在不降低性能的前提下实现显著的端到端加速。

- **关键技术细节**（根据摘要推断，无完整算法流程）：  
  - **评估管线敏感性分析**：控制变量实验，逐一改变随机种子、系统提示、多轮模板构造方式、历史交互传递策略，量化各因素对最终性能的影响。  
  - **RL训练加速技术**：  
    - 可能通过过滤掉不产生学习信号的rollout样本，减少无效计算；  
    - 优化策略更新阶段的计算效率（例如减少不必要的梯度计算或采用更高效的优化器调度）。

- **公式或算法流程**：论文未提供具体公式，仅通过文字描述上述策略。

---

### 3. 实验设计

- **使用的数据集/场景**：摘要未明确列出具体数据集名称，仅提到“多轮设置”（multi-turn settings）。通常工具调用评估可能涉及Typical Benchmarks（如ToolBench、ToolLlama等），但此处无具体信息。
- **Benchmark**：未指明。
- **对比方法**：未明确说明，但从方法论推测，对比了标准RL训练与作者提出的加速RL变体，以及不同评估管线配置下的性能差异。

---

### 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等。仅指出RL训练存在计算浪费，并提出了加速技术，但未公开具体算力细节。因此无法量化资源消耗。

---

### 5. 实验数量与充分性

- **实验数量**：论文系统分析了多个实现细节（随机种子、系统提示、多轮模板、历史传递），每个维度至少进行了控制变量实验，但未给出具体实验组数。  
- **充分性与客观性**：  
  - **优点**：覆盖了评估管线的主要敏感因素，且关注多轮设置（更贴近真实代理交互场景）。  
  - **不足**：缺乏具体数据集、基准方法、消融实验的量化结果，无法判断实验是否全面覆盖不同模型、不同任务类型；未对比其他加速RL方法；未提及统计置信区间和多次重复实验的细节。

---

### 6. 论文的主要结论与发现

- 工具调用的评估结果对随机种子、系统提示、多轮模板构造、历史交互传递等看似微小的实现细节高度敏感，导致排行榜排名不可靠。  
- 标准RL训练在工具调用中存在显著的计算浪费（rollout和策略更新两个阶段）。  
- 提出的两种加速技术能实现显著的端到端加速（wall-clock speedup）且不降低性能。  
- 需要标准化工具调用评估流程，同时RL训练可以有效提升工具调用效率。

---

### 7. 优点

- **问题聚焦**：同时关注评估标准化和训练效率两个关键问题，实用性强。  
- **系统性分析**：对评估管线进行多维敏感性分析，揭示了容易被忽视的噪声来源，有助于社区建立更严谨的评估协议。  
- **实用技术**：提出的RL加速方法直接面向训练成本痛点，具有实际应用价值。  
- **动机清晰**：明确指出现有评估不可靠、RL训练浪费的问题，并给出解决方案。

---

### 8. 不足与局限

- **实验细节缺失**：未提供完整的数据集、基准、模型规格、消融实验设计，结论的可复现性较低。  
- **领域覆盖有限**：可能仅针对特定类型的工具调用任务（如API调用或代码执行），未讨论更广泛的代理场景（如多工具协作）。  
- **未公开算力**：无法评判加速比的绝对量级及与现有方法相比的效率提升。  
- **未讨论局限性**：摘要中未提及方法可能存在的适用边界（例如对模型大小、推理链长度的敏感度）。  
- **没有与现有方法全面对比**：仅提及“标准RL”，未与SOTA RL for tool-calling（如ReAct, Reflexion等）的基线对比。

（完）
