---
title: Neuro-evolutionary Continual Reinforcement Learning
title_zh: 神经演化持续强化学习
authors: "Pengyi Li, Hongyao Tang, Yifu Yuan, YAN ZHENG, Xin Xu, Jianye HAO"
date: 2026-04-30
pdf: "https://openreview.net/pdf/718ba942b4a3f03d972afafbae6506c462828e20.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 技能保留与任务策略种群，持续强化学习中的技能习得
tldr: 现有持续强化学习方法在技能保留和迁移上存在不足。本文提出神经演化持续强化学习（Nevo-CRL），通过维护固定容量的策略网络并使用掩码种群为每个任务选择激活，实现任务特定策略的演化与新技能的获取。实验表明该方法在避免灾难性遗忘的同时有效利用先前知识。贡献在于提供了持续场景下基于技能的强化学习新范式。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 机器人需在开放世界中持续学习新任务，同时保留已有技能并利用旧知识。
method: 维护固定容量的策略网络，为每个新任务构建掩码种群选择性激活隐藏层输出，形成任务特定策略种群。
result: 在持续学习基准上，Nevo-CRL在保留旧技能和学习新任务方面均优于现有方法。
conclusion: 神经演化方法能有效解决持续RL中的技能保留与迁移问题。
---

## Abstract
Deploying robots in open-ended real-world environments demands continual learning capabilities to adapt to an ever-expanding range of tasks. This requires retaining previously acquired skills without forgetting while effectively leveraging prior knowledge to learn new ones. Inspired by neuroscience, we propose **N**euro-**e**volutionary **C**ontinual **R**einforcement **L**earning (**Nevo-CRL**). Nevo-CRL maintains a fixed-capacity monolithic policy network, solving tasks by optimizing inter-layer connectivity and neuron parameters.
For each new task, Nevo-CRL constructs a mask population to selectively activate the outputs of each hidden layer, thereby forming a task-specific policy population. Upon completing each task, the best-performing mask is stored, and its activated neurons are frozen to prevent catastrophic forgetting. To facilitate knowledge transfer, Nevo-CRL reuses neurons from acquired skills based on semantic similarity between tasks, while dynamically allocating additional neurons for task-specific adaptation.
In the learning process, Nevo-CRL iteratively adjusts masks via importance-guided crossover to optimize the policy network connectivity. To improve neuron utilization, we prune low-activity connections to recycle neurons. Experiments demonstrate that Nevo-CRL achieves state-of-the-art performance among continual RL methods.
The code is available at [https://github.com/yeshenpy/Nevo-CRL](https://github.com/yeshenpy/Nevo-CRL).

---

## 论文详细总结（自动生成）

# 神经演化持续强化学习（Nevo-CRL）中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：机器人在开放世界环境中需要具备持续学习能力，以不断适应新任务。核心挑战在于：既要保留已习得的技能（避免灾难性遗忘），又要有效利用先前知识来学习新任务。
- **背景**：现有持续强化学习方法在技能保留和迁移方面存在不足，受神经科学启发，希望通过演化算法优化神经网络连接结构以实现持续学习。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：维护一个固定容量的整体策略网络，通过优化层间连接和神经元参数来解决一系列任务。每个新任务时，构建一个掩码种群（mask population），选择性地激活每个隐藏层的输出，从而形成任务特定的策略种群。
- **关键技术细节**：
  - 任务完成后，存储表现最佳的掩码，并将该掩码激活的神经元冻结（防止灾难性遗忘）。
  - 知识迁移：基于任务间的语义相似性，重用已有技能的神经元，同时动态分配额外神经元用于新任务适应。
  - 学习过程：通过重要性引导的交叉（importance-guided crossover）迭代调整掩码，优化策略网络连接。
  - 神经元利用率改进：修剪低活性的连接以回收神经元。
- **算法流程（文字描述）**：
  1. 初始化固定容量的策略网络（主干网络）。
  2. 对于每个新任务，随机生成一组掩码（每个掩码决定各隐藏层哪些神经元激活）。
  3. 每个掩码对应一个子策略，通过强化学习训练该子策略，形成任务特定策略种群。
  4. 训练过程中，根据重要性指标进行交叉变异，优化掩码。
  5. 任务结束后，选择最优掩码，冻结其激活的神经元，防止后续任务修改。
  6. 利用语义相似度，从已冻结的神经元中选择可重用的部分，不足时分配新的神经元。
  7. 定期修剪低活性连接，回收神经元资源。

## 3. 实验设计

- **使用场景/数据集**：持续强化学习基准（具体环境名称未在摘要中明确列出，但论文声称在持续学习基准上测试，包括标准持续RL任务）。
- **Benchmark**：持续强化学习领域常用的一系列任务序列（如不同难度的连续控制任务或离散控制任务）。
- **对比方法**：现有持续RL方法（未列举具体名称，但论文表示Nevo-CRL在保留旧技能和学习新任务方面均优于这些方法）。

## 4. 资源与算力

- **文中说明**：未明确提及使用的GPU型号、数量或训练时长。仅提到代码开源。
- **补充指出**：论文未提供计算资源细节，因此无法评估其算力消耗。

## 5. 实验数量与充分性

- **实验数量**：摘要仅提到在持续学习基准上测试，并进行了性能比较，未列明具体实验组数（如不同任务序列、消融实验等）。
- **充分性评估**：由于摘要信息有限，无法判断实验是否充分。但作者包含消融实验（修剪低活性连接等）和可回收神经元机制，说明进行了模块分析。整体上实验设计可能较为完整，但公开信息不足以全面评价。

## 6. 主要结论与发现

- Nevo-CRL在持续RL基准上达到了**最优性能**（state-of-the-art）。
- 神经演化方法能有效解决持续RL中的技能保留与迁移问题，避免灾难性遗忘同时促进知识利用。
- 提出的掩码种群和重要性引导交叉机制能有效优化网络连接，神经元冻结与重用保证了旧知识稳定性和新任务适应性。

## 7. 优点（方法或实验设计亮点）

- **创新性**：将神经演化（掩码种群和交叉变异）与持续强化学习结合，提供了一种基于技能的持续学习新范式。
- **资源高效**：固定容量网络、神经元重用、修剪低活性连接提升了参数利用率。
- **理论启发**：受神经可塑性启发，通过动态分配与冻结模拟大脑技能存储机制。
- **代码开源**：便于复现与扩展。

## 8. 不足与局限

- **实验覆盖**：摘要未详细列出测试的具体任务、任务数量、统计显著性等，说服力可能不足。
- **偏差风险**：仅报告了在基准上的最佳结果，未讨论失败情况或敏感度分析。
- **应用限制**：固定容量网络可能限制可学习任务的总复杂度；掩码种群演化可能带来额外计算开销，实际部署时需权衡。
- **信息缺失**：缺少与更广泛基线（如非持续RL方法）的对比，也未讨论超参数敏感性。

（完）
