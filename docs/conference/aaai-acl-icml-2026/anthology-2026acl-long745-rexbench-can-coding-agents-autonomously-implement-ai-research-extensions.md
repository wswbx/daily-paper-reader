---
title: "RExBench: Can coding agents autonomously implement AI research extensions?"
title_zh: RExBench：编码智能体能自主实现AI研究扩展吗？
authors: "Nicholas Edwards, Yukyung Lee, Yujun Audrey Mao, Yulu Qin, Sebastian Schuster, Najoung Kim"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.745.pdf"
tags: ["query:ar"]
score: 9.0
evidence: 评估编码智能体自主实现研究扩展的基准
tldr: 该论文提出RExBench，一个用于评估编码智能体是否能够自主实现AI研究扩展的基准。它包含12篇研究论文的现实扩展任务，每个任务都需要基于现有论文和代码库实现新假设。RExBench对数据污染具有鲁棒性，是自主研究能力评估的重要进展。实验揭示了当前智能体在理解研究指令和复现复杂扩展上的局限性。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1647, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1632, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1642, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1648, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 713, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1563, \"height\": 623, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1644, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 760, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 784, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.745/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1634, \"height\": 314, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1663, \"height\": 1419, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 697, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 693, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 699, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1640, \"height\": 1940, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1647, \"height\": 1818, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1381, \"height\": 583, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1660, \"height\": 682, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1664, \"height\": 2003, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1664, \"height\": 2005, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1663, \"height\": 1765, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1666, \"height\": 1737, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1665, \"height\": 1783, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1659, \"height\": 1838, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1662, \"height\": 1764, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1657, \"height\": 1803, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1659, \"height\": 1690, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1660, \"height\": 1669, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1660, \"height\": 1707, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1657, \"height\": 1764, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1658, \"height\": 1690, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1662, \"height\": 1725, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1664, \"height\": 1762, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.745/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1657, \"height\": 1688, \"label\": \"Table\"}]"
motivation: 研究扩展是实现是自主研究系统的关键能力，但缺乏评估基准。
method: 构建包含12篇论文扩展任务的基准RExBench，每个任务附带专家指令。
result: 基准揭示了当前编码智能体在自主实现研究扩展上的不足。
conclusion: RExBench为自主研究智能体的能力评估提供了标准平台。
---

## Abstract
Agents based on Large Language Models (LLMs) have shown promise for performing sophisticated software engineering tasks autonomously. In addition, there has been progress towards developing agents that can perform parts of the research pipeline in machine learning and the natural sciences. We argue that research extension and its implementation is a critical capability for such systems, and introduce RExBench to support the evaluation of this capability. RExBench is a benchmark consisting of realistic extensions of 12 research papers that aim to investigate novel research hypotheses. Each task is set up as an extension to an existing research paper and codebase, accompanied by domain expert-written instructions. RExBench is robust to data contamination, and supports an automatic evaluation infrastructure that executes agent outputs to determine whether the success criteria are met. We use this benchmark to evaluate 12 LLM agents implemented using two different frameworks: aider and OpenHands. We find that all agents fail to autonomously implement the majority of the extensions, with the best agent at around 33% success rate. Although the success rate improves with additional human-written hints, the best performance under this setting remains below 44%. This indicates that current agents are still short of being able to handle realistic research extension tasks without substantial human guidance.

---

## 论文详细总结（自动生成）

# RExBench 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）智能体在自主完成复杂软件工程任务上展现出潜力，但在科学研究自动化方面，尤其是“研究扩展”——即基于现有论文提出新假设并实现代码实验——这一关键能力尚缺乏系统性评估。
- **背景问题**：
  - 现有基准（如 PaperBench）主要评估论文复现（replication），而非新颖扩展（extension），且存在数据污染风险（复现代码可能已出现在训练数据中）。
  - 研究扩展的实现需要理解原始论文与代码库，自主规划并编写代码执行新假设，是迈向全自主科研系统的重要一步。
- **整体目标**：提出 **RExBench**，一个专门用于评估 LLM 智能体能否自主实现假设驱动型研究扩展的基准，填补该领域评估空白。

## 2. 论文提出的方法论

- **核心思想**：构建一组基于真实已发表论文的“研究扩展”任务。每个任务包括：
  - 原始研究论文（PDF 和 Markdown 格式）
  - 原始代码库（可复现原论文结果）
  - 领域专家撰写的扩展指令（高量级、仅给出目标和方法概要，不提供实现细节）
- **任务定义**：智能体需根据指令修改代码库，生成新的实验结果，输出为 git 补丁文件。
- **关键技术细节**：
  - **自动评估基础设施**：在 OpenStack 虚拟机上运行，使用 Apptainer 容器，保证硬件与依赖一致；随机种子固定以减少变异。
  - **成功评判标准**：执行智能体修改后的代码，将数值结果与黄金实现（gold implementation）的结果进行对比。若任务有输出的随机性，则采用5次运行的均值±2标准差作为容忍范围。
  - **数据污染防护**：所有扩展任务均为全新，黄金实现存储在私有 Bitbucket 仓库，不在公共网络上；评估脚本也不对智能体开放。
- **无需复杂公式**：整个过程是代码生成→执行→数值比对，无额外数学算法。

## 3. 实验设计

- **使用的数据集 / 场景**：RExBench 本身包含 12 个研究扩展任务，覆盖 NLP 和 AI 多个子领域（按类型分为模型、算法、数据、评估修改）。例如：WinoDict（替换目标单词为英语词汇并测试频率效应）、Othello（更改游戏状态表示）、COGS（移除早停训练）等。每个任务基于一篇或多篇已发表论文及配套代码库。
- **基准（Benchmark）**：即 RExBench 自身，所有智能体在同一组任务上比较。
- **对比的方法（智能体组合）**：
  - 两个代理框架：**aider**（非迭代、一次性输出补丁）和 **OpenHands**（多轮交互、支持 bash 和文件操作）。
  - 六种 LLM 骨干：Claude 4 Sonnet / 3.7 Sonnet、GPT-5、o1、o4-mini、DeepSeek-R1。后续还额外测试了 Claude 4.5 Opus。
  - 共评估 12 种智能体组合（2 框架 × 6 模型）。
- **实验设置**：
  - 每个智能体对每个任务运行 5 次（因随机变异）。
  - 输入包括原始论文、代码库、扩展指令；智能体在独立环境中完成任务，输出补丁文件。
  - 还设计了两种提示级别实验（信息定位提示、逐步实现提示），以检验任务的可解性并诊断困难点。

## 4. 资源与算力

- **硬件环境**：根据任务不同，使用不同类型的 GPU（如 K80、A100）或仅 CPU。表 3 列出了每个任务的实例类型（如 CheckEval 仅 CPU，COGS 用 K80，多数任务用 A100）和黄金实现运行时长（最长 6 小时）。
- **计算集群**：实验在波士顿大学研究计算服务（SCC）以及新英格兰研究云（NERC）提供的共享计算集群上执行。
- **总算力估计**：附录指出，包括初步实验和失败重试在内，总计算量约为报告结果的 4–5 倍。但未给出精确 GPU 数量或总时长。
- **成本分析**：表 7 给出了各智能体每任务平均开支（如 OpenHands+Claude 4 Sonnet 约 $5.21，aider+DeepSeek-R1 约 $0.02），总成本最高为 OpenHands+Claude 4 Sonnet 约 $937。

## 5. 实验数量与充分性

- **实验组数**：
  - 主实验：12 智能体 × 12 任务 × 5 次 = 720 次独立运行。
  - 提示实验：针对所有智能体在两种提示水平下重复类似运行。
  - 额外实验：对 Claude 4.5 Opus 进行全量评估（包括提示实验）。
  - 消融分析：检查执行成功率、文件召回率，以及通过混合效应模型分析任务难度因素。
- **充分性**：
  - 覆盖了多个前沿 LLM 和两种主流的开源智能体框架。
  - 每个任务重复 5 次以控制方差。
  - 提供了多维度指标（最终成功率、执行成功率、文件召回率）。
  - 对错误模式进行了分类统计（表 9、10）和定性分析。
- **潜在的公平性**：所有智能体使用相同输入，评估环境完全隔离，随机种子固定。但任务指令由论文作者编写，可能对特定框架/模型存在潜在偏向（如 OpenHands 更适合多轮交互）。作者已承认这一点，但未明确测试指令偏差。

## 6. 论文的主要结论与发现

- **核心发现**：当前所有 LLM 智能体在 RExBench 上都表现不佳，最高平均最终成功率仅为 **33%**（OpenHands + Claude 4 Sonnet）。带提示的实验最高提升至 **44%**（OpenHands + Claude 4 Sonnet 或 GPT-5）。
- **模型差异**：
  - Claude 4 Sonnet 和 GPT-5 表现最优；o1 和 DeepSeek-R1 接近 0% 成功率。
  - 更强模型往往产生更多“隐式错误”（代码可执行但数值不匹配），此类错误更难调试。
- **错误模式**：
  - 显式错误：Python 值错误、空补丁（尤见于 aider+弱模型）、执行超时。
  - 隐式错误：实现逻辑错误、数值偏差、过度编辑（添加多余修改）。
- **影响因素**：实现努力（代码变更行数）是唯一显著负相关因素（β = -0.038, p < 0.01）。代码库大小、论文引用数等影响不显著。
- **迭代设计重要性**：OpenHands（多轮交互）普遍优于 aider（非迭代），显示逐步调试能力的关键性。

## 7. 优点

- **新颖性与真实性**：聚焦“研究扩展”而非“复现”，更贴近真实科研实践；扩展任务由领域专家设计，确保合理性和挑战性。
- **数据污染免疫**：所有扩展及其黄金实现仅存在于私有存储库，无需担心模型记忆。
- **自动评估可靠性**：通过容器化、固定随机种子、多范围容忍机制，保证评估公平且可重复。
- **多维度指标**：最终成功、执行成功、文件召回三个指标从不同角度刻画智能体能力。
- **开放与可扩展**：发布平台接受社区贡献（https://rexbench.com），鼓励更广泛覆盖。
- **成本/效能分析与可操作建议**：提供帕累托前沿图，并给出具体建模建议（如增加迭代、添加草稿板、防止过度编辑等）。

## 8. 不足与局限

- **任务范围有限**：仅包含 12 个 NLP/AI 领域任务，缺乏跨学科多样性（如化学、生物学）。领域专家编写指令，可能带有特定偏好。
- **指令过于明确**：为便于自动评估，指令将扩展的测试方式和约束写得非常详细，与实际科研中高度开放的扩展（如“试试 X 方法”）存在差距，可能高估智能体在真实场景下的自主性。
- **缺乏过程级指标**：仅依赖最终输出，未设置中间里程碑检查，导致隐式错误难以定位，也无法防止奖励黑客行为（生成正确数字但逻辑错误）。
- **任务数量有限**：尽管每个任务包含高复杂度，但 12 个任务不足以精确区分性能相近的模型（如 Claude 4 Sonnet 与 GPT-5 差异不显著）。
- **框架/模型选择有限**：仅测试了 aider 和 OpenHands，未涵盖其他新兴框架（如 CodeAct、SWE-agent）；LLM 仅限闭源前沿模型和 DeepSeek-R1，未涉及其他开源模型（如 Llama-3、Qwen）。
- **计算开销与碳排放**：未报告总 GPU 小时数或碳排放，不利于可重复性和绿色 AI 讨论。

（完）
