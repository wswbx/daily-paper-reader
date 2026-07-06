---
title: "MetaSymNet: A Tree-like Symbol Network with Adaptive Architecture and Activation Functions"
title_zh: MetaSymNet：具有自适应架构和激活函数的树状符号网络
authors: "Yanjie Li, Weijun Li, Lina Yu, Min Wu, Jingyi Liu, Shu Wei, Yusong Deng, Meilan Hao"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/34915/37070"
tags: ["query:sr"]
score: 10.0
evidence: 用于符号回归的树状符号网络
tldr: 现有符号回归方法在复杂任务上性能不佳，且忽略了符号的数值意义。MetaSymNet提出树状符号网络，可自适应调整架构和激活函数，利用数值优化求解符号回归。在多个基准上优于遗传编程和强化学习方法，展示了有效性和可扩展性。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
motivation: 现有符号回归方法忽视符号的数值意义，复杂任务表现差。
method: 构建树状符号网络，通过数值优化自适应调整结构和激活函数。
result: 在多个基准上超越遗传编程和强化学习方法。
conclusion: MetaSymNet为符号回归提供了更高效的数值优化范式。
---

## Abstract
Mathematical formulas are the language of communication between humans and nature. Discovering latent formulas from observed data is an important challenge in artificial intelligence, commonly known as symbolic regression(SR). The current mainstream SR algorithms regard SR as a combinatorial optimization problem and use Genetic Programming (GP) or Reinforcement Learning (RL) to solve the SR problem. These methods perform well on simple problems, but poorly on slightly more complex tasks. In addition, this class of algorithms ignores an important aspect: in SR tasks, symbols have explicit numerical meaning. So can we take full advantage of this important property and try to solve the SR problem with more efficient numerical optimization methods? Extrapolation and Learning Equation (EQL) replaces activation functions in neural networks with basic symbols and sparsifies connections to derive a simplified expression from a large network. However, EQL's fixed network structure can't adapt to the complexity of different tasks, often resulting in redundancy or insufficient, limiting its effectiveness. Based on the above analysis, we propose MetaSymNet, a tree-like network that employs the PANGU meta-function as its activation function. PANGU meta-function can evolve into various candidate functions during training. The network structure can also be adaptively adjusted according to different tasks. Then the symbol network evolves into a concise, interpretable mathematical expression. To evaluate the performance of MetaSymNet and five baseline algorithms, we conducted experiments across more than ten datasets, including SRBench. The experimental results show that MetaSymNet has achieved relatively excellent results on various evaluation metrics.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：符号回归（Symbolic Regression, SR）旨在从观测数据中自动发现可解释的数学表达式。主流方法（如遗传编程GP、强化学习RL）将SR看作组合优化问题，虽然对简单问题有效，但在复杂任务上性能显著下降，因为搜索空间呈指数增长。
- **被忽视的关键特性**：在SR中，每个符号（如`+`、`sin`、`x`）具有明确的数学含义，而传统组合优化方法仅将其视为无意义的“动作”。这一特性可以用于更高效的**数值优化**，而不是离散搜索。
- **现有神经方法（EQL）的不足**：Equation Learner（EQL）用固定符号作为激活函数，并通过稀疏化提取表达式，但存在两个主要问题：①稀疏化难以平衡精度和简洁性；②网络结构固定，无法适应任务复杂度，导致冗余或欠拟合。

**整体含义**：本文提出一种新的SR范式——将SR重新表述为**数值优化问题**，利用符号的数学意义，通过可微分训练直接学习符号网络，从而在保持可解释性的同时提升效率与性能。

### 2. 论文提出的方法论

#### 核心思想
MetaSymNet是一个**树状符号网络**，每个节点对应一个神经单元。内部节点使用**PANGU元函数**作为激活函数，叶节点使用**Variable元函数**。网络结构可在训练过程中根据梯度信息自适应调整（增长或缩减），最终演化为简洁的数学表达式。

#### 关键技术细节

- **PANGU元函数（PANGU Meta-Function）**  
  每个内部节点输出：  
  `OUT = w * (E · O) + b`  
  其中：
  - `O = [x_l + x_r, x_l - x_r, x_l * x_r, x_l / x_r, sin(x_l), cos(x_l), exp(x_l), log(x_l), sqrt(x_l), x_1, ..., x_n]`，是预定义候选函数（二元和一元）的输出向量。
  - `Z = [z_1, ..., z_n]` 是可优化的选择参数，通过softmax得到概率分布 `E = softmax(Z)`。
  - `w` 和 `b` 分别为幅度和偏置参数，也参与优化。

- **Variable元函数（Variable Meta-Function）**  
  叶节点输出：  
  `OUT = w * (E · X) + b`  
  其中 `X = [x_1, ..., x_k]` 为输入变量，`D = [d_1, ..., d_k]` 作为可优化选择参数，通过softmax确定变量概率。最终选中概率最高的两个变量，并依据精度从候选函数中匹配最佳符号。

- **参数优化**  
  交替优化两组参数：①幅度集`W`和偏置集`B`；②选择参数集`Z`和`D`。先训练`W`和`B`，再优化`Z`和`D`，反复迭代多轮后，根据`Z`和`D`确定每个节点演化的具体符号，并从网络中提取公式，进一步精炼常数。

- **网络结构动态调整**  
  基于梯度信息自动调整树结构：
  - **增长**：当叶节点演变为一元或二元函数时，该节点替换为PANGU元函数，并添加新的叶节点作为输入。
  - **缩减**：当内部节点演变为变量时，其子树被剪除，节点退化为Variable元函数。
  - 该机制避免了人工预设拓扑，使结构自动匹配任务复杂度。

- **损失函数**  
  `L = MSE + λ · L_entropy`，其中 `L_entropy = - (1/M) Σ log(max(E_j))`，引入熵项鼓励每个PANGU元函数的选择概率分布向one-hot形式集中（即一个大值、其余很小），从而促进明确演化。

### 3. 实验设计

- **数据集与场景**：
  - **标准数据集**：Nguyen（10个）、Keijzer（6个）、Korns（5个）、Constant、Livermore、Vladislavleva、R、Jin、Neat、Others，共10组标准基准。
  - **SRBench**：包含Feynman、Strogatz、Black-box子集，用于评估实际科学计算场景。
  - 噪声鲁棒性测试：在y上添加不同级别噪声（0~10%），评估R²变化。
  - 推理时间测试：选择所有方法都能达到R²>0.99的表达式，测量平均时间。

- **对比方法**（五个当前最优基线）：
  - DSO（强化学习+遗传编程）
  - TPSR（基于Transformer的规划）
  - SPL（MCTS符号物理学习器）
  - NeSymReS（Transformer预训练生成前置表达式）
  - EQL（方程学习器，固定网络+稀疏化）

- **评估指标**：
  - 拟合能力：决定系数 R²
  - 结果复杂度：表达式二叉树节点数
  - 噪声鲁棒性：不同噪声水平下的平均R²
  - 推理效率：R²-时间帕累托图

- **公平性措施**：
  - 严格控制所有算法使用相同的输入采样区间和符号约束库。
  - 每个表达式运行20次取平均值，置信水平0.95。

### 4. 资源与算力

- **未明确说明**：论文没有提及使用的GPU型号、数量或训练时长。仅提到数值优化算法（如SGD、BFGS、L-BFGS）进行参数训练，但未报告具体硬件消耗。因此无法量化算力需求。

### 5. 实验数量与充分性

- **实验数量**：主实验覆盖13个数据集（标准10个+SRBench 3个），每个数据集内包含多个表达式（共约60+个目标函数）。此外进行了：
  - 噪声鲁棒性实验（10个噪声级别 × 20次重复）
  - 推理时间实验（选出的表达式×10次）
  - 结果复杂度对比（所有方法R²>0.999的表达式）
  - 消融实验（有无熵损失）
- **充分性评估**：
  - **充分**：覆盖多个领域（数学、物理、工程），采用标准化基准（SRBench），对比了三种主流的SR范式（GP、RL、Transformer、EQL），进行了消融和鲁棒性分析。
  - **客观公平**：报告了平均值和标准差，严格控制了实验条件，但未提供跨方法超参数调优的详细说明。
  - **局限**：缺少对超参数（如λ）敏感性分析；没有提到是否在不同随机种子下验证稳定性（虽有多轮重复）。

### 6. 论文的主要结论与发现

- MetaSymNet在大部分数据集上取得**SOTA R²**（平均值0.9859，优于DSO的0.9749等）。
- 噪声鲁棒性显著优于所有基线，在高噪声（10%）时仍保持较高R²。
- 推理效率与TPSR接近，但在复杂度（平均节点数）上优于除TPSR外的所有方法（25.3 vs TPSR 24.4），表明能同时兼顾精度与简洁。
- 消融实验验证了熵损失的有效性：引入后R²从0.9743提升至0.9859，节点数减少，时间缩短。

### 7. 优点

- **方法创新**：将符号回归重新定义为数值优化问题，利用符号的数值含义进行可微分优化，避免了组合爆炸。
- **自适应结构与激活函数**：PANGU元函数和Variable元函数使得网络能在训练中自动选择符号并调整拓扑，无需手动设计或后期稀疏化。
- **高效率**：相比RL/GP方法，数值优化收敛更快，在精度和时间上达到良好平衡。
- **可解释性**：最终输出是清晰的数学表达式，适合高风险决策领域（金融、医疗、法律）。
- **实验设计严谨**：包含多种对比方法、多数据集、消融实验和噪声测试，证据充分。

### 8. 不足与局限

- **超参数敏感**：损失函数中的λ难以自动调整，可能需要多次试错。
- **局部最优陷阱**：方法可能收敛到近似而非精确表达式，特别是在复杂非凸场景。
- **搜索策略单一**：当前使用贪心策略选择符号，未来需探索更高级的搜索（如波束搜索、MCTS）以跳出局部最优。
- **缺少算力报告**：未给出训练时间或GPU型号，影响可复现性。
- **未处理常数优化**：虽然精炼常数，但未讨论如何高效学习复杂常数（如长期依赖的系数）。
- **扩展性验证有限**：仅在低维（最多10个变量）数据集上测试，对高维数据（>100维）的效果未知。

（完）
