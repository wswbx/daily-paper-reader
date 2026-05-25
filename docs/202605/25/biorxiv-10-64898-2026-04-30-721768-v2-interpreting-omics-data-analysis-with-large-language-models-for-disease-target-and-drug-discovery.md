---
title: Interpreting Omics Data Analysis with Large Language Models for Disease Target and Drug Discovery
title_zh: 利用大型语言模型解释组学数据分析以进行疾病靶点和药物发现
authors: "XU, Z., Chen, W., Ren, W., Xu, T., Amaechin, S., Khan, R., Chen, Y., Province, M., Payne, P., Li, F."
date: 2026-05-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.30.721768v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 大语言模型用于组学数据解释助力药物发现
tldr: 本文提出一个溯源感知的Text-to-Target框架，结合模式约束的大语言模型检索与数值组学数据分析，通过模态感知融合将候选分为锚点、隐藏中心和新兴节点，并在拓扑约束下生成假设与策略。在阿尔茨海默病和胰腺导管癌中验证，分别获得34和75个基因候选集及相应策略，策略保留完整溯源，实现端到端可审计性，为靶点发现提供了可转移的融合架构。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有大语言模型虽能快速检索疾病机制，但文本输出缺乏队列特异性定量证据，无法可靠用于靶点和药物优先排序。
method: 提出溯源感知的Text-to-Target框架，通过模式约束多模型LLM检索与组学分析结合，进行模态感知融合（锚点、隐藏中心、新颖节点），在拓扑约束下分阶段生成假设与策略。
result: 在胰腺导管癌中生成75基因候选集和23个策略，阿尔茨海默病中生成34基因候选集和14个策略，策略均保留完整溯源闭环，支持端到端审计。
conclusion: 该框架证明组学证据可约束生物活性，LLM检索扩展机制空间，网络感知融合保持可解释性，为双疾病靶点优先排序和文献-机制持续一致性提供可转移的发现架构。
---

## 摘要
在生物医学科学发现中，综合文献中的先验知识是解释数值组学数据分析以识别疾病靶点和药物发现的重要组成部分。大型语言模型（LLMs）可以快速从生物医学文本中检索疾病机制，但仅文本输出是通用的，且在没有队列特定定量证据的情况下，对于靶点和药物优先级排序不可靠。在此，我们提出了一种带有来源感知的Text-to-Target框架，将模式约束的多模型LLM检索与数值组学数据分析相结合。关键设计是一个模态感知融合步骤：候选被划分为重叠支持的锚点、仅检索隐藏枢纽和网络涌现的新颖节点，然后在拓扑约束下传播到分阶段假设和策略生成。我们在阿尔茨海默病（AD）和胰腺导管腺癌（PDAC）中评估了该模型。在PDAC中，工作流产生了均衡的75基因候选集和23策略组合，在靶点水平和策略水平上都有显著的DepMap支持。在AD中，更严格的候选控制产生了紧凑的34基因集和14个策略；在扩展的CRISPRbrain注册表下，靶点水平轴均显著，且策略水平富集度高。在两种疾病中，最终策略保持了与候选池的完整来源闭合，实现了从检索伪像到验证输出的端到端可审计性。这些结果支持一种可转移的发现架构，其中组学证据约束生物活性，LLM检索扩展机制搜索空间，网络感知融合保持可解释性。该框架为双疾病靶点优先级排序提供了可重复的基础，并激励与智能体证据刷新循环的持续文献-机制一致性。

## Abstract
In biomedical scientific discovery, synthesizing prior knowledge from the literature is an essential component of interpreting numerical omics data analyses for disease target identification and drug discovery. Large language models (LLMs) alone can rapidly retrieve disease mechanisms from biomedical text, but text-only outputs are general and unreliable for target and drug prioritization without cohort-specific quantitative evidence. Herein, we propose a provenance-aware Text-to-Target framework that couples schema-constrained multi-model LLM retrieval with numeric omics data analysis. The key design is a modality-aware fusion step: candidates are partitioned into overlap-supported anchors, retrieval-only hidden hubs, and network-emergent novelty nodes, then propagated into staged hypothesis and strategy generation under topology constraints. We evaluate the model in Alzheimer's disease (AD) and pancreatic ductal adenocarcinoma (PDAC). In PDAC, the workflow produced a balanced 75-gene candidate universe and a 23-strategy portfolio, with significant DepMap support at both target level and strategy level. In AD, stricter candidate controls yielded a compact 34-gene universe and 14 strategies; under an expanded CRISPRbrain registry, both target-level axes were significant , with strong strategy-level enrichment. Across both diseases, final strategies preserved full provenance closure to the candidate pool, enabling end-to-end auditability from retrieval artifacts to validation outputs. These results support a transferable discovery architecture in which omics evidence constrains biological activity, LLM retrieval expands mechanistic search space, and network-aware fusion preserves interpretability. The framework provides a reproducible basis for dual-disease target prioritization and motivates continuous literature-mechanism concordance with agentic evidence-refresh loops.