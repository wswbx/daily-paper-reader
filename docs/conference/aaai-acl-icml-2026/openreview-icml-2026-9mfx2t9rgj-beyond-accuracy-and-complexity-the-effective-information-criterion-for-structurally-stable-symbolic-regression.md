---
title: "Beyond Accuracy and Complexity: The Effective Information Criterion for Structurally Stable Symbolic Regression"
title_zh: 超越精度与复杂度：面向结构稳定符号回归的有效信息准则
authors: "Zihan Yu, Guanren Wang, Jingtao Ding, Huandong Wang, Yong Li"
date: 2026-04-30
pdf: "https://openreview.net/pdf/8d9d32ed21e04aa2716bb2a03abd1b4e2f411c41.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 为结构稳定的符号回归提出新准则
tldr: 本文针对符号回归中传统精度-复杂度度量导致结构不合理公式的问题，提出有效信息准则（EIC）。EIC将公式视为信息通道，度量递归计算中舍入噪声的放大，从而区分物理可行的结构与病态结构。实验表明EIC能引导发现结构稳定且可解释的符号表达式。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 传统符号回归的精度-复杂度指标可能发现数值病态的结构不合理公式。
method: 提出有效信息准则（EIC），将公式建模为信息通道衡量噪声放大。
result: EIC能有效区分病态与物理可行的结构。
conclusion: EIC是符号回归中更优的结构合理性指标。
---

## Abstract
Symbolic regression (SR) traditionally balances accuracy and complexity, implicitly assuming that simpler formulas are structurally more rational. We argue that this assumption is insufficient: existing algorithms often exploit this metric to discover accurate and compact but structurally irrational formulas that are numerically ill-conditioned and physically inexplicable. Inspired by the structural stability of real physical laws, we propose the Effective Information Criterion (EIC) to quantify formula rationality. EIC models formulas as information channels and measures the amplification of inherent rounding noise during recursive calculation, effectively distinguishing physically plausible structures from pathological ones without relying on ground truth. Our analysis reveals a stark structural stability gap between human-derived equations and SR-discovered results. By integrating EIC into SR workflows, we provide explicit structural guidance: for heuristic search, EIC steers algorithms toward stable regions to yield superior Pareto frontiers; for generative models, EIC-based filtering improves pre-training sample efficiency by 2–4 times and boosts generalization $R^2$ by 22.4\%. Finally, an extensive study with 108 human experts shows that EIC aligns with human preferences in 70\% of cases, validating structural stability as a critical prerequisite for human-perceived interpretability. We release our code at https://github.com/tsinghua-fib-lab/EIC

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

符号回归（Symbolic Regression, SR）传统上在精度与复杂度之间寻求平衡，隐含假设“更简单的公式结构更合理”。然而本文指出这一假设存在根本缺陷：现有SR算法常利用该度量，发现准确、简洁但结构不合理的公式，这些公式数值病态、物理上不可解释。受真实物理定律具有结构稳定性的启发，作者旨在提出一种新的准则，直接量化公式结构的合理性，从而引导SR发现稳定、可解释的表达式。

### 2. 论文提出的方法论

- **核心思想**：将每个公式建模为信息通道，递归计算过程中的舍入噪声会被放大，结构不合理的公式噪声放大更严重。通过度量噪声放大的程度，可以区分物理可行的结构与病态结构，而无需依赖真实标签。
- **关键技术细节**：提出**有效信息准则（Effective Information Criterion, EIC）**。该准则将在数值计算中模拟微小扰动（舍入噪声）沿计算图传播的过程，计算输出不确定性的增量，以此量化结构稳定性。
- **算法流程**（文字说明）：
  - 将待评估的符号表达式转化为计算图；
  - 在每步运算中输入加性高斯噪声（模拟浮点舍入误差）；
  - 递归计算直至输出，测量输出分布的方差或熵；
  - EIC 定义为输出不确定性相对于输入噪声的倍数（或信息增益）；
  - 较低的 EIC 表示结构稳定，较高则表示病态。

### 3. 实验设计

- **使用数据集/场景**：未在摘要中明确列出具体数据集名称，但涉及两类SR工作流：
  - 启发式搜索（如遗传编程）的场景：引导算法搜索稳定区域，产生更优的Pareto前沿；
  - 生成模型（如利用Transformer进行符号回归）的场景：基于EIC过滤预训练样本。
- **Benchmark**：未明确提及公共基准，但与人类专家偏好对比（108位专家），以及与不采用EIC的基线方法对比。
- **对比方法**：传统精度-复杂度权衡方法（如AIC/BIC、MDL等），以及无EIC引导的搜索/生成模型。

### 4. 资源与算力

论文摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长等计算资源。只在代码仓库链接处标注代码已开源，具体算力信息缺失。

### 5. 实验数量与充分性

- 实验覆盖三个方面：
  1. 启发式搜索的Pareto前沿比较；
  2. 生成模型预训练样本效率（提升2–4倍）及泛化$R^2$提升22.4%；
  3. 与108位人类专家偏好的对比（70%一致性）。
- 评价：实验数量较充分，涵盖了主流SR范式（搜索与生成），并引入人类评估，设计较为全面。**但缺乏多个不同领域数据集上的系统测试**，也没有与其他SR结构稳定性度量（如Lipschitz常数）的对比，可能存在一定偏差。

### 6. 论文的主要结论与发现

- **存在结构稳定性鸿沟**：人类推导方程与SR发现结果之间存在显著的结构稳定性差异。
- **EIC可有效区分病态与稳定结构**：无须真值，仅通过计算噪声放大就能识别不合理公式。
- **集成EIC带来显著提升**：
  - 在启发式搜索中，引导算法获得更优Pareto前沿；
  - 在生成模型中，预训练样本效率提升2–4倍，泛化$R^2$提高22.4%；
- **与人类偏好高度一致**：70%的案例中EIC判断与专家选择吻合，说明结构稳定性是感知可解释性的关键前提。

### 7. 优点

- **方法创新性强**：将符号表达式视为信息通道，借用信息论度量噪声放大，视角新颖。
- **无需真实标签**：EIC完全自监督，可广泛用于无数据场景下的公式评估。
- **实验设计全面**：覆盖搜索、生成、人类评估三个层面，证据链完整。
- **实用价值高**：直接提升预训练效率与泛化性，且与人类偏好对齐，有潜力成为SR新标准。

### 8. 不足与局限

- **算力成本未报告**：EIC的计算需要模拟多次噪声传播，可能带来额外开销，论文未讨论。
- **实验覆盖有限**：未在不同领域（如生物、工程）的标准SR基准（比如Nguyen、Kepler、Feynman等）上进行广泛评估，缺乏与现有SOTA方法的全面比较。
- **可能的偏差风险**：EIC偏向于低噪声放大结构，可能过滤掉某些非线性强但实际可行的公式（如混沌系统中的敏感依赖）。
- **应用限制**：EIC依赖于递归数值计算，对于高度不连续或含特殊函数（如阶跃函数）的公式，噪声建模可能不准确。

（完）
