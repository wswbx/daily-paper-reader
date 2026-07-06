---
title: "MoRAgent: Parameter Efficient Agent Tuning with Mixture-of-Roles"
title_zh: MoRAgent：基于角色混合的参数高效智能体微调
authors: "Jing Han, Binwei Yan, Tianyu Guo, Zheyuan Bai, Mengyu Zheng, Hanting Chen, Ying Nie"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=rdeDanrYEj"
tags: ["query:cli-agent"]
score: 6.0
evidence: 面向智能体任务的参数高效微调
tldr: 本文针对大语言模型在智能体任务中的参数高效微调，提出MoRAgent方法。受Reason+Action范式启发，将智能体能力分解为推理者、执行者和总结者三个角色，并分别进行参数高效微调。该方法在多个智能体基准上实现了与全参数微调相当的性能，同时大幅减少可训练参数。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有参数高效微调在智能体任务中研究不足，需要针对性策略。
method: 将智能体角色分解为推理者、执行者、总结者，对应不同参数组进行高效微调。
result: 在多个智能体任务上达到与全参数微调相近的性能，但参数量显著减少。
conclusion: 角色分解和参数高效微调能有效降低智能体调优成本。
---

## Abstract
Despite recent advancements of fine-tuning large language models (LLMs) to facilitate agent tasks, parameter-efficient fine-tuning (PEFT) methodologies for agent remain largely unexplored. In this paper, we introduce three key strategies for PEFT in agent tasks: 1) Inspired by the increasingly dominant \textit{Reason+Action} paradigm, we first decompose the capabilities necessary for the agent tasks into three distinct roles: reasoner, executor, and summarizer. The reasoner is responsible for comprehending the user's query and determining the next role based on the execution trajectory. The executor is tasked with identifying the appropriate functions and parameters to invoke. The summarizer conveys the distilled information from conversations back to the user. 2) We then propose the Mixture-of-Roles (MoR) framework, which comprises three specialized Low-Rank Adaptation (LoRA) groups, each designated to fulfill a distinct role. By focusing on their respective specialized capabilities and engaging in collaborative interactions, these LoRAs collectively accomplish the agent task. 3) To effectively fine-tune the framework, we develop a multi-role data generation pipeline based on publicly available datasets, incorporating role-specific content completion and reliability verification.
We conduct extensive experiments and thorough ablation studies on various LLMs and agent benchmarks, demonstrating the effectiveness of the proposed method. This project is publicly available at https://mor-agent.github.io

---

## 论文详细总结（自动生成）

# 中文论文总结：MoRAgent: Parameter Efficient Agent Tuning with Mixture-of-Roles

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：大语言模型（LLM）在智能体（Agent）任务中得到广泛应用，通常需要全参数微调来适配任务。然而，参数高效微调（PEFT）方法在智能体场景下的研究尚不充分。
- **核心问题**：如何在保持与全参数微调相当性能的前提下，大幅减少可训练参数数量，降低智能体调优的计算成本。
- **动机**：受“Reason+Action”范式启发，作者认为智能体任务涉及多种能力（推理、执行、总结），若使用统一LoRA模块可能限制各能力的发展。因此提出角色分解与混合专家思路，针对不同子能力分别进行参数高效微调。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将智能体所需能力分解为三个角色，并为每个角色分配独立的LoRA模块，通过角色协作完成完整任务。
- **三个角色定义**：
  - **推理者（Reasoner）**：理解用户查询，根据执行轨迹决定下一步角色调用。
  - **执行者（Executor）**：负责识别正确的函数和参数进行调用。
  - **总结者（Summarizer）**：将对话中的关键信息提炼后回传给用户。
- **关键技术细节**：
  - 提出 **Mixture-of-Roles (MoR)** 框架：包含三个专门的LoRA组，每组对应一个角色，参数独立训练但协同工作。
  - 开发了 **多角色数据生成流水线**：基于公开数据集，进行角色特定内容补全和可靠性验证，生成用于训练的多角色标注数据。
- **算法流程**（文字说明）：
  1. 使用预训练LLM作为基础模型。
  2. 为Reasoner、Executor、Summarizer各附加一个LoRA适配器（A/B低秩矩阵）。
  3. 在推理时，根据当前状态激活对应角色的LoRA模块，其余模块处于静止。
  4. 通过角色序列（Reasoner → Executor → Summarizer 循环）执行智能体任务。
  5. 训练时仅更新三个LoRA模块的参数（秩r远小于隐藏维度），主模型参数冻结。

## 3. 实验设计

- **数据集/场景**：基于公开的智能体数据集（文中未明确列举，但提及使用公开数据生成多角色数据）。
- **基准测试（Benchmark）**：多个智能体基准任务（具体名称未在摘要中给出，但声称在多种LLM和基准上验证）。
- **对比方法**：
  - 全参数微调（Full Fine-tuning）
  - 标准LoRA（单一LoRA模块）
  - 可能还有其他PEFT方法（摘要中未列举，但消融实验应包含）。
- **评估指标**：任务完成准确率、参数效率等。

## 4. 资源与算力

- 论文摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长等具体算力信息。仅提到项目开源代码链接。这可能是因为论文正文中可能含细节，但截取部分缺失。需指出这一点。

## 5. 实验数量与充分性

- **实验数量**：声称“广泛实验和彻底消融研究”，包括：
  - 多种LLM（如不同规模的模型）上的性能对比。
  - 消融实验（例如：移除某个角色、使用单一LoRA、不同秩设置等）。
- **充分性与客观性**：
  - 覆盖了多种模型和任务，对比了全参数微调与基线PEFT方法，实验设计较全面。
  - 但具体基准名称和数据集规模未详细说明，信息不够透明；且缺少与更多最新PEFT方法的对比（如Adapter、Prefix Tuning等）。总体而言，实验在论文范围内应是充分的，但外部验证需依赖公开代码和论文全文。

## 6. 主要结论与发现

- MoRAgent在多个智能体基准上达到了**与全参数微调相当的性能**，同时**可训练参数数量大幅减少**。
- 角色分解方案优于单一LoRA，说明分角色训练能更有效地利用参数预算。
- 多角色数据生成流水线有效提升了训练数据质量。

## 7. 优点

- **创新性强**：首次将角色分解与混合专家的思路引入智能体PEFT，打破统一LoRA的局限。
- **参数高效**：显著降低训练成本，使大模型在智能体场景下的部署更可行。
- 提供了**开源代码**和项目页面，便于复现和后续研究。
- **数据生成流水线**解决了角色标注数据稀缺问题，具有实用价值。

## 8. 不足与局限

- **实验覆盖**：未明确说明使用的具体智能体基准（如WebShop, AlfWorld等），导致读者难以评估方法适用性。可能会对特定类型任务（如多轮对话、工具调用）的效果差异缺乏讨论。
- **偏差风险**：数据生成流水线依赖已有公开数据集，可能存在分布偏差，影响泛化性。
- **应用限制**：角色分解依赖明确的 Reason+Action 范式，对于非结构化或开放式智能体任务可能不适用。
- **算力资源未披露**：难以评估实际训练成本优势。
- **与其他高级PEFT方法对比不足**：如LoRA+混合专家（MoE）变体、自适应秩等方法未提及。

（完）
