---
title: Evolving Agents
title_zh: 进化代理
authors: Leonardo Ranaldi
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.754.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 提出自主学习的伪符号抽象范式，与自主研究相关
tldr: 当前AI代理缺乏自主生成抽象概念的能力，本文提出EVA（进化代理）范式，通过元控制系统动态协调观察与交互，在线蒸馏出伪符号抽象表示，使代理能在开放环境中持续学习，为自主研究代理提供了关键能力。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1648, \"height\": 818, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 799, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 797, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 769, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 782, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 797, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 803, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 807, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 545, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.754/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 315, \"height\": 283, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1660, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 818, \"height\": 669, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 677, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 812, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 838, \"height\": 996, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 815, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 793, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 795, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.754/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 795, \"height\": 464, \"label\": \"Table\"}]"
motivation: 现有AI代理在开放动态环境中无法自主生成抽象概念，限制了长期适应能力。
method: 提出EVA范式，采用元控制系统通过伪符号抽象在线生成状态、动作和目标的抽象表示。
result: EVA使代理能够构建稳健的内部课程，在动态任务中表现优异。
conclusion: 伪符号抽象是实现真正自主代理的关键。
---

## Abstract
AI agents struggle to operate within open and dynamic environments because they lack a fundamental capacity: the autonomous generation of abstractions. Current models remain static entities, incapable of compressing the infinite complexity of the real world into generalisable concepts once their training phase has concluded.We introduce EVA (Evolving Agents), a novel paradigm for autonomous learning driven by pseudo-symbolic abstraction. EVA introduces a meta-control system that dynamically orchestrates observation and active interaction to distil on-the-fly abstract representations of states, actions, and goals. By disentangling contextual noise from pure logical reasoning, these pseudo-symbolic abstractions allow the agent to construct a highly robust internal curriculum.EVA leverages these self-generated abstractions to form an internal curriculum. This continuous compression of raw sensorimotor experience into reusable concepts allows the agent to independently guide its own exploration, planning, and error correction. Structured upon a bi-level evolutionary-developmental (Evo/Devo) framework, EVA demonstrates how the dynamic refinement of abstractions enables rapid adaptation to unforeseen scenarios. This approach resolves the domain mismatch problem and lays the groundwork for truly autonomous, continuously evolving AI models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

当前由大语言模型（LLM）驱动的 AI 代理在规划、推理和使用工具方面表现出色，但它们在动态、开放环境中仍然脆弱，无法持续适应和进化。其根本原因是这些代理缺乏一个关键能力：**自主生成和重用抽象概念**。现有的代理将推理、记忆和决策功能碎片化，无法将经验系统性地提炼为可跨上下文复用的能力，导致重复相同错误、丢失先前经验，尤其是在遭遇分布偏移时性能急剧下降。

论文旨在解决“如何让 AI 代理在持续交互过程中从经验中自主进化”这一根本问题。作者提出 EVA（**Ev**olving **A**gents）框架，将**准符号抽象（quasi-symbolic abstractions）** 作为核心表示，统一感知、策略执行和元控制，使代理能够在开放环境中持续学习、适应和恢复。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想
EVA 通过一个**元控制系统**动态协调观察与主动交互，在运行时蒸馏出准符号抽象（半结构化表示），这些抽象同时充当：
- 执行轨迹的结构化摘要；
- 情景记忆的检索接口；
- 控制器推导元状态的源表示。

### 2.2 准符号抽象机制
定义抽象为四元组：
\[ A = (V, T, C, E) \]
- \( V \)：变量、实体、工具或状态；
- \( T \)：状态‑动作转换；
- \( C \)：约束、前提条件；
- \( E \)：结果信号（进度、成功/失败）。

Perceptor 在每一步 \( t \) 根据轨迹窗口 \( \tau_t^{(k)} \) 动态诱导出抽象 \( A_t \)。

### 2.3 框架三大模块

| 模块 | 功能 | 核心操作 |
|------|------|----------|
| **Perceptor（感知器）** | 从观察和动作中抽象出结构 | 输入目标 \( g \)、当前观察 \( o_t \)、轨迹 \( \tau_t^{(k)} \)，输出 \( A_t \)；并计算序列置信度代理 \( c_t \) |
| **Actor（执行器）** | 基于抽象执行策略，产生环境动作 | 条件于 \( g, o_t, A_t \) 及可能的检索增强 \( eA_t \) 生成动作 \( a_t \) |
| **Controller（控制器）** | 元控制：决定是否继续、抽象、检索或回滚 | 从 \( A_t \) 和记忆 \( M_t \) 推导元状态 \( sm_t = [c_t, \delta_t, \nu_t, \ell_t] \)，选择元动作之一：**ACT、ABSTRACT、RETRIEVE、ROLLBACK** |

### 2.4 记忆管理
- **情景记忆**：存储抽象及其来源轨迹、结果标签（SUCCESS/FAILURE）。
- **程序记忆**：保留当前操作状态。
- 记忆更新与裁剪：基于动态效用分数 \( q_\eta(A_j) = \frac{n^+_j}{n^+_j + n^-_j} \cdot \gamma^{\Delta t_j} \)，保护最少复用次数 \( m \)，淘汰低效用或过时条目。

### 2.5 两阶段学习方案
- **第一阶段：元控制校准（外环）**：在分布 \( D_{env} \) 上校准控制器参数 \( \phi \)，使用策略梯度，优化后冻结。
- **第二阶段：交互时适应（内环）**：冻结控制器，通过 GRPO 更新 Perceptor 和 Actor 适配器，内环更新受置信度门控 \( \zeta_t = \mathbb{I}[c_t \ge \kappa_c] \) 约束。

### 2.6 推理循环
1. Perceptor 诱导 \( A_t \)；
2. Controller 从 \( A_t \) 和 \( M_t \) 推导元状态，选择元动作；
3. 若为 ACT → Actor 直接行动；若为 RETRIEVE → 从记忆检索结构相似抽象并绑定到当前上下文 → Actor 行动；若为 ABSTRACT → 扩展窗口重新诱导；若为 ROLLBACK → 恢复最近一致抽象并重新规划。

## 3. 实验设计

### 3.1 数据集 / 场景
| 类别 | 数据集 | 指标 |
|------|--------|------|
| 长程交互规划 | ALFWorld、WebShop、AppWorld | 成功率（ALFWorld）、平均得分（WebShop）、任务目标完成率（TGC）和场景目标完成率（SGC，AppWorld） |
| 分布偏移鲁棒性 | ScienceWorld 及自建变体 **SW‑Shift**（第 500 步注入域变化） | 总体成功率 |
| 知识密集型检索 | Natural Questions、TriviaQA、HotPotQA、2WikiMultiHopQA | Exact Match |

### 3.2 对比基线
- **提示型代理**：Direct、ReAct；
- **RL 框架**：GRPO；
- **技能学习+记忆增强**：SkillRL；
- **文本空间技能优化**：GEPA、SkillOpt；
- **检索增强**：Search‑R1、Search‑R2。

### 3.3 EVA 配置变体
- **EVA**：完整单代理，内环更新两者；
- **EVA‑Doc**：冻结权重，仅靠抽象构造/检索/文档巩固适应；
- **EVA‑S**：仅保留成功轨迹；
- **EVA‑A**：仅更新 Actor；
- **EVA‑M**：冻结权重多代理扩展（Planner + 专门 Executor）。

### 3.4 实现细节
- 框架：VeRL；
- 主干：主实验使用 **Qwen‑2.5‑7B**，额外实验使用 **Llama‑3‑8B** 和 **Mistral‑v0.3‑7B**；
- 超参数：学习率 \( 1\times10^{-6} \)，KL 系数 0.001，组大小 \( G=8 \)，置信度阈值 \( \kappa_c = 0.6 \)，记忆容量 512，检索 \( K_R = 3 \)。

## 4. 资源与算力

论文明确说明：**所有实验在 4 块 NVIDIA H200 GPU 上运行**。未报告具体训练时长或总 GPU 小时数。实际部署环境为单机多卡，算力规格中等偏上。

## 5. 实验数量与充分性

论文进行了丰富且系统的实验，包括：

- **主表（Table 1）**：在 Qwen‑2.5‑7B 上对比 8 个方法 + 5 个 EVA 变体，覆盖 6 个任务，共 13×6 ≈ 78 个主要数据点。
- **消融实验（Table 2 和 Figure 2）**：分别移除 Controller、记忆、准符号抽象、在线适应、外环、置信度门控等组件，以及对比冻结权重和替代记忆格式，共 11 个变体。
- **额外骨干网络（Table 7 & 8）**：在 Llama‑3‑8B 和 Mistral‑7B 上重复主实验，排除主干依赖。
- **训练动力学分析（Figure 5‑10）**：Controller 元动作分布、训练曲线、记忆效用增长、置信度阈值敏感性、跨模型迁移等，共 6 组深入分析。
- **检索任务（Table 3）**：额外 4 个知识数据集。

**充分性评价**：实验设计全面、对比基线新且强、消融细致、覆盖多种任务类型（交互、检索、分布偏移）。所有对比使用相同主干和预算，公平性较好。消融采用单一变量原则，结论可信。

## 6. 主要结论与发现

1. **EVA 全面超越所有基线**：在 ALFWorld 上达 88.7%（比最优基线 SkillOpt 高 4.4 点），ScienceWorld 上 78.2%，SW‑Shift 上 60.9%。平均逻辑错误率从 ReAct 的 20‑25% 降至 6.2%。相对收敛比达 3.7×，即仅用 Direct 约 27% 的交互就达到 90% 最终性能。
2. **准符号抽象是性能基石**：移除准符号抽象导致最大下降（ALFWorld −24.9 点），结构化表示带来的增益远超原始轨迹或自由文本技能。
3. **两阶段学习机制有效**：冻结权重的 EVA‑Doc 仍优于所有冻结基线，但全模型进一步通过内环权重适应获得 2.2 点提升，说明两种适应方式互补。
4. **失败轨迹的保留对分布偏移恢复至关重要**：EVA‑S（仅保留成功）在 SW‑Shift 上比完整 EVA 低 3.7 点。
5. **控制器元动作随时间动态变化**：初期 ABSTRACT 和 RETRIEVE 频繁，随记忆丰富变为以 ACT 为主。
6. **跨模型可迁移性**：Llama‑3‑8B 诱导的记忆可直接用于 Qwen‑2.5‑7B，差距不超过 4.5 点，证明抽象表示不依赖特定模型。

## 7. 优点

- **统一的表示基座**：将感知、记忆、元控制统一在准符号抽象上，减少异构接口，使系统内聚。
- **两阶段适应设计**：外环校准 + 内环适应分离了长期知识与短期调整，避免持续元更新带来的不稳定性。
- **模块化架构易于扩展**：Controller 的元动作空间可扩展（如多代理 DISPATCH），Actor 和 Perceptor 可独立升级。
- **深入细致的实验验证**：涵盖多种任务和骨干，消融完备，训练动力学分析直观揭示内部行为。
- **开源实现**：基于 VeRL 框架，超参数公开，便于复现。

## 8. 不足与局限

- **手动设计的抽象模式**：当前的 \( (V,T,C,E) \) 模式是手工定义的，未实现无监督或可微结构归纳，限制了向多模态或更复杂域的扩展。
- **置信度信号 \( c_t \) 是似然代理**：并非校准的结构正确性度量，纯依赖生成概率可能误导门控。修复方向：学习式置信度估计器。
- **检索依赖类型谓词匹配**：对表面形式不同的实体匹配能力有限，需更鲁棒的语义匹配。
- **计算开销**：Perceptor 和 Controller 的频繁调用（尤其 ABSTRACT 和 ROLLBACK）增加了推理延迟，稀疏路由是自然改进方向。
- **多代理扩展（EVA‑M）仍为初步**：仅在一组任务上验证，未系统研究团队规模与任务分解结构的扩展规律。
- **内部忠实性未保证**：与 CoT 类似，正确的答案不保证抽象 \( A_t \) 真正捕获了底层推理过程，存在推理‑表示不一致风险。
- **未在真实世界、非模拟场景中测试**：所有实验集中在模拟环境（ALFWorld、WebShop 等）和静态 QA 数据集，缺乏噪声、延迟、不完整反馈等现实挑战。

（完）
