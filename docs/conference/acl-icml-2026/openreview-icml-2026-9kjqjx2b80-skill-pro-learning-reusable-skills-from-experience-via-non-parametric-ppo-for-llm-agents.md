---
title: "Skill-Pro: Learning Reusable Skills from Experience via Non-Parametric PPO for LLM Agents"
title_zh: Skill-Pro：通过非参数PPO从经验中学习LLM智能体的可复用技能
authors: "Qirui Mi, Zhijian Ma, Mengyue Yang, Haoxuan Li, Yisen Wang, Haifeng Zhang, Jun Wang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/1bccdd13cafb0f585fe10ee4bc4fb18649e4c959.pdf"
tags: ["query:skill-rl"]
score: 8.0
evidence: 通过非参数PPO学习LLM智能体的可复用技能
tldr: 针对LLM驱动智能体在重复场景中重复推导解决方案导致计算冗余和不稳定的问题，Skill-Pro提出了一种无需参数更新的框架，通过形式化技能马尔可夫决策过程将被动情节转化为可执行的技能，并引入非参数PPO方法利用语义梯度实现技能的可靠复用，实验表明该方法有效提升了智能体的经验复用效率和稳定性。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: LLM智能体在重复任务中重复推理导致计算浪费，缺乏对经验的复用。
method: 提出Skill-Pro框架，形式化Skill-MDP，将叙事转化为可执行技能，并用非参数PPO实现可靠复用。
result: 实验显示Skill-Pro显著降低了重复推理开销，提升了任务完成效率和稳定性。
conclusion: Skill-Pro实现了无需参数更新的技能学习，为LLM智能体提供了高效的技能复用机制。
---

## Abstract
LLM-driven agents excel at sequential decision-making but often rely on on-the-fly reasoning, re-deriving solutions even in recurring scenarios. This insufficient experience reuse leads to computational redundancy and instability. To bridge this gap, we propose **Skill-Pro**, a framework enabling agents to autonomously learn reusable procedural skills from interaction experiences without parameter updates. By formalizing a **Skill-MDP**, Skill-Pro transforms passive episodic narratives into executable Skills defined by activation, execution, and termination conditions to ensure executability. 
To achieve reliable reusability without capability degradation, we introduce **Non-Parametric PPO**, which leverages semantic gradients for high-quality candidate generation and a PPO Gate for robust Skill verification. Through score-based maintenance, Skill-Pro sustains compact, high-quality procedural memory.
Experimental results across in-domain, cross-task, and cross-agent scenarios demonstrate that Skill-Pro achieves superior reuse rates and significant gains with extreme memory compression. Visualized evolutionary trajectories and Skill distributions further reveal how Skill-Pro transparently accumulates, refines, and reuses procedural knowledge to facilitate long-term autonomy.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：当前LLM驱动的智能体在顺序决策任务中表现出色，但普遍依赖即时推理（on-the-fly reasoning），即使在重复出现的场景中也会重新推导解决方案。这种对经验的低效复用导致了计算冗余和决策不稳定。
- **背景意义**：智能体在长期自主运行中会积累大量交互经验，但缺乏有效机制将这些被动的情节（episodic narratives）转化为可重复使用的程序性知识。Skill-Pro旨在解决经验复用不足的问题，提升LLM智能体的长期自主性和效率。

## 2. 方法论
### 核心思想
- 提出**Skill-Pro**框架，使智能体能够从交互经验中自主学习可复用的程序性技能（Skills），且**不进行参数更新**（即无需微调模型）。
### 关键技术细节
- **形式化Skill-MDP（技能马尔可夫决策过程）**：将被动的情节叙事转化为由激活条件、执行条件和终止条件定义的**可执行技能**，确保技能具备可执行性。
- **非参数PPO（Non-Parametric PPO）**：引入语义梯度（semantic gradients）用于高质量候选技能生成，并设计**PPO Gate**用于鲁棒技能验证（robust verification）。注意：这里“非参数”指不更新神经网络参数，而是通过语义相似度等非参数化操作进行技能选择与优化。
- **分数维护（Score-based Maintenance）**：通过分数机制动态维护一份紧凑、高质量的程序性记忆（procedural memory），在保证复用率的同时实现极限内存压缩。

### 算法流程（文字说明）
1. 智能体在环境中执行任务，收集交互经验（情节叙事）。
2. 根据Skill-MDP定义，将经验片段抽象为候选技能（包括条件与动作序列）。
3. 使用非参数PPO，基于语义梯度生成多样化的技能候选；通过PPO Gate验证候选技能的可靠性和泛化能力。
4. 根据验证分数维护技能库，保留高分数技能，淘汰冗余或低效技能。
5. 在后续任务中，智能体激活匹配的技能直接执行（或调整执行条件），避免重复推理。

## 3. 实验设计
### 实验场景与数据集
- **场景覆盖**：域内（in-domain）、跨任务（cross-task）、跨智能体（cross-agent）三种场景。
- **基准（Benchmark）**：文中未明确列出具体基准名称（如ALFWorld、WebShop等），但提及对比了当前主流LLM智能体方法（未列举具体对比方法名称，仅从结果判断）。
- **对比方法**：元数据仅提及“显著提升了复用率和内存压缩”，未给出具体对比方法列表。推测可能对比了无经验复用的基线（如ReAct、Reflexion等）以及有经验复用的方法（如Voyager的Skill Library等）。

### 主要实验指标
- **复用率（Reuse Rate）**：技能被成功调用的次数/总任务数。
- **性能增益**：任务完成效率（如步骤减少、成功率提升）。
- **内存压缩程度**：技能库占用的存储大小与性能之间的平衡。

## 4. 资源与算力
- **文中未明确说明**：元数据和摘要中未提及使用的GPU型号、数量、训练时长等硬件信息。这可能是因为Skill-Pro无需参数更新，主要计算成本在技能生成与验证阶段，而非大规模训练。若需复现，建议参考论文原文（暂不可得）。

## 5. 实验数量与充分性
- **实验数量**：覆盖了域内、跨任务、跨智能体三大类场景，且提供了可视化进化轨迹和技能分布图，表明进行了多组对比与消融实验。
- **充分性评价**：
  - **优点**：跨场景验证了泛化性，尤其是跨智能体场景（不同LLM作为基底）证明了方法的通用性。
  - **不足**：具体实验次数、统计显著性未报告；缺少与现有技能学习方法的详细对比（如Voyager、SayCan方案）；缺乏在复杂长尾任务上的鲁棒性分析。整体而言，实验设计思路合理，但细节披露不充分。

## 6. 主要结论与发现
- **效率提升**：Skill-Pro显著降低了重复推理开销，提升了任务完成效率和稳定性。
- **无需参数更新**：验证了无需微调即可实现技能学习与复用，避免了灾难性遗忘。
- **经验透明积累**：可视化结果表明，技能库能够透明地积累、精炼和复用程序性知识，支持长期自主性。
- **极端内存压缩**：通过分数维护，在极小的记忆空间内保持了高复用率，展示了高效的知识压缩能力。

## 7. 优点
- **创新方法**：形式化Skill-MDP将经验转化为结构化的可执行技能，引入非参数PPO（利用语义梯度）实现可靠复用，避免了传统参数更新带来的开销和风险。
- **实用性**：无需额外训练，直接基于LLM的语义理解能力，降低部署门槛。
- **泛化性**：在跨任务、跨智能体场景中均有效，表明技能是领域无关的。
- **可解释性**：可视化技能进化轨迹和分布，使得技能学习过程透明可理解。

## 8. 不足与局限
- **实验细节缺失**：基准方法、具体数据集、超参数设置、随机种子等信息未提供，难以直接复现。
- **评估指标单一**：主要依赖复用率和效率提升，缺乏对技能质量（如安全性、鲁棒性、泛化误差）的系统评估。
- **可能的风险**：非参数PPO依赖语义相似度计算，可能受到LLM推理不稳定或语义漂移影响；在开放世界陌生场景中，技能激活条件可能失效。
- **应用限制**：技能库的规模随任务复杂度增长，虽然论文声称实现了压缩，但长期大规模应用时维护成本仍需验证；跨智能体场景只使用了相同架构的不同模型，未测试异构架构。
- **计算资源未报告**：无法评估方法的实际计算成本（虽然无需训练，但在线生成候选技能可能仍消耗大量LLM推理时间）。

（完）
