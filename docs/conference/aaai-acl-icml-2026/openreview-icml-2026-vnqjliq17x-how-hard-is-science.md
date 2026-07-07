---
title: How Hard Is Science?
title_zh: 科学有多难？
authors: "Adil Soubki, Miles Cranmer"
date: 2026-04-30
pdf: "https://openreview.net/pdf/56f6caa041c942450ef5c3b8a03d30b78e3740c4.pdf"
tags: ["query:sr"]
score: 8.0
evidence: 符号回归复杂度的理论分析
tldr: "本文从参数化复杂度理论重新审视符号回归的NP难问题。证明当以表达式深度或树大小为参数时，符号回归是固定参数可解的（FPT），为实际算法的高效搜索提供了理论依据；但同时表明当参数为原始函数数量时是W[1]-难的。该工作弥合了最坏情况难度与实际成功之间的鸿沟。"
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 符号回归NP难但实际算法有效，理论与实践的差距需要解释。
method: 使用参数化复杂度理论分析SR的易处理性。
result: SR在表达式深度或树大小参数下是FPT的。
conclusion: 参数化复杂度解释了SR实际可解的原因。
---

## Abstract
Symbolic Regression (SR) is the task of finding a closed-form mathematical expression that optimizes some objective. Solving this task is NP-hard. However, SR software routinely discovers accurate, interpretable models without exhaustively searching function space. 
Motivated by this disconnect between worst-case theory and practical success, we study SR through the lens of \emph{parameterized complexity theory}. In particular, we reanalyze tractability with respect to practically relevant parameters like expression depth, tree size, and number of primitives used. We show that SR is fixed-parameter tractable (FPT) when parameterized by expression depth or tree size, formalizing the tractable regime exploited by bounded-complexity search in popular SR algorithms. However, SR becomes W[1]-hard when parameterized by the number of variables or primitives used, identifying selection as a source of intractability. We further find lower bounds under the exponential time hypothesis, prove approximation hardness, and rule out polynomial kernels for the case where the primitive set is part of the input.

---

## 论文详细总结（自动生成）

# 科学有多难？——论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
符号回归（Symbolic Regression, SR）的目标是从数据中自动发现封闭形式的数学表达式，以优化某个目标函数。该问题被证明是NP难的，这意味着在最坏情况下，求解器需要指数级时间。然而，实际中的符号回归软件（如基于遗传编程、贝叶斯方法等）却能够在不穷举函数空间的前提下，频繁地发现准确且可解释的模型。这种**最坏情况理论难度与实际算法成功之间的显著差距**构成了论文的核心研究动机。作者试图引入**参数化复杂度理论**（Parameterized Complexity Theory）来重新审视符号回归的易处理性，从而解释为什么在实际场景中问题往往可以被高效求解。

## 2. 方法论：核心思想、关键技术细节
### 核心思想
论文将符号回归问题视为一个参数化问题，通过选择**实际相关的参数**（如表达式深度、树大小、原始函数数量等）来刻画问题的结构复杂度，而不是仅仅考虑输入规模（样本数或变量数）。作者利用参数化复杂度理论中的**固定参数可解性（FPT）** 和**W[]-难性**来刻画不同参数化下的算法下界与上界。

### 关键技术细节
- **参数化定义**：将符号回归问题参数化为 \((x, k)\)，其中 \(k\) 是所关注的参数（如树深度 \(d\)、树大小 \(s\)、原始函数数量 \(p\)、变量个数 \(n\) 等）。
- **FPT 结果**：当参数化为**表达式深度**或**树大小**时，证明符号回归是**固定参数可解的（FPT）**，即存在算法时间复杂度为 \(O(f(k) \cdot n^c)\)，其中 \(f(k)\) 是仅依赖于参数 \(k\) 的函数，\(c\) 是常数。这形式化了流行符号回归算法（如限制表达式复杂度的搜索）所利用的**可处理区域**。
- **W[1]-难结果**：当参数化为**变量个数**或**原始函数数量**时，证明符号回归是 **W[1]-难的**，意味着在这些参数下问题不太可能具有FPT算法（除非层次化复杂度发生坍塌）。这识别出“选择哪些原始函数或变量”是导致不可处理性（intractability）的根源。
- **其他下界**：基于**指数时间假设（ETH）** 推导出更紧的计算复杂性下界；证明了近似困难性；并排除了当原始函数集合作为输入一部分时存在多项式核的可能性（即不能将问题压缩到多项式规模的内核）。

### 算法流程（文字说明）
论文未提供具体算法实现，而是进行理论分析：通过归约证明SR在特定参数下属于FPT（例如，通过分支定界或动态规划在深度限制下进行搜索），或通过从已知W[1]-难问题（如k-团、多色团等）归约证明SR的W[1]-难性。

## 3. 实验设计
**由于论文本质为理论分析论文，并未包含实验部分**。文中未使用任何数据集、基准测试或对比方法。所有论证均基于数学推导和复杂性归约，属于纯理论贡献。

## 4. 资源与算力
论文未提及任何计算资源（GPU型号、数量、训练时长等），因为不涉及实验。理论工作不需要算力支撑。

## 5. 实验数量与充分性
不适用。论文没有实验，无法评价实验充分性。但理论证明的严谨性通常通过构造归约、引用已知复杂度结论以及逻辑推理来保证。从提供的元数据看，论文被ICML-2026接受（假设），说明其理论论证应已通过同行评审。

## 6. 主要结论与发现
1. **符号回归在表达式深度或树大小参数化下是FPT的**——这解释了为何实际中通过限制表达式复杂度的SR算法（如遗传编程中的深度限制、贝叶斯符号回归的树先验）能够高效运行。
2. **符号回归在变量个数或原始函数数量参数化下是W[1]-难的**——这说明了变量选择和函数库选择是导致困难的核心因素，当需要从大量候选函数中选择时，问题变得极其困难。
3. 基于ETH的下界和近似困难性进一步强化了这些结果：即使是近似解也难以在理论时间下找到。
4. 排除了多项式核的存在性，意味着问题无法被有效压缩到小空间内。

这些结论弥合了理论与实践的鸿沟：实际中SR有效是因为算法通常隐式地约束了表达式深度或大小，而变量/函数选择要么被预先简化，要么使用启发式方法处理。

## 7. 优点
- **问题定位精准**：敏锐地捕捉到符号回归NP难但实际可解的矛盾，并引入合适的理论工具（参数化复杂度）进行解释。
- **理论创新**：首次系统性地将参数化复杂度理论应用于符号回归的易处理性分析，提供了关于可解性边界的明确刻画。
- **参数选择合理**：所选参数（深度、树大小、变量数、函数数）均为实际SR算法中的关键设计维度，具有直接指导意义。
- **结果完整**：既给出了正面的FPT结果，也给出了负面的W[1]-难结果以及下界，形成了完整的图景。

## 8. 不足与局限
- **缺乏实证验证**：作为纯理论论文，没有通过实际数据集或模拟实验来验证FPT结果在真实场景中的计算意义（例如，参数k的实际典型值是否足够小使得FPT算法可行）。
- **未提出具体FPT算法**：仅证明了存在性，未给出实用的算法实现，因此对实践者的直接帮助有限（尽管它为设计高效算法提供了理论基础）。
- **忽略其他实际因素**：真实SR中还有噪声、缺失数据、多目标优化等问题，论文的模型可能过于简化。
- **应用限制**：W[1]-难结果表明当变量/函数很多时问题仍然困难，但实际中常使用特征选择或领域知识缩减搜索空间，论文未讨论这些启发式方法对参数化复杂度的影响。

（完）
