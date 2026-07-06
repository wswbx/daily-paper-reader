---
title: Optimizing Reasoning for Text-to-SQL with Execution Feedback
title_zh: 基于执行反馈的文本到SQL推理优化
authors: "Bohan Zhai, Canwen Xu, Yuxiong He, Zhewei Yao"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.982.pdf"
tags: ["query:opd"]
score: 8.0
evidence: 基于在策略DPO的文本到SQL推理优化
tldr: 本文提出ExCoT-DPO框架，针对文本到SQL任务，将链式思考推理与在策略直接偏好优化（DPO）结合，仅以执行准确率作为反馈，无需奖励模型或人工标注偏好。实验表明该方法显著提升了开源LLM的SQL生成能力，且无需额外标注数据。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.982/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1657, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.982/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 788, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.982/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 774, \"height\": 374, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.982/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1419, \"height\": 1168, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.982/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 782, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.982/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 654, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.982/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 624, \"height\": 413, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.982/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1685, \"height\": 417, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.982/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1677, \"height\": 1096, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.982/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 742, \"height\": 248, \"label\": \"Table\"}]"
motivation: 零样本链式思考在文本到SQL中增益微小，且无链式思考的DPO改进有限。
method: 提出ExCoT-DPO，迭代优化LLM，结合链式思考推理与在策略DPO，利用执行准确率作为唯一反馈。
result: 在多个文本到SQL基准上取得显著性能提升，无需奖励模型或人工偏好。
conclusion: 在策略DPO与链式思考结合可有效提升LLM在结构化查询生成中的推理能力。
---

## Abstract
Text-to-SQL demands precise reasoning to convert natural language questions into structured queries. While large language models (LLMs) excel in many reasoning tasks, their ability to leverage Chain-of-Thought (CoT) reasoning for text-to-SQL remains underexplored. We identify critical limitations: zero-shot CoT offers minimal gains, and Direct Preference Optimization (DPO) applied without CoT yields marginal improvements. We propose ExCoT-DPO, a novel framework that iteratively optimizes open-source LLMs by combining CoT reasoning with off-policy and on-policy DPO, relying solely on execution accuracy as feedback. This approach eliminates the need for reward models or human-annotated preferences. Our experimental results demonstrate significant performance gains: ExCoT-DPO improves execution accuracy on BIRD from 57.37% to 68.51% and on Spider from 78.81% to 86.59% for LLaMA-3 70B, with Qwen-2.5-Coder demonstrating similar improvements. Our best model achieves state-of-the-art performance in the single-model setting on both BIRD and Spider datasets.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **任务**：Text-to-SQL（将自然语言问题转换为结构化 SQL 查询），需要精确推理与模式链接、处理嵌套查询、消除歧义等。
- **现有不足**：
  - 大语言模型（LLMs）在推理任务中表现优异，但在 Text-to-SQL 中，零样本 Chain-of-Thought (CoT) 几乎无提升。
  - 直接应用 Direct Preference Optimization (DPO) 而不结合 CoT 带来的改进也非常有限。
- **核心动机**：如何有效利用 CoT 推理步骤，结合偏好优化，以提升 LLMs 在 Text-to-SQL 上的推理准确率，同时避免对人工标注或奖励模型的依赖。

## 2. 方法论：ExCoT-DPO
- **核心思想**：以执行准确率（Execution Accuracy）作为唯一反馈信号，结合 CoT 推理与离策略 + 在策略 DPO，迭代优化模型。
- **关键技术步骤**：
  1. **CoT 数据生成与监督微调（SFT）**：
     - 使用 GPT-4o 生成多种 CoT 解决方案（简单 CoT 和复杂 CoT - 分治策略）。
     - 在本地 SQLite 中执行生成的 SQL，与真实结果比对，标记正确/错误。
     - 将正确的 CoT 样本用于 SFT，构建高质量 SFT 数据集（BIRD 5.6k, Spider 6.1k 条）。
  2. **离策略 DPO**：
     - 利用 GPT-4o 生成的正确/错误对构建偏好数据。
     - 选择编辑距离最大的正确-错误对（最大化差异，强化区分信号）。
  3. **在策略迭代 DPO**：
     - 使用当前模型自身生成的 CoT 数据（执行反馈验证正确性）。
     - 偏好对选择策略：选择编辑距离较小的正确-错误对（聚焦模型的细粒度错误）。
     - 迭代多轮（论文中 1 轮离策略 + 2 轮在策略）。
- **特点**：无需奖励模型、无需人工标注偏好，仅依赖执行结果。

## 3. 实验设计
- **数据集**：
  - **BIRD**（9.2k 训练查询）和 **Spider**（8.6k 训练查询），均为跨领域 Text-to-SQL 基准。
  - **评测指标**：执行准确率（EX%）和 SQL 有效性（Valid%）。
- **基准方法**：
  - 基础模型：LLaMA-3.1 70B、Qwen-2.5-Coder 32B。
  - 对比方法：零样本 CoT、SFT、离策略 DPO、在策略 DPO、纯在策略 DPO、不同采样策略、以及闭源模型（GPT-4o、Claude 3.5 Sonnet、o1-mini、o3-mini）和近期开源模型（XiYanSQL-QwenCoder 32B、CodeS 等）。
- **实验组数**：涵盖多种 CoT 类型、不同训练阶段、采样策略变体、轮次影响、消融实验（共数十组），并附带案例研究（附录 B）。

## 4. 资源与算力
- **硬件**：64 个 NVIDIA H100 GPU。
- **SFT**：batch size per GPU=2（全局 128），学习率 1e-5，训练 2 epochs，耗时 **448 GPU 小时**。
- **DPO**：batch size per GPU=1（全局 64），学习率 1e-6，每轮 2 epochs；1 轮离策略 + 2 轮在策略，总计 **160 GPU 小时**。
- **总计算成本**：约 608 GPU 小时。

## 5. 实验数量与充分性
- **充分性**：实验设计较为全面，覆盖：
  - 不同 CoT 形式（无 CoT、简单 CoT、复杂 CoT）。
  - 不同训练阶段（SFT、离策略 DPO、在策略 DPO）。
  - 不同采样策略（随机、最远、最近）的消融（表 3）。
  - 纯在策略 vs 离策略+在策略的对比（表 2）。
  - 多轮迭代的影响（图 2、图 3）。
  - 与多种闭源/开源模型的对比（表 1、表 4）。
- **公平性**：所有超参数固定，实验在相同条件进行；标注了 SOTA 单模型设置。
- **客观性**：执行准确率是固定的自动评测指标，避免主观性。

## 6. 主要结论与发现
1. **零样本 CoT 对 Text-to-SQL 无提升**；无 CoT 的 DPO 增益微小。
2. **SFT + 离策略 DPO + 在策略迭代 DPO 显著提升性能**：LLaMA-3.1 70B 在 BIRD 上从 57.37% 提升至 **68.51%**，在 Spider 上从 78.81% 提升至 **86.59%**。
3. **采样策略影响**：离策略 DPO 使用“最远”编辑距离最好；在策略 DPO 使用“最近”编辑距离最佳。
4. **在策略迭代轮次增加带来递减收益**，但至少两轮在策略有利。
5. **最佳模型在单模型设置中达到 SOTA**（BIRD 测试集 68.53%）。
6. **CoT 长度随训练增加**（从 560 tokens 增至 910 tokens），表明模型学会了更细致的推理。

## 7. 优点
- **方法简洁高效**：仅依赖执行反馈，无需人工标注或奖励模型，降低对齐成本。
- **可迭代自改进**：通过模型自身生成的 CoT 进行在策略 DPO，持续提升。
- **通用性强**：框架可迁移至其他结构化输出任务（如代码合成、逻辑推理）。
- **全面实验验证**：在两大基准上均取得 SOTA，并涵盖多组消融。
- **开源代码与模型**：促进复现与后续研究。

## 8. 不足与局限
- **复杂模式依赖领域知识**：高度专门化的数据库模式可能需要更丰富的领域数据或专家背景。
- **CoT 推理不完全可靠**：中间推理步骤可能存在局部正确但不一致、冗余或自相矛盾，影响下游 SQL 质量。
- **误差传播风险**：执行反馈仅确认最终结果，不保证推理逻辑完全正确；在关键应用（如医疗、政策）中需人工验证。
- **数据偏差**：训练数据的偏差可能被模型放大，导致生成查询不公平或不正确。
- **性能提升边际递减**：随着偏好对池枯竭，更多轮次迭代收益有限。
- **仅探索离线 DPO**：更高级的在线 DPO、PPO、GRPO 等方法留待未来。

（完）
