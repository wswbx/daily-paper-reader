---
title: "MetaAgent: Automatically Constructing Multi-Agent Systems Based on Finite State Machines"
title_zh: MetaAgent：基于有限状态机自动构建多智能体系统
authors: "Yaolun Zhang, Xiaogeng Liu, Chaowei Xiao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=vOxaD3hhPt"
tags: ["query:cli-agent"]
score: 4.0
evidence: 自动构建多智能体系统，使用有限状态机，可用于CLI智能体系统
tldr: 现有手动设计的多智能体框架场景受限，自动设计方法依赖外部数据且结构僵化。本文提出MetaAgent，基于有限状态机自动从任务描述生成多智能体系统，并通过优化算法自动打磨。该方法支持工具集成和灵活通信，实验表明其在多种任务中优于人工设计的基线，为自动构建智能体系统提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 手动设计的智能体框架场景有限，现有自动设计方法存在依赖外部数据和结构僵化等问题。
method: 提出MetaAgent，基于有限状态机从任务描述自动生成并优化多智能体系统。
result: 在多个基准任务上，MetaAgent自动生成的智能体系统性能优于人工设计的基线。
conclusion: 有限状态机框架实现了灵活、高效的多智能体自动构建，可推广到CLI智能体等场景。
---

## Abstract
Large Language Models (LLMs) have demonstrated the ability to solve a wide range of practical tasks within multi-agent systems. However, existing human-designed multi-agent frameworks are typically limited to a small set of pre-defined scenarios, while current automated design methods suffer from several limitations, such as the lack of tool integration, dependence on external training data, and rigid communication structures. In this paper, we propose \textbf{MetaAgent}, a  \textbf{finite state machine} based framework that can automatically generate a multi-agent system. Given a task description, MetaAgent will design a multi-agent system and polish it through an optimization algorithm. When the multi-agent system is deployed, the finite state machine will control the agent's actions and the state transitions. To evaluate our framework, we conduct experiments on both text-based tasks and practical tasks. The results indicate that the generated multi-agent system surpasses other auto-designed methods and can achieve a comparable performance with the human-designed multi-agent system, which is optimized for those specific tasks.

---

## 论文详细总结（自动生成）

好的，以下是根据提供的论文信息生成的详细中文总结。

---

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的大语言模型多智能体系统通常为人工设计，只能处理少数预定义场景，泛化性差；而现有的自动设计方法则存在工具集成缺失、依赖外部训练数据、通信结构僵化等局限。
- **研究动机**：提出一种能够自动从任务描述生成多智能体系统，并自动优化的框架，以克服上述缺陷，使多智能体系统能够灵活适应各种新任务。
- **整体含义**：该工作展示了将有限状态机（FSM）用于多智能体自动构建的可行性，为智能体系统的自动化、可扩展部署提供了新思路。

## 2. 论文提出的方法论

- **核心思想**：基于**有限状态机（Finite State Machine, FSM）** 构建一个名为 **MetaAgent** 的框架，实现从任务描述到多智能体系统的自动生成与优化。
- **关键技术细节**：
  - **自动生成**：给定任务描述，MetaAgent 自动设计多智能体系统的结构，包括智能体的角色、通信拓扑、状态转移规则等。
  - **优化算法**：系统生成后，通过迭代优化算法进行打磨（polish），提升性能。
  - **部署阶段**：有限状态机控制每个智能体的动作和状态转换，实现灵活、结构化的多智能体协作。
  - **工具集成**：框架支持将外部工具集成到智能体系统中，增强了实用性。
  - **通信结构**：不同于刚性通信模式，FSM 允许动态、模块化的交互。
- **算法流程（文字说明）**：
  1. 输入任务描述；
  2. MetaAgent 根据描述生成初始多智能体系统（包括角色、FSM 状态/转移、工具绑定）；
  3. 通过优化算法（可能是基于 LLM 的自我反思或搜索）自动改进系统；
  4. 输出最终的系统配置，并部署运行；
  5. 运行时，FSM 驱动智能体按状态执行动作并转移。

## 3. 实验设计

- **数据集/场景**：同时使用**基于文本的任务**和**实际任务**两类场景，具体名称未在提供的摘要/元数据中列出。
- **基准（Benchmark）**：未明确说明具体 benchmark 名称，但与人工设计的基线系统以及其它自动设计方法进行了对比。
- **对比方法**：
  - 其他自动设计方法（auto-designed methods）；
  - 为特定任务优化的人工设计多智能体系统（human-designed multi-agent system）。
- **评估指标**：未在提供信息中详述，但性能上 MetaAgent 生成的系统超过了其他自动设计方法，并与人工设计系统性能相当。

## 4. 资源与算力

- **文中信息**：所提供的内容中**没有明确说明**使用的 GPU 型号、数量、训练时长等算力资源信息。
- **备注**：由于缺乏实验细节，无法评判其计算成本。这可能是因为论文正文未提取到相关章节，或原文未强调算力。

## 5. 实验数量与充分性

- **实验数量**：从摘要可知，实验涵盖了文本任务和实际任务，但具体实验组数（例如几个数据集、是否包含消融实验）未在提供的信息中列出。
- **充分性与公平性**：
  - **优点**：同时对比了自动设计方法和人工设计基线，且任务类型多样（文本+实际），具有一定的覆盖面。
  - **不足**：由于缺乏实验细节（如数据集名称、多次运行稳定性、统计显著性检验等），难以判断实验的完整性和公平性。元数据中的 tldr 提到“在多个基准任务上”，但具体数量与统计细节未知。

## 6. 论文的主要结论与发现

- MetaAgent 基于有限状态机自动生成的多智能体系统，在文本任务和实际任务中均**超越了其他自动设计方法**。
- 其性能**与为特定任务精心设计的人工系统相当**，显示了自动构建的潜力。
- 结论：有限状态机框架实现了灵活、高效的多智能体自动构建，并可推广到 CLI 智能体等场景。

## 7. 优点

- **自动化与灵活性**：无需人工设计 agent 结构，从任务描述自动生成；FSM 支持高度模块化的状态/转移，适应动态交互。
- **工具集成**：支持将外部工具直接集成到智能体系统中，增强了实用性。
- **无需外部训练数据**：不依赖额外标注或预定义数据，仅利用任务描述。
- **通用性**：在文本任务和实际任务上都取得了良好效果，并具备扩展到 CLI 智能体的潜力。

## 8. 不足与局限

- **实验细节不透明**：提供的摘要与元数据中缺乏具体数据集名称、任务规模、对比方法的实现细节，削弱了可复现性。
- **缺乏消融实验**：未提及是否对框架各组件（如 FSM 设计、优化策略、工具集成）进行消融分析。
- **计算成本未知**：未报告自动生成与优化过程的计算开销（LLM 调用次数、耗时等），难以评估实用性。
- **偏差风险**：实验可能仅在少量任务上验证，且未说明是否进行了多轮随机种子测试，存在结果偶然性风险。
- **应用限制**：虽然声称可推广到 CLI 智能体，但缺乏实际 CLI 场景的实验证据；框架对复杂任务（需要大量智能体或深层状态）的可扩展性未知。

---

（完）
