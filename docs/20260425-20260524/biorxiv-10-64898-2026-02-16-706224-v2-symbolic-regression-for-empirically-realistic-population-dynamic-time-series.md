---
title: Symbolic regression for empirically realistic population dynamic time series
title_zh: 符号回归用于经验现实的种群动态时间序列
authors: "Jarman, C. N., Levi, T., Novak, M."
date: 2026-05-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.16.706224v2.full.pdf"
tags: ["query:sr"]
score: 8.0
evidence: 用于种群动态的符号回归
tldr: 本研究评估符号回归在生态学实地种群动态时间序列中的实用性，通过合成数据模拟采样密度、周期不对称、过程噪声和虚假变量等现实条件。结果表明，低采样密度下符号回归失效，高密度时过程噪声反而提高方程恢复率，但现有评估准则无法一致甄别真实模型，亟需更稳健的选择标准。
source: biorxiv
selection_source: fresh_fetch
motivation: 实地种群动态时间序列缺乏理想化特性，需评估符号回归在非理想条件下的表现。
method: 采用合成数据，改变采样密度、周期不对称性、过程噪声和虚假变量，比较两种数据预处理和四种方程评估工作流。
result: 采样密度低于每周期10点时符号回归失效；高于25点时频繁恢复真实模型，但评估工作流未能始终选择它。
conclusion: 现有后算法选择准则不足，需要更鲁棒的方程选择方法以从候选模型中找出目标方程。
---

## 摘要
机器学习在生态学中的应用正在迅速扩展。符号回归因其在从模拟和实验室种群时间序列中逆向工程可读的解释性种群模型（包括逻辑增长和Lotka-Volterra方程）方面的成功而受到特别关注。然而，野外种群通常缺乏先前评估中使用的理想化时间序列的特征。我们通过量化符号回归在采样密度、种群周期不对称性、过程噪声以及错误考虑虚假变量等合成数据中的成功程度，评估了符号回归对此类时间序列的实用性。我们进一步比较了两种用于估计种群增长率的预处理选项，以及四种用于选择方程的评估工作流程。结果表明，采样密度与过程噪声之间的权衡主要驱动了方程和变量的恢复。当每个周期的采样密度低于10个点时，符号回归无法恢复底层方程；然而，在更高的采样密度下，过程噪声确实提高了方程恢复率。重要的是，尽管在每个周期25个或更多点的采样密度下经常恢复真实模型，但评估工作流程并未一致地选择它。这种差异凸显了需要更鲁棒的算法后选择标准，以便在竞争候选者中识别焦点方程。

## Abstract
Applications of machine learning in ecology are rapidly expanding. Symbolic regression is gaining particular attention for its success in reverse-engineering human-readable explanatory population models, including the logistic growth and Lotka-Volterra equations, from simulated and laboratory-based population time series. However, field-based populations often lack the characteristics of the idealized time series used in prior assessments. We evaluated the utility of symbolic regression for such time series by quantifying its success for synthetic data varying in sampling density, population cycle asymmetry, process noise, and the erroneous consideration of spurious variables. We further compared two data preprocessing options for estimating population growth rates, and four evaluation workflows for selecting equations. Results indicate that a trade-off between sampling density and process noise primarily drives equation and variable recovery. Symbolic regression failed to recover the underlying equation at sampling densities below 10 points per cycle; however, at higher sampling densities, process noise did increase equation recovery rates. Importantly, although the true model was frequently recovered at sampling densities of 25 or more points per cycle, it was not consistently selected by the evaluation workflows. This discrepancy highlights a need for more robust post-algorithm selection criteria to identify the focal equation among competing candidates.