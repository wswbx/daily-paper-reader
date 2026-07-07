---
title: "DeepSynth-Eval: Objectively Evaluating Information Consolidation in Deep Survey Writing"
title_zh: DeepSynth-Eval：深度调查写作中信息整合的客观评估
authors: "Hongzhi Zhang, Yuanze Hu, Tinghai Zhang, Jia Fu, Tao Wang, Junwei Jing, Zhaoxin Fan, Victoria W., Ruiming Tang, Han Li, Guorui Zhou, Kun Gai"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1688.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 深度调查写作中信息整合的评估基准
tldr: 针对深度研究代理在信息综合阶段缺乏客观评估的问题，DeepSynth-Eval利用高质量综述论文作为黄金标准，通过反向工程研究需求并构建Oracle上下文，隔离检索噪声，细粒度评估代理的整合能力。实验证明该基准能有效区分不同代理的综合水平，填补了深度研究评估在综合环节的空白。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1688/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1299, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1688/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 591, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1688/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 597, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1688/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 656, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1688/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 652, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1688/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 662, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1688/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1518, \"height\": 1009, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1688/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 584, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1688/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 795, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1688/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1573, \"height\": 1466, \"label\": \"Table\"}]"
motivation: 现有深度研究评估侧重检索能力，忽视了检索后信息综合阶段的客观评估。
method: 提出DeepSynth-Eval基准，利用高质量综述论文构建黄金标准，通过反向工程和Oracle上下文隔离检索噪声。
result: 该基准能够客观评估代理的信息整合能力，并有效区分不同代理的综合水平。
conclusion: DeepSynth-Eval填补了深度研究代理在综合环节的评估空白。
---

## Abstract
The evolution of Large Language Models (LLMs) towards autonomous agents has catalyzed progress in Deep Research. While retrieval capabilities are well-benchmarked, the post-retrieval synthesis stage—where agents must digest massive amounts of context and consolidate fragmented evidence into coherent, long-form reports—remains under-evaluated due to the subjectivity of open-ended writing.To bridge this gap, we introduce DeepSynth-Eval, a benchmark designed to objectively evaluate information consolidation capabilities. We leverage high-quality survey papers as gold standards, reverse-engineer research requests, and construct Oracle Contexts from their bibliographies to isolate synthesis from retrieval noise. We propose a fine-grained evaluation protocol using General Checklists (for factual coverage) and Constraint Checklists (for structural organization), transforming subjective judgment into verifiable metrics. Experiments across 96 tasks reveal that synthesizing information from hundreds of references remains a significant challenge. Our results demonstrate that agentic "plan-then-write" workflows significantly outperform single-turn generation, effectively reducing hallucinations and improving adherence to complex structural constraints.

---

## 论文详细总结（自动生成）

# DeepSynth-Eval: 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

随着大型语言模型从基础 token 补全向自主代理进化，“深度研究”（Deep Research）成为新趋势。现有评估体系高度关注信息检索能力（如 GAIA、HLE、BrowseComp 等基准），但**检索后的信息综合阶段**——代理必须消化大量上下文、将碎片化证据整合成连贯的长篇报告——却因开放式写作的主观性而长期缺乏客观评估。具体困境包括：
- 端到端评估将检索噪声与综合失败混杂，无法隔离模型的真实整合能力。
- 现有评价依赖人工或 LLM 作为法官的整体打分，成本高、不稳定，且易受奖励破解（reward hacking）影响。

因此，**论文的核心动机是：构建一个能客观、可复现地衡量深度调查写作中信息整合能力的基准**，填补现有评估体系在综合环节的空白。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 核心思想
利用高质量综述论文作为“黄金标准”，反向工程出研究请求，并从其参考文献构建“Oracle 上下文”（Oracle Context），从而隔离检索噪声。通过将主观评价转换为可验证的细粒度检查项清单，实现客观度量。

### 关键技术细节

1. **检查项清单设计**：
   - **通用检查项（General Checklist）**：从综述中提取的关键事实要点（如代表性方法、关键设计、重要数据集等），用于评估事实覆盖度。
   - **约束检查项（Constraint Checklist）**：提取的结构化组织要求（如特定分类法、表格应包含哪些属性等），用于评估结构遵守情况。

2. **构建流程**：
   - 对每篇参考综述，使用 LLM 反向生成通用问题 \( q_{gen} \)。
   - 采用**分层主题锚点（Hierarchical Topic Anchor）**策略：先让 LLM 从综述中合成多个主题，再在每个主题内生成通用检查项，避免直接生成长列表导致低召回或幻觉。
   - 使用**结构锚点（Structure Anchor）**提取约束问题与对应检查项（如表格的列定义、分类标准）。约束检查项仅在注入对应约束问题时才有效，从而保证结构可比性。

3. **Oracle 上下文构建**：
   - 从综述参考文献中收集论文全文本或摘要，形成封闭的知识边界，确保模型只能基于给定文献生成报告，避免检索噪声和知识泄露。

4. **容错组评分（Fault-Tolerant Group Scoring）**：
   - 检查项按语义分组，每组设定饱和度阈值 \( \theta_k \)，当组内累计正确数达到阈值后不再加分，防止长列表组过度主导分数。
   - 组级聚合：对通用组和约束组分别计算平均分 \( S_{gen} \)、\( S_{con} \)，以及总体分 \( S_{all} \)。
   - 此外汇报精度（Precision）：正确提及数 / (正确+错误提及数)。

5. **奖罚机制**：每个检查项由法官模型判定为正确（+1）、未提及（0）、错误（-1），错误提及会降低精度分。

## 3. 实验设计

### 数据集 / 场景
- **DeepSynth-Eval 基准**：包含 96 个任务，每个任务源于一篇高质量计算机科学综述。
- **每任务统计**：
  - 平均 199.7 个检查项（128.2 通用 + 71.5 约束）。
  - 大量任务参考文献总字数超 100 万词（部分任务达 600 万词）。
- **数据来源**：通过 arXiv 检索、Semantic Scholar API 获取元数据，人类专家两轮验证筛选，最终保留 96 个实例。

### Benchmark 与对比方法
**两种受控合成工作流**，所有模型使用相同 Oracle 上下文：

1. **E2E 单回合工作流**：先将每篇参考文献压缩成摘要拼接成 Oracle 上下文，然后一次性生成完整报告（无中间规划或迭代修改）。
2. **Agentic 多回合工作流**：分解为规划阶段（构建“智力骨架”）、逐节写作循环（选择关键论文、深入阅读、写章节）、最终润色三阶段。

**评估模型**：
- Qwen3-30B-A3B-Thinking-2507
- Qwen3-235B-A22B-Thinking-2507
- DeepSeek-V3.2
- GPT-5.2

此外，还评估了外部系统（Doubao DeepResearch、OpenAI DeepResearch、OpenAI Agentic 管道），但作为补充参考而非主要排名。

## 4. 资源与算力

论文**未明确说明**所使用 GPU 型号、数量、训练时长等算力资源。仅提及使用 Gemini 3 辅助语言润色，但未涉及模型训练或大规模推理的硬件配置。因此，这是一个缺失细节，后续研究可补充。

## 5. 实验数量与充分性

### 实验数量
- 核心实验：在 96 个任务上比较了 4 种模型 × 2 种工作流，共 8 组主实验结果（Table 1）。
- 补充实验：外部系统评估在 39 个任务子集上进行（Table 2）。
- 额外分析：检查项状态分解（Figure 4/6）、分数分布（Figure 5）、案例分析（失败模式与质量分析）。

### 充分性与客观性
- **客观性**：基于原子化检查项的验证比整体主观评分更可复现、更细粒度。法官模型使用 DeepSeek v3.2，并通过黄金综述（参考论文）验证法官精度达 99.6%，证明可靠性高。
- **公平性**：控制工作流下 Oracle 上下文固定，隔离检索噪声；外部系统评估时设置允许列表和严格时间截止，防止知识泄露。
- **充分性**：96 个任务覆盖多个计算机科学领域，但论文自身承认受访范围偏窄（主要限于计算机科学）。进一步消融实验较少（如不同法官模型、不同饱和度阈值设置等），但主要研究问题得到充分回答。

## 6. 主要结论与发现

1. **单回合 E2E 工作流**：
   - 模型间性能差异显著。GPT-5.2 表现最强（总体 28.3%），在约束分数（36.1%）和精度（85.5%）上领先，表明其单次合成中指令遵循和内容基础化能力较好。
   - 较弱模型（如 Qwen3-30B）在单回合中基本崩溃（总体仅 6.3%），说明长上下文整合高度依赖模型容量。

2. **Agentic 多回合工作流显著提升性能**：
   - 所有模型在总体和通用分数上均获得提升（例如 Qwen3-235B 从 24.8% → 35.5%，GPT-5.2 从 28.3% → 33.3%）。
   - 分数分布向右偏移，表明提升不是由少数任务驱动，而是系统性改善。
   - 检查项状态分解显示：Agentic 工作流增加了正确率，降低了错误率，说明阶段性计划→阅读→写作流程改善了事实性。

3. **剩余差距**：即使使用 SOTA 模型和 Agentic 工作流，最高总体分数仅为 37%（GPT-5.2 有效子集），表明从百篇以上文献中综合生成报告仍是重大挑战。

4. **外部系统表现**：受限于检索插补和指令负担，端到端深度研究系统并未显著优于受控工作流。

## 7. 优点

- **创新性评估范式**：首次提出将开放式长文评估转化为可验证的检查项清单，极大提升客观性和可复现性。
- **设计精巧的隔离机制**：Oracle 上下文严格基于参考文献构建，避免了检索噪声与综合能力的混淆，实现纯净的后检索合成能力测试。
- **细粒度与容错评分**：组级饱和度阈值设计防止长组过度主导，对开放式写作更公平；三级奖罚机制（正确/遗漏/错误）提供更丰富的反馈信号。
- **高质量数据集**：96 个任务由专家两轮筛选，平均近 200 个检查项，难度高、区分度强。
- **揭示关键发现**：明确提出“计划-然后-写作”工作流比单回合生成更有效，且模型容量与工作流设计同等重要。

## 8. 不足与局限

- **领域覆盖局限**：当前数据集主要由计算机科学综述构成，虽方法论通用，但多样性不足。扩展到其他科学学科（如生物、物理）可增加泛化性。
- **缺失算力与训练细节**：未提供模型推理/训练的硬件配置，影响可复现性与成本评估。
- **法官模型依赖**：检查项验证使用 DeepSeek v3.2 作为法官，其自身可能存在偏见，尽管通过黄金综述校正，但法官模型的选择未做消融实验。
- **约束问题的合理性问题**：论文承认存在“过度指定”和“上下文模糊”两类问题，已通过人工筛选剔除，但人工筛查本身可能引入主观偏差。
- **工作流实现细节的通用性**：Agentic 工作流的具体设计（如选择性深度阅读、润色阶段）可能受限于作者选择的提示模板，不同实现可能导致不同结果。
- **外部系统评估的公平性**：尽管设置了允许列表和截止日期，但外部系统可能因协议限制仍无法完全利用全部参考文献，导致分数偏低，不能完全反映其真实综合潜能。

（完）
