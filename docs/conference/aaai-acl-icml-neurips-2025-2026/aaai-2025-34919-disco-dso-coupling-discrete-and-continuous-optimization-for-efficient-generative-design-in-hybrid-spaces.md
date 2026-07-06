---
title: "DisCo-DSO: Coupling Discrete and Continuous Optimization for Efficient Generative Design in Hybrid Spaces"
title_zh: DisCo-DSO：耦合离散与连续优化实现混合空间高效生成式设计
authors: "Jacob F. Pettit, Chak Shing Lee, Jiachen Yang, Alex Ho, Daniel Faissol, Brenden Petersen, Mikel Landajuela"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/34919/37074"
tags: ["query:sr"]
score: 8.0
evidence: 符号回归作为应用场景被提及
tldr: 本文提出DisCo-DSO方法，通过生成模型联合优化离散和连续变量，解决混合空间黑箱优化问题。该方法在决策树学习和符号回归等任务上有效，相比解耦方法使用更少目标函数评估，对不可微目标鲁棒，并能从先前样本学习以指导搜索。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
motivation: 现有混合空间优化方法通常分别处理离散和连续变量，导致评估次数多且对不可微目标鲁棒性差。
method: 提出DisCo-DSO，使用生成模型学习离散和连续设计变量的联合分布，从而采样新的混合设计方案。
result: 在符号回归等任务上，联合优化方法比标准解耦方法使用更少目标函数评估，且对非可微目标更鲁棒。
conclusion: DisCo-DSO为混合离散连续空间的黑箱优化提供了一种高效且鲁棒的生成式方法。
---

## Abstract
We consider the challenge of black-box optimization within hybrid discrete-continuous and variable-length spaces, a problem that arises in various applications, such as decision tree learning and symbolic regression. We propose DisCo-DSO (Discrete-Continuous Deep Symbolic Optimization), a novel approach that uses a generative model to learn a joint distribution over discrete and continuous design variables to sample new hybrid designs. In contrast to standard decoupled approaches, in which the discrete and continuous variables are optimized separately, our joint optimization approach uses fewer objective function evaluations, is robust against non-differentiable objectives, and learns from prior samples to guide the search, leading to significant improvement in performance and sample efficiency. Our experiments on a diverse set of optimization tasks demonstrate that the advantages of DisCo-DSO become increasingly evident as problem complexity grows. In particular, we illustrate DisCo-DSO's superiority over the state-of-the-art methods for interpretable reinforcement learning with decision trees.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：论文关注混合离散-连续空间中的黑箱优化问题，该空间具有可变长度结构和前缀相关的位置约束。这类问题广泛存在于决策树学习、符号回归等领域。现有方法通常采用“解耦”策略：先通过深度学习优化离散骨架（如符号表达式结构），再使用独立优化器（如BFGS、模拟退火）优化连续参数。这种解耦方式导致每个候选解需要多次目标函数评估（用于连续优化），效率低下，且无法利用离散与连续之间的耦合信息。
- **动机**：作者提出联合优化离散和连续变量，有望减少评估次数、提高样本效率，并增强对非可微目标的鲁棒性。

#### 2. 论文提出的方法论

- **核心思想**：基于自回归生成模型与深度强化学习，学习离散序列与连续参数的联合分布，从而直接采样完整的候选解（同时包含离散骨架和连续参数）。
- **技术细节**：
    - 将每个token定义为`(l_i, β_i)`，其中`l_i`为离散token（可能带参数），`β_i`为连续参数（若`l_i`无参数则忽略）。
    - 模型（RNN/Transformer）在每个生成步输出两组logits：`ψ^((i))`用于离散token选择，`ϕ^((i))`用于连续参数分布（如截断正态分布）的参数。
    - 采样时，先根据`ψ^((i))`选择`l_i`，若`l_i`属于带参数集合，则根据`ϕ^((i))`和`l_i`采样`β_i`；否则忽略`β_i`。
    - 采用风险寻求策略梯度（risk-seeking policy gradient）训练，目标为`J_ε(θ)=E[R(τ)|R(τ)≥R_ε(θ)]`，鼓励模型关注高分样本。
    - 支持位置相关约束：通过将不可行token的logits设为`-∞`来强制执行。
    - 针对决策树节点参数边界，提出递归更新方法：每个决策节点根据父节点约束动态调整参数范围（如截断正态分布的可采样区间）。

#### 3. 实验设计

- **场景与数据集**：
    - **参数化位串任务（PB）**：人工合成任务，控制离散/连续奖励权重α和目标函数复杂度（f1: sinc函数多局部极值；f2: 分段函数不连续）。长度T可变。
    - **决策树策略优化**：使用OpenAI Gym四个环境：MountainCar-v0, CartPole-v1, Acrobot-v1, LunarLander-v2。每个环境评估1,000个随机种子的平均奖励。
    - **符号回归（SR）**：使用多个公开基准（附录给出具体数据集），评估测试集上的归一化MSE倒数。
- **基准方法**：
    - **解耦RL+连续优化器**：Decoupled-RL-{BFGS, anneal, evo}（即Deep Symbolic Regression方法）。
    - **解耦GP+连续优化器**：Decoupled-GP-{BFGS, anneal, evo}（遗传编程）。
    - **贝叶斯优化（BO）**：仅用于位串任务（固定长度）。
    - **文献对比**：进化决策树（Custode & Iacca 2023）、级联决策树（Ding et al. 2020）、可解释可微决策树（Silva et al. 2020）、以及符号回归方法（Biggio et al. 2021, Kamienny et al. 2022）。
- **模型配置**：所有RL方法和DisCo-DSO使用单层32单元RNN；GP使用DEAP库。

#### 4. 资源与算力
- **文中未明确说明**：未提及GPU型号、数量或训练时长。仅提到“使用Livermore Computing和实验室定向研究发展项目（21-SI-001）支持”，但无具体算力细节。

#### 5. 实验数量与充分性

- **实验数量**：
    - 位串任务：2种目标函数×2种权重（α=0.5,0.9），每种5个随机种子（图2）。
    - 决策树：4个环境，每个10个随机种子（图4、表1）。
    - 符号回归：多个基准（≥1维和≤3维分组），表2给出均值±标准差。
    - 额外文献对比（表1）确保使用相同评估协议（1,000种子/环境）。
- **充分性与公平性**：
    - 对比基线包括经典方法（GP+BFGS）和最新方法（Biggio 2021, Kamienny 2022），且对于缺失实现的方法，作者自行训练并标注星号。
    - 评估时所有方法使用相同种子集，避免评估偏差。
    - 位串任务中比较了非深度学习基线（BO），但BO因计算复杂度高仅适用小样本。
    - 消融实验：通过位串任务系统分析离散/连续重要性的影响（权重α），验证了联合优化优势随离散部分重要性增加而更明显。

#### 6. 论文的主要结论与发现

- **核心结论**：DisCo-DSO在所有任务上均优于解耦方法，尤其在问题复杂度高时优势更显著。
- **具体发现**：
    - 位串任务：联合优化比解耦方法更少评估次数即找到最优解，且当离散贡献权重α=0.9时优势最大。
    - 决策树策略：DisCo-DSO在所有4个环境中获得最高平均奖励，且参数数量与最佳基线相当或更少（表1）。样本效率显著高于解耦方式（图4）。
    - 符号回归：DisCo-DSO在测试集上取得最高平均奖励，且使用最少函数评估数（图6）。解耦GP方法过拟合严重（膨胀问题），联合优化避免了此问题。

#### 7. 优点

- **方法论亮点**：
    - 首次将混合MDP中的参数化动作空间思想引入符号优化，实现离散-连续联合生成。
    - 支持可变长度和位置约束，适用于树结构、表达式树等实际场景。
    - 风险寻求策略梯度聚焦高分样本，提高优化效率。
    - 决策树参数边界动态更新机制，保证采样参数在语义有效范围内。
- **实验设计亮点**：
    - 采用综合基准（合成+真实RL+SR），覆盖不同难度级别。
    - 与多种类型基线（RL、GP、BO、文献方法）公平对比。
    - 评估协议统一（如1,000种子评估），确保可比性。

#### 8. 不足与局限

- **实验局限**：
    - 仅实验了单变量决策树（univariate），未扩展到多变量（oblique）决策树。
    - 符号回归评估局限于≤3维与少量基准（Biggio只能处理≤3维），更高维场景未充分测试。
    - 算力细节缺失，难以评估方法实际资源需求。
- **方法局限**：
    - 依赖领域知识定义连续参数范围；若缺乏先验信息，需估计范围，可能影响性能。
    - 生成模型仅采用32单元单层RNN，未探索更先进架构（如Transformer的因果注意），可能限制表达力。
- **应用限制**：
    - 对于完全无结构或离散/连续高度耦合的问题，联合分布学习可能困难。
    - 当前框架未考虑大规模并行化或分布式训练的讨论。

（完）
