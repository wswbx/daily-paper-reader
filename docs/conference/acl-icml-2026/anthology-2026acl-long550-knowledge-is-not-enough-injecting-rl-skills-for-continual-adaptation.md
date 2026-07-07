---
title: "Knowledge is Not Enough: Injecting RL Skills for Continual Adaptation"
title_zh: 知识不足：注入RL技能实现持续自适应
authors: "Pingzhi Tang, Yiding Wang, Muhan Zhang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.550.pdf"
tags: ["query:skill-rl"]
score: 8.0
evidence: 通过参数技能迁移注入RL技能实现持续自适应
tldr: 针对大语言模型知识截止和强化学习计算成本高的问题，PaST通过观察SFT和RL参数更新近似正交，提出参数技能迁移框架，将RL学到的技能以参数形式注入LLM，仅需少量计算即可实现持续自适应，实验证明该方法在知识更新和技能获取方面效果显著。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.550/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1597, \"height\": 1071, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.550/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 772, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.550/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1652, \"height\": 767, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.550/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 775, \"height\": 630, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1631, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 473, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 796, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 696, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 682, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 759, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 798, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 714, \"height\": 308, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1344, \"height\": 585, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1164, \"height\": 574, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1409, \"height\": 992, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1083, \"height\": 1169, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1116, \"height\": 468, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.550/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 902, \"height\": 787, \"label\": \"Table\"}]"
motivation: LLM面临知识截止问题，SFT难以获得推理技能，RL计算成本高。
method: 提出PaST框架，基于SFT与RL更新正交性，通过参数迁移注入RL技能。
result: 实验显示PaST有效提升了LLM在新知识上的推理和决策能力，且计算开销低。
conclusion: PaST为LLM的持续学习提供了一种高效的技能注入方法。
---

## Abstract
Large Language Models (LLMs) face the "knowledge cutoff" challenge, where their frozen parametric memory prevents direct internalization of new information. While Supervised Fine-Tuning (SFT) is commonly used to update model knowledge, it often updates factual content without reliably improving the model’s ability to use the newly incorporated information for question answering or decision-making. Reinforcement Learning (RL) is essential for acquiring reasoning skills; however, its high computational cost makes it impractical for efficient online adaptation. We empirically observe that the parameter updates induced by SFT and RL are nearly orthogonal. Based on this observation, we propose **Parametric Skill Transfer (PaST)**, a framework that supports modular skill transfer for efficient and effective knowledge adaptation. By extracting a domain-agnostic **Skill Vector** from a source domain, we can linearly inject knowledge manipulation skills into a target model after it has undergone lightweight SFT on new data. Experiments on knowledge-incorporation QA (SQuAD, LooGLE) and agentic tool-use benchmarks (ToolBench) demonstrate the effectiveness of our method. On SQuAD, PaST outperforms the state-of-the-art self-editing SFT baseline by up to 9.9 points. PaST further scales to long-context QA on LooGLE with an 8.0-point absolute accuracy gain, and improves zero-shot ToolBench success rates by +10.3 points on average with consistent gains across tool categories, indicating strong scalability and cross-domain transferability of the Skill Vector.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）面临“知识截止”问题，其冻结的参数记忆无法直接内化新信息。常用方法监督微调（SFT）虽能注入事实知识，却难以提升模型对新知识的推理和决策能力；而强化学习（RL）虽擅长学习推理技能，但计算成本极高，不适合频繁的在线适应。
- **整体含义**：本文指出知识（通过SFT获取）与技能（通过RL获取）在模型中存在“功能脱节”——模型“知道”事实但不会“使用”事实。现有参数更新方法在知识适应中忽视了这一脱节，导致模型在新领域中缺乏执行逻辑。
- **研究动机**：需要一种既能利用RL的推理优势，又能避免在每次知识更新时重新运行RL的高效方法。

## 2. 方法论

- **核心思想**：基于实证发现——SFT诱导的参数更新（ΔW_SFT）与RL诱导的更新（ΔW_RL）在参数空间中近乎正交，说明知识与技能的解耦。因此，可以将RL学到的技能提取为独立的“技能向量”，并线性注入到经过轻量SFT的新知识模型中。
- **关键技术细节**：
  - **技能向量提取**：在源域中，先对基模型进行SFT（获得θ_sft^S），再在其基础上进行RL（获得θ_rl^S），技能向量定义为v_skill = θ_rl^S – θ_sft^S。该向量捕获了域无关的推理逻辑。
  - **目标域适应**：对目标域进行轻量SFT（获得θ_sft^T），然后将技能向量线性注入：θ_final = θ_sft^T + λ·v_skill（实验默认λ=1）。
  - **迭代技能精炼**：将源数据分为K个不相交子集，每一轮先SFT，再注入上一轮技能向量作为RL初始化，训练后更新技能向量。这迫使技能向量收敛到内容不变的推理模式。
- **算法流程简述**（文本描述）：
  1. 初始化v0 = 0。
  2. 对每轮k = 1…K：
     a. 对源子集进行SFT获得θ_sft^k；
     b. 注入上一轮技能：θ_init = θ_sft^k + v_{k-1}；
     c. 进行RL（GRPO/PPO）获得θ_rl^k；
     d. 更新技能向量：v_k = θ_rl^k – θ_sft^k。
  3. 输出最终技能向量v*，用于目标域。

## 3. 实验设计

- **数据集与场景**：
  - **SQuAD**（闭书知识融入）：模型先通过测试时权重更新记忆段落，然后不提供上下文回答问题。采用单一文档、CPT（n=200）和CPT（n=2067）三种规模。
  - **LooGLE**（长上下文QA）：文档平均超21k tokens，评估短依赖QA任务。源域使用最后10个文档，目标域使用前50个文档。
  - **ToolBench**（闭书工具使用）：模型仅靠参数记忆API名称，需多轮交互完成任务。源域为Movies类别，目标域为20个RL未见过的工具类别。
- **基准（Baseline）**：
  - SQuAD: 对比Base Model、Passage-Only SFT、SFT + Synthetic Data、SFT + GPT-4.1 Data、SEAL（SOTA自编辑方法）。
  - LooGLE: 对比标准SFT基线。
  - ToolBench: 对比Target SFT基线（无技能注入）。
- **对比方法**：除了上述基线，还进行了消融比较：
  - 迭代精炼 vs 单轮提取。
  - 不同传输策略（顺序微调、预注入、后注入）。
  - 与目标域直接RL对比。

## 4. 资源与算力

- **GPU型号**：所有实验使用NVIDIA A100 80GB GPU。
- **资源分配**：
  - SQuAD：单文档LoRA使用2张A100（1张vLLM推理，1张更新）；CPT（200/2067文档）全微调使用1张。
  - LooGLE：SFT与RL阶段均使用8张A100。
  - ToolBench：SFT阶段使用8张A100；RL阶段使用4张A100。
- **训练时长**：文中未给出所有实验总时长，但在比较目标域RL时提到：每文档RL训练需33–91分钟（25–100步），而PaST额外时间为0（因为技能向量预先提取）。SFT阶段时长未明确列出。

## 5. 实验数量与充分性

- **实验数量**：共涵盖3个主要任务，每个任务包含多个子实验：
  - SQuAD：3种规模×多个方法，加消融（迭代精炼对比2轮vs单轮）。
  - LooGLE：主实验（SFT vs PaST 1轮/2轮），消融（迭代K×M权衡、传输策略、与目标RL对比）。
  - ToolBench：20个目标类别×2方法（基线 vs PaST），还含跨类别统计。
- **充分性与公平性**：
  - 对比基线均为当前SOTA或标准方法（SEAL、SFT变体），且使用相同的数据生成范式。
  - 消融实验设计系统：控制数据量、步数、频率等变量。
  - 结果均取多次独立运行的平均值（如LooGLE报告3次，ToolBench3次），使用GPT-4.1作为公正评估者。
  - 实验设计较全面，覆盖知识融入、长上下文、工具使用三种不同能力域，证明了方法的泛化性和鲁棒性。

## 6. 主要结论与发现

- **SFT和RL参数更新近似正交**：在LooGLE上可视化余弦相似度接近零，而两个SFT更新则正相关。这一发现为技能向量可分离、可迁移提供了实证与理论（激活空间解耦）基础。
- **PaST显著提升知识利用能力**：
  - SQuAD上，PaST（两轮迭代）达到56.9%准确率，超过SEAL（47.0%）和GPT-4.1合成（46.3%），提升达+17.2%。
  - LooGLE上，仅5个源文档提取的技能向量使准确率从30.1%提升至38.1%（绝对+8.0%）。
  - ToolBench上，零样本跨域转移提升平均成功率+10.3%，所有20个目标类别均获益，包括两个基数为0的类别。
- **迭代精炼优于单轮提取**：多轮迭代使技能向量更关注内容无关的推理逻辑，避免过拟合到特定源数据。
- **后注入方式最佳**：先SFT目标知识再注入技能向量，优于顺序微调或预注入，因为避免了SFT对技能向量的干扰。
- **与目标域RL对比**：PaST（0额外训练时间）在LooGLE上达到44.6%，而100步目标域RL为46.2%，PaST以极低成本获得接近的性能。

## 7. 优点

- **创新性**：首次发现并利用SFT与RL更新的正交性，据此提出参数级技能解耦与线性组合方法。
- **高效性**：避免在目标域进行昂贵的RL，仅需轻量SFT和一次向量加法，适合持续适应的场景。
- **跨域泛化强**：技能向量可迁移至完全不同的知识域和工具类别，零样本激活新域的能力。
- **实验设计系统**：涵盖知识、长上下文、工具使用三类任务，并进行多重消融，验证了方法各组件贡献。
- **可解释性**：对正交性提供数学推导（Hanson-Wright不等式），从理论角度支撑了技能与知识的可分离性。

## 8. 不足与局限

- **实验领域广度有限**：虽然覆盖QA和工具使用，但“源到目标”的迁移场景还可以进一步扩展（如多步推理、数学推理等）。
- **缩放系数静态**：λ始终设为1，未探索不同领域的最佳缩放系数，可能限制了性能上限。
- **模型架构泛化待验证**：主实验基于Qwen2.5-7B（基础/指令版），虽理论上正交性普遍成立，但跨不同架构（如不同规模、不同初始化）的验证尚不充分。
- **技能向量抽取依赖源域RL质量**：若源域RL训练不足或奖励设计有偏，技能向量可能携带噪声，影响下游效果。
- **长上下文实验中数据处理较复杂**：生成合成QA和多任务数据依赖于基模型自身，可能存在自我强化偏差。

（完）
