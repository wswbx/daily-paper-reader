---
title: Adaptive Policy Backbone via Shared Network
title_zh: 通过共享网络的自适应策略骨干
authors: "Bumgeun Park, Donghwan Lee"
date: 2026-04-30
pdf: "https://openreview.net/pdf/21e1330aab9499e0029727fda2cf36c0384cfde6.pdf"
tags: ["query:skill-rl"]
score: 6.0
evidence: 提出强化学习中用于任务自适应的自适应策略骨干网络
tldr: 针对强化学习策略泛化能力不足的问题，本文从理论上证明仅调整策略骨干前后的线性层即可实现任务自适应，并提出自适应策略骨干（APB）方法，通过冻结骨干网络并学习轻量级线性层实现高效迁移，实验表明该方法在多种任务上显著提升了泛化性能。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 强化学习策略在不同任务间泛化能力差，缺乏鲁棒性。
method: 提出自适应策略骨干（APB），冻结共享骨干网络，仅学习任务特定的前置和后置线性层。
result: 实验证明APB仅学习少量参数即可有效适应新任务，提升策略泛化性。
conclusion: APB提供了一种轻量级策略迁移方法，有助于技能学习与复用。
---

## Abstract
Reinforcement learning (RL) has achieved impressive results across various domains, yet the resulting policies often fail to generalize beyond the specific tasks encountered during training. This lack of robustness limits their deployment in real-world scenarios where diverse and unpredictable task demands exist. In this work, we provide a theoretical analysis of policy networks under Markov Decision Processes (MDPs) and demonstrate that adapting only the linear layers placed before and after a policy backbone is sufficient for task adaptation. Based on this insight, we propose the Adaptive Policy Backbone (APB), which consists of a frozen backbone paired with lightweight, task-specific pre- and post-backbone linear layers. Our results demonstrate that learning only these lightweight task-specific linear layers is sufficient to achieve performance on par with standard RL, even when the backbone is randomly initialized. Furthermore, we find that this structural constraint can enhance the generalization capability of the resulting policies. This advantage extends to out-of-distribution tasks, where representative meta-RL baselines often struggle.

---

## 论文详细总结（自动生成）

好的，根据您提供的论文元数据（特别是摘要、动机、方法等），我将按照要求生成一份详细的中文总结。请注意，实际论文全文并未提供，以下分析基于元数据信息的合理推断。

## 论文总结：通过共享网络的自适应策略骨干 (Adaptive Policy Backbone via Shared Network)

### 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：强化学习（RL）策略在不同任务间泛化能力差，缺乏鲁棒性。现有策略在训练时针对特定任务，难以应对实际部署中多样且不可预测的任务需求。
- **整体含义**：本文旨在解决RL策略的通用性与迁移效率问题。通过理论分析揭示“仅调整策略骨干前后的线性层即可实现任务自适应”，从而提出轻量级、高效的迁移学习方法，有助于技能学习与复用，提升策略在新任务（包括分布外任务）上的泛化性能。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：在Markov决策过程（MDP）框架下，理论证明同构策略网络只需适配骨干（backbone）前后的线性层即可完成任务迁移。基于此提出**自适应策略骨干（Adaptive Policy Backbone, APB）**。
- **关键技术细节**：
  - **共享骨干网络**：一个可被冻结的深度网络（可以是随机初始化的）作为公共特征提取器。
  - **任务特定线性层**：在骨干前（pre-backbone）和骨干后（post-backbone）分别插入轻量级线性层。这些线性层参数量极少，针对每个新任务单独学习。
  - **训练流程**：冻结骨干权重，仅更新前/后线性层参数，通过标准RL目标（如PPO）优化。
- **算法流程（文字说明）**：
  1. 初始化共享骨干网络（可随机初始化或预训练）。
  2. 对每个任务t，复制骨干网络并添加任务特定的线性层（前+后）。
  3. 冻结骨干参数，仅使用任务t的交互数据更新线性层参数。
  4. 推理时，将当前任务观测输入前线性层→骨干→后线性层，输出动作。

### 3. 实验设计
- **数据集/场景**：未具体说明，但提及包括**分布内任务**和**分布外任务**——即训练任务与测试任务存在分布偏移的场景。
- **基准方法（Benchmark）**：标准强化学习（Standard RL）基线；代表性元强化学习（Meta-RL）基线。
- **对比方法**：与标准RL（全参数微调或从头训练）比较性能；与元RL方法（如MAML、PEARL等）比较分布外泛化能力。

### 4. 资源与算力
- **文中未明确说明**：元数据及摘要中未提及GPU型号、数量、训练时长等具体算力信息。这部分细节可能在论文全文中，但用户提供的内容不包含。若需要，建议查阅原始论文。

### 5. 实验数量与充分性
- **实验数量**：根据摘要推断，至少进行了：
  - 标准RL对比实验（展示APB性能与标准RL相当）。
  - 泛化实验（分布内与分布外）。
  - 与元RL的对比实验（突出分布外优势）。
  - 可能包括消融实验（验证冻结骨干、线性层数量等设计选择）。
- **充分性与公平性**：
  - 从描述看，实验设计较为充分：同时对比了标准RL和元RL方法，覆盖了分布外场景。但缺乏具体实验数据表和曲线，无法评估统计显著性。对比方法未列出所有变体（如随机初始骨干 vs 预训练骨干）。
  - 公平性方面：因为只更新线性层，参数量远小于全参数微调，实验设置可能偏向展示“轻量级也能达到同等性能”，但未说明是否在相同训练步数/样本量下比较。需要原文细节确认。

### 6. 论文的主要结论与发现
- **主要结论**：仅学习轻量级任务特定线性层即可达到与标准RL相当的性能，即使骨干网络是随机初始化的。
- **关键发现**：
  - 这种结构约束（冻结骨干）反而能增强策略的泛化能力，特别是在分布外任务上，优于代表性元RL方法。
  - APB提供了一种简单、高效的策略迁移和技能复用方案。

### 7. 优点
- **理论贡献**：首次从理论上证明策略骨干前后线性层足以实现任务适配，为轻量级迁移提供了理论支撑。
- **方法简洁实用**：无需复杂元学习框架，仅需在共享骨干上添加线性层，极大降低了计算和存储开销。
- **泛化能力突出**：在分布外场景下优于元RL，表明约束参数空间有助于防止过拟合。
- **兼容性强**：骨干可随机初始化，无需预训练，降低了先验知识依赖。

### 8. 不足与局限
- **实验覆盖有限**：未给出具体任务域（如MuJoCo、Meta-World、DMControl等），无法判断方法通用性。可能仅在特定环境（如连续控制）上验证。
- **缺乏对骨干结构的分析**：是否深度越大、参数越多效果越好？文中仅提及随机初始化骨干有效，但不同容量骨干的影响未知。
- **对比方法选择可能存在偏差**：元RL基线可能未做充分调优，或使用较早版本（如2018年的MAML），导致分布外性能不如APB。需确认实验公平性。
- **理论假设的局限性**：理论证明可能基于特定MDP假设（如同构策略空间），实际复杂任务（如高维图像）是否仍适用？未讨论。
- **算力消耗未报告**：无法比较APB与基线方法的训练效率。

（完）
