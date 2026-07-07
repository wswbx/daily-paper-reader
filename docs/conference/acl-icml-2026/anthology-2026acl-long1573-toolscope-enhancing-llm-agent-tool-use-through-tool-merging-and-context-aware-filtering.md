---
title: "ToolScope: Enhancing LLM Agent Tool Use through Tool Merging and Context-Aware Filtering"
title_zh: ToolScope：通过工具合并与上下文感知过滤增强大语言模型智能体工具使用
authors: "Marianne Menglin Liu, Daniel Garcia, Fjona Parllaku, Vikas Upadhyay, Fahad Shah, Dan Roth"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.1573.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: 通过工具合并与检索增强LLM智能体工具使用，与CLI智能体工具管理相关
tldr: 面对真实工具集中冗余和上下文限制问题，ToolScope通过自动合并重复工具并基于查询智能检索相关工具，压缩工具集并提升选择准确率。在三个LLM和三个工具集上评估，ToolScope显著提高工具使用性能，对CLI智能体等需要处理大量命令的场景具有直接价值。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 812, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1657, \"height\": 721, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 800, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 649, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 800, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 730, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 783, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 696, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 687, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 700, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 662, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 666, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1573/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 784, \"height\": 419, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 808, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1673, \"height\": 631, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 574, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1658, \"height\": 1689, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 813, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 795, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1702, \"height\": 1308, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 512, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1667, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 509, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1456, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1573/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1153, \"height\": 266, \"label\": \"Table\"}]"
motivation: 真实工具集存在冗余和名称描述重叠，LLM受上下文限制难以高效考虑大规模工具集。
method: 提出ToolScopeMerger自动合并冗余工具并修正错误，以及ToolScopeRetriever按查询排序筛选最相关工具。
result: 在多个LLM和工具集上，ToolScope减少了工具冗余并提高了选择准确率，优于现有方法。
conclusion: ToolScope能有效压缩工具集并提高LLM智能体选择工具的准确性，适用于CLI智能体等复杂工具使用场景。
---

## Abstract
Large language model (LLM) agents rely on external tools to solve complex tasks, but real-world toolsets often contain redundant tools with overlapping names and descriptions, introducing ambiguity and reducing selection accuracy. LLMs also face strict input context limits, preventing efficient consideration of large toolsets. To address these challenges, we propose ToolScope, which includes: (1) ToolScopeMerger with Auto-Correction to automatically audit and fix tool merges, reducing redundancy, and (2) ToolScopeRetriever to rank and select only the most relevant tools for each query, compressing toolsets to fit within context limits without sacrificing accuracy. Evaluations on three state-of-the-art LLMs and three open-source tool-use benchmarks show gains of 8.38% to 38.6% in tool selection accuracy, demonstrating ToolScope’s effectiveness in enhancing LLM tool use.

---

## 论文详细总结（自动生成）

# ToolScope 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）智能体依赖外部工具（如API、函数）解决复杂任务。然而，真实世界的工具集往往存在大量语义冗余的工具，它们的名称和描述重叠，导致LLM在工具选择时产生歧义，降低准确率。此外，LLM有严格的输入上下文长度限制，无法高效考虑大规模工具集。
- **整体意义**：提出一种名为ToolScope的框架，通过自动合并冗余工具和上下文感知过滤，同时解决工具重叠和上下文限制两大挑战，显著提升LLM智能体的工具选择能力，为实际部署可扩展的工具使用方法提供新路径。

## 2. 方法论

### 2.1 核心思想
ToolScope由两个主要组件构成：
- **ToolScopeMerger**：自动识别、分类并合并语义相似的工具，减少冗余，附带**Auto-Correction**模块审计和修正合并错误。
- **ToolScopeRetriever**：针对每个查询，通过混合检索（稀疏+稠密）和重排序，只保留最相关的top-k工具，压缩输入到LLM的上下文长度。

### 2.2 关键技术细节

#### ToolScopeMerger 流程（三阶段）：
1. **候选生成**：使用嵌入模型（如`thenlper/gte-large`）编码每个工具的描述，余弦相似度>阈值（0.82）的配对作为候选。
2. **关系分类与图构建**：LLM二分类器判断工具对是否语义等价，构建无向图，提取连通分量作为待合并簇。
3. **合并与自动修正**：
   - 每个簇选择一个代表工具（选择函数名字符串最短的）。
   - **Auto-Correction**：用另一个LLM验证器检查簇内所有工具是否真正等价；若无效则提出修正（分裂或移除成员）。
   - 合成新的工具签名和描述（由LLM完成），更新工具集和基准数据集的标签映射。

#### ToolScopeRetriever 流程：
- **单工具选择**：混合检索分数 `s(q,t) = α·s_dense + (1-α)·s_sparse`，取top-M候选，再用交叉编码器重排序，选择得分最高的工具。
- **多工具选择**：将查询分解为子查询，对每个子查询执行单工具选择，得到每个子查询的top-1；其余工具分数经min-max归一化后全局排序，选取top-k工具。
- **关键参数**：混合权重α=1（稠密检索最优），重排候选数M=50。

## 3. 实验设计

### 3.1 数据集与基准
- **BFCL**（400查询，400工具，单工具场景）
- **Seal-Tools**（654查询，4076工具，多工具场景）
- **UltraTool**（4814查询，1885工具，多工具场景）

### 3.2 评估指标
- **Correct Selection Rate (CSR@k)**：预测工具集与真实工具集完全匹配的比例，k为返回的工具数。
- **Recall@k**：真实工具在top-k中出现的比例。

### 3.3 对比方法
- **BM25**：基于词频的检索。
- **Dense Embeddings**：稠密向量检索（余弦相似度）。
- 额外对比：DPR、ToolShed（仅在Seal-Tools检索评估中）。

### 3.4 主实验设置
- 三个LLM作为工具选择代理：GPT-4o、LLaMA-3.3-70B、Cohere-Command-R-08-2024。
- 完整结果表显示ToolScope（包含Auto-Correction）在所有组合上均超越基线。

## 4. 资源与算力

论文在**Hyperparameters and Infrastructure**部分明确说明：
- **GPU**：3 × NVIDIA A100（40 GB）。
- **推理参数**：温度0.0，最大输出4000 tokens，top_p=1，频率惩罚0.0。
- **一次性合并成本**：每工具约1.17美分（使用GPT-4o），延迟3.27秒。对于BFCL（400工具）约22分钟（$4.60），UltraTool（1.9K工具）约2小时（$26），Seal-Tools（4K工具）约3小时（$41）。
- **检索与重排序**：使用开源模型（gte-large、ms-marco-MiniLM-L6-v2），无API推理成本，每查询延迟<1秒。
- **工具选择代理**：GPT-4o每查询1.8秒、0.01美元；LLaMA 3.3 70B和Cohere-R-08-2024每查询1.5秒、无推理成本。

## 5. 实验数量与充分性

- **主实验**：在3个基准×3个LLM×多个k值（BFCL: k=1,5,10,15; Seal-Tools: k=5,10,15,20,25,30; UltraTool: k=20,30）下进行，共超过60组CSR比较。
- **消融实验**（Table 3）：对Reranker、Merger、Auto-Correction三个组件进行开/关组合，共4种配置×3数据集=12组实验。
- **检索性能评估**（Table 5）：Recall@k在Seal-Tools和BFCL上与BM25、Dense、DPR、ToolShed对比。
- **敏感性分析**（Figure 4）：余弦相似度阈值从0.77到0.90扫描。
- **混合权重α调优**（Figure 7）：α从0到1变化。
- **端到端评估**：20条BFCL查询，比较BM25、Dense、ToolScope+Auto-Correction的最终答案准确率。
- **文档质量鲁棒性**：按低/中/高文档质量分组分析CSR。
- **人工评估**：48个BFCL工具簇的正确合并判断（95.4%正确），Auto-Correction的F1=94.4%。
- **功能覆盖率**：TCCR和UCC计算（Table 9）。
- **Merger模型消融**：使用LLaMA 3.3 70B和LLaMA 3.1 8B作为合并模型，结果接近GPT-4o。

**充分性评估**：实验覆盖全面，包含多个数据集、多种LLM、多个k值、核心组件消融、敏感性分析、人工验证、端到端测试，统计结果报告充分，对比基线合理。但端到端实验规模较小（20条查询），且未在全部数据集上做完整端到端评估。整体客观公平。

## 6. 主要结论与发现

- ToolScope显著提升工具选择准确率：在Seal-Tools上CSR提升34.6%，UltraTool提升38.6%，BFCL提升8.8%。
- ToolScopeMerger减少工具冗余（BFCL减少14%，Seal-Tools减少2.1%，UltraTool减少25.3%），同时保留大部分功能（TCCR 82-95%，UCC 80-96%）。
- Auto-Correction进一步改善CSR，尤其在多工具、高冗余数据集上（Seal-Tools +2.9%，UltraTool +7.9%）。
- 检索器大幅压缩上下文长度（98.5%–99.9%），提升效率。
- 工具质量差异对ToolScope影响较小，即使在低质量文档下仍有85%以上CSR。
- 当前开源基准工具集存在显著重叠问题，ToolScope可作为修复工具。

## 7. 优点

- **创新性**：首次将自动化工具合并与混合检索结合，系统性解决工具重叠和上下文限制。
- **可扩展性**：自动化流水线，无需人工干预（加上Auto-Correction后更可靠），适用于大规模工具集。
- **鲁棒性**：对文档质量不敏感；合并阈值在0.77-0.90内稳定；支持不同LLM作为合并模型。
- **实验充分**：多维度对比、消融、敏感性分析、人工评估、端到端验证，结果可信。
- **实用性强**：工具合并是一次性预处理，检索轻量且显著压缩上下文，适合部署。

## 8. 不足与局限

- **依赖LLM生成**：ToolScopeMerger的合并和修正依赖外部LLM（GPT-4o或开源模型），存在推理成本、延迟、幻觉和偏差风险。
- **检索范围有限**：当前仅使用工具名称、签名和描述，未利用更丰富的元数据（如使用案例、输入/输出模式），可能限制大规模工具集的检索精度。
- **多工具场景分解**：查询分解为子查询的步骤未详细说明自动方法，可能依赖人工或LLM，影响可复现性。
- **端到端评估规模小**：仅20条BFCL查询，未在Seal-Tools和UltraTool上进行完整端到端测试，难以完全证明提升转化为任务成功。
- **伦理风险**：作者明确指出不适用于医疗、法律、金融等高风险领域，因为工具选择错误可能造成严重后果。
- **未探讨推理型LLM**：仅测试了标准LLM，未考虑具有强化推理能力的模型（如使用搜索或内部推理），可能影响Auto-Correction和工具选择质量。

（完）
