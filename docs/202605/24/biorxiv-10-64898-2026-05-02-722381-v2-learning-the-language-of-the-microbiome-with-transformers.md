---
title: Learning the Language of the Microbiome with Transformers
title_zh: 用Transformer学习微生物组的语言
authors: "Treloar, N. J., Ur-Rehman, S., Yang, J."
date: 2026-05-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.02.722381v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 6.0
evidence: 微生物组科学中的自监督预训练
tldr: 针对微生物组数据自监督预训练研究不足的问题，本文构建了包含53.9万数据点的Atlas数据集，训练了6M-170M参数的Waypoint系列GPT-2模型，并提出包含8个任务的Compass基准。实验表明，预训练显著提升下游任务性能，数据规模和分词策略影响模型质量，超1万样本时Transformer优于经典方法，Waypoint达到微生物组基础模型最佳水平。
source: biorxiv
selection_source: fresh_fetch
motivation: 微生物组数据在自监督预训练领域探索不足，缺乏大规模数据集和统一评估框架。
method: 构建Atlas数据集训练Waypoint系列GPT-2模型，并设计Compass基准评估8个预测任务。
result: 预训练持续提升下游性能，数据规模与分词策略影响模型质量，超过约1万样本时Transformer优于经典方法，Waypoint达到SOTA。
conclusion: 大规模自监督预训练对微生物组学习至关重要，Atlas、Compass和Waypoint为该领域提供了有价值资源。
---

## 摘要
自监督预训练已成为生物机器学习的核心，然而在建模方法和评估框架方面，微生物组数据仍相对未充分探索。为填补这一空白，我们提出了Atlas，这是一个来自MGnify数据库的超过53.9万个微生物组数据点的预训练数据集。利用Atlas，我们训练了Waypoint系列微生物组基础模型：一系列GPT-2风格的因果语言模型，参数规模从600万到1.7亿不等。我们还引入了Compass，这是一个包含八项预测任务的精选基准，涵盖生物群落分类、药物-微生物组相互作用、药物降解以及婴儿肠道发育。利用该基准，我们将Waypoint模型的性能与经典基线及现有的MGM基础模型进行了比较。结果表明，预训练带来了下游任务性能的一致且显著的提升，数据集规模和分词策略都影响模型质量，并且预训练对于实现有利的扩展行为至关重要。此外，一旦训练数据超过约1万个样本——这是现代微生物组研究可达到的阈值——预训练Transformer模型开始可靠地优于经典方法。最后，我们证明Waypoint模型在微生物组基础模型中达到了最先进的性能。总体而言，我们的工作强调了该领域大规模自监督预训练的重要性，并将Atlas、Compass和Waypoint模型确立为这一新兴领域研究社区的宝贵资源。

## Abstract
Self-supervised pretraining has become central to biological machine learning, yet microbiome data remains comparatively underexplored in terms of both modeling approaches and evaluation frameworks. To address this gap, we present Atlas, a pretraining dataset of over 539,000 microbiome datapoints from the MGnify database. Using Atlas, we train the Waypoint family of microbiome foundation models: a series of GPT-2 style causal language models ranging from 6M to 170M parameters. We also introduce Compass, a curated benchmark of eight predictive tasks spanning biome classification, drug-microbiome interactions, drug degradation, and infant gut development. Using this benchmark, we compare the performance of Waypoint models against classical baselines and the existing MGM foundation model. Our results show that pretraining leads to consistent and significant improvements in downstream task performance, that both dataset scale and tokenization strategy impact model quality, and that pretraining is essential for achieving favorable scaling behavior. Furthermore, pretrained transformer models begin to reliably outperform classical methods once training data exceeds roughly 10,000 examples - a threshold that is attainable for modern microbiome studies. Finally, we demonstrate that the Waypoint models achieve state-of-the-art performance among microbiome foundation models. Overall, our work highlights the importance of large-scale self-supervised pretraining in this domain and establishes Atlas, Compass, and the Waypoint models as valuable resources for the research community in this emerging field.