---
title: "VeRO: A Harness for Agents to Optimize Agents"
title_zh: VeRO：用于智能体优化智能体的外框架
authors: "Varun Ursekar, Apaar Shanker, Veronica Chatrath, Yuan Xue, Samuel Marc Denton"
date: 2026-04-30
pdf: "https://openreview.net/pdf/38a8d3fd104d5e22b373e495b857fc055245fcdf.pdf"
tags: ["query:cli-agent"]
score: 6.0
evidence: 智能体框架优化；编码智能体；任务自动化
tldr: VeRO提出了一个用于优化目标智能体的外框架，通过版本控制、预算评估和结构化轨迹捕获来迭代改进智能体代码。该工作为自动化终端任务的CLI智能体提供了基础的优化工具和方法论支持。实验表明VeRO-Bench能够有效评估智能体优化能力，推动任务自动化领域的发展。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有编码智能体在智能体框架优化任务上缺乏系统理解，因框架交织确定代码与随机LLM补全，需要结构化追踪。
method: 提出VeRO框架，提供版本快照、预算控制和结构化执行轨迹，以及VeRO-Bench基准套件。
result: VeRO-Bench为评估智能体优化性能提供了标准测试环境，揭示了当前智能体的不足。
conclusion: VeRO作为通用工具，有助于推动任务自动化智能体的开发和改进。
---

## Abstract
An important emerging application of coding agents is *agent harness optimization*: the iterative improvement of a *target agent* by editing and evaluating its code. Despite its relevance, the community lacks a systematic understanding of coding agent performance on this task. Harness optimization differs from conventional software engineering: agent harnesses interleave deterministic code with stochastic LLM completions, requiring structured capture of both intermediate execution traces and downstream outcomes. To address these challenges, we introduce (1) VeRO (Versioning, Rewards, and Observations), an *outer harness* that provides versioned snapshots, budget-controlled evaluation, and structured execution traces of *target harnesses*, and (2) VeRO-Bench, a benchmark suite of target agents and tasks with reference evaluation procedures. Using VeRO, we conduct an empirical study comparing optimizers across tasks and analyzing which modifications reliably improve target agent harnesses. We release VeRO to support research on agent optimization as a core capability for coding agents. Code is available at https://github.com/scaleapi/vero.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：智能体（Agent）框架优化任务——即通过编辑和评估目标智能体的代码来迭代改进其性能——缺乏系统性的理解与方法支持。
- **动机**：传统的软件工程优化方法不适用于智能体框架，因为智能体框架交织了确定性代码与随机的大语言模型（LLM）补全结果，需要同时捕获中间执行轨迹和下游结果。
- **背景**：编码智能体（coding agent）的一个新兴重要应用是“智能体外框架优化”（agent harness optimization），但现有工作未对该任务进行系统研究。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：提出VeRO（Versioning, Rewards, and Observations）——一个“外框架”（outer harness），用于对目标智能体（target agent）进行版本控制、奖励评估和结构化轨迹捕捉，从而实现迭代优化。
- **关键技术细节**：
  - **版本快照**（Versioned snapshots）：记录每次修改后的智能体代码版本，便于回滚与对比。
  - **预算控制评估**（Budget-controlled evaluation）：在有限的资源（如调用次数、时间）下评估目标智能体性能。
  - **结构化执行轨迹**（Structured execution traces）：同时捕获中间执行步骤与最终结果，用于分析优化效果。
- **算法流程**（文字说明）：
  1. 初始化目标智能体代码（target harness）。
  2. 对目标智能体应用优化器（即另一个编码智能体），生成修改后的版本。
  3. 使用VeRO外框架对新版本进行预算控制下的评测，记录版本快照和结构化轨迹。
  4. 根据奖励（Rewards）决定是否接受该修改。
  5. 重复步骤2-4直到满足停止条件（如预算耗尽或性能收敛）。
- **基准套件**：同时提出VeRO-Bench，包含一组目标智能体及其任务，并提供参考评估流程。

## 3. 实验设计

- **数据集/场景**：VeRO-Bench提供了多个目标智能体与任务的组合，覆盖典型的终端任务自动化场景（如命令行工具、代码生成等）。
- **Benchmark**：VeRO-Bench本身即为基准，用于评测不同优化器（即其他编码智能体）在智能体框架优化上的性能。
- **对比方法**：论文中未明确列出具体对比方法，但实验部分通过“跨任务对比优化器”和“分析哪些修改可靠地改进了目标智能体”来评估不同策略的有效性。

## 4. 资源与算力

- **明确说明**：论文原文未提及使用的算力资源（如GPU型号、数量、训练时长等）。因此无法总结该部分，仅能指出文中未提供此类信息。

## 5. 实验数量与充分性

- **实验数量**：论文进行了“实证研究”，比较了多个优化器在不同任务上的表现，并分析了修改类型对性能的影响。具体实验组数未详细列出，但包含了跨任务的多组对比。
- **充分性评估**：实验设计较为客观，通过结构化轨迹和预算控制避免了随机性带来的偏差，但缺乏消融实验（例如针对外框架不同组件的贡献分析）的详细描述。整体上实验覆盖了基本验证需求，但可能不够全面。

## 6. 论文的主要结论与发现

- VeRO-Bench为评估智能体优化能力提供了标准测试环境，揭示了当前编码智能体在该任务上的不足。
- 通过对修改类型的分析，发现某些类型的代码修改（如调整LLM调用参数、改进错误处理）能更可靠地提升目标智能体性能。
- VeRO作为通用工具，能够有效支持智能体框架优化的研究与开发，有助于推动任务自动化智能体的进步。

## 7. 优点

- **方法创新**：专门针对智能体框架与LLM混合场景设计，提出版本控制、预算评估、结构化轨迹三位一体的优化框架。
- **实用性**：开源代码（GitHub），可直接复现与使用；VeRO-Bench为社区提供标准化评测。
- **实验严谨**：通过结构化轨迹分离确定性代码与随机LLM输出，减少评估噪声。

## 8. 不足与局限

- **实验覆盖有限**：论文未提供大规模、多领域的实验（如仅在少数任务上测试），推广性有待验证。
- **偏差风险**：目标智能体任务可能偏向特定领域（如CLI代理），对其他类型智能体（如对话、多模态）的适用性未知。
- **计算资源未公开**：无法评估方法的经济成本和可复现门槛。
- **缺乏消融研究**：未单独分析版本控制、预算控制和轨迹捕获各自对优化的贡献。

（完）
