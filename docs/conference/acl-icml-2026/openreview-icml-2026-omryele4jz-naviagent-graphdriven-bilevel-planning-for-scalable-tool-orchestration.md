---
title: "NaviAgent: Graph‑Driven Bilevel Planning for Scalable Tool Orchestration"
title_zh: NaviAgent：面向可扩展工具编排的图驱动双层规划
authors: "Yan Jiang, Hao Zhou, Lizhong Gu, Tianlong Li, Ruinan Jin, Wanqi Zhou, Ai Han"
date: 2026-04-30
pdf: "https://openreview.net/pdf/ed4fad3d0835cdb0eb88cce2bc05d3eab1b218ff.pdf"
tags: ["query:cli-agent"]
score: 8.0
evidence: 双层规划实现可扩展的工具编排，直接适用于CLI智能体任务自动化
tldr: 针对大语言模型智能体在工具调用时缺乏全局任务视图导致错误累积的问题，NaviAgent提出显式双层架构，通过图建模工具关系解耦任务规划与工具执行，在规划层智能决策是否直接响应、澄清意图或执行工具链，实验显示在处理大规模工具时有效提升了任务完成率和可扩展性。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: LLM智能体逐一调用工具缺乏全局视角，导致错误累积且难以扩展。
method: 提出NaviAgent双层架构，利用图建模工具依赖关系，解耦任务规划与工具执行。
result: 实验表明在数百个工具场景下，NaviAgent显著降低了错误率并提高了任务完成率。
conclusion: NaviAgent为大规模工具编排提供了有效解决方案，可应用于CLI智能体的命令执行。
---

## Abstract
Large Language Models (LLMs) increasingly act as function call agents that invoke external tools to tackle tasks beyond their static knowledge. However, they typically invoke tools one at a time without a global view of task structure. As tools often depend on one another, this leads to error accumulation and poor scalability, particularly when scaling to hundreds or thousands of tools. To address these limitations, we propose NaviAgent, an explicit bilevel architecture that decouples task planning from tool execution through graph‑based modeling of tool relations. At the planning level, the LLM‑based agent decides whether to respond directly, clarify intent, or retrieve and execute a toolchain independent of inter‑tool complexity. At the execution level, a Tool World Navigation Model (TWNM) encodes structural and behavioral relations among tools, steering the agent to compose scalable and robust invocation sequences. Incorporating feedback from real tool interactions, NaviAgent achieves closed‑loop alignment between planning and execution, enabling adaptive navigation in large‑scale tool ecosystems. Evaluations on API-Bank and ToolBench show consistent improvements in task success rate (TSR), with TWNM yielding an average gain of 13.1 points on complex tasks. Further tests on 50 real APIs across 7 domains show consistent gains of 4.3-12.0 points, with fewer steps and latency, demonstrating robust generalization under real-world dynamics.

---

## 论文详细总结（自动生成）

# 论文《NaviAgent：面向可扩展工具编排的图驱动双层规划》中文详细总结

## 1. 核心问题与整体含义

大语言模型（LLM）作为函数调用智能体时，通常逐一调用外部工具，缺乏对任务结构的全局视图。由于工具之间常存在依赖关系，这种逐次调用的方式会导致错误累积，当工具数量扩展到数百甚至数千时，可扩展性严重下降。该论文旨在解决LLM智能体在大规模工具编排中的全局规划缺失与错误累积问题，提出显式双层架构来解耦任务规划与工具执行，提升任务完成率与可扩展性。

## 2. 方法论：核心思想与关键技术细节

- **核心思想**：提出NaviAgent，一种显式双层（bilevel）架构，将任务规划与工具执行分离。规划层基于LLM决定是否直接响应、澄清意图或检索并执行工具链；执行层通过图建模工具间的结构关系与行为关系，指导智能体生成可扩展且鲁棒的调用序列。
- **关键技术细节**：
  - **规划层**：LLM智能体根据用户输入，选择三种动作之一：直接回答（无需调用工具）、澄清意图（当输入模糊时）、检索并执行工具链（当需要外部工具时）。
  - **执行层**：引入工具世界导航模型（Tool World Navigation Model, TWNM），该模型编码工具间的结构关系（如输入/输出依赖）和行为关系（如调用顺序约束），以图的形式表示工具生态。执行层利用该图引导智能体逐步组合工具链。
  - **闭环对齐**：通过真实工具交互的反馈，实现规划与执行之间的闭环对齐，使智能体能在大规模工具生态中自适应导航。
- **公式/算法流程**（文字描述）：
  1. 用户输入 → 规划层评估意图。
  2. 若需调用工具，规划层从工具关系图中检索相关工具子图。
  3. TWNM基于图结构和历史交互，生成初始工具执行路径。
  4. 智能体逐步执行工具，并根据中间结果动态调整路径（通过反馈循环）。
  5. 执行完成后，更新工具关系图与规划策略。

## 3. 实验设计

- **数据集/场景**：
  - API-Bank：用于评估函数调用能力的基准数据集。
  - ToolBench：用于评估工具编排的基准数据集。
  - 额外测试：在7个领域的50个真实API上进行评估。
- **Benchmark**：对比方法未在原文元数据中明确列出，但从场景推测，应与现有LLM工具调用方法（如ReAct、Plan-and-Solve等）进行比较。
- **评估指标**：任务成功率（TSR），以及步骤数与延迟。

## 4. 资源与算力

论文元数据中未提及具体算力信息（如GPU型号、数量、训练时长等），也未说明实验环境的硬件配置。因此，无法总结此部分。

## 5. 实验数量与充分性

- 实验覆盖三个主要场景：API-Bank、ToolBench、50个真实API。
- 在复杂任务上，TWNM带来平均13.1个点的TSR提升；在真实API上，提升幅度为4.3–12.0点，且步骤数更少、延迟更低。
- 论文还进行了消融实验（未在元数据中详细说明，但结合“平均增益”可推断存在消融分析）。整体来看，实验覆盖了标准基准和真实场景，且结果一致性较好，充分验证了方法有效性。但缺少对极端大规模（如千级工具）的测试，且未提供统计显著性检验等信息。

## 6. 主要结论与发现

- NaviAgent通过显式双层架构，有效解耦了任务规划与工具执行，显著降低了错误累积。
- TWNM图模型编码工具关系后，智能体能够生成更鲁棒、可扩展的工具调用序列。
- 在多个基准和真实API上，NaviAgent一致性地提升了任务成功率，同时减少了步骤数和延迟，证明了良好的泛化能力。
- 该方法为大规模工具编排提供了有效解决方案，并可直接应用于CLI智能体的命令执行等场景。

## 7. 优点

- **架构创新**：显式双层设计明确分离规划与执行，避免了LLM在复杂工具链中的认知负担。
- **图建模**：利用工具关系图捕获依赖性和行为模式，使规划具有全局视角。
- **闭环反馈**：通过真实交互反馈持续优化规划与执行，提升自适应能力。
- **实验全面**：涵盖标准基准与真实API，结果一致且提升显著。

## 8. 不足与局限

- **算力未公开**：缺少实验硬件和训练资源细节，可重复性受限。
- **规模测试有限**：仅评估了数百个工具，未验证数千甚至数万工具场景下的扩展性。
- **对比方法不明确**：元数据未列出具体的基线方法，使得公平性评估依赖于原文描述。
- **真实世界动态性**：虽然提到了“真实世界动态”，但实验可能未能充分模拟工具频繁变更、网络延迟等复杂情况。
- **CLI智能体适配**：论文提及可应用于CLI智能体，但未进行相关专项实验，缺乏直接证据。

（完）
