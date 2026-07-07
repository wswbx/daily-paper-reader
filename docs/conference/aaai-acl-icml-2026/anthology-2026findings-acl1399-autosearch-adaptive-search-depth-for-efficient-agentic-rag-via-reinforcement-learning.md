---
title: "AutoSearch: Adaptive Search Depth for Efficient Agentic RAG via Reinforcement Learning"
title_zh: "AutoSearch: 基于强化学习的自适应搜索深度实现高效智能体RAG"
authors: "Jingbo Sun, Wenyue Chong, Songjun Tu, Qichao Zhang, Yaocheng Zhang, Jiajun Chai, Xiaohan Wang, Wei Lin, Guojun Yin, Dongbin Zhao"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1399.pdf"
tags: ["query:ar"]
score: 5.0
evidence: AutoSearch通过强化学习自适应搜索深度，提升自主研究智能体的检索效率
tldr: 智能体RAG系统中冗余搜索步导致高计算成本。本文提出AutoSearch，通过强化学习自适应确定每个问题所需的最小搜索深度，在保持精度的同时大幅降低延迟。该工作可应用于自主研究任务中的多步检索优化。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1399/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 788, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1399/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1521, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1399/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1659, \"height\": 950, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1399/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 784, \"height\": 611, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1399/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 722, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1399/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1640, \"height\": 1018, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1399/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1542, \"height\": 1393, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1399/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 821, \"height\": 718, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1399/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1539, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1399/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1434, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1399/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1382, \"height\": 518, \"label\": \"Table\"}]"
motivation: 智能体RAG中搜索步冗余，固定深度限制导致复杂问题探索不足。
method: 提出AutoSearch，利用强化学习根据问题复杂度动态调整搜索深度。
result: 在多个基准上实现了精度与效率的最佳权衡，减少了不必要的搜索步。
conclusion: 自适应搜索深度策略可显著提升自主研究智能体的检索效率。
---

## Abstract
Agentic retrieval-augmented generation (RAG) systems enable large language models (LLMs) to solve complex tasks through multi-step interaction with external retrieval tools. However, such multi-step interaction often involves redundant search steps, incurring substantial computational cost and latency. Prior work limits search depth (i.e., the number of search steps) to reduce cost, but this often leads to underexploration of complex questions. To address this, we first investigate how search depth affects accuracy and find a minimal sufficient search depth that defines an accuracy-efficiency trade-off, jointly determined by question complexity and the agent’s capability. Furthermore, we propose AutoSearch, a reinforcement learning framework that evaluates each search step via self-generated intermediate answers. By a self-answering mechanism, AutoSearch identifies the minimal sufficient search depth and promotes efficient search by rewarding its attainment while penalizing over-searching. In addition, reward mechanisms are introduced to stabilize search behavior and improve answer quality on complex questions. Extensive experiments on multiple benchmarks show that AutoSearch achieves a superior accuracy-efficiency trade-off, alleviating over-searching while preserving search quality.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：Agentic RAG（检索增强生成）系统通过多步交互调用外部检索工具来解决复杂任务，但多步搜索常包含冗余步骤，导致高计算成本和延迟。
- **现有方法局限**：以往工作通过固定或被动限制搜索深度（如惩罚搜索次数）来降低成本，但这种方式往往导致复杂问题探索不足，损害最终答案准确性。
- **关键发现**：作者首先系统研究了搜索深度对准确率的影响，发现存在一个**最小充分搜索深度**（minimal sufficient search depth），该深度由**问题复杂度**和**智能体自身能力**共同决定，构成了准确率与效率的权衡边界。
- **论文目标**：提出一种让智能体能够自适应调整搜索深度的方法，在保持答案质量的前提下最大化搜索效率。

## 2. 方法论

### 核心思想
- 提出 **AutoSearch**，一个基于强化学习（RL）的自适应搜索框架，通过**自我生成中间答案**来评估每一步的搜索必要性，从而动态确定最优搜索深度。
- 采用 **PPO（Proximal Policy Optimization）** 算法进行训练，并设计了三个互补的奖励信号。

### 关键技术细节与奖励设计

#### (1) 基础奖励（Base Reward）
- **格式奖励**：强制执行结构化动作格式（<think>、<search>、<answer>），对格式错误或重复检索进行惩罚。
- **结果奖励**：最终答案与真实答案的精确匹配（Exact Match, EM），仅在最后一步赋予。

#### (2) 搜索效率奖励（Search Efficiency Reward）
- **中间答案生成**：每一步让智能体基于当前轨迹生成中间答案（使用特定prompt）。
- **能力感知最优深度**：定义为最早出现中间答案与真实答案匹配的步骤 \( t_c \)；若始终无法正确回答则设为 -1。
- **奖励分配**：
  - 如果 \( t_c < 0 \)（整体未能答对），所有步给予小正奖励鼓励继续搜索。
  - 如果 \( 0 < t \leq t_c \)（有效搜索），给予正奖励，且 \( t_c \) 越小奖励越高。
  - 如果 \( t > t_c \)（过度搜索），给予负奖励惩罚冗余。
- 该设计使得累计奖励在最优深度处达到峰值，过低和过高都会降低奖励。

#### (3) 搜索质量奖励（Search Quality Reward）
- 基于中间答案与真实答案的 **F1 分数增益**：当前步的F1减去历史最佳F1，鼓励每一步提供有意义的新信息。

#### 训练过程
- 整体奖励为三者之和。
- 训练时对检索到的外部观察 token 进行掩码（mask），避免影响策略梯度。
- PPO 目标函数为标准形式，使用 GAE 估计优势。

## 3. 实验设计

### 数据集与场景
- **通用 QA（单跳）**：NQ、TriviaQA、PopQA
- **多跳 QA（复杂推理）**：HotpotQA、2WikiMultiHopQA、Bamboogle
- 覆盖不同难度和知识来源，评价全面。

### 基准方法（Baselines）
- **Search-R1**：结局奖励式RL，允许自推理与搜索交替。
- **StepSearch**：步进式奖励，利用信息增益并惩罚冗余。
- **HIPRAG**：使用外部LLM监督每一步搜索必要性，减少过度搜索。

### 评估指标
- **答案质量**：Exact Match (EM)、F1
- **搜索效率**：搜索深度 (SD)、搜索效率 (SE = EM / SD)、过度搜索比率 (OSR，即能在最后一步之前正确回答的比例)

### 训练与评估设置
- 使用 Qwen2.5 系列 **3B** 和 **7B** 两个基模型（Base/Instruct）。
- 训练数据混合 NQ 和 HotpotQA 训练集。
- 检索器：2018 Wikipedia 快照 + E5 检索器，每步采样3篇文档。
- 所有基线均复现以保证公平比较。

## 4. 资源与算力

论文明确说明了训练配置：
- **硬件**：单节点配备 **8 张 NVIDIA H20 GPU**
- **批大小**：总 batch size 512，PPO mini-batch 256
- **微批大小**：actor 64，critic 8
- **训练步数**：总共 **1005 个优化步骤**
- **学习率**：actor 1×10⁻⁶，critic 1×10⁻⁵，带 warm-up
- **最大上下文长度**：4,096 tokens

该资源配置属于中等规模训练成本，未提及预训练或大规模分布式训练。

## 5. 实验数量与充分性

- **主实验**：在6个数据集上，分别对3B和7B模型全面比较4种方法，涵盖 EM、F1、SD、SE 和 OSR 指标，表格数据丰富。
- **消融实验**：对三个奖励组件分别去除（w/o Base Reward、w/o Search Efficiency Reward、w/o Search Quality Reward），在6个数据集上分析EM、F1、SD、OSR的变化。
- **RL算法对比**：将PPO替换为GRPO（基于结局奖励），在6个数据集上比较EM、F1、SD、SE，发现GRPO也能取得相近效果。
- **训练动态分析**：记录了搜索时间、有效动作比率、搜索深度和token长度随训练步数的变化曲线，并与Search-R1和StepSearch对比。
- **案例分析**：提供了5个典型对比案例（与Search-R1、StepSearch、HIPRAG），展示AutoSearch的检索效率和准确性优势。

**充分性评价**：实验覆盖了不同复杂度、不同模型规模、不同奖励组合、不同RL算法，并且有定性分析，整体设计较为充分、客观、公平。所有基线均复现，指标定义清晰。

## 6. 主要结论与发现

1. **存在最小充分搜索深度**：该深度由问题复杂度和智能体能力共同决定，超出该深度会导致过度搜索且准确率下降。
2. **AutoSearch 实现了最佳精度-效率权衡**：在绝大多数数据集上，AutoSearch 的 EM/F1 达到或超越最强基线，同时搜索深度最低、搜索效率最高、过度搜索比率最低。
3. **三个奖励组件缺一不可**：消融实验表明，去除任何一个都会损害精度或效率，特别是效率奖励对控制深度至关重要，质量奖励能提升复杂问题的答案质量。
4. **PPO 和 GRPO 均可有效训练**：使用 GRPO 也能取得与 PPO 相当的性能，说明方法的通用性强。
5. **训练稳定高效**：AutoSearch 在训练后期搜索深度稳定降低、有效动作比率高、token长度下降，优于 Search-R1 和 StepSearch。

## 7. 优点

- **自适应能力**：无需外部LLM或预定义阈值，完全依靠智能体自身生成的中间答案动态调整搜索深度，适应不同问题和模型能力。
- **奖励设计巧妙**：效率奖励基于能力感知最优深度，形成峰值激励；质量奖励通过F1增益鼓励非冗余信息获取；三者协同效果好。
- **简单高效**：方法框架清晰，不依赖复杂的外部监督或两阶段训练，实验表明训练稳定且收敛快。
- **实验充分、对比公平**：在多个数据集、两个参数规模、四种基线方法下验证，并进行了消融、RL算法对比和案例分析，结论可信。
- **性能卓越**：在保持甚至提升准确率的同时大幅降低搜索步数，改善了实际部署中的延迟和成本。

## 8. 不足与局限

- **实验搜索深度范围有限**：论文仅探索了较少的最大搜索步数（如0-4步），对于需要极长搜索链的极端复杂任务（如科研文献调研、法律检索等）的泛化能力未验证。
- **依赖中间答案的准确性**：效率奖励的核心依赖于即时生成的中间答案与真实答案的匹配。如果模型在早期生成错误但后续纠正，奖励机制可能误判最优深度。论文未分析这种误判的影响。
- **未讨论对长尾或开放域问题的泛化**：训练集仅混合NQ和HotpotQA，虽然测试了其他数据集，但领域覆盖有限（主要为百科知识类QA），对非事实型、观点性或实时性更强的任务表现未知。
- **仅使用单一基模型（Qwen2.5系列）**：未在更多不同架构或规模的模型（如Llama、Mistral）上验证，可能限制结论的普适性。
- **未对比计算代价**：虽然报告了搜索步数和效率，但未详细对比训练/推理的总耗时或FLOPs，不同方法的计算成本差异可能被低估。

（完）
