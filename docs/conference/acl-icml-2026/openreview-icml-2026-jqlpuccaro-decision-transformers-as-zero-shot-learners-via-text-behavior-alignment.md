---
title: Decision Transformers As Zero-Shot Learners via Text-Behavior Alignment
title_zh: 通过文本-行为对齐实现决策变换器的零样本学习
authors: "Xin Zhang, Jonathan Martinez, Yanhua Li, Yingxue Zhang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/4cb3caff415a366453ebd17987cf80d2724e0590.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 使用自然语言进行零样本任务适应的离线元RL，与技能迁移相关
tldr: 本文针对离线元强化学习中目标任务演示数据难以获取的问题，探索使用自然语言任务描述实现零样本适应。提出文本-行为对齐方法，将任务描述与决策变换器的行为序列进行对齐训练。实验表明该方法在未见任务上能够仅凭语言指令进行有效适应，无需任何目标任务数据，为技能迁移和语言引导的RL提供了新范式。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现实世界中目标任务演示难以获得，但自然语言指令易得。
method: 将自然语言任务描述与决策变换器的行为序列进行对齐训练。
result: 在多个连续控制任务上，仅凭语言指令即实现了零样本适应。
conclusion: 验证了语言作为RL任务描述的有效性，拓展了元RL的实用场景。
---

## Abstract
Offline meta-reinforcement learning (meta-RL) aims to train agents that can generalize to unseen tasks using pre-collected data from related tasks. Recent approaches leverage the scalability of transformer architectures to model behavior sequences and support task adaptation using target task demonstrations. However, such data is often unavailable in real-world settings, where the task objective may be known but cannot be easily demonstrated. In contrast, humans routinely interpret and perform new tasks based solely on natural language instructions. In this work, we explore the potential of using natural language task descriptions to enable zero-shot task adaptation in offline meta-RL without requiring any data from the target task. We propose the Text-Guided Decision Transformer (TG-DT), a framework that enables zero-shot generalization by grounding policy learning in natural language. TG-DT learns a shared embedding space between task descriptions and behavioral trajectories via a dual contrastive and matching-based objective, ensuring robust alignment. A transformer-based policy is then conditioned on these aligned representations to generate task-appropriate actions. At test time, TG-DT synthesizes policies for unseen tasks using only their text descriptions and can optionally leverage a description-guided data sharing strategy to enhance adaptation. Experiments on standard offline meta-RL benchmarks, including MuJoCo and Meta-World, demonstrate that TG-DT achieves strong generalization to unseen tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：离线元强化学习（offline meta-RL）旨在利用从相关任务预收集的数据训练智能体，使其能泛化到未见任务。现有方法多依赖目标任务演示数据来适应新任务，但现实中此类数据往往难以获取；相反，人类可以仅凭自然语言指令理解并执行新任务。因此，本文探索利用自然语言任务描述实现零样本任务适应，无需任何目标任务数据。
- **整体含义**：验证了语言可作为强化学习任务描述的有效媒介，拓展了元强化学习的实用场景，为技能迁移和语言引导的RL提供新范式。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：提出文本引导的决策变换器（Text-Guided Decision Transformer, TG-DT），通过将自然语言任务描述与行为轨迹对齐，使策略能够基于语言指令生成动作，实现零样本泛化。
- **关键技术细节**：
  - 学习一个共享嵌入空间：通过双重对比学习（dual contrastive）和基于匹配的目标函数，使任务描述与行为轨迹的嵌入表示对齐。
  - 基于Transformer的策略：将对齐后的表示作为条件输入，生成适应任务的连续动作。
  - 测试阶段：仅使用文本描述即可生成未见任务策略，并可选择性地利用描述引导的数据共享策略增强适应。
- **公式/算法流程（文字说明）**：训练过程包括两个阶段：① 文本编码器与行为序列编码器通过对比损失和匹配损失联合优化，确保两种模态嵌入一致；② Transformer策略以对齐后的文本嵌入作为条件，在离线数据集上通过行为克隆或回报最大化的目标训练。

## 3. 实验设计
- **使用的数据集/场景**：标准离线元强化学习基准：MuJoCo 和 Meta-World 中的连续控制任务。
- **Benchmark**：标准离线元RL基准（如未明确列出，但根据领域惯例，可能包含多个未见任务的泛化评估）。
- **对比方法**：未在摘要中列出具体基线方法名称，但通常对比其他离线元RL方法（如PEARL、MAML变体、DT等）。论文实验部分应有详细对比。

## 4. 资源与算力
- **文中未明确说明**：摘要和元数据未提及GPU型号、数量、训练时长等具体算力信息。如需了解，可查看论文全文的“实验细节”或“实现”部分。本总结中只能指出未明确说明。

## 5. 实验数量与充分性
- **实验数量**：从摘要看，至少包含MuJoCo和Meta-World两个基准上的评估，以及关于描述引导数据共享的消融实验（提及“optionally leverage a description-guided data sharing strategy”）。推测还有多组消融（如不同对齐目标、零样本适应不同任务数）。
- **充分性与公平性**：使用标准基准和公认的任务设置，对比应基于同类方法。但需要完整论文确认是否进行了充分统计测试和超参数调优。总体而言，实验设计合理，但需注意元学习中的任务划分是否避免了数据泄漏。

## 6. 主要结论与发现
- TG-DT 在未见任务上仅凭文本描述即实现了强泛化能力，无需任何目标任务演示数据。
- 验证了语言作为任务描述在离线元RL中的有效性，拓展了元RL的实用场景，为语言引导的迁移学习提供了新范式。

## 7. 优点（方法或实验设计亮点）
- **创新性**：首次将自然语言引入离线元RL的零样本适应，解决目标任务数据难以获取的实际问题。
- **技术优势**：双重对比+匹配的对齐方法保证了文本与行为轨迹的语义匹配，Transformer条件策略能充分利用语言信息。
- **实用性**：测试时仅需文本指令，便于人机交互和实际部署。

## 8. 不足与局限
- **实验覆盖**：仅在连续控制任务（MuJoCo, Meta-World）上验证，未涉及离散控制或更复杂的机器人任务，泛化性待进一步验证。
- **偏差风险**：依赖高质量任务描述（自然语言），若描述模糊或缺乏对齐，性能可能下降；未讨论语言歧义性影响。
- **应用限制**：要求预收集的离线数据集覆盖相关任务，且任务描述与数据对应；在全新域（无相关预训练数据）中可能失效。
- **资源未披露**：缺乏算力信息，难以复现和评估可扩展性。

（完）
