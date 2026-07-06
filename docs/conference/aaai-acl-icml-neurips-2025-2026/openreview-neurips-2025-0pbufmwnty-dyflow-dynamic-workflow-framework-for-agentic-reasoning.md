---
title: "DyFlow: Dynamic Workflow Framework for Agentic Reasoning"
title_zh: "DyFlow: 用于代理推理的动态工作流框架"
authors: "Yanbo Wang, Zixiang Xu, Yue Huang, Xiangqi Wang, Zirui Song, Lang Gao, Chenxi Wang, Xiangru Tang, Yue Zhao, Arman Cohan, Xiangliang Zhang, Xiuying Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=0pbUfmwNTy"
tags: ["query:cli-agent"]
score: 7.0
evidence: 用于代理推理的动态工作流框架，可应用于CLI代理
tldr: DyFlow提出动态工作流生成框架，针对大语言模型代理自适应构建推理流程，利用实时反馈增强鲁棒性和泛化能力，实验表明在复杂推理任务上优于静态流程方法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有代理工作流设计依赖人工且缺乏适应性，限制了复杂任务的效果。
method: 提出DyFlow框架，根据任务需求和实时反馈动态构建和调整推理过程。
result: 在多个基准测试中，DyFlow提升了推理任务的准确率和泛化性。
conclusion: 动态工作流生成是提升代理推理能力的关键方向。
---

## Abstract
Agent systems based on large language models (LLMs) have shown great potential in complex reasoning tasks, but building efficient and generalizable workflows remains a major challenge. Most existing approaches rely on manually designed processes, which limits their adaptability across different tasks. While a few methods attempt automated workflow generation, they are often tied to specific datasets or query types and make limited use of intermediate feedback, reducing system robustness and reasoning depth. Moreover, their operations are typically predefined and inflexible.
To address these limitations, we propose **DyFlow**, a dynamic workflow generation framework that adaptively constructs and adjusts reasoning procedures based on task requirements and real-time intermediate feedback, thereby enhancing cross-task generalization.
DyFlow consists of two core components: a designer and an executor. The designer decomposes complex problems into a sequence of sub-goals defined by high-level objectives and dynamically plans the next steps based on intermediate outputs and feedback. These plans are then carried out by the executor, which executes each operation using dynamic operators with context-aware parameterization, enabling flexible and semantically grounded reasoning.
We systematically evaluate DyFlow across diverse domains, including social reasoning, biomedical tasks, mathematical problem solving, and code generation.
Results demonstrate that DyFlow significantly outperforms existing baselines, achieving substantial Pass@k improvements and exhibiting robust generalization across diverse domains.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：基于大语言模型（LLMs）的代理系统在复杂推理任务中潜力巨大，但现有工作流设计主要依赖人工手动设计，缺乏对新任务的适应性；少数自动化方法局限于特定数据集或查询类型，且未能充分利用中间反馈，导致系统鲁棒性和推理深度不足；操作流程通常是预定义的，缺乏灵活性。
- **整体含义**：现有静态、固定模式的工作流限制了代理在跨任务场景下的泛化能力，亟需一种能根据任务需求和实时反馈动态调整推理流程的通用框架。

### 2. 论文提出的方法论
- **核心思想**：提出 **DyFlow**，一个动态工作流生成框架。该框架能够自适应地构建并调整推理过程，利用实时中间反馈增强跨任务泛化能力。
- **关键技术细节**：
  - **两个核心组件**：
    - **设计者（Designer）**：将复杂问题分解为一系列高级目标定义的子目标序列，并根据中间输出和反馈动态规划下一步操作。
    - **执行者（Executor）**：使用带有上下文感知参数化的动态算子执行每个操作，实现灵活且语义驱动的推理。
  - **动态工作流**：不是预定义固定步骤，而是基于任务特征和迭代反馈实时生成与调整，从而提升对多样化场景的鲁棒性。
- **公式或算法流程**（文字说明）：算法输入为任务描述，设计者首先解析任务，基于当前状态生成下一个子目标，执行者通过动态算子完成该子目标并返回结果及反馈，设计者根据反馈判断是否继续或调整策略，如此循环直至得到最终答案。无显式数学公式。

### 3. 实验设计
- **数据集/场景**：覆盖多个领域：社会推理（social reasoning）、生物医学（biomedical tasks）、数学问题求解（mathematical problem solving）、代码生成（code generation）。
- **基准（Benchmark）**：未明确具体基准名称，但评价指标为 Pass@k（生成多个候选答案中至少有一个正确的概率）。
- **对比方法**：声称与“现有基线”（existing baselines）对比，但未列出具体方法名称。推测包括静态工作流方法（如ReAct、Reflexion等）及少量自动化工作流方法。

### 4. 资源与算力
- 论文摘要及元数据中**未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅能推断实验在标准深度学习硬件上进行，但具体细节缺失。

### 5. 实验数量与充分性
- **实验数量**：至少涵盖四个不同领域的任务，每个领域应包含相应数据集。元数据仅提及“多个基准测试”，但未给出具体数字。
- **充分性**：论文宣称在各类任务上实现了显著的Pass@k提升，并体现了跨领域的稳健泛化能力。但若缺少消融实验、对比实验的详细列表（如是否与动态方法如AutoGPT对比），则充分性有限。从摘要看，未提到消融实验或细粒度分析，可能不够全面。
- **客观性与公平性**：由于缺乏对比方法名称和超参数设置细节，无法完全判断公平性。但多领域评估增加了结果的可信度。

### 6. 论文的主要结论与发现
- DyFlow在多个领域（社会推理、生物医学、数学、代码生成）上显著优于现有基线，Pass@k指标提升明显。
- 动态工作流生成是提升代理推理能力和泛化性的关键方向；利用实时反馈调整流程比静态流程更有效。

### 7. 优点
- **动态适应性**：摆脱了人工预定义工作流的限制，根据任务和中间反馈实时推理，提升泛化能力。
- **双组件结构**（设计师+执行者）明确分离规划与执行，易于模块化扩展。
- **多领域评估**：覆盖社会、生物、数学、代码四种类型任务，验证了跨领域有效性。

### 8. 不足与局限
- **实验细节不透明**：未列出具体数据集名称、对比方法、实验设置，使得复现和公平性评估困难。
- **算力资源未报告**：缺乏计算成本信息，难以衡量实际部署门槛。
- **消融分析缺失**：未分析各组件（如动态算子、反馈利用）的独立贡献，可能无法确认设计选择的最优性。
- **应用限制**：仅针对推理类任务，未涉及多轮对话、工具调用等更复杂的代理场景；动态规划可能引入额外延迟与开销。

（完）
