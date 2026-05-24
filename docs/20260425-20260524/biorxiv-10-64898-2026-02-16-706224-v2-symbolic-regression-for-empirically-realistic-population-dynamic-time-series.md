---
title: Symbolic regression for empirically realistic population dynamic time series
title_zh: 符号回归用于经验现实的人口动态时间序列
authors: "Jarman, C. N., Levi, T., Novak, M."
date: 2026-05-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.16.706224v2.full.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 符号回归用于生态种群动态
tldr: 研究评估了符号回归在具有现实特征（如低采样密度、过程噪声、周期不对称和伪变量）的生态时间序列中恢复人口模型的能力。通过合成数据实验发现，采样密度和过程噪声的权衡是关键：低于每周期10点无法恢复，但高采样密度下噪声反而提高恢复率。然而，真实模型虽常被恢复，却被评价工作流不一致地选中，凸显了后算法选择标准的必要性。
source: biorxiv
selection_source: fresh_fetch
motivation: 符号回归在实验室数据中成功重构人口模型，但能否处理野外数据的现实复杂性尚不清楚。
method: 通过改变采样密度、过程噪声、周期不对称性和伪变量，生成合成时间序列，并比较两种预处理和四种评价工作流。
result: 采样密度低于每周期10点时失败，高于25点时常恢复真实模型，但评价工作流未能一致选择它。
conclusion: 需要更鲁棒的后算法选择标准来从竞争模型中识别正确方程。
---

## 摘要
机器学习在生态学中的应用正在迅速扩展。符号回归因其在从模拟和实验室基于种群时间序列中逆向工程可读的解释性种群模型（包括逻辑增长和Lotka-Volterra方程）的成功而受到特别关注。然而，基于野外的种群通常缺乏先前评估中使用的理想化时间序列的特征。我们通过量化符号回归在采样密度、种群周期不对称性、过程噪声和虚假变量的错误考虑等因素变化下的合成数据上的成功程度，评估了其对此类时间序列的效用。我们还比较了两种估计种群增长率的数据预处理选项，以及四种用于选择方程式的评估工作流。结果表明，采样密度和过程噪声之间的权衡主要驱动方程和变量的恢复。当每个周期的采样密度低于10个点时，符号回归未能恢复底层方程；然而，在更高的采样密度下，过程噪声确实增加了方程恢复率。重要的是，尽管在每周期25个或更多点的采样密度下经常恢复真实模型，但评估工作流并未一致地选择它。这一差异突出了需要更鲁棒的算法后选择标准来在竞争候选者中识别焦点方程。

## Abstract
Applications of machine learning in ecology are rapidly expanding. Symbolic regression is gaining particular attention for its success in reverse-engineering human-readable explanatory population models, including the logistic growth and Lotka-Volterra equations, from simulated and laboratory-based population time series. However, field-based populations often lack the characteristics of the idealized time series used in prior assessments. We evaluated the utility of symbolic regression for such time series by quantifying its success for synthetic data varying in sampling density, population cycle asymmetry, process noise, and the erroneous consideration of spurious variables. We further compared two data preprocessing options for estimating population growth rates, and four evaluation workflows for selecting equations. Results indicate that a trade-off between sampling density and process noise primarily drives equation and variable recovery. Symbolic regression failed to recover the underlying equation at sampling densities below 10 points per cycle; however, at higher sampling densities, process noise did increase equation recovery rates. Importantly, although the true model was frequently recovered at sampling densities of 25 or more points per cycle, it was not consistently selected by the evaluation workflows. This discrepancy highlights a need for more robust post-algorithm selection criteria to identify the focal equation among competing candidates.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：符号回归（Symbolic Regression）作为一种机器学习方法，在从模拟和实验室种群时间序列中逆向工程出可解释的种群模型（如逻辑增长方程和Lotka-Volterra方程）方面已取得成功。然而，野外种群的时间序列通常不具备这些理想化特征（如高采样密度、低噪声、无伪变量等）。本研究旨在评估符号回归在更接近现实生态数据的复杂条件下（低采样密度、周期不对称性、过程噪声、伪变量干扰）能否有效恢复底层种群动态方程。
- **整体意义**：揭示符号回归在现实生态数据中的适用性边界，并指出当前评价工作流在模型选择上的不足，为生态学中可解释机器学习方法的实际应用提供指导。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：通过合成数据实验，系统改变影响时间序列现实性的多个因素（采样密度、周期不对称性、过程噪声、伪变量），测试符号回归在不同条件下的方程恢复成功率。同时比较两种数据预处理策略和四种模型评价工作流。
- **关键技术细节**：
  - 数据生成：使用已知的种群动态模型（如逻辑增长、Lotka-Volterra等）生成合成时间序列，人为添加不同水平的过程噪声、改变采样密度（每周期点数）、调整周期不对称性（波形形状）、引入不相关的伪变量（如温度、降水等无关协变量）。
  - 预处理选项：两种估计种群增长率的方法（例如直接差分或平滑后差分）。
  - 符号回归算法：采用标准符号回归算法（未指定具体软件包），在候选方程中搜索拟合度最好的表达式。
  - 评价工作流：四种不同的模型选择策略，可能基于AIC、BIC、交叉验证误差或拟合优度等指标。
- **算法流程（文字描述）**：
  1. 选择真实种群模型（如逻辑增长方程 \( dN/dt = rN(1-N/K) \)）。
  2. 生成时间序列数据，设置参数：采样密度 \( S \)（每周期点数）、过程噪声强度 \( \sigma \)、周期不对称系数、伪变量个数。
  3. 对时间序列进行预处理（两种方案）。
  4. 运行符号回归，产生一组候选方程。
  5. 应用四种评价工作流分别从候选集中选择“最佳”方程。
  6. 统计真实模型被恢复并被正确选中的次数。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集/场景**：全部为合成数据。变量包括：
  - 采样密度：从极低（<10点/周期）到高（≥25点/周期）。
  - 过程噪声：不同标准差水平。
  - 周期不对称性：对称vs非对称波形。
  - 伪变量：引入1~2个无关变量。
- **Benchmark**：未明确提及外部标准，以能否恢复生成数据的真实方程作为成功标准。
- **对比方法**：
  - 两种数据预处理方案（增长率估计方法）。
  - 四种评价工作流（模型选择标准）。未与其他机器学习方法（如神经网络、随机森林）对比。

## 4. 资源与算力（若有说明）

- 论文中未明确提及使用的GPU型号、数量或训练时长等算力信息。从预印本内容看，符号回归通常不需要大量GPU资源，但此处无相关数据。

## 5. 实验数量与充分性

- **实验数量**：论文未详细列出具体实验组数，但根据描述，实验涵盖多个维度（采样密度、噪声、不对称性、伪变量），每个维度取若干水平，组数可观。
- **充分性判断**：
  - 优点：系统控制了多个现实因素，变量覆盖较全面。
  - 不足：未包含不同模型形式（如复杂非线性、时滞模型）的比较，也未与真实野外数据（如已知的种群记录）进行对照。样本量或重复次数未明确，可能影响统计可靠性。
  - 客观性：合成数据允许已知真值，结果可量化。但仅依赖于一种符号回归算法和特定模型家族，推广性有限。

## 6. 论文的主要结论与发现

- **关键发现1**：采样密度和过程噪声之间存在权衡。当采样密度低于每周期10个点时，符号回归无法恢复底层方程；而当采样密度高于25点/周期时，方程恢复率显著提高，且过程噪声反而有助于提升恢复率（可能是噪声带来更多信息或避免过拟合）。
- **关键发现2**：即使在高采样密度下真实模型经常被恢复，但四种评价工作流并未一致地选择它，说明当前的后算法选择标准不够鲁棒，容易选错候选者。
- **结论**：符号回归在实际生态时间序列中的应用受限于采样密度，且需要更可靠的模型选择准则来从多个竞争方程中识别正确的动力学模型。

## 7. 优点：方法或实验设计上的亮点

- **系统性**：同时考察了多个影响现实生态数据的关键因素（采样、噪声、不对称、伪变量），提供多维度的性能图谱。
- **务实性**：聚焦于实际野外数据常见的非理想条件，而非理想化模拟，增强了实用性。
- **对比预处理与评价工作流**：首次系统比较不同增长率估计方法和模型选择策略对符号回归结果的影响，为实践者提供具体操作建议。

## 8. 不足与局限

- **实验覆盖局限**：
  - 只使用了一种符号回归算法，未对比其他算法（如遗传编程的不同变体、深度符号回归等）。
  - 仅基于有限的几种种群模型（如逻辑增长、Lotka-Volterra），未扩展到更真实的复杂动态（如混沌、多物种交互、延迟效应等）。
  - 伪变量数量和种类有限，未考虑测量误差、缺失数据等更现实的复杂情况。
- **偏差风险**：合成数据基于已知模型，与现实生态数据的随机性仍有差距；未使用真实野外数据验证结论的泛化能力。
- **应用限制**：论文指出在采样密度低于每周期10点时无法恢复，而许多野外监测数据实际采样密度可能更低。此外，评价工作流的不一致意味着实际应用中难以确定哪个模型是“正确”的，限制了可操作性。
- **资源与算力信息缺失**：无法评估方法的计算复杂度。

（完）
