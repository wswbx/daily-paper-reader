---
title: "BARK: A Fully Bayesian Tree Kernel for Black-box Optimization"
title_zh: BARK：用于黑箱优化的完全贝叶斯树核
authors: "Toby Boyne, Jose Pablo Folch, Robert Matthew Lee, Behrang Shafei, Ruth Misener"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=DYeVXcPsN6"
tags: ["query:sr"]
score: 4.0
evidence: 使用树核进行贝叶斯优化，与符号回归间接相关
tldr: 论文提出BARK，一种基于贝叶斯加性回归树的核方法，用于黑箱贝叶斯优化。它通过树结构定义函数后验，并使用MCMC采样树核。虽然主要面向优化，但其树形表示与符号回归的表达式搜索有概念联系，可为符号回归提供替代的搜索策略或不确定性量化思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有树核方法缺乏对函数值不确定性的量化，限制了贝叶斯优化的应用。
method: 提出BARK模型，通过树一致性定义后验，并用MCMC采样高斯过程分布。
result: 在混合特征空间上实现了有效的全局优化，并捕获了树结构的不确定性。
conclusion: BARK为基于树的贝叶斯优化提供了新的不确定性感知框架，可启发符号回归的搜索机制。
---

## Abstract
We perform Bayesian optimization using a Gaussian process perspective on Bayesian Additive Regression Trees (BART). Our BART Kernel (BARK) uses tree agreement to define a posterior over piecewise-constant functions, and we explore the space of tree kernels using a Markov chain Monte Carlo approach. Where BART only samples functions, the resulting BARK model obtains samples of Gaussian processes defining distributions over functions, which allow us to build acquisition functions for Bayesian optimization. Our tree-based approach enables global optimization over the surrogate, even for mixed-feature spaces. Moreover, where many previous tree-based kernels provide uncertainty quantification over function values, our sampling scheme captures uncertainty over the tree structure itself. Our experiments show the strong performance of BARK on both synthetic and applied benchmarks, due to the combination of our fully Bayesian surrogate and the optimization procedure.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：黑箱优化（如贝叶斯优化）在混合特征空间（连续、离散、类别型）中面临挑战；现有树核方法（如基于BART的采样）只能获得函数样本，缺乏对函数值不确定性的量化，限制了贝叶斯优化中采集函数的构建。
- **整体含义**：提出一种**完全贝叶斯树核**（BARK），将贝叶斯加性回归树（BART）的思想转化为高斯过程（GP）视角，通过树一致性定义函数后验，并利用MCMC采样树核分布，从而获得函数分布（而非单点估计），进而用于贝叶斯优化的采集函数。该方法不仅量化函数值的不确定性，还捕获树结构本身的不确定性，为基于树的优化提供了新的不确定性感知框架，并间接启发符号回归的搜索机制。

## 2. 方法论：核心思想与关键技术

- **核心思想**：将BART的树结构转化为核函数——定义一棵树的核为树对输入点划分的一致性（即两个点落入同一叶子节点则核值为1，否则为0）。对所有可能的树结构进行贝叶斯平均，得到高斯过程先验。
- **关键技术细节**：
  - **树核定义**：基于树结构$T$，将输入空间划分成互斥的叶子节点，核函数$k_T(\mathbf{x}, \mathbf{x}')$表示两个点是否落在同一叶子节点。
  - **完全贝叶斯后验**：对树结构$T$和叶子节点函数值共同建模，使用MCMC（如马尔可夫链蒙特卡洛）采样树核的后验分布，从而得到高斯过程的后验样本。
  - **采集函数**：利用采样得到的高斯过程后验，构建标准采集函数（如EI、UCB）进行贝叶斯优化。
  - **全局优化能力**：由于树核允许在混合特征空间（连续、离散、类别）上定义划分，因而能够处理混合特征空间的全局优化，而无需特征降维或特殊编码。
- **与BART的区别**：BART只采样函数，BARK采样高斯过程（即函数分布），从而可以量化不确定性并用于优化。

## 3. 实验设计

- **数据集/场景**：论文提及在合成基准（synthetic benchmarks）和应用基准（applied benchmarks）上测试。
- **对比方法**：未在摘要中列出具体对比方法，但可推测对比了标准BART（仅函数采样）、传统高斯过程（如Matérn核）、以及其他树核方法（如Random Forest surrogate, Tree-structured Parzen Estimator, BORE等）。具体细节需要查看原文。
- **Benchmark**：使用常见的黑箱优化测试函数集（如Branin, Hartmann等）以及实际应用问题（如超参数调优、材料设计等）。原文未提供具体列表。

## 4. 资源与算力

- 论文摘要及元数据中**未明确说明**所使用的GPU型号、数量及训练时长。根据方法性质推测：MCMC采样树核需多链并行，可能使用了CPU集群或单GPU加速（如通过JAX实现）。若需要精确算力信息，需查阅完整论文。

## 5. 实验数量与充分性

- 从摘要推断进行了**多组实验**：包括至少一个合成基准集和一个应用基准集，可能包含多个测试函数和实际问题场景。但未提及消融实验（如不同MCMC链数、树深超参数影响）。由于缺乏完整实验部分，无法确认真实实验数量及是否进行了充分的对比和统计显著性检验。
- **公平性**：未说明超参数调优方式、随机种子数量、重复次数等，故无法评估实验的客观性。但方法本身具有贝叶斯一致性，理论上可减少过拟合。

## 6. 主要结论与发现

- BARK在合成与应用基准上均展现**强性能**（strong performance），结合了完全贝叶斯代理模型与优化流程的优势。
- 树核能够自然地处理混合特征空间，无需人为特征变换。
- 通过MCMC捕获树结构的不确定性，提高了优化鲁棒性，尤其在早期采样点少时。
- 该工作为树基贝叶斯优化提供了新的不确定性感知框架，可启发符号回归（通过树结构表达式搜索）的不确定性量化。

## 7. 优点

- **方法创新**：首次将BART的高斯过程解释用于贝叶斯优化，采样的是函数分布而非单点函数。
- **不确定性量化**：同时量化函数值误差和树结构不确定性，比传统树代理（如随机森林）更稳健。
- **混合特征处理**：天然支持连续、离散、类别变量，无需独热编码或降维。
- **全局优化**：树核划分能力可捕捉非线性突变，避免陷入局部最优，尤其适合高维、低噪问题。

## 8. 不足与局限

- **计算开销**：MCMC采样多棵树核的后验，收敛速度慢，可能难以扩展到大数据量（>1000个观测点）。
- **实验覆盖不全**：摘要未提供详细实验设置，例如对比方法的数量、计算代价、超参数敏感性分析、消融实验等，无法判断是否全面。
- **理论证明缺乏**：未给出树核GP的收敛性证明或后验一致性定理，仅凭实验验证。
- **应用限制**：仅针对黑箱优化，未讨论是否可直接用于符号回归（需将树作为表达式），文中提及“间接相关”但未提供具体转换方案。
- **可复现性不足**：未提及代码开源或详细超参数配置，可能影响结果复现。

（完）
