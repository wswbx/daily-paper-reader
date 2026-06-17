---
title: "AutoZyme: An Autonomous Agentic Framework to Optimize Bioinformatics Software"
title_zh: AutoZyme：一个用于优化生物信息学软件的自主智能体框架
authors: "Xie, E., Cheng, L., Cai, Y., Shireman, J., Kendziorski, C."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.12.731250v1.full.pdf"
tags: ["query:cli-agent"]
score: 6.0
evidence: 自主代理框架，通过终端自动构建基准、识别瓶颈并迭代测试代码修改
tldr: "基因组学和生物信息学软件的性能瓶颈随数据规模增长而加剧，传统依赖专家手动优化难以扩展。AutoZyme提出自主智能框架，自动构建基准测试、识别瓶颈并迭代优化代码。在45个函数中超过95%提升运行时，针对Seurat等38个函数实现中位数8.52倍加速，最大超676倍。优化函数通过AutoZyme-Library即插即用，框架可重用，显著降低优化成本。"
source: biorxiv
selection_source: fresh_fetch
motivation: 解决基因组学软件性能瓶颈，摆脱对专家手动优化的依赖，实现可扩展的自动优化。
method: AutoZyme自动构建基准测试、识别瓶颈并迭代生成并测试代码更改，保留加速且不改变输出。
result: "在45个函数中超过95%提升运行时，Seurat等38个函数中位数加速8.52倍，最大676倍，内存无显著增加。"
conclusion: AutoZyme以可重用框架发布，优化函数作为即插即用替换，显著降低生物信息学软件优化门槛。
---

## 摘要
广泛使用的基因组学和生物信息学软件中的性能瓶颈带来了巨大且日益增长的负担，因为生物数据集的大小和数量持续增加。缓解这些瓶颈主要依赖于专家手动优化，因此难以规模化。这里我们提出AutoZyme，一个用于科学软件优化的智能体框架。给定目标函数，AutoZyme构建基准、识别瓶颈并迭代测试代码变更，仅保留那些改善运行时间且保持输出的变更。我们在45个函数上评估了AutoZyme，在超过95%的案例中改善了运行时间且没有显著的内存增加。对于来自基因组学和生物信息学中的Seurat、Scanpy及相关包的38个函数，AutoZyme将运行时间中位数降低8.52倍，最大降低超过676倍。优化后的函数通过AutoZyme-Library作为现有分析管道的即插即用替代品进行分发。我们还发布了AutoZyme作为一个可重用框架，用于优化用户指定的其他包和函数。

## Abstract
Performance bottlenecks in widely used genomics and bioinformatics software present a substantial and growing burden as biological datasets continue to increase in size and number. Relieving these bottlenecks relies largely on expert manual optimization and therefore remains difficult to scale. Here we present AutoZyme, an agentic framework for scientific software optimization. Given a target function, AutoZyme builds benchmarks, identifies bottlenecks, and iteratively tests code changes, retaining only those that improve runtime while preserving output. We evaluated AutoZyme on 45 functions, improving runtime without substantial memory increases in over 95% of cases considered. Across 38 functions from Seurat, Scanpy and related packages in genomics and bioinformatics, AutoZyme reduced runtime by a median of 8.52-fold, with the largest reductions exceeding 676-fold. The optimized functions are distributed through AutoZyme-Library as drop-in replacements for existing analysis pipelines. We also release AutoZyme as a reusable framework for optimizing additional user-specified packages and functions.