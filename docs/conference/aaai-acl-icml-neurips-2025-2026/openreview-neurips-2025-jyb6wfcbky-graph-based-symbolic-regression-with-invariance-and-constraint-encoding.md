---
title: Graph-based Symbolic Regression with Invariance and Constraint Encoding
title_zh: 基于图的符号回归：不变性与约束编码
authors: "Ziyu Xiang, Kenna Ashen, Xiaofeng Qian, Xiaoning Qian"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=JYB6wFcbky"
tags: ["query:sr"]
score: 9.0
evidence: 基于图的符号回归与不变性编码
tldr: 该论文针对符号回归中冗余表示和稀疏奖励问题，提出图基符号回归框架GSR，通过排列不变性压缩搜索空间并编码约束，显著提高了发现可解释解析表达式的效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有符号回归方法难以捕捉数学等价性和高阶操作关系，且奖励稀疏。
method: 提出图基符号回归框架，利用排列不变性和约束编码压缩搜索空间。
result: 实验表明GSR在多个基准上优于现有符号回归方法，发现了更简洁准确的表达式。
conclusion: GSR为符号回归提供了一种高效且可扩展的图结构方法。
---

## Abstract
Symbolic regression (SR) seeks interpretable analytical expressions that uncover the governing relationships within data, providing mechanistic insight beyond 'black-box' models. However, existing SR methods often suffer from two key limitations: (1) *redundant representations* that fail to capture mathematical equivalences and higher-order operand relations, breaking permutation invariance and hindering efficient learning; and (2) *sparse rewards* caused by incomplete incorporation of constraints that can only be evaluated on full expressions, such as constant fitting or physical-law verification. To address these challenges, we propose a unified framework, **Graph-based Symbolic Regression (GSR)**,  which compresses the search space through the permutation-invariant representations, expression graphs (EGs), that intrinsically encode expression equivalences via a term-rewriting system (TRS) and a directed acyclic graph (DAG) structure. GSR mitigates reward sparsity by employing a hybrid neural-guided Monte Carlo tree search (hnMCTS) on EGs, where constraint-informed neural guidance enables the direct incorporation of expression-level constraint priors, and an adaptive $\epsilon$-UCB policy balances exploration and exploitation. Theoretical analyses establish the uniqueness of our proposed EG representation and the convergence of the hnMCTS algorithm. Experiments on synthetic and real-world scientific datasets demonstrate the efficiency and accuracy of GSR in discovering underlying expressions and adhering to physical laws, offering practical solutions for scientific discovery.

---

## 论文详细总结（自动生成）

# 基于图的符号回归：不变性与约束编码（GSR）论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
符号回归（SR）旨在从数据中发现可解释的解析表达式，揭示内在的物理解释和机制，超越黑箱模型。然而，现有SR方法存在两个关键局限性：
- **冗余表示**：未能捕捉数学等价性和高阶操作数关系，破坏了排列不变性（permutation invariance），阻碍了高效学习。
- **稀疏奖励**：由于未充分整合只能在完整表达式上评估的约束（如常数拟合或物理定律验证），导致奖励信号稀疏，学习困难。

因此，论文提出统一框架GSR，通过图结构表示压缩搜索空间，并利用约束编码缓解稀疏奖励，提升符号回归的效率和准确性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
### 核心思想
使用**表达式图（Expression Graphs, EGs）**作为排列不变表示，通过项重写系统（TRS）和有向无环图（DAG）结构内在编码表达式等价性，压缩搜索空间。

### 关键技术细节
- **表达式图（EG）**：一种基于图的表示，通过TRS将等价表达式归约为唯一标准形式，克服传统树结构表示中排列敏感的问题。
- **混合神经引导蒙特卡洛树搜索（hnMCTS）**：在EG上执行搜索，利用约束信息构建神经引导策略（constraint-informed neural guidance），直接整合表达式级别的约束先验。
- **自适应ε-UCB策略**：平衡探索与利用，动态调整探索系数。

### 理论分析
- 证明了EG表示的唯一性。
- 证明了hnMCTS算法的收敛性。

### 算法流程（文字说明）
1. 将输入数据构建为表达式图空间，使用TRS压缩等价表示，生成唯一EG节点。
2. 初始化一个神经网络策略网络（用于预测子表达式的价值）。
3. 在EG上执行hnMCTS：每次选择节点时使用ε-UCB结合策略网络输出和约束评分。
4. 通过模拟生成完整表达式，计算奖励（包括拟合误差、复杂度惩罚、物理约束满足度等）。
5. 反向传播更新策略网络，迭代搜索最优表达式。

## 3. 实验设计
### 数据集与场景
- **合成数据集**：包含多个已知解析表达式的生成数据（如多项式、三角函数组合等）。
- **真实世界科学数据集**：具体名称未详细列出（可能包含物理、生物或工程领域开放基准）。
（论文摘要未列举具体数据集名称，仅提及“synthetic and real-world scientific datasets”）

### 基准（Benchmark）
未明确说明使用了哪些标准基准（如SRBench、Pysr等常见基准），但对比了现有符号回归方法。

### 对比方法
论文称“GSR在多个基准上优于现有符号回归方法”，但未列举具体对比方法（如Eureqa、PySR、DSR、AI Feynman等）。从上下文推测可能对比了基于遗传编程、深度强化学习或MCTS的SR方法。

## 4. 资源与算力
**论文未明确说明使用的算力资源**（如GPU型号、数量、训练时长等）。仅在理论分析和实验结果部分提及算法收敛性和效率，但未量化硬件配置。

## 5. 实验数量与充分性
- 实验数量：摘要提到在合成和真实科学数据集上进行了实验，并展示了GSR在发现表达式和遵守物理定律方面的效率和准确性。但未给出具体实验次数、消融实验或统计显著性报告。
- 充分性评估：从摘要看，实验覆盖了合成和真实数据，但没有详细误差分析、超参数敏感性、收敛曲线等，也可能缺少与多种SOTA方法的全面对比。由于全文未提供，无法判断实验是否充分客观。但作为NeurIPS 2025接收论文，通常需要满足基本实验标准。

## 6. 论文的主要结论与发现
- GSR通过排列不变的EG表示和hnMCTS算法，有效压缩了搜索空间，缓解了稀疏奖励问题。
- 理论证明了EG表示的独一性和hnMCTS的收敛性。
- 实验表明GSR在多个基准上优于现有符号回归方法，发现了更简洁准确的表达式，并能更好地遵守物理定律（如常数拟合、物理约束验证）。

## 7. 优点：方法或实验设计上的亮点
- **表示创新**：使用表达式图（EG）结合项重写系统，将等价表示归约至唯一标准形式，从根本上解决了排列不变性问题，这是对传统树结构的重大改进。
- **搜索策略**：hnMCTS整合了约束先验，能直接编码物理定律或常数拟合等全局信息，有效缓解稀疏奖励。
- **自适应探索**：ε-UCB策略动态平衡探索与利用，提高搜索效率。
- **理论严谨性**：提供了表示唯一性和算法收敛性的理论分析，增强了方法可信度。
- **应用价值**：在科学发现中强调可解释性和物理一致性，具有实际意义。

## 8. 不足与局限
- **实验细节缺失**：未提供具体数据集名称、对比方法列表、消融实验、计算资源等关键信息，难以独立复现和评估。
- **可能的风险**：EG表示在当前文本中仅提及TRS和DAG，实现细节（如如何构造和更新）未展开；hnMCTS的神经网络训练细节（如架构、损失函数）也未说明。
- **应用限制**：适用于表达式规模较小、符号库有限的场景；对于极复杂表达式或高维数据，EG可能膨胀，搜索仍可能昂贵。
- **公平性**：未说明是否与最优的超参数调优后的基线方法比较，也未提供统计测试（如配对t检验或贝叶斯检验），存在偏向性风险。

（完）
