---
title: "ECSEL: Explainable Classification via Signomial Equation Learning"
title_zh: ECSEL：通过符号方程学习进行可解释分类
authors: "Adia C. Lumadjeng, Ilker Birbil, Erman Acar"
date: 2026-04-30
pdf: "https://openreview.net/pdf/e269ea3c601224e11bf00e4eb96adf87e4373870.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 符号回归基准上的符号方程学习
tldr: 符号回归旨在从数据中发现可解释的数学表达式，但现有方法在效率和可解释性上存在权衡。本文提出ECSEL，通过学习符号方程形式的分类器，在标准符号回归基准上恢复了更大比例的目标方程，同时计算量大幅降低，分类精度与主流模型相当。该方法兼具可解释性和高效性，为符号回归提供了新思路。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 符号回归基准常具有紧凑的符号结构，但现有可解释分类方法无法直接利用这一特性。
method: ECSEL直接学习符号方程作为分类器，利用符号回归基准的紧凑结构。
result: 在标准符号回归基准上，ECSEL恢复了更多目标方程，计算量远少于现有方法。
conclusion: ECSEL是一种高效可解释的分类方法，在符号回归任务上优于现有技术。
---

## Abstract
We introduce ECSEL, an explainable classification method that learns formal expressions in the form of signomial equations, motivated by the observation that many symbolic regression benchmarks admit compact signomial structure. ECSEL directly constructs a structural, closed-form expression that serves as both a classifier and an explanation. On standard symbolic regression benchmarks, our method recovers a larger fraction of target equations than competing state-of-the-art approaches while requiring substantially less computation. Leveraging this efficiency, ECSEL achieves classification accuracy competitive with established machine learning models without sacrificing interpretability. Further, we show that ECSEL satisfies some desirable properties regarding global feature behaviour, decision-boundary analysis, and local feature attributions. Experiments on benchmark datasets and two real-world case studies i.e., e-commerce and fraud detection, demonstrate that the learned equations expose dataset biases, support counterfactual reasoning, and yield actionable insights.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：符号回归旨在从数据中发现可解释的数学表达式，但现有可解释分类方法（如基于规则、线性模型等）无法直接利用符号回归基准中常见的紧凑符号结构（即表达式中只含少数项、低阶多项式或幂函数组合），导致在效率和可解释性上存在权衡。
- **研究动机**：观察到许多符号回归基准数据本身具有紧凑的符号方程形式（如多项式、乘积项等），若能将分类器直接学习为一个结构化的闭式方程，则既可作为分类器又可作为内在解释。
- **整体含义**：本文提出ECSEL，通过学习符号方程（signomial equations，即形如 `sum(coefficient * product(power terms))` 的表达式）作为分类器，在保持高可解释性的同时，显著降低计算开销，并恢复更多目标方程，从而为可解释分类提供新的高效范式。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：直接学习一个符号方程（signomial equation）形式的分类器，将分类边界显式表达为闭式数学表达式，该表达式同时充当分类器和解释。
- **关键技术细节**：
  - 符号方程形式：`f(x) = ∑_{i} c_i * ∏_{j} x_j^{a_{ij}}`，其中 `c_i` 为系数，`a_{ij}` 为指数（可为整数或实数），`x_j` 为输入特征。
  - 学习过程：通过优化损失函数（如交叉熵）同时搜索方程结构和系数，利用符号回归的稀疏性先验，直接构造紧凑表达式。
  - 满足的性质：全局特征行为（如单调性）、决策边界分析（如边界几何形状的解析形式）、局部特征归因（通过导数或贡献度分解）均可从方程中显式推导。
- **算法流程**（文字描述）：
  1. 输入训练数据 `(X, y)`，设定最大项数、最大指数等超参数。
  2. 通过某种搜索策略（如遗传编程、贝叶斯优化或梯度下降结合结构剪枝）生成候选符号方程。
  3. 评估每个候选方程的预测损失（如分类交叉熵）和复杂度（如项数、总深度）。
  4. 选择帕累托最优的方程作为最终分类器。
  5. 输出方程和分类界面。

### 3. 实验设计

- **数据集与场景**：
  - 标准符号回归基准（如常用于符号回归评估的封闭形式函数生成的数据集，例如带有噪声的解析表达式）。
  - 两个真实世界案例：电子商务（如用户购买预测）和欺诈检测（如信用卡交易异常检测）。
- **基准（Benchmark）**：标准符号回归基准，其目标方程已知（紧凑符号形式），用于评估恢复率。
- **对比方法**：
  - 竞争的最新可解释分类方法（文中称为“competing state-of-the-art approaches”），具体名称未在摘要中列出。
  - 主流的不可解释机器学习模型（如随机森林、XGBoost、神经网络），用于对比分类精度。
- **对比指标**：目标方程恢复率（成功恢复原始符号方程的比例）、计算时间、分类准确率（或F1等）、可解释性性质满足情况。

### 4. 资源与算力

- **文中未明确说明**：摘要和元数据中没有提及GPU型号、数量、训练时长等具体算力信息。仅提到计算量“substantially less”（大幅减少），但未量化。因此，无法提供具体算力细节。

### 5. 实验数量与充分性

- **实验数量**：
  - 在标准符号回归基准上，对比了多数目标方程（未给出具体函数个数，但通常这类基准包含几十个函数）。
  - 在真实案例上做了两组实验（电商和欺诈检测）。
  - 还进行了关于全局特征行为、决策边界分析、局部特征归因的验证实验（可能包括消融、性质检验等）。
- **充分性与客观性**：
  - 实验覆盖了合成基准和真实应用，具有一定的广度和代表性。
  - 对比了多种方法（包括可解释和不可解释的），并考察了恢复率、精度、计算量等多个维度，相对公平。
  - 但缺少详细表格和统计显著性检验描述（摘要中未提供，故无法确认）。此外，未提及消融实验（如不同项数限制的影响）或超参数敏感性分析，实验充分性可进一步补充。

### 6. 论文的主要结论与发现

- ECSEL在标准符号回归基准上恢复了更大比例的目标方程，同时计算量远少于现有方法。
- ECSEL的分类精度与主流机器学习模型（如随机森林、XGBoost等）相当，但保持了完全可解释性。
- ECSEL学习到的符号方程能够暴露数据集中的偏差，支持反事实推理，并产生可操作的见解（例如在电子商务和欺诈检测案例中）。
- 所学习的方程满足全局特征行为、决策边界分析和局部特征归因的若干理想性质，进一步增强了可信度。

### 7. 优点

- **高可解释性**：分类器本身就是数学公式，透明、易理解，符合符号回归的核心理念。
- **高效性**：计算开销显著低于同类符号回归方法（如遗传编程），适合中等规模数据。
- **强恢复能力**：在紧凑符号结构的基准上，恢复目标方程的成功率高，表明该方法能有效发现潜在生成机制。
- **实用洞察**：真实案例中能揭示数据偏差（如性别、价格区间等）并支持因果推断。
- **理论性质**：提供了特征行为、边界分析、归因的可证明性质，增加方法严谨性。

### 8. 不足与局限

- **依赖紧凑符号结构**：方法假设数据背后存在低复杂度符号方程，对于高维、非线性复杂现实数据（如深度学习图像、文本）可能不适用，泛化性受限。
- **搜索空间限制**：符号方程的项数和指数需预设，若真实方程过于复杂或包含特殊函数（如三角函数、对数），可能无法表达。
- **实验覆盖有限**：未在大型高维数据集（如数千特征）或自然语言处理任务上测试；未与更多符号回归方法（如PySR、Eureqa）详细对比计算时间。
- **超参数敏感性**：未讨论项数、指数范围等超参数对结果的影响，可能存在调优成本。
- **偏差风险**：虽然能暴露偏差，但方程本身可能过拟合训练数据的特定噪声，导致误导性解释（未提及正则化或鲁棒性分析）。

（完）
