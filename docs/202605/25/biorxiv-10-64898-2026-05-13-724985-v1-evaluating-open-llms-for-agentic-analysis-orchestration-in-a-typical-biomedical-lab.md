---
title: Evaluating open LLMs for agentic analysis orchestration in a typical biomedical lab
title_zh: 评估开放大语言模型在典型生物医学实验室中的代理分析编排能力
authors: "Nekrutenko, A."
date: 2026-05-18
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.13.724985v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 6.0
evidence: 评估开源LLM用于智能体生物医学数据分析
tldr: 27b在所有计划上均达到前沿精度，且成本极低（低于2000美元硬件）。研究提供了可复现的评估框架。
source: biorxiv
selection_source: fresh_fetch
motivation: 降低生物医学数据分析中依赖商业大模型的高昂推理成本，探索免费开源模型的替代能力。
method: 使用Claude Opus制定逐步精细的变异检测计划，让六个开源大模型在桌面GPU上执行计划，并通过36个错误注入单元进行精度对比。
result: 27b在所有计划上复现了前沿精度，在错误注入矩阵中与Claude Opus逐单元匹配。
conclusion: 开源大模型在特定任务上可达到商业模型精度，且硬件成本低，适合作为执行工具；未来模型更新后需重新评估。
---

## 摘要
代理工具——一种软件环境，其中大型语言模型规划、调用外部工具、执行代码并以最少的人工干预进行迭代——将在未来几年内承担大量常规生物医学数据分析工作。然而，前沿模型每次调用的推理成本是瓶颈，且会迅速累积。本文测试了一个免费、本地可运行的开放权重模型能否以前沿的准确性接管重复的执行步骤。我们使用Claude Opus为每个样本的变异调用制定详细程度递增的计划，并在桌面级GPU上让六个2026年发布的开放权重实现模型执行这些计划。qwen3.6:27b在每个计划上都重现了前沿准确性，并在一个36细胞的错误注入矩阵上与Opus实现细胞水平的匹配。售价低于2000美元的Jetson或Apple Mac Mini足以支持实现端。开放权重模型格局以月为单位演变，因此本文推荐的特定实现模型将被取代；我们在https://github.com/nekrut/LLM-eval-paper上提供了计划、工具、评分代码和每个细胞的产物，作为未来模型重新评估的框架。

## Abstract
Agentic tools -- software environments where a large language model plans, calls external tools, executes code, and iterates with minimal human intervention -- will run a substantial share of routine biomedical data analysis within the next few years. However, per-call inference cost on frontier models is the bottleneck and can add up quickly. Here, we tested whether a free, locally-runnable open-weight model could take over the repetitive execution steps at frontier accuracy. We used Claudes Opus to author plans of increasing detail for per-sample variant calling, and ran six 2026-release open-weight implementer LLMs against those plans on a set of desktop GPUs. qwen3.6:27b reproduced frontier accuracy on every plan and matched Opus cell-for-cell on a 36-cell error-injection matrix. A sub-$2,000 Jetson or Apple Mac Mini sufficed for the implementer side. The open-weight model landscape evolves on the order of months, so the specific implementer recommended here will be superseded; we provide the plans, harness, scoring code, and per-cell artifacts at https://github.com/nekrut/LLM-eval-paper as a framework for re-evaluating future models.