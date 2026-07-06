---
title: "Rethinking Stateful Tool Use in Multi-Turn Dialogues: Benchmarks and Challenges"
title_zh: 重新思考多轮对话中的有状态工具使用：基准与挑战
authors: "Hongru Wang, Wenyu Huang, Yufei Wang, Yuanhao Xi, Jianqiao Lu, Huan Zhang (张欢), Nan Hu, Zeming Liu, Jeff Z. Pan, Kam-Fai Wong"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.284.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: 多轮对话中有状态工具使用的基准，与理解自然语言命令的CLI智能体直接相关
tldr: 现有工具使用基准多聚焦于无状态单轮交互，忽略多轮应用中的状态特性。本文构建DialogTool数据集，涵盖工具创建、利用和响应三个阶段六个关键任务，并搭建虚拟移动评估环境VirtualMobile。该基准系统评估了语言模型在多轮对话中的工具使用能力，揭示了状态化交互带来的新挑战。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.284/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 787, \"height\": 718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.284/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 756, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.284/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 813, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.284/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 504, \"height\": 762, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.284/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 802, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.284/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1661, \"height\": 1185, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.284/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1662, \"height\": 1182, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.284/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1506, \"height\": 443, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.284/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 682, \"height\": 402, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.284/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1422, \"height\": 648, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.284/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 811, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.284/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 762, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.284/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1491, \"height\": 904, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.284/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1654, \"height\": 510, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.284/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1051, \"height\": 343, \"label\": \"Table\"}]"
motivation: 现有基准忽略了多轮对话中工具使用的状态特性，导致评估不全面。
method: 构建DialogTool多轮对话数据集，包含六个关键任务，并搭建虚拟移动评估环境。
result: 实验揭示了语言模型在多轮有状态工具使用中的显著不足。
conclusion: 该基准为评估和改善智能体的工具使用能力提供了重要参考。
---

## Abstract
Existing benchmarks that assess Language Models (LMs) as Language Agents (LAs) for tool use primarily focus on stateless, single-turn interactions or partial evaluations, such as tool selection in a single turn, overlooking the inherent stateful nature of interactions in multi-turn applications. To fulfill this gap, we propose DialogTool, a multi-turn dialogue dataset with stateful tool interactions considering the whole life cycle of tool use, across six key tasks in three stages: 1) tool creation ; 2) tool utilization : tool awareness, tool selection, tool execution; and 3) role-consistent response : response generation and role play. Furthermore, we build VirtualMobile – an embodied virtual mobile evaluation environment to simulate API calls and assess the robustness of the created APIs. Taking advantage of these artifacts, we conduct comprehensive evaluation on 13 distinct open- and closed-source LLMs and provide detailed analysis at each stage, revealing that the existing state-of-the-art LLMs still cannot perform well to use tools over long horizons .

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有评估语言模型作为工具使用智能体的基准大多聚焦于无状态、单轮交互，或仅评估单轮中的工具选择等局部能力，忽视了多轮对话中工具使用的**状态性**（stateful）——即历史对话、已创建的工具、已执行的API调用会影响后续轮次的行为。
- **整体含义**：为了弥补这一空白，论文提出了**DialogTool**数据集，构建了涵盖工具使用全生命周期（创建、利用、响应）的六个关键任务，并搭建了虚拟移动评估环境**VirtualMobile**，系统性地评估多轮有状态工具使用的挑战。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将有状态工具使用的完整过程划分为三个大阶段、六个子任务：
  1. **工具创建（Tool Creation）**：根据用户需求生成新的API函数（包括函数名、参数、文档字符串等）。
  2. **工具利用（Tool Utilization）**：
     - 工具意识（Tool Awareness）：判断当前轮次是否需要调用工具。
     - 工具选择（Tool Selection）：从候选工具中选择正确的工具。
     - 工具执行（Tool Execution）：生成正确的JSON格式调用参数。
  3. **角色一致响应（Role-Consistent Response）**：
     - 响应生成（Response Generation）：基于工具返回结果生成自然语言回复。
     - 角色扮演（Role Play）：在对话中保持预设角色的一致性（如语气、风格）。
- **数据集构建**：基于**ToolBench**作为种子，通过GPT-4生成多轮对话场景，并人工筛选和修正，得到**1,000条多轮对话**，涵盖17个垂直领域、744种API。
- **VirtualMobile环境**：模拟真实移动设备上的API调用，支持基于状态（如已安装应用、历史操作）的鲁棒性测试。该环境可验证工具调用是否导致预期状态变化。

## 3. 实验设计

- **使用的数据集/场景**：
  - **DialogTool**数据集：包含1,000个多轮对话，每个对话平均约3.8轮。
  - **VirtualMobile**环境：用于模拟API执行和状态追踪。
- **Benchmark**：论文自身提出的多轮有状态工具使用基准，包含6个子任务评价指标。
- **对比方法**：评估了13种不同的开源和闭源LLM，包括：
  - 闭源：GPT-4、GPT-3.5-turbo、Claude-2等。
  - 开源：LLaMA-2-7B/13B/70B、Mistral-7B、Mixtral-8x7B、ChatGLM-6B、Qwen-7B/14B等。
- **实验设置**：使用few-shot（2-shot）提示，评估每个子任务的准确率或F1等指标。

## 4. 资源与算力

- **论文未明确说明具体算力**（GPU型号、数量、训练时长）。仅提及使用了开源模型的预训练权重进行推理，未进行微调。推断实验在标准学术GPU集群上完成，但未提供细节。

## 5. 实验数量与充分性

- **实验数量**：论文进行了大量对比实验，主要包括：
  - 对13个模型在6个子任务上的整体性能对比（如表3、4、5）。
  - 消融实验：分析工具数量（2/4/6）对工具选择和工具意识的影响（表6）。
  - 错误分析：对模型输出进行分类统计（如参数错误、API不存在等）。
  - 多轮度分析：比较不同轮次（第1轮 vs 后续轮次）的性能变化（图5）。
- **充分性与公平性**：
  - 实验覆盖了多种大小和类型的模型，开源闭环均有。
  - 所有模型使用相同提示模板和评估流程，确保公平。
  - 但仅基于GPT-4生成的数据集，可能存在数据偏差；人工验证降低了偏差但未完全消除。
  - 未进行模型微调或上下文学习调优，仅评估零样本/少样本能力。

## 6. 主要结论与发现

- 现有最先进的LLM（包括GPT-4）在多轮有状态工具使用中表现不佳，尤其在**工具意识**（判断何时需要调用工具）和**角色一致响应**上存在显著差距。
- 随着工具数量增加，所有模型性能下降，尤其是开源模型。
- 模型在多轮交互中容易“遗忘”历史状态（如已创建的工具、之前的选择），导致重复创建或错误调用。
- **工具执行**（参数生成）相对容易，但**工具选择**和**角色扮演**是主要瓶颈。
- 闭源模型普遍优于开源模型，但整体上仍有较大提升空间。

## 7. 优点

- **创新性**：首次系统性地定义和评估多轮对话中的有状态工具使用全过程，填补了现有基准的空白。
- **全面性**：数据集覆盖6个子任务，评估粒度细，且提供了虚拟环境用于真实状态模拟。
- **实用性**：构建的VirtualMobile环境可用于测试模型在真实API调用场景下的鲁棒性，便于后续研究。
- **实验设计严谨**：对比了13个模型，进行了多维度分析（轮次、工具数量影响等）。

## 8. 不足与局限

- **数据来源**：完全依赖GPT-4生成数据，可能存在模型特定偏差，尽管有人工修正，但多样性受限。
- **评估指标**：部分子任务（如角色扮演）缺乏客观衡量标准，依赖人工评估或基于GPT-4的自动评估，可能引入噪音。
- **算力细节缺失**：未提供实验资源消耗，不利于复现和成本估计。
- **应用限制**：VirtualMobile环境较为简单，实际移动设备API调用复杂度更高（如异步调用、权限管理），评估场景不够真实。
- **未进行训练/微调**：论文仅评估了现有LLM的零样本/少样本能力，未探索通过专门训练提升性能的方法，结论偏诊断性。
- **多轮长度有限**：平均3.8轮，更长的多轮对话（如10轮以上）下的状态保持挑战可能未被充分揭示。

（完）
