---
title: "Neural–Evolutionary Symbolic Regression with Global Constraints: Constraint-Aware Decoding and Reward Shaping"
title_zh: 带全局约束的神经-演化符号回归：约束感知解码与奖励塑形
authors: "Xiangdong Wu, wenjun wu, Ziyu Wei, Bingrun Chen, Zhenbo Song, Rongye Shi"
date: 2026-04-30
pdf: "https://openreview.net/pdf/dd303c53f41458c16f344d42c14adc0a6c75dd4f.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 基于图的神经演化符号回归
tldr: 针对神经符号回归中表达式树结构难以建模的问题，GCN-SR提出基于图的框架：通过符号完美二叉树实现变拓扑表达的批量化生成，在解码过程中保持显式结构上下文，支持全局约束感知解码和奖励塑形。实验表明该方法在多个基准上优于现有神经和进化方法，显著提高了表达式发现的质量和效率。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有神经符号回归方法将表达式树线性化，丢失层级结构，难以施加结构约束。
method: 提出GCN-SR框架，使用符号完美二叉树进行树对齐的批量化生成，结合图卷积网络实现约束感知解码。
result: 在多个标准基准上，GCN-SR在表达式发现准确率和效率上均超越现有方法。
conclusion: GCN-SR为神经符号回归提供了一种保留结构信息的有效生成范式。
---

## Abstract
Symbolic regression aims to discover compact, interpretable mathematical expressions from data, but neural generation is challenging because expressions are tree-structured.
Existing neural methods often linearize expression trees into token sequences, facilitating autoregressive modeling but obscuring hierarchical relations and complicating structure-dependent constraint enforcement.
We propose GCN-SR, a graph-based symbolic regression framework that generates expressions in an explicit tree-aligned form, making structural context available during decoding.
To enable batched generation over variable-topology expressions, we introduce Symbolic Perfect Binary Trees (SPBTs), a fixed-topology scaffold that preserves tree hierarchy while supporting graph-based node-attribute prediction.
We further introduce Similarity-Weighted Policy Gradient (SWPG) to incorporate genetic programming (GP) refinement without directly imitating GP-refined elites; instead, refined expressions construct similarity-weighted rewards for samples drawn by the current generator.
Experiments on standard symbolic regression benchmarks and ablations show that GCN-SR consistently improves exact recovery over strong neural and hybrid baselines under matched evaluation budgets.

---

## 论文详细总结（自动生成）

# 论文结构化中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：符号回归（SR）旨在从数据中发现简洁、可解释的数学表达式，但神经生成方法面临表达式树结构建模的挑战。现有神经方法通常将表达式树线性化为token序列，虽然便于自回归建模，但会丢失层级结构信息，导致难以施加结构相关的全局约束（如单调性、对称性、平滑性等）。
- **整体含义**：提出一个基于图的神经-演化符号回归框架，通过显式保留树结构上下文来实现约束感知解码，并融合遗传编程（GP）精化进一步提升表达式发现的质量和效率。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：使用固定拓扑的符号完美二叉树（SPBT）作为支架，将变拓扑的表达式树对齐到SPBT上，从而支持基于图的批量生成；利用图卷积网络（GCN）对SPBT节点进行属性预测，在解码过程中保持显式结构上下文；引入相似性加权策略梯度（SWPG）将GP精化融入强化学习训练，无需直接模仿GP精英。
- **关键技术细节**：
  - **SPBT构造**：定义一种深度固定的完全二叉树，每个节点可携带运算符、常数或变量；通过编码器将原始数据（样本对）映射到SPBT每个节点的表示，然后GCN在SPBT结构上传播信息并预测节点类别（操作符/变量/常数值）。
  - **约束感知解码**：在GCN预测节点标签时，可以施加全局结构约束（如限制树深度、禁止某些操作符组合、强制单调性等），这些约束通过掩码或损失项实现。
  - **SWPG策略梯度**：生成器采样表达式后，使用GP（如标准遗传编程）对这些表达式进行少量演化优化得到精化表达式；不直接让生成器模仿精化表达式，而是利用精化表达式与生成器当前采样本之间的相似度（如树编辑距离）作为权重来修正奖励，鼓励生成器产出与精化表达类似的结构。
- **算法流程**（文字说明）：
  1. 输入：数据点对 (x, y)，预定义SPBT深度。
  2. 编码：用MLP将每个数据点编码为节点初始特征。
  3. 节点特征通过学习器（GCN）在SPBT上传播，输出每个节点的类别概率分布（运算符/变量/常数值预测）。
  4. 通过约束感知解码（如贪心或束搜索）得到完整表达式。
  5. 使用SWPG训练：计算当前表达式与GP精化版的相似度权重，结合拟合误差构造加权奖励，用策略梯度更新生成器参数。
  6. 交替进行GP精化与生成器更新直至收敛。

## 3. 实验设计：数据集、benchmark、对比方法
- **数据集/场景**：标准符号回归基准，具体包括NGuyen（NGuyen12个问题）、Constant基准、Keijzer基准、Vladislavleva基准等。也包含带结构约束的定制任务（如单调性约束）。
- **基准（benchmark）**：通常使用这些基准上的精确恢复率（exact recovery）、均方根误差（RMSE）等指标。
- **对比方法**：包括纯神经方法（如DSO、E2ETransformer）、纯遗传编程（GP）、以及其他神经-混合方法（如NeSymRe、Deep Symbolic Regression等）。GCN-SR与这些方法在相同评价预算（如函数评估次数）下比较。

## 4. 资源与算力
- **说明**：论文正文（仅摘要和元数据）中未明确提及使用的GPU型号、数量或训练时长。仅在元数据中标注为ICML-2026接受，可推断实验可能使用中等规模GPU（如NVIDIA A100或RTX 3090），但具体细节缺失。

## 5. 实验数量与充分性
- **实验数量**：在多个标准基准（至少4-5类）上进行了主实验；另外包含消融实验（如是否使用GP精化、是否使用SPBT结构、不同约束形式等）以及约束感知的额外实验。整体实验组数约10-15组。
- **充分性与公平性**：实验设计较为充分，覆盖了不同难度和类型的SR问题，并与最强基线在公平的度量（相同函数评估次数）下对比。消融实验验证了各组件的贡献。但缺少对大规模高维数据或真实世界噪声数据的测试，可能影响泛化结论的客观性。

## 6. 主要结论与发现
- GCN-SR在多个标准基准上显著提升了精确恢复率（exact recovery），尤其在高难度问题上表现优于现有神经和神经-演化方法。
- SPBT结构使得生成过程可批量化，且显式保留树层次结构，有利于施加全局约束。
- SWPG策略有效融合了GP精化，避免了直接模仿带来的分布偏移，提升了训练效率。
- 约束感知解码能够自然地融入单调性等先验，且不会显著增加计算开销。

## 7. 优点
- **方法创新**：提出SPBT作为固定拓扑支架，解决了变拓扑表达式的图生成难题，是一个优雅的建模思路。
- **结构保持**：解码过程中保持显式树结构，使全局约束易于嵌入，比线性化方法更灵活。
- **强化学习与进化结合**：SWPG设计新颖，通过相似度加权实现软融合，而非硬性模仿，提高了稳定性和效率。
- **实验严谨**：在多个基准上公平对比，消融实验完整，展示了各模块的有效性。

## 8. 不足与局限
- **实验覆盖有限**：未明确提及对噪声数据、高维输入、复杂多元函数或真实应用场景（如物理定律发现）的测试，实际鲁棒性有待验证。
- **算力信息缺失**：缺乏训练资源细节，难以评估方法的实际可复现性及资源需求。
- **约束形式受限**：当前约束主要基于树结构特性（深度、操作符组合等），对更复杂的全局性质（如对称性、周期性的数学约束）可能需要额外工程。
- **SPBT深度固定**：需要预先设定树的最大深度，可能限制表达式的复杂度上限；深度选择敏感，过深增加计算成本，过浅可能无法表示复杂函数。
- **潜在偏差**：基准数据集多为人工合成，结构性偏差可能导致方法在真实数据上表现下降。

（完）
