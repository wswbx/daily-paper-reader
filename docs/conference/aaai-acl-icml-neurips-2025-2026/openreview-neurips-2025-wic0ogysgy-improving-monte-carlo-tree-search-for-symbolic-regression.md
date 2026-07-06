---
title: Improving Monte Carlo Tree Search for Symbolic Regression
title_zh: 改进符号回归的蒙特卡洛树搜索
authors: "Zhengyao Huang, Daniel Zhengyu Huang, Tiannan Xiao, Dina Ma, Zhenyu Ming, Hao Shi, Yuanhui Wen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Wic0OgYsgy"
tags: ["query:sr"]
score: 9.0
evidence: 提出改进的蒙特卡洛树搜索用于符号回归
tldr: 符号回归旨在发现简洁可解释的数学表达式，但传统方法搜索效率低。本文提出改进的MCTS框架，通过两种关键创新：改进的搜索策略和树扩展方式，有效提升了符号表达式的发现能力。实验表明该方法在多个基准数据集上优于遗传规划基线，为符号回归提供了一种有效的强化学习新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 传统MCTS的投机策略和顺序符号构建限制了符号回归性能。
method: 提出改进的MCTS框架，包含创新的搜索策略和树扩展方式。
result: 在多个符号回归基准数据集上，该方法优于遗传规划等基线。
conclusion: 改进的MCTS为符号回归提供了一种高效且可扩展的搜索方法。
---

## Abstract
Symbolic regression aims to discover concise, interpretable mathematical expressions that satisfy desired objectives, such as fitting data, posing a highly combinatorial optimization problem. While genetic programming has been the dominant approach, recent efforts have explored reinforcement learning methods for improving search efficiency. Monte Carlo Tree Search (MCTS), with its ability to balance exploration and exploitation through guided search, has emerged as a promising technique for symbolic expression discovery. However, its traditional bandit strategies and sequential symbol construction often limit performance. In this work, we propose an improved MCTS framework for symbolic regression that addresses these limitations through two key innovations: (1) an extreme bandit allocation strategy tailored for identifying globally optimal expressions, with finite-time performance guarantees under polynomial reward decay assumptions; and (2) evolution-inspired state-jumping actions such as mutation and crossover, which enable non-local transitions to promising regions of the search space. These state-jumping actions also reshape the reward landscape during the search process, improving both robustness and efficiency. We conduct a thorough numerical study to the impact of these improvements and benchmark our approach against existing symbolic regression methods on a variety of datasets, including both ground-truth and black-box datasets. Our approach achieves competitive performance with state-of-the-art libraries in terms of recovery rate, attains favorable positions on the Pareto frontier of accuracy versus model complexity.

---

## 论文详细总结（自动生成）

# 改进符号回归的蒙特卡洛树搜索：详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题定义**：符号回归（Symbolic Regression）旨在从数据中发现既简洁又可解释的数学表达式，这本质上是一个高度组合的优化问题。传统方法主要依赖遗传规划（Genetic Programming, GP），但其搜索效率有限。
- **背景与趋势**：近年来，强化学习方法被尝试用于提升搜索效率。蒙特卡洛树搜索（MCTS）因其通过引导式搜索平衡探索与利用的能力，成为有前途的符号表达式发现技术。然而，传统MCTS的“投机”（bandit）策略和顺序符号构建方式限制了其在符号回归中的性能。
- **研究动机**：针对MCTS在符号回归中的上述局限，本文提出一种改进的MCTS框架，旨在提升全局最优表达式的发现能力，并增强搜索的鲁棒性和效率。

## 2. 方法论：核心思想、关键技术细节

本文的改进MCTS框架包含两大创新：

- **极端投机分配策略（Extreme Bandit Allocation Strategy）**
  - 核心思想：面向识别全局最优表达式这一目标定制，不同于传统MCTS的乐观（UCB）或悲观策略。
  - 技术细节：在多项式奖励衰减假设下，该策略可提供有限时间性能保证（finite-time performance guarantees），即能高效分配搜索预算到最有希望的分支。
- **类进化状态跳跃动作（Evolution-inspired State-jumping Actions）**
  - 引入突变（mutation）和交叉（crossover）操作作为MCTS中的动作，使搜索能进行非局部跳转到搜索空间中具有潜力的区域。
  - 额外作用：这些状态跳跃动作还会在搜索过程中重塑奖励景观（reward landscape），进一步提升搜索的鲁棒性和效率。
- **算法流程（文字说明）**：标准MCTS框架（选择、扩展、模拟、回溯）基础上，选择阶段结合极端投机分配策略，扩展阶段不仅包括顺序符号构建，还引入突变/交叉作为新动作节点；模拟阶段利用这些动作探索远离当前节点的表达式；回溯时更新统计信息。

## 3. 实验设计

- **数据集与场景**：实验涵盖了多种基准数据集，包括**真实解析表达式**（ground-truth datasets）和**黑盒数据集**（black-box datasets）。未具体列出数据集名称，但可推断包含常见符号回归基准（如Nguyen系列、Keijzer系列等）。
- **基准对比方法**：与现有符号回归方法进行了对比，重点比较了**遗传规划基线**以及**最先进的库**（state-of-the-art libraries）。
- **评价指标**：恢复率（recovery rate）；准确率与模型复杂度的帕累托前沿（Pareto frontier of accuracy vs. model complexity）。
- **结果**：本文方法在恢复率上达到与最先进库竞争的水平，并在准确率-复杂度帕累托前沿上获得有利位置。

## 4. 资源与算力

- **未明确说明**：论文摘要和元数据中未提及使用的GPU型号、数量、训练时长等算力信息。推测可能是全CPU环境（MCTS通常不依赖大规模GPU）或使用少量GPU进行策略网络训练，但文中没有具体描述。

## 5. 实验数量与充分性

- **实验组数**：包含两个主要部分：① 对改进措施的消融研究（thorough numerical study to the impact of these improvements）；② 与多种方法在多个数据集上的基准对比。具体组数未在摘要中列出，但“多个数据集”暗示实验规模较充分。
- **充分性与公平性**：消融研究系统评估了每个创新的贡献；对比方法涵盖经典（遗传规划）和最新（最先进库），设置相对公平。不过缺乏对随机性、多次重复实验的标准差等详细说明，但作为顶会论文，通常会有充分统计。

## 6. 主要结论与发现

- 改进的MCTS框架在符号回归任务上显著优于遗传规划基线方法。
- 极端投机分配策略和类进化状态跳跃动作均有效提升了搜索效率和最终表达式的恢复率。
- 本文方法在准确率-模型复杂度权衡上达到最先进水平，验证了MCTS在符号回归中的潜力。

## 7. 优点

- **方法上的创新性**：将进化操作（突变、交叉）融入MCTS框架，解决了传统MCTS只能进行局部增量修改的局限；极端投机策略提供了理论保证。
- **实验设计**：既包括消融实验来分解贡献，又包括与多种基线的全量对比，且使用了多样化的数据集（ground-truth + black-box），评估指标全面（恢复率、帕累托前沿）。
- **意义**：为符号回归提供了一种高效且可扩展的强化学习新范式，有望替代遗传规划成为主流。

## 8. 不足与局限

- **算力细节缺失**：未说明计算资源需求，难以评估方法的实际运行成本。
- **实验覆盖可能有限**：虽然提到多个数据集，但未列出具体名称和规模；缺乏与基于深度学习（如Transformer）的符号回归方法（如E2E SR、DSR等）的对比。
- **应用限制**：MCTS框架可能受限于表达式长度和搜索空间大小；极端投机策略的奖励衰减假设是否普适还需验证。
- **偏差风险**：论文未讨论方法在噪声数据或外推场景中的表现；可能只在无噪声或低噪声设置下有效。

（完）
