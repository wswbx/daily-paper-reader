---
title: A Survey of Large Language Model-Based Search Agents
title_zh: 基于大语言模型的搜索智能体综述
authors: "Yunjia Xi, Jianghao Lin, Yongzhao Xiao, Zheli Zhou, Rong Shan, Te Gao, Jiachen Zhu, Weiwen Liu, Yong Yu, Weinan Zhang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.374.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 对基于LLM的搜索智能体进行综述，强调自主信息探索
tldr: 该综述首次系统分析了基于大语言模型的搜索智能体。文章从架构、优化、应用和评估等维度全面梳理现有工作，指出这些智能体能够理解用户意图、进行多轮动态检索，代表自主信息探索的范式转变。以Deep Research为代表的案例展示了其在深度信息挖掘中的潜力。这份调查为自主研究领域中搜索智能体的设计提供了完整参考。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.374/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 836, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.374/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1559, \"height\": 870, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1580, \"height\": 2473, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1574, \"height\": 2557, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1575, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1599, \"height\": 2465, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1600, \"height\": 2196, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1623, \"height\": 2499, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1622, \"height\": 2570, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1626, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1655, \"height\": 2491, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1687, \"height\": 2535, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1655, \"height\": 2553, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.374/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1659, \"height\": 1536, \"label\": \"Table\"}]"
motivation: 搜索智能体正在向自主、动态的信息寻求转变，但缺乏系统性分析。
method: 提出从架构、优化、应用和评估四个维度的分类体系。
result: 总结出关键挑战并指出了未来方向。
conclusion: 该综述为搜索智能体的理解和进一步发展奠定了基础。
---

## Abstract
The advent of Large Language Models (LLMs) has significantly revolutionized web search. The emergence of LLM-based Search Agents marks a pivotal shift towards deeper, dynamic, autonomous information seeking. These agents can comprehend user intentions and environment context and execute multi-turn retrieval with dynamic planning, extending search capabilities far beyond the web. Leading examples like OpenAI’s Deep Research highlight their potential for deep information mining and real-world applications. This survey provides the first systematic analysis of search agents. We comprehensively analyze and categorize existing works from the perspectives of architecture, optimization, application, and evaluation, ultimately identifying critical open challenges and outlining promising future research directions in this rapidly evolving field.

---

## 论文详细总结（自动生成）

# 基于大语言模型的搜索智能体综述：详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：随着大语言模型（LLM）的发展，网络搜索范式经历了从传统搜索到LLM增强搜索（如查询重写、检索增强生成RAG）的演变。然而，这些方法往往是被动的、单轮的或基于规则迭代的，难以应对复杂动态的上下文。为了突破这一瓶颈，研究者开始探索**搜索智能体（Search Agent）**——能够自主理解用户意图、规划搜索策略、执行多轮动态检索并整合多源信息的LLM代理。
- **整体含义**：搜索智能体代表了一种从“信息检索”向“自主信息探索”的范式转变，典型商业应用如OpenAI的Deep Research、Gemini和Perplexity的深度搜索已展示了其在深度信息挖掘和实际部署中的巨大潜力。然而，该领域缺乏系统性综述。本文首次从**搜索结构、优化方法、应用场景、评估体系**四个维度对搜索智能体进行全面分类和分析，并指出关键挑战和未来方向。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将搜索智能体建模为一个迭代的“计划→行动→观察→反思”循环，其任务定义为：给定用户意图\(q\)和上下文\(C\)，智能体经过多步搜索产生观察序列\(O\)，从中选择相关证据\(E\)，最后生成回答\(\hat{y}_q\)。
- **关键技术细节（按维度分）**：
  - **如何搜索（How to Search）**：系统梳理了三种搜索结构：
    - **并行结构**：分解原查询为多个子查询同时执行，如基于分解（decomposition-based）和基于多样化（diversification-based）。
    - **顺序结构**：根据上一步的观察和反思动态决定下一步动作，包括反思驱动（reflection-driven）和主动驱动（proactivity-driven）。
    - **混合结构**：结合并行和顺序，如树状搜索（Tree-based，可并行扩展节点，常用MCTS）和图状搜索（Graph-based，允许回溯和节点动态增减）。
  - **如何优化（How to Optimize）**：分为**免调优**和**基于调优**两类：
    - **免调优**：依赖人工知识和预定义流程，包括单智能体架构（迭代循环、反思链）、多智能体架构（分配不同的规划、搜索、生成角色）和测试时扩展（test-time scaling，如增加搜索轮次、结合推理和搜索的扩展）。
    - **基于调优**：通过监督微调（SFT，蒸馏、自我改进、为RL预热）和强化学习（RL，如PPO、GRPO、Reinforce++）来内化搜索能力。设计多目标奖励函数（正确性、效率、多样性、证据质量、冗余惩罚等），奖励来源包括规则验证（rule-based）、结果奖励模型（ORM）和过程奖励模型（PRM）。常采用SFT预热+RL微调的混合策略。
  - **如何应用（How to Apply）**：
    - **外部应用**：AI助手（聊天机器人、深度研究Deep Research）、电商、金融、代码、医学、生物、化学、科研辅助等。
    - **内部应用**：增强智能体自身的工具使用（agentic search用于工具选择）、记忆检索（复杂意图下在记忆库中搜索）、推理（从内部经验中检索相关经验辅助推理）。
  - **如何评估（How to Evaluate）**：
    - **数据集**：闭端QA（多跳QA、挑战性QA、事实验证）、开端QA（深度研究式报告生成）、领域特定数据集。
    - **指标**：针对闭端任务用准确率、F1、EM、Pass@k等；开端任务用关键点覆盖、信息量、广度深度、连贯性、引用准确性、胜率等。
    - **评判方式**：从基于规则→LLM-as-a-Judge→Agent-as-a-Judge，人工评估作为黄金标准但成本高。
- **流程图/公式**：文中给出了任务形式化描述（第2节），以公式定义了计划、行动、观察、生成等步骤。无需重复代码，但已用文字说明。

## 3. 实验设计

- **本文为综述论文，未开展新的实验**。但它系统归纳了已有工作的实验设置：
  - **覆盖的数据集**：按类别列出，如多跳QA（HotpotQA、2WikiMultiHopQA、Bamboogle、MuSiQue等）、挑战性QA（BrowseComp、InfoDeepSeek、ORION等）、事实验证（LongFact、Hover、FEVEROUS等）、开端QA（Researchy Questions、DeepResearchGym等）、领域特定（FinSearchBench-24、MedMCQA、GPQA、GAIA等）。详见论文附录表4。
  - **Benchmark**：综述未提出新的benchmark，但梳理了各任务常用基准和评估环境（静态/动态/规则/LLM评判）。
  - **对比方法**：在“如何优化”部分对比了调优/免调优的多种代表方法，如Self-RAG、Search-R1、R1-Searcher、DeepResearcher等，并在表1、表2中列出了模型名称、搜索结构、是否多智能体、是否TTS、训练算法、奖励类型、评估指标等。
- **实验充分性**：作为综述，它覆盖了大量已有工作（数十篇论文），提供了系统化的分类和对比表格，实验分析充分、客观。

## 4. 资源与算力

- **未明确说明**。综述论文不涉及自身训练，也未对引用的各工作的具体算力（GPU型号、数量、训练时长）进行汇总。只在第7章“稳健的基础设施”中提及需要优化RL采样效率和高召回检索系统等，但无具体数值。

## 5. 实验数量与充分性

- **实验数量**：本文没有自有的实验。作为综述，它汇总了**超过100篇相关文献**的实验结果，并在表1（免调优方法）、表2（调优方法）、表3（应用领域）、表4（数据集）中进行了详细对比。
- **充分性**：覆盖全面，从搜索结构、优化策略、应用范围和评估体系四个角度系统梳理，各类方法的关键特征（多智能体、TTS、奖励设计等）均以表格形式直观呈现，分析充分客观。

## 6. 论文的主要结论与发现

- **搜索结构的演化趋势**：从固定子查询向上下文动态生成发展，从并行向顺序和混合结构演进。免调优方法更倾向于混合结构以覆盖更多路径；调优方法通常将灵活性内化到顺序结构中，提升效率。
- **调优范式的有效性**：主流高效流水线是SFT预热+RL微调，RL通常使用可验证奖励（格式、准确率），优化算法以PPO和GRPO为主。高质量监督轨迹和中间奖励能缓解奖励稀疏性。
- **应用拓展**：搜索智能体正从AI助手向电商、金融、医学、科研等专业领域扩展，同时也被用于增强智能体内部的记忆、工具选择和推理能力。
- **评估挑战**：现有基准多聚焦于效率和准确性，缺乏对信息甄别、来源可靠性、多源融合能力的深度评估。未来需要Agent-as-a-Judge等更复杂的评判方式。
- **关键挑战**：信息源融合（私有数据库 vs 外部web）、不完美检索（噪声、偏见、虚假信息）、从文本到多模态、定制化RL算法（长程稀疏奖励）、知识边界困境（何时依赖内化知识 vs 外部搜索）、信息真实性验证、工具不可靠性、智能体自我进化（自主发现缺陷并改进）。

## 7. 优点

- **首次系统性综述**：是该领域第一篇全面覆盖搜索结构、优化、应用、评估的综述，填补了空白。
- **清晰的分类体系**：从“如何搜索、如何优化、如何应用、如何评估”四个维度入手，逻辑清晰，便于读者快速定位。
- **丰富详实的对比表格**：提供了免调优方法、调优方法、应用案例、数据集等多张对比表（表1~4），涵盖方法名、结构、调优策略、奖励设计、评估指标等关键信息，极具参考价值。
- **前瞻性分析**：不局限于现有工作，还系统梳理了挑战和未来方向（如自我进化、多模态、定制化RL等），对后续研究具有指导意义。

## 8. 不足与局限

- **商业应用覆盖不足**：论文明确指出自身主要聚焦学术论文，对商业系统（如OpenAI Deep Research、Gemini等）的内部技术细节无法深入分析，可能存在学术与工业界实践脱节的风险。
- **缺乏定量实验**：作为综述，自身未进行任何对比实验或消融实验，对各类方法的性能差异只能依赖原文报告，缺乏统一的实验复现和公平比较。
- **评估维度偏传统**：虽然提到了需要更复杂的评估，但当前工作仍主要基于正确性和效率指标，对智能体的“批判性思维”“信息甄别能力”“长程推理稳定性”等核心能力的度量仍不成熟，综述对此也未提出具体测评方案。
- **应用领域侧重QA**：尽管列举了多个外部领域，但大多数应用仍以问答为中心，“深度研究报告生成”等开放任务评估体系尚在初期，跨领域迁移性有待验证。
- **未涉及伦理与安全**：论文未讨论搜索智能体可能引发的信息操纵、偏见放大、隐私泄露等伦理安全问题，这是后续研究中不可忽视但本综述未覆盖的部分。

（完）
