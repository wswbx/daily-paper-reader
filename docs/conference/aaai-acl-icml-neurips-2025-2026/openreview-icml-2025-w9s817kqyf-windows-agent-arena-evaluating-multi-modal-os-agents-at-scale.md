---
title: "Windows Agent Arena: Evaluating Multi-Modal OS Agents at Scale"
title_zh: Windows代理竞技场：大规模评估多模态操作系统代理
authors: "Rogerio Bonatti, Dan Zhao, Francesco Bonacci, Dillon Dupont, Sara Abdali, Yinheng Li, Yadong Lu, Justin Wagle, Kazuhito Koishida, Arthur Bucker, Lawrence Keunho Jang, Zheng Hui"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=W9s817KqYf"
tags: ["query:cli-agent"]
score: 8.0
evidence: Windows操作系统下的多模态代理评估
tldr: 该论文提出Windows Agent Arena，一个大规模基准平台，用于在多模态Windows操作系统环境中评估LLM代理，涵盖真实应用和工具的使用，解决了现有基准领域局限和评估速度慢的问题，为OS代理研究提供了标准化评估框架。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有基准局限于特定模态或领域，且评估耗时巨大。
method: 构建Windows Agent Arena环境，允许代理在真实操作系统中自由操作，模拟人类用户使用各种应用和工具。
result: 提供了对多种LLM代理在跨领域任务上的系统评估，揭示了多模态交互的挑战。
conclusion: Windows Agent Arena为开发更通用、更有效力的OS代理提供了重要测试平台。
---

## Abstract
Large language models (LLMs) show potential as computer agents, enhancing productivity and software accessibility in multi-modal tasks. 
However, measuring agent performance in sufficiently realistic and complex environments becomes increasingly challenging as: 
(i) most benchmarks are limited to specific modalities/domains (e.g., text-only, web navigation, Q&A) and 
(ii) full benchmark evaluations are slow (on order of magnitude of multiple hours/days) given the multi-step sequential nature of tasks.
To address these challenges, we introduce Windows Agent Arena: a general environment focusing exclusively on the Windows operating system (OS) where agents can operate freely within a real OS to use the same applications and tools available to human users when performing tasks.
We create 150+ diverse tasks across representative domains that require agentic abilities in planning, screen understanding, and tool usage.
Our benchmark is scalable and can be seamlessly parallelized for a full benchmark evaluation in as little as $20$ minutes.
Our work not only speeds up the development and evaluation cycle of multi-modal agents, but also highlights and analyzes existing shortfalls in the agentic  abilities of several multimodal LLMs as agents within the Windows computing environment---with the best achieving only a 19.5\% success rate compared to a human success rate of 74.5\%.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的大语言模型（LLM）作为计算机代理的基准测试存在两大局限：（1）大多数基准局限于特定模态或领域（如纯文本、网页导航、问答）；（2）由于任务的多步顺序特性，完整评估耗时过长（数小时甚至数天），严重制约了代理能力的迭代开发。
- **整体含义**：为了弥补真实复杂环境与现有评估之间的鸿沟，需要一个通用、可扩展且高效的评估平台，能够模拟人类用户在实际操作系统中的多模态交互，从而推动更通用、更强大的操作系统代理的发展。

## 2. 论文提出的方法论

- **核心思想**：构建一个名为 **Windows Agent Arena** 的通用评估环境，该环境专门针对 Windows 操作系统设计，允许代理在真实的 OS 中自由操作，使用与人类用户相同的应用程序和工具来完成多样化任务。
- **关键技术细节**：
  - **真实操作系统环境**：代理可以在真实的 Windows 系统中执行鼠标点击、键盘输入、屏幕截图、文件操作等动作，而非模拟界面。
  - **任务设计**：创建了 **150+ 个多样化任务**，覆盖多个代表性领域（如办公软件、文件管理、浏览器操作等），要求代理具备规划、屏幕理解和工具使用等智能能力。
  - **可扩展性与并行化**：环境设计支持无缝并行化，可以在约 **20 分钟** 内完成整个基准的评估，极大缩短评估周期。
  - **评估流程**：以任务完成成功率（Success Rate）作为主要评价指标，人类基线为 74.5%。

## 3. 实验设计

- **使用的数据集/场景**：作者自行构建的 **150+ 个任务**，涵盖不同领域的 Windows 操作系统操作场景（未列出具体类别，但强调代表性）。
- **基准（Benchmark）**：Windows Agent Arena 本身即为新的基准平台。
- **对比的方法**：论文对比了多种多模态大语言模型（Multimodal LLMs）作为代理的表现。最佳模型在 Windows 环境下的成功率为 **19.5%**，而人类成功率为 **74.5%**。具体对比了哪些模型（如 GPT-4V 等）未在摘要中说明，但元数据提到“多种 LLM 代理”。

## 4. 资源与算力

- **明确说明**：论文中并未明确提及使用的 GPU 型号、数量或训练/评估时长（仅指出完整基准评估可并行化至 20 分钟完成）。
- **需要指出**：算力信息缺失，可能是由于该方法聚焦于评估而非训练，但评估所需的硬件资源（如是否依赖 API、本地 GPU 等）未披露。

## 5. 实验数量与充分性

- **实验数量**：主实验为 **150+ 个任务** 构成的一组评估。未提及消融实验、超参数调优或多轮实验。
- **充分性与公平性**：
  - **充分性较弱**：任务数量相对有限（150+），且未说明任务分布的多样性是否完全覆盖典型 Windows 操作场景。
  - **公平性较好**：提供了人类基线（74.5%），直接展示人机差距，有利于客观评估。
  - **局限性**：未提供不同模型在子任务上的详细表现分析，也未考虑代理失败原因的细粒度分类。

## 6. 主要结论与发现

- 当前最强的多模态 LLM 代理在真实的 Windows 操作环境中表现远低于人类水平（19.5% vs 74.5%），暴露出现有模型在规划、屏幕理解和工具使用等方面存在显著短板。
- Windows Agent Arena 作为一个高效、可扩展的评估平台，能够加速多模态代理的开发与评估循环，并为后续研究提供标准化测试床。

## 7. 优点（方法或实验设计上的亮点）

- **真实环境**：在真实 Windows 操作系统中进行评估，而非模拟或受限环境，更贴近实际应用需求。
- **多模态覆盖**：任务需要同时处理视觉（屏幕）、语言和工具使用，体现了 OS 代理的核心挑战。
- **高效评估**：通过并行化将完整评估时间压缩至 20 分钟，极大提升研究迭代速度。
- **人类基线对比**：引入人类成功率作为参考，使代理能力差距量化、直观。

## 8. 不足与局限

- **平台局限**：仅关注 Windows 操作系统，无法直接推广到 macOS、Linux 等其他 OS，限制了通用性。
- **任务规模较小**：150+ 个任务数量不足以覆盖所有长尾场景，可能产生过拟合评估的风险。
- **缺乏模型细节与分析**：未公开具体测试了哪些模型、各模型在不同任务上的表现差异，也未进行失败案例分析。
- **算力信息缺失**：未说明评估所需硬件资源，影响可复现性评估。
- **偏差风险**：任务设计可能存在隐式偏向（如偏向某类软件操作），导致评估不能完全代表真实用户环境。

（完）
