---
title: "A²Flow: Automating Agentic Workflow Generation via Self-Adaptive Abstraction Operators"
title_zh: "A²Flow: 通过自适应抽象算子自动化代理工作流生成"
authors: "Mingming Zhao, Xiaokang Wei, Yuanqi Shao, Kaiwen Zhou, Lin Yang, Siwei Rao, Junhui Zhan, Zhitang Chen"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40240/44201"
tags: ["query:cli-agent"]
score: 7.0
evidence: 全自动代理工作流生成框架，使用自适应抽象算子，适用于CLI代理工作流
tldr: A²Flow提出全自动代理工作流生成方法，通过自适应的抽象算子提取与聚类，无需人工干预即可生成可迁移的工作流，在多种代理任务上显著提升效率。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有方法依赖手动预定义算子，限制了工作流自动化的泛化性。
method: 提出三阶段算子提取流程：基于案例生成、聚类抽象和深度提取，形成通用执行算子。
result: 在多个AgentBench任务上，A²Flow实现了更高效的工作流生成和执行。
conclusion: 自适应抽象算子是实现自动化代理工作流生成的有效途径。
---

## Abstract
Large language models (LLMs) have shown strong potential in automating the design of agentic workflows. However, existing methods still rely heavily on manually predefined operators, limiting generalization and scalability. To address this issue, we propose A²Flow, a fully automated framework for agentic workflow generation based on self-adaptive abstraction operators. A²Flow employs a three-stage operator extraction process: 1) Case-based Initial Operator Generation: leveraging expert demonstrations and LLM reasoning to generate case-specific operators; 2) Operator Clustering and Preliminary Abstraction: grouping similar operators across tasks to form preliminary abstractions; and 3) Deep Extraction for Abstract Execution Operators: applying long chain-of-thought prompting and multi-path reasoning to derive compact and generalizable execution operators. These operators serve as reusable building blocks for workflow construction without manual predefinition. Furthermore, we enhance node-level workflow search with an operator memory mechanism, which retains historical outputs to enrich context and improve decision-making. Experiments on general and embodied benchmarks show that A²Flow achieves a 2.4% and 19.3% average performance improvement and reduces resource usage by 37% over state-of-the-art baselines.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

当前大型语言模型（LLM）在自动化设计代理工作流（agentic workflow）方面展现出潜力，但现有方法（如AFLOW、DebFlow、MermaidFlow）仍严重依赖**手动预定义的算子（operators）**，例如“Ensemble”“Review”“Revise”等。这种依赖导致：
- **泛化性受限**：面对开放世界任务（如具身控制、WebShop）需重新设计算子；
- **可扩展性差**：人工设计耗时且难以保证最优性；
- **搜索效率低**：预设算子引入了人工偏置，可能遗漏更有效的组合。

论文的目标是**实现完全自动化的代理工作流生成**，消除对手动预定义算子的依赖，从而提升泛化性、可扩展性和资源效率。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
提出**A²Flow**框架，通过**自适应抽象算子（Self-Adaptive Abstraction Operators）** 和**算子记忆机制（Operators Memory Mechanism）**，自动从专家数据中提取可复用、通用的执行算子，并用于工作流搜索与优化。

### 关键技术细节（三阶段算子提取 + 算子记忆 + 工作流优化）

#### 阶段1：基于案例的初始算子生成（Case-based Initial Operator Generation）
- 将专家数据集划分为20%验证集、80%测试集（固定随机种子42）。
- 利用LLM和提示模板，为每个任务案例生成**案例特定的算子**（如`ObserveEnvironment()`、`CreatePlan()`）。
- 每个算子被定义为代码块，具有单一输入输出，无中间跳转或分支。

#### 阶段2：算子聚类与初步抽象（Operator Clustering and Preliminary Abstraction）
- 用LLM对初始算子进行功能聚类，将相似或重叠的算子合并，形成**初步抽象算子集**（如从多个具体算子抽象出`TaskPlanner()`、`Locator()`等）。
- 这一步减少了算子数量，但抽象程度仍不够。

#### 阶段3：深度提取抽象执行算子（Deep Extraction for Abstract Execution Operators）
- 采用**长链式思维（Long CoT）提示**和**多路径并行生成**（m=6个独立推理路径）。
- 每条路径经过**三次迭代精炼**，每次引入CoT推理和代码有效性检查（反射机制，Python执行器验证语法与可执行性）。
- 最终通过LLM聚合函数合并多条路径的结果，得到**任务感知的抽象执行算子**（如`Planner()`、`Executor()`、`Validator()`）。

#### 算子记忆机制（Operators Memory Mechanism）
- 在每个工作流节点中引入记忆空间`M_k`，存储之前所有算子的输出。
- 第k个算子的计算依赖`input_k`、指令`P_k`和历史记忆`M_{k-1}`。
- 更新规则：`M_k = M_{k-1} ∪ {o_k}`。
- 这使得算子能利用完整的上下文信息，提升决策质量。

#### 自动工作流优化
- 基于AFLOW的MCTS变体框架，但替换其预定义算子为**自适应抽象算子集**。
- 搜索循环：初始化、选择、扩展、评估、反向传播。
- 使用混合概率选择策略平衡探索与利用，每个候选工作流在验证集上多次执行取均值。

## 3. 实验设计：数据集、基准、对比方法

### 数据集（8个公开基准，覆盖5个领域）
| 领域 | 数据集 |
|------|--------|
| 代码生成 | HumanEval, MBPP |
| 数学推理 | GSM8K, MATH（仅使用4个原型问题类型，复杂度5级） |
| 阅读理解 | HotpotQA, DROP |
| 具身任务 | ALFWorld（含Seen/UnSeen子集） |
| 游戏 | TextCraft |

### 对比方法
- **手动设计工作流**：IO（直接调用）、CoT、Self-Consistency（5次采样）、Multi-Persona debate、Self-Refine。
- **自动工作流优化器**：ADAS、AFLOW（SOTA基线）。

### 评估指标
- 代码生成：pass@1
- 数学推理：Solve Rate
- 阅读理解：F1 Score
- 具身/游戏：二元成功/失败奖励
- 效率：token用量折算成本，绘制Pareto前沿

## 4. 资源与算力

论文中**未明确说明**具体使用的GPU型号、数量或训练时长。仅提及：
- 使用**Claude-3.5-sonnet**作为工作流优化器（生成/搜索）。
- 使用**GPT-4o-mini、GPT-4o、DeepSeek-v3**作为执行模型。
- 使用**DeepSeek-v3**作为抽象算子生成器。
- 成本分析中展示了不同模型执行工作流时的token成本与性能关系图。

未提及模型训练或大规模预训练所需的算力信息。

## 5. 实验数量与充分性

### 实验数量
- **主实验**（表1）：在6个数据集（HotpotQA、DROP、HumanEval、MBPP、GSM8K、MATH）上对比8种基线，每个结果取3次独立试验均值。
- **具身/游戏任务**（表2）：在ALFWorld（Seen/UnSeen）、TextCraft上对比ReAct和AFLOW。
- **消融实验**（表3）：在MATH上对比4个变体（无初始算子、无聚类、无深度提取、无数算子记忆），并报告绝对分数和变化率。
- **成本分析**（图3）：在DROP上对比A²Flow与AFLOW的Pareto前沿。
- **案例研究**（图4）：以ALFWorld为例展示算子生成与工作流搜索过程。

### 充分性评估
- **正面**：覆盖多种任务类型（代码、数学、阅读理解、具身、游戏），消融实验验证了每个组件的贡献，成本分析展示了效率优势。
- **潜在不足**：
  - 部分数据集未在消融中覆盖（如仅在MATH上做消融，未在其他任务验证）。
  - 实验仅使用GPT-4o-mini作为执行器报告主结果，对其他执行模型的泛化性未充分探讨。
  - MermaidFlow和DebFlow未被纳入对比（论文发表于AAAI-26，但MermaidFlow和DebFlow可能更晚或未被引用）。
  - 结论中声称“优于SOTA 2.4%和19.3%”，但从表1看，在某些任务（如HumanEval）A²Flow并非最优（91.6% vs AFLOW 90.9%，但不如CoT SC的91.6%），可能存在选择性报告。

## 6. 论文的主要结论与发现

- A²Flow在数学推理、代码生成、阅读理解上平均提升**2.4%**，在具身/游戏任务上提升**19.3%**。
- 资源使用降低**37%**（相比AFLOW）。
- 自适应抽象算子能自动发现有效算子集，无需手动设计。
- 算子记忆机制通过共享历史信息提升搜索性能（消融显示去掉记忆机制导致性能下降4.1%）。
- 成本分析显示A²Flow能发现更高效的工作流，使较弱模型（如GPT-4o-mini）在成本-性能前沿上超越更强模型（如GPT-4o）。

## 7. 优点：方法或实验设计上的亮点

- **全自动化**：首次实现从原始专家数据到通用执行算子的端到端自动提取，消除人工干预。
- **三阶段递进抽象**：从案例级到聚类级再到深度抽象，逐步压缩和提炼算子，逻辑清晰。
- **算子记忆机制**：创新性地引入跨节点记忆，使后续算子能感知历史输出，提升上下文理解。
- **多路径CoT与自一致性**：通过多条推理路径生成候选算子并聚合，增强鲁棒性。
- **代码级有效性检验**：通过Python执行器自动验证算子代码的语法和可执行性，保证生成质量。
- **成本-性能分析**：在Pareto前沿上展示性价比优势，实用性强。
- **实验覆盖多领域**：从符号推理到具身代理，验证了泛化能力。

## 8. 不足与局限

- **资源算力未公开**：无法复现或比较训练/搜索成本。
- **对比基线不完全**：未与同期最新方法（如MermaidFlow、DebFlow）直接对比，可能导致结论时效性不足。
- **消融实验仅限MATH**：未在其他任务上验证各组件影响，无法确认组件贡献是否一致。
- **部分任务性能未达到SOTA**：HumanEval上A²Flow（92.4%）低于CoT SC的91.6%（但本身差异很小），且未超过MedPrompt等手动方法。
- **依赖于特定LLM作为算子提取器**：使用DeepSeek-v3，但未探讨对其他LLM的迁移性。
- **专家数据需求量**：需要一定量的标注案例（20%验证集），在数据稀缺场景下可能受限。
- **代码工作流表示限制**：假设每个算子为单输入单输出代码块，可能无法表达更复杂的控制流（如循环条件分支），但论文通过记忆机制部分弥补。
- **仅测试有限任务类型**：未涉及多模态、对话、网页交互等更复杂的代理场景。

（完）
