---
title: "Single-cell foundation models benefit from cross-modal training: adding proteomics data beats parameter scaling"
title_zh: 单细胞基础模型受益于跨模态训练：添加蛋白质组学数据优于参数扩展
authors: "Burq, M., Stepec, D., Kim, C., Cimermancic, P."
date: 2026-08-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.14.744845v1.full.pdf"
tags: ["query:tabular-fm"]
score: 7.0
evidence: 单细胞基础模型的跨模态训练，直接涉及单细胞表格数据的基础模型
tldr: 单细胞基础模型多依赖RNA大规模扩展。本文引入跨模态持续预训练，在大型蛋白质组学数据上微调Tahoe-x1。70M参数训练一epoch即在多数基准超过1B/3B RNA-only模型，且改善蛋白质扰动预测。表明扩充异质蛋白质组学数据比纯参数扩展更有效，为多模态生物模型提供新路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞模型仅靠扩大RNA数据规模，本文探究加入蛋白质组学模态能否带来更大收益。
method: 对70M参数的Tahoe-x1在440项质谱研究的48843个蛋白质组样本上进行跨模态持续预训练。
result: 在多数Tahoe-x1基准上匹配或超过1B/3B RNA-only模型，并提升蛋白质扰动预测性能。
conclusion: 精心策划的蛋白质组学数据比参数扩展收益更大，多模态预训练是生物基础模型的有前景方向。
---

## 摘要
领先的细胞基础模型已在数亿个单细胞转录组上进行了训练，其进展日益依赖于更大的数据集和模型规模的扩展。在此，我们探究了在仅扩展RNA-only模型的基础上，添加蛋白质组学模态是否能够改善基因水平和细胞水平的表征。我们引入了跨模态持续预训练，在一个大型蛋白质组学图谱语料库上对已发布的单细胞模型（Tahoe-x1）进行微调。仅在一个周期内，对来自440项不同质谱研究的48843个蛋白质组学样本训练一个7000万参数的Tahoe-x1模型，在Tahoe-x1原始评估基准的大多数指标上，匹配或超过了10亿和30亿参数的RNA-only模型。这表明，采用正确的训练方案，异质性的蛋白质组学数据能够改善单细胞RNA-seq样本的学习表征，展现出强大的分布外泛化能力。跨模态预训练还改善了对一个保留的蛋白质扰动基准的迁移，而在该基准上，仅扩展RNA-only模型无法提供同等的收益。这些结果表明，对蛋白质组学数据进行精心的针对性筛选所带来的效益可能超过单纯增加模型规模，并提示多模态预训练是迈向更具信息量的生物基础模型的一条有前景的路径。

## Abstract
Leading cellular foundation models have been trained on hundreds of millions of single-cell transcriptomes, with progress increasingly driven by larger datasets and model scaling. Here, we asked whether adding a proteomics modality can improve gene-level and cell-level representations beyond scaling RNA-only models. We introduce cross-modal continued pretraining, fine-tuning a published single-cell model (Tahoe-x1) on a large corpus of proteomic profiles. Training a 70M-parameter Tahoe-x1 model for a single epoch on 48843 proteomic samples from 440 diverse mass-spectrometry studies matched or exceeded 1B- and 3B-parameter RNA-only models across most of the original Tahoe-x1 evaluation benchmarks. This shows that with the right training recipe, heterogeneous proteomics data can improve the learned representations of single-cell RNAseq samples, demonstrating strong out-of-distribution generalization. Cross-modal pretraining also improves transfer to a held-out protein perturbation benchmark, where scaling the RNA-only model does not provide comparable benefits. These results demonstrate that careful targeted curation of proteomics data can provide larger benefits than increasing the model size alone and suggest that multimodal pretraining is a promising path toward more informative biological foundation models.