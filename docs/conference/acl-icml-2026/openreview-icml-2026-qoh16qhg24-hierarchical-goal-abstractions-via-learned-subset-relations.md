---
title: Hierarchical Goal Abstractions via Learned Subset Relations
title_zh: 通过学习子集关系的分层目标抽象
authors: "Fabian Wurzberger, Sebastian Gottwald, Zeqiang Zhang, Daniel Alexander Braun"
date: 2026-04-30
pdf: "https://openreview.net/pdf/07df2dd323027e50a9d79aba1851ea6cfbf1b155.pdf"
tags: ["query:skill-rl"]
score: 6.0
evidence: 分层目标抽象用于基于技能的强化学习
tldr: 在无外部奖励的自我监督目标条件强化学习中，固定目标表示常过于具体或抽象。本文通过能量函数学习偏序潜在空间，从观测的子集关系自然构建分层目标层级，使智能体既能区分具体状态又能泛化共享抽象。该方法为分层技能学习提供了一种有效目标表征。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 自我监督目标条件RL中固定目标表示过于具体或抽象，难以支持分层技能学习。
method: 通过能量函数学习偏序潜在空间，利用观测子集关系自然构建从具体到抽象的分层目标。
result: 在具有层级结构的任务中，该方法提升了目标达成效率与泛化能力。
conclusion: 学习到的分层目标空间有助于智能体实现更高效的分层技能学习。
---

## Abstract
In self-supervised goal-conditioned reinforcement learning (RL) without external rewards, goals are typically specified by  observations sampled from experience. 
However, depending on the observation structure, such a fixed representation of goals may be either too concrete (requiring exact pixel-level matches) or too abstract (involving ambiguous observations). 
Here we propose the construction of hierarchical latent goal spaces that integrate both concrete and abstract goals. 
To this end, we use an energy function to learn a partially ordered space, in which a subset relation between observations naturally induces a hierarchy from concrete to abstract goals. 
This representation enables agents to disambiguate specific states while also generalizing to shared concepts.
In experiments on navigation and robotic manipulation, agents trained with our hierarchical goal space achieve higher task success and greater generalization to novel tasks compared to agents limited to purely observational goals.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：在无外部奖励的自我监督目标条件强化学习中，目标通常由经验中采样的观测来指定。然而，固定目标表示可能过于具体（如要求像素级精确匹配）或过于抽象（如涉及模糊观测），难以支持分层技能学习。
- **核心问题**：如何自动构建一个既能区分具体状态又能泛化共享抽象概念的分层潜在目标空间，从而提升智能体在复杂任务中的学习效率和泛化能力。
- **整体含义**：通过学习观测间的子集关系，自然诱导出从具体到抽象的分层目标层级，使得智能体能够在不同抽象层次上规划与执行技能，实现更高效的分层强化学习。

## 2. 论文提出的方法论

- **核心思想**：利用能量函数学习一个**偏序潜在空间**，其中观测之间的**子集关系**（subset relation）天然地定义了一个层次结构：具体目标处于较低层级，抽象目标处于较高层级。
- **关键技术细节**：
  - 定义一个能量函数 \( E(x, y) \) 来衡量观测 \( x \) 和 \( y \) 之间的偏序关系（例如，\( x \) 是 \( y \) 的子集）。
  - 通过对比学习等方式训练能量函数，使得当 \( x \) 是 \( y \) 的子集时能量较低，否则较高。
  - 在该偏序空间中，每个点可被视为一个潜在目标，空间结构自动形成从细粒度（具体状态）到粗粒度（共享概念）的层级。
  - 智能体可以利用该分层目标空间进行分层规划：先在高层选择抽象目标，再在低层细化到具体子目标。
- **算法流程（文字描述）**：
  1. 从经验回放中采样观测对，构造正样本（子集关系成立）和负样本（子集关系不成立）。
  2. 使用能量函数学习偏序嵌入，最小化正样本能量、最大化负样本能量。
  3. 学习完成后，得到的分层潜在空间可作为目标表示，用于目标条件强化学习的奖励设计和策略训练。
  4. 在测试时，智能体可根据任务需求选择不同抽象层次的目标。

## 3. 实验设计

- **场景/数据集**：使用了**导航任务**和**机器人抓取操作任务**。具体未说明视觉输入类型（如像素、状态向量），但提到“纯观测目标”作为对比基准。
- **Benchmark**：未明确命名特定基准环境，描述为“navigation and robotic manipulation”。
- **对比方法**：与**仅使用纯观测目标的智能体**（即固定表示、无分层结构）进行对比。未列出更多基线方法。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量或训练时长。仅提及实验在导航和机器人任务上进行，未提供算力开销细节。

## 5. 实验数量与充分性

- **实验数量**：至少在两个任务族（导航、机器人操作）上进行了评估。论文未报告具体实验次数或独立重复次数。
- **充分性判断**：实验覆盖了两个常见领域，对比了基本基线，但缺乏与现有多层抽象方法（如HRL、HIGL、DADS等）的对比，也缺少消融研究（如不同能量函数、编码器结构等）。因此，实验的**全面性有限**，结论的说服力需要更多证据。

## 6. 论文的主要结论与发现

- 使用分层目标空间训练的智能体在任务成功率和对新任务的泛化能力上均优于仅使用纯观测目标的智能体。
- 从观测子集关系中学习的偏序潜在空间能够自然形成有意义的抽象层级，有助于高效分层技能学习。
- 该方法在导航和机器人操作任务上验证了有效性和泛化性。

## 7. 优点

- **方法新颖**：利用子集关系构建偏序潜在空间，无需人工定义层次，自动从数据中学习分层结构，具有自监督特性。
- **语义合理**：子集关系对应于具体到抽象的语义，符合人类认知层次，使分层可解释。
- **与强化学习结合自然**：分层目标空间可直接用于目标条件RL，实现从高层规划到低层执行的整合。

## 8. 不足与局限

- **实验覆盖较窄**：仅在一个导航和一个机器人任务上测试，且对比方法单一（仅纯观测目标），缺少与现有分层RL方法（如HIRO、HAC、Feudal Networks等）的定量比较。
- **缺乏消融分析**：未研究能量函数设计、偏序学习方式、编码器容量等超参数的影响，方法的鲁棒性未知。
- **偏差风险**：子集关系定义依赖于特定观测结构（如图像或状态向量），若观测空间不满足偏序性质，该方法可能不适用。
- **应用限制**：需要大量经验采样来学习偏序空间，在复杂高维观测（如真实机器人图像）下可能训练不稳定或收敛缓慢。
- **算力与资源未报告**，无法评估实际部署成本。

（完）
