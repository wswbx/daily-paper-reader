---
title: An AI System for Autonomous Algorithm Evolution in Drug Development
title_zh: 用于药物开发中自主算法进化的人工智能系统
authors: "Zhou, Z., Nan, Y., Mou, M., Qian, Y., Liu, Y., Zuo, Z., Yang, H., Xu, W., Li, B., Jiang, W., Ren, Y., Liao, Y., Wang, Y., Li, Y., Yang, Q., Xi, Z., Mi, T., Sun, H., Liu, P., Zhu, F."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.16.745117v1.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 药物研发中的自主算法演化多角色LLM闭环系统
tldr: 药物开发中的AI算法依赖专家设计和任务特定优化，难以跨阶段协同提升。DrugEvolve多角色大语言模型系统融合研究员、工程师、分析师角色，实现闭环自主演化，对算法进行迭代设计、实现、评估与优化。在覆盖靶点识别、药物发现、临床前及临床研究的11项任务、120个基准测试集上取得性能显著提升，并泛化至生物序列、图、分子拓扑及文本等异构数据模态。该系统不仅作为药物开发算法基础设施，也为更广泛科学领域提供可迁移范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 药物开发中AI算法依赖专家设计和任务特定优化，难以实现跨任务、跨阶段的协同提升，需要自主演化机制。
method: 提出DrugEvolve，融合研究员、工程师、分析师角色的多角色大语言模型，实现算法设计、实现、评估与优化的闭环自主演化。
result: 在11项任务、120个基准测试集上显著提升性能，并泛化至生物序列、图、分子拓扑及文本等异构数据模态，在预测和生成任务中均有效。
conclusion: DrugEvolve可作为药物开发的算法基础设施，并为更广泛科学领域提供可迁移的自主演化范式。
---

## 摘要
人工智能（AI）正日益渗透到药物开发流程中。人们已经构建了众多用于加速这一多阶段、多任务过程的算法，而这些算法高度依赖于专家设计和劳动密集型的特定任务优化。鉴于AI驱动的药物开发加速被认为是跨多个阶段的累积效应，往往具有协同作用，因此需要在整个流程中实现现有算法的自主进化，以获得整体性的进展。在此，我们提出了DrugEvolve，一个用于药物开发中系统性和自主算法进化的多角色大语言模型系统。DrugEvolve通过整合研究者（Researcher）、工程师（Engineer）和分析师（Analyst）领域，实现了闭环进化过程，并利用科学知识和累积的进化经验，实现了算法的迭代设计、实施、评估和优化。在涵盖靶点识别、药物发现、临床前研究和临床试验的十一个代表性任务中，DrugEvolve自主进化出相应的任务特定算法，并在120个基准测试集上实现了显著的性能提升。此外，它在异构数据模态（从生物序列和图到分子拓扑和文本语言）中表现出强大的泛化能力，并在预测和生成任务中都取得了增益。总的来说，这一AI系统不仅可作为药物开发的算法基础设施，还可作为更广泛科学领域的可迁移范式。

## Abstract
Artificial intelligence (AI) is increasingly permeating the drug development pipeline. Numerous algorithms for accelerating this multi-stage and multi-task process have been constructed, which depends heavily on expert design and labor-intensive task-specific optimization. Given that AI-driven acceleration of drug development is recognized as a cumulative, often synergistic, effect across multiple stages, the autonomous evolution of existing algorithms across the entire pipeline is demanded to achieve a holistic advancement. Here, we present DrugEvolve, a multi-role large language model system for systematic and autonomous algorithm evolution in drug development. DrugEvolve realizes a closed-loop evolution process by incorporating Researcher, Engineer, and Analyst domains, and enables an iterative design, implementation, evaluation, and refinement of algorithm by leveraging scientific knowledge and accumulated evolutionary experience. Across eleven representative tasks spanning target identification, drug discovery, preclinical study, and clinical trial, DrugEvolve autonomously evolved the corresponding task-specific algorithms and achieved substantial performance enhancement on 120 benchmark test sets. Moreover, it showed robust generalizabilities across heterogeneous data modalities (ranging from biological sequence and graph to molecular topology and textual language), and realized gains in both predictive and generative tasks. Collectively, this AI system can serve not only as an algorithmic infrastructure for drug development, but also as a transferable paradigm for broader scientific domains.

---

## 论文详细总结（自动生成）

# 论文总结：DrugEvolve — 药物开发中的自主算法进化 AI 系统

## 1. 核心问题与整体含义

- **背景**：人工智能已广泛渗透到药物开发的多个阶段（靶点识别、药物发现、临床前研究、临床试验），但现有算法高度依赖专家手工设计，且需要针对特定任务进行劳动密集型的优化。
- **核心问题**：药物开发中的 AI 加速效应是跨阶段累积且协同的，但当前缺乏一种机制让算法在整个流程中自主进化，以实现整体性的性能提升。
- **整体含义**：提出一个能够自主迭代设计、实现、评估和优化算法的 AI 系统，从而将药物开发中的算法研发从“人工驱动”转变为“自主进化驱动”。

## 2. 方法论

- **系统名称**：DrugEvolve —— 一个多角色（multi-role）大语言模型（LLM）系统。
- **核心思想**：通过模拟科研团队中的三种角色，形成闭环进化过程：
  - **研究者（Researcher）**：负责生成科学假设、提出算法设计方案。
  - **工程师（Engineer）**：负责将设计转化为可运行的代码实现。
  - **分析师（Analyst）**：负责对算法进行评估、诊断问题并提出优化方向。
- **闭环流程**：迭代执行“设计 → 实现 → 评估 → 优化”，每一轮进化都会利用科学知识库和上一轮累积的进化经验，逐步改进算法。
- **技术特点**：并非针对单个任务进行手工调优，而是让系统在统一框架下自主适应不同任务和数据模态。

## 3. 实验设计

- **任务覆盖**：涵盖药物开发的四个关键阶段 —— 靶点识别、药物发现、临床前研究、临床试验。
- **任务数量**：共 11 个代表性任务。
- **基准测试**：在 120 个基准测试集上进行了性能验证。
- **数据模态**：包括生物序列、图结构、分子拓扑、文本语言等异构数据模态。
- **任务类型**：同时覆盖预测任务（如属性预测）和生成任务（如分子生成）。
- **对比方法**：摘要中未明确列出具体对比的基线算法，但根据“自主进化并显著提升性能”的表述，推测是与各任务原有专用算法或初始版本的算法进行了对比。

## 4. 资源与算力

- 原文摘要**未提及** GPU 型号、数量、训练时长、电能消耗等具体算力信息。
- 仅能推断：由于涉及多个 LLM 角色的迭代调用和 120 个基准测试集的评估，其计算开销可能较大，但论文未公开详细资源需求。

## 5. 实验数量与充分性

- **实验规模**：11 个任务 × 120 个基准测试集，覆盖多种模态和生成/预测两类任务，规模较大，具有较好的广度。
- **充足性评估**：
  - 从摘要看，实验覆盖面广，能够证明系统的跨任务、跨模态泛化能力。
  - 但摘要未提及消融实验（如去除某个角色的影响）、对进化轮次的敏感性分析、与人工专家设计算法的对比、统计显著性检验等细节，因此**无法完全判断实验的深度和公平性**。
  - 如果论文正文中补充了上述细节，则充分性会更高；仅凭摘要，尚不足以全面评估。

## 6. 主要结论与发现

- DrugEvolve 能在 11 个代表性任务、120 个基准测试集上实现**显著的性能提升**。
- 系统对**异构数据模态**（生物序列、图、分子拓扑、文本）具有较强的泛化能力。
- 在**预测任务和生成任务**中均能获得增益，说明该方法具有通用性。
- 作者认为该 AI 系统不仅可作为药物开发的算法基础设施，还能作为更广泛科学领域可迁移的自主进化范式。

## 7. 优点

- **创新性**：首次（从摘要推断）将多角色 LLM 协同用于药物开发算法的自主进化，而非单任务优化。
- **闭环自主性**：融合设计、实现、评估、优化于同一系统，减少人工干预。
- **可迁移性**：跨模态、跨任务、跨阶段的一致改进，说明方法具有较强的通用性。
- **应用价值**：有望降低药物开发中 AI 算法的研发成本，加速药物研发进程。

## 8. 不足与局限

- **信息不透明**：
  - 未报告计算资源（GPU 等），难以评估实际使用门槛。
  - 未报告具体基准测试集名称、数据规模、各任务提升幅度，可复现性受限。
- **对比可能不够充分**：
  - 未明确给出与最先进基线（state-of-the-art）或人工专家设计算法的详细对比，无法判断优势的真实幅度。
- **潜在偏差风险**：
  - 多角色 LLM 系统依赖大模型输出，可能存在幻觉或生成无效算法，摘要未提及失败案例或鲁棒性分析。
  - 120 个测试集全部来自单一框架下的自主进化，是否存在过拟合或评估标准偏差需进一步验证。
- **应用限制**：
  - 药物开发涉及严格的生物学验证与监管要求，算法层面的提升不一定能直接转化为临床疗效或获批药物；摘要未讨论实际湿实验验证。
  - 系统进化出的算法可解释性不明，对人类专家审校构成挑战。

---

**说明**：本总结基于论文摘要和元数据撰写，部分细节（如具体实验配置、算力、基线方法）在摘要中未提供，若需完整评估，应查阅论文全文。

（完）
