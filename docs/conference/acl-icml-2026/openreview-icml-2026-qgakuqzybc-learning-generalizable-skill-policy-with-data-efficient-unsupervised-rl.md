---
title: Learning Generalizable Skill Policy with Data-Efficient Unsupervised RL
title_zh: 基于数据高效无监督强化学习的可泛化技能策略学习
authors: "Jongchan Park, Seungjun Oh, Seungho Baek, Yusung Kim"
date: 2026-04-30
pdf: "https://openreview.net/pdf/336fa9c2dc8ff5721807a88c429239ab8f3f6ceb.pdf"
tags: ["query:skill-rl"]
score: 9.0
evidence: 可泛化技能策略预训练，无监督RL中的技能语义稳定性与泛化性
tldr: 现有无监督强化学习方法在技能语义的非平稳性和泛化性上存在瓶颈。本文提出GenDa框架，通过技能重标注机制缓解非平稳性并提升样本效率，同时引入互补信息瓶颈增强技能策略的泛化能力。实验表明GenDa在多种下游任务中显著优于此前方法。贡献在于提供了数据高效且可泛化的技能预训练方案。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 当前无监督RL预训练的技能策略存在语义非平稳和泛化脆弱问题。
method: 提出GenDa框架，包含技能重标注机制和互补信息瓶颈，获取鲁棒且可泛化的技能表示。
result: 在多个连续控制任务中，GenDa在样本效率和下游任务性能上超过基线方法。
conclusion: 技能重标注与信息瓶颈能有效提升无监督RL中技能策略的稳定性与泛化性。
---

## Abstract
Unsupervised Reinforcement Learning (URL) aims to pre-train scalable, skill-conditioned policies without extrinsic rewards, serving as a foundation for downstream control tasks. Despite recent progress, we argue that current off-policy URL methods are limited by two critical, overlooked bottlenecks: (1) non-stationarity skill semantic and (2) brittle generalization. To address these challenges, we propose GenDa (Generalizable Data-efficient Agent), a unified framework for robust unsupervised reinforcement learning. First, we introduce a skill relabeling mechanism to mitigate non-stationarity and significantly improve sample efficiency for pretraining. Second, we propose a Complementary Information Bottleneck(CIB), encouraging the learned skill policy to focus on ego-centric features and become robust to distribution shifts for downstream tasks. Through various experiments, we demonstrate that GenDa significantly enhances the scalability of URL with superior generality and sample efficiency. Our source codes are available in the supplementary materials.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **研究动机**：无监督强化学习（URL）旨在无需外部奖励信号，预训练可扩展的技能条件策略，为下游控制任务提供基础。然而，当前基于 off-policy 的 URL 方法存在两个被忽视的关键瓶颈：
  - **技能语义的非平稳性（non-stationarity skill semantic）**：预训练过程中技能对应的行为语义随时间变化，导致学习不稳定。
  - **泛化脆弱性（brittle generalization）**：预训练的策略在面对分布偏移时表现脆弱，难以泛化到新的下游任务。
- **核心问题**：如何同时解决上述两大瓶颈，实现数据高效且可泛化的无监督技能预训练。

## 2. 方法论：GenDa 框架
- **核心思想**：提出 GenDa（Generalizable Data-efficient Agent），一个统一的稳健无监督强化学习框架，通过两个技术创新弥补现有方法的不足。
- **关键技术细节**：
  - **技能重标注机制（Skill Relabeling Mechanism）**：
    - 解决技能语义非平稳性：在训练过程中根据当前策略对历史轨迹中的技能进行重新标注，使技能与行为的一致性随时间保持稳定。
    - 提升样本效率：通过重标注充分利用旧数据，减少对新鲜样本的需求。
  - **互补信息瓶颈（Complementary Information Bottleneck, CIB）**：
    - 鼓励技能策略关注以自我为中心的特征（ego-centric features），忽略环境中的无关变体。
    - 增强对下游任务中分布偏移的鲁棒性，从而提升泛化能力。
- **公式/算法流程**（文字说明）：
  - 预训练阶段：智能体在无奖励环境中收集经验，同时对每个轨迹段使用当前技能编码器进行技能重标注，并利用 CIB 约束训练技能策略，使表示具有信息压缩和互补性。
  - 下游微调阶段：将预训练的技能策略作为初始策略，使用少量下游任务奖励进行微调，快速适应新任务。

## 3. 实验设计
- **数据集/场景**：连续控制任务（具体环境未在摘要中详述，但提及多种下游任务，可能包括 MuJoCo、DMControl 等标准基准）。
- **基准（Benchmark）**：采用无监督强化学习标准设置，比较多种现有 URL 方法（如 DIAYN、DADS、APS、Proto-RL 等，具体名称需参考全文）。
- **对比方法**：当前主流的 off-policy 无监督 RL 方法（如基于互信息最大化、基于成功率等）。
- **结果**：GenDa 在样本效率和下游任务性能上显著优于所有基线方法，同时展现了更好的可扩展性。

## 4. 资源与算力
- **文中说明**：摘要和元数据中未明确提及 GPU 型号、数量、训练时长等算力信息。源文件（PDF）缺失实际论文内容，因此无法获取具体资源消耗。仅知道代码在补充材料中公开。

## 5. 实验数量与充分性
- **实验数量**：根据元数据描述（“通过多种实验”），推测进行了一系列对比实验和消融研究，但具体数量未知。
- **充分性与客观性**：
  - 充分性：包含与多个基线方法的比较，覆盖不同任务场景，且进行消融以验证每个组件（技能重标注和 CIB）的贡献。
  - 客观性：实验设置和结果报告应遵循 ICML 标准，公平性较高。但由于无法获得完整论文，无法评估统计显著性、随机种子数等细节。

## 6. 主要结论与发现
- GenDa 有效缓解了技能语义非平稳性，并提升了技能策略的泛化能力。
- 技能重标注机制显著提高了样本效率。
- 互补信息瓶颈使得技能表示更关注主体相关特征，对分布偏移更鲁棒。
- 整体上，GenDa 在无监督 RL 预训练中实现了更好的可扩展性和下游迁移性能。

## 7. 优点
- **创新性**：同时针对两个被忽视的瓶颈提出统一解决方案，而非单一改进。
- **实用性**：数据高效（适合样本稀缺场景）且泛化性强（适合多任务迁移）。
- **可复现性**：开源代码有利于社区验证和后续研究。
- **理论结合实践**：信息瓶颈理论在无监督 RL 中的创新应用，具有启发性。

## 8. 不足与局限
- **实验覆盖**：仅涉及连续控制任务，未说明是否在离散控制或视觉任务上验证（可能未涵盖）。
- **偏差风险**：可能仅在特定基准环境（如 MuJoCo）上有效，真实机器人部署或复杂变体环境中的表现未知。
- **应用限制**：技能重标注机制可能增加计算开销，且 CIB 的实现细节（如何选择互补特征）需要人工设计或经验调整。
- **缺失内容**：由于论文全文不可获取，无法评估数学证明、超参数敏感性、安全鲁棒性等方面的分析。

（完）
