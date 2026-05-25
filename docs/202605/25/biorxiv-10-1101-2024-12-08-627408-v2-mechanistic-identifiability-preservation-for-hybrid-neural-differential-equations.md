---
title: Mechanistic Identifiability Preservation for Hybrid Neural Differential Equations
title_zh: 混合神经微分方程的机理可辨识性保持
authors: "Whipple, B., Hernandez-Vargas, E. A."
date: 2026-05-23
pdf: "https://www.biorxiv.org/content/10.1101/2024.12.08.627408v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 6.0
evidence: 混合神经常微分方程保持机械可辨识性用于科学建模
tldr: 混合神经常微分方程（HNDEs）将神经网络嵌入机械模型中，结合了结构可解释性和逼近能力。本文针对其可能损害机械可辨识性的问题，建立了理论框架，形式化了有界神经校正类，推导了轨迹和观测差异界限，并给出了近似机械参数可恢复性的充分条件。经验似然分析证实了神经网络增强会系统性削弱可辨识性，揭示了表达性与可辨识性之间的权衡。
source: biorxiv
selection_source: fresh_fetch
motivation: 神经网络增强可能导致观测简并，损害混合模型中机械参数的可辨识性和科学可解释性。
method: 通过形式化有界神经校正类并推导Gronwall型轨迹与观测差异界限，建立近似机械参数可恢复性的充分条件。
result: 神经网络增强会系统性削弱但不会消除机械可辨识性，存在表达性与可辨识性的根本权衡。
conclusion: 为在科学智能计算中部署HNDEs提供了理论基础和可操作的指导。
---

## 摘要
混合神经微分方程（HNDEs）将神经网络组件嵌入机理支架中，结合了领域模型的结构可解释性与神经动力学的逼近能力。尽管它们在生物学和工程学中的应用日益广泛，但神经增强可能引入观测简并性，损害机理可辨识性和科学可解释性。在本文中，我们开发了一个理论框架，用于在实际中保持HNDEs的机理可辨识性。我们形式化了有界神经校正类，并推导了Gronwall型轨迹与观测差异界限，将神经扰动与机理参数模糊性联系起来。我们进一步建立了充分条件，在此条件下，混合神经校正能够保持近似机理参数的可恢复性，且容忍度可显式量化。对基准系统的经验似然剖面分析证实，神经增强系统地削弱了（但并未消除）机理可辨识性，揭示了表达性与可辨识性之间的基本权衡。这些结果为在科学智能计算中部署HNDEs提供了理论基础和可操作的指导。

## Abstract
Hybrid neural differential equations (HNDEs) embed neural network components within mechanistic scaffolds, combining the structural interpretability of domain-derived models with the approximation power of neural dynamics. Despite their growing adoption in biology and engineering, neural augmentation can introduce observational degeneracies that compromise mechanistic identifiability and scientific interpretability. In this paper, we develop a theoretical framework for practical preservation of mechanistic identifiability in HNDEs. We formalize bounded neural correction classes and derive Gronwall-type trajectory and observational discrepancy bounds linking neural perturbations to mechanistic parameter ambiguity. We further establish sufficient conditions under which hybrid neural corrections preserve approximate mechanistic parameter recoverability up to explicitly quantifiable tolerances. Empirical likelihood profile analyses on benchmark systems confirm that neural augmentation systematically weakens---but does not eliminate---mechanistic identifiability, revealing a fundamental expressiveness--identifiability trade-off. These results provide theoretical foundations and actionable guidance for deploying HNDEs in scientific intelligent computing.