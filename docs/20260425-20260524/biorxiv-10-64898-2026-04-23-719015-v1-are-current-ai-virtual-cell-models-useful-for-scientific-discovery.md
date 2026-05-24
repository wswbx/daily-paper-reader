---
title: Are Current AI Virtual Cell Models Useful for Scientific Discovery?
title_zh: 当前的AI虚拟细胞模型对科学发现有用吗？
authors: "Bereket, M. D., Leskovec, J."
date: 2026-04-25
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.23.719015v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: AI辅助科学研究中命中发现的评估框架
tldr: 当前AI虚拟细胞模型虽用于预测扰动对基因表达的影响，但现有基准无法可靠衡量其性能。本文提出需建立直接评估模型预测对科学发现价值的新基准，并介绍PerturbHD框架，用于AI辅助的命中发现评估，以弥补这一缺陷。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准无法有效衡量AI虚拟细胞模型预测对实际科学发现的价值。
method: 提出了PerturbHD评估框架，直接量化模型预测对特定科学发现结果的贡献。
result: PerturbHD框架展示了如何评估AI模型在命中发现任务中的实用性。
conclusion: 需要开发以科学发现直接结果为导向的基准来验证AI模型的实用性。
---

## 摘要
人工智能模型越来越多地被开发用于预测扰动对基因表达的影响，但当前的基准测试无法可靠地衡量模型性能。在此，我们认为需要新的基准测试，直接衡量模型预测对特定科学发现结果的价值，以弥补这一差距。我们提出了PerturbHD，一个用于人工智能驱动的命中发现评估框架，以展示我们提出的方法的优势。

## Abstract
AI models are increasingly developed to predict the effect of perturbations on gene expression, but current benchmarks fail to reliably measure model performance. Here, we argue that new benchmarks that directly measure the value of model predictions for specific scientific discovery outcomes are needed to address this gap. We present PerturbHD, an evaluation framework for AI-enabled hit discovery, to demonstrate the benefits our proposed approach.