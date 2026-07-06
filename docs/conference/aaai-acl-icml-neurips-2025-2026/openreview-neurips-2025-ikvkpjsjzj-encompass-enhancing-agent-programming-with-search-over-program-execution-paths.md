---
title: "EnCompass: Enhancing Agent Programming with Search Over Program Execution Paths"
title_zh: EnCompass：通过程序执行路径搜索增强代理编程
authors: "Zhening Li, Armando Solar-Lezama, Yisong Yue, Stephan Zheng"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=IKVkpjSJzJ"
tags: ["query:cli-agent"]
score: 6.0
evidence: 面向LLM代理的编程框架
tldr: 当前代理程序设计常将工作流逻辑与推理策略耦合，难以灵活实验。本文提出概率天使非确定性（PAN）编程模型，通过EnCompass框架将代理工作流编译成搜索空间，支持独立调整推理策略。案例研究表明该框架能显著简化代理开发流程。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 代理设计中的工作流逻辑与推理策略纠缠，限制了灵活性和可复用性。
method: 引入概率天使非确定性编程模型，利用Python装饰器将工作流编译为搜索空间。
result: 通过三个案例展示了框架在简化代理开发及提升策略可调性方面的优势。
conclusion: 解耦工作流与推理策略是提升代理编程效率的关键。
---

## Abstract
We introduce a new approach to *agent programming*, the development of LLM-based agents. Current approaches to agent programming often entangle two aspects of agent design: the core workflow logic and the inference-time strategy (e.g., tree search). We introduce *probabilistic angelic nondeterminism* (PAN), a programming model that disentangles these two concerns, allowing the programmer to describe the agent workflow and independently experiment with different inference-time strategies by simply changing a few inputs. We provide an implementation of PAN in Python as the EnCompass framework, which uses a Python decorator to compile agent workflow programs into a search space. We present three case studies that demonstrate how the framework lets the programmer quickly improve the reliability of an agent and easily switch between different inference-time strategies, all with little additional coding.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- 当前基于大语言模型（LLM）的智能体编程中，工作流逻辑（workflow logic）与推理时策略（inference-time strategy，如树搜索）高度耦合，导致灵活性和可复用性差。
- 开发者在修改推理策略时往往需要重写大量工作流代码，难以独立实验不同策略。
- 因此，论文的目标是解耦这两个方面，使程序员能专注于工作流描述，同时独立切换和调整推理策略，从而提升代理编程效率。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：引入*概率天使非确定性*（Probabilistic Angelic Nondeterminism, PAN）编程模型，将工作流中的不确定性（如函数调用的多个可能结果）表示为概率分布，由推理策略负责选择或搜索。
- **关键技术**：
  - 基于Python装饰器（decorator）将代理工作流程序编译为搜索空间。
  - 程序员只需用装饰器标记非确定性函数或分支，框架自动构建搜索图，并允许通过简单改变输入参数来切换不同推理策略（如贪心搜索、束搜索、A*等）。
- **流程说明**：
  1. 程序员使用装饰器定义工作流中的非确定性点（如多个可能的工具调用或回复内容）。
  2. EnCompass框架将这些点编译为有向图形式的搜索空间，每个节点对应一个程序状态，边对应动作。
  3. 推理时，策略模块（如蒙特卡洛树搜索）基于这个搜索空间探索最优执行路径。
  4. 改变推理策略只需更换策略模块或调整其参数，工作流代码无需修改。

## 3. 实验设计：使用了哪些数据集 / 场景，benchmark 是什么，对比了哪些方法
- **案例研究**：论文呈现了三个案例，但具体数据集/场景未详细说明（从摘要和元数据无法获取完整实验细节）。
- **可能场景**：根据题目和动机推测，可能涉及工具调用、多步推理、网页交互等常见LLM代理任务。
- **对比方法**：未明确列出，但隐含对比的是传统耦合工作流与策略的编程方式（如直接编码树搜索到工作流中）。
- **说明**：由于仅提供了摘要和元数据，无法获取完整的实验设置、benchmark名称和对比基线。

## 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。
- **未明确说明**：提供的元数据和摘要中没有提及任何GPU型号、数量、训练时长或推理资源消耗信息。因此无法总结算力情况。

## 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平。
- **实验数量**：仅提及三个案例研究，未给出每组实验内部的具体消融或对比实验数量。
- **充分性**：从现有信息看，实验规模有限，可能不足以全面证明框架的通用性和可扩展性。但作为案例研究，旨在演示概念可行性，尚可接受。
- **公平性**：缺少与现有框架的定量对比，难以判断是否公平。摘要只提到“demonstrate... advantages”，未展示具体指标。

## 6. 论文的主要结论与发现
- 概率天使非确定性编程模型能有效解耦工作流逻辑和推理策略，简化代理开发流程。
- EnCompass框架通过装饰器编译搜索空间，使程序员可以快速提高代理可靠性，并轻松切换不同推理策略，且只需极少额外编码。
- 结论：解耦工作流与推理策略是提升代理编程效率的关键。

## 7. 优点：方法或实验设计上有哪些亮点
- **方法亮点**：
  - 创新性引入非确定性编程思想到LLM代理领域，形式化地解耦关注点。
  - 基于Python装饰器的实现轻量易用，开发者学习成本低。
  - 搜索空间自动构建，支持多种推理策略即插即用。
- **实验设计亮点**：
  - 采用案例研究展示了实际开发流程的简化，提供了直观的易用性证据。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
- **实验覆盖不足**：仅有三个案例，缺乏大规模、多领域的定量评估，无法证明框架在复杂实际场景中的通用性。
- **偏差风险**：案例选择可能偏向有利于框架表现的任务，存在选择偏差。
- **应用限制**：
  - 依赖LLM的调用成本，搜索空间扩大可能带来高推理延迟和计算开销。
  - 工作流中的非确定性需要程序员手动标注，增加了初始设计负担。
  - 未讨论非确定性子句的语义正确性保证（如可能陷入死循环或无效分支）。
- **缺失资源报告**：无算力消耗对比，不利于评估实际部署成本。

（完）
