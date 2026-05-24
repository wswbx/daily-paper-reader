---
title: Interpreting Omics Data Analysis with Large Language Models for Disease Target and Drug Discovery
title_zh: 利用大语言模型解读组学数据分析以进行疾病靶点和药物发现
authors: "XU, Z., Chen, W., Ren, W., Xu, T., Amaechin, S., Khan, R., Chen, Y., Province, M., Payne, P., Li, F."
date: 2026-05-05
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.30.721768v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: LLM和组学数据用于知识发现
tldr: 本文提出一个基于大语言模型和组学数据分析的Text-to-Target框架，通过模态感知融合策略将LLM的文献知识检索与数值组学分析结合，用于疾病靶点发现和药物研发。在阿尔茨海默病和胰腺癌中验证，框架能生成平衡的候选基因集和策略组合，并保留完整溯源，实现端到端可审计。
source: biorxiv
selection_source: fresh_fetch
motivation: 大语言模型从文献中检索疾病机制快速但缺乏定量证据，不可靠；纯组学数据分析缺乏先验知识。需要一种结合两者优势的方法。
method: 提出schema约束的多模型LLM检索与组学数据分析结合的Text-to-Target框架，通过模态感知融合将候选分为三类（重叠支持锚点、检索隐藏节点、网络新颖节点），在拓扑约束下生成假设和策略。
result: 在胰腺癌中生成75基因候选集和23策略，在阿尔茨海默病中生成34基因集和14策略，均获得DepMap/CRISPRbrain数据库的显著支持，且策略保持完整溯源。
conclusion: 该框架提供了一个可复现的双疾病靶点优先排序基础，并推动了文献-机制一致性的持续证据更新循环。
---

## 摘要
在生物医学科学发现中，综合文献中的先验知识是解读数值组学数据分析以识别疾病靶点和发现药物的关键组成部分。大语言模型（LLM）可以快速从生物医学文本中检索疾病机制，但仅文本输出对于靶点和药物优先级排序而言是通用的且不可靠，因为它们缺乏基于特定队列的定量证据。在此，我们提出了一种可溯源的文本到靶点框架，该框架将受模式约束的多模型LLM检索与数值组学数据分析相结合。关键设计是一个模态感知的融合步骤：候选对象被划分为重叠支持的锚点、仅检索的隐藏枢纽以及网络涌现的新颖节点，然后在拓扑约束下传播到分阶段的假设和策略生成中。我们在阿尔茨海默病（AD）和胰腺导管腺癌（PDAC）中评估了该模型。在PDAC中，该工作流程生成了一个平衡的75个基因的候选宇宙和一个23个策略的组合，在靶点水平和策略水平上都得到了显著的DepMap支持。在AD中，更严格的候选控制产生了一个紧凑的34个基因宇宙和14个策略；在扩大的CRISPRbrain注册库下，两个靶点水平轴均显著，且策略水平富集强烈。在这两种疾病中，最终策略保持了对候选池的完全来源封闭性，实现了从检索伪影到验证输出的端到端可审计性。这些结果支持一种可转移的发现架构，其中组学证据约束生物活性，LLM检索扩展机制搜索空间，而网络感知融合保持可解释性。该框架为双重疾病靶点优先级排序提供了可重复的基础，并通过代理证据刷新循环促进文献-机制一致性持续更新。

## Abstract
In biomedical scientific discovery, synthesizing prior knowledge from the literature is an essential component of interpreting numerical omics data analyses for disease target identification and drug discovery. Large language models (LLMs) alone can rapidly retrieve disease mechanisms from biomedical text, but text-only outputs are general and unreliable for target and drug prioritization without cohort-specific quantitative evidence. Herein, we propose a provenance-aware Text-to-Target framework that couples schema-constrained multi-model LLM retrieval with numeric omics data analysis. The key design is a modality-aware fusion step: candidates are partitioned into overlap-supported anchors, retrieval-only hidden hubs, and network-emergent novelty nodes, then propagated into staged hypothesis and strategy generation under topology constraints. We evaluate the model in Alzheimers disease (AD) and pancreatic ductal adenocarcinoma (PDAC). In PDAC, the workflow produced a balanced 75-gene candidate universe and a 23-strategy portfolio, with significant DepMap support at both target level and strategy level. In AD, stricter candidate controls yielded a compact 34-gene universe and 14 strategies; under an expanded CRISPRbrain registry, both target-level axes were significant, with strong strategy-level enrichment. Across both diseases, final strategies preserved full provenance closure to the candidate pool, enabling end-to-end auditability from retrieval artifacts to validation outputs. These results support a transferable discovery architecture in which omics evidence constrains biological activity, LLM retrieval expands mechanistic search space, and network-aware fusion preserves interpretability. The framework provides a reproducible basis for dual-disease target prioritization and motivates continuous literature-mechanism concordance with agentic evidence-refresh loops.