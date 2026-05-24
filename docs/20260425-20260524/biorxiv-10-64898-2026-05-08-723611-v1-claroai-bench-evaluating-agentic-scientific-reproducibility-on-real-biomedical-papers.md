---
title: "ClaroAI-Bench: Evaluating Agentic Scientific Reproducibility on Real Biomedical Papers"
title_zh: ClaroAI-Bench：在真实生物医学论文上评估智能体的科学可重复性
authors: "O'Connell, K. A."
date: 2026-05-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.08.723611v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 生物医学论文中AI代理科学可重复性的基准测试
tldr: "ClaroAI-Bench是一个评估AI代理复现生物医学论文计算结果的基准测试，包含35篇真实NIH资助论文，覆盖五种模态。通过五维度评分（数据可发现性、可访问性、代码可用性、环境可重建性、结果可复现性）全面衡量复现能力。全功能代理成功复现60.6%的论文，而基线方法复制率为0%。元数据评分与复现结果强相关（r=0.68），数据代码可访问的论文复现得分高出2.9倍。该基准填补了代码生成和端到端科学AI评估之间的空白。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准（如SWE-bench）缺乏对AI代理在真实科学复现任务中处理脆弱环境、缺失元数据和访问约束的能力评估。
method: 构建35篇NIH资助论文的复现任务，定义五维度评分规则，使用三种代理配置（审计基线、仅bash代理、全功能代理）进行消融实验，并采用三个前沿模型进行多模型评分。
result: "全功能代理（Claude Code）成功复现20/33篇计算论文（60.6%），元数据评分与复现结果强相关（r=0.68），数据代码可访问的论文复现率提高2.9倍，环境重建维度评估者一致性最低（r=0.51-0.81）。"
conclusion: ClaroAI-Bench有效评估了AI代理在真实生物医学论文复现中的能力，揭示了当前主要瓶颈在于环境重建和元数据获取，为改进科学AI代理提供了明确方向。
---

## 摘要
我们介绍了ClaroAI-Bench，一个评估套件，用于衡量AI智能体从已发表的生物医学研究中复现计算发现的能力。该基准包含35篇真实的NIH资助论文，涵盖五种模态（基因组学、影像学、临床/电子健康记录、流行病学、湿实验室），按五个维度评分：数据可发现性（D1）、数据可访问性（D2）、代码可用性（D3）、环境可重构性（D4）和结果可复现性（D5）。每项任务要求智能体定位数据、获取代码、重建计算环境、执行分析并根据已发表的主张验证结果——模拟完整的科学复现流程。在三条件消融实验中，仅审计基线（D1-D4元数据评分）和仅bash智能体（API + bash工具）均达到0%的D5复现，而全能力智能体（Claude Code，所有工具）复现了33篇计算论文中的20篇（60.6%；95% CI [42.4, 75.8]）。D1-D4元数据评分强烈预测D5结果（Spearman r=0.68, p<0.0001），且具有可访问数据和代码的论文的D5得分比受限论文高2.9倍（p=0.0013）。使用三种前沿模型（Claude Opus 4.6、GPT-5.4、Gemini 2.5 Pro）的多模型评分在D3上产生r=0.85-0.97的模型间一致性，但在D4上仅为r=0.51-0.81，将环境重构确定为评估者分歧最大的维度。ClaroAI-Bench通过测试具有脆弱环境、缺失元数据和访问限制的长周期真实世界复现任务，填补了代码生成基准（SWE-bench）与端到端科学AI评估之间的空白。该基准、评分标准、智能体日志和可pip安装的审计器存档在https://doi.org/10.5281/zenodo.20071236和HuggingFace数据集https://huggingface.co/datasets/kyleaoconnell22/claroai-bench。

## Abstract
We introduce ClaroAI-Bench, an evaluation suite for measuring AI agents ability to reproduce computational findings from published biomedical research. The benchmark comprises 35 real NIH-funded papers spanning five modalities (genomics, imaging, clinical/EHR, epidemiology, wet-lab) scored on a five-dimension rubric: data findability (D1), data accessibility (D2), code availability (D3), environment reconstructability (D4), and results reproducibility (D5). Each task requires an agent to locate data, obtain code, reconstruct the compute environment, execute the analysis, and verify results against published claims--mirroring the full scientific reproduction pipeline. In a three-condition ablation, an audit-only baseline (D1-D4 metadata scoring) and a bash-only agent (API + bash tool) both achieve 0% D5 reproduction, while a full-capability agent (Claude Code, all tools) reproduces 20 of 33 computational papers (60.6%; 95% CI [42.4, 75.8]). D1-D4 metadata scores strongly predict D5 outcomes (Spearman r=0.68, p<0.0001), and papers with accessible data and code achieve 2.9x higher D5 scores than restricted papers (p=0.0013). Multi-model scoring with three frontier models (Claude Opus 4.6, GPT-5.4, Gemini 2.5 Pro) yields inter-model agreement of r=0.85-0.97 on D3 but only r=0.51-0.81 on D4, identifying environment reconstruction as the dimension with highest evaluator disagreement. ClaroAI-Bench fills a gap between code-generation benchmarks (SWE-bench) and end-to-end scientific AI evaluations by testing long-horizon, real-world reproduction tasks with brittle environments, missing meta-data, and access constraints. The benchmark, scoring rubric, agent logs, and pip-installable auditor are archived at https://doi.org/10.5281/zenodo.20071236 and on HuggingFace Datasets at https://huggingface.co/datasets/kyleaoconnell22/claroai-bench.