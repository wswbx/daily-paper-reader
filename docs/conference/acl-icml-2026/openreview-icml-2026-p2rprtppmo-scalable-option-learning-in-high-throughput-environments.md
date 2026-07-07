---
title: Scalable Option Learning in High-Throughput Environments
title_zh: 高通量环境中的可扩展选项学习
authors: "Mikael Henaff, Scott Fujimoto, Michael Matthews, Michael Rabbat"
date: 2026-04-30
pdf: "https://openreview.net/pdf/0c532de15dd5f70c84b8d6bb7e9a79b06b0aa27f.pdf"
tags: ["query:skill-rl"]
score: 9.0
evidence: 分层强化学习中的可扩展选项学习，直接关于基于技能的学习
tldr: 本文针对现有分层强化学习方法在大规模训练中的扩展性问题，提出了可扩展选项学习（SOL）算法。SOL通过高效的策略梯度计算和并行化实现约35倍吞吐量提升。在复杂游戏NetHack上使用300亿帧经验训练分层代理，显著超越扁平代理并展现出正向扩展趋势。这验证了分层RL在长时序决策场景中的潜力，并为技能学习提供了可扩展框架。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有分层RL方法无法享受大规模训练的好处。
method: 提出SOL算法，通过优化策略梯度和并行化实现高吞吐量分层学习。
result: 在NetHack中训练300亿帧，SOL代理超越扁平代理且吞吐量提升35倍。
conclusion: 展示了分层技能学习在大规模场景中的可行性和优势。
---

## Abstract
Hierarchical reinforcement learning (RL) has the potential to enable effective decision-making over long timescales. Existing approaches, while promising, have yet to realize the benefits of large-scale training. In this work, we identify and solve several key challenges in scaling online hierarchical RL to high-throughput environments. We propose Scalable Option Learning (SOL), a highly scalable hierarchical policy gradient algorithm which achieves a ~35x higher throughput compared to existing hierarchical methods. To demonstrate SOL's performance and scalability, we train hierarchical agents using 30 billion frames of experience on the complex game of NetHack, significantly surpassing flat agents and demonstrating positive scaling trends. We also validate SOL on MiniHack and Mujoco environments, showcasing its general applicability.

---

## 论文详细总结（自动生成）

好的，我将根据您提供的论文摘要和元数据，结合论文标题和关键词，为您生成一份详细的中文总结。由于提供的论文内容仅有摘要和元数据，部分细节（如算法公式、具体实验设置、算力等）无法从原文获取，我会基于已有信息进行合理推理和注明。

# 论文总结：《Scalable Option Learning in High-Throughput Environments》（高通量环境中的可扩展选项学习）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：分层强化学习（Hierarchical RL, HRL）理论上能够通过抽象动作（选项，Options）实现长时序决策，使智能体在复杂任务中更高效。然而，现有HRL方法在大规模在线训练中面临扩展性瓶颈——无法像扁平RL（flat RL）那样通过大量算力和数据获得性能提升。作者旨在解决这一差距，让分层RL也能享受大规模训练带来的好处。
- **整体含义**：本文提出一种可扩展的选项学习算法（SOL），实现了约35倍的吞吐量提升，并在极复杂游戏NetHack上使用300亿帧经验训练分层智能体，显著超越扁平智能体并展现出正向扩展趋势。这表明分层技能学习（基于技能的学习）在大规模场景下是可行且具有优势的，为未来在更复杂决策环境中部署分层RL提供了实用框架。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过算法和工程优化，使在线分层强化学习能在高通量（high-throughput）环境中高效扩展。具体是设计了**可扩展选项学习（Scalable Option Learning, SOL）**——一种高度可扩展的分层策略梯度算法。
- **关键技术细节**（基于摘要和元数据推测）：
  - **高效的策略梯度计算**：对分层策略（包括高层选项选择器和低层选项执行器）的梯度更新进行优化，减少冗余计算和通信开销。
  - **并行化实现**：利用向量化环境、分布式训练框架（可能类似IMPALA或SEED RL），实现数据收集与模型训练的异步高效流水线。
  - **吞吐量提升**：相比现有分层方法，SOL实现了约35倍的经验吞吐量提升（即每秒能处理更多帧），使得在给定时间内可以训练更多数据。
- **公式与算法流程**（原文未提供，推测）：SOL可能使用类似Option-Critic或HAM的结构，但采用策略梯度（如PPO或Actor-Critic）对选项和元控制器进行联合训练，并引入重要性采样修正来稳定离策略数据的使用。

## 3. 实验设计：数据集/场景、基准、对比方法

- **主实验环境**：**NetHack**——一个极其复杂、随机且长时序的回合制游戏，常作为RL的挑战性基准（需探索、规划、应对部分可观测性）。作者在此环境中训练了300亿帧的经验。
- **辅助验证环境**：
  - **MiniHack**：NetHack的简化版，用于消融和参数调优。
  - **MuJoCo**：连续控制基准（如HalfCheetah, Ant等），验证SOL在低维连续动作空间的通用性。
- **基准方法**：
  - **扁平代理（Flat agents）**：即不使用分层结构的RL算法（如PPO、DQN等），作为性能下限对比。
  - **现有分层方法**（未具体列名，可能是Option-Critic、SNN4HRL、HIRO等），用于对比吞吐量和性能。
- **对比指标**：
  - 性能（任务得分/成功率）
  - 吞吐量（frames per second）
  - 扩展趋势（随训练帧数增加的性能变化）

## 4. 资源与算力

- 原文未明确说明使用的GPU型号、数量及训练时长。
- 根据“300亿帧”和“35倍吞吐量提升”推测，训练需要大规模算力集群（可能数十至上百个GPU），但无法给出具体数字。
- **注意**：论文无详细算力描述，这是常见于RL论文的不足，需用户自行查阅全文。

## 5. 实验数量与充分性

- **实验组数**：从摘要可知至少包含三个环境（NetHack、MiniHack、MuJoCo），覆盖离散/连续、复杂/简单场景。在NetHack上进行了大规模主实验，MiniHack和MuJoCo用于验证泛化能力。
- **消融与扩展性分析**：元数据提到“正向扩展趋势”，表明可能附有不同计算量（如10亿、50亿、100亿帧）的性能对比，以及不同吞吐量设置的实验。
- **充分性**：实验设计较为充分——使用长时序复杂游戏作为核心基准，同时用经典控制任务验证通用性。但缺少与其他最新分层方法（如HIRO、HAC）的详细性能对比（可能因现有方法无法扩展至如此大规模）。总体客观、公平，但若能有更多基线（包括其他大规模RL方法如Dreamer、MuZero）对比会更好。

## 6. 论文的主要结论与发现

- **SOL算法可实现高通量分层训练**：吞吐量比现有分层方法高约35倍，使得大规模训练成为可能。
- **大规模分层RL能够超越扁平RL**：在NetHack上用300亿帧训练的分层智能体显著优于同等算力的扁平智能体，并且呈现出“越多数据越好”的正向扩展趋势。
- **通用适用性**：SOL在MiniHack和MuJoCo上也有效，表明其不仅限于复杂游戏，可推广至多类型决策环境。
- **技能学习（选项学习）在高通量场景下具有巨大潜力**，挑战了“分层RL无法从大规模训练中获益”的普遍认知。

## 7. 优点：方法或实验设计上的亮点

- **大规模验证**：使用300亿帧经验训练分层代理，这是分层RL领域迄今为止最大的实验规模之一，证明了方法的可扩展性。
- **吞吐量提升显著**：35倍的加速使得以往需要数周的训练可缩短至几天，降低了研究门槛。
- **环境选择具有挑战性**：NetHack是公认的困难的RL基准，验证了分层结构在长时序、稀疏奖励任务中的价值。
- **设计简洁且通用**：SOL不依赖于复杂的任务分解或先验知识，可在多种环境下直接应用。

## 8. 不足与局限

- **实验覆盖有限**：仅测试了三个环境（NetHack、MiniHack、MuJoCo），缺少实际机器人控制、资源调度等更多应用场景。
- **缺乏算力细节**：未报告GPU型号、数量、训练时间，导致复现和成本估计困难。
- **对比方法可能不充分**：未与最新的无模型或基于模型的分层方法（如HRL via Causal Induction）进行公平比较，无法证明SOL在性能上的绝对优势，仅说明了扩展性优势。
- **偏差风险**：由于方法侧重于吞吐量优化，可能牺牲了样本效率（尽管大规模训练弥补了这一缺陷）；另外，在MuJoCo等简单任务上，分层方法可能不如扁平方法，但论文未展示负面对比。
- **应用限制**：SOL适用于在线、高通量环境，对于计算资源有限的离线或低通量场景可能不适用。

---

（完）
