---
title: "Using AI to Build AI: AIDO.Builder Enables Autonomous Machine Learning Model Building for Biomedicine"
title_zh: 用AI构建AI：AIDO.Builder实现生物医学领域的自主机器学习模型构建
authors: "Guo, H., Liang, Y., Cheng, X., Ellington, C., Xie, P., Song, L., Xing, E."
date: 2026-04-29
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.20.719735v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 9.0
evidence: 自主AI模型构建用于生物医学
tldr: 本文提出AIDO.Builder，一种基于代理的AI系统，能根据自然语言任务描述自动构建生物医学预测模型，包括设计管道、选择架构、执行实验和迭代优化。在多个基准上，它无需人工干预即可达到与人类专家相竞争的性能，展示了AI自动化加速生物医学AI开发的潜力。
source: biorxiv
selection_source: fresh_fetch
motivation: 生物医学中构建有效预测模型需要大量专业知识和手动迭代，阻碍了机器学习在该领域的广泛应用。
method: AIDO.Builder利用代理AI架构，根据自然语言输入自动生成训练和评估管道，通过反馈循环迭代优化代码、配置和训练流程。
result: 在多种生物医学基准任务上，AIDO.Builder生成的模型性能与人类专家构建的模型相当，且无需手动迭代。
conclusion: AI自身可用于自动化生物医学AI模型的开发过程，显著降低对专家依赖并加速研究。
---

## 摘要
机器学习加速了生物医学发现，但创建有效的预测模型需要专业的人类知识和大量手动工作。研究人员必须反复设计流程、选择架构并调试代码。这一挑战在生物医学中尤为严峻，因为该领域普遍存在异构数据集、稀疏标注和复杂的评估协议。我们提出了AIDO.Builder，一个代理型人工智能系统，完全自动化生物医学模型开发的整个生命周期。仅需提供自然语言任务描述和目标指标，AIDO.Builder即可自主构建可执行的训练和评估流程。该系统选择合适的建模策略，执行实验，并利用自动反馈循环迭代地修改自己的代码、配置和训练过程。它通过从头训练专门模型或使用预训练基础模型进行任务适配来灵活适应新任务。我们证明，在多个生物医学基准上，AIDO.Builder产生了与人类方法高度竞争的解决方案，同时消除了先前稳健模型开发所需的手动迭代。通过将原始数据自动转化为可靠的AI模型，AIDO.Builder展示了如何利用AI本身来加速生物医学研究的AI应用。

## Abstract
Machine learning accelerates biomedical discovery, but creating effective predictive models requires specialized human expertise and demanding manual effort. Researchers must iteratively design pipelines, select architectures, and debug code. This challenge is particularly severe in biomedicine because of the heterogeneous datasets, sparse annotations, and complex evaluation protocols that are common in the domain. We present AIDO.Builder, an agentic artificial intelligence system that fully automates the entire life-cycle of biomedical model development. Provided only with a natural language task description and a target metric, AIDO.Builder autonomously constructs executable training and evaluation pipelines. The system selects suitable modeling strategies, executes experiments, and uses automated feedback-loop to iteratively revise its own code, configurations, and training procedures. It flexibly adapts to new tasks by training specialized models de novo or by using pretrained foundation models to build predictive models through task-appropriate adaptation. We show that across diverse biomedical benchmarks, AIDO. Builder produces highly competitive solutions against human alternatives, while eliminating the manual iteration previously required for robust model development. By automating the translation of raw data into reliable AI models, AIDO.Builder demonstrates how AI itself can be used to accelerate AI for biomedical research.