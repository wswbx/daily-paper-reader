---
title: Post-Hoc Refinement for Multitask Symbolic Regression via Consensus-Accelerated Shapley Analysis
title_zh: 通过共识加速的Shapley分析实现多任务符号回归的后处理优化
authors: "Xinyue Li, Wang Hu, Yu Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/41034/44995"
tags: ["query:sr"]
score: 10.0
evidence: 直接处理多任务符号回归，提出后处理优化方法
tldr: 论文针对多任务符号回归中传统遗传编程丢弃大量有用表达式的问题，提出MTGP-BS方法。该方法通过共识加速的Shapley分析识别重要子表达式，并从“赢家通吃”转向合成策略，显著提升了表达式发现的质量。实验表明，该方法在多个多任务符号回归基准上优于现有技术。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 多任务遗传编程丢弃了大量有价值表达式，限制了符号回归性能。
method: 提出双向合作与共识加速Shapley分析的后处理框架，从群体中合成子表达式。
result: 在多个多任务符号回归任务上取得更优的表达式精度和简洁性。
conclusion: MTGP-BS为多任务符号回归提供了一种有效的后处理合成范式。
---

## Abstract
Multitask genetic programming (MTGP) is one of the primary methods for solving multitask symbolic regression (MTSR), the problem of discovering mathematical expressions for multiple interconnected tasks simultaneously. However, conventional MTGP approaches discard a wealth of valuable knowledge from the population of expressions due to their inherent “winner-take-all” selection criteria. To address this, we introduce MTGP with bidirectional cooperation and consensus-accelerated Shapley analysis (MTGP-BS), a method whose core is a novel post-hoc refinement framework that shifts from selection to synthesis. Our method first employs a consensus-accelerated Shapley analysis to reliably identify important subexpressions by multi-model attribution. Second, to supply this analysis with high-quality candidates, we design a bidirectional subexpression cooperative extraction method to create a refined archive of effective components by improving knowledge transfer and filtering out redundancies. These allow MTGP-BS to synthesize superior expressions by integrating knowledge dispersed throughout the entire population. On diverse MTSR problems, our algorithm statistically outperformed state-of-the-art approaches in 140 out of 160 direct comparisons, with its effectiveness and practical utility further verified by real-world case studies and in-depth ablation analyses.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：多任务符号回归（MTSR）旨在同时为多个互相关联的任务发现数学表达式。传统多任务遗传编程（MTGP）采用“赢家通吃”策略，仅从演化种群中选取单个最优表达式作为最终模型，丢弃了大量子最优表达式中的有价值子表达式（如通过“+”和“-”拆分得到的子结构），导致模型准确性和泛化能力受限。
- **动机**：若能利用整个种群中分散的知识，通过分析、评估和组合最有影响力的子表达式来合成新表达式，有望突破“赢家通吃”的局限。但这面临两大挑战：① 原始子表达式数量庞大且冗余，直接分析计算昂贵且易遗漏关键子表达式；② 子表达式重要性的可靠评估困难，如简单的Shapley值分析（SHAP）因随机误差可能产生不可靠结果。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出MTGP-BS框架，将后处理优化从“选择”转向“合成”。首先通过**双向子表达式合作提取方法**构建紧凑、高质量的候选子表达式档案；再通过**共识加速的Shapley分析**（Bootstrap多模型归因 + 共识机制）可靠地识别最关键的子表达式；最后用迭代最小二乘法将选出的子表达式组合成最终表达式。
- **关键技术细节**：
  - **双向子表达式合作提取**（分为三步骤）：
    1. **任务内频率引导归档**：对当前任务的原始子表达式进行频率分布k-means聚类，只保留高频簇中的子表达式到初始档案 \(A_t^{(1)}\)。
    2. **条件性任务间补充**：若初始档案多样性足够（唯一子表达式数 > \(\theta_{div})\) 且相关任务的最优表达式正确（性能 > \(\theta_{perf})\)，则将其子表达式补充进档案；若多样性不足，则无条件补充。
    3. **任务内最优驱动注入**：将当前任务最优表达式的子表达式强制加入档案，得最终档案 \(A_t\)。
  - **共识加速Shapley分析**（分为三步骤）：
    1. **Bootstrap数据准备**：从原始数据集D抽取K个Bootstrap样本，保留对应的Out-of-Bag样本用于无偏评估。
    2. **基于SHAP的多模型归因**：对每个任务，训练K个模型（如线性回归），将档案中的子表达式视为特征。对每个模型，计算所有子表达式在OOB样本上的平均绝对SHAP值 \(\phi_{k,m}\)，得到重要性矩阵 \(\Phi_t \in \mathbb{R}^{K \times M}\) 和排序矩阵 \(\Gamma_t \in \mathbb{Z}^{K \times M}\)。
    3. **基于共识的子表达式选择**：
       - **投票选择**：若某个子表达式在至少一半模型中具有相同的高位排序（前一半中的具体排名），则直接入选。
       - **增强轮盘选择**：对剩余子表达式，进行K次轮盘赌（概率正比于该模型的绝对SHAP值），若某子表达式被超过一半的模型选中，则入选。  
       该机制有理论保证（命题1：在随机排序零假设下，投票选择被选中的概率极低）。
  - **表达式生成**：从选出的子表达式集合 \(\tilde{A}_t\) 出发，利用迭代最小二乘法拟合系数，合成最终表达式 \(e_t\)。

### 3. 实验设计：数据集/场景、基准、对比方法

- **基准问题**：使用16个MTSR问题（每个含两个相关任务），覆盖不同复杂度、运算符种类和变量个数（表1中列出了Set1~16，具体表达式在附录或表2中给出部分示例）。
- **对比方法**：5个多任务优化算法——MO-MFEA、MFEA-DGD、BLKT-DE、MTDE-MKTA、MTES-KG。此外，将后处理模块应用到这些基线测试通用性。
- **额外验证**：
  - 从单任务SR基准（如Jin et al., Uy et al.）构建6个新的MTSR问题。
  - 真实案例：人类人口（H）与碳排放（Q）作为GDP（D）和能源消耗（ε）的表达式。
- **评价指标**：均方误差（MSE），统计显著性采用Wilcoxon符号秩检验（α=0.05）。

### 4. 资源与算力

文中未明确说明使用的GPU型号、数量或训练时长。实验参数：种群规模50（每个任务），最大评估次数100,000，每个实验独立重复30次。运行时间分析（图7）表明，后处理优化开销仅占总运行时间的一小部分（多数时间为MTGP演化消耗），但未给出具体硬件配置或墙钟时间。因此，算力资源信息缺失。

### 5. 实验数量与充分性

- **实验数量**：共进行160次直接对比（16个问题 × 2个任务 × 5个基线），加上消融实验（MTGP-BS vs MTGP-S，以及三种共识消融变体），后处理增强对比（6个算法 × 每个算法增强前后对比），6个构造MTSR问题对比，以及真实案例。还有参数敏感性分析（模型数K从3到11）。
- **充分性与公平性**：
  - 重复30次，使用非参数统计检验，确保可靠性。
  - 消融实验验证了双向提取和共识加速两个核心模块的必要性。
  - 通用性测试说明后处理可作为即插即用模块提升多个基线。
  - 未测试所有可能的基线和超参数设置，但覆盖了主要竞争方法和合理范围。总体实验设计充分、客观。

### 6. 论文的主要结论与发现

- MTGP-BS在160次直接比较中统计显著优于对比方法140次，表现出最高的表达式精度和结构正确性（表1、表3）。
- 消融实验证明双向提取和共识加速Shapley分析均对性能有显著贡献（图4、图5）。
- 后处理框架具有通用性，可以显著提升多种多任务优化算法的性能（图6、图7）。
- 在构造的MTSR问题和真实案例（人口与碳排放预测）上同样取得最佳结果（图8、图10、表4）。
- 敏感性分析显示模型数K=5是性能与运行时的最佳折中（图9）。

### 7. 优点

- **方法论创新**：首次系统解决MTGP中“赢家通吃”引起的知识丢失问题，提出后处理合成范式，而非修改演化过程。
- **技术亮点**：
  - 双向合作提取通过频率聚类、条件性跨任务补充和最优个体注入，生成紧凑高质量档案，克服了原始子表达式的冗余和噪声。
  - 共识加速Shapley分析利用多模型归因和双重共识（投票+轮盘赌），显著提高了重要性评估的稳定性和可靠性，并有理论支撑。
- **实验全面**：涵盖多样问题、多个基线、消融、通用性、敏感性及真实案例，统计严谨。
- **实用性**：后处理模块可即插即用，运行开销低，易于集成到现有MTGP流程。

### 8. 不足与局限

- **算力资源未公开**：缺少GPU型号/数量、训练时长等细节，影响复现和性能评估。
- **实验覆盖**：仅测试了5个特定多任务基线，未考虑其他如多任务神经网络或更先进的进化多任务方法。另外，构造的MTSR问题数量较少（6个）。
- **偏差风险**：所有基准为两任务场景，多任务数量≥3时框架有效性未验证。使用的函数集（“+”“-”拆分）可能不适用于含乘除或更复杂运算的表达式（论文中明确子表达式是通过“+”和“-”拆分，但实际库中可能包含其他运算符？文中未明确限制，但框架可能更适用线性可组合情况）。
- **应用限制**：后处理合成依赖于子表达式作为特征，要求表达式可分解为加法形式，对于非加法结构（如嵌套函数、乘积）可能效果受限。此外，SHAP分析假设特征独立性，子表达式之间可能存在依赖，可能影响归因准确性。

（完）
