---
title: "From Experience to Skill: Multi-Agent Generative Engine Optimization via Reusable Strategy Learning"
title_zh: 从经验到技能：通过可复用策略学习的多智能体生成引擎优化
authors: "Beining Wu, Fuyou Mao, Jiong Lin, Cheng Yang, Jiaxuan Lu, Yifu Guo, Siyu Zhang, Yifan Wu, Ying Huang, Fu Li"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.2149.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 技能提炼；可复用策略；多智能体框架
tldr: MAGEO将生成引擎优化重构为策略学习问题，提出多智能体框架，通过协调规划、编辑和保真评估，将验证有效的编辑模式逐步蒸馏为可复用的引擎特定优化技能。这项工作展示了技能从经验中提炼和迁移的过程，与基于技能的强化学习高度相关。实验证明MAGEO能有效跨任务和跨引擎转移技能，提升优化效率。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2149/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1637, \"height\": 721, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2149/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1647, \"height\": 807, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2149/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1645, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2149/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 809, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2149/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 796, \"height\": 517, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2149/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 646, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2149/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1645, \"height\": 1260, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2149/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 797, \"height\": 639, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2149/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 790, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2149/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 799, \"height\": 640, \"label\": \"Table\"}]"
motivation: 现有生成引擎优化方法逐实例优化，无法积累和迁移有效策略。
method: 提出MAGEO多智能体框架，将验证过的编辑模式蒸馏为可复用的引擎专用优化技能。
result: MAGEO跨任务和跨引擎转移技能，显著提升优化效果和效率。
conclusion: 为技能学习和迁移在生成引擎优化中提供了有效范例。
---

## Abstract
Generative engines (GEs) are reshaping information access by replacing ranked links with citation-grounded answers, yet current Generative Engine Optimization (GEO) methods optimize each instance in isolation, unable to accumulate or transfer effective strategies across tasks and engines. We reframe GEO as a strategy learning problem and propose MAGEO, a multi-agent framework in which coordinated planning, editing, and fidelity-aware evaluation serve as the execution layer, while validated editing patterns are progressively distilled into reusable, engine-specific optimization skills. To enable controlled assessment, we introduce a Twin Branch Evaluation Protocol for causal attribution of content edits and DSV-CF, a dual-axis metric that unifies semantic visibility with attribution accuracy. We further release MSME-GEO-Bench, a multi-scenario, multi-engine benchmark grounded in real-world queries. Experiments on three mainstream engines show that MAGEO substantially outperforms heuristic baselines in both visibility and citation fidelity, with ablations confirming that engine-specific preference modeling and strategy reuse are central to these gains, suggesting a scalable learning-driven paradigm for trustworthy GEO. Code is available at https://github.com/Wu-beining/MAGEO.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

当前的生成引擎（如 Gemini、ChatGPT、Qwen）使用检索增强生成（RAG）提供带引用的答案，取代了传统的排序链接列表。这给内容创作者带来了新的优化挑战：传统 SEO 信号（如关键词密度、链接结构）在语义驱动的生成引擎中失效，而现有生成引擎优化（GEO）方法仅针对单个实例进行优化，无法积累或跨任务、跨引擎转移有效的策略。论文将 GEO 重新定义为策略学习问题，旨在通过可复用的技能积累实现持续优化。

## 2. 方法论：核心思想、关键技术细节

**核心思想**：提出 MAGEO，一个双层多智能体框架——执行层通过多智能体协作（偏好、规划、编辑、评估）进行迭代优化；学习层将验证过的编辑模式蒸馏为可复用的、引擎专用的优化技能，存储在技能库（Skill Bank）中，供未来任务直接复用。

**关键技术细节**：
- **执行层**：
  - 偏好智能体（Apref）：分析大规模查询-响应数据，构建引擎偏好画像。
  - 规划智能体（Aplan）：综合引擎偏好、当前响应状态和技能库中的策略技能，制定高层次的修订策略。
  - 编辑智能体（Aedit）：执行具体修改（结构调整、证据增强、风格适应），并行生成候选变体。
  - 评估智能体（Aeval）：使用 LLM-as-a-Judge 协议预测 DSV-CF 增益，并应用保真门（Fidelity Gate）拒绝语义忠实度低于阈值的变体。
- **学习层**（技能库）：
  - 步骤级记忆：记录单次优化会话中每个编辑尝试的结果（正/负片段）。
  - 创建者级记忆：每次成功会话后，将重复出现的有效模式抽象为结构化策略技能，按引擎和场景索引。
  - 技能检索：新任务到来时，规划智能体根据当前引擎和场景从技能库中检索匹配策略，缩小搜索空间。
- **优化循环**：每轮 t，规划智能体检索技能 + 当前约束指导编辑智能体生成候选池，评估智能体过滤并选择最佳变体，循环至性能持平或预算耗尽。

**关键公式**：优化目标为最大化双轴语义可见性与内容保真度指标（DSV-CF）：
```
S_DSV-CF = λ · S_SSV + (1-λ) · S_ISI - γ · (1-AA)
```
其中 SSV 为表面语义可见性（包含词级可见性WLV、衰减位置权威DPA、引用显著性CP、主观印象SI），ISI 为内在语义影响（包含归因准确度AA、响应级忠实度FA、关键点覆盖KC、答案主导性AD）。默认 λ=0.5, γ=0.5。

**双分支评估协议**：通过冻结检索列表，比较基线分支（原始文档）与优化分支（替换目标文档为优化版本）的生成结果，实现内容编辑的因果归因。

## 3. 实验设计

**数据集**：
- **MSME-GEO-Bench**（自行构建）：基于 ELIS 理论和 HLD-QT 分类，覆盖 5 大生活领域、15 个子类，包含真实查询、意图和复杂度标签，共 100 个测试样本（用于人类验证），具体规模未全文给出。
- **GEO-Bench**（Aggarwal et al., 2024）：标准 GEO 基准，用于与已有基线直接比较。

**目标引擎**：
- 专有模型：GPT-5.2（OpenAI）、Gemini-3 Pro（Google）
- 开源模型：Qwen-3 Max

**对比方法**：官方 GEO 仓库发布的 9 种启发式 GEO 策略（权威性、引用可信来源、统计添加、引用添加、易读、流畅、独特词汇、技术术语、关键词优化），以及它们的组合（双策略、三策略、四策略组合）。

**主要指标**：DSV-CF 及其子指标（WLV、DPA、CP、SI、AA、FA、KC、AD）。

## 4. 资源与算力

论文中**未明确说明**使用的 GPU 型号、数量或训练时长。仅提到了 token 消耗和延迟（例如 MAGEO Full 平均 12.4k tokens，38.7s 延迟），但未给出训练或推理的具体硬件配置。

## 5. 实验数量与充分性

论文报告了多个维度的实验：
- **主实验结果**：在 MSME-GEO-Bench 和 GEO-Bench 上对比了 9 个单启发式基线 + 3 个专用策略（MAGEO 及其两个消融变体），覆盖 GPT-5.2、Gemini-3 Pro 和 Qwen-3 Max 三个引擎。
- **消融实验**：分别移除引擎偏好模块和技能库，观察性能下降（约19%和13%）。
- **人类验证**：100 个样本的 LLM 判断与人工标注的 Spearman 相关性（DSV-CF ρ=0.81）。
- **组合基线实验**：构建双、三、四策略组合（共10种）对比 MAGEO。
- **进化优化分析**：展示 10 个版本的优化轨迹。
- **成本-效果分析**：比较 None、GEO Quote、MAGEO Lite、MAGEO Full 的 token 消耗和 WLV。
这些实验覆盖了主要的比较维度，对比基线是官方实现且可复现，消融实验合理。但缺少跨场景泛化分析（如技能库在不同引擎间的迁移效果），以及更大规模数据集上的统计检验。

## 6. 主要结论与发现

1. **MAGEO 在三个引擎上均显著优于所有启发式基线**，WLV 提升至基线的 3-4 倍，且不牺牲归因保真度。
2. **引擎偏好建模和技能库是关键组件**：移除后者导致约 13% 性能下降，移除前者导致约 19% 下降。
3. **MAGEO 不是简单启发式组合**：最佳组合（四策略）WLV 仅 1.90，远低于 MAGEO 的 4.52。
4. **保真意识优化**：MAGEO 保持高保真度（FA > 7.05），避免了关键词填充等策略带来的幻觉惩罚。
5. **成本-效果平衡**：MAGEO Lite 是性价比最优选择（2.9× token 获得 3× WLV 增益）。
6. **进化优化存在收益递减**：约第 5 轮达到峰值，之后可能过度优化降低保真度。

## 7. 优点

- **问题重构**：将 GEO 从逐实例试错提升为策略学习和技能积累，具有前瞻性。
- **双层架构**：执行层与学习层分离，实现了可迁移技能，这是现有 GEO 方法未有的。
- **因果评估协议**：双分支协议能严格隔离内容编辑的因果效应，避免检索噪声干扰。
- **多维度、多引擎验证**：在三个主流引擎（含开源）上验证，增强了泛化性。
- **成本分析**：明确提供了 token 消耗和延迟数据，强调实际部署的权衡。
- **人类验证**：对 LLM 作为评估者的可靠性进行了验证（ρ=0.81）。

## 8. 不足与局限

- **算力与效率**：未报告 GPU 配置或训练时长；多智能体框架的 token 开销高（MAGEO Full 4x token），限制高吞吐场景。
- **基准规模**：MSME-GEO-Bench 虽覆盖多领域，但现仅有 100 个样本用于人类验证，整体规模未明述，可能限制精细子组分析。
- **模型偏差**：Gemini-3 Pro 参与生成查询和标注，尽管有检索验证和人工检查，仍可能残留模型特定偏差。
- **技能泛化**：未提供技能库在新场景或引擎漂移下的学习曲线分析，也未分析跨领域迁移性能。
- **时间漂移**：引擎偏好会随时间演变，当前框架未涉及自适应技能维护。
- **模态局限**：仅限文本，未考虑多模态 GEO。
- **评估近似**：DSV-CF 部分依赖 LLM 判断，虽经人类验证但仍是近似，高风险管理场景需人工审计。

（完）
