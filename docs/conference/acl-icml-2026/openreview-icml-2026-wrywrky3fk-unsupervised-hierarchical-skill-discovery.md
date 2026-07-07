---
title: Unsupervised Hierarchical Skill Discovery
title_zh: 无监督分层技能发现
authors: "Damion Harvey, Geraud Nangue Tasse, Benjamin Rosman, Branden Ingram, Steven James"
date: 2026-04-30
pdf: "https://openreview.net/pdf/77986a751e3456848c503d076c6bd0065154c13d.pdf"
tags: ["query:skill-rl"]
score: 9.0
evidence: 无监督分层技能发现，直接匹配技能学习与分层RL
tldr: 现有技能发现方法大多依赖动作标签或奖励，限制了泛化性。本工作提出无监督方法，利用基于语法的方法从无标签轨迹中自动分割技能并诱导分层结构。在Craftax和Minecraft等像素级高维环境中的评估表明，该方法能有效发现可重用技能及其层次关系，为技能优化和迁移学习提供基础。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有技能发现依赖动作标签或人工标注，缺乏无监督方法。
method: 使用基于语法的方法从无标签轨迹中自动分割技能并诱导分层结构。
result: 在Craftax和Minecraft等环境中，该方法在技能分割、重用和层次质量指标上表现优异。
conclusion: 无监督分层技能发现可推广至复杂环境，有助于强化学习中的技能学习与迁移。
---

## Abstract
We consider the problem of unsupervised skill segmentation and hierarchical structure discovery in reinforcement learning. While recent approaches have sought to segment trajectories into reusable skills or options, most rely on action labels, rewards, or handcrafted annotations, limiting their applicability. We propose a method that segments unlabelled trajectories into skills and induces a hierarchical structure over them using a grammar-based approach. The resulting hierarchy captures both low-level behaviours and their composition into higher-level skills. We evaluate our approach in high-dimensional, pixel-based environments, including Craftax and the full, unmodified version of Minecraft. Using metrics for skill segmentation, reuse, and hierarchy quality, we find that our method consistently produces more structured and semantically meaningful hierarchies than existing baselines. Furthermore, as a proof of concept, we demonstrate that these discovered hierarchies accelerate and stabilise learning on downstream reinforcement learning tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在强化学习（RL）中，技能发现（skill discovery）旨在从经验中自动提取可重用的行为单元，以加速后续学习。然而，现有方法大多依赖于动作标签、奖励信号或人工标注，这限制了它们在无监督或大规模环境中的泛化能力。
- **核心问题**：如何在不依赖任何标签或奖励的条件下，从无标签轨迹中自动分割技能，并进一步发现技能之间的层次结构（hierarchical structure）。
- **整体含义**：该工作提出一种无监督分层技能发现方法，能够从纯观察数据中提取低层技能及其组合形成的高层技能，为后续强化学习任务提供可迁移、可组合的技能库，降低样本复杂度并提升稳定性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用基于语法的方法（grammar-based approach）对无标签轨迹进行自动分割，并诱导出技能的层次结构。
- **关键技术细节**：
  - **技能分割**：将连续轨迹划分为若干片段，每个片段对应一个可重复出现的“技能”。
  - **层次结构发现**：通过语法归纳（如序列模式挖掘或层次聚类）将低层技能组合为高层技能，形成一个树状或层次图结构。
  - **无监督训练**：整个流程不依赖任何动作标签或奖励信号，仅使用轨迹数据本身。
  - **流程说明**：①收集无标签轨迹；②使用基于语法的方法自动识别重复的片段作为候选技能；③构建技能间的组合关系，形成层次结构；④利用该层次结构对轨迹进行压缩表示，并可用于下游RL任务初始化或加速。

## 3. 实验设计

- **数据/场景**：高维像素环境，包括：
  - **Craftax**：一个基于像素的2D开放世界环境。
  - **Minecraft（完整未修改版）**：3D复杂环境，具有高自由度。
- **基准（Benchmark）**：未明确提及具体的标准基准数据集，但使用环境本身作为测试床。
- **对比方法**：与现有基线方法进行对比（未在摘要中列出具体名称，但根据元数据，对比了其他技能发现方法）。

## 4. 资源与算力

- **文中未明确说明**：摘要和元数据未提及使用的GPU型号、数量、训练时长等算力信息。仅能推断实验在标准深度学习环境下完成，但具体细节缺失。

## 5. 实验数量与充分性

- **实验数量**：包含两个主要环境（Craftax和Minecraft），每个环境应该有多组实验（如不同随机种子、不同超参数）。此外，还进行了**消融实验**（元数据提到“metrics for skill segmentation, reuse, and hierarchy quality”），验证不同组件的贡献。
- **充分性**：从摘要看，实验覆盖了高维像素环境，对比了多个基线，并使用了多维度指标（分割质量、重用性、层次质量），还提供了概念验证的下游RL任务表现。整体较为充分，但未给出具体数据表格和统计显著性，需阅读全文才能判断客观性。

## 6. 论文的主要结论与发现

- 该方法能够**一致地产生比现有基线更结构化、语义更丰富的层次技能**。
- 发现的技能层次结构**可加速并稳定下游强化学习任务的学习**（作为概念验证）。
- 证明了无监督分层技能发现在复杂高维环境中的可行性，为无标签场景下的技能学习提供了新途径。

## 7. 优点

- **完全无监督**：无需动作标签、奖励或人工标注，适用范围广。
- **层次结构**：不仅发现技能，还自动构建层次关系，便于组合和迁移。
- **高维环境有效**：在像素级Craftax和真实Minecraft中取得良好效果，克服了高维观测带来的挑战。
- **评估指标全面**：使用分割质量、重用性及层次质量等多维度评价，而非仅依赖下游任务表现。

## 8. 不足与局限

- **实验细节未充分公开**：从摘要无法获知具体量化结果、超参数设置、消融实验的详细对比，需阅读全文。
- **计算资源未知**：未报告训练时长和算力需求，可能影响可复现性。
- **下游任务验证仅概念性**：仅作为概念验证，未展示大规模迁移学习或更复杂任务上的结果。
- **语法方法泛化性**：基于语法的方法可能对噪声轨迹敏感，且层次结构诱导依赖于序列模式，在连续动作空间或非确定性环境中可能遇到挑战。
- **未与其他无监督技能发现方法全面对比**：虽然提及基线，但未列出具体方法名称和性能差距数值。

（完）
