---
title: "MARS: Modular Agent with Reflective Search for Automated AI Research"
title_zh: "MARS: 面向自动化AI研究的模块化智能体与反思式搜索"
authors: "Jiefeng Chen, Bhavana Dalvi Mishra, Jaehyun Nam, Rui Meng, Tomas Pfister, Jinsung Yoon"
date: 2026-04-30
pdf: "https://openreview.net/pdf/faa2d50139c5418d4ae94887486b3cdf027aef90.pdf"
tags: ["query:ar"]
score: 9.0
evidence: MARS是专为自动化AI研究设计的模块化智能体，具有反思式搜索
tldr: 自动化AI研究的关键瓶颈是复杂机器学习工程任务的执行。MARS框架通过预算感知的蒙特卡洛树搜索平衡性能与开销，采用模块化构建和反思式搜索，在多个MLE任务上显著优于现有智能体。该工作为自主研究提供了可扩展的框架。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有LLM智能体难以处理计算开销大且归因困难的MLE任务。
method: 提出预算感知MCTS规划、模块化构建及反思搜索三部分框架。
result: 在多种MLE基准上超越现有方法，实现高效自主研究。
conclusion: MARS为自动化AI研究提供了有效的模块化智能体范式。
---

## Abstract
A critical bottleneck in automating AI research is the execution of complex machine learning engineering (MLE) tasks. MLE differs from general software engineering due to computationally expensive evaluation (e.g., model training) and opaque performance attribution. Current LLM-based agents struggle here, often generating monolithic scripts that ignore execution costs and causal factors. We introduce **MARS** (**M**odular **A**gent with **R**eflective **S**earch), a framework optimized for autonomous AI research. MARS relies on three pillars: (1) Budget-Aware Planning via cost-constrained Monte Carlo Tree Search (MCTS) to explicitly balance performance with execution expense; (2) Modular Construction, employing a "Design-Decompose-Implement" pipeline to manage complex research repositories; and (3) Comparative Reflective Memory, which addresses credit assignment by analyzing solution differences to distill high-signal insights. MARS achieves state-of-the-art performance among open-source frameworks on MLE-Bench under comparable settings, maintaining competitiveness with the global leaderboard's top methods. Furthermore, the system exhibits qualitative "Aha!" moments, where 63% of all utilized lessons originate from cross-branch transfer, demonstrating that the agent effectively generalizes insights across search paths.

---

## 论文详细总结（自动生成）

好的，以下是根据提供的论文信息生成的中文总结。

---

# MARS: 面向自动化AI研究的模块化智能体与反思式搜索

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：自动化AI研究面临的关键瓶颈在于复杂机器学习工程（MLE）任务的执行。MLE任务与通用软件工程不同，其评估代价高昂（例如需要训练模型），且性能归因困难（很难确定哪些修改带来了性能提升）。
- **现有方法不足**：当前的基于大语言模型（LLM）的智能体难以处理此类任务，常常生成单体脚本（monolithic scripts），忽略执行成本，且无法有效归因因果因素。
- **整体含义**：本文提出MARS框架，旨在为自主AI研究提供可扩展的、高效的模块化智能体范式，能够平衡性能与计算开销，并实现跨搜索路径的知识迁移。

## 2. 论文提出的方法论：核心思想、关键技术细节

MARS框架基于三大支柱：

- **预算感知规划（Budget-Aware Planning）**：通过成本约束的蒙特卡洛树搜索（MCTS）来显式平衡性能与执行开销。MCTS在搜索时不仅考虑结果性能，还将计算预算（如训练时间、GPU成本）纳入决策，避免无限制的试验。
- **模块化构建（Modular Construction）**：采用“设计-分解-实现”（Design-Decompose-Implement）流水线来管理复杂的研究代码仓库。将任务分解为可独立评估和重用的子模块，降低整体复杂度。
- **对比反思记忆（Comparative Reflective Memory）**：通过分析不同解决方案之间的差异，提炼出高信号（high-signal）的见解，解决信用分配（credit assignment）问题。系统将成功的经验总结为“教训”（lessons），并跨搜索分支迁移利用。摘要提到63%的已利用教训来源于跨分支迁移，表明智能体能够有效泛化见解。

整体流程可描述为：MARS首先通过预算感知MCTS规划一系列实验，然后以模块化方式构建代码，执行并评估效果，最后通过对比反思更新记忆，指导后续搜索。

## 3. 实验设计：数据集/场景、基准、对比方法

- **数据集/场景**：MLE-Bench，这是自动化AI研究领域常用的机器学习工程基准，包含多种MLE任务（如模型训练、调参、数据预处理等）。
- **对比方法**：与其他开源框架进行对比，作者声称MARS在可比较的设置下取得了开源自框架中的最先进性能（state-of-the-art），并且与全球排行榜（global leaderboard）上的顶尖方法具有竞争力。具体对比了哪些方法未在摘要中列出，但暗示包括了其他LLM智能体方案。
- **评估指标**：主要依据性能与成本平衡，可能包括任务完成率、最终得分、计算开销等。

## 4. 资源与算力

- 摘要及元数据中未明确说明使用的GPU型号、数量或训练时长。论文方法本身涉及多次模型训练（MLE任务），但具体的算力消耗信息缺失。需要指出这一点：原文未提供详细的算力配置。

## 5. 实验数量与充分性

- 摘要仅提到在MLE-Bench上进行了整体性能对比，以及跨分支迁移比例的定性分析（63%的教训来自跨分支）。未提及消融实验的具体数量或不同设置下的对比。
- 实验充分性评估：根据现有信息，实验覆盖了一个基准，且强调了开源自框架中的SOTA，但缺乏对多个数据集的验证。此外，消融实验（如去掉预算感知、模块化或反思记忆的变体）仅在元数据中提及进行了消融？元数据的中文tldr提到“在多个MLE任务上显著优于现有智能体”，但具体数量不明确。总体来看，实验设计有一定代表性，但充分性有待作者在完整论文中补充更多细节。

## 6. 论文的主要结论与发现

- MARS框架在自动化AI研究任务上显著优于现有的开源智能体，在MLE-Bench上达到开源自框架最佳性能，与全球排行榜顶尖方法有竞争力。
- 系统展示了定性上的“顿悟”时刻（Aha! moments）：63%的利用教训来源于跨不同搜索分支的迁移，证明模块化反思机制确实能够有效泛化知识，而不仅仅是记忆。

## 7. 优点：方法或实验设计上的亮点

- **预算感知MCTS**：将计算成本显式纳入规划，比无限制搜索更实用、更贴近现实资源约束。
- **模块化构建**：降低了复杂工程的实现难度，有利于代码复用和独立调试。
- **对比反思记忆**：创新的信用分配机制，通过比较差异提炼见解，并实现了跨分支知识迁移，这是自动化研究智能体在泛化能力上的重要进步。
- 实验设计上，不仅对比了整体性能，还分析了学习教训的来源，提供了对内部机制的定性洞察。

## 8. 不足与局限

- **实验覆盖有限**：仅在一个基准（MLE-Bench）上验证，缺乏在更多样化、更复杂AI研究任务上的测试。
- **算力信息缺失**：未报告具体的GPU型号、数量或训练耗时，使得可重复性和资源评估困难。
- **消融实验细节缺乏**：摘要未提供消融实验的具体结果或统计分析，削弱了对各组件贡献度的理解。
- **应用限制**：方法依赖LLM（未明确模型），可能受限于LLM本身的能力和成本；且MCTS搜索在预算约束下可能仍然需要较多试错，适用于资源充足场景。
- **偏差风险**：跨分支教训迁移的63%比例来自单一框架的表现，可能对特定搜索空间敏感。

---

（完）
