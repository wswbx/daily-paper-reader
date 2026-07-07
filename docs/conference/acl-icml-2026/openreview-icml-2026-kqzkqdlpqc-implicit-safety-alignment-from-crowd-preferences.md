---
title: Implicit Safety Alignment from Crowd Preferences
title_zh: 从众包偏好中隐式安全对齐
authors: "Qian Lin, Daniel S. Brown"
date: 2026-04-30
pdf: "https://openreview.net/pdf/4634a7567acc01a1a6cdfe3d8e297057fd4dde4a.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 从众包偏好中提取技能用于强化学习迁移
tldr: 该论文关注从众包偏好中提取共享的安全标准，并迁移到下游强化学习任务。它发现直接组合奖励存在局限，因此提出安全的众包偏好强化学习框架，层次化地提取安全对齐的技能。实验表明该方法能有效正则化智能体行为并保障安全性。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 直接组合偏好学习奖励和任务奖励无法有效迁移安全标准。
method: 提出层次化框架，从众包偏好中提取安全对齐的技能并迁移。
result: 方法有效正则化智能体行为，提升安全性。
conclusion: 从众包偏好学习技能可安全迁移至下游任务。
---

## Abstract
Reinforcement Learning from Human Feedback (RLHF) can reveal implicit objectives such as safety considerations that go beyond task completion. In this work, we focus on the common safety criteria embedded in crowd preference datasets, where different users may express distinct preferences or objectives, yet follow similar safety principles. Our aim is to discover shared safety criteria from crowd preferences and then transfer them to downstream RL tasks to regularize agent behavior and enforce safety. We first show that direct reward combination—optimizing a preference-learned reward model together with downstream task rewards—has inherent limitations. Motivated by this, we propose Safe Crowd Preference-based RL, a hierarchical framework that extracts safety-aligned skills from crowd preferences and composes them via a high-level policy to safely solve downstream tasks. Experiments across safe RL environments and a preliminary LLM-style task with diverse user goals and shared safety constraints demonstrate that our approach substantially lowers safety costs without access to explicit safety rewards, while achieving task performance comparable to oracle methods trained with ground-truth safety signals.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：如何从众包偏好数据中自动提取共享的安全标准，并将其有效迁移到下游强化学习（RL）任务中，以正则化智能体行为、保障安全性，同时避免显式安全奖励的依赖。
- **研究动机**：现有的RLHF方法可以学习到隐含的偏好（如安全考虑），但直接组合偏好学习获得的奖励模型与下游任务奖励存在固有局限性（见方法部分分析）。不同用户虽有个性化目标，但往往遵循相似的安全原则，因此从众包偏好中提取共享安全技能并迁移是实现安全对齐的可行路径。
- **整体含义**：提出一种层次化框架（Safe Crowd Preference-based RL），能够从众包偏好中学习安全对齐的技能，并通过高层策略组合这些技能以安全地解决下游任务，为无需显式安全信号的安全强化学习提供了新范式。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：通过层次化框架将众包偏好中的安全约束解耦为可迁移的技能，避免直接奖励组合带来的问题（例如偏好奖励与任务奖励可能冲突、泛化能力弱）。
- **关键技术与流程**：
  1. **安全对齐技能提取**：从众包偏好数据中学习一组隐式表示的安全技能（skill），这些技能编码了共享的安全准则（如避免碰撞、禁止危险动作）。
  2. **高层策略组合**：在下游任务中，一个高层策略根据当前状态选择或组合这些安全技能，以同时满足任务目标和安全约束。
  3. **训练方式**：整体采用RL框架，安全技能作为底层策略，高层策略学习如何调度技能。不需要显式安全奖励函数，仅依赖任务奖励和从偏好中习得的技能。
- **公式/算法说明**：论文隐含了基于最大熵、变分推断或对抗训练等技巧实现技能解耦，具体公式未在摘要中详述，但可推断其框架类似于分层强化学习（HRL）中的技能发现。

## 3. 实验设计：数据集/场景、Benchmark、对比方法

- **数据集/场景**：
  - 安全RL环境（如导航、机器人控制等标准Safe RL benchmark）。
  - 一个初步的LLM风格任务，包含多样化用户目标和共享安全约束（可能类似对话安全）。
- **Benchmark**：未明确列出具体环境名称，但提及“safe RL environments”，推测可能为Safety Gym、Mujoco约束版本等常见基准。
- **对比方法**：
  - 直接奖励组合方法（即优化偏好学习奖励模型+下游任务奖励）。
  - 使用显式安全奖励训练的oracle方法（作为上界）。
  - 可能还包括其他迁移基线（如直接微调、多任务学习等，但摘要未详述）。

## 4. 资源与算力

- **文中未明确说明**：论文摘要和元数据中没有提及使用的GPU型号、数量或训练时长。仅能从实验结果推断进行了计算实验，但具体算力信息缺失。

## 5. 实验数量与充分性

- **实验数量**：至少包含两类环境（Safe RL + LLM风格任务），每组环境可能设有多组不同user目标/安全约束的配置。摘要未列出消融实验数量，但框架本身包含技能提取、高层策略等组件，理论上应有消融研究（例如去掉技能迁移 vs. 直接奖励组合）。
- **充分性与公平性**：
  - **优点**：对比了两类方法（直接组合和oracle），且实验结果展示了安全成本显著降低、任务性能接近oracle，说明验证较为全面。
  - **不足**：未详细说明统计显著性、随机种子数、任务多样性等；LLM风格任务仅称为“preliminary”，可能覆盖不充分。整体而言，实验设计具有合理性，但细节披露不足限制了对充分性的评判。

## 6. 论文的主要结论与发现

- 直接奖励组合在迁移安全标准时存在固有局限，而提出的层次化框架能够有效从众包偏好中提取安全对齐的技能。
- 该方法在不使用显式安全奖励的情况下，显著降低了安全成本（例如违规次数、碰撞率等），同时任务性能与使用真实安全信号的oracle方法相当。
- 证明众包偏好中蕴含的共享安全标准可以跨用户和任务迁移，为安全RL提供了一种实用、标签高效的方法。

## 7. 优点

- **方法创新**：将众包偏好中的安全知识抽象为可迁移技能，避免了传统奖励工程或显式安全性标注的负担。
- **实用性强**：适用于真实场景中众包数据易获取但安全奖励难以定义的情况。
- **性能优秀**：实验证明在安全性和任务完成度之间取得良好平衡，接近有监督oracle方法。
- **框架通用**：不仅适用于标准Safe RL，还初步拓展到LLM安全对齐任务，展示跨领域潜力。

## 8. 不足与局限

- **实验覆盖有限**：仅提及一个LLM风格预实验，缺乏更大规模或更多样化任务的验证（如真实自动驾驶、机器人操作等）。
- **算力与复现信息缺失**：未报告训练成本，不利于复现和评估实际部署可行性。
- **假设依赖**：假设众包偏好中存在共享安全标准，若用户偏好高度冲突或缺乏一致性，方法效果可能下降。
- **安全性保证边界**：技能提取可能遗漏某些长尾风险，无法提供形式化安全保证。
- **理论基础**：未深入分析技能的可迁移性边界或收敛性，理论分析可能不够充分。

（完）
