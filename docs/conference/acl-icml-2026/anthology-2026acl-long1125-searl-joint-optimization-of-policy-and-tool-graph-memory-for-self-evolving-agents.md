---
title: "SEARL: Joint Optimization of Policy and Tool Graph Memory for Self-Evolving Agents"
title_zh: SEARL：策略与工具图记忆的联合优化用于自我进化智能体
authors: "Xinshun Feng, Xinhao Song, Lijun Li, Gongshen Liu, Jing Shao"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.1125.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: 自我进化智能体；工具记忆；强化学习；任务自动化
tldr: SEARL提出了一个基于工具记忆的自我进化智能体框架，利用可验证奖励的强化学习，使智能体能够从轨迹中合成工具并积累经验。该工作解决了资源受限环境下智能体学习的挑战，为命令行任务自动化智能体提供了高效的学习和适应方法。实验验证了其在多轮推理和工具使用上的优越性。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1125/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 804, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1125/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1660, \"height\": 853, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1125/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 808, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1125/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 813, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1125/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1486, \"height\": 700, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1125/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 806, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1125/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 832, \"height\": 322, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1125/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1644, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1125/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 649, \"height\": 502, \"label\": \"Table\"}]"
motivation: 现有自我进化智能体依赖大规模LLM或多智能体框架，且奖励稀疏，难以在资源受限场景部署。
method: 提出SEARL框架，联合优化策略与工具记忆图，通过工具合成和经验积累实现高效学习。
result: 在多个智能体基准上，SEARL比基线方法更高效，特别是在低资源环境下表现突出。
conclusion: 该工作为构建自进化、资源友好的任务自动化智能体提供了可行方案。
---

## Abstract
Recent advances in Reinforcement Learning with Verifiable Rewards (RLVR) have demonstrated significant potential in single-turn reasoning tasks. With the paradigm shift toward self-evolving agentic learning, models are increasingly expected to learn from trajectories by synthesizing tools or accumulating explicit experiences. However, prevailing methods typically rely on large-scale LLMs or multi-agent frameworks, which hinder their deployment in resource-constrained environments. The inherent sparsity of outcome-based rewards also poses a substantial challenge, as agents typically receive feedback only upon task completion. To address these limitations, we introduce a Tool-Memory based self-evolving agentic framework SEARL. Unlike approaches that directly utilize interaction experiences, our method constructs a structured experience memory that integrates planning with execution. This provides a novel form of state abstraction that facilitates the aggregation of actions within functionally analogous contexts, such as tool reuse. Consequently, agents not only extract explicit knowledge from historical data but also leverage inter-trajectory correlations to densify reward signals. We evaluate our framework on knowledge reasoning and complex search tasks, demonstrating its effectiveness in achieving more practical and efficient agentic learning.

---

## 论文详细总结（自动生成）

# 论文详细总结：SEARL：策略与工具图记忆的联合优化用于自我进化智能体

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：当前大型语言模型（LLM）在单轮推理任务中借助可验证奖励的强化学习（RLVR）取得了显著进展。然而，当转向需要自我进化的智能体学习时，模型需要从轨迹中合成工具或积累显式经验。现有方法通常依赖大规模LLM或多智能体框架，难以在资源受限环境中部署；同时，基于结果的奖励稀疏（仅在任务完成时获得反馈），导致学习效率低下。
- **整体含义**：提出一种**工具记忆（Tool-Memory）** 的自我进化智能体框架SEARL，通过构建结构化的经验记忆，将规划与执行整合，实现状态抽象的创新，从而在功能相似的上下文（如工具复用）中聚合动作，利用轨迹间相关性密集化奖励信号，最终实现更实用和高效的智能体学习。

## 2. 方法论：核心思想、关键技术细节、算法流程（文字说明）

- **核心思想**：联合优化智能体的策略参数和外部工具记忆（工具图TG），使智能体在训练过程中持续获取、精炼和复用问题解决能力。关键创新在于：
    1. **工具图记忆（Tool Graph Memory）**：以有向图形式存储工具（节点）和执行依赖关系（边），持续演化并提供归纳偏置以改进泛化和规划。
    2. **工具记忆感知策略优化算法**：结合轨迹级和步级信用分配，利用工具锚点（anchor）实现细粒度优势估计。
    3. **结构化轨迹生成**：将决策过程分解为四个阶段：计划（Planning）、检索（Retrieve）、思考（Think）、动作（Action），并使用XML标签封装。
- **关键技术细节**：
    - **奖励设计**：包括稀疏结果奖励（任务成功得1）和密集过程奖励（规划奖励、工具创建奖励、工具执行奖励、格式奖励）。
    - **优势估计**：双层结构——**情节级相对优势**（基于同一任务的多条轨迹的总体回报归一化）和**步级工具锚点相对优势**（将同一MCP工具相关的动作分组，计算该组内的相对优势）。最终优势 = 情节优势 + ω × 步级优势。
    - **工具图生命周期**：子图提取 → 工具注册 → 工具检索 → 记忆更新与合并。合并时通过语义嵌入余弦相似度判断工具等价性，超过阈值则合并节点并重定向边。
- **算法流程**（文字说明）：
    1. 初始化策略πθ、参考策略πref、工具图TG。
    2. 每次迭代：采样一批任务，为每个任务生成N条轨迹，每条轨迹中执行计划-检索-思考-动作循环，收集工具创建候选。
    3. 轨迹生成后：通过执行成功和奖励筛选有效工具，注册到TG（合并或新增节点、边）。
    4. 计算优势：先按轨迹组计算情节级相对优势，再按工具锚点分组计算步级相对优势，加权得到最终优势。
    5. 使用裁剪的PPO目标更新策略，并加入KL散度正则化。

## 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**：
    - **数学推理**：AIME2024（30道高难度数学题）、MATH500（500道挑战题）、GSM8K（小学应用题）。
    - **知识密集型推理**：HotpotQA、2WikiMultihopQA、Musique、Bamboogle（均基于维基百科的多跳问答）。另使用WebWalker等。
- **Benchmark**：包括上述7个数据集，采用LLM-as-Judge（使用Qwen3-32B作为评判模型）评估pass@1准确率。
- **对比方法**：
    - TIR Prompting（直接提示）
    - GRPO（群体相对策略优化）
    - DAPO（带Clip-Higher的RL算法）
    - REINFORCE++
    - ARPO（智能体强化策略优化）
    - 排除了GiGPO（因不兼容当前任务设置）
- **训练数据**：来自Tool-star的10,000条开源RL训练样本，配备Python解释器和本地Wikipedia搜索服务器。

## 4. 资源与算力

- **GPU型号**：NVIDIA H200 GPUs。
- **数量**：6张GPU（Global Batch Size为384，配置为64 × 6 GPUs）。
- **训练时长**：每个训练epoch约需10小时。论文中训练epoch数为1。
- **模型**：Qwen3-4B（标准生成模式，非思考模式）。
- **其他设置**：最大轨迹轮次6，最大提示长度4096，最大回答长度2048，学习率1e-6。

## 5. 实验数量与充分性

- **主要实验**：表1展示了SEARL在7个数据集上与5个基线的对比，共覆盖7×6=42个数据点（每个数据集每个方法一个准确率）。
- **消融实验**：图4移除了三个组件（单组消失、步级分组、步级奖励），在7个数据集上分别展示，共21个对比柱状图。结果清晰地展示了各组件重要性，尤其步级分组影响最大。
- **动态分析**：图3展示了训练奖励和熵的演化，对比GRPO，验证了SEARL在奖励和探索性上的优势。
- **工具图演化分析**：图6展示了不同训练阶段的工具子图结构增长，分析节点和边的数量，揭示语义簇的形成和合并。
- **案例分析**：图5比较了基线（整体工具）和SEARL（模块化工具链）在约束几何序列问题上的表现，展示效率和可复用性的提升。
- **公平性**：采用统一的数据划分和评估方法（LLM-as-Judge），对比方法采用官方或常用实现，训练与测试集分离，实验结果结果具有客观性。但在数学简单任务上SEARL并未达到最优，说明可能存在公平性上的权衡（工具创建代价）。
- **充分性评价**：实验覆盖了数学和知识推理两大领域，消融分析合理，但未在更多样化的环境（如WebArena或真实世界工具）中验证，也未探讨不同基座模型（如7B/13B）的扩展性，存在一定局限性。

## 6. 主要结论与发现

- SEARL在多跳知识推理任务上显著领先所有基线，尤其在HotpotQA（0.335）、2wiki（0.360）、Bamboogle（0.304）上表现最好，验证了结构化工具记忆对外部信息合成的有效性。
- 在数学推理上，SEARL在AIME24上与ARPO并列第一（0.3333），在GSM8K和MATH500上虽低于GRPO但保持竞争力，表明工具生成对简单问题可能引入噪声，但在复杂问题上具有更好的泛化能力。
- 消融实验表明步级分组（工具锚点优势）对性能贡献最大，步级奖励次之，单组消失机制影响相对较小但稳定训练。
- 学习动态显示SEARL保持更高熵值，鼓励探索，训练奖励优于GRPO。
- 工具图随时间从孤立子图演化为多簇连接结构，捕获交叉领域的经验。

## 7. 优点：方法或实验设计上的亮点

- **结构化工具记忆**：有向图形式的工具记忆不仅存储工具代码，还保存执行依赖关系和因果结构，支持细粒度的复用和规划。
- **细粒度信用分配**：利用工具锚点将步级优势从原始状态空间映射到有限工具集，实现了在跨轨迹的相似工具使用场景下进行对比，有效解决了稀疏奖励和信用分配难题。
- **联合优化**：同时迭代策略和外部记忆，突破传统RL仅优化参数的局限，使智能体具备真正的自我进化能力。
- **资源友好**：基于4B参数模型，借助工具记忆提升能力，降低了部署门槛。
- **模块化工具创建**：鼓励创建细粒度、可复用的工具，而非整体求解器，提高了训练稳定性和泛化性。
- **实验严谨性**：覆盖多领域（数学、知识推理），消融分析完整，动态演化分析直观，案例对比清晰。

## 8. 不足与局限

- **简单任务性能下降**：在GSM8K和MATH500上，SEARL低于GRPO，表明工具创建的开销可能干扰基本推理能力，简单问题直接推理比工具分解更有效。
- **工具集适应性限制**：训练中生成的工具可能偏向当前领域（数学/维基百科问答），对直接搜索或高度专业化领域的迁移性有待验证。
- **工具质量有限**：受限于4B模型，许多创建的工具过于简单，难以被其他LLM有效复用，工具图的实际价值依赖模型规模。
- **奖励设计风险**：尽管设计了细致奖励，但策略仍可能钻空子（reward hacking），例如为了获得工具创建奖励而生成格式正确但无实际功能的工具。论文也承认这一点。
- **实验范围不够广泛**：未在纯搜索环境（如WebArena）、多轮对话或更复杂的长程任务上评估，也未测试不同基座模型（如7B/14B）的推广性。
- **计算资源需求**：虽然基于4B模型，但每个epoch需6×H200运行10小时，对于更大规模模型和更多轮次训练，资源消耗可能显著增长。

（完）
