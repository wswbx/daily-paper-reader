---
title: Keeping SCORE enables interpretable uncertainty-aware classification from diffusion models for genomics
title_zh: 保持SCORE使得从扩散模型中进行可解释的、具有不确定性感知的基因组学分类成为可能
authors: "Kuznets-Speck, B., Jung, J., Pholraksa, P., Zhong, A., Schwartz, L., Prashnani, E., Vaikuntanathan, S., Goyal, Y."
date: 2026-05-13
pdf: "https://www.biorxiv.org/content/10.1101/2025.11.26.690838v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 7.0
evidence: AI在基因组学分类中的可解释应用
tldr: 针对基因组学分类任务需要准确、可解释和不确定性校准的需求，提出Keeping SCORE框架，通过计算条件扩散模型沿随机噪声轨迹的精确似然，将其转化为概率分类与回归引擎。在图像识别、单细胞转录组（22M细胞、164类）、CRISPRi遗传扰动和蛋白质稳定性回归任务中，精度匹配或超越现有方法，并提供后验概率和特征归因，且无需重新训练或修改架构。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有非线性分类器虽准确但缺乏不确定性量化和对关键特征的可解释性。
method: 通过计算条件扩散模型沿随机噪声轨迹的精确似然，实现端到端的不确定性感知分类与回归。
result: 在单细胞分类（22M细胞、164类）、遗传扰动预测和蛋白质稳定性回归任务中，精度匹配或超越判别式基线，并提供后验概率和特征归因。
conclusion: Keeping SCORE无需重新训练或架构改变，即可为基因组学提供便携、可解释且不确定性感知的预测工具。
---

## 摘要
从高维分子和基因组测量中分类细胞状态，需要的方法不仅要提供准确的预测，还要提供校准的不确定性和可解释性。当前的非线性分类器提供了准确性，但通常缺乏不确定性量化以及对最重要特征的机制性洞察。我们引入了Keeping SCORE框架，该框架通过沿着随机加噪轨迹计算精确的似然，将条件扩散模型转化为用于分类和回归的概率引擎。我们首先在图像识别任务（手写数字、自然照片）上对Keeping SCORE进行了基准测试。然后，我们将Keeping SCORE应用于跨越2200万细胞图谱的单细胞转录组学，对164种细胞类型进行分类，其准确性与最先进的方法相当或超越，同时独特地提供了后验概率估计和预测置信度。对于跨多研究Perturb-seq数据集中100个CRISPRi条件的遗传扰动映射，我们的方法再次匹配或超越了判别基线，并通过特征级归因识别驱动每个决策的基因组特征。应用于大规模蛋白质序列数据时，我们的框架准确回归了突变稳定性效应，并将这些效应定量归因于输入序列上的位置。Keeping SCORE不需要对现有扩散模型进行重新训练或架构更改，为生物发现提供了可移植、可解释且具有不确定性感知的预测。

## Abstract
Classifying cellular states from high-dimensional molecular and genomic measurements requires methods that provide not only accurate predictions but also calibrated uncertainty and interpretability. Current nonlinear classifiers offer accuracy but often lack uncertainty quantification and mechanistic insights into the features that matter most. We introduce Keeping SCORE, a framework that transforms conditional diffusion models into probabilistic engines for classification and regression by computing exact likelihoods along stochastic noising trajectories. We first benchmark Keeping SCORE on image recognition tasks (handwritten digits, natural photos). We then apply Keeping SCORE to single-cell transcriptomics across a 22-million-cell atlas, classifying 164 cell types with accuracy matching or exceeding state-of-the-art methods, while uniquely providing posterior probability estimates and prediction confidence. For genetic perturbation mapping across 100 CRISPRi conditions in a multi-study Perturb-seq dataset, our approach again matches or surpasses discriminative baselines, with feature-level attributions identifying which genomic features drive each decision. Applied to large-scale protein sequence data, our framework accurately regresses mutational stability effects, attributing them quantitatively to positions along the input sequence. Keeping SCORE requires no retraining or architectural changes to existing diffusion models, providing portable, interpretable, and uncertainty-aware predictions for biological discovery.