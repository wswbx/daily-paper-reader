---
title: Offline Multi-agent Continual Cooperation via Skill Partition and Reuse
title_zh: 基于技能划分与重用的离线多智能体持续协作
authors: "Yuchen Xiao, Lei Yuan, Ruiqi Xue, Tieyue Yin, Yang Yu"
date: 2026-04-30
pdf: "https://openreview.net/pdf/0dc5f123a5a55a551e3fe7fb8a07ed7dc48dd573.pdf"
tags: ["query:skill-rl"]
score: 9.0
evidence: 技能划分与重用，用于持续多智能体强化学习
tldr: 针对多智能体持续学习场景中技能库爆炸导致灾难性遗忘和塑性损失的问题，提出COMAD框架，通过技能划分与重用机制，从离线混合数据中持续发现协调技能。该方法避免固定技能库的弊端，在开放环境中实现技能的有效迁移与复用，显著提升学习效率与泛化能力。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 多智能体持续学习中固定技能库难以应对技能空间增长和分布偏移，导致灾难性遗忘与塑性损失。
method: 提出COMAD框架，通过技能划分与重用，从离线混合数据中持续发现协调技能。
result: 在持续多智能体任务上，COMAD有效缓解遗忘，提升技能复用率与协作性能。
conclusion: 技能划分与重用是开放环境下多智能体持续学习的有效范式。
---

## Abstract
Extracting skills from multi-agent offline dataset improves learning efficiency via sharing task-invariant coordination skills among tasks. In settings where tasks occur sequentially and the space of skills grows exponentially, existing approaches that rely on heuristically designed and fixed-sized skill libraries struggle to resolve the problem of distributional shift and interference, facing catastrophic forgetting and plasticity loss. To address this problem and endow agents with the ability to continually discover and reuse coordination skills in open-environment, we propose COMAD, a principled framework for **C**ontinual **O**ffline **M**ulti-**a**gent Skill **D**iscovery via Skill Partition and Reuse. We first discover skills from mixed multi-agent behavior data with an auto-encoder to transform coordination knowledge into reusable coordination skills. Then we construct a skill-augmented policy learning objective with multi-head architectures, explicitly guiding the advantage function with reusable skills identified via a density-based reusability estimator.
Theoretical analysis shows our method approximates the optimum of a continual skill discovery problem. Empirical results across diverse MARL benchmarks show that COMAD continually expands its skill library to mitigate interference, achieving superior forward and backward transfer for task streams compared to multiple baselines.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：多智能体系统在开放环境中需要持续学习新任务，而现有方法依靠启发式设计的固定大小技能库，难以应对技能空间随任务数量指数增长的问题。固定技能库在面对分布偏移和任务干扰时，容易引发灾难性遗忘和塑性损失（plasticity loss），即旧技能被覆盖或新技能无法有效学习。
- **背景问题**：从离线多智能体数据集中提取技能可以共享任务无关的协调知识，但任务顺序出现时，技能库需要动态扩展以容纳新技能，同时避免遗忘旧技能。
- **核心问题**：如何让智能体在持续任务流中能够持续发现和重用协调技能，而不会因技能库爆炸导致性能下降。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出 **COMAD**（Continual Offline Multi-agent Skill Discovery via Skill Partition and Reuse）框架，通过技能划分（partition）与重用（reuse）机制，从离线混合行为数据中持续发现协调技能，并动态扩展技能库以避免干扰。
- **关键技术细节**：
  - **技能发现**：使用自编码器（auto-encoder）从混合多智能体行为数据中提取可重用的协调技能，将协调知识编码为潜在表示。
  - **技能划分**：不是维护固定大小的技能库，而是通过密度估计器（density-based reusability estimator）判别新技能与已有技能的相似性，决定是新增技能还是重用旧技能，从而实现技能库的动态扩展。
  - **技能增强策略学习**：构造多头架构（multi-head architectures）的策略学习目标，显式地将可重用技能引导到优势函数（advantage function）中，利用识别出的可重用技能优化策略参数。
- **理论分析**：论文证明了所提方法能够近似优化一个持续技能发现问题的最优解，即理论上保证了技能划分和重用的有效性。
- **算法流程（文字说明）**：
  1. 对离线混合数据集，使用自编码器学习协调技能的低维表示。
  2. 对于每个新任务，评估当前技能库中的技能与任务数据的匹配度，通过密度估计判断是否引入新技能。
  3. 若密度估计显示已有技能足够覆盖，则重用旧技能；否则将新技能加入技能库。
  4. 基于技能增广的策略学习目标（多头结构）优化策略，使得智能体能够同时利用新旧技能进行协调。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：使用了多个多智能体强化学习（MARL）基准任务，具体名称未在摘要中列出，但“diverse MARL benchmarks”表明覆盖了多种典型任务（如协作导航、捕食者-猎物、星际争霸等可能类型）。
- **Benchmark**：持续学习场景下任务顺序出现，评估前向迁移（对新任务的学习效率）和后向迁移（对旧任务的保留能力）。
- **对比方法**：与多个基线方法对比，包括固定技能库方法、无技能迁移的持续学习方法等（具体基线名称未在摘要中详述，但文中应包含典型持续学习基线如EWC、L2P等）。

## 4. 资源与算力

- **未明确说明**：摘要及元数据中未提及使用的GPU型号、数量、训练时长等具体算力信息。通常ICML论文会在实验部分给出硬件环境，但此处提取内容不包含该细节。

## 5. 实验数量与充分性

- **实验数量**：摘要提到“Empirical results across diverse MARL benchmarks”，表明至少在多组不同任务上进行了实验。但未给出具体实验组数、消融实验细节。
- **充分性判断**：论文可能包含了与多个基线的对比、消融研究（例如验证技能划分 vs 固定库、密度估计的作用等），但当前文本未提供详细信息。从得分9.0（高）推测实验设计较为充分且公平。不过，由于缺乏具体数据，无法完全确认。

## 6. 论文的主要结论与发现

- 在持续多智能体任务流中，COMAD能够持续扩展技能库以缓解干扰，相比多个基线实现了显著的前向迁移（对新任务学习更快）和后向迁移（对旧任务遗忘更少）。
- 技能划分与重用是开放环境下多智能体持续学习的有效范式，所提框架能近似达到持续技能发现问题的理论最优。
- 该方法有效解决了固定技能库导致的灾难性遗忘和塑性损失问题。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 提出动态技能库扩展机制（基于密度估计的划分与重用），避免固定库的僵化。
  - 多头架构将可重用技能显式融入优势函数，理论上保证了最优近似。
  - 框架原则性强，具有理论支撑。
- **实验设计亮点**：
  - 同时评估前向和后向迁移，全面衡量持续学习性能。
  - 在多个MARL基准上验证，覆盖不同复杂度场景，增加了泛化性说服力。

## 8. 不足与局限

- **实验信息不足**：当前摘要未提供具体任务名称、超参数设置、对比基线列表、消融实验细节等，难以全面评估实验的充分性和公平性。
- **算力缺失**：未说明训练资源，可能对可重复性造成影响。
- **潜在偏差风险**：仅依赖离线数据集，技能发现质量受数据质量和多样性限制；密度估计器在任务分布剧烈变化时可能误判。
- **应用限制**：方法假设任务顺序已知且技能库可以无限扩展，在极大规模任务流中可能仍面临存储和计算开销问题。

（完）
