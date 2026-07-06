---
title: "OS Agents: A Survey on MLLM-based Agents for Computer, Phone and Browser Use"
title_zh: 操作系统代理：基于多模态大语言模型的计算机、手机和浏览器使用代理综述
authors: "Xueyu Hu, Tao Xiong, Biao Yi, Zishu Wei, Ruixuan Xiao, Yurun Chen, Jiasheng Ye, Meiling Tao, Xiangxin Zhou, Ziyu Zhao, Yuhuai Li, Shengze Xu, Shenzhi Wang, Xinchen Xu, Shuofei Qiao, Zhaokai Wang, Kun Kuang, Tieyong Zeng, Liang Wang, Jiwei Li, Yuchen Eleanor Jiang, Wangchunshu Zhou, Guoyin Wang, Keting Yin, Zhou Zhao, Hongxia Yang, Fan Wu (吴凡, 吴钒), Shengyu Zhang, Fei Wu"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.369.pdf"
tags: ["query:cli-agent"]
score: 10.0
evidence: 全面综述涵盖在CLI环境中操作的多模态大语言模型代理用于任务自动化
tldr: 本文全面综述了基于多模态大语言模型的OS代理，这些代理通过GUI和CLI界面在计算机、手机和浏览器上自主完成任务。文章系统阐述了代理的关键组件与能力，并分析了构建方法。对于设计能够理解自然语言命令并执行终端任务的智能CLI代理提供了系统化的参考。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.369/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 767, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.369/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1664, \"height\": 1070, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.369/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1648, \"height\": 870, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.369/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 778, \"height\": 834, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.369/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1637, \"height\": 781, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.369/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1642, \"height\": 783, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.369/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 2462, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.369/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1157, \"height\": 2121, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.369/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1035, \"height\": 1897, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.369/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1562, \"height\": 822, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.369/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1621, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.369/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 806, \"height\": 758, \"label\": \"Table\"}]"
motivation: 随着MLLM的发展，创建像J.A.R.V.I.S.一样的AI助手成为可能，但缺乏系统性的综述。
method: 对MLLM-based OS代理进行综述，涵盖基于GUI和CLI的代理，分析其关键组件、能力和构建方法。
result: 系统梳理了OS代理的最新进展，包括架构、训练方式和应用场景。
conclusion: 该综述为OS代理的未来发展提供了全面基础，特别强调了CLI代理的重要性。
---

## Abstract
The dream to create AI assistants as capable and versatile as the fictional J.A.R.V.I.S from Iron Man has long captivated imaginations. With the evolution of multi-modal large language models ((M)LLMs), this dream is closer to reality, as (M)LLM-based Agents using computers, mobile phones and web browsers by operating within the environments and interfaces (e.g., Graphical User Interface (GUI) and Command Line Interface (CLI)) provided by operating systems (OS) to automate tasks have significantly advanced. This paper presents a comprehensive survey on these advanced agents, designated as OS Agents. We begin by elucidating the fundamentals of OS Agents, exploring their key components and capabilities. We then examine methodologies for constructing OS Agents, focusing on domain-specific foundation models and agent frameworks. A detailed review of evaluation metrics and benchmarks highlights how OS Agents are assessed across diverse platforms and tasks. Finally, we discuss current challenges and identify promising directions for future research. An open-source GitHub repository is maintained as a dynamic resource to foster further innovation in this field.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文《OS Agents: A Survey on MLLM-based Agents for Computer, Phone and Browser Use》生成的详细中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

#### **研究动机**
- **长期愿景**：创造像钢铁侠中的“J.A.R.V.I.S.”一样、能够理解并执行复杂任务的超级AI助手，是人类的长期梦想。
- **技术契机**：随着（多模态）大语言模型 ((M)LLMs) 的快速发展，基于这些模型的智能体（Agent）具备了前所未有的理解与规划能力。
- **研究空白**：（M）LLM 赋能的操作系统代理（OS Agents）在学术和工业界都迎来了爆发式增长（如 Anthropic 的 Computer Use、Apple Intelligence），但缺乏一个系统、全面的综述来梳理该领域的现状、方法、评估与未来方向。

#### **研究背景**
- **“OS Agents”定义**：指那些利用操作系统提供的环境（如 GUI、CLI）和接口，在计算机、手机、浏览器等平台上自主完成任务（如在线购物、预订行程）的 AI 代理。
- **发展现状**：该领域经历了从2023年的技术验证到2024-2025年产品化的爆发，产生了大量研究工作（如CogAgent, AutoGLM）和商业产品（如OpenAI Operator）。

### 2. 论文提出的方法论：核心思想、关键技术细节

#### **核心思想**
本文并非提出一个单一的新方法，而是系统性地梳理和分类了构建 OS Agents 的两大主流方法：
1.  **开发领域特定的基础模型**：针对 OS 任务训练专用模型。
2.  **设计 OS Agent 框架**：围绕通用（M）LLM，构建模块化代理框架。

#### **关键技术细节**

##### **A. 基础模型构建**
1.  **模型架构**：
    - **现有LLMs**：直接使用开源大模型处理HTML等文本输入。
    - **现有MLLMs**：使用开源多模态模型，直接处理GUI截图。
    - **拼接型MLLMs**：将LLM与视觉编码器拼接，更适合特定OS任务。
    - **修改型MLLMs**：对MLLM架构进行修改，例如CogAgent引入高分辨率视觉编码器（1120x1120）以解析复杂GUI。
2.  **训练策略**：
    - **预训练 (Pre-training)**：使用公开数据或合成数据，进行屏幕定位、屏幕理解和光学字符识别 (OCR) 等任务。
    - **监督微调 (SFT)**：使用规则或模型合成的高质量数据（如链式行动思维 Chain-of-Action-Thought），提升代理的导航和执行力。
    - **强化学习 (RL)**：将（M）LLM作为策略模型，使用PPO等算法优化代理的最终任务成功率。

##### **B. Agent 框架设计**
1.  **感知（Perception）**：
    - **文本描述**：早期工作将环境转换为HTML、DOM树等结构化文本。
    - **GUI截图**：主流做法，直接处理截图，并结合标记法（SoM）和语义描述增强理解。
2.  **规划（Planning）**：
    - **全局规划**：一次性生成完整计划并执行，如Chain-of-Thought (CoT)。
    - **迭代规划**：根据环境和历史动态调整计划，如ReAct模式（推理+行动）。
3.  **记忆（Memory）**：
    - **内部记忆**：保存任务过程中的行动历史、截图等。
    - **外部记忆**：通过知识库、API工具获取长期知识。
    - **记忆优化**：包括管理（去冗、抽象）、成长经验（从成功/失败中学习）和经验检索（匹配相似任务的经验）。
4.  **行动（Action）**：
    - **输入操作**：鼠标/键盘/触屏操作。
    - **导航操作**：滚动、翻页等。
    - **扩展操作**：执行代码脚本、调用API以超越常规操作限制。

### 3. 实验设计：数据集 / 场景，Benchmark，对比方法

#### **核心特征**
这是一篇综述性论文，**不包含新的实验**。其“实验设计”体现为对现有评估方法的系统性梳理和总结。

#### **评估指标与基准**
- **评估指标**：
    - **步骤级**：评估每一步行动定位的准确性。
    - **任务级**：评估整体任务的成功率和执行效率（如步数比、耗时）。
- **评估基准 (Benchmarks)**：
    - **平台分类**：计算机、手机、浏览器。
    - **环境分类**：静态（如MiniWoB, Mind2Web）和交互式（真实/模拟，如OSWorld, AndroidWorld, WebArena）。
    - **任务类型**：
        - **GUI定位**：将指令转化为屏幕上的具体操作元素。
        - **信息检索**：从动态界面中提取信息。
        - **代理任务**：最核心的任务，要求自主规划、执行和完成目标。
- **对比方法**：论文在附录中总结了大量研究工作（如CogAgent, SeeClick, AutoWebGLM）和商业产品（如OpenAI Operator, Claude Computer Use）在上述基准上的性能表现（例如，在OSWorld基准中，OpenAI Operator达到38.1%的成功率，而Claude Computer Use为22.0%）。

### 4. 资源与算力

**未明确说明**。由于是综述论文，其并未进行任何新的模型训练或大规模实验，因此没有涉及具体的算力使用（如 GPU 型号、数量、训练时长等）。

### 5. 实验数量与充分性

- **数量**：作为综述，它涵盖了该领域**数十篇**代表性论文和**十余个**主要商业产品，覆盖了从2022年到2025年初的广泛工作。
- **充分性**：对方法的分类（如架构、训练策略、框架组件）和基准（平台、环境、任务类型）的梳理是详尽且系统的。通过在附录中给出性能对比表，间接地提供了对现有工作的评估概览。
- **客观性**：论文对方法和挑战的描述较为客观，没有刻意偏向某一特定方法。结论和建议基于对文献的广泛分析，具有一定权威性。

### 6. 论文的主要结论与发现

1.  **领域现状**：基于 MLLM 的 OS Agents 是一个高速发展的领域，已经从学术验证阶段进入到大规模商业产品化阶段。
2.  **构建路径**：主要存在两种互补的构建路径：训练专用基础模型（更好性能，但成本高）和设计通用代理框架（更灵活，但对底层模型能力要求高）。
3.  **核心挑战**：安全与隐私（如注入攻击、后门攻击）是当前最严峻的挑战之一，且针对 OS Agents 的特定防御措施尚不成熟。
4.  **未来方向**：个性化和自我进化能力是下一代OS代理的关键。从单一工具/插件形式向系统级深度集成（如Apple Intelligence）是发展趋势。
5.  **CLI代理的重要性**：论文明确将**命令行界面（CLI）** 与GUI并列为OS Agent的重要操作环境，指出CLI代理在自动化任务中的价值和未来潜力。
6.  **评估现状**：现有基准多为平台特定（电脑、手机、浏览器），缺乏统一的、跨平台的综合评估标准，且真实世界环境评估仍存在挑战。

### 7. 优点

1.  **系统性与全面性**：首次以“OS Agents”为统一概念，整合了在不同平台（电脑、手机、浏览器）和界面（GUI、CLI）上的代理研究，提供了一个宏观的、结构化的知识图谱。
2.  **清晰的分类学**：对构建方法（基础模型 vs. 代理框架）、代理能力（理解、规划、定位）和评估维度（平台、任务、指标）的分类清晰、合理，便于读者快速理解领域全貌。
3.  **工业与学术结合**：不仅分析了学术前沿，还梳理了主要商业产品（如Operator, Apple Intelligence），并讨论了它们之间的关系，视角全面。
4.  **前瞻性**：明确指出了安全、隐私、个性化和自我进化等关键挑战和未来方向，具有很强的指导意义和启发性。
5.  **资源总结**：论文包含了详尽的表格（如基础模型总结、框架对比、基准对比、产品列表），为后续研究者提供了宝贵的文献参考和工具索引。

### 8. 不足与局限

1.  **缺乏直接实验**：作为纯综述，它没有进行任何新的量化实验或提出新方法，因此无法提供直接的性能对比或验证其观点的正确性。
2.  **信息深度有限**：尽管分类全面，但对每个具体方法的细节描述可能不够深入。读者仍需阅读原始论文以获得完整的理解和实现细节。
3.  **伦理与偏见讨论薄弱**：虽然在第6章和附录F.1中提到了伦理问题（如偏见、公平性），但篇幅有限，仅作概述，没有像安全与隐私那样进行详细讨论。
4.  **边缘设备部署讨论不足**：论文在局限性部分承认，对于如何在手机等边缘设备上高效部署模型这一关键现实问题，讨论不够深入。
5.  **偏重英文主流环境**：综述主要基于英文世界的科研论文和产品，对其他语言或地域的相关工作覆盖较少，可能存在一定的偏差风险。

（完）
