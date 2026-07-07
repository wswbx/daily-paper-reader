---
title: Dynamic Tool Dependency Retrieval for Lightweight Function Calling
title_zh: 面向轻量级函数调用的动态工具依赖检索
authors: "Bhrij Patel, Davide Belli, Amir Jalalirad, Maximilian Arnold, Aleksandr Ermolov, Bence Major"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1680.pdf"
tags: ["query:cli-agent"]
score: 6.0
evidence: 动态工具依赖检索，适用于CLI智能体的工具选择
tldr: 现有函数调用智能体工具检索方法依赖静态输入，忽略多步工具依赖。本工作提出动态工具依赖检索DTDR，基于初始查询和动态工具调用计划进行自适应检索。DTDR从函数调用示例中建模工具依赖，在多个基准上减少了无关工具引入，提高了智能体效率和准确性，对CLI智能体等需要筛选大量命令的场景有价值。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1680/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1650, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1680/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1334, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1680/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1639, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1680/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1465, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1680/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1491, \"height\": 369, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1654, \"height\": 463, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1492, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 804, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1491, \"height\": 764, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 811, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1375, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1651, \"height\": 413, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1325, \"height\": 1973, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1680/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1485, \"height\": 2118, \"label\": \"Table\"}]"
motivation: 现有检索方法依赖静态输入，无法捕捉多步工具依赖和演进的任务上下文。
method: 提出DTDR，基于查询和动态工具调用计划建模依赖关系，实现自适应检索。
result: 在多个LLM智能体工具使用任务上，DTDR减少了无关工具引入，提升了效率和准确率。
conclusion: DTDR为工具依赖检索提供了高效轻量的解决方案，可优化CLI智能体等代理系统的工具选择。
---

## Abstract
Function calling agents powered by Large Language Models (LLMs) select external tools to automate complex tasks. On-device agents typically use a retrieval module to select relevant tools, improving performance and reducing context length. However, existing retrieval methods rely on static and limited inputs, failing to capture multi-step tool dependencies and evolving task context. This limitation often introduces irrelevant tools that mislead the agent, degrading efficiency and accuracy. We propose Dynamic Tool Dependency Retrieval (DTDR), a lightweight retrieval method that conditions on both the initial query and the evolving tool calling plan. DTDR models tool dependencies from function calling demonstrations, enabling adaptive retrieval as plans unfold. We benchmark DTDR against state-of-the-art retrieval methods across multiple datasets and LLM backbones, evaluating retrieval precision, downstream task accuracy, and computational efficiency. Additionally, we explore strategies to integrate retrieved tools into prompts. Our results show that DTDR improves function calling success rates between 23% and 104% compared to state-of-the-art static retrievers.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大型语言模型（LLM）增强的工具使用（函数调用）智能体依赖于检索模块从大量工具中筛选相关工具，以减少上下文长度并提升性能。现有检索方法主要分为两类：基于查询-工具语义相似性的静态检索（如BM25、Query-Tool Similarity）和基于工具依赖图的静态检索（如ToolNet）。
- **问题**：这些方法都是**静态的**，要么仅依赖初始查询，要么仅依赖最近一次工具调用，无法捕捉**多步工具依赖关系**和**演进的任务上下文**。这导致检索出无关工具，误导智能体，降低效率和准确性。
- **本文贡献**：提出**动态工具依赖检索（Dynamic Tool Dependency Retrieval, DTDR）**，一种轻量级检索方法，同时基于**用户查询**和**当前的工具调用历史**（即演化中的计划）来检索相关工具，并建模工具间的依赖关系。

## 2. 论文提出的方法论

### 核心思想
- DTDR 将检索模块 $\omega$ 建模为：$\omega(q, f_{0:t-1})$，其中 $q$ 是用户查询，$f_{0:t-1}$ 是到上一时刻为止的工具调用序列（计划历史）。
- 利用已有的**演示数据**（demonstration trajectories）来学习工具依赖，使得检索能够随计划展开而动态调整。

### 两种轻量级变体
1. **DTDR-C（聚类方法）**
   - 使用预训练的句子嵌入模型将演示查询转为向量，然后对演示数据做 **K-Means 聚类**。
   - 对于每个聚类 $k$，利用该聚类内的演示构建一个**加权工具依赖图** $G_k$（N阶马尔可夫链），记录给定历史工具序列后下一工具的概率分布。
   - 测试时：将测试查询 $q$ 分配给最近的聚类，然后用当前工具历史 $f_{0:t-1}$ 查询该聚类的依赖图 $G_k$，得到下一工具的概率分布 $F_t = G_{C(\beta)}(f_{0:t-1})$。
   - 参数量：$e \times K$（$e$=嵌入维度，$K$=聚类数）。

2. **DTDR-L（线性分类器方法）**
   - 训练一个**单层线性分类器** $\phi$，输入为查询与历史工具的拼接嵌入 $E(q + f_{0:t-1})$，输出为每个工具的概率分布（通过 softmax）。
   - 训练目标：最小化每个时间步的二元交叉熵损失（公式2）。
   - 测试时：设定阈值 $\alpha$，保留概率大于 $\alpha$ 的工具构成 $F_t$。
   - 参数量：$e \times |\mathcal{F}|$（$e$=嵌入维度，$|\mathcal{F}|$=工具总数）。

### 算法流程（文字描述）
- **训练阶段**（仅DTDR-L需要监督训练）：使用演示数据对 $\phi$ 进行多步训练（每个时间步串联查询与历史，预测下一工具）。
- **推理阶段**（以函数选择的每一步为例）：
  1. 输入 `(query, func_history)`；
  2. 通过 DTDR 模块（C或L）得到工具概率分布 $\omega$，然后选取子集 $F_t$；
  3. 将 $F_t$ 编码到 prompt 中（如 Hard Masking 只保留这些工具的描述）；
  4. LLM 从 $F_t$ 中选择下一工具 $f_t$；
  5. 将 $f_t$ 加入 history，重复直到预测“end-of-plan”。

## 3. 实验设计

### 数据集
- **TinyAgent**：39874 个计划，17 个工具，每计划平均 4.5 次调用，依赖数 1.9。
- **TaskBench DailyLife** (TB-DL)：3860 个计划，41 个工具，依赖数仅 0.1（工具间几乎无依赖）。
- **TaskBench HuggingFace** (TB-HF)：4959 个计划，24 个工具，依赖数 1.1。
- **TaskBench Multimedia** (TB-MM)：4310 个计划，41 个工具，依赖数 1.5。

### 基准方法
- **无检索**：No ICL（所有工具全量给出）。
- **文本相似度**：BM-25。
- **查询-工具相似度**：QTS (Vanilla)、QTS (Gao et al., 2025 Tool Graph Retriever)、QTS (Paramanayakam et al., 2025 Less-is-More)。
- **静态依赖检索**：DR (Liu et al., 2024a ToolNet)，仅基于最近一次工具调用。
- **静态学习检索**：LR (Erdogan et al., 2024 TinyAgent)，仅基于查询。
- **动态检索**：DTDR-C、DTDR-L（本文提出）。

### LLM 骨干
- **Qwen 3 系列**：0.6B、1.7B、4B、8B、14B（代表边缘设备）。
- **GPT-4o**（云端大模型）。
- **Gorilla-V2**（专为函数调用微调的模型）。

### 评估指标
- **检索性能**：MRR (Mean Reciprocal Rank)、F1-score。
- **下游任务性能**：
  - 函数选择准确率（FSA）：每一步选择的函数是否属于正确答案集。
  - 端到端成功率（SR）：整个计划的函数名称和参数均正确。
- **效率**：提示长度（prompt length）作为预填充速度的代理；参数量（模型大小）。

### 实验设置
- 每个数据集随机划分 30% 测试，其余为演示数据。
- 句子嵌入模型统一使用 `paraphrase-MiniLM-L6-v2`（维度 384）。
- 不同 ICL 策略：Hard Mask、Soft Mask、Weighted Hard/Soft Mask、Raw Demonstrations（提供额外5个示例轨迹）。

## 4. 资源与算力

- 论文明确提到：**所有实验在 NVIDIA A100 GPU 上进行**，未说明具体数量或总训练时长。
- Qwen 3 模型和 Gorilla-V2 使用 FP16 精度，GPT-4o 通过云端 API 调用。
- DTDR 方法本身参数量很小（DTDR-C: $e \times K$，DTDR-L: $e \times |\mathcal{F}|$），训练开销低于 LLM 的推理开销。

## 5. 实验数量与充分性

- **数量丰富**：涵盖了 4 个数据集、7 个 LLM 骨干（从 0.6B 到 GPT-4o）、多项对比方法（10 种以上）、2 种 DTDR 变体。
- **消融实验**：系统分析了历史长度（图6a）、聚类数（图6b）、演示数据量（图6c）的影响。
- **ICL 策略对比**：比较了 No ICL、Raw Demonstrations、Hard/Soft/Weighted Masking 等 5 种策略。
- **公平性**：
  - 所有检索方法使用相同的句子嵌入模型。
  - 函数选择实验使用相同的 LLM 骨干，仅 prompt 不同。
  - 阈值通过验证集优化（仅 DTDR-C 无阈值参数）。
- **客观性**：在多个模型尺寸和数据集上重复验证，结果趋势一致。

## 6. 论文的主要结论与发现

1. **动态检索显著优于静态方法**：DTDR 在检索 MRR、F1 以及下游 FSA/SR 上全面超越所有基线。提升幅度为 23%–104%（与 SOTA 静态检索相比）。
2. **DTDR-L 整体最佳**：在 TinyAgent 和 TaskBench DailyLife 上，DTDR-L 的 FSA 高达 65.1%–94.2%，优于 DTDR-C 和其他基线。
3. **历史长度影响**：历史长度 l=3 时增益最大；无历史时 DTDR-L 容易过拟合到高频工具。
4. **聚类数影响**：DTDR-C 的最优聚类数约为演示数的 1/10；单个聚类（无查询条件）性能显著下降。
5. **ICL 策略选择**：Hard Masking 对小型模型效果最佳；Weighted Hard Masking 在检索置信度高时更优，反之则否。Raw Demonstrations 虽然大模型效果好，但大幅增加提示长度。
6. **提示长度压缩**：DTDR 可将总提示长度减少达 73%，变量部分减少 48%，且不影响性能。
7. **模型缩放**：DTDR-L + Qwen3-4B 可达到 No ICL + Qwen3-14B 或 GPT-4o 的准确率，弥合边缘与云端模型的差距。

## 7. 优点

- **轻量高效**：DTDR 变体参数量极小，仅依赖小型句子嵌入和线性分类器/聚类，非常适合设备端部署。
- **动态适应性**：同时利用查询和逐步更新的工具历史，克服了静态检索无法捕捉多步依赖的缺陷。
- **可解释性与可控性**：DTDR-C 提供可视化工具依赖图，DTDR-L 提供明确的概率输出，便于调试。
- **通用性**：方法不依赖于特定 LLM 或数据集，在 7 种不同尺寸的模型上均有效。
- **完整消融**：对历史长度、聚类数、数据量等超参数进行了充分的敏感性分析。
- **实际价值**：在设备端场景下，通过更精准的检索显著提升函数调用成功率，同时降低推理时延。

## 8. 不足与局限

- **OOD 泛化问题**：
  - DTDR-C 在分布外任务上性能下降明显，因为 K-Means 聚类和 N 阶马尔可夫链需要足够的训练数据覆盖。
  - 对于强 OOD 的工具名或依赖结构，所有检索方法均失效，缺乏不确定性回退机制。
- **对特殊词汇敏感**：DTDR-C 在处理非常用或领域特定的工具名/描述时（如 HuggingFace 风格函数名）效果不佳，因为预训练嵌入可能无法捕获语义。DTDR-L 可通过自适应缓解此问题。
- **依赖真值演示**：方法假设拥有完全正确的专家演示轨迹，这在现实世界中可能难以获得（如演示包含错误或不完整）。
- **仅限文本工具**：未扩展到多模态或机器人等具有非文本输入/输出形式的工具使用场景。
- **参数填充模块独立**：实验中采用单独的提示进行参数填充，未考虑检索与参数联合建模的可能。
- **缺乏不确定性估计**：没有对低置信度检索进行定量判断并采取回退策略（如全量工具）。

---

（完）
