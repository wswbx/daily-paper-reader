---
title: Automating Complex Document Workflows via Stepwise and Rollback-Enabled Operation Orchestration
title_zh: 自动复杂文档工作流的逐步可回滚操作编排
authors: "Yanbin Zhang, Hanhui Ye, Yue Bai, Qiming Zhang, Liao Xiang, Wu Mianzhi, Renjun Hu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40974/44935"
tags: ["query:cli-agent"]
score: 6.0
evidence: 工作流自动化智能体，逐步编排类似CLI任务自动化
tldr: 现有代理系统难以自动化多步会话级工作流，本文提出AutoDW框架，通过逐步规划和回滚机制实现文档操作编排。该方法基于用户指令和文档状态增量执行API动作，并支持参数和API级别的故障恢复。实验表明AutoDW在复杂文档任务中显著提升自动化效率和鲁棒性，为工作流自动化提供了新的执行范式。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有代理系统只能执行孤立指令，无法高效自动化多步会话级文档工作流。
method: 提出AutoDW框架，通过逐步API动作规划、意图过滤和回滚机制实现文档操作编排。
result: 在复杂文档任务中，AutoDW相比基线方法显著提升了自动化完成率和鲁棒性。
conclusion: 逐步可回滚的操作编排有效解决了多步工作流自动化难题，具有实际应用价值。
---

## Abstract
Workflow automation promises substantial productivity gains in everyday document-related tasks. While prior agentic systems can execute isolated instructions, they struggle with automating multi-step, session-level workflows due to limited control over the operational process. To this end, we introduce AutoDW, a novel execution framework that enables stepwise, rollback-enabled operation orchestration. AutoDW incrementally plans API actions conditioned on user instructions, intent-filtered API candidates, and the evolving states of the document. It further employs robust rollback mechanisms at both the argument and API levels, enabling dynamic correction and fault tolerance. These designs together ensure that the execution trajectory of AutoDW remains aligned with user intent and document context across long-horizon workflows. To assess its effectiveness, we construct a comprehensive benchmark of 250 sessions and 1,708 human-annotated instructions, reflecting realistic document processing scenarios with interdependent instructions. AutoDW achieves 90% and 62% completion rates on instruction- and session-level tasks, respectively, outperforming strong baselines by 40% and 76%. Moreover, AutoDW also remains robust for the decision of backbone LLMs and on tasks with varying difficulty.

---

## 论文详细总结（自动生成）

# 论文《Automating Complex Document Workflows via Stepwise and Rollback-Enabled Operation Orchestration》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有基于大语言模型（LLM）的代理系统能够执行孤立指令（如单个文档操作），但在自动化**多步、会话级**复杂文档工作流时表现不佳。主要瓶颈在于对操作过程的控制力不足：缺乏上下文敏感的实时调整能力，且没有有效的错误恢复机制，单次错误的API调用会级联传播，导致整个会话失败。
- **研究动机**：文档处理占据知识工作者大量时间，自动化这些工作流能显著提升生产力。虽然已有工具使用、工作流编排、文档代理等方向的研究，但它们要么依赖人工验证（人机循环），要么采用预先确定的计划且无错误恢复，无法胜任真实场景下具有高度指令依赖性和长跨度（每个会话需15-75次API调用）的文档自动化任务。
- **整体含义**：提出AutoDW框架，通过**逐步规划**与**自适应回滚**相结合，实现精确可控的操作编排，使代理在执行过程中持续与用户意图及动态文档状态对齐，从而大幅提升长程工作流的自动化成功率。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
将复杂文档工作流分解为一系列原子API调用，每次只规划并执行一个API，执行后立即验证其效果与用户意图是否对齐，若不对齐则触发**两级回滚机制**（参数级、API级）进行动态纠正。

### 关键技术细节（包含三个模块）

1. **逐步规划模块（Stepwise Planning）**
   - 每个时刻，基于当前完整文档状态（编码为7个组件：文档信息、段落、表格、图像、页面布局、交互元素、样式）、用户指令和已执行API历史，先生成一个**子指令**（对应一个原子操作）。
   - 子指令通过**8类意图分类器**（基于178M参数BERT模型，微调于3,315条指令-意图对，测试准确率98%）过滤出top-3候选意图，从预定义API库（共74个API）中检索相关API。
   - 最终由LLM根据子指令、候选API列表和上下文生成具体API及其参数。

2. **API执行与状态跟踪模块（Execution & State Tracking）**
   - 在Python运行时环境中执行选定的API，并提取更新后的文档状态（包含7类组件，每个组件有详细属性，如段落内容、表格细胞签名等）。
   - 若状态解析失败，则视为非法执行结果，触发API级回滚。

3. **自适应回滚模块（Adaptive Rollback）**
   - **变化分析**：通过多层面分析器（结构、内容、格式、样式、表格、超链接）对比执行前后的文档状态，输出变化描述Δ。
   - **对齐验证**：LLM验证器接收Δ、子指令、当前状态和历史API，输出通过/失败决策、置信度分数（0-1）及解释。
   - **回滚策略**：若验证失败且置信度≥0.6，则先尝试**参数级回滚**（保持API选择，仅修改参数）；若仍失败，则升级为**API级回滚**（重新选择新API）。默认只进行一轮双级回滚，实验证明此设计在性能与成本间取得最佳平衡。

### 公式或算法流程（文字说明）
- 输入：初始文档状态S₀，用户指令序列{I₁, I₂,...}；输出：API动作序列P = [A₁, A₂,...]
- 循环处理每条指令：
  1. 生成子指令 → 意图分类 → 检索候选API
  2. LLM生成具体API动作
  3. 执行API，获取新状态S_t
  4. 分析状态变化Δ
  5. 验证对齐性
  6. 若通过则接受动作，否则执行回滚（参数级→API级）
  7. 继续下一个子指令，直至当前指令完成

## 3. 实验设计：数据集/场景、基准、对比方法

### 数据集/场景
- **构建新基准 DWBench**：包含250个多轮会话，共1,708条人工标注指令，每条指令含可行API序列。
- **特征**：每会话指令数4-8条（平均6.8），每会话API调用数15-75（平均34.8），每条指令所需API数2-22（平均5.1）。指令间高度依赖。
- **文档类型**：Word文档自动化（双语，中文+英文），覆盖8类意图对应的74个API。
- **评估指标**：操作正确性——通过LLM Judge比较执行后的文档状态与地面真实状态是否语义等价。LLM Judge与人工判断的一致性经过专门验证。

### 对比方法
1. **检索仅（Retrieval-only）**：语义匹配用户指令与API描述，用默认参数直接执行，无动态规划。
2. **推理仅（Reasoning-only）**：将全部API库放入LLM上下文，由LLM直接选择API并生成参数，无验证。
3. **混合方法（Hybrid）**：参照PPTC论文的多阶段流水线（指令理解→抽象意图→规则映射→API序列），一次生成完整计划，无回滚。
4. **AutoDW（本文方法）**：逐步规划+自适应回滚。

### 评测维度
- **指令级准确率（iACC）**：每条指令独立评估。
- **会话级准确率（sACC）**：从头开始顺序执行所有指令后评估。
- 同时报告平均API调用数、平均token使用量。

## 4. 资源与算力

论文中**未明确说明使用的GPU型号、数量、训练时长**。仅提及BERT意图分类器是微调于3,315条数据（测试准确率98%），但未给出微调的资源信息。LLM推理部分使用了DeepSeek-V3（默认）、Qwen-Plus、Gemini-2.5-Pro、GPT-4.1，均为通过API调用的商用或开源模型，未报告具体硬件配置。因此算力消耗不可量化。

## 5. 实验数量与充分性

### 实验组数
- **主对比实验**：AutoDW vs 三种基线，报告iACC、sACC及成本指标（Table 2）。
- **鲁棒性实验**：4种不同LLM（Table 3），并进一步按指令难度（简单/中等/困难，以API数≤3、4-6、≥6划分）分层报告iACC。
- **消融实验**：回滚机制消融，比较无回滚、仅参数级回滚、AutoDW（一轮双级）、两轮回滚四种配置的精度与token成本（Figure 3）。
- **额外分析**：验证了LLM Judge与人工判断的一致性（简短提及），以及阈值0.6的敏感性分析（简要提及）。

### 充分性与客观性
- **充分性**：覆盖了主要基线（每种范式一个代表）、多种LLM、难度分层、关键模块消融，实验设计较为完整。
- **客观性**：采用自动化评估（LLM Judge）并验证了与人工判断的一致性，减少了主观偏差。重复3次实验取平均，统计可靠。
- **公平性**：基线方法均基于相同API库和文档状态提取机制（确保比较公平），但混合方法baseline来自PPTC论文实现，其设计细节可能不完全匹配本文框架，存在一定实现偏差风险。

## 6. 论文的主要结论与发现

1. **AutoDW显著优于所有基线**：iACC达90.33%，sACC达62.00%，相比最强的混合方法分别提升40.1%和76.1%，且仅多消耗26.5%的token。
2. **逐步规划与回滚机制的关键作用**：消融实验显示，无回滚的逐步规划仅35.6% sACC，加入一轮双级回滚后提升至62.0%，相对增益74%，证明回滚模块是核心贡献。
3. **鲁棒性好**：在多个LLM（DeepSeek-v3、Qwen-Plus、Gemini-2.5-Pro、GPT-4.1）上均保持高准确率（iACC 82.8%-92.0%），且不同LLM间差异主要出现在会话级而非指令级，说明框架能较好地利用更强LLM的推理能力。对于困难指令（≥6个API），iACC仅比总体低4.4%，表明对复杂度不敏感。
4. **成本-性能平衡出色**：一轮双级回滚在精度提升与token消耗之间达到最优，两轮回滚增益微弱。

## 7. 优点：方法或实验设计上的亮点

- **方法设计亮点**：
  - **逐步规划而非一次性规划**：避免了长程任务中计划失效和状态漂移问题。
  - **双级回滚的层次化错误恢复**：参数级回滚更轻量，API级回滚更彻底，且通过验证器置信度自适应触发，避免过度纠正。
  - **状态跟踪完善**：7个组件、每组件详尽的属性列表（如表1），确保LLM有足够上下文进行决策。
  - **小BERT+LLM混合意图分类**：用小巧的BERT模型高效过滤候选API，减少LLM推理负担，同时保留top-3以考虑歧义。
- **实验设计亮点**：
  - **构建了高难度的真实基准DWBench**：含复杂依赖、长API序列、人工标注地面真值，填补了文档自动化执行评估的空白。
  - **操作正确性评估采用LLM Judge并验证与人工一致**，提高了评估可信度。
  - **消融实验揭示核心贡献**：明确量化了回滚机制带来的74%相对提升。

## 8. 不足与局限

- **实验覆盖的局限性**：
  - 仅评估了Word文档场景，未扩展到表格（如Excel）、PDF、演示文稿等其他格式，通用性有待验证。
  - 仅使用了74个API，虽然覆盖8类意图，但真实场景可能需更多、更细粒度的API。
  - 基准数据规模较小（250会话、1708指令），且中文+英文混合，可能不足以代表所有语言和文档类型。
- **偏差风险**：
  - LLM Judge作为评估器存在潜在偏差（可能偏好符合自身生成风格的答案），尽管作者验证了与人工判断的一致性，但样本较少。
  - 基线混合方法（Hybrid）可能未完全优化（如无任何错误恢复），导致其性能偏低，从而使AutoDW的领先幅度被放大。
  - 回滚阈值0.6仅在当前数据集上调优，缺乏跨域泛化验证。
- **应用限制**：
  - 依赖商用LLM API调用，成本不菲（平均每会话284.9k tokens），且对网络、延迟敏感。
  - 需要预定义API库且维护成本高，新增操作需手动扩展。
  - 未处理多轮对话中历史错误累积导致回滚难以恢复的极端情况（仅支持单次回滚，两轮提升有限）。
- **资源信息缺失**：未报告模型训练和推理的硬件配置、能耗、时间等，可复现性受影响。

（完）
