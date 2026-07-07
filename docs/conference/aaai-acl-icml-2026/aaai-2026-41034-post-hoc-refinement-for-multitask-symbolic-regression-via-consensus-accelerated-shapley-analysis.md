---
title: Post-Hoc Refinement for Multitask Symbolic Regression via Consensus-Accelerated Shapley Analysis
title_zh: 基于共识加速Shapley分析的多任务符号回归后验优化
authors: "Xinyue Li, Wang Hu, Yu Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/41034/44995"
tags: ["query:sr"]
score: 9.0
evidence: 多任务符号回归的后验优化
tldr: 针对多任务遗传规划中丢弃种群知识的局限，MTGP-BS提出后验优化框架：通过共识加速的Shapley分析从种群中合成重要子表达式，而非简单的优胜者选择。实验表明该方法在多个多任务符号回归基准上显著提升了表达式质量和泛化能力，为多任务表达发现提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 传统多任务遗传规划采用胜者全取选择，丢弃了种群中的大量有效知识。
method: 提出MTGP-BS方法，通过共识加速Shapley分析从种群中识别重要子表达式并合成新表达式。
result: 在多个多任务回归基准上，MTGP-BS相比传统方法显著提升了表达式质量和泛化性能。
conclusion: 从选择转向合成的后验优化范式为多任务符号回归提供了有效途径。
---

## Abstract
Multitask genetic programming (MTGP) is one of the primary methods for solving multitask symbolic regression (MTSR), the problem of discovering mathematical expressions for multiple interconnected tasks simultaneously. However, conventional MTGP approaches discard a wealth of valuable knowledge from the population of expressions due to their inherent “winner-take-all” selection criteria. To address this, we introduce MTGP with bidirectional cooperation and consensus-accelerated Shapley analysis (MTGP-BS), a method whose core is a novel post-hoc refinement framework that shifts from selection to synthesis. Our method first employs a consensus-accelerated Shapley analysis to reliably identify important subexpressions by multi-model attribution. Second, to supply this analysis with high-quality candidates, we design a bidirectional subexpression cooperative extraction method to create a refined archive of effective components by improving knowledge transfer and filtering out redundancies. These allow MTGP-BS to synthesize superior expressions by integrating knowledge dispersed throughout the entire population. On diverse MTSR problems, our algorithm statistically outperformed state-of-the-art approaches in 140 out of 160 direct comparisons, with its effectiveness and practical utility further verified by real-world case studies and in-depth ablation analyses.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

多任务符号回归（MTSR）旨在同时发现多个相互关联任务的数学表达式。主流方法多任务遗传规划（MTGP）采用“胜者全取”选择策略，仅保留每个任务的最优表达式，丢弃了种群中大量有价值的子表达式（subexpressions），这些子表达式可能包含有意义的结构片段。这种知识丢弃限制了最终表达式的精度和泛化能力。作者提出一种后验优化框架，将思路从“选择”转向“合成”，通过分析整个演化种群中的子表达式，重新合成更优的表达式。

## 2. 论文提出的方法论

- **核心思想**：利用后验优化框架，在标准MTGP演化结束后，对种群中所有子表达式进行提取、评估和组合，从而为每个任务合成一个新表达式。
- **关键技术细节**：
  - **双向子表达式协同提取方法**（Bidirectional Subexpression Cooperative Extraction）：
    - 第一步：**任务内频率引导归档**。对当前任务的子表达式进行k-means聚类，提取高频子表达式形成初始档案。
    - 第二步：**条件性任务间补充**。若当前任务档案多样性不足，或相关任务的最优表达式正确，则从相关任务的最优表达式中提取子表达式加入档案。
    - 第三步：**任务内最优驱动注入**。将当前任务的最优表达式中的子表达式强制加入档案。
    - 最终得到每个任务的紧凑高质量子表达式档案 \( \mathbf{A}_t \)。
  - **共识加速的Shapley分析**（Consensus-Accelerated Shapley Analysis）：
    - **自举数据准备**：对原始数据集进行K次自举抽样，生成K个训练集和对应的袋外样本。
    - **基于SHAP的多模型归因**：对每个数据集训练一个模型，计算每个子表达式的SHAP值，得到重要性矩阵 \( \Phi_t \) 和秩矩阵 \( \Gamma_t \)。
    - **基于共识的子表达式选择**：两步选择：第一步，投票选择：若某个子表达式在多数模型中排名位于前一半中的某个具体排名，则直接选中。第二步，增强的轮盘赌选择：将未选中的子表达式进行K次轮盘赌选择，若某个子表达式被多数轮次选中，则加入最终集合。
  - **最终表达式生成**：使用迭代最小二乘法从选中的子表达式中构造最终表达式。
- **算法流程**（文字说明）：
  1. 初始化多任务种群。
  2. 执行标准MTGP演化。
  3. 提取原始子表达式。
  4. 通过双向协同提取方法构建紧凑档案。
  5. 对每个任务，通过共识加速Shapley分析选择重要子表达式。
  6. 使用最小二乘法合成最终表达式。
- **关键命题**：提出命题1，证明在随机排名假设下，投票选择选中某子表达式的概率极低，确保选择结果的统计显著性。

## 3. 实验设计

- **数据集/场景**：使用16个多任务符号回归问题，每个问题由两个任务组成，涵盖不同复杂度、运算符和变量数量。此外，还从单任务符号回归基准构建了6个新的MTSR问题，以及一个真实世界案例（人口与碳排放预测，变量为GDP和能源消耗）。
- **基准方法**：对比5种多任务算法：MO-MFEA、MFEA-DGD、BLKT-DE、MTDE-MKTA、MTES-KG。同时，将后验优化框架作为插件应用到这些基线算法上。
- **评价指标**：均方误差（mse），Wilcoxon符号秩检验判断统计显著性。
- **参数设置**：种群大小50，最大评估次数100,000，GEP头部长度10，每个实验重复30次。

## 4. 资源与算力

论文中未明确提及使用的GPU型号、数量或训练时长。文中仅分析了运行时间，指出初始演化占主导，后验优化开销仅为总时间的很小一部分。因此，无法获取具体的算力信息，需指出未说明。

## 5. 实验数量与充分性

- **实验数量**：
  - 16个MTSR问题 × 2任务 × 30次独立运行 = 960次运行（对比方法共160次直接比较）。
  - 额外6个新建MTSR问题 × 2任务 × 30次运行。
  - 消融实验：对比MTGP-BS与缺失双向提取的变体MTGP-S；对比三种共识分析变体（单模型、简单平均SHAP、仅投票共识）。
  - 敏感性分析：模型数量K从3到11。
  - 泛化性实验：将后验优化框架应用于6种基线算法。
- **充分性与公平性**：
  - 实验覆盖了多种复杂度的基准，包括真实世界案例。
  - 使用Wilcoxon符号秩检验统计显著性，多次重复（30次）减少随机性。
  - 对比方法为当前先进的多任务算法，确保了比较的公平性。
  - 消融实验验证了各个组件的必要性。
  - 实验设计较为全面、客观。

## 6. 主要结论与发现

- MTGP-BS在140/160次直接比较中统计显著优于所有对比算法，在多数任务上取得最低mse。
- 定性分析显示，MTGP-BS能发现结构与真实表达式高度吻合、且数值精度极高的表达式。
- 消融实验证实双向提取和共识加速Shapley分析均对性能有显著贡献。
- 后验优化框架作为通用插件，可有效提升所有基线算法的性能，且计算开销低。
- 在真实世界案例（人口与碳排放预测）中，MTGP-BS获得最低预测误差和更可解释的表达式。
- 敏感性分析确定K=5为最佳平衡点。

## 7. 优点

- **方法创新**：首次系统性地解决MTGP中知识丢弃问题，提出从选择到合成的范式转变，结合子表达式提取与基于SHAP的共识分析。
- **设计精巧**：双向提取机制通过频率、多样性、正确性等条件自适应补充子表达式，避免冗余；共识分析通过多模型和两次选择机制提升重要性评估的可靠性。
- **实验充分**：大量标准化基准、新建基准、真实案例、多角度的消融和敏感性分析，统计验证严谨。
- **实用性强**：框架可作为黑盒插件增强现有MTGP方法，代码已开源，便于复现和进一步研究。

## 8. 不足与局限

- **缺乏算力报告**：未明确说明实验所用的GPU/CPU型号、训练时长等资源信息，不利于可重复性。
- **超参数选择**：对K（模型数量）的选择仅通过一个问题的敏感性分析确定，未在多个问题上验证其鲁棒性。
- **通用性边界**：虽在多个基准上有效，但未探讨在极高维或极大噪声任务下的表现，可能对特定类型的数据分布存在偏差风险。
- **理论深度有限**：共识机制的随机性分析仅给出一个命题，缺乏更深入的收敛性或最优性保证。
- **实际部署**：真实世界案例仅为一个（人口与碳排放），需要更多工业场景验证。

（完）
