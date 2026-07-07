---
title: "CLAG: Adaptive Memory Organization via Agent-Driven Clustering for Small Language Model Agents"
title_zh: CLAG：通过代理驱动聚类实现自适应记忆组织的小语言模型代理
authors: "Taeyun Roh, WonJune Jang, Junha Jung, Jaewoo Kang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.824.pdf"
tags: ["query:cli-agent"]
score: 4.0
evidence: 面向LLM代理的自适应记忆组织，可支持CLI代理
tldr: 针对小语言模型代理全局记忆池导致知识稀释的问题，提出CLAG框架：通过SLM代理驱动的路由器将每条新记忆分配给语义连贯的簇，并持续演化簇内内容。检索时只访问少量相关簇，显著降低了跨主题干扰。实验表明CLAG在多个推理任务上提高了小模型代理的性能，且计算开销低。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.824/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1496, \"height\": 815, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.824/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1597, \"height\": 869, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 764, \"height\": 1333, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 778, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1465, \"height\": 985, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1581, \"height\": 919, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1369, \"height\": 552, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 668, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1206, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 609, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 721, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1656, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 786, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 814, \"height\": 574, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 812, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 807, \"height\": 887, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 735, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1676, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1581, \"height\": 857, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.824/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1630, \"height\": 1125, \"label\": \"Table\"}]"
motivation: 小语言模型代理对无关上下文敏感，全局记忆池易稀释知识。
method: CLAG使用代理驱动的路由器将记忆分配到语义簇，并持续演化簇结构。
result: 在问答和推理任务上，CLAG提升了小模型代理的准确率和效率。
conclusion: 为小语言模型代理提供了有效的结构化记忆管理方案。
---

## Abstract
Large language model agents heavily rely on external memory to support knowledge reuse and complex reasoning tasks. Yet most memory systems store experiences in a single global retrieval pool which can gradually dilute or corrupt stored knowledge. This problem is especially pronounced for small language models (SLMs), which are highly vulnerable to irrelevant context. We introduce CLAG, a CLustering-based AGentic memory framework where an agent actively organizes memory. CLAG employs an SLM-agent driven router to assign each new memory to a semantically coherent cluster. By performing continual evolution within the cluster, it effectively reduces cross-topic interference. During the retrieval phase, CLAG targets a small set of relevant clusters for retrieval, thereby excluding distractors and reducing the search space. Experiments on multiple QA datasets with three SLM backbones show that CLAG consistently improves answer quality and robustness over prior memory systems for agents, remaining lightweight and efficient.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

大型语言模型智能体在长期交互中依赖外部记忆进行知识复用和推理。然而，现有记忆系统通常将所有经验存储在一个全局检索池中，随着记忆增长，容易出现知识稀释和跨主题干扰，尤其对于**小语言模型（SLM）**，其对无关上下文高度敏感，这一问题更为严重。CLAG 的提出旨在通过**代理驱动的聚类机制**，将记忆组织成语义连贯的簇，从而减少噪声干扰、提升小模型在长期任务中的鲁棒性。

### 2. 论文提出的方法论

- **核心思想**：将聚类作为代理控制的在线操作，而非静态预处理。SLM 代理充当路由器，将每条新记忆分配到最合适的语义簇；在每个簇内部进行**局部化演化**（链接生成、记忆重写）；检索时采用**两阶段策略**：先通过簇轮廓过滤出相关簇，再在簇内进行细粒度检索。
- **关键技术细节**：
  - **记忆表示**：每条记忆包含原始内容、所属簇 ID、时间戳、关键词、标签、上下文描述、链接。
  - **路由算法**：冷启动阶段先缓存 n 条记忆，用 K-Means 初始化 k 个簇；后续记忆先通过余弦相似度选出 top-k 候选簇，再交由 SLM 代理选择最佳簇；若相似度低于阈值则新建簇；簇大小超过阈值时自动二分。
  - **局部演化**：新记忆加入簇后，只在该簇内找 top-k 个邻居，通过 SLM 生成链接、更新邻居的内容和簇轮廓。
  - **两阶段检索**：第一阶段基于查询的嵌入与簇质心距离选出候选簇，再由 SLM 代理筛选出最相关的簇；第二阶段仅在选中的簇内进行常规检索。

### 3. 实验设计

- **数据集**：
  - **LoCoMo**：超长对话基准（最多 35 轮、平均 300 轮、9K token）。
  - **HotpotQA**：多跳问答，每个问题配 20 个文档（含干扰项）。
  - **BioASQ**（Task 10b）：生物医学领域问答，同样配干扰项。
- **对比方法**：标准 RAG、A-mem、MemoryOS、GAM。
- **骨干模型**：Llama-3.2-1B-Instruct、Qwen3-0.6B、DeepSeek-R1-Distill-Qwen-1.5B。
- **评价指标**：F1、BLEU-1、METEOR、BERTScore；检索评估用证据精度/召回/F1、Recall@K、nDCG@K。

### 4. 资源与算力

文中仅提及**所有实验在单块 NVIDIA A100 GPU 上执行**（用于延迟测量），未报告训练时长或 GPU 数量。由于 CLAG 基于预训练 SLM 进行推理，未涉及模型微调，故算力需求主要体现在检索与代理调用上。

### 5. 实验数量与充分性

- **主实验**：3 个数据集 × 3 个骨干模型 × 5 种方法，共 45 个条件（表 1）。
- **消融实验**：局部演化 vs 全局演化、两阶段检索 vs 全局检索（表 7）；聚类策略对比（表 5）。
- **类别分析**：LoCoMo 的 5 个子类（表 3）。
- **检索质量分析**：证据级指标、Recall@K、nDCG（表 4）。
- **延迟对比**（表 2）。
- **超参数敏感性**：初始化簇数（表 9）、新簇阈值（表 10）。
- **失败案例分类**（表 13-14）。
- **更大模型实验**：Qwen3-8B（表 6）。
- **评估指标全面**：同时报告 F1、BLEU-1、METEOR、BERTScore、检索精度/召回/F1、nDCG。

整体实验设计充分，基准选择合理，消融和敏感性分析增强了可靠性。但部分基线（GAM、MemoryOS）因输出长度不固定，在检索指标上被排除，稍显不足。

### 6. 论文的主要结论与发现

- CLAG 在**所有三个数据集和三个 SLM 骨干**上大部分指标优于基线，尤其在需要多跳推理和对抗性问题的场景下提升显著。
- **局部演化**通过提升簇内信息密度，使检索到的内容更精炼，从而改善最终答案质量（BioASQ 上 F1 提升 2.46）。
- **两阶段检索**有效降低搜索空间（平均减少约 8%），并过滤掉域内干扰项，对 SLM 特别有益。
- 相比 GAM，CLAG 在精度相当的情况下**延迟降低两个数量级**，实现了更好的准确-效率权衡。
- 随着模型规模增大（Qwen3-8B），CLAG 的优势缩小但仍具竞争力，说明其对小模型的增益最大。

### 7. 优点

- **方法新颖**：将聚类与代理驱动相结合，实现在线、自适应的记忆组织，而非静态索引。
- **设计轻量**：局部化操作避免全局遍历，延迟远低于同类代理记忆系统（如 GAM）。
- **实验扎实**：覆盖多种领域、多种模型、多种指标，并有充分的消融和敏感性分析。
- **鲁棒性强**：在对抗性、多跳等困难类型上表现突出，尤其适合资源受限场景。

### 8. 不足与局限

- **对提示设计敏感**：代理路由和演化依赖精心设计的 prompt，不同 LLM 版本可能表现波动。
- **分布漂移未充分测试**：未系统评估话题或写作风格剧烈变化时路由质量。
- **部分场景欠佳**：在 LoCoMo 的“开放域”类别中，CLAG 有时不如 GAM，表明覆盖性与局部化存在权衡。
- **隐私与数据治理**：论文仅提及潜在问题，未提供具体安全机制（如访问控制、删除策略）。
- **检索质量分析中排除两个基线**：GAM 和 MemoryOS 因输出可变长度未被纳入标准 K 度量比较，虽另有预算感知实验（附录 I），但对比稍显不完整。
- **未探索更大参数的 SLM 上限**：仅在 <2B 模型上重点验证，对 3-7B 模型仅做了 Qwen3-8B 单次验证。

（完）
