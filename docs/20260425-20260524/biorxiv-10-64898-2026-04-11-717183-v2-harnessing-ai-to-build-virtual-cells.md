---
title: Harnessing AI to Build Virtual Cells
title_zh: 利用人工智能构建虚拟细胞
authors: "Cheng, X., Li, P., Guo, H., Liang, Y., Gong, J., de Vazelhes, W., Gou, C., Xie, P., Song, L., Xing, E. P."
date: 2026-04-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.11.717183v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 9.0
evidence: AI用于构建虚拟细胞进行科学发现
tldr: 本文提出VCHarness，一个自主AI系统，结合AI编码代理与多模态基础模型，自动构建扰动-响应模型，用于虚拟细胞研究。该系统以最少人工干预探索架构与训练流程，在多个基准测试中性能超越专家设计，且开发时间从数月缩短至数天。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统扰动-响应模型开发依赖专家数月的手动设计、训练与调试，效率低下。
method: VCHarness整合AI编码代理与多模态生物学基础模型，自主迭代生成、评估与优化候选模型架构和训练流程。
result: 在多个扰动-响应基准测试中，VCHarness识别的模型架构优于专家设计，开发时间从数月降至数天，并发现非明显的性能提升模式。
conclusion: 该方法标志着从手动模型工程向自主系统的转变，为构建虚拟细胞世界模型组件提供了可扩展的数据驱动路径。
---

## 摘要
虚拟细胞是细胞的世界模型：一个预测、模拟和编程跨模态和尺度的细胞过程的计算系统。实现这一目标的重要途径是模拟遗传和化学扰动如何引起转录响应，这是疾病理解和药物发现的核心能力。然而，当前的方法仍然依赖专家，需要数月时间反复进行手动模型设计、训练和调试。

本文提出VCHarness，一个自主人工智能系统，通过结合AI编码智能体与多模态生物基础模型来构建扰动-响应模型。该系统以最少的人工干预探索庞大的架构和训练流水线空间，迭代生成、评估和优化候选模型。在多个扰动-响应基准测试中，VCHarness识别出优于专家设计方法的架构，同时将开发时间从数月缩短至数天。它还发现了与性能提升相关的非显而易见架构模式，表明自动搜索可以超越传统设计策略。这些结果表明，从手动工程模型向构建虚拟细胞世界模型组件的自主系统转变，能够实现细胞系统的可扩展和数据驱动探索。

## Abstract
A virtual cell is a world model of a cell: a computational system that predicts, simulates and programs cellular processes across modalities and scales. An important path toward this goal is to model how genetic and chemical perturbations give rise to transcriptional responses, a core capability for disease understanding and drug discovery. However, current approaches remain expert-intensive, relying on iterative manual model design, training and debugging over months.

Here we present VCHarness, an autonomous AI system that constructs perturbation-response models by combining an AI coding agent with multimodal biological foundation models. The system explores large spaces of architectures and training pipelines with minimal human intervention, iteratively generating, evaluating and refining candidate models. Across multiple perturbation-response benchmarks, VCHarness identifies architectures that outperform expert-designed approaches while reducing development time from months to days. It further uncovers non-obvious architectural patterns associated with improved performance, indicating that automated search can extend beyond conventional design strategies. These results suggest a shift from manually engineered models toward autonomous systems for constructing components of virtual cell world models, enabling scalable and data-driven exploration of cellular systems.