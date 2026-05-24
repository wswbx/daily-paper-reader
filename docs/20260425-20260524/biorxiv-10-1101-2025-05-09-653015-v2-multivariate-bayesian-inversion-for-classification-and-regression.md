---
title: Multivariate Bayesian Inversion for Classification and Regression
title_zh: 分类与回归的多变量贝叶斯反演
authors: "Soch, J., Allefeld, C."
date: 2026-05-18
pdf: "https://www.biorxiv.org/content/10.1101/2025.05.09.653015v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 6.0
evidence: 统计方法可用于科学发现中的分类回归任务
tldr: 该论文提出多变量贝叶斯反演（MBI）方法，通过将监督学习转化为贝叶斯推断和模型比较，使用多变量一般线性模型（MGLM）与先验分布，给出新的分类规则和回归预测，在模拟和实际数据上展示了可解释性、先验知识融入和概率预测的优势。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统算法机器学习缺乏可解释性和概率预测，论文旨在提出一种统计建模方法作为替代。
method: 采用MGLM描述标签对特征的影响，结合先验分布进行贝叶斯推断估计参数，并通过贝叶斯模型比较进行预测。
result: 推导出新的分类规则和回归预测，实验表明该方法可解释性强、能融入先验知识并提供概率预测。
conclusion: MBI方法具有解释性、可融入先验知识和概率预测等优点，并讨论了未来潜力。
---

## 摘要
我们提出了一种统计建模方法用于监督学习（即根据特征预测标签），作为算法机器学习（ML）的替代方案。该方法通过采用多变量一般线性模型（MGLM）来描述标签对特征的影响（可能考虑无关协变量），并结合模型参数的先验分布来展示。ML的“训练”被转化为通过贝叶斯推断估计MGLM参数，而ML的“测试”或应用则被转化为贝叶斯模型比较——这种互逆关系我们称之为多变量贝叶斯反演（MBI）。我们针对监督学习的标准情形（离散分类和连续回归）设计了MBI算法，推导了新的分类规则和回归预测，并使用实际例子（模拟数据和真实数据）来说明统计建模方法的优势：可解释性、先验知识的融入、概率性预测。最后，我们讨论了MBI的进一步优势、劣势及未来潜力。

## Abstract
We propose the statistical modelling approach to supervised learning (i.e. predicting labels from features) as an alternative to algorithmic machine learning (ML). The approach is demonstrated by employing a multivariate general linear model (MGLM) describing the effects of labels on features, possibly accounting for covariates of no interest, in combination with prior distributions on the model parameters. ML "training" is translated into estimating the MGLM parameters via Bayesian inference and ML "testing" or application is translated into Bayesian model comparison - a reciprocal relationship we refer to as multivariate Bayesian inversion (MBI). We devise MBI algorithms for the standard cases of supervised learning, discrete classification and continuous regression, derive novel classification rules and regression predictions, and use practical examples (simulated and real data) to illustrate benefits of the statistical modelling approach: interpretability, incorporation of prior knowledge, probabilistic predictions. We close by discussing further advantages, disadvantages and the future potential of MBI.