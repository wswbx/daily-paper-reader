---
title: An AI System for Autonomous Algorithm Evolution in Drug Development
title_zh: 用于药物开发中自主算法进化的人工智能系统
authors: "Zhou, Z., Nan, Y., Mou, M., Qian, Y., Liu, Y., Zuo, Z., Yang, H., Xu, W., Li, B., Jiang, W., Ren, Y., Liao, Y., Wang, Y., Li, Y., Yang, Q., Xi, Z., Mi, T., Sun, H., Liu, P., Zhu, F."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.16.745117v1.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 药物研发中的算法自主演化
tldr: 药物开发多阶段多任务依赖专家设计的专用算法，缺乏跨阶段协同优化，制约整体AI加速效果。为此提出DrugEvolve，一种多角色大语言模型系统，通过研究者、工程师、分析师协作，实现算法设计、实现、评估、改进的闭环自主进化。在11个代表性任务、120个基准测试集上显著提升性能，且对序列、图、分子拓扑、文本等异构数据模态及预测和生成任务均表现稳健。该系统不仅是药物开发的算法基础设施，也为更广泛科学领域提供了可迁移的自主进化范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有药物开发算法依赖人工设计与任务特化优化，难以跨阶段协同与自主迭代，阻碍整体AI赋能效果。
method: DrugEvolve构建多角色LLM闭环系统，融合Researcher、Engineer、Analyst三域，迭代执行设计、实现、评估与改进，实现算法自主进化。
result: 在11项任务120个基准测试集上大幅提升性能，并展示出对异构数据模态及预测、生成两类任务的稳健泛化能力。
conclusion: DrugEvolve可作为药物开发算法基础设施，并为更广泛科学领域提供算法自主进化的可迁移范式。
---

## 摘要
人工智能（AI）正日益渗透到药物开发流程中。为加速这一多阶段、多任务过程，人们构建了大量算法，而这些算法高度依赖专家设计和劳动密集型的任务特定优化。鉴于AI驱动的药物开发加速被认为是跨多个阶段的累积性、往往协同性的效应，因此需要在整个流程中实现现有算法的自主进化，以达成整体性进步。在此，我们提出了DrugEvolve——一个用于药物开发中系统化、自主算法进化的多角色大语言模型系统。DrugEvolve通过整合研究员、工程师和分析师角色，实现了闭环进化过程，并借助科学知识与累积的进化经验，支持算法的迭代设计、实现、评估与改进。在涵盖靶点识别、药物发现、临床前研究和临床试验的十一个代表性任务中，DrugEvolve自主进化出相应的任务特定算法，并在120个基准测试集上实现了显著的性能提升。此外，它展示了跨异构数据模态（从生物序列、图形到分子拓扑和文本语言）的稳健泛化能力，并在预测和生成任务中均取得了收益。总体而言，这一人工智能系统不仅可作为药物开发的算法基础设施，也可作为更广泛科学领域的可迁移范式。

## Abstract
Artificial intelligence (AI) is increasingly permeating the drug development pipeline. Numerous algorithms for accelerating this multi-stage and multi-task process have been constructed, which depends heavily on expert design and labor-intensive task-specific optimization. Given that AI-driven acceleration of drug development is recognized as a cumulative, often synergistic, effect across multiple stages, the autonomous evolution of existing algorithms across the entire pipeline is demanded to achieve a holistic advancement. Here, we present DrugEvolve, a multi-role large language model system for systematic and autonomous algorithm evolution in drug development. DrugEvolve realizes a closed-loop evolution process by incorporating Researcher, Engineer, and Analyst domains, and enables an iterative design, implementation, evaluation, and refinement of algorithm by leveraging scientific knowledge and accumulated evolutionary experience. Across eleven representative tasks spanning target identification, drug discovery, preclinical study, and clinical trial, DrugEvolve autonomously evolved the corresponding task-specific algorithms and achieved substantial performance enhancement on 120 benchmark test sets. Moreover, it showed robust generalizabilities across heterogeneous data modalities (ranging from biological sequence and graph to molecular topology and textual language), and realized gains in both predictive and generative tasks. Collectively, this AI system can serve not only as an algorithmic infrastructure for drug development, but also as a transferable paradigm for broader scientific domains.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **背景**：人工智能（AI）正在逐步渗透药物开发流程，已在靶点识别、药物发现、临床前研究及临床试验等多个阶段构建了大量专用算法。
- **问题**：现有算法高度依赖专家设计及劳动密集型的任务特定优化，缺乏跨阶段的协同与自主迭代能力，难以实现全局性的加速效果。
- **核心观点**：AI 驱动的药物开发加速应被视为跨多个阶段的**累积性、协同性效应**，因此需要一种能跨越整个流程的**算法自主进化机制**。
- **整体意义**：提出一种系统性、自主的算法进化范式，有望成为药物开发乃至更广泛科学领域的基础设施。

## 2. 方法论：核心思想、关键技术细节与流程
- **系统名称**：DrugEvolve，一个多角色大语言模型系统。
- **核心思想**：通过整合三类角色（Researcher、Engineer、Analyst）形成**闭环进化回路**，实现算法的自主迭代改进。
- **角色分工**：
  - **Researcher（研究员）**：负责科学知识驱动的问题定义与算法策略设计。
  - **Engineer（工程师）**：负责算法的具体实现与代码编写。
  - **Analyst（分析师）**：负责评估算法性能并分析改进方向。
- **进化流程**：迭代执行“设计 → 实现 → 评估 → 改进”四个环节，并利用**累积的进化经验**与**科学知识**指导后续迭代。
- **未提及具体公式或网络架构**，属于系统级描述。

## 3. 实验设计：数据集、基准与对比方法
- **任务覆盖**：11 个代表性任务，横跨药物开发全流程（靶点识别、药物发现、临床前研究、临床试验）。
- **基准规模**：共使用 **120 个基准测试集**。
- **数据模态**：生物序列、图结构、分子拓扑、文本语言等**异构数据**。
- **任务类型**：同时包含**预测任务**与**生成任务**。
- **对比方法**：摘要中**未明确列出具体基线算法**，仅提及“显著性能提升”，缺乏与现有 SOTA 方法的直接对比描述。

## 4. 资源与算力
- **未在摘要及元数据中给出**具体 GPU 型号、数量、训练时长或计算成本。
- 由于原始提取文本不完整，无法获知算力配置信息。

## 5. 实验数量与充分性
- **实验规模**：11 个任务、120 个基准测试集，覆盖面较广，属于大规模实证。
- **充分性**：
  - 优势：任务类型、数据模态多样，能较好测试泛化能力。
  - 不足：摘要未报告具体性能数值、方差、显著性检验；**未提及消融实验**（如移除某个角色或闭环机制带来的影响）；未说明与现有方法的公平对比设置。因此，实验的客观性与公平性尚无法充分评估。

## 6. 主要结论与发现
- DrugEvolve 能够自主进化出任务特定算法，并在 120 个基准测试集上带来“显著性能提升”。
- 系统展示了跨异构数据模态（序列、图、分子拓扑、文本）的**稳健泛化能力**。
- 在预测与生成两类任务中均取得收益。
- 作者认为该 AI 系统不仅可作为药物开发的**算法基础设施**，也能作为更广泛科学领域的**可迁移算法进化范式**。

## 7. 优点
- **自主性**：以闭环 LLM 系统减少人工专家干预，实现算法持续迭代。
- **多角色协同**：明确区分研究、工程、分析三个环节，结构清晰。
- **全局视角**：覆盖药物开发全流程，强调跨阶段协同优化。
- **广泛验证**：涉及多种任务与数据模态，初步证明通用性。

## 8. 不足与局限
- **细节缺失**：未提供具体性能数据、基线算法、消融实验，难以客观判断提升幅度。
- **计算成本不明**：未报告算力需求，可能限制实际落地。
- **可靠性风险**：算法自主进化可能引入不可预测行为，缺乏安全性与可控性讨论。
- **可解释性**：LLM 驱动的进化过程缺乏透明性，难以为关键药物开发决策提供解释。
- **未涉及伦理与监管**：对药物开发领域的高风险要求，如合规性、验证标准未做探讨。
- **提取文本不完整**：原文 PDF 因访问限制未能获取，部分技术细节可能遗漏。

（完）
