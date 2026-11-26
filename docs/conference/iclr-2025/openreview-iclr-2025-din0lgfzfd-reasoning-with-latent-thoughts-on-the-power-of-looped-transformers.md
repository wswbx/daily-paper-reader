---
title: "Reasoning with Latent Thoughts: On the Power of Looped Transformers"
title_zh: 以潜在思维进行推理：论循环 Transformer 的能力
authors: "Nikunj Saunshi, Nishanth Dikkala, Zhiyuan Li, Sanjiv Kumar, Sashank J. Reddi"
date: 2025-01-22
pdf: "https://proceedings.iclr.cc/paper_files/paper/2025/file/2676109d49d1eb26d6bc584a8f556305-Paper-Conference.pdf"
tags: ["query:looped-llm"]
score: 10.0
evidence: 研究k层结构循环L次的循环Transformer架构
tldr: 缩放定律通常把大模型推理能力归因于参数量与深度。作者提出许多推理问题只需要大深度而非多参数，并系统研究循环Transformer。实验发现k层模型循环L次即可接近kL层非循环模型的表现，显著优于单次k层模型，理论分析也表明这类问题可用迭代算法求解。该结果揭示了以重复计算替代参数扩张的推理新路径。
source: ICLR-2025-Accepted
selection_source: topic_research
id: openreview-iclr-2025-din0lgfzfd
canonical_id: "work:c720d6d299d34090937dc82b"
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
official_pdf_url: "https://proceedings.iclr.cc/paper_files/paper/2025/file/2676109d49d1eb26d6bc584a8f556305-Paper-Conference.pdf"
official_link: "https://proceedings.iclr.cc/paper_files/paper/2025/hash/2676109d49d1eb26d6bc584a8f556305-Abstract-Conference.html"
conference_acceptance_status: accepted
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-001.webp\", \"caption\": \"\", \"page\": 6, \"index\": 1, \"width\": 566, \"height\": 540}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-002.webp\", \"caption\": \"\", \"page\": 6, \"index\": 2, \"width\": 558, \"height\": 548}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-003.webp\", \"caption\": \"\", \"page\": 6, \"index\": 3, \"width\": 558, \"height\": 540}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-004.webp\", \"caption\": \"\", \"page\": 6, \"index\": 4, \"width\": 581, \"height\": 541}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-005.webp\", \"caption\": \"\", \"page\": 7, \"index\": 5, \"width\": 790, \"height\": 593}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-006.webp\", \"caption\": \"\", \"page\": 7, \"index\": 6, \"width\": 790, \"height\": 593}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-007.webp\", \"caption\": \"\", \"page\": 7, \"index\": 7, \"width\": 800, \"height\": 593}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-008.webp\", \"caption\": \"\", \"page\": 16, \"index\": 8, \"width\": 3600, \"height\": 2400}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-009.webp\", \"caption\": \"\", \"page\": 16, \"index\": 9, \"width\": 3600, \"height\": 2400}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-010.webp\", \"caption\": \"\", \"page\": 16, \"index\": 10, \"width\": 3600, \"height\": 2400}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-011.webp\", \"caption\": \"\", \"page\": 16, \"index\": 11, \"width\": 3600, \"height\": 2400}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-012.webp\", \"caption\": \"\", \"page\": 17, \"index\": 12, \"width\": 2758, \"height\": 852}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-013.webp\", \"caption\": \"\", \"page\": 21, \"index\": 13, \"width\": 560, \"height\": 540}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-014.webp\", \"caption\": \"\", \"page\": 21, \"index\": 14, \"width\": 560, \"height\": 540}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-015.webp\", \"caption\": \"\", \"page\": 21, \"index\": 15, \"width\": 560, \"height\": 540}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-016.webp\", \"caption\": \"\", \"page\": 21, \"index\": 16, \"width\": 560, \"height\": 540}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-017.webp\", \"caption\": \"\", \"page\": 22, \"index\": 17, \"width\": 816, \"height\": 593}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-018.webp\", \"caption\": \"\", \"page\": 22, \"index\": 18, \"width\": 790, \"height\": 593}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-019.webp\", \"caption\": \"\", \"page\": 22, \"index\": 19, \"width\": 800, \"height\": 593}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-020.webp\", \"caption\": \"\", \"page\": 25, \"index\": 20, \"width\": 1074, \"height\": 1366}, {\"url\": \"assets/figures/openreview/openreview-iclr-2025-din0lgfzfd/fig-021.webp\", \"caption\": \"\", \"page\": 25, \"index\": 21, \"width\": 1096, \"height\": 1328}]"
motivation: 缩放定律认为参数尤其是深度驱动推理能力，作者质疑推理是否真的需要大量参数。
method: 采用循环Transformer把k层结构重复L次，并在加法、p跳归纳和数学等合成推理任务上与非循环模型对比。
result: 实验表明循环L次的k层模型性能接近kL层非循环模型，且显著优于仅k层模型。
conclusion: 说明许多推理问题只需大深度而无需多参数，为循环模型在推理中的应用提供理论与实证支持。
---

## 摘要
大语言模型已展现出显著的推理能力，而缩放定律表明，大量参数——尤其是沿深度轴——是其主要驱动因素。在本工作中，我们提出一个更强的论断：许多推理问题需要较大的深度，但不一定需要很多参数。这解锁了循环模型在推理中的一种新颖应用。首先，我们表明，对于许多合成推理问题，如加法、p-hop 归纳和数学问题，一个循环 L 次的 k 层 Transformer 几乎能匹敌 kL 层非循环模型的性能，并且显著优于 k 层模型。理论结果进一步佐证了这一点：许多此类推理问题可以通过迭代算法求解，因此可以用具有近乎最优深度的循环模型有效求解。也许令人惊讶的是，这些优势也延伸到语言建模的实际场景中——在许多下游推理任务上，一个循环 L 次的 k 层语言模型可以与 kL 层语言模型相竞争，甚至更优。事实上，我们的实证分析揭示了一个有趣现象：循环模型和非循环模型表现出依赖于其有效深度的缩放行为，类似于思维链（CoT）推理的推理时缩放。我们进一步通过证明循环模型隐式生成潜在思维，并可用 T 次循环模拟 T 步 CoT，来阐明其与 CoT 推理的联系。受这些发现启发，我们还提出了推理与记忆之间一种有趣的两分法，并设计了一种在两方面均有效的基于循环的正则化。

## Abstract
Large language models have shown remarkable reasoning abilities and scaling laws suggest that large parameter count, especially along the depth axis, is the primary driver. In this work, we make a stronger claim --- many reasoning problems require a large depth but not necessarily many parameters. This unlocks a novel application of looped models for reasoning. Firstly, we show that for many synthetic reasoning problems like addition, $p$-hop induction, and math problems, a $k$-layer transformer looped $L$ times nearly matches the performance of a $kL$-layer non-looped model, and is significantly better than a $k$-layer model. This is further corroborated by theoretical results showing that many such reasoning problems can be solved via iterative algorithms, and thus, can be solved effectively using looped models with nearly optimal depth. Perhaps surprisingly, these benefits also translate to practical settings of language modeling --- on many downstream reasoning tasks, a language model with $k$-layers looped $L$ times can be competitive to, if not better than, a $kL$-layer language model. In fact, our empirical analysis reveals an intriguing phenomenon: looped and non-looped models exhibit scaling behavior that depends on their effective depth, akin to the inference-time scaling of chain-of-thought (CoT) reasoning. We further elucidate the connection to CoT reasoning by proving that looped models implicitly generate latent thoughts and can simulate $T$ steps of CoT with $T$ loops. Inspired by these findings, we also present an interesting dichotomy between reasoning and memorization, and design a looping-based regularization that is effective on both fronts.

---

## 论文详细总结（自动生成）

# 论文总结：Reasoning with Latent Thoughts: On the Power of Looped Transformers

## 1. 核心问题与整体含义

- **研究动机**：大语言模型的推理能力通常被归因于参数规模，尤其是深度。缩放定律也显示参数数量是性能的主要驱动因素。论文提出更强论断：**许多推理问题需要较大“有效深度”，但不一定需要很多参数**。
- **核心问题**：能否用“少量参数、反复计算”的循环模型替代“大量参数、深层堆叠”的非循环模型来完成推理？循环模型是否不仅在合成推理任务上有效，也能在真实语言建模的下游推理任务中表现出有利的归纳偏置？
- **整体含义**：论文将 **k 层 Transformer 循环 L 次**记为 \((k \otimes L)\)，其参数量与 \((k \otimes 1)\) 相同，FLOPs/有效深度与 \((kL \otimes 1)\) 非循环模型相近。作者主张循环模型是研究“深度换参数”的重要架构，并把它与思维链（CoT）的潜在思维、推理时缩放联系起来。
- **四个核心主张**：
  - 许多推理问题需要深度但不需要大量参数，可通过循环模型求解；
  - 语言建模中，循环模型尽管困惑度较差，但对推理任务有归纳偏置；
  - 循环模型隐式生成“潜在思维”，理论上可用 T 次循环模拟 T 步 CoT；
  - 受循环模型启发，可设计正则化，在保持困惑度的同时提升推理。

## 2. 方法论

### 2.1 循环 Transformer 的基本思想

- 对任意序列到序列函数 \(f\)，循环 L 次即 \(f^{(L)}=f\circ f\circ\cdots\circ f\)。
- 在论文中 \(f\) 通常是 k 层 Transformer 主干；\((k \otimes L)\) 表示同一组 k 层权重被重复应用 L 次。
- 对比基线：
  - **iso-param 基线** \((k \otimes 1)\)：k 层非循环模型，参数量与循环模型相同；
  - **iso-flop 基线** \((kL \otimes 1)\)：kL 层非循环模型，有效深度/FLOPs 与循环模型相近，但参数量多 L 倍；
  - **循环模型** \((k \otimes L)\)：参数少、深度大。
- 论文还探索了 **middle looping**：首尾层保持独立，仅对中间层块循环，以兼顾表达力和困惑度。

### 2.2 合成推理任务上的训练方式

- 直接在输入-输出对上训练，不使用 CoT 中间步骤。
- 任务包括：
  - **n 元加法**：多个 3 位数相加，训练 n 的混合，评估更大 n；
  - **p-hop induction**：在字母序列中递归回溯 p 次，测试递归检索能力；
  - **i-GSM**：符号化的小学数学应用题，由算术 DAG 构成，模 7 运算，图深度限制为 4。
- 核心比较：\((k \otimes 12/k)\) 或 \((k \otimes L)\) 循环模型 vs \((k \otimes 1)\) iso-param vs \((kL \otimes 1)\) iso-flop。

### 2.3 语言建模与评估指标

- 在 Pile 上做因果语言建模，训练 24 层约 1B 参数模型；对 k 层模型循环 \(24/k\) 次以匹配 24 层基线的有效深度。
- 评估四组下游任务：
  - 闭卷 QA：主要测记忆；
  - 开卷 QA：需要从上下文推理；
  - 数学应用题；
  - 推理原语：如变量赋值链解析。
- 提出 **% Gap** 指标衡量循环模型弥补 iso-param 与 iso-flop 基线差距的程度：
  - 公式含义：\(\%Gap = [Avg_G(k\otimes 24/k)-Avg_G(k\otimes 1)]/[Avg_G(24\otimes 1)-Avg_G(k\otimes 1)]\)；
  - 接近 0% 表示该任务更依赖参数；接近或超过 100% 表示深度/循环更关键。
- 使用 **困惑度-下游指标等值线图**：训练过程中绘制验证 log perplexity 与下游准确率，比较同等困惑度下不同架构的归纳偏置。

### 2.4 循环启发的正则化

- 若 24 层模型被划分为若干 k 层块，则鼓励相邻块中对应参数组的余弦相似度高。
- 对参数组 G，正则项为相邻 k 层块对应参数余弦相似度的平均：
  - \(R_G(k)=\frac{1}{L-k}\sum_i\sum_j \mathrm{Cosine}(\theta^{(ik+j)}_G,\theta^{((i+1)k+j)}_G)\)；
- 总损失：交叉熵损失 + \(\lambda_{reg}\) 加权的各参数组正则项平均。
- \(\lambda_{reg}=0\) 为普通训练；\(\lambda_{reg}\to\infty\) 趋近完全循环模型；中间值得到“近似循环”模型。
- 论文使用余弦相似度而非 \(\ell_2\)，因为更稳健有效。

### 2.5 理论分析

- **群组合问题**：1 层循环 Transformer 循环 \(\lceil\log_2 n\rceil\) 次可计算 n 个群元素的组合，深度接近已知最优。
- **模拟非循环模型**：若非循环模型只有 R 种不同层，则可用 1 层循环 Transformer 以少量维度/头数增加模拟其 L 层计算。
- **p-hop 问题**：1 层 Transformer 循环 \(\lfloor\log_2 p\rfloor+2\) 次可解，匹配非循环模型的下界。
- **模拟 CoT**：L 层非循环 Transformer 的 m 步 CoT，可由 L+O(1) 层循环 Transformer 在输入后接 m 个占位 token、循环 m 次来模拟。直观上，循环模型每轮可产生多个“潜在思维”，比每轮一个 token 的 CoT 更强。

## 3. 实验设计

### 3.1 数据集与场景

- **合成推理任务**：
  - n 元加法：训练 n∈{2,4,8,16,32}，评估 n∈{8,16,24,32}；
  - p-hop induction：字母表大小 4，序列长度 256，p∈{16,32}；
  - i-GSM：约 400 万训练样本、约 5 万测试样本，符号化数学题，模 7。
- **语言建模**：
  - Pile 数据集，250B tokens；
  - 24 层约 1B 参数 GPT 风格解码器；
  - 下游 19 个任务，分为闭卷 QA、开卷 QA、数学应用题、推理原语四组。
- **具体下游任务**：
  - 闭卷 QA：TriviaQA、TydiQA-NoContext、Natural Questions、Web Questions；
  - 开卷 QA：TydiQA-GoldP、SQuADv2、DROP、QuAC、CoQA；
  - 数学：ASDiv、MAWPS-AddSub/MultiArith/SingleEq/SingleOp、SVAMP；
  - 推理原语：depth-0/depth-1 的代码与数学变量赋值任务。

### 3.2 对比方法与实验设置

- 合成任务：
  - 基线 \((12\otimes1)\)、\((6\otimes1)\) 等；
  - 循环模型 \((k\otimes 12/k)\)，k∈{2,3,4,6}；
  - p-hop 中比较 1/2/3 层基线与循环版本；
  - i-GSM 中比较深度 1/2/4/8 及不同循环次数。
- 语言建模：
  - 24 层基线；
  - k∈{4,6,8,12} 的 iso-param 基线与 \((k\otimes24/k)\) 循环模型；
  - middle looping 变体；
  - 正则化模型，k∈{4,6,8,12}，\(\lambda_{reg}=1\) 或 10。
- 缩放实验：
  - 训练 \((4\otimes L)\)，L∈{1,2,3,6,9,12}；
  - 对比 iso-FLOP 的 \((4L\otimes1)\) 非循环模型；
  - 拟合 \(Acc=\alpha\log(D)+\beta\)，比较 \(\alpha_{loop}/\alpha_{base}\)。

## 4. 资源与算力

- 论文**未明确报告 GPU 型号、GPU 数量、总训练时长或总算力**。
- 可获得的训练配置信息：
  - 语言建模：Pile 250B tokens，
