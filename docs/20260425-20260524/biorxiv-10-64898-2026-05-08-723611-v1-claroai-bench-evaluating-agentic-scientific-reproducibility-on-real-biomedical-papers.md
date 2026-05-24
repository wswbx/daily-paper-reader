---
title: "ClaroAI-Bench: Evaluating Agentic Scientific Reproducibility on Real Biomedical Papers"
title_zh: "ClaroAI-Bench: 在真实生物医学论文上评估智能体的科学可再现性"
authors: "O'Connell, K. A."
date: 2026-05-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.08.723611v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 6.0
evidence: 评估AI代理复现科学发现的基准
tldr: "ClaroAI-Bench是一个评估AI代理复现生物医学论文计算结果的基准，包含35篇真实NIH资助论文，从数据可发现性、可访问性、代码可用性、环境可重建性和结果可复现性五维评分。实验发现仅全能力代理（Claude Code）复现率达60.6%，而基线方法为0%，且元数据评分与复现结果强相关（r=0.68）。该基准填补了代码生成基准与端到端科学AI评估之间的空白。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准缺乏对AI代理在真实、长周期科学复现任务中能力的评估，需要填补代码生成基准与端到端科学AI评估之间的空白。
method: 构建35篇真实生物医学论文的五维评分标准，通过三种条件（审计基线、仅bash代理、全能力代理）对比评估，并使用三个前沿模型进行多模型评分验证。
result: "全能力代理成功复现33篇计算论文中的20篇（60.6%），基线方法复现率为0%；元数据评分与复现结果强相关（Spearman r=0.68），数据代码可获取论文的D5评分高2.9倍。"
conclusion: ClaroAI-Bench通过测试长周期、真实世界复现任务，揭示了环境重建是评估中最具分歧的维度，为科学AI代理能力提供了有效评测工具。
---

## 摘要
我们推出ClaroAI-Bench，一个用于衡量AI智能体再现已发表生物医学研究计算发现能力的评估套件。该基准包含35篇真实的NIH资助论文，涵盖五种模态（基因组学、成像、临床/EHR、流行病学、湿实验），并按照五个维度进行评分：数据可查找性（D1）、数据可访问性（D2）、代码可用性（D3）、环境可重构性（D4）和结果可再现性（D5）。每个任务要求智能体定位数据、获取代码、重构计算环境、执行分析，并将结果与已发表的声明进行验证——镜像了完整的科学再现流程。在三条件消融实验中，仅审计基线（D1-D4元数据评分）和仅bash智能体（API + bash工具）均实现了0%的D5再现，而全功能智能体（Claude Code，所有工具）再现了33篇计算论文中的20篇（60.6%；95% CI [42.4, 75.8]）。D1-D4元数据得分强烈预测D5结果（Spearman r=0.68，p<0.0001），且具有可访问数据和代码的论文比受限论文的D5得分高2.9倍（p=0.0013）。使用三个前沿模型（Claude Opus 4.6、GPT-5.4、Gemini 2.5 Pro）进行多模型评分，在D3上得到r=0.85-0.97的模型间一致性，但在D4上仅为r=0.51-0.81，表明环境重构是评估者分歧最大的维度。ClaroAI-Bench通过测试具有脆弱环境、缺失元数据和访问限制的长期真实世界再现任务，填补了代码生成基准（SWE-bench）和端到端科学AI评估之间的空白。该基准、评分标准、智能体日志和可pip安装的审计器已存档于https://doi.org/10.5281/zenodo.20071236和HuggingFace数据集https://huggingface.co/datasets/kyleaoconnell22/claroai-bench。

## Abstract
We introduce ClaroAI-Bench, an evaluation suite for measuring AI agents ability to reproduce computational findings from published biomedical research. The benchmark comprises 35 real NIH-funded papers spanning five modalities (genomics, imaging, clinical/EHR, epidemiology, wet-lab) scored on a five-dimension rubric: data findability (D1), data accessibility (D2), code availability (D3), environment reconstructability (D4), and results reproducibility (D5). Each task requires an agent to locate data, obtain code, reconstruct the compute environment, execute the analysis, and verify results against published claims--mirroring the full scientific reproduction pipeline. In a three-condition ablation, an audit-only baseline (D1-D4 metadata scoring) and a bash-only agent (API + bash tool) both achieve 0% D5 reproduction, while a full-capability agent (Claude Code, all tools) reproduces 20 of 33 computational papers (60.6%; 95% CI [42.4, 75.8]). D1-D4 metadata scores strongly predict D5 outcomes (Spearman r=0.68, p<0.0001), and papers with accessible data and code achieve 2.9x higher D5 scores than restricted papers (p=0.0013). Multi-model scoring with three frontier models (Claude Opus 4.6, GPT-5.4, Gemini 2.5 Pro) yields inter-model agreement of r=0.85-0.97 on D3 but only r=0.51-0.81 on D4, identifying environment reconstruction as the dimension with highest evaluator disagreement. ClaroAI-Bench fills a gap between code-generation benchmarks (SWE-bench) and end-to-end scientific AI evaluations by testing long-horizon, real-world reproduction tasks with brittle environments, missing meta-data, and access constraints. The benchmark, scoring rubric, agent logs, and pip-installable auditor are archived at https://doi.org/10.5281/zenodo.20071236 and on HuggingFace Datasets at https://huggingface.co/datasets/kyleaoconnell22/claroai-bench.