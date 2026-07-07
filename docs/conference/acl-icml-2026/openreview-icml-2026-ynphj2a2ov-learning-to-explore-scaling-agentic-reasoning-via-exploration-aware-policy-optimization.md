---
title: "Learning to Explore: Scaling Agentic Reasoning via Exploration-Aware Policy Optimization"
title_zh: 学习探索：通过探索感知策略优化扩展智能体推理
authors: "Xingyuan Hua, Sheng Yue, Ju Ren"
date: 2026-04-30
pdf: "https://openreview.net/pdf/1eaaa70094a1d7c3a9a83f5516f18234624bca0c.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 面向LLM智能体的探索感知强化学习框架，与RL技能学习相关
tldr: 现有智能体测试时扩展方法采用无差别探索策略，效率低下。本工作提出探索感知强化学习框架，通过变分推断设计细粒度奖励函数，估计探索动作对改善未来决策的潜在贡献，并结合探索感知分组机制。实验表明该方法能有效提升LLM智能体在复杂任务中的推理能力，可促进技能发现与重用。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有方法缺乏对何时需要探索的自适应区分，导致探索效率低下。
method: 基于变分推断设计奖励函数评估探索动作的潜在收益，并引入探索感知分组机制。
result: 在多个基准上，该方法显著提升了LLM智能体的任务完成质量与探索效率。
conclusion: 探索感知策略优化可有效提高智能体在不确定性下的决策能力，对技能学习有支持作用。
---

## Abstract
Recent advancements in agentic test-time scaling allow models to gather environmental feedback before committing to final actions. A key limitation of existing methods is that they typically employ undifferentiated exploration strategies, lacking the ability to adaptively distinguish when exploration is truly required. In this paper, we propose an exploration-aware reinforcement learning framework that enables LLM agents to adaptively explore only when uncertainty is high. Our method introduces a fine-grained reward function via variational inference that explicitly evaluates exploratory actions by estimating their potential to improve future decision-making, together with an exploration-aware grouping mechanism that separates exploratory actions from task-completion actions during optimization. By targeting informational gaps, this design allows agents to explore selectively and transition to execution as soon as the task context is clear. Empirically, we demonstrate that our approach achieves consistent improvements across a range of challenging text-based and GUI-based agent benchmarks.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文元数据和摘要生成的结构化中文总结。

---

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的大语言模型（LLM）智能体在“测试时扩展”（test-time scaling）方法中，通常采用**无差别（undifferentiated）的探索策略**，即不论当前环境的不确定性高低，都进行同等程度的探索。这导致探索效率低下，且在任务上下文已足够清晰时仍浪费计算资源。
- **研究动机**：智能体需要在不确定性高的情境下进行有效探索，而在不确定性低时及时转向任务执行。现有方法缺乏自适应区分“何时真正需要探索”的能力。
- **整体含义**：该工作旨在通过强化学习（RL）赋予LLM智能体**探索感知能力**，使其能够根据当前信息缺口（informational gaps）智能地决定是否探索，从而提升复杂任务中的推理能力和技能发现/重用。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出一个**探索感知强化学习框架**（Exploration-Aware RL Framework），使智能体仅在不确定性高时进行适应性探索。
- **关键技术细节**：
  - **细粒度奖励函数设计（基于变分推断）**：通过变分推断显式地评估每个探索动作对改善未来决策的潜在贡献，将这种“信息收益”转化为奖励信号，从而区分探索动作与常规任务完成动作。
  - **探索感知分组机制**：在优化过程中将探索性动作与任务完成性动作分离处理，避免混合优化导致策略退化。
  - **训练流程**：智能体首先通过探索收集环境反馈，当任务上下文清晰后立即切换到执行阶段，实现“选择性探索‑快速执行”的动态过渡。

## 3. 实验设计：数据集/场景、基准、对比方法

- **数据集/场景**：涵盖**基于文本**（text-based）和**基于GUI**（GUI-based）的多种具有挑战性的智能体基准任务。
- **Benchmark**：具体包括哪些环境未在摘要中详列，但提及“a range of challenging text-based and GUI-based agent benchmarks”，推测为经典的文本游戏（如ALFWorld）、GUI操作（如MiniWob++、WebShop）等。
- **对比方法**：论文元数据未明确列出对比基线，但从问题背景推测，应与现有的测试时扩展方法（如Chain-of-Thought with self-consistency、Tree-of-Thoughts、ReAct、或基于RL的探索策略）进行比较。

## 4. 资源与算力

- **文中说明**：所提供的元数据和摘要中**未明确提及**使用的GPU型号、数量、训练时长等算力信息。
- **备注**：由于是ICML 2026接收论文，通常需要大量的计算资源，但具体细节需查看完整论文才能获知。

## 5. 实验数量与充分性

- **实验数量**：元数据提到“多个基准”，且方法论包含消融设计（如是否加入分组机制、不同奖励函数变体等），推测至少包含3‑5个主要数据集上的性能对比，以及若干消融实验和可视化分析。但具体数字无法从现有信息确认。
- **充分性与公平性**：从tldr和摘要的积极表述看，实验应较为充分，并与主流基线进行了公平比较。但未提供详细统计信息（如重复次数、置信区间），可能存在一定偏差风险，需阅读完整论文验证。

## 6. 论文的主要结论与发现

- **主要结论**：探索感知策略优化能够**有效提升LLM智能体在不确定性下的决策能力**，推动技能发现与重用。
- **具体发现**：相比无差别探索方法，该方法在多个文本和GUI基准上实现了**一致且显著的性能提升**，同时提高了探索效率（更快完成任务、更少的无效探索）。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - **变分推断驱动的奖励函数**：为探索动作提供了理论上有依据的信息增益估计，而非启发式探索惩罚。
  - **分组机制**：将探索与执行分离优化，解决了传统RL中探索噪声干扰策略学习的问题。
  - **自适应探索终止**：智能体能自动识别任务上下文清晰时刻，实现从探索到执行的平滑过渡，既避免过度探索，又保证必要信息收集。
- **实验亮点**：覆盖文本和GUI两种典型智能体场景，结果一致提升，体现了方法具有较好的泛化能力。

## 8. 不足与局限

- **实验覆盖的局限性**：未提供详细的基准列表和对比基线，难以评估方法在更多复杂真实环境（如机器人操作、多智能体协作）中的表现。
- **偏差风险**：仅依赖元数据中的“score: 7.0”和正面tldr，可能忽略负面结果或局限性陈述；实际论文中可能包含失败案例及约束条件。
- **应用限制**：方法依赖RL训练，需要预先设计奖励函数（变分推断计算可能较复杂）；对于反馈周期极长的任务或高维连续动作空间，探索效率仍需进一步验证。
- **计算开销**：变分推断奖励估计可能引入额外计算成本，文中未提及推理时开销。

（完）
