---
title: Dimension Reduction for Symbolic Regression
title_zh: 符号回归的维度缩减
authors: "Paul Kahlmeyer, Markus Fischer, Joachim Giesen"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/33947/36102"
tags: ["query:sr"]
score: 10.0
evidence: 直接针对符号回归问题，通过变量替换降低维度
tldr: 本文针对符号回归中变量多导致公式恢复困难的问题，提出通过搜索固定变量组合并替换为单变量的方法降低问题维度，在多个合成和真实数据集上有效提高了符号回归算法的命中率和效率。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
motivation: 符号回归中变量增多时公式恢复变得非常困难，而自然公式中变量常以固定组合出现。
method: 通过搜索变量组合并替换为新变量来降低维度，减少搜索空间。
result: 在多种符号回归基准上，该方法显著提升了恢复正确公式的成功率。
conclusion: 维度缩减有效提升了符号回归在实际问题中的可扩展性。
---

## Abstract
Solutions of symbolic regression problems are expressions that are composed of input variables and operators from a finite set of function symbols. One measure for evaluating symbolic regression algorithms is their ability to recover formulae, up to symbolic equivalence, from finite samples. Not unexpectedly, the recovery problem becomes harder when the formula gets more complex, that is, when the number of variables and operators gets larger. Variables in naturally occurring symbolic formulas often appear only in fixed combinations. This can be exploited in symbolic regression by substituting one new variable for the combination, effectively reducing the number of variables. However, finding valid substitutions is challenging. Here, we address this challenge by searching over the expression space of small substitutions and testing for validity. The validity test is reduced to a test of functional dependence. The resulting iterative dimension reduction procedure can be used with any symbolic regression approach. We show that it reliably identifies valid substitutions and significantly boosts the performance of different types of state-of-the-art symbolic regression algorithms.

---

## 论文详细总结（自动生成）

# 符号回归的维度缩减——论文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：符号回归的目标是从观测数据中恢复出可解释的符号表达式。随着表达式中变量和运算符数量的增加（即复杂度增加），现有符号回归算法的恢复成功率急剧下降。  
- **动机**：许多自然出现的符号公式中，变量常以固定组合形式出现（例如 Washburn 方程中 `r * cos(ϕ)`）。如果能将这样的组合替换为一个新变量，就能减少变量个数，从而降低回归难度。  
- **整体含义**：通过系统性地发现并应用有效的变量替换，可以大幅提升符号回归算法在复杂公式上的恢复能力，且该方法与具体符号回归算法无关。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：  
  - 利用**输入替换**（input substitution）和**输出-输入替换**（out-input substitution）将原始高维回归问题转化为更低维的辅助回归问题。  
  - 通过枚举小型表达式 DAG（有向无环图）生成候选替换函数 `g` 或 `h`。  
  - 使用**函数依赖度量**（functional dependence measure）来检验候选替换是否有效：即变换后的输入与输出之间是否存在函数依赖。  
- **关键技术细节**：  
  - 函数依赖度量：使用 **Chatterjee 系数**（单变量）、**CODEC**（多变量）或 **KMAC**（基于核与几何图）来量化依赖程度，值越接近 1 表示越可能存在函数依赖。  
  - 对于输入替换 `g(x_I)`，检验观测数据 `(g(x_I), x_\I) -> y` 是否保持函数依赖。  
  - 对于输出-输入替换 `h(x_I, y)`，检验 `x_\I -> h(x_I, y)` 是否函数依赖，然后利用计算机代数系统（SymPy）反解出 `y`。  
- **算法流程**：  
  1. **搜索阶段**：以原始问题为根节点，对每个候选替换（由小 DAG 枚举得到）计算函数依赖分数。采用**束搜索**（beam search）按广度优先方式探索分数最高的 `beam_size` 个路径，迭代降低变量数。  
  2. **恢复阶段**：将束搜索中找到的最高得分简化问题交给任意符号回归算法（如 UDFS、DSR、PySR 等）求解，再沿路径反向组合得到原始公式。

## 3. 实验设计
- **数据集**：  
  - **Wikipedia eponymous equations**（880 个公式）：来自维基百科的知名方程。  
  - **Feynman symbolic regression dataset**（114 个公式）：从费曼物理学讲义中提取。  
- **基准方法**：  
  - 对比的符号回归算法：**UDFS**（搜索 DAG）、**DSR**（深度强化学习）、**TRANSF**（序列到序列学习）、**PySR**（遗传编程）、**Operon**（遗传编程）、**POLY**（二次多项式回归）。  
  - 对比的替换策略：仅使用**AIFeynman**的四类替换（加、减、乘、除）作为基线。  
- **评估指标**：  
  - **恢复率**（recovery rate）：公式恢复至符号等价的比例（用 SymPy 验证）。  
  - **模型拟合**：在保留测试集上的归一化均方根误差（NRMSE）。  
  - **模型复杂度**：表达式树的节点数（SymPy 简化后）。  
  - **降维率**：替换后变量数与原始变量数之比。

## 4. 资源与算力
- 论文明确说明**算力配置**：  
  - 一台 Intel Xeon Gold 6226R 64核处理器，128GB RAM，Python 3.10。  
  - **未提及 GPU** 使用，所有实验均在 CPU 上运行。  
  - 平均每个替换识别时间：CODEC 约 2.9–3.3 ms，KMAC 约 23–24 ms，体积法约 21–22 ms（表 1）。  
- **未提供总体训练时长**，但给出了单步替换的时间量级。

## 5. 实验数量与充分性
- **实验组数**：  
  - **参数研究**（图 3、表 1–3）：  
    - 对比三种依赖度量（CODEC、KMAC、体积法）在两种数据集、不同噪声水平下的降维率。  
    - 对比束搜索 beam size 1~5 的降维率。  
    - 对比替换类型（输入+输出、仅输入、仅 AIFeynman）。  
  - **恢复率实验**（表 4）：在 Feynman 数据集上对比 6 种符号回归算法（base vs. with beam search）的恢复率、NRMSE、复杂度。  
  - **消融分析**较充分：分别验证了依赖度量、束宽、替换类型的影响。  
- **充分性与公平性**：  
  - 数据集为公开基准；对比方法涵盖主流工作；使用符号等价验证而非近似匹配，结果客观。  
  - 对 Feynman 数据集还添加了不同噪声水平（图 3）。  
  - 不足之处：**未在 Wikipedia 数据集上报告恢复率结果**（论文声称在全文版中提供，但本摘要未包含），可能降低了实验完整性。

## 6. 主要结论与发现
- 在无噪声情况下，束搜索可将变量数减少约 **50%（Feynman）** 和 **35%（Wikipedia）**；噪声存在时 CODEC 和 KMAC 仍有效，而体积法失效。  
- 束搜索与任何符号回归算法结合均能**显著提升恢复率**（例如 UDFS 从 0.58→0.69，DSR 从 0.37→0.66，POLY 从 0.06→0.34）。  
- 输出-输入替换比仅输入替换带来更大的降维收益（Feynman: 0.49 vs. 0.39）。  
- 使用 CODEC 度量 + beam size=1 即可达到良好效果，且计算速度快。

## 7. 优点
- **方法通用性强**：可与任意现有符号回归算法结合，无需修改算法内部。  
- **理论简洁有效**：将发现替换转化为函数依赖检验，利用成熟统计工具（Chatterjee 系数、CODEC）。  
- **工程巧妙**：通过束搜索迭代简化问题，并用计算机代数系统自动验证替换有效性。  
- **实验全面**：覆盖多种算法类型、多种依赖度量、不同噪声水平，结果可信度高。

## 8. 不足与局限
- **搜索空间受限**：仅枚举最多一个中间节点和一个输出节点的 DAG，可能遗漏更复杂的替换（如嵌套函数）。  
- **依赖度量阈值问题**：论文未明确给出判断替换有效的具体截断值，实际使用时需调参。  
- **实验覆盖不完整**：未在 Wikipedia 数据上报告恢复率结果；仅在 Feynman 数据上进行了完整的恢复率对比。  
- **可扩展性**：替换必须满足“输出替换后仍保持函数依赖”，对高度非线性或噪声极大的场景可能失效。  
- **计算开销**：虽然单步替换快，但束搜索需多次枚举和检验，当变量数很多或搜索空间大时可能耗时较长。

（完）
