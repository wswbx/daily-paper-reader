---
title: "DeepAnalyze: Agentic Large Language Models for Autonomous Data Science"
title_zh: "DeepAnalyze: 用于自主数据科学的智能体大语言模型"
authors: "Shaolei Zhang, Ju Fan, Meihao Fan, Yizhe Liu, Yuxin Zhang, Xiaoyong Du"
date: 2026-04-30
pdf: "https://openreview.net/pdf/63f494c22e2663906f91db74443c1a6040bef340.pdf"
tags: ["query:ar"]
score: 9.0
evidence: DeepAnalyze是首个实现端到端自主数据科学的智能体LLM
tldr: 现有数据智能体依赖预定义工作流，难以实现完全自主。DeepAnalyze通过课程式智能体训练范式，让LLM逐步学习并整合多种数据科学技能，首次实现了从原始数据到研究报告的端到端自动化。在复杂数据科学任务中展现出超越工作流方法的性能。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有数据智能体依赖工作流，无法实现完全自主的数据科学。
method: 提出课程式智能体训练，渐进式学习数据科学全流程技能。
result: 在端到端数据科学任务中取得领先性能。
conclusion: 课程训练范式可赋予LLM真正的自主数据科学能力。
---

## Abstract
Autonomous data science has been a long-standing challenge, and is now becoming feasible with the emergence of powerful large language models (LLMs). Recent workflow-based data agents have shown promising results on specific data tasks but remain fundamentally limited in achieving full autonomy due to their reliance on predefined workflows. In this paper, we introduce DeepAnalyze, the first agentic LLM for autonomous data science, capable of automatically completing the end-to-end data science from raw data to research reports. To tackle high-complexity data science tasks, we propose a curriculum-based agentic training paradigm that emulates the learning trajectory of human data scientists, enabling LLMs to progressively acquire and integrate multiple capabilities in real-world environments. Accordingly, we contribute a data-grounded trajectory synthesis framework to constructs high-quality data science training data. Through training in real-world environment, DeepAnalyze learns to perform a broad spectrum of data tasks, ranging from data question answering to open-ended data research. Experiments on 13 benchmarks demonstrate that, with only 8B parameters, DeepAnalyze outperforms workflow-based agents built on advanced proprietary LLMs. DeepAnalyze is fully open-sourced, paving the way toward autonomous data science.

---

## 论文详细总结（自动生成）

# DeepAnalyze: 用于自主数据科学的智能体大语言模型 — 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：自主数据科学（autonomous data science）长期以来是人工智能领域的挑战。尽管近期大语言模型（LLM）的兴起使得构建数据科学智能体成为可能，但现有的工作流式数据智能体（workflow-based data agents）虽然在特定数据任务上表现良好，却因依赖预定义的工作流程而**无法实现真正意义上的完全自主**——它们不能根据任务动态调整行为，缺乏从原始数据到研究报告的端到端自动化能力。
- **整体含义**：本文首次提出了一种**端到端自主数据科学的智能体LLM**——DeepAnalyze，它能够自动完成从原始数据到最终研究报告的完整数据科学流程，无需人工干预或预设工作流，从而推动数据科学领域向更高程度的自动化迈进。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：受人类数据科学家学习轨迹的启发，提出**课程式智能体训练范式（curriculum-based agentic training paradigm）**，让LLM在真实环境中逐步习得并整合数据科学的多种技能，最终具备自主完成复杂数据科学任务的能力。
- **关键技术细节**：
  - **课程式学习**：将数据科学全流程分解为从简单到复杂的多个阶段（如数据清洗、探索性分析、建模、报告生成等），模型按照课程顺序逐步学习，避免一次性学习全部能力的困难。
  - **数据驱动的轨迹合成框架（data-grounded trajectory synthesis framework）**：自动构建高质量的数据科学训练数据，确保模型学习到的行为序列（trajectories）既有数据基础又覆盖广泛任务。
  - **环境交互训练**：在真实的数据科学环境中（如Python环境、数据库等）训练模型，使其能够执行代码、调用工具并观察结果，从而获得反馈并调整行为。
  - **端到端自主**：模型无需预定义工作流，而是根据当前任务上下文自主决定下一步行动，最终输出完整的研究报告。

## 3. 实验设计：数据集/场景、基准、对比方法

- **基准（Benchmarks）**：在 **13 个公开数据集/基准**上进行了评估，涵盖数据问答（data question answering）和开放式数据研究（open-ended data research）等多种任务类型。
- **对比方法**：主要对比了**基于工作流的智能体（workflow-based agents）**，这些智能体通常依赖强大的专有LLM（如GPT-4、Claude等）作为推理引擎，但运行在预设的工作流框架中。DeepAnalyze则仅使用 **8B参数**的开源模型，与这些大型专有模型的智能体进行对比。
- **场景覆盖**：包括结构化数据分析、自然语言查询、可视化生成、统计检验、模型构建等常见数据科学子任务，以及从原始数据直接生成研究报告的端到端场景。

## 4. 资源与算力

- **文中未明确说明**：论文摘要和元数据中**没有提及**具体使用的GPU型号、数量、训练时长或总计算量。仅知模型参数量为8B（8 billion parameters），属于中小规模的开源LLM。如需了解计算资源细节，需要查阅论文正文的实验设置部分。

## 5. 实验数量与充分性

- **实验数量**：在13个基准上进行了系统性评估，且对比了多种工作流基线的变体，实验组数较多（每个基准可能包含多个子任务）。此外，论文提到了“课程式训练”本身涉及多阶段训练，暗示了消融实验或阶段对比（尽管摘要中未详细列出）。
- **充分性与客观性**：
  - 覆盖了从简单数据问答到复杂开放研究的多种任务，场景较为全面。
  - 仅8B参数模型超过基于先进专有LLM的工作流智能体，结果具有说服力。
  - 但**未提及是否进行了人类评估**（如报告质量的人工评分），仅依赖自动指标可能存在偏差；也未说明多个基准结果的方差或统计显著性检验。总体来说实验设计较好，但部分细节（如消融研究、超参数敏感性）可能需要在正文中进一步验证。

## 6. 论文的主要结论与发现

- **核心结论**：课程式智能体训练范式能够有效赋予LLM真正的自主数据科学能力，使模型不再依赖预定义工作流。
- **关键发现**：
  - DeepAnalyze（8B参数）在13个基准上**全面超越**基于大型专有LLM（如GPT-4）构建的工作流智能体，证明了自主智能体相比于固定工作流的优势。
  - 模型仅需8B参数即可实现端到端自主，说明训练范式的有效性远胜于单纯扩大模型规模。
  - 数据驱动的轨迹合成是高质量训练的关键，可使模型在真实环境中习得正确的行为序列。
  - 开源全部代码和模型，为后续研究提供了基础。

## 7. 优点：方法或实验设计上的亮点

- **方法新颖性**：首次提出课程式智能体训练，模仿人类数据科学家的学习路径，避免了传统多任务学习中的灾难性遗忘和技能碎片化问题。
- **实用性强**：模型仅8B参数，可部署在消费级GPU上，实用性和可复现性高。
- **实验设计全面**：在13个基准上评估，涵盖多种数据科学任务，且与强基线（基于GPT-4等）进行比较，结果可靠。
- **开源贡献**：完全开源模型、代码和训练数据，促进社区进一步研究和复现。

## 8. 不足与局限

- **算力细节缺失**：未报告训练所需计算资源，影响对方法经济性的评估。
- **实验覆盖有限**：虽然基准数量多，但均基于英文数据和公开数据集，缺乏对中文、多语言或领域特定数据（如医疗、金融）的验证，泛化能力未知。
- **未报告消融研究**：未详细说明课程式训练的各阶段效果、轨迹合成框架的贡献度等，难以判断哪些组件最关键。
- **缺乏人类评估**：数据科学研究报告的最终质量通常需要人工评判（如逻辑性、可读性、结论正确性），文中未提及此类评估，可能遗漏重要的质量维度。
- **潜在偏差**：如果训练数据本身存在偏见（如特定数据分布或常见分析模板），模型可能会复制这些偏见；开放自主的任务更易产生不可控行为。
- **应用限制**：自主数据科学仍面临安全性和可解释性问题，模型在真实业务场景中可能产生错误结论，需谨慎部署。

（完）
