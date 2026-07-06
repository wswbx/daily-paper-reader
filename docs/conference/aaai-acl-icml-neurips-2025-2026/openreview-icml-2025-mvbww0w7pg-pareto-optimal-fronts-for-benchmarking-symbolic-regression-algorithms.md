---
title: Pareto-Optimal Fronts for Benchmarking Symbolic Regression Algorithms
title_zh: 用于符号回归算法基准测试的帕累托最优前沿
authors: "Kei Sen Fong, Mehul Motani"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=mvbWw0w7pG"
tags: ["query:sr"]
score: 9.0
evidence: 符号回归基准测试的帕累托前沿方法
tldr: 该论文针对符号回归算法的评估问题，提出绝对帕累托最优解的概念，以R方和表达式长度为指标构建基准测试，解决了传统相对性能比较缺乏效率标尺的局限，为SR方法比较提供了更全面的标准。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有符号回归算法评估常基于相对帕累托支配，缺乏绝对效率标尺。
method: 提出绝对帕累托最优前沿的概念，通过R方与表达式长度的最优权衡来客观比较算法。
result: 展示了如何利用APO解集进行算法评估，揭示了不同SR算法的实际效率。
conclusion: 绝对帕累托前沿为符号回归算法提供了更公平、更信息丰富的基准测试方法。
---

## Abstract
Symbolic Regression (SR) algorithms select expressions based on prediction performance while also keeping the expression lengths short to produce explainable white box models. In this context, SR algorithms can be evaluated by measuring the extent to which the expressions discovered are Pareto-optimal, in the sense of having the best R-squared score for a given expression length. This evaluation is most commonly done based on relative performance, in the sense that an SR algorithm is judged on whether it Pareto-dominates other SR algorithms selected in the analysis, without any indication on efficiency or attainable limits. In this paper, we explore absolute Pareto-optimal (APO) solutions instead, which have the optimal tradeoff between the multiple SR objectives, for 34 datasets in the widely-used SR benchmark, SRBench, by performing exhaustive search. Additionally, we include comparisons between eight numerical optimization methods. We extract, for every dataset, an APO front of expressions that can serve as a universal baseline for SR algorithms that informs researchers of the best attainable performance for selected sizes. The APO fronts provided serves as an important benchmark and performance limit for SR algorithms and is made publicly available at: https://github.com/kentridgeai/SRParetoFronts

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：符号回归（SR）算法需要在预测性能（如 R²）与表达式长度（可解释性）之间进行权衡，但现有评估方法多基于相对帕累托支配（即判断算法是否优于其他被选算法），缺乏一个绝对的效率标尺，无法告知研究者“在给定长度下能达到的最优性能极限”。
- **整体含义**：本文提出“绝对帕累托最优（APO）”概念，通过穷举搜索为每个数据集构建**APO前沿**（即R²与表达式长度的最优权衡曲线），作为SR算法通用基准，从而提供更公平、信息更丰富的性能评估标准。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将SR问题视为多目标优化（最大化R²、最小化表达式长度），定义**绝对帕累托最优解**为在全体可能表达式空间中真正非支配的解（而非仅相对于少数对比算法）。
- **关键技术细节**：
  - 对每个数据集，通过**穷举搜索**（具体方法未在摘要中详细说明，但指出“by performing exhaustive search”）生成所有可能表达式（或足够大的搜索空间），然后依据R²和长度筛选出非支配解，构成APO前沿。
  - 以APO前沿作为**通用基线**：任何SR算法的输出均可映射到该前沿附近，通过距离、覆盖度等指标衡量其效率。
- **算法流程**（文字说明）：
  1. 选定数据集与表达式长度上限。
  2. 穷举生成所有候选表达式（或采用枚举策略）。
  3. 计算每个表达式的R²与长度。
  4. 提取帕累托最优解集（即APO前沿）。
  5. 将APO前沿作为基准，对比各类SR算法输出的表达式离前沿的远近。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：使用广泛采用的SR基准**SRBench**中的**34个数据集**（覆盖不同规模和领域）。
- **基准**：每个数据集对应的APO前沿（由穷举搜索获得）作为通用基准。
- **对比方法**：**8种数值优化方法**（即8种不同的符号回归算法，如遗传编程、线性回归变体等，摘要未具体列出名称）。

### 4. 资源与算力

- **文中未明确说明**使用了何种GPU型号、数量或训练时长。仅提到进行了穷举搜索，但计算成本未量化。如需复现，可参考其GitHub仓库（https://github.com/kentridgeai/SRParetoFronts）中可能的实现细节。

### 5. 实验数量与充分性

- **实验数量**：在34个数据集上分别构建APO前沿，并对比8种SR算法。未提及消融实验。
- **充分性**：
  - **充分**：数据集来自主流SRBench，覆盖多种场景；对比8种方法具有代表性。
  - **客观公平**：APO前沿基于穷举搜索，理论上为真实帕累托边界，避免了相对比较的偏差。
  - **不足**：穷举搜索可能受限于表达式长度上限，未讨论更大空间或更复杂算子（如三角函数、指数等）的覆盖性。

### 6. 论文的主要结论与发现

- APO前沿可以作为SR算法普适的性能极限基准，提供“在给定表达式长度下能达到的最佳R²”的明确信息。
- 通过对比8种数值优化方法，揭示了不同SR算法在实际数据集上的效率差异（如哪些算法更接近APO前沿）。
- 该基准有助于研究者更公平地比较和改进SR算法，推动可解释建模的发展。

### 7. 优点

- **方法新颖**：首次提出绝对帕累托最优前沿用于SR基准测试，替代了传统的相对比较。
- **为领域提供标准**：生成公开可用的APO前沿数据（GitHub可获取），促进可复现研究。
- **直观信息丰富**：研究者能明确知道算法还差多少达到理论最优，而非仅知道比对手好。

### 8. 不足与局限

- **穷举搜索的可行性**：当表达式空间极大（如包含更多操作符、变量数多）时，穷举搜索可能不现实，本工作的有效性依赖于搜索空间的合理裁剪。
- **指标单一**：仅使用R²与长度，未考虑其他常见指标（如MSE、AIC、BIC或模型复杂度度量），可能不够全面。
- **未讨论数据集规模差异**：34个数据集大小差异未说明，可能影响穷举搜索的可行性及前沿的代表性。
- **未提供算力成本**：缺少计算资源描述，难以评估方法推广性。

（完）
