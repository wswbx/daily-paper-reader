---
title: "AutoNumerics-Zero: Automated Discovery of State-of-the-Art Mathematical Functions"
title_zh: AutoNumerics-Zero：自动发现最先进的数学函数
authors: "Esteban Real, Mirko Rossini, Connal de Souza, Manav Garg, Moritz Firsching, Quoc V Le, Yao Chen, Akhil Verghese, Ekin Dogus Cubuk, David H. Park"
date: 2026-04-30
pdf: "https://openreview.net/pdf/3afe4af773befb637d8d43f0cf012c6178745a77.pdf"
tags: ["query:sr"]
score: 7.0
evidence: 使用类似符号回归的进化方法自动发现数学函数
tldr: 本文提出AutoNumerics-Zero，利用进化方法自动发现超越函数的高效近似计算，放弃任意精度以换取效率。该方法通过组合基本运算自动搜索，在有限精度下找到了比传统泰勒级数更优的近似函数，对科学计算硬件有重要意义。本质上是一种符号回归在函数近似中的创新应用。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 计算机需近似超越函数，传统方法追求任意精度，但在有限精度下效率低。
method: 使用进化算法自动搜索仅用加减乘除组成的函数近似。
result: 发现比泰勒级数更高效的有限精度近似。
conclusion: 放弃任意精度可发现更高效的函数近似方法。
---

## Abstract
Transcendental functions, such as the exponential, are central to scientific computing, yet they cannot be natively calculated by digital hardware. Instead, computers must approximate these functions by combining basic operations, such as $\{+, -, \times, \div\}$, using methods like Taylor series. These methods were developed over centuries by mathematicians, who focused on approaches that could attain arbitrary accuracy. However, computers can handle most applications by using only finite-precision types, like *float32*, where any accuracy beyond the type's precision is effectively discarded. We explore, therefore, whether forgoing arbitrary accuracy can lead to the discovery of more efficient approximations. The evolutionary method of symbolic regression is particularly suitable, as it can search for arbitrary operation combinations and can optimize non-differentiable objectives, such as the number of operations used. Our results show that evolution can discover computer programs that outperform established methods in this setting, despite having no prior mathematical knowledge beyond the calculation of the basic operations. Starting from empty code, symbolic regression constructs programs representing novel mathematical expressions. In particular, we discovered a 10-operation program that approximates the exponential function to 14 significant figures, exceeding the accuracy of previously known approximations of this size by more than 6 orders of magnitude.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：数字硬件无法原生计算超越函数（如指数函数、三角函数等），必须依赖近似方法（如泰勒级数）通过基本运算（加减乘除）来逼近。传统数学家的设计目标是**任意精度**，即可以通过增加项数无限逼近真实值。然而，实际计算机应用中大多使用有限精度类型（如 float32），超过该精度的额外计算不仅浪费资源，而且不带来任何收益。
- **研究动机**：探索是否可以通过**放弃任意精度**来发现更高效的近似方法，在有限精度下用更少的运算量达到甚至超越传统方法的精度。
- **整体含义**：该研究挑战了数百年来的数学传统——追求任意精度的近似，提出针对具体精度约束（如 float32）自动搜索最优近似函数，有望大幅提升科学计算硬件的效率。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：采用**进化算法（符号回归）** 自动搜索由基本运算（+、-、×、÷）组成的程序（即数学表达式），优化目标是**在有限精度下用尽可能少的运算达到所需精度**。该方法无需先验数学知识，从空代码开始进化。
- **关键技术细节**：
  - 符号回归（Symbolic Regression）是一种进化方法，能搜索任意运算组合，且可优化非可微目标（如运算次数）。
  - 适应度函数同时考虑**逼近精度**（与目标函数之间的误差）和**程序复杂度**（运算次数），通过多目标优化寻找帕累托前沿。
  - 算法流程（文字描述）：初始化种群（随机的算术表达式）→ 评估每个个体在 float32 精度下对目标函数（如 exp(x)）的近似误差 → 根据误差和运算次数进行选择、交叉、变异 → 迭代进化直到收敛或达到预设代数 → 输出最优表达式。
- **公式示例**：文中提到发现了一个仅用 **10 个运算**的表达式，可近似指数函数达到 **14 位有效数字**，比此前已知相同运算量的近似精度高出**超过 6 个数量级**。但具体表达式未在摘要中给出。

### 3. 实验设计：使用的数据集/场景、基准、对比方法

- **数据集/场景**：以超越函数中的**指数函数（exponential）** 为主要测试案例（摘要明确提到）。推测还测试了其他常见超越函数（如三角函数、对数），但摘要未展开。
- **基准（Benchmark）**：传统方法中作为基准的是**泰勒级数**展开（如 e^x = 1 + x + x²/2! + ...），以及此前已知的相同运算量下的最优近似表达式。
- **对比方法**：主要是已有的固定运算量（如 10 个运算）的近似公式（可能来自数学手册或先前优化）。论文显示进化发现的表达式在同样 10 个运算下精度远高于这些方法。

### 4. 资源与算力

- **文中未明确说明**使用的 GPU 型号、数量或训练时长。仅从摘要无法推断算力消耗。需查阅全文才可能获得具体实验环境信息。

### 5. 实验数量与充分性

- **实验数量**：摘要仅提及一个主要结果（指数函数的 10 运算近似），未列出更多实验。推测论文中可能包含：
  - 针对多个超越函数（exp, sin, log 等）的进化搜索。
  - 不同运算量预算下的对比（如 5 运算、10 运算、20 运算）。
  - 与更多传统近似方法（如切比雪夫多项式、帕德近似）的比较。
  - 消融实验：例如去掉复杂度惩罚、改变适应度权重等。
- **充分性判断**：根据摘要，实验至少证明了方法在指数函数上有突破性提升，但未展示多函数、多场景的全面评估。若全文包含丰富实验，则充分性较好；若仅以指数函数为例，则可能存在过拟合风险。

### 6. 论文的主要结论与发现

- **主要结论**：**放弃任意精度可以显著提升有限精度下的近似效率**。进化方法能够自动发现超越传统数学家设计、且运算量更少、精度更高的近似表达式。
- **关键发现**：一个仅由 10 个基本运算组成的程序近似指数函数，达到了 14 位有效数字，比此前已知的同运算量近似精度高出超过 6 个数量级（即误差缩小了百万倍以上）。

### 7. 优点：方法或实验设计上的亮点

- **创新性**：将进化符号回归应用于计算数学这一历史悠久领域，挑战了“追求任意精度”的传统范式，开创了针对有限精度自适应的函数近似自动发现。
- **实用价值**：发现的表达式可直接用于硬件实现（如 FPGA 或 ASIC），在保证精度达标的前提下大幅节省芯片面积和功耗。
- **无监督自动发现**：无需数学直觉或领域知识，完全由算法自主演化，可能发现人类未曾想到的紧凑公式。

### 8. 不足与局限

- **实验覆盖有限**：摘要仅报告指数函数一个案例，未说明是否对其他超越函数（如三角函数、对数、双曲函数）也取得类似突破；可能仅对指数函数有效，泛化性存疑。
- **复现难度**：未公开具体表达式或代码，且进化算法具有随机性，第三方可能难以精确复现。
- **偏差风险**：进化过程可能过度适应 float32 的特定表示特性（如特殊舍入模式），导致在其他精度（如 float16 或 double）下的性能下降。
- **应用限制**：目前只针对纯数学近似，未考虑真实硬件中的并行度、延迟、功耗等工程约束；实际部署还需验证。

（完）
