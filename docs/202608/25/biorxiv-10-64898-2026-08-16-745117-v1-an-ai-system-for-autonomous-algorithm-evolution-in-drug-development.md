---
title: An AI System for Autonomous Algorithm Evolution in Drug Development
title_zh: 用于药物开发中自主算法进化的人工智能系统
authors: "Zhou, Z., Nan, Y., Mou, M., Qian, Y., Liu, Y., Zuo, Z., Yang, H., Xu, W., Li, B., Jiang, W., Ren, Y., Liao, Y., Wang, Y., Li, Y., Yang, Q., Xi, Z., Mi, T., Sun, H., Liu, P., Zhu, F."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.16.745117v1.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 药物研发中多角色大语言模型驱动的自主算法进化，契合自主研究主题
tldr: 药物开发算法通常依赖专家设计与任务特定优化，难以实现跨阶段的协同加速。DrugEvolve作为多角色大语言模型系统，整合研究员、工程师和分析师角色，形成设计-实现-评估-细化的闭环，驱动算法自主进化。在11个任务、120个基准测试集上取得显著提升，并跨序列、图、拓扑、文本等异构数据模态和预测/生成任务展现泛化能力。该系统可作为药物开发的算法基础设施，也为更广泛科学领域提供可迁移的演化范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AI算法依赖专家设计与任务特定优化，难以协同加速药物开发全流程，亟需自主进化机制。
method: DrugEvolve整合研究员、工程师、分析师多角色，形成设计-实现-评估-细化闭环，驱动算法自主迭代进化。
result: 在11个任务、120个基准测试集上性能显著提升，并跨序列、图、拓扑、文本等数据模态及预测/生成任务展现出泛化能力。
conclusion: 该系统可作为药物开发算法基础设施，也为更广泛科学领域提供可迁移的自主演化范式。
---

## 摘要
人工智能（AI）正日益渗透到药物开发流程中。人们已经构建了许多用于加速这一多阶段、多任务过程的算法，这些算法在很大程度上依赖于专家设计和劳动密集型的特定任务优化。鉴于AI驱动的药物开发加速被认为是在多个阶段上累积的、通常具有协同效应的，因此需要对整个流程中的现有算法进行自主进化，以实现整体推进。在此，我们提出了DrugEvolve，一个用于药物开发中系统性和自主算法进化的多角色大语言模型系统。DrugEvolve通过整合研究员、工程师和分析师领域，实现了闭环进化过程，并利用科学知识和积累的进化经验，实现了算法的迭代设计、实现、评估和优化。在涵盖靶点识别、药物发现、临床前研究和临床试验的十一个代表性任务中，DrugEvolve自主进化了相应的任务特定算法，并在120个基准测试集上实现了显著的性能提升。此外，它在异构数据模态（从生物序列、图形到分子拓扑和文本语言）上表现出强大的泛化能力，并在预测和生成任务中都实现了增益。总的来说，这个AI系统不仅可以作为药物开发的算法基础设施，也可以作为更广泛科学领域的可迁移范式。

## Abstract
Artificial intelligence (AI) is increasingly permeating the drug development pipeline. Numerous algorithms for accelerating this multi-stage and multi-task process have been constructed, which depends heavily on expert design and labor-intensive task-specific optimization. Given that AI-driven acceleration of drug development is recognized as a cumulative, often synergistic, effect across multiple stages, the autonomous evolution of existing algorithms across the entire pipeline is demanded to achieve a holistic advancement. Here, we present DrugEvolve, a multi-role large language model system for systematic and autonomous algorithm evolution in drug development. DrugEvolve realizes a closed-loop evolution process by incorporating Researcher, Engineer, and Analyst domains, and enables an iterative design, implementation, evaluation, and refinement of algorithm by leveraging scientific knowledge and accumulated evolutionary experience. Across eleven representative tasks spanning target identification, drug discovery, preclinical study, and clinical trial, DrugEvolve autonomously evolved the corresponding task-specific algorithms and achieved substantial performance enhancement on 120 benchmark test sets. Moreover, it showed robust generalizabilities across heterogeneous data modalities (ranging from biological sequence and graph to molecular topology and textual language), and realized gains in both predictive and generative tasks. Collectively, this AI system can serve not only as an algorithmic infrastructure for drug development, but also as a transferable paradigm for broader scientific domains.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

- **研究背景**：人工智能正加速渗透到药物开发全流程，涵盖靶点识别、药物发现、临床前研究及临床试验等多个阶段。目前已构建了大量针对特定任务的AI算法，但这些算法高度依赖专家的人工设计与劳动密集型的任务特定优化。
- **核心问题**：药物开发的AI加速通常被认为是一个多阶段累积、且往往具有协同效应的整体过程。然而，现有算法各自独立、缺乏跨阶段的协同进化机制，难以实现整个流程的"整体推进"。
- **整体含义**：论文提出了一种全新的范式——让算法在药物开发全流程中实现**自主进化**，而非依赖人工逐任务优化。这一方向不仅针对药物开发本身，更试图树立一个可迁移至更广泛科学领域的AI驱动算法自主演化范式。

## 2. 论文提出的方法论

- **核心思想**：构建一个多角色大语言模型系统 **DrugEvolve**，通过模拟科研团队中不同角色的分工协作，实现算法的闭环自主进化，摆脱对人类专家逐任务调优的依赖。
- **三大角色域**：
  - **研究员（Researcher）**：负责基于科学知识和已有文献提出算法改进方向与设计思路。
  - **工程师（Engineer）**：负责将设计思路转化为可运行的代码实现，完成算法的具体落地。
  - **分析师（Analyst）**：负责评估算法性能、诊断问题，并将评估结果反馈给前序环节。
- **闭环进化流程**：设计（Design）→ 实现（Implementation）→ 评估（Evaluation）→ 细化（Refinement）→ 再设计，如此循环迭代，实现算法的逐步自主优化。
- **关键机制**：系统不仅依赖大语言模型自身的科学知识，还累积了历次进化过程中获得的"进化经验"，并将其用于指导后续的算法设计迭代，从而实现跨轮次的持续进步。

## 3. 实验设计

- **任务覆盖**：涵盖药物开发全流程的 **11 个代表性任务**，具体分布在四个阶段中：
  - 靶点识别
  - 药物发现
  - 临床前研究
  - 临床试验
- **基准规模**：在 **120 个基准测试集**上进行了系统评估。
- **数据模态**：覆盖了多种异构数据模态，包括：
  - 生物序列（如蛋白质/基因序列）
  - 图结构（如分子图、化合物结构图）
  - 分子拓扑（如分子指纹/拓扑描述符）
  - 文本语言（如生物医学文献、临床试验文本）
- **任务类型**：同时覆盖 **预测型任务**（如性质预测、相互作用预测）和 **生成型任务**（如分子生成、序列设计）。
- **对比情况**：由于提供的文本内容有限，论文摘要中未详细列出具体的基线方法名称。但可合理推断，对比对象应当是各任务上已有的、专家设计的SOTA（state-of-the-art）算法或标准基准方法。实际论文全文应包含详细的对比实验表格。

## 4. 资源与算力

- 在提供的元数据和摘要文本中，**未明确说明**实验所使用的具体算力资源，包括：
  - GPU 型号（如 A100、H100 等）与数量
  - 训练或推理总时长
  - 大语言模型的参数规模
  - 进化迭代的总轮数或总计算消耗
- 这一信息的缺失在论文中通常属于实验设置的补充细节，若要评估该系统的可复现性和实际部署成本，需要查阅论文全文的实验设置部分或补充材料。

## 5. 实验数量与充分性

- **实验规模**：从数量上看，覆盖 11 个任务 × 120 个基准测试集，并且横跨 4 种数据模态和 2 种任务类型（预测 + 生成），实验体量较大、覆盖面广泛。
- **充分性评估**：
  - ✅ **覆盖面好**：任务与数据模态的多样性较强，能较好地验证系统在不同场景下的泛化能力。
  - ✅ **结果一致性**：在 120 个基准测试集上均取得显著性能提升，说明方法的有效性不是偶然的。
  - ⚠️ **可能的不足**：从摘要中无法确认是否存在以下验证手段——消融实验（如移除某个角色域的影响）、不同初始算法条件下的进化对比、与人工专家优化算法的直接成本/收益对比等。若缺少这些实验，结论的因果归因可能不够严谨。
  - ⚠️ **公平性**：论文声称"自主进化提升了现有算法"，但提升幅度、方差和显著性检验的细节需要进一步确认。另外，是否在评估过程中避免了数据泄漏（如进化过程中意外接触测试集信息）也是关键的严谨性考量。

## 6. 论文的主要结论与发现

- **核心结论**：DrugEvolve 作为一个多角色大语言模型系统，能够以闭环方式自主进化药物开发各阶段的任务特定算法，并且在 11 个任务、120 个基准测试集上产生了显著且一致的性能提升。
- **泛化能力**：系统不仅在单一类型任务上有效，还展现了跨数据模态（序列、图、拓扑、文本）和跨任务类型（预测、生成）的稳健泛化能力。
- **应用价值**：
  - 可作为药物开发的**算法基础设施**，持续为全流程提供更优算法；
  - 也可作为**可迁移的演化范式**，为其他科学领域中算法自主迭代提供模板。

## 7. 优点

- **问题选择富有战略意义**：瞄准药物开发全流程的协同加速需求，而非单一任务优化，具有更宏观的实际意义。
- **多角色协作机制新颖**：将大语言模型在科研过程中的角色细分（研究员、工程师、分析师），模仿人类团队协作模式，设计合理且具有解释性。
- **闭环迭代设计**：通过"设计-实现-评估-细化"的闭环结构，使算法进化具有持续性和自我改进能力，而非一次性输出。
- **广泛而系统的验证**：实验覆盖了 11 个任务、120 个基准测试集，横跨多种数据模态与任务类型，验证了方法的通用性，研究说服力较强。
- **"经验累积"机制**：利用进化过程中积累的历史经验来指导后续迭代，使每一次进化不只是孤立的尝试，而是递进式的累积改进。
- **范式的可迁移性**：不仅服务于药物开发，还提出了一个通用的"AI 自主演化算法"框架，具有跨领域启发性。

## 8. 不足与局限

- **计算成本不透明**：多角色大语言模型多轮迭代调用的计算开销可能非常庞大，但摘要中未披露相关算力消耗，实际部署的可行性和经济性亟待评估。
- **对基础模型能力的依赖**：进化效果高度依赖底层大语言模型的科学推理与代码生成能力。若更换更弱的基座模型，系统表现可能大幅下降，鲁棒性未经验证。
- **缺少与人类专家的对比分析**：未明确说明系统进化出的算法与人类专家设计并优化的算法在成本、效率和质量上的综合对比。"自主"不等于"更好"，需要更精细的成本-收益分析。
- **缺乏消融分析**：从摘要中无法获知三大角色缺一不可的证据——例如，去掉"工程师"改用预置代码库是否仍能取得同样效果？各角色的贡献度如何？这些问题需要消融实验来回答。
- **潜在的评估偏差风险**：需要确认算法进化过程中是否严格隔离了测试数据，以及大语言模型是否可能已通过预训练"见过"部分基准数据集，从而导致评估结果虚高。
- **真实世界验证不足**：论文中的评估以公开基准测试集为准，能否在真实药物开发项目中（如临床前实验、真实患者数据）复现增益，仍有待进一步确认。
- **关于临床前与临床试验的实际意义有限**：临床阶段的加速最终需要动物实验和人体验证，计算上的性能提升并不能直接等同于临床成功率提高，这在整体应用中应理性看待。

（完）
