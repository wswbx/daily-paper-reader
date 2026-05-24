---
title: A unified benchmark of synthetic data generation for clinical transcriptomic cancer cohorts
title_zh: 临床转录组癌症队列的合成数据生成统一基准
authors: "Trinh, T.-C., Woillard, J.-B., Uguzzoni, G., Battail, C."
date: 2026-05-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.13.724858v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 6.0
evidence: 临床转录组学合成数据基准，AI用于精准肿瘤学
tldr: 针对精准肿瘤学中临床转录组数据共享的生物效用与隐私权衡问题，本文首次构建高维癌症转录组合成数据生成基准，提出SynOmicsBench框架，结合标准化预处理、统计保真度、攻击隐私评估和下游生物学验证。在三个临床试验比较多种方法，发现Gaussian Copula表现最平衡，且合成数据能重现生物信号方向但效应减弱，为隐私保护下的假设生成提供工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 在精准肿瘤学中，实现临床转录组数据共享时的生物效用与患者隐私间的权衡仍是一个关键挑战。
method: 提出SynOmicsBench框架，结合标准化预处理与多维评估（统计保真度、攻击隐私、下游生物学验证），对比多种合成数据生成方法。
result: Gaussian Copula和Avatar表现较好，但无单一方法全面占优；合成数据可复现生物信号方向但效应和变异衰减。
conclusion: 该框架为可重复的方法选择提供决策支持，促进生物学知情且隐私感知的合成数据在精准肿瘤学中的采用。
---

## 摘要
在精准肿瘤学中，将转录组临床数据集应用于人工智能时，在生物效用与患者隐私之间取得平衡仍然是安全数据共享的关键挑战。本文首次针对高维临床转录组癌症数据引入基准研究，比较了三种临床癌症试验中的合成数据生成方法。我们的框架SynOmicsBench将标准化预处理与多维评估相结合，优先考虑下游生物学验证，同时兼顾统计保真度和基于攻击的隐私评估。结果表明，没有任何单一方法在所有维度上占优，其中Gaussian Copula实现了最平衡的性能，其次是Avatar，这表明仅基于度量的相似性不足以确保高阶分子依赖性的保留。合成数据一致地再现了生物医学信号的方向性，但效应大小和重复间变异性有所减弱，这支持采用多种子合成时的假设生成。总体而言，该框架为方法选择提供了可重复的决策支持工具，并促进了在精准肿瘤学中基于生物学知识、注重隐私的合成数据应用。

## Abstract
Achieving a trade-off between biological utility and patient privacy remains a key challenge for secure data sharing when applying transcriptomic clinical datasets to artificial intelligence in precision oncology. Here, we introduce the first benchmarking study tailored to high-dimensional clinical transcriptomic cancer data, comparing synthetic data generation methods across three clinical cancer trials. Our framework, SynOmicsBench, combines standardized preprocessing with multidimensional evaluation, prioritizing downstream biological validation alongside statistical fidelity and attack-based privacy assessment. Results indicate that no single method dominated all dimensions, with Gaussian Copula achieving the most balanced performance, followed by Avatar, demonstrating that metric-based similarity alone is insufficient to ensure preservation of higher-order molecular dependencies. Synthetic data consistently reproduced biomedical signal directionality but with attenuated effect sizes and inter-replicate variability, supporting hypothesis generation when multi-seed synthesis is adopted. Collectively, this framework provides a reproducible decision-support tool for method selection and promotes biologically informed, privacy-aware adoption of synthetic data in precision oncology.