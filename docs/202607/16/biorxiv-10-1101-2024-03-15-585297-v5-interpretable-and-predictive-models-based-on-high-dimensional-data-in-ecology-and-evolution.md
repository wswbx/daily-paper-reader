---
title: Interpretable and predictive models based on high-dimensional data in ecology and evolution
title_zh: 基于高维数据的生态学与进化生物学可解释与预测模型
authors: "Jahner, J. P., Buerkle, C. A., Gannon, D. G., Grames, E. M., McFarlane, S. E., Siefert, A., Bell, K. L., DeLeo, V. L., Forister, M. L., Harrison, J. G., Laughlin, D. C., Patterson, A. C., Powers, B. F., Werner, C. M., Oleksy, I. A."
date: 2026-07-08
pdf: "https://www.biorxiv.org/content/10.1101/2024.03.15.585297v5.full.pdf"
tags: ["query:sr"]
score: 7.0
evidence: 比较九种变量选择与预测方法
tldr: 生态与进化生物学中的高维数据易导致过拟合，即模型在样本内预测良好但泛化能力差。本文在模拟不同样本量、变量数和效应强度的数据集上对比了九种变量选择与预测方法。结果发现多数方法存在过拟合，但部分稀疏方法能平衡预测精度与过拟合。研究表明准确变量选择在现实采样中难以实现，并总结了统计学习可行的数据特征，为高维数据建模提供指导。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2024-03-15-585297-v5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1373, \"height\": 1344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2024-03-15-585297-v5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1686, \"height\": 1019, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2024-03-15-585297-v5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1681, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2024-03-15-585297-v5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1680, \"height\": 755, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-1101-2024-03-15-585297-v5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1299, \"height\": 1350, \"label\": \"Figure\"}]"
motivation: 高维数据在生态进化模型中存在过拟合与预测泛化能力的权衡问题。
method: 通过模拟不同样本量、变量数和效应强度的数据集，竞争九种变量选择与预测方法。
result: 多数方法存在过拟合，但在大样本和强效应下内外样本预测收敛；准确变量选择难以实现。
conclusion: 稀疏方法可提升预测准确性并控制过拟合，需根据数据特征选择合适方法。
---

## 摘要
生态学和进化生物学中高维数据的激增，为高度可预测且可解释的统计学和机器学习模型带来了希望。然而，高维数据通常存在固有的权衡：随着模型中包含更多变量，样本内预测结果会改善，但这可能以牺牲未来或未采样观测（样本外预测）的预测准确性和泛化能力为代价。为了应对这种过拟合问题，稀疏模型可以通过正确地对不重要变量赋予低权重来聚焦关键变量。我们比较了九种方法，使用不同样本量、变量数量和效应强度的模拟数据，量化它们在变量选择和预测中的表现。过拟合在多种方法和模拟场景中很常见。尽管如此，对于具有更多观测、更大因果效应和更少变量的模拟，样本内和样本外预测都收敛于真实预测目标。对于生态学和进化生物学中许多实际采样方案，支持基于过程理解的准确变量选择将难以实现。我们利用分析来刻画统计学习可能的数据属性，并说明一些稀疏方法如何在减轻和了解过拟合程度的同时实现预测准确性。

## Abstract
The proliferation of high-dimensional data in ecology and evolutionary biology raises the promise of statistical and machine learning models that are highly predictive and interpretable. However, high-dimensional data are commonly burdened with an inherent trade-off: in-sample prediction of outcomes will improve as additional variables are included in the model, but this may come at the cost of poor predictive accuracy and limited generalizability for future or unsampled observations (out-of-sample prediction). To confront this problem of overfitting, sparse models can focus on key variables by correctly placing low weight on unimportant variables. We competed nine methods to quantify their performance in variable selection and prediction using simulated data with different sample sizes, numbers of variables, and strengths of effects. Overfitting was typical for many methods and simulation scenarios. Despite this, in-sample and out-of-sample prediction converged on the true predictive target for simulations with more observations, larger causal effects, and fewer variables. Accurate variable selection to support process-based understanding will be unattainable for many realistic sampling schemes in ecology and evolution. We use our analyses to characterize data attributes for which statistical learning is possible, and illustrate how some sparse methods can achieve predictive accuracy while mitigating and learning the extent of overfitting.