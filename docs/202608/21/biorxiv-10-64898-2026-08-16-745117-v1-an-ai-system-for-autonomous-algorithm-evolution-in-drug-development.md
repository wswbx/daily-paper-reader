---
title: An AI System for Autonomous Algorithm Evolution in Drug Development
title_zh: 用于药物开发中自主算法进化的人工智能系统
authors: "Zhou, Z., Nan, Y., Mou, M., Qian, Y., Liu, Y., Zuo, Z., Yang, H., Xu, W., Li, B., Jiang, W., Ren, Y., Liao, Y., Wang, Y., Li, Y., Yang, Q., Xi, Z., Mi, T., Sun, H., Liu, P., Zhu, F."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.16.745117v1.full.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 多角色大语言模型系统实现药物研发中的自主算法演化
tldr: 现有药物研发算法依赖专家设计和任务特化优化，难以实现全流程协同进化。DrugEvolve通过研究者、工程师、分析师三种角色的多智能体大语言模型系统，实现算法设计、实现、评估和优化的闭环自主进化。在11个代表性任务和120个基准测试集上显著提升性能，并展现出跨数据模态和预测/生成任务的泛化能力。该系统为药物研发提供算法基础设施，也为更广泛科学领域提供可迁移范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 药物研发各阶段算法依赖专家设计与任务特定优化，缺乏跨阶段自主进化能力，亟需系统性方法实现全流程协同提升。
method: DrugEvolve构建多角色大语言模型系统，融合研究者、工程师、分析师角色，形成设计、实现、评估、优化的闭环进化机制。
result: 在涵盖药物研发全流程的11个任务、120个基准测试集上实现显著性能提升，并验证了跨模态与跨任务类型的泛化能力。
conclusion: DrugEvolve可作为药物研发的算法基础设施，其自主进化范式可迁移至其他科学领域，推动AI驱动的系统性创新。
---

## 摘要
人工智能正日益渗透到药物开发流程中。人们已经构建了许多用于加速这一多阶段、多任务过程的算法，而这些算法在很大程度上依赖于专家设计和劳动密集型的特定任务优化。鉴于人工智能驱动的药物开发加速被认为是跨多个阶段的累积效应，通常是协同效应，因此需要在整个流程中实现现有算法的自主进化，以实现整体进步。在此，我们提出了DrugEvolve，一个多角色大语言模型系统，用于药物开发中系统化、自主的算法进化。DrugEvolve通过整合研究员、工程师和分析师领域，实现了闭环进化过程，并利用科学知识和积累的进化经验，实现了算法的迭代设计、实现、评估和改进。在涵盖靶点识别、药物发现、临床前研究和临床试验的十一项代表性任务中，DrugEvolve自主进化了相应的任务特定算法，并在120个基准测试集上实现了显著的性能提升。此外，它在异构数据模态（从生物序列和图到分子拓扑和文本语言）中展现出强大的泛化能力，并在预测和生成任务中均实现了增益。总的来说，这一人工智能系统不仅可以作为药物开发的算法基础设施，也可以作为更广泛科学领域的可迁移范式。

## Abstract
Artificial intelligence (AI) is increasingly permeating the drug development pipeline. Numerous algorithms for accelerating this multi-stage and multi-task process have been constructed, which depends heavily on expert design and labor-intensive task-specific optimization. Given that AI-driven acceleration of drug development is recognized as a cumulative, often synergistic, effect across multiple stages, the autonomous evolution of existing algorithms across the entire pipeline is demanded to achieve a holistic advancement. Here, we present DrugEvolve, a multi-role large language model system for systematic and autonomous algorithm evolution in drug development. DrugEvolve realizes a closed-loop evolution process by incorporating Researcher, Engineer, and Analyst domains, and enables an iterative design, implementation, evaluation, and refinement of algorithm by leveraging scientific knowledge and accumulated evolutionary experience. Across eleven representative tasks spanning target identification, drug discovery, preclinical study, and clinical trial, DrugEvolve autonomously evolved the corresponding task-specific algorithms and achieved substantial performance enhancement on 120 benchmark test sets. Moreover, it showed robust generalizabilities across heterogeneous data modalities (ranging from biological sequence and graph to molecular topology and textual language), and realized gains in both predictive and generative tasks. Collectively, this AI system can serve not only as an algorithmic infrastructure for drug development, but also as a transferable paradigm for broader scientific domains.