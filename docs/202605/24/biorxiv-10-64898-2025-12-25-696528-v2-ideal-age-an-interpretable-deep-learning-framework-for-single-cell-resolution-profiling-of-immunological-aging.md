---
title: "IDEAL-Age: an interpretable deep learning framework for single-cell resolution profiling of immunological aging"
title_zh: IDEAL-Age：用于免疫衰老单细胞分辨率图谱的可解释深度学习框架
authors: "Xu, Y., Luo, Z., He, K., Zhang, F., Zhang, Y., Wang, J., Wen, H., Li, Y., Han, D."
date: 2026-05-22
pdf: "https://www.biorxiv.org/content/10.64898/2025.12.25.696528v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 7.0
evidence: 可解释深度学习用于单细胞分辨率的免疫老化发现
tldr: 提出IDEAL-Age，一个可解释的深度学习框架，直接分析单细胞PBMC转录组，评估免疫衰老。在31种方法中表现最优，揭示了线性和非线性转录动态及阶段特异性生理转变，并识别出促年轻或促衰老的细胞贡献。应用于系统性红斑狼疮，发现干扰素相关单核细胞转变导致免疫衰老加速。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有免疫衰老时钟基于bulk转录组，无法解析细胞异质性，亟需高分辨率方法。
method: 构建可解释深度学习框架，直接处理单细胞PBMC转录组数据。
result: 在独立队列中优于31种方法，揭示免疫衰老的线性和非线性动态，识别细胞贡献，并在SLE中发现加速衰老。
conclusion: IDEAL-Age为解析系统性免疫衰老提供了高分辨率计算框架。
---

## 摘要
免疫衰老会增加感染的易感性并降低疫苗反应性，然而批量转录组时钟掩盖了这一过程背后的细胞异质性。在此，我们提出了IDEAL-Age，一个直接在单细胞PBMC转录组上运行的可解释深度学习框架。在独立队列中对31种方法进行基准测试，显示出优越的预测性能。该框架的可解释性揭示了线性和非线性的转录组动态，这些动态揭示了阶段特异性的生理转变，并识别出促年轻或促衰老的细胞贡献。应用于系统性红斑狼疮（SLE）揭示了由干扰素相关单核细胞转变驱动的加速免疫衰老。IDEAL-Age建立了一个高分辨率计算框架，用于解读系统性免疫衰老。

## Abstract
Immunosenescence increases susceptibility to infection and reduces vaccine responsiveness, yet bulk transcriptomic clocks obscure the cellular heterogeneity underlying this process. Here, we present IDEAL-Age, an interpretable deep learning framework that operates directly on single-cell PBMC transcriptomes. Benchmarking against 31 methods across independent cohorts demonstrates superior predictive performance. The framework' s interpretability uncovers linear and non-linear transcriptomic dynamics that reveal phase-specific physiological transitions, and identifies pro-youthful or pro-aging cellular contributions. Application to systemic lupus erythematosus (SLE) reveals accelerated immunological aging driven by interferon-associated monocyte shifts. IDEAL-Age establishes a high-resolution computational framework for deciphering systemic immune aging.