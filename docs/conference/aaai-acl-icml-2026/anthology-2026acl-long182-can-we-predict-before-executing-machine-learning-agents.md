---
title: Can We Predict Before Executing Machine Learning Agents?
title_zh: 能否在执行前预测机器学习智能体的结果？
authors: "Jingsheng Zheng, Jintian Zhang, Yujie Luo, Yuren Mao, Yunjun Gao, Lun Du, Huajun Chen, Ningyu Zhang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.182.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 预测机器学习智能体的执行结果以减少物理执行成本
tldr: "自主科研智能体受限于执行瓶颈，假设评估依赖昂贵的物理执行。本文提出在执行前预测结果，通过构建数据偏好语料库和利用验证数据分析报告，LLM能实现61.5%的预测准确率，为绕开物理执行提供了可行路径。"
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 789, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1657, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1628, \"height\": 861, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1636, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1266, \"height\": 1272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1441, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1642, \"height\": 774, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1621, \"height\": 716, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1647, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1564, \"height\": 1254, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.182/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1739, \"height\": 323, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 799, \"height\": 558, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1657, \"height\": 1133, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 792, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 611, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 714, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1605, \"height\": 1861, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1615, \"height\": 837, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1654, \"height\": 930, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1657, \"height\": 1715, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1625, \"height\": 836, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1268, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1142, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1481, \"height\": 1252, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1110, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1522, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1156, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.182/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1429, \"height\": 245, \"label\": \"Table\"}]"
motivation: 物理执行昂贵且耗时，需要预测机制加速自主研究。
method: 构建数据偏好语料库，利用验证数据分析报告引导LLM进行预测。
result: "LLM在预测任务上达到61.5%准确率，具有鲁棒置信度。"
conclusion: 预测执行结果可显著降低自主研究智能体的运行成本。
---

## Abstract
Autonomous machine learning agents have revolutionized scientific discovery, yet they remain constrained by a Generate-Execute-Feedback paradigm. Previous approaches suffers from a severe Execution Bottleneck, as hypothesis evaluation relies strictly on expensive physical execution. To bypass these physical constraints, we internalize execution priors to substitute costly runtime checks with instantaneous predictive reasoning, drawing inspiration from World Models. In this work, we formalize the task of Data-centric Solution Preference and construct a comprehensive corpus of 18,438 pairwise comparisons. We demonstrate that LLMs exhibit significant predictive capabilities when primed with a Verified Data Analysis Report, achieving 61.5% accuracy and robust confidence calibration. Finally, we instantiate this framework in ForeAgent, an agent that employs a Predict-then-Verify loop, achieving a 6x acceleration in convergence while surpassing execution-based baselines by +6%.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 一、论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：自主机器学习智能体在科学发现中广泛应用，但依赖“生成-执行-反馈”循环，每次假设评估都需要昂贵的物理执行（如训练深度学习模型），导致**执行瓶颈**（Execution Bottleneck）。例如MLE-Bench中单次运行可长达9小时。
- **研究目标**：能否将数小时的物理执行压缩为几秒的逻辑推理？即**在执行前预测哪个解决方案更优**，从而绕过物理执行成本。
- **灵感来源**：源于强化学习中的**世界模型（World Model）**，智能体通过内部模拟评估行动，而非外部试错。本文将其扩展到代码/数据领域，实现“隐式执行先验”。

## 二、论文提出的方法论

### 核心思想
- **形式化任务**：**数据中心的解决方案偏好（Data-centric Solution Preference）**——给定任务描述、数据报告、两个候选代码，预测哪个更好及其置信度。
- **关键组件**：
  1. **验证数据分析报告（Verified Data Analysis Report）**：通过“代码生成→执行验证→语义化总结”三步将原始数据统计转化为因果语义叙述，桥接数值与语义空间。
  2. **预测机制**：利用LLM（如DeepSeek-V3.2-Thinking）在推理模式下（CoT）分析任务、数据报告和代码，输出偏好及置信度。
  3. **ForeAgent框架**：将预测作为筛选器，采用**预测-验证循环**（Predict-then-Verify）：
     - 并行生成多个候选（m=10，扩展搜索宽度）
     - 用世界模型低开销筛选（置信度门控c=0.7）
     - 仅对Top-1候选进行物理执行验证，确保不确定决策不引入执行成本。

### 关键技术细节
- **输入表示**：`X = (I, D_rep, {C0, C1}, P)`，其中`D_rep`为验证数据分析报告。
- **输出**：推理链`cot`、预测胜者`y_hat`（二进制）、置信度`c ∈ [0,1]`。
- **语料库构建**：
  - 来源：AIDE和AutoMind两个智能体在MLE-Bench平台上运行的真实轨迹（使用DeepSeek-V3.1和o3-mini）。
  - 过滤：专家参与去重、标签标注、算法多样性采样，得到895个高质量实例。
  - 配对：产生18,438对比较，平衡位置偏差。

## 三、实验设计

### 数据集/场景
- **预测语料库**：18,438对比较，覆盖26个不同任务，分三大领域：计算机视觉（9个任务）、自然语言处理（8个任务）、数据科学（9个任务）。任务包括分类、回归、匹配、排序、分割等。
- **Agent集成测试**：5个AI4Science任务（MLE-Bench子集），包括2个未见过任务（Aerial Cactus Identification、Histopathologic Cancer Detection）。

### Benchmark与对比方法
- **预测任务基线**：
  1. 随机猜测（50%）
  2. 复杂度启发式（50.8%）：LLM对代码从工程复杂度、模型架构、数据流水线三个维度打分，取总分高者。  
  3. 执行验证（M_val）作为理论上限（72.2%）。
- **Agent集成基线**：标准的AIDE智能体（12小时限制）。
- **模型**：
  - 主模型：DeepSeek-V3.2-Thinking（推理模式）、GPT-5.1（gpt-5.1-2025-11-13）同样使用推理指令。
  - 消融模型：Qwen系列（4B~1T）、不同规模、有无CoT等。

## 四、资源与算力

- **硬件**：Intel Xeon Gold 6138 CPU（80逻辑核，2.00GHz） + 6× NVIDIA GeForce RTX 3090 GPU（各24GB VRAM）。并行化评估，6个并发worker，每个任务分配独立GPU。
- **Token消耗**：
  - 主预测基准（18,438对）约78.5M tokens（输入+输出）。
  - 消融实验子集约9.6M tokens。
  - Agent基线（AIDE等）因自动反馈循环导致token用量高度随机，未精确统计。
- **训练时长**：论文未声明模型训练过程，仅评估现有LLM；Agent集成实验基于12小时执行预算。

## 五、实验数量与充分性

- **主实验**：18,438对比较，报告准确率（61.5% vs 58.8%），并分领域、难度、算法时代、粒度、复杂度等维度分析，统计显著。
- **机制分析（RQ1–RQ4）**：四项系统性研究：
  - RQ1：数据表示（Code Only → Raw Data → Numerical Stats → Verbal Report），验证语义理解的关键作用。
  - RQ2：推理能力、领域敏感性、排名泛化、置信度校准。
  - RQ3：缩放定律（参数规模与准确率关系），发现非传统缩放模式（早期饱和）。
  - RQ4：与人类判断对比、验证-测试差距。
- **Agent集成**：5个AI4Science任务×3次独立运行，报告平均Beat Ratio、速度提升、搜索扩展倍数。
- **消融实验**：温度稳定性、轨迹方差、Top-k选型、复杂度差距等（附录C）。
- **充分性评价**：实验设计较为全面，覆盖预测阶段和Agent应用阶段，消融深入，统计严格（多次运行、标准偏差）。未遗漏常见消融变量（如推理模式、模型规模）。客观性方面，对基线（复杂度启发式）和上限（M_val）均进行了清晰界定，并讨论了潜在的过拟合风险。

## 六、论文的主要结论与发现

1. **LLM展现显著预测能力**：DeepSeek-V3.2-Thinking达61.5%准确率，远超随机（50%）和复杂度启发式（50.8%），验证了执行可被推理部分替代。
2. **预测源于语义理解而非复杂度偏差**：验证数据分析报告是核心，数值统计直接输入增益有限；模型能拒绝“越大越好”偏见，优先考虑数据-模型匹配。
3. **确认推理导向架构而非纯规模带来的优势**：缩放定律显示参数规模至30B后收益递减，但推理优化模型（DeepSeek-V3.2 vs Qwen系列）显著领先。
4. **良好的置信度校准**：高置信度样本准确率可达86.8%，支持可靠的门控机制。
5. **ForeAgent实现6倍加速和+6%性能提升**：通过预测筛选，搜索空间扩展3.2倍，验证-测试差距部分缓解，中间迭代成功率提高23%（测试改进率）。
6. **验证-测试差距上限**：仅依赖执行验证（M_val）的准确率72.2%，说明即使完美预测也无法超越验证代理的局限性。

## 七、优点

- **问题定义新颖**：正式提出数据中心的解决方案偏好任务，弥合了执行前预测与实际ML工作流之间的差距。
- **语料库规模大且真实**：18,438对比较来自真实智能体轨迹（含中途不完美状态），而非合成数据。
- **验证数据分析报告机制**：有效将数值特征转化为语义因果关系，避免LLM处理高熵数值的弱点，同时保证事实性（通过执行验证）。
- **系统性的机理分析**：从数据表示、推理模式、缩放定律、人类对比等多角度解释模型如何运作，不仅报告结果。
- **实用Agent集成**：ForeAgent不仅加速，还提升性能，展示了从预测到行动的有效转化，并开放代码和数据集。
- **开源贡献**：代码、数据集公开，促进可复现研究和后续方向（如奖励模型训练）。

## 八、不足与局限

- **语料不平衡与领域覆盖不全面**：26个任务中分类/回归占主导，而多标签分类、排序、提取等样本少，对音频、实时终端等长尾科学场景的泛化能力未充分验证。
- **验证数据分析报告依赖元数据**：对CV和NLP的非结构化数据仅使用元数据，未集成多模态分析代理进行深度语义剖析。
- **Agent集成实现保守**：ForeAgent采用严格的预测-验证循环，仅为简单Top-1筛选，未探索更复杂的推理时策略（如多轮交互、自适应置信阈值）。作者承认报告的性能可能是框架能力的下界。
- **未扩展到通用奖励模型**：虽然讨论了指出的潜力，但未实验验证用作强化学习奖励模型的可行性。
- **静态预测的固有上限**：由于验证-测试差距（72.2%），静态预测无法超越动态验证的性能，且当前模型存在**同质性屏障**，生成的功能上相似的解决方案缺乏真正创新。
- **评估环境限制**：实验仅在一个平台（MLE-Bench）和两个智能体（AIDE、AutoMind）上展开，未来需更多样化的环境和智能体验证鲁棒性。
- **算力资源消耗虽优化但仍显著**：尽管引入了预测，整体系统仍需GPU集群支持；预测过程消耗约78.5M tokens，对高吞吐量场景仍有负担。

（完）
