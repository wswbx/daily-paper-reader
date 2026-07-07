---
title: "AI Agents for the Science of Science: A Survey of Tasks, Architectures, Evaluations, and Challenges"
title_zh: 面向科学学的AI智能体：任务、架构、评估与挑战综述
authors: "Yixuan Liu, Yicheng Zhang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1804.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 关于AI智能体在科学学中应用的综述，涵盖自主研究工具和模拟
tldr: 该综述首次对科学学中的AI智能体进行了系统调查。它提出了以任务为中心的分类法，区分了作为模拟的智能体（模拟科学行为）和作为工具的智能体（辅助实证分析）。该工作涵盖了自主研究相关的大量工作，包括多智能体模拟和工具增强系统，为自主研究领域提供了全面的视角和未来方向。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1804/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1663, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1804/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1654, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1804/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 794, \"height\": 471, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1804/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1665, \"height\": 610, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1804/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1671, \"height\": 910, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1804/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1676, \"height\": 829, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1804/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 812, \"height\": 673, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1804/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1628, \"height\": 961, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1804/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1438, \"height\": 1812, \"label\": \"Table\"}]"
motivation: 科学学数据增长，AI智能体开始参与科学研究，但缺乏系统综述。
method: 提出任务中心分类法，区分模拟型智能体和工具型智能体。
result: 总结了当前方法和开放挑战。
conclusion: 该综述为自主研究智能体的发展和评估提供指导。
---

## Abstract
The Science of Science (SciSci) examines how scientific knowledge is generated, evaluated, and transformed by utilizing large-scale scholarly and bibliometric data. As these data grow in scale and complexity, analysis has increasingly relied on statistical, network-based, machine learning methods, and is now seeing growing involvement of AI agents. This emerging class of such agents, ranging from multi-agent simulations of scientific behavior to tool-augmented systems for empirical analysis, is beginning to reshape how SciSci research is conducted. In this survey, we propose a task-centered taxonomy, distinguishing *agents as simulations*, which model citation, collaboration, and community dynamics, from *agents as tools*, which assist empirical analysis and scientific workflows. We review agent architectures, learning mechanisms, evaluation, and SciSci benchmarks, and examine open challenges related to reliability, data quality, and bias. Our survey aims to clarify the landscape of AI agents in SciSci and to support the development of reliable and scientifically useful AI systems for studying science and scientific communities.

---

## 论文详细总结（自动生成）

# 面向科学学的AI智能体：任务、架构、评估与挑战综述 —— 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究对象**：科学学（Science of Science, SciSci）——研究科学知识如何生成、评估和转化的交叉学科，利用大规模文献计量数据（如出版物、引文、合作网络、职业轨迹）揭示科学进步、创新和不平等的规律。
- **传统方法困境**：早期依赖统计、网络分析、机器学习，但数据规模与复杂度持续增长，传统方法难以处理多步推理、跨学科分析及实时数据交互。
- **AI智能体兴起**：大语言模型（LLM）赋能的智能体（agent）具备规划、工具使用、记忆、环境交互等能力，非常适合SciSci中多步骤、数据密集的工作流。但该领域缺乏系统性梳理。
- **论文核心问题**：AI智能体如何有效支持SciSci研究？有哪些架构和执行范式？如何评估？存在哪些开放挑战？
- **整体含义**：首次对SciSci领域的AI智能体进行系统调查，提出任务中心分类法，明确模拟型智能体（测试机制假设）与工具型智能体（辅助实证分析）两大角色，并为未来开发和评估提供指导。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出任务中心分类法，将AI智能体分为两类：
  - **作为模拟的智能体**（Agents as Simulations）：建模科学过程（引文网络、合作动态、同行评审），用于测试机制性假设。
  - **作为工具的智能体**（Agents as Tools）：操作化SciSci理论概念（知识重组、评审规范、证据积累），辅助实证分析和科学工作流。
- **关键技术细节**（概念性描述，无具体公式）：
  - **Agent能力**：推理与规划（Chain-of-Thought, Tree-of-Thoughts, ReAct）、工具使用与知识整合（实时API、RAG）、可扩展语义分析、人类行为模拟（角色条件化、记忆、多智能体交互）、假设生成与迭代优化（多智能体辩论、自我批评）。
  - **架构模式**（图2）：
    - **单智能体**：单一LM控制器，顺序执行规划-行动-反思循环（如AI Scientist, SciMON）。
    - **多智能体**：角色专业化（规划者、文献检索、分析师、写作者、批评者），通过共享工具和记忆协调（如VirSci, ResearchTown, CiteAgent）。
    - **混合架构**：编排者管理分阶段工作流（检索→分析→综合），结合RAG、工具、持久性记忆（如PaperQA2, SciSciGPT）。
  - **学习范式**：
    - **推理时适应**为主：上下文学习（角色提示）、检索增强（RAG）、反思与自我批评。
    - **监督微调**（SFT）少用：仅REMOR在~1700条同行评审样本上进行LoRA SFT。
    - **偏好优化**（RLHF/DPO/GRPO）极少：仅REMOR应用GRPO训练，产生>2倍人类基线。
  - **无公式或算法伪代码**：论文以综述形式梳理已有系统，未提出新算法。

## 3. 实验设计：数据集、Benchmark、对比方法

- **论文本身是综述，未进行独立实验**。但总结了所评述系统的评估方式和基准：
  - **评估方式**：
    - **人类评估**：专家评分（如ResearchAgent用10位专家、15标准，ρ=0.83）；创意支持指数（CSI）；湿实验室验证（AI Co-Scientist验证肿瘤抑制）。
    - **自动评估**：LLM-as-judge、基于嵌入的相似度（SciBERT）、SciSci指标（如新颖性复合得分）、多维框架（REMOR的8维度奖励、SciSciGPT的三级自评）。
    - **自动与人类评估不对齐**：LLM评分膨胀（Agent Lab报告高出60%），相关性低（ResearchTown r=0.49）。
  - **Benchmark与数据集**（表4）：
    - **想法生成**：ResearchAgent corpus (50K), VirSci (85K), SciMON, Scideator facets。
    - **同行评审**：AgentReview (53K), REMOR PeerRT+HPRR (16K)。
    - **声明验证**：SciFact (1.4K claims), LitQA2 (248), PubMedQA (273K)。
    - **自动化**：ScienceAgentBench (102 tasks), MLE-Bench (75), ResearchBench (1.4K)。
    - **引文网络**：Cora, CiteSeer, OGB-Citation2 (2.9M), SciSciNet, LLM-Agent corpus。
    - **共享语料**：S2ORC (81M), OpenAlex (250M), Semantic Scholar, AMiner。
  - **对比方法**：论文仅引用各系统报告的性能（如PaperQA2在LitQA2上85.2%准确率优于人类专家73.8%；REMOR比人类基线高2倍；Agent Lab显示LLM评分高估60%），没有统一对比实验。

## 4. 资源与算力

- **论文未说明自身消耗的算力**。
- 对于所评述的系统，部分提及：
  - REMOR使用LoRA在~1700样本上微调，后接GRPO训练。
  - 大多数系统依赖预训练基础的LLM（如GPT-4, Claude），无需额外大规模训练。
  - 未提供GPU型号、数量或训练时长等具体信息。

## 5. 实验数量与充分性

- **作为综述，论文本身无实验**，而是总结了数十个系统的实验设置。
- **覆盖范围较广**：涵盖模拟（3个子任务）和工具（4个子任务），涉及10+代表性系统（CiteAgent, VirSci, ResearchTown, AgentReview, MARG, REMOR, SciMON, ResearchAgent, SciAgents, PaperQA2, SciSciGPT等）。
- **充分性评价**：
  - **优势**：对现有多样性系统进行了全面整理，提供了清晰的分类和架构对比。
  - **不足**：不同系统之间缺乏统一评估标准，任务定义、数据划分、评价协议高度异构，难以直接比较。论文自身未设计控制实验验证分类法的有效性。
  - **客观性**：论文承认该领域存在评估不一致、闭源模型、未公开提示词等问题，并指出复现困难，态度客观。

## 6. 论文的主要结论与发现

- **AI智能体为SciSci提供范式转变**：从仅观察科学过程转向能够干预和进行反事实实验（如模拟合作网络、引文动态、评审偏见）。
- **双重角色**：智能体既是研究工具，也是研究对象——其输出（模拟的引文网络、生成的评审、发现的创意）本身成为SciSci分析的实证对象。
- **关键挑战**：
  - 评估不对齐：自动评价与人类判断弱相关，LLM评分往往膨胀。
  - 幻觉与可重复性：智能体可能产生虚假信息，影响科学流程可靠性。
  - 偏差放大：LLM训练数据反映并强化现有科学偏见（如引文偏见、集体焦点收缩）。
  - 偏好优化未被充分探索：大部分系统依赖推理时技术，而通过RLHF/DPO对齐科学规范的方法几乎空白。
  - 缺乏统一基准：虽共享语料丰富，但任务级标准化不足。
- **未来方向**：需要开发更鲁棒的评估方法、偏好优化策略，并解决智能体成为研究对象后的反射性挑战。

## 7. 优点：方法或实验设计上的亮点

- **分类体系清晰**：提出“模拟vs工具”二元分类，有效区分了两种不同目的的系统，便于理解不同系统的设计目标。
- **架构归纳全面**：总结单智能体、多智能体、混合三种架构模式，并给出角色分类表格（表3），具有实用参考价值。
- **学习范式梳理**：指出当前领域偏好“推理时适应”而忽视“偏好优化”的现状，为后续研究提供方向。
- **评估和基准汇总**：整理了主要基准和评估方法，并坦率指出自动评估与人类评估的差距，客观反映领域现状。
- **对反射性挑战的识别**：指出智能体既是SciSci工具又是研究对象这一独特特性，是对其他领域（如代码、电商）智能体研究所不具备的深刻洞察。
- **局限性声明**：论文明确列出了自身范围、agent定义模糊、可复现性等局限，体现学术严谨性。

## 8. 不足与局限

- **实验缺失**：作为综述，没有设计任何对比实验验证分类法的有效性或总结性结论的普适性。
- **覆盖不完整**：聚焦于明确设计用于SciSci的系统，但“AI for Science”领域的许多相关工作（如材料发现、药物设计）被排除；一些具备agent属性但未明确标注的系统可能未被纳入。
- **Agent定义边界模糊**：论文承认“AI agent”在不同社区定义不一致，一些被评价的系统实际上只是工具增强的LLM流水线，而有些未标注的系统却具有agent属性。
- **不可复现性**：多数系统依赖闭源模型、未公开的提示词或不断演变的API，难以独立验证和复现。
- **评估比较受限**：缺乏跨系统的公平对比实验，无法确认不同架构或学习范式在统一任务上的相对优劣。
- **理论深度不足**：主要描述已有系统，但对Why某些架构有效、What是理论最优解等分析较浅。
- **数据集和基准部分不够统一**：虽然列出了众多资源，但未建议标准化的评估协议或集成基准，对社区推动力有限。

（完）
