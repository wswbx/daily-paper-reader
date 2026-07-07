---
title: Teaching Language Models to Forecast Research Success Through Comparative Idea Evaluation
title_zh: 通过比较想法评估教会语言模型预测研究成功
authors: "Srujan P Mule, Aniketh Garikaparthi, Manasi Patwardhan"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1918.pdf"
tags: ["query:ar"]
score: 5.0
evidence: 自动化评估研究想法，支持自主研究
tldr: "本文研究如何让语言模型预测研究想法的成功率，通过构建11,488个想法对的数据集，采用SFT训练后模型准确率达77.1%，超越GPT-5。该方法可实现对AI生成研究想法的自动筛选，减少实验负担，有潜力推动自主研究流程。"
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1656, \"height\": 711, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1658, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 806, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1648, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 778, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 775, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 775, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 733, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 741, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 786, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 796, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 800, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 798, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1918/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 800, \"height\": 492, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 806, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 806, \"height\": 679, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 802, \"height\": 643, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 803, \"height\": 819, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1660, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 805, \"height\": 510, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1373, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1638, \"height\": 1719, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1653, \"height\": 1189, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 700, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 804, \"height\": 631, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1652, \"height\": 710, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1918/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 795, \"height\": 424, \"label\": \"Table\"}]"
motivation: AI生成大量研究想法后，评估筛选成为新瓶颈。
method: 构建比较性经验预测数据集，使用SFT训练语言模型。
result: "SFT模型准确率77.1%，超越GPT-5的61.1%。"
conclusion: 语言模型可有效预测研究想法成功性，助力自主研究。
---

## Abstract
As language models accelerate scientific research by automating hypothesis generation and implementation, a new bottleneck emerges: evaluating and filtering hundreds of AI-generated ideas without exhaustive experimentation. We ask whether LMs can learn to forecast the empirical success of research ideas before any experiments are run. We study comparative empirical forecasting : given a benchmark-specific research goal and two candidate ideas, predict which will achieve better benchmark performance. We construct a dataset of 11,488 idea pairs grounded in objective outcomes from PapersWithCode. While off-the-shelf 8B-parameter models struggle (30% acc.), SFT dramatically boosts performance to 77.1%, outperforming GPT-5 (61.1%). By framing evaluation as a reasoning task via Reinforcement Learning with Verifiable Rewards (RLVR), we train models to discover latent reasoning paths, achieving 71.35% acc. with interpretable justifications. Through additional ablations and out-of-distribution tests, we show robustness to surface-level heuristics and transfer to both a cross-domain time-split test set and an independently constructed test set. Our results demonstrate that compute-efficient small language models can serve as effective, objective verifiers, offering a scalable path for autonomous scientific discovery.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：语言模型正加速科学研究，可以自动生成假设、实施实验并分析结果。然而，当模型一次性生成数百个候选想法时，如何在不进行详尽实验的情况下有效评估和筛选这些想法，成为新的瓶颈。
- **现有方法局限**：当前评估多依赖语言模型对“兴奋度”、“创新性”、“新颖性”等主观准则的判断，但这些指标只是代理指标——一个想法可以新颖且论证充分，但在实践中仍然失败。
- **核心问题**：本文研究语言模型能否学习**比较性经验预测**——给定一个基准测试的研究目标和两个候选想法，预测哪个想法在基准测试上能取得更好的实证表现。目标是训练一个高效的小模型作为客观验证器，补充生成模型的规模，通过成对比较缩小候选池。

## 2. 论文提出的方法论

- **核心思想**：将比较性经验预测建模为偏好预测问题。构建大规模数据集，其中每个样本包含研究目标、两个想法描述、以及基于客观基准分数的二元标签（哪个想法更好）。然后通过监督微调（SFT）和强化学习（RL）训练语言模型，使其学会预测。
- **数据集构建**：
  - 从PapersWithCode爬取NLP排行榜，获取724个有效基准、5695篇结果报告论文和832篇原始论文。
  - 用LLM（Gemini-2.5-pro）提取每个想法的详细信息（排除实证结果、比较、模型名称等）。
  - 对每个基准内所有想法计算统一分数（归一化指标，若多指标则平均），并按分数标准差σ划分难度等级：1σ（难）、2σ（中）、3σ（易）。
  - 生成所有可能想法对（共11,488对），并进行交换增强以避免位置偏差。
- **训练方法**：
  - **SFT（直接预测）**：输入研究目标和两个想法，输出二元标签。使用交叉熵损失。
  - **RL（推理生成）**：两阶段训练：
    1. **冷启动SFT**：在小规模推理轨迹子集上微调（包括从GPT-5提取的合成推理轨迹和从论文内容提取的文献接地推理）。
    2. **GRPO变体**：使用DAPO或Dr.GRPO策略优化，奖励函数包含正确性（±3）和格式（±0.5）。
- **推理形式**：模型需先生成推理链（CoT），再输出最终预测。RL训练鼓励模型探索导致正确预测的潜在推理路径。

## 3. 实验设计

- **数据集**：
  - 主数据集：11,488个想法对，基于724个NLP基准排行榜。训练集10,619对，测试集869对（手动验证）。
  - 跨领域测试集：705个想法对，来自非NLP基准（如语音合成、分子属性预测），年份≥2024，使用GPT-5提取想法。
  - 独立构建测试集：来自Wen等人（2025）的1,750个想法对，无重叠。
- **基准方法**：
  - 基础模型：Qwen3-8B、Llama3.1-8B（零样本、推理模式）。
  - 前沿模型：GPT-5（低/中/高推理努力）、Gemini 2.5 Flash。
  - 消融：3-shot GPT-5、不同训练变体（Direct-SFT、Reason-SFT、Reason-DAPO等）。
- **评估指标**：一致性准确率（交换位置后预测一致且正确）。还报告了条件准确率、排名指标（Top-1准确率、RMSE）、校准指标（Brier、ECE、MCE）、鲁棒性偏差检验（长度、新近性、释义）。
- **鲁棒性测试**：对长度偏好、新近性偏好、释义后性能进行bootstrap统计检验。

## 4. 资源与算力

- **硬件**：所有训练在NVIDIA A100-40GB GPU上进行，使用BF16精度。未明确指出GPU数量。
- **训练配置**：
  - SFT：LoRA rank=64, α=128, dropout=0.1, batch_size=2, lr=2e-4, weight_decay=0.01, 1 epoch。
  - RL：LoRA rank=64, α=128, dropout=0, batch_size=1, lr=5e-6, group_size=4, β=1e-5, max_output_tokens=3600。
- **模型规模**：8B参数（Qwen3-8B, Llama3.1-8B），远小于GPT-5等前沿模型。

## 5. 实验数量与充分性

- **实验组数**：
  - 主实验：对比了6种Qwen3变体、2种Llama3.1变体、GPT-5三种推理设置、Gemini 2.5 Flash，共约12组模型在测试集上的表现。
  - 消融实验：3-shot GPT-5、不同难度子集（1σ/2σ/3σ）、跨领域测试、独立测试集、2025年只有子集、条件准确率、排名评估、校准评估。
  - 鲁棒性分析：长度、新近性、释义三类偏差的bootstrap显著性检验（10,000次重采样），报告置信区间和p值。
- **充分性**：实验设计较为全面，涵盖了不同训练范式、不同难度、不同领域、不同构建来源的数据集，并进行了统计检验和偏差分析。但未在真实想法生成工作流中验证实用性（论文在局限性中承认）。

## 6. 主要结论与发现

- **基础模型差**：未训练的8B模型准确率约20-30%（随机猜测约25%）。
- **SFT大幅提升**：Qwen3-8B Direct-SFT达到77.1%，超越GPT-5的61.1%（高推理努力）。
- **RL可实现可解释推理**：Reason-SFT-DAPO和Reason-SFT-DrGRPO达到71.35%准确率，且能生成连贯的推理轨迹。
- **泛化能力强**：在跨领域测试集上，所有训练模型与GPT-5持平或更优；在独立构建的测试集上（Wen et al.），Reason-SFT-DrGRPO达到67.49%，超过GPT-4.1+检索的51.4%。
- **鲁棒性**：除新近性偏好外，模型对长度和释义不敏感；新近性偏好可能反映科学进步的真实先验。
- **排名潜力**：训练模型在想法排名任务上（Top-1准确率和RMSE）优于或持平GPT-5。

## 7. 优点

- **大规模高质量数据集**：基于客观排行榜分数构建，手动验证测试集，包含难度分层和跨领域变体。
- **计算高效**：8B参数小模型通过微调即可超越前沿大模型，可访问性强。
- **可解释性**：通过RL训练，模型能生成结构化推理，解释为何一个想法更好。
- **鲁棒性分析全面**：对位置偏差、长度、新近性、释义进行了统计检验，证实非表面启发。
- **方法创新**：将评估问题转化为推理任务，结合SFT和RLVR有效诱导推理能力。

## 8. 不足与局限

- **数据源噪声**：基于PapersWithCode（已关闭），但方法论可迁移到其他排行榜。
- **领域限制**：当前仅限NLP基准，扩展到其他科学领域需额外数据构建和验证。
- **未验证工作流实用性**：虽提议作为想法筛选组件，但未在完整创意生成流程中评估效果。
- **推理质量问题**：RL训练易出现奖励黑客（如重复简短句子），Reason-SFT-DrGRPO趋于最小化推理，可解释性打折。
- **新近性偏好**：所有模型表现出统计显著的新近性偏好，虽被认为是领域特征，但可能导致对较旧但有潜力想法的偏见。
- **校准性能**：RL变体的最大校准误差（MCE）较高，表明在某些置信区间预测不可靠。

（完）
