---
title: Benchmarking and behavioral characterization of LLM agents for protein design
title_zh: 用于蛋白质设计的LLM智能体的基准测试与行为特征描述
authors: "Kim, J., Romero, P. A."
date: 2026-05-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.06.723381v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: LLM代理在科学发现（蛋白质设计）中的基准测试
tldr: 本文提出BioDesignBench，一个包含76个专家精选蛋白质设计任务的基准，用于评估LLM代理在蛋白质设计中的性能和行为。研究发现最强的LLM代理超越确定性硬编码流程，但持续逊于专家实践；代理通常选择合适工具，但评估候选设计过浅、很少比较替代方案、过早终止探索。强制多指标评估显著提升性能，表明限制是行为而非能力约束。
source: biorxiv
selection_source: fresh_fetch
motivation: 缺乏标准化框架来评估LLM代理在科学工作流中的性能和行为。
method: 构建包含76个专家任务、人类和非LLM基线及行为指标的基准BioDesignBench，评估四个前沿LLM代理。
result: 最强代理超越确定性流程但逊于专家，存在评估过浅、比较不足、探索过早终止等问题。
conclusion: 限制是行为性的，强制深度多指标评估可显著提升性能，需改进代理的评估策略。
---

## 摘要
大型语言模型（LLM）越来越多地被部署为科学发现的智能体，但目前缺乏评估它们在科学工作流程中性能和行为的标准化框架。蛋白质设计提供了一个具有挑战性的测试案例，因为现代工作流程结合了随机生成模型、结构预测系统和基于物理的评估工具，需要广泛的候选探索和筛选。在此，我们引入了BioDesignBench，这是一个包含76个专家策划的蛋白质设计任务的基准测试，涵盖抗体、酶、荧光蛋白、结合剂和支架，以及人类和非LLM基线以及从工具使用轨迹中得出的行为指标。我们在不同的蛋白质设计工作流程中评估了四个前沿的LLM智能体，发现最强的智能体超越了确定性硬编码流程，但始终低于专家实践。尽管智能体通常选择适当的工具，但它们对候选设计的评估过于肤浅，很少比较替代方案，并且过早终止探索。引导式工作流程提高了工具覆盖率，但未提高评估深度。强制执行更深入的多指标评估显著提升了智能体性能，表明这些限制是行为性的而非基本能力约束。我们发布了BioDesignBench、开源参考智能体和一个公共排行榜，作为评估和改进蛋白质工程AI智能体的社区资源。

## Abstract
Large language models (LLMs) are increasingly deployed as agents for scientific discovery, but standardized frame-works for evaluating their performance and behaviour in scientific workflows are lacking. Protein design provides a demanding test case because modern workflows combine stochastic generative models, structure prediction systems, and physics-based evaluation tools that require extensive candidate exploration and filtering. Here we introduce BioDesignBench, a benchmark of 76 expert-curated protein design tasks spanning antibodies, enzymes, fluorescent proteins, binders, and scaffolds, together with human and non-LLM baselines and behavioural metrics derived from tool-use traces. We evaluate four frontier LLM agents across diverse protein design workflows and find that the strongest agents surpass deterministic hardcoded pipelines but consistently underperform expert practice. Although agents generally select appropriate tools, they evaluate candidate designs too shallowly, rarely compare alternatives, and terminate exploration prematurely. Guided workflows improve tool coverage but not evaluation depth. Enforcing deeper multi-metric evaluation substantially improves agent performance, demonstrating that these limitations are behavioural rather than fundamental capability constraints. We release BioDesignBench, open-source reference agents, and a public leaderboard as a community resource for evaluating and improving AI agents for protein engineering.