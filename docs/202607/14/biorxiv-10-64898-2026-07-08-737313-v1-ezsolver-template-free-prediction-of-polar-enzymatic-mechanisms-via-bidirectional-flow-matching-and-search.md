---
title: "EZSolver: Template-free prediction of polar enzymatic mechanisms via bidirectional flow matching and search"
title_zh: EZSolver：通过双向流匹配与搜索的无模板极性酶机制预测
authors: "Kuo, L.-H., Yang, J., Arnold, F."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.08.737313v1.full.pdf"
tags: ["query:ar"]
score: 6.0
evidence: 通过生成流匹配和搜索自动预测酶机制
tldr: "酶促反应机制预测对酶功能理解和设计至关重要，但现有规则字典方法无法泛化到未知化学反应。本文提出EZSolver，一种无模板生成式框架，通过流匹配预测器EZFlow学习电子重分布，并借助双向束搜索优化路径。在多种酶类上，全机制预测准确率达60.0%，化学合理性84.6%，且能成功推断未记录的催化途径。该工作为自动化酶功能预测和新型生物催化剂设计奠定了基础。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737313-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 669, \"height\": 230, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737313-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1407, \"height\": 775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737313-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737313-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1184, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737313-v1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1477, \"height\": 968, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737313-v1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1805, \"height\": 1198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-08-737313-v1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1406, \"height\": 1406, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-08-737313-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1210, \"height\": 494, \"label\": \"Table\"}]"
motivation: 现有基于规则的预测器无法泛化到分布外的化学反应，需要一种能学习电子重分布而非记忆模板的方法。
method: 提出EZSolver，包含流匹配预测器EZFlow和评估器引导的双向束搜索，无模板地预测极性酶促反应机制。
result: "在多种酶类上达到60.0%全机制预测准确率和84.6%化学合理性，在分布外测试中成功推断未知路径。"
conclusion: EZSolver通过生成式学习电子重分布，突破了模板依赖，为酶机制预测和新型生物催化剂设计提供了新范式。
---

## 摘要
预测酶促反应机理对于理解酶功能以及设计和发现新酶至关重要。目前的计算预测器依赖于确定性的、基于规则的词典，这些词典在分布内任务中表现良好，但无法推广到分布外（OOD）化学过程。为解决这一局限，我们提出了EZSolver，一种用于极性酶机理预测的无模板生成框架。EZSolver由流匹配预测器（EZFlow）驱动，并通过评估器引导的双向束搜索导航，它学习电子重新分布的化学机制，而非记忆僵化的模板。在多种酶类上的评估表明，EZSolver对未见过的极性酶促反应的完整机理预测达到60.0%的准确率和84.6%的化学合理性。而基于规则的模型在没有预定义模板时会崩溃，EZSolver则成功外推化学知识以推断未编录的路径，这在严格的OOD基准测试中得到验证。通过阐明酶促化学机理，EZSolver为自动预测酶功能以及发现和设计用于可持续化学的新型生物催化剂铺平了道路。

## Abstract
Predicting enzymatic reaction mechanisms is critical for understanding enzyme function and for designing and discovering new enzymes. Current computational predictors rely on deterministic, rule-based dictionaries, which perform well on in-distribution tasks but fail to generalize to out-of-distribution (OOD) chemistry. To address this limitation, we present EZSolver, a template-free, generative framework for polar enzymatic mechanism prediction. Powered by a flow matching predictor (EZFlow) and navigated by an evaluator-guided bidirectional beam search, EZSolver learns the chemistry of electron redistribution instead of memorizing rigid templates. Evaluated across diverse enzyme classes, EZSolver achieves a 60.0% accuracy and an 84.6% chemical plausibility rate for full mechanism prediction of unseen polar enzymatic reactions. While rule-based models collapse without predefined templates, EZSolver successfully extrapolates chemical knowledge to infer uncatalogued pathways, as demonstrated during rigorous OOD benchmarking. By illuminating enzymatic chemical mechanisms, EZSolver helps pave the way for automated prediction of enzyme function and discovery and design of novel biocatalysts for sustainable chemistry.

TOC Graphic

O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=152 SRC="FIGDIR/small/737313v1_ufig1.gif" ALT="Figure 1">
View larger version (30K):
org.highwire.dtl.DTLVardef@18a4abdorg.highwire.dtl.DTLVardef@30f366org.highwire.dtl.DTLVardef@1bbc227org.highwire.dtl.DTLVardef@1c7a1cb_HPS_FORMAT_FIGEXP  M_FIG C_FIG