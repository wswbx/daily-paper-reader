---
title: "OmniCellAgent: An AI Scientist for Omic-Driven Scientific Discovery"
title_zh: OmniCellAgent：一种用于组学驱动的科学发现的AI科学家
authors: "Huang, D., Li, H., Li, W., Zhang, H., Xu, T., Lu, Y., Fang, K., Xu, Z., Chen, J., Dickson, P., Sardiello, M., Buchser, W., Cooper, J. D., Cruchaga, C., Eghtesady, P., Li, G., Goedegebuure, P., DeNardo, D., Ding, L., Fields, R. C., Zhan, M., Miller, J. P., Province, M., Chen, Y., Payne, P., Li, F."
date: 2026-05-20
pdf: "https://www.biorxiv.org/content/10.1101/2025.07.31.667797v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 9.0
evidence: 用于组学驱动发现的AI科学家
tldr: 本文提出OmniCellAgent，一个基于大规模单细胞RNA测序资源的多智能体AI框架，能自动检索、整合和分析疾病与对照数据集，并结合生物医学先验知识进行靶点注释和下游解读，生成结构化报告和假设，降低组学驱动发现的障碍。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统组学数据分析需要用户预定义疾病数据集，耗时且对非计算研究者困难。
method: 构建多智能体框架，包括自动数据获取、先验知识注释和专家解读模块。
result: 在多疾病设置下能识别相关数据集、优先生物意义靶点并生成综合假设。
conclusion: 多智能体AI系统可降低组学发现门槛，加速精准医学假设生成。
---

## 摘要
在生物医学科学发现中，识别相关的组学数据集并利用来自数据库和文献的先验知识解释分析结果对于产生新假设至关重要。尽管最近的AI智能体支持自动化的组学分析和文献检索，但它们通常需要用户预先定义和整理疾病特定数据集，这一过程即使对非计算领域的研究人员来说仍然具有挑战性和耗时。在此，我们提出OmniCellAgent，一个基于大规模单细胞RNA测序（scRNA-seq）资源的多智能体AI框架，能够自主检索、整合和分析跨组织和条件下的多种细胞类型的疾病和对照相关数据集。此外，OmniCellAgent包含一个生物医学先验知识智能体，用于使用整理好的数据库和文献进行系统的靶点注释，以及领域特定的专家智能体用于高优先级靶点的下游解释。通过汇总各智能体的证据，该框架生成结构化的分析报告和数据驱动的假设。我们在多种疾病背景下评估了OmniCellAgent，证明了其识别相关数据集、优先选择具有生物学意义的靶点以及生成全面、有证据支持的假设的能力。我们的结果表明，多智能体AI系统可以降低组学驱动发现的障碍，并加速精准医学中的假设生成。

## Abstract
In biomedical scientific discovery, identifying relevant omics datasets and interpreting analysis results using prior knowledge from databases and literature are essential for generating novel hypotheses. Although recent AI agents support automated omics analysis and literature retrieval, they typically require users to predefine and curate disease-specific datasets, which is a process that remains challenging and time-consuming, particularly for non-computational researchers. Herein we present OmniCellAgent, a multi-agent AI framework built on large-scale single-cell RNA sequencing (scRNA-seq) resources that autonomously retrieves, integrates and analyzes disease and control-related datasets of diverse cell types across tissues and conditions. Moreover, OmniCellAgent incorporates a biomedical prior knowledge agent for systematic target annotation using curated databases and literature, as well as domain-specific expert agents for downstream interpretation of high-priority targets. By aggregating evidence across agents, the framework generates structured analytical reports and data-driven hypotheses. We evaluate OmniCellAgent across multiple disease settings, demonstrating its ability to identify relevant datasets, prioritize biologically meaningful targets and produce comprehensive, evidence-supported hypotheses. Our results suggest that multi-agent AI systems can reduce barriers to omics-driven discovery and accelerate hypothesis generation in precision medicine.