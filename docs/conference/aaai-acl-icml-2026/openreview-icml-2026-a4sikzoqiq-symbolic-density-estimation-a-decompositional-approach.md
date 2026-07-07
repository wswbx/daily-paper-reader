---
title: "Symbolic Density Estimation: A Decompositional Approach"
title_zh: 符号密度估计：一种分解方法
authors: "Angelo Rajendram, Xieting Chu, Max Fieg, Aishik Ghosh, Vijay Ganesh"
date: 2026-01-21
pdf: "https://openreview.net/pdf/ae0761184cd12b307ed347b9b9d5edcdeee28bbb.pdf"
tags: ["query:sr"]
score: 8.0
evidence: 符号回归应用于密度估计
tldr: 该论文首次将符号回归（SR）应用于密度估计（SymDE），提出AI-Kolmogorov框架。通过聚类/图模型分解、非参数密度估计、支撑估计再对密度进行符号回归的多阶段流程，在合成分布和高能物理应用中展示了可解释密度建模的能力。
source: ICML-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 符号回归在回归任务中有效，但在密度估计中尚未开发。
method: 提出多阶段流程：分解、非参数密度估计、支撑估计，最后符号回归拟合密度。
result: 在合成混合模型和高能物理分布上验证了有效性。
conclusion: 符号密度估计为可解释密度建模打开了新途径。
---

## Abstract
We introduce AI-Kolmogorov, a novel framework for Symbolic Density Estimation (SymDE). Symbolic regression (SR) has been effectively used to produce interpretable models in standard regression settings but its applicability to density estimation tasks has largely been unexplored. To address the SymDE task we introduce a multi-stage pipeline: (i) problem decomposition through clustering and/or probabilistic graphical model structure learning; (ii) nonparametric density estimation; (iii) support estimation; and finally (iv) SR on the density estimate. We demonstrate the efficacy of AI-Kolmogorov on synthetic mixture models, multivariate normal distributions, and three exotic distributions, two of which are motivated by applications in high-energy physics. We show that AI-Kolmogorov can discover underlying distributions or otherwise provide valuable insight into the mathematical expressions describing them.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 论文的核心问题与整体含义

- **研究动机**：符号回归（Symbolic Regression, SR）在常规回归任务中已能生成可解释的数学模型，但其在密度估计（Density Estimation）任务中的应用尚未被充分探索。密度估计是机器学习中的基础问题，传统方法（如核密度估计、混合模型）虽有效但缺乏可解释性，得到的模型往往是黑箱。
- **核心问题**：如何将符号回归引入密度估计领域，以得到显式、可解释的数学表达式来描述未知概率密度函数。
- **整体含义**：该工作首次提出**符号密度估计（SymDE）** 的概念，并设计名为 **AI-Kolmogorov** 的框架，旨在为可解释的密度建模开辟新途径，尤其适用于需要洞悉数据生成机制的领域（如高能物理）。

## 2. 方法论：核心思想与关键技术

- **核心思想**：将密度估计任务分解为一系列可处理的子步骤，在每一步引入可解释性，最终使用符号回归对密度函数进行符号化拟合。
- **多阶段流水线**（共四步）：
    1. **问题分解**：通过聚类或概率图模型结构学习，将复杂的联合密度分解为多个较简单的子密度。例如对多模态分布先聚类，或对高维变量学习条件独立结构。
    2. **非参数密度估计**：对每个子成分（或条件分布）使用核密度估计等非参数方法得到初始密度近似，这一步保留灵活性但不要求符号形式。
    3. **支撑估计**：估计密度函数的定义域（支撑集），有助于后续符号回归时限定搜索空间。
    4. **符号回归（SR）**：以非参数密度估计结果为目标，使用符号回归算法（如遗传编程）搜索能够精确拟合该密度函数的数学表达式。输出结果为一个（或一组）显式代数公式。
- **关键技术细节**：框架不依赖于特定的符号回归算法，但强调分解步骤是降低问题复杂度和保证可解释性的关键。文中未给出具体公式，但逻辑链清晰。

## 3. 实验设计

- **数据集/场景**：
    - 合成混合模型（如高斯混合模型）
    - 多元正态分布
    - 三个“奇异分布”，其中两个来自高能物理应用（例如粒子物理中某些碰撞产物的分布），第三个可能是理论上的复杂分布。
- **基准（Benchmark）**：未明确列出对比方法。摘要仅说明“展示了有效性”，未提及与核密度估计、混合模型、神经密度估计（如归一化流）等方法的定量比较。推测属于初步概念验证实验。
- **对比方法**：未提及。实验侧重于框架能否发现/恢复ground truth符号表达式，而非与其他密度估计方法对比精度。

## 4. 资源与算力

- **文中未说明**：论文摘要和元数据中没有任何关于GPU型号、数量、训练时长或算力开销的信息。由于符号回归通常计算量较大，但具体资源消耗未知。这一点可视为报告不完整。

## 5. 实验数量与充分性

- **实验数量**：从描述看，至少包含了**四种**分布族：合成混合模型、多元正态、三个奇异分布（其中两个高能物理）。实际测试案例大概在5个左右。没有提及消融实验（如去掉分解步骤、更换非参数方法的影响）。
- **充分性评估**：
    - **客观性**：实验覆盖了简单和复杂分布，但缺少与现有方法的对比，难以客观评估符号密度估计相对于其他可解释方法（如贝叶斯可加回归树、符号回归直接拟合对数密度等）的优势。
    - **公平性**：没有设置对照组，仅展示了自身框架能工作，不足以证明其优越性。
    - **充分性**：对于一篇提出新概念的工作，初步验证是合理的，但作为正式论文（ICML 2026被拒）可能存在实验不充分的问题，例如缺少高维真实数据集测试、缺少复杂真实场景的鲁棒性分析等。

## 6. 主要结论与发现

- AI-Kolmogorov 框架能够成功地将符号回归应用于密度估计，对于合成及物理应用中的分布，可以恢复出或发现其背后的数学表达式，从而提供有价值的洞察。
- 符号密度估计是可解释密度建模的有效途径，尤其适合需要显式公式的领域（如高能物理中的理论模型验证）。

## 7. 优点

- **新颖性**：首次明确提出符号密度估计的概念，并设计了系统性的分解-回归流水线。
- **可解释性**：输出为显式数学表达式，远优于黑箱密度估计。
- **模块化设计**：分解、非参数估计、支撑估计、符号回归各步骤可独立替换或改进，灵活性强。
- **应用导向**：选择高能物理中的真实问题，体现实际价值。

## 8. 不足与局限

- **实验不充分**：
    - 缺少与现有密度估计方法（如核密度、高斯混合、归一化流）的定量对比（如KL散度、似然度）。
    - 未进行消融实验，无法确定分解和支撑估计的必要性。
    - 未测试高维数据（维度>5），符号回归在高维下可能失效。
- **偏差风险**：合成分布可能过于理想，符号回归容易恢复；真实高能物理分布的未知ground truth，如何验证正确性？
- **算力与可扩展性**：未报告符号回归的计算成本，可能随数据量和维度急剧增长，难以实用。
- **应用限制**：符号回归只能找到有限复杂度的表达式，对于极其复杂的密度函数（如深度生成模型）可能无法符号化。
- **推理不完整**：缺少数学证明或理论保证（如一致性、收敛性）。

（完）
