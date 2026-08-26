---
title: An AI System for Autonomous Algorithm Evolution in Drug Development
title_zh: 用于药物开发中自主算法进化的人工智能系统
authors: "Zhou, Z., Nan, Y., Mou, M., Qian, Y., Liu, Y., Zuo, Z., Yang, H., Xu, W., Li, B., Jiang, W., Ren, Y., Liao, Y., Wang, Y., Li, Y., Yang, Q., Xi, Z., Mi, T., Sun, H., Liu, P., Zhu, F."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.16.745117v1.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 药物开发中的自主算法进化
tldr: 药物开发各阶段算法构建依赖于专家设计与任务特定优化，难以实现全流程自主进化。DrugEvolve系统引入多角色大语言模型，整合研究员、工程师和分析师职能，构建迭代设计、实现、评估与改进的闭环进化机制。该系统在目标识别、药物发现、临床前研究及临床试验等11项代表性任务中自主进化出任务专用算法，在120个基准测试集上取得显著性能提升，并展现了对生物序列、图、分子拓扑及文本等多种数据模态的稳健泛化，同时适用于预测性与生成性任务。DrugEvolve不仅为药物开发提供基础设施，也树立了可推广至更广阔科学领域的自主算法进化范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有药物开发算法高度依赖专家设计与任务级优化，缺少跨阶段自主进化的整体机制。
method: 提出DrugEvolve多角色大语言模型系统，融合研究员、工程师与分析职能，构建迭代设计-实现-评估-改进的闭环进化机制。
result: 在11项药物开发任务及120个基准测试集上自主进化算法，取得显著性能提升，并跨多种数据模态稳健泛化。
conclusion: 该AI系统为药物开发提供算法基础设施，并为更广泛科学领域提供可迁移的自主进化范式。
---

## 摘要
人工智能（AI）日益渗透到药物开发流程中。为了加速这一多阶段、多任务的过程，人们构建了许多算法，这些算法在很大程度上依赖于专家设计和劳动密集型的特定任务优化。鉴于AI驱动的药物开发加速被认为是跨多个阶段的累积效应，往往是协同效应，因此需要在整个流程中自主进化现有算法，以实现整体进步。在这里，我们提出了DrugEvolve，一个用于药物开发中系统化和自主算法进化的多角色大型语言模型系统。DrugEvolve通过整合研究者、工程师和分析师领域，实现了闭环进化过程，并利用科学知识和累积的进化经验，实现算法的迭代设计、实现、评估和改进。在涵盖靶点识别、药物发现、临床前研究和临床试验的11个代表性任务中，DrugEvolve自主进化了相应的特定任务算法，并在120个基准测试集上取得了显著的性能提升。此外，它展示了跨异构数据模态（从生物序列和图到分子拓扑和文本语言）的鲁棒泛化能力，并在预测和生成任务中都实现了收益。总的来说，这个人工智能系统不仅可以作为药物开发的算法基础设施，也可以作为更广泛科学领域的可迁移范式。

## Abstract
Artificial intelligence (AI) is increasingly permeating the drug development pipeline. Numerous algorithms for accelerating this multi-stage and multi-task process have been constructed, which depends heavily on expert design and labor-intensive task-specific optimization. Given that AI-driven acceleration of drug development is recognized as a cumulative, often synergistic, effect across multiple stages, the autonomous evolution of existing algorithms across the entire pipeline is demanded to achieve a holistic advancement. Here, we present DrugEvolve, a multi-role large language model system for systematic and autonomous algorithm evolution in drug development. DrugEvolve realizes a closed-loop evolution process by incorporating Researcher, Engineer, and Analyst domains, and enables an iterative design, implementation, evaluation, and refinement of algorithm by leveraging scientific knowledge and accumulated evolutionary experience. Across eleven representative tasks spanning target identification, drug discovery, preclinical study, and clinical trial, DrugEvolve autonomously evolved the corresponding task-specific algorithms and achieved substantial performance enhancement on 120 benchmark test sets. Moreover, it showed robust generalizabilities across heterogeneous data modalities (ranging from biological sequence and graph to molecular topology and textual language), and realized gains in both predictive and generative tasks. Collectively, this AI system can serve not only as an algorithmic infrastructure for drug development, but also as a transferable paradigm for broader scientific domains.

---

## 论文详细总结（自动生成）

# 论文总结：DrugEvolve——药物开发中的自主算法进化AI系统

## 1. 核心问题与研究动机（背景与意义）

- **背景**：人工智能正日益深入药物开发全流程，涵盖靶点识别、药物发现、临床前研究和临床试验等多个阶段。已有大量算法被构建用于加速这一多阶段、多任务流程。
- **核心痛点**：现有算法的构建高度依赖专家设计与劳动密集型的任务特定优化——每个任务都需要人工定制、调参和反复迭代，缺乏跨阶段的自动化能力。
- **关键洞察**：AI驱动的药物开发加速被认为是一种跨阶段的累积效应，甚至具有协同效应（各阶段算法的进步相互叠加放大）。因此，**仅在单个任务上优化算法是不够的**，需要在全流程中实现算法的自主进化，才能获得整体性（全局性）的进步。
- **研究意义**：该工作试图解决的是药物开发算法领域的"自动化天花板"问题——即从"人工设计算法"走向"AI自主进化算法"的范式转变。

## 2. 方法论：DrugEvolve 系统

### 核心思想

- DrugEvolve 是一个**多角色大语言模型（LLM）系统**，通过集成三个专业角色，实现算法的闭环自主进化，使算法能够**迭代地设计、实现、评估和改进**。

### 三个核心角色

1. **研究员（Researcher）**：负责算法设计，基于科学知识与进化经验提出算法改进方案和创新思路。
2. **工程师（Engineer）**：负责算法实现，将设计转化为可运行的代码，确保算法正确落地的工程可行性。
3. **分析师（Analyst）**：负责算法评估，通过实验验证算法性能，将结果反馈给研究员，形成闭环。

### 算法进化流程（闭环）

- **迭代进化循环**：设计（Researcher）→ 实现（Engineer）→ 评估（Analyst）→ 改进（回到 Researcher）→ 不断重复。
- **知识积累机制**：系统利用科学知识和**累积的进化经验**——每一轮迭代的成败经验都会沉淀下来，为后续进化提供参考，实现自我迭代式的能力增长。

## 3. 实验设计

### 任务覆盖范围

- **11 个代表性任务**，覆盖药物开发的四大阶段：
  - 靶点识别（target identification）
  - 药物发现（drug discovery）
  - 临床前研究（preclinical study）
  - 临床试验（clinical trial）

### 基准测试集

- 共 **120 个基准测试集**（benchmark test sets）用于性能评估。

### 数据模态覆盖

- 涵盖**异质数据模态**：
  - 生物序列（biological sequence）
  - 图（graph）
  - 分子拓扑（molecular topology）
  - 文本语言（textual language）

### 任务类型覆盖

- **预测性任务**（predictive tasks）
- **生成性任务**（generative tasks）

### 对比方式

- 从摘要内容推断，其主要对比的是**进化前后的算法版本**——即评估 DrugEvolve 自主进化出的任务专用算法相较于原算法（初始版本）的性能提升。

## 4. 资源与算力

- **论文中未明确说明**所使用的算力资源详情，包括：
  - GPU 型号与数量
  - 训练时长
  - 计算成本
  - 系统运行开销等
- 由于原始材料仅提供摘要级别的信息，无法获知具体的硬件配置、云资源使用量或大规模实验的总体算力消耗。这是一个信息缺口。

## 5. 实验数量与充分性

### 实验规模

- **规模较大**：涉及 11 项任务 × 120 个基准测试集，覆盖多个药物开发阶段，实验面较广。
- **模态/任务多样性充足**：涵盖序列、图、分子、文本等多模态，以及预测与生成两类任务，验证了系统的通用性。

### 充分性与客观性

- **优势**：多任务、多模态、多阶段的实验布局较为全面，能有效支撑"全流程自主进化"和"跨模态泛化"的核心主张。
- **局限性**：根据现有材料，未提及消融实验（如去除某个角色后系统性能如何变化、不同LLM后端的影响等），也没有与**其他自动化算法设计方法**（如传统AutoML、其他LLM智能体框架）的直接对比。因此，虽然绝对性能提升已证实，但相对先进性的证据尚不完整。

### 公正性

- 从摘要描述看，性能提升是在 120 个基准测试集上取得的"显著提升"，但缺乏对基准选择标准、初始基线版本设置、统计显著性检验方式等细节的描述，无法完全确认评测的公平性控制。

## 6. 主要结论与发现

1. **自主进化有效性**：DrugEvolve 能够在 11 个药物开发代表性任务中自主进化出任务专用算法，并取得显著的性能提升。
2. **跨模态泛化能力**：系统在不同数据模态之间展现出稳健的泛化能力——从生物序列、图到分子拓扑、文本语言均可适用。
3. **任务类型普适性**：在预测性任务和生成性任务两类场景中均实现了性能收益。
4. **双重定位**：该AI系统既可作为药物开发的**算法基础设施**，也可作为更广泛科学领域中的**可迁移范式**——即其他科学领域也可以借鉴这一自主算法进化框架。

## 7. 方法亮点与优势

- **闭环进化机制**：设计-实现-评估-改进的完整闭环，克服了传统"单轮优化"的局限，实现了持续自我改进。
- **多角色协同设计**：将研究员、工程师、分析师三个角色分工整合到LLM系统中，既保留了专业性分工，又实现了自动化协同，有效模拟了真实科研团队的工作模式。
- **经验积累机制**：系统能够复用累积的进化经验，具有"记忆"和"学习历史"的能力，使进化过程呈现递增式改善趋势。
- **端到端自动化**：从算法设计到实现再到评估的全部环节无需人工干预，大幅降低了对专家设计的依赖。
- **跨模态与跨任务泛化**：系统的架构与进化策略不依赖特定数据模态或任务类型，展现较强的通用性。
- **全流程覆盖**：对药物开发四大阶段的整体覆盖，体现了系统级视野而非单点优化，符合药物开发各阶段协同增效的实际需求。

## 8. 不足与局限

- **算力信息缺失**：论文未披露训练与运行DrugEvolve所需的算力资源、成本和时间开销，这会影响读者对系统落地可行性与复现成本的判断。
- **对比基线不明确**：从已有材料看，主要对比是进化前后的算法提升；缺少与其他自动化算法设计方法（如AutoML、其他基于LLM的智能体系统）的系统性对比，削弱了优势论断的排他性。
- **消融实验不足**：未提及对系统各组件（如三个角色各自的贡献、经验积累机制的作用）进行消融分析，无法确定各设计要素的独立贡献。
- **评测细节缺失**：缺乏对120个基准集选用标准、性能提升的统计显著性检验、评测指标的具体设定等细节的说明。
- **进化成本与效率未讨论**：自主进化可能需要大量迭代计算，每轮进化所需的时间与成本、以及在真实药物开发时间约束下是否可行，尚未讨论。
- **安全性问题未涉及**：药物开发关系到临床安全，由AI自主进化的算法在用于关键决策时的可靠性、可解释性和失败风险需进一步评估，摘要中未提及相关安全机制。
- **泛化边界未界定**："可迁移到更广阔科学领域"的论断尚需更多领域（如物理、材料等）的验证数据支撑。

---

**（完）**
