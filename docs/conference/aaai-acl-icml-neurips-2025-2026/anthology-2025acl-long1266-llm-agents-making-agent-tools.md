---
title: LLM Agents Making Agent Tools
title_zh: LLM代理制作代理工具
authors: "Georg Wölflein, Dyke Ferber, Daniel Truhn, Ognjen Arandjelovic, Jakob Nikolas Kather"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.1266.pdf"
tags: ["query:cli-agent"]
score: 6.0
evidence: LLM代理从代码自主创建工具用于任务自动化
tldr: 本文提出ToolMaker框架，该框架能自主将带有代码的论文转化为LLM兼容的工具，通过闭环自我纠正机制实现调试。这解决了LLM代理在生命科学等领域需要大量专业工具时因人类开发者前置实现而受限的问题。实验表明，ToolMaker能有效生成工具并完成任务，推动了自主工具创造的发展。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1266/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 803, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1266/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 811, \"height\": 728, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1266/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1659, \"height\": 774, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1266/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 661, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.1266/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1323, \"height\": 1088, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 797, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1642, \"height\": 528, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 789, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1640, \"height\": 524, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1639, \"height\": 528, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1634, \"height\": 726, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1100, \"height\": 2317, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1101, \"height\": 2313, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1100, \"height\": 2317, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1101, \"height\": 2314, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1100, \"height\": 2315, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1101, \"height\": 2314, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.1266/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1101, \"height\": 2314, \"label\": \"Table\"}]"
motivation: LLM代理因工具需人工实现而受限，尤其在生命科学等需大量专业工具的领域。
method: 提出ToolMaker框架，根据GitHub URL和任务描述自动安装依赖、生成代码，并利用闭环自我纠正进行调试。
result: ToolMaker能自主将论文代码转化为可用工具，并在实际任务中表现良好。
conclusion: ToolMaker实现了自动化工具创造，扩展了LLM代理的应用范围。
---

## Abstract
Tool use has turned large language models (LLMs) into powerful agents that can perform complex multi-step tasks by dynamically utilising external software components. However, these tools must be implemented in advance by human developers, hindering the applicability of LLM agents in domains demanding large numbers of highly specialised tools, like in life sciences and medicine. Motivated by the growing trend of scientific studies accompanied by public code repositories, we propose ToolMaker, an agentic framework that autonomously transforms papers with code into LLM-compatible tools. Given a GitHub URL and short task description, ToolMaker autonomously installs dependencies and generates code to perform the task, using a closed-loop self-correction mechanism for debugging. To evaluate our approach, we introduce a benchmark comprising 15 complex computational tasks spanning various domains with over 100 unit tests to assess correctness and robustness. Our method correctly implements 80% of the tasks, substantially outperforming current state-of-the-art software engineering agents. ToolMaker therefore is a step towards fully autonomous agent-based scientific workflows.

---

## 论文详细总结（自动生成）

# 论文《LLM Agents Making Agent Tools》中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：大型语言模型（LLM）代理通过调用外部工具可以完成复杂多步任务，但现有工具必须由人类开发者预先实现和集成，这严重限制了代理在需要大量高度专业化工具的领域（如生命科学、医学）的应用。
- **背景**：科研领域日益强调可重复性，论文常附带公开代码仓库，这为自主工具生成提供了可能。作者提出让LLM代理自主从论文及代码仓库中生成可复用工具，从而绕过人工干预，向完全自主的科学工作流迈进。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：提出**ToolMaker**框架，根据用户提供的任务描述、论文代码仓库URL及示例调用，自动生成**环境定义**（Docker镜像或bash脚本）和**Python工具函数**，使下游LLM代理能直接调用该函数完成任务。
- **关键技术细节**：
  - **状态模型**：工作流状态由对话历史`h`和环境状态`e`（基于Docker容器）组成。
  - **组件类型**：
    - **LLM调用**：仅更新对话历史。
    - **环境交互**：包括`RUN_BASH_COMMAND`、`READ_FILE`、`WRITE_FILE`、`BROWSE`等读写操作，其中`RUN_IMPLEMENTATION`用于执行候选工具。
    - **代理（Agent）**：将LLM调用与环境交互链式组合，完成特定子任务。
  - **算法流程（Algorithm 1）**：
    1. **环境设置**：利用`INSTALL_REPOSITORY`代理从空白Docker镜像开始，克隆仓库、安装依赖、下载模型等，并记录所有写操作以生成环境定义。
    2. **初始实现**：通过`EXPLORE`代理探索仓库，`PLAN`生成实现步骤，`IMPLEMENT`生成候选Python函数。
    3. **闭环自我改进**：
       - 重置环境至“刚安装”状态，运行候选工具。
       - 用`ASSESS_TOOL_OUTPUT`评估执行结果（是否合理、有无错误）。
       - 若失败，通过`DIAGNOSE_ERROR`收集错误信息并诊断根因，然后`REIMPLEMENT`更新代码，并`SUMMARISE`当前尝试。
       - 循环直至成功或达到限制。
- **执行环境**：基于Docker容器，支持状态检查点恢复和沙箱隔离，保证可重复性和安全性。

## 3. 实验设计

- **数据集/场景**：论文新构建了**TM-Bench**基准，包含15个来自不同科学领域的复杂计算任务，涵盖病理学、放射学、组学、3D视觉、自然语言处理等，每个任务对应一篇学术论文及其代码仓库。
- **基准评估指标**：每个任务提供1个示例调用（用于工具生成）和2–3个测试调用（用于评估泛化性），总共15个任务、42个测试调用、124个单元测试。测试检查返回值结构、值范围、文件存在性及执行错误等。
- **对比方法**：主要对比**OpenHands**（先前在SWE-Bench上达到SOTA的软件工程代理），并适配其生成相同产物。同时进行消融实验：
  - 是否使用论文摘要（gpt-4o生成任务相关摘要）。
  - 使用不同LLM后端（o3-mini、Claude 3.5 Sonnet）。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量及训练时长。主要使用的LLM是**OpenAI gpt-4o**（以及消融中的o3-mini、Claude 3.5 Sonnet），所有工作涉及LLM推理调用和Docker容器内的工具执行。
- 算力消耗以API调用成本衡量：ToolMaker平均每个工具花费**$0.94**，OpenHands平均$0.15。

## 5. 实验数量与充分性

- **主实验**：在15个任务上完成了ToolMaker与OpenHands的完整对比，报告了每个任务的测试通过率、成本、动作次数、token数。
- **消融实验**：
  1. **论文摘要**：对比有无摘要对性能的影响。
  2. **LLM后端**：使用o3-mini、Claude 3.5 Sonnet对比gpt-4o。
- **充分性评估**：
  - 实验覆盖多个学科（医学、成像、组学、NLP等），任务难度从简单到复杂（多步工具）。
  - 单元测试数量充足（124个），且测试用例与示例分离，避免过拟合。
  - 对比方法OpenHands也是当前SOTA，且消融实验考虑了LLM变体，总体设计较客观。但未与其他工具生成方法（如CRAFT、CREATOR）直接对比，因为这些方法不支持复杂任务和系统交互。

## 6. 主要结论与发现

- **ToolMaker显著优于OpenHands**：在TM-Bench上正确实现了**80%**（12/15）的任务，而OpenHands仅完成**20%**（3/15）。
- **多步工具能力**：ToolMaker能够创建需要多个步骤的复杂工具（如先特征提取再训练分类模型），OpenHands在环境设置阶段常失败。
- **论文摘要的效用**：加入摘要并不提升准确率，但减少了所需动作次数和自纠正迭代次数（降低成本和token量）。
- **LLM后端的影响**：使用o3-mini降低了成本但也降低了性能，Claude 3.5 Sonnet在OpenHands上表现不如gpt-4o。
- **自纠正机制的有效性**：闭环自我改进是成功的关键，ToolMaker平均每工具执行21.8次动作、多个迭代。

## 7. 优点

- **创新性**：首次提出从论文代码仓库到LLM工具的端到端自动化，突破了现有工具创建方法仅限于简单Python函数的局限。
- **鲁棒性**：通过Docker容器实现环境隔离与状态回滚，保证可重复性；自纠正循环能自动诊断和修复安装及实现错误。
- **评估全面**：构建了多学科、多难度的基准，包含124个单元测试，并提供了详细的消融分析。
- **实用性**：对科研人员极有意义，能大幅降低使用专业工具的技术门槛，推动自主科学发现。

## 8. 不足与局限

- **依赖代码仓库质量**：假设仓库结构良好且有文档，实际中可能难以安装或使用。
- **评估范围限制**：15个任务规模较小，单元测试无法覆盖所有真实场景的边界情况。
- **安全风险**：自动创建生物化学工具可能被滥用；缺少安全护栏和伦理审查。
- **物理实验缺失**：仅覆盖计算任务，无法处理需要实际实验的科研环节。
- **外部因素影响**：依赖固定commit，但仓库可能更新或删除，影响长期可复现性。
- **无人类验证**：生成的工具在高风险应用（如临床研究）中需要额外验证。

（完）
