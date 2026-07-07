---
title: "Going Beyond State-Reaching: Learning Abstractions for Intrinsically Motivated Skill Discovery"
title_zh: 超越状态达到：面向内在动机技能发现的抽象学习
authors: "Akhil Bagaria, Anita De Mello Koch, George Konidaris"
date: 2026-01-21
pdf: "https://openreview.net/pdf/66d9c28ba79abeb37d72bd6c9bdd44b137f0951f.pdf"
tags: ["query:skill-rl"]
score: 10.0
evidence: 层次强化学习中的技能发现
tldr: 该论文针对现有选项发现算法局限于状态达到的问题，提出了一种通过识别每个子目标的相关特征来学习抽象、可迁移选项的方法。该方法避免了选项数量爆炸，加速了稀疏奖励环境下的探索。实验证明其在多个图像任务中实现了高效探索。
source: ICML-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有选项发现算法因追求全状态达到而导致选项数量膨胀，难以泛化。
method: 提出识别每个子目标的相关特征子集，学习可迁移的抽象选项。
result: 在三个稀疏奖励图像任务中实现快速探索，优于基线。
conclusion: 通过学习抽象、可迁移的选项，显著提升探索效率。
---

## Abstract
Temporal abstraction via options can improve exploration in vast environments. However, existing option discovery algorithms find subgoals that target all aspects of the state simultaneously. This \textit{state-reaching} approach produces options that only apply in narrow regions of the state-space, eventually causing an explosion in the number of options that overwhelms the agent, and impedes progress on its primary task of reward maximization. We introduce an algorithm that instead identifies a small, relevant subset of features for each subgoal, yielding options that generalize broadly and accelerate exploration. Our approach learns abstract, transferrable options and achieves rapid exploration in three sparse-reward, image-based domains, including the Atari game \textsc{MontezumasRevenge}.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义
该论文聚焦于层次强化学习中的技能发现问题。现有选项（option）发现算法通常要求子目标**同时达到状态的所有维度**（即全状态达到），导致每个技能只能应用于状态空间中极狭窄的区域。随着技能数量爆炸，智能体被海量选项淹没，难以在主要任务（奖励最大化）上取得进展。论文旨在**超越状态达到的局限**，通过学习每个子目标中少量相关的特征，生成**可泛化、可迁移的抽象选项**，从而显著加速稀疏奖励环境下的探索。

## 2. 方法论
- **核心思想**：并非对所有状态特征都设定达到目标，而是为每个子目标识别出一个**小型的相关特征子集**（例如仅关注关键物体位置），忽略无关特征。这样学到的选项不再绑定到完整状态，而是抽象的操作（如“到达梯子”而非“到达坐标(12,34)处的梯子”），从而能广泛迁移到不同但相似的场景。
- **关键技术细节**：
    - 算法自动判断哪些特征是当前子目标的关键特征，哪些可以忽略。
    - 通过识别可迁移的抽象选项，避免选项数量随状态空间增长而爆炸。
    - 选项的学习过程仍然使用内在动机（如基于选项的奖赏）驱动，但目标函数仅考虑相关特征而非全状态。
- **公式或算法流程**：论文未给出具体伪代码，描述为“识别每个子目标的小型相关特征子集”并“学习抽象、可迁移的选项”。

## 3. 实验设计
- **使用的数据集/场景**：三个基于图像（image-based）的稀疏奖励领域，包括**Atari游戏《夺宝奇兵》（Montezuma’s Revenge）**。
- **Benchmark**：与现有选项发现算法（状态达到类方法）进行对比。
- **对比方法**：文中提及“现有选项发现算法”，但未列出具体命名；推测对比了典型的state-reaching选项发现基线（如基于subgoal的选项发现、option-critic等）。

## 4. 资源与算力
论文中未明确说明使用的GPU型号、数量或训练时长等算力资源。元数据中也未提及。

## 5. 实验数量与充分性
- 论文在**三个图像任务**上进行了实验（包括Montezuma’s Revenge），覆盖了不同的稀疏奖励场景。
- 元数据中未提及消融实验或其他补充实验。仅给出“实现了快速探索，优于基线”的结果，未提供详细的实验次数、统计数据或显著性检验。
- 实验**充分性**：有一定覆盖（三个场景），但缺乏消融研究（如不同特征选择策略的对比）和统计可靠性说明。从提供信息看，实验设计较简洁，充分性有待加强。

## 6. 主要结论与发现
- 通过学习抽象、可迁移的选项（仅关注相关特征），智能体能在**稀疏奖励图像任务**中实现**快速探索**。
- 该方法避免了选项数量爆炸，加速了主要任务（奖励最大化）的进展。
- 在Montezuma’s Revenge等难点游戏中表现优于基线方法。

## 7. 优点
- **创新性**：明确指出现有选项发现算法被“全状态达到”束缚，提出特征子集抽象的思想，方向新颖。
- **可迁移性**：学到的选项不再依赖完整状态，可在不同环境下复用，提升样本效率和泛化能力。
- **实用性**：适用于图像输入的高维状态空间，对真实稀疏奖励游戏（如Montezuma’s Revenge）有效。

## 8. 不足与局限
- **实验覆盖不足**：只有三个任务，缺乏在更广泛领域（如连续控制、机器人）的验证。
- **缺乏消融与详细分析**：未实验不同特征选择方法的影响，也未讨论选项数量与泛化效果的权衡。
- **资源与复现信息缺失**：未提供算力、超参数、代码开源等细节，可复现性存疑。
- **方法细节模糊**：元数据中仅有高层面描述，缺少算法伪代码或数学公式，读者难以了解具体实现。
- **可能存在偏差风险**：仅报告优于基线，未展示失败案例或局限性（如何时特征子集选择失败）。

（完）
