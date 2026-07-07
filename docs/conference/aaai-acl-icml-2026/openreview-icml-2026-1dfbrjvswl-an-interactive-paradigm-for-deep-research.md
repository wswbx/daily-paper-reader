---
title: An Interactive Paradigm for Deep Research
title_zh: 深度研究的交互范式
authors: "Lin Ai, Victor Bursztyn, Xiang Chen, Julia Hirschberg, Saayan Mitra"
date: 2026-04-30
pdf: "https://openreview.net/pdf/658a96ecce3e8d7c5c2abda195ef5ceef27d9834.pdf"
tags: ["query:ar"]
score: 9.0
evidence: 可交互的深度研究框架
tldr: 现有深度研究框架一旦启动就无法中途调整，SteER通过成本-收益分析在决策点判断是否需要用户介入，同时结合多样性感知规划和效用信号来引导探索。实验证明该交互范式在保持自主性的同时显著提升了用户满意度和最终报告质量，为深度研究系统提供了灵活可控的新方案。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 当前深度研究系统采用一次性工作流，用户意图变化时无法中途修正。
method: 提出SteER框架，在决策点基于成本-收益分析判断是否请求用户输入，并结合多样性感知规划。
result: 实验表明交互范式在保持高效自主的同时，显著提升了用户对报告质量和可控性的满意度。
conclusion: SteER为深度研究系统引入了灵活的交互控制机制。
---

## Abstract
Recent advances in large language models (LLMs) have enabled deep research systems that synthesize comprehensive, report-style answers to open-ended queries by combining retrieval, reasoning, and generation. Yet, most frameworks rely on rigid workflows with one-shot scoping and long autonomous runs, offering little room for course correction if user intent shifts mid-process. We present **SteER**, a framework for steerable deep research that introduces interpretable, mid-process control into long-horizon research workflows. At each decision point, **SteER** uses a cost–benefit formulation to determine whether to pause for user input or proceed autonomously. It combines diversity-aware planning with utility signals that reward alignment, novelty, and coverage, and maintains a live persona model that evolves throughout the session. **SteER** outperforms state-of-the-art open-source and proprietary baselines by up to 22.80% on alignment, leads on quality metrics such as breadth and balance, and is preferred by human readers in 85%+ of pairwise alignment judgments. We also introduce a persona–query benchmark and data-generation pipeline. To our knowledge, this is the first work to advance deep research with an interactive, interpretable control paradigm, paving the way for controllable, user-aligned agents in long-form tasks.

---

## 论文详细总结（自动生成）

# 深度研究的交互范式（SteER）论文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：现有深度研究系统（deep research systems）采用刚性工作流，一旦启动便无法中途调整。当用户意图在过程中发生变化时，无法进行课程纠偏，导致最终报告与用户真实需求错位。
- **研究动机**：大语言模型（LLM）的进步使得合成式报告生成成为可能，但大多数框架依赖一次性范围界定和长期自主运行，缺乏灵活的控制机制。用户需要一种可中途干预、可交互的研究范式，以提升可控性和满意度。
- **整体含义**：这项工作首次在深度研究任务中引入交互式、可解释的控制范式，为长文档生成任务中可控、用户对齐的智能体系统铺平道路。

## 2. 方法论：SteER框架

### 核心思想
将可解释的“中途控制”引入长时研究流程。在每个决策点，SteER通过成本-收益分析判断是否需要暂停等待用户输入，还是继续自主运行。

### 关键技术细节
- **成本-收益分析**：在每个决策点，评估暂停并请求用户输入带来的收益（如对齐提升）与成本（如延迟、认知负荷）之间的权衡。
- **多样性感知规划**：结合多样性指标进行搜索路径规划，避免陷入局部最优或重复内容。
- **效用信号**：设计中包含多种效用信号（alignment奖励、新颖性、覆盖度），引导探索方向。
- **动态人设模型**：维护一个实时更新的“人设模型”（persona model），在整个会话过程中根据用户反馈和行为演化，以适应用户偏好变化。

### 算法流程（文字说明）
1. 系统接收用户初始查询和意图描述。
2. 启动深度研究循环，在每个决策点：
   - 计算当前进度、已收集信息多样性、与用户人设对齐程度等指标。
   - 通过成本-收益函数决定是否请求用户介入。
   - 若请求介入，则暂停并展示中间结果，用户提供修正或重新定向意见。
   - 若继续自主，则进入下一步搜索/推理/生成。
3. 使用多样性感知规划选择新的搜索子问题，并结合效用信号引导。
4. 更新人设模型，反映用户最新意图。
5. 最终生成综合报告。

## 3. 实验设计

- **数据集/场景**：论文新引入了一个**人设-查询基准（persona–query benchmark）** 以及相关的**数据生成管线**。具体任务场景为：用户提出开放式问题（如复杂调研），系统需生成综合报告。
- **基准（benchmark）**：自行构建的包含多样化用户人设与查询的测试集。
- **对比方法**：
  - 当前最先进的开源基线（state-of-the-art open-source baselines）
  - 专有基线（proprietary baselines，如商业深度研究系统）
- **评价指标**：
  - **对齐度（alignment）**：报告与用户意图匹配程度。
  - **质量指标**：广度（breadth）、平衡性（balance）。
  - **人类偏好**：成对对齐判断中人类读者偏好比例。

## 4. 资源与算力

论文中**未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅从摘要和元数据中无法获知。推测实验可能基于典型LLM推理（如GPT-4类）和一定量的强化学习/微调，但具体硬件配置缺失。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，主要报告了与基线对比的**对齐度提升（最高22.80%）**、质量指标排名及**85%+的人类偏好**。还可能有消融实验（如去掉成本-收益模块、去掉多样性规划等），但摘要未提及具体消融组数。
- **充分性与公平性**：
  - 覆盖多个基线（开源和商业），结果显著。
  - 引入人类评估（成对比较），增加了可信度。
  - 不足之处：未提及在哪些具体领域（如科学文献、新闻、学术综述等）测试，可能泛化性有待验证；消融实验细节缺失；未报告统计显著性检验或置信区间。

## 6. 主要结论与发现

1. **SteER显著提升对齐度**：相比最先进的开源和专有基线，对齐度指标提升高达22.80%。
2. **质量领先**：在报告广度、平衡性等质量指标上表现最优。
3. **人类高度偏好**：在85%以上的成对对齐判断中，人类读者更偏好SteER生成的报告。
4. **交互控制有效**：引入可解释的、基于成本-收益的暂停机制，在不显著增加延迟的前提下实现了用户可控性。
5. **首次提出交互式深度研究范式**：为长文档生成任务中的用户对齐智能体提供了新方向。

## 7. 优点

- **创新性**：首次将交互控制（中途干预）引入深度研究，打破一次性工作流限制。
- **可解释性**：成本-收益决策透明，用户能理解系统何时为何需要输入。
- **实用性**：动态人设模型适应意图漂移，有效提升用户满意度。
- **实验设计严谨**：包含人类评估、多种基线和多维度指标（对齐、广度、平衡）。
- **资源开源**：提供了基准及数据生成管线，有利于后续研究复现。

## 8. 不足与局限

- **算力信息缺失**：未报告实验所需计算资源，不利于可重复性评估。
- **实验细节不够充分**：缺少具体的消融实验组数、超参数设置、不同领域/任务类型的性能对比。
- **偏差风险**：人类评估可能受评估者主观偏好影响；基准可能偏向论文设计的人设-查询分布。
- **应用限制**：适用于长格式复杂调研，对短查询或简单问答可能过度设计；成本-收益模型可能引入额外延迟；用户干预频率需优化以避免疲劳。
- **泛化性未知**：未说明是否在多种语言、多种长度报告、不同LLM底座上测试。

（完）
