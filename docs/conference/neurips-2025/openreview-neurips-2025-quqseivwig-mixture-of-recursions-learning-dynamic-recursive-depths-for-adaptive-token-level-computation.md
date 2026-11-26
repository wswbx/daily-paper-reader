---
title: "Mixture-of-Recursions: Learning Dynamic Recursive Depths for Adaptive Token-Level Computation"
title_zh: Mixture-of-Recursions：学习动态递归深度以实现自适应 token 级计算
authors: "Sangmin Bae, Yujin Kim, Reza Bayat, Sungnyun Kim, Jiyoun Ha, Tal Schuster, Adam Fisch, Hrayr Harutyunyan, Ziwei Ji, Aaron Courville, Se-Young Yun"
date: 2025-09-18
pdf: "https://papers.neurips.cc/paper_files/paper/2025/file/8b08bbf8b420faa6eeb4020720582ec7-Paper-Conference.pdf"
tags: ["query:looped-llm"]
score: 9.0
evidence: 递归Transformer在递归步骤间复用共享层堆栈
tldr: 扩展语言模型带来高昂的训练与部署开销，已有高效化工作或聚焦参数共享或聚焦自适应计算，难以兼得。作者提出Mixture-of-Recursions框架，在单一递归Transformer中复用共享层堆栈以实现参数效率，同时用轻量路由器为每个词元动态分配不同递归深度。实验表明该设计在保持性能的同时显著减少注意力与计算开销。其贡献在于把循环层复用与自适应计算统一到同一架构中。
source: NeurIPS-2025-Accepted
selection_source: topic_research
id: openreview-neurips-2025-quqseivwig
canonical_id: "work:0a0936d2d87e44b218ba112f"
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
official_pdf_url: "https://papers.neurips.cc/paper_files/paper/2025/file/8b08bbf8b420faa6eeb4020720582ec7-Paper-Conference.pdf"
official_link: "https://papers.neurips.cc/paper_files/paper/2025/hash/8b08bbf8b420faa6eeb4020720582ec7-Abstract-Conference.html"
conference_acceptance_status: accepted
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-quqseivwig/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 1741, \"height\": 1081}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-quqseivwig/fig-002.webp\", \"caption\": \"\", \"page\": 35, \"index\": 2, \"width\": 951, \"height\": 951}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-quqseivwig/fig-003.webp\", \"caption\": \"\", \"page\": 35, \"index\": 3, \"width\": 928, \"height\": 928}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-quqseivwig/fig-004.webp\", \"caption\": \"\", \"page\": 35, \"index\": 4, \"width\": 928, \"height\": 928}]"
motivation: 参数共享与自适应计算两类高效化手段此前难以在同一模型中同时实现。
method: 在递归Transformer中复用共享层堆栈，并用轻量路由器为词元分配不同递归深度。
result: 该框架在保持模型能力的同时降低注意力与计算开销，实现参数与计算双重高效。
conclusion: 将循环层复用与自适应计算统一，为递归式LLM架构提供可行范式。
---

## 摘要
扩展语言模型可释放出强大的能力，但随之而来的计算与内存需求使训练和部署都变得昂贵。现有的效率提升工作通常只针对参数共享或自适应计算之一，尚未解决如何同时实现二者的问题。我们提出 Mixture-of-Recursions（MoR），一个在单个 Recursive Transformer 内结合这两个效率维度的统一框架。MoR 在多个递归步骤间复用共享层堆栈以实现参数效率，而轻量级路由器通过为各个 token 动态分配不同的递归深度，实现自适应的 token 级思考。这使 MoR 能够仅在给定递归深度上仍处于活跃状态的 token 之间进行二次注意力计算，并通过仅选择性地缓存这些 token 的键值对来进一步提升内存访问效率。除这些核心机制外，我们还提出一种 KV 共享变体，复用第一次递归中的 KV 对，专门用于进一步降低内存占用。在 135M 到 1.7B 参数的一系列模型规模上，MoR 形成了新的帕累托前沿：在相同训练 FLOPs 和更小模型规模下，它显著降低验证困惑度并提升少样本准确率，同时相比普通模型和现有递归基线具有更高吞吐量。

## Abstract
Scaling language models unlocks impressive capabilities, but the accompanying computational and memory demands make both training and deployment expensive. Existing efficiency efforts typically target either parameter sharing or adaptive computation, leaving open the question of how to attain both simultaneously. We introduce Mixture-of-Recursions (MoR), a unified framework that combines the two axes of efficiency inside a single Recursive Transformer. MoR reuses a shared stack of layers across recursion steps to achieve parameter efficiency, while lightweight routers enable adaptive token-level thinking by dynamically assigning different recursion depths to individual tokens. This allows MoR to focus quadratic attention computation only among tokens still active at a given recursion depth, further improving memory access efficiency by selectively caching only their key-value pairs. Beyond these core mechanisms, we also propose a KV sharing variant that reuses KV pairs from the first recursion, specifically designed to further decrease memory footprint. Across model scales ranging from 135M to 1.7B parameters, MoR forms a new Pareto frontier: at equal training FLOPs and smaller model sizes, it significantly lowers validation perplexity and improves few-shot accuracy, while delivering higher throughput compared with vanilla and existing recursive baselines.

---

## 论文详细总结（自动生成）

# Mixture-of-Recursions（MoR）论文中文总结

## 1. 核心问题与整体含义

- **背景**：扩展语言模型（从数十亿到数千亿参数）带来强大的少样本泛化和推理能力，但训练与部署的计算和内存开销巨大，难以在超大规模数据中心之外使用。
- **现有高效化路线**：
  - **参数效率**：通过层绑定（layer tying）复用共享权重，如 Universal Transformer、Recursive Transformer。
  - **自适应计算**：通过早退（early-exiting）或路由机制，仅为“困难”token 分配更多计算。
- **核心问题**：此前工作通常只沿单一效率轴推进，**缺少一个能同时统一参数共享与自适应计算的架构**。递归 Transformer 虽自带权重共享，但现有动态递归方法往往需要额外的专用训练流程，或在高效部署上面临挑战，因此多数仍退回固定递归深度，无法实现真正的 token 级自适应计算。
- **论文含义**：提出 **Mixture-of-Recursions（MoR）**，在单个 Recursive Transformer 内同时实现：
  1. 跨递归步骤复用共享层堆栈（参数效率）；
  2. 轻量路由器为每个 token 动态分配递归深度（自适应计算）；
  3. 仅对当前递归深度活跃 token 做注意力并选择性缓存 KV（内存/IO 效率）。
- **定位**：MoR 被视为一种面向隐空间推理的预训练框架——在解码每个 token 时直接进行“非言语思考”，并沿模型纵向轴实现自适应推理深度。

## 2. 方法论

### 2.1 核心思想

- 将模型划分为 $N_r$ 个**递归块**，每个块复用同一组共享参数 $\Phi'$。
- 每个 token 根据路由器决策，决定通过递归块的次数（递归深度），从而实现 token 级自适应计算。
- 注意力仅在当前递归深度仍活跃的 token 之间计算，KV 缓存也仅针对这些 token 选择性存储。

### 2.2 参数共享策略

论文比较了四种策略，最终采用 **Middle-Cycle**：

- **Cycle**：递归块循环复用，如 $L=9, N_r=3$ 时展开为 $[(0,1,2),(0,1,2),(0,1,2)]$。
- **Sequence**：每个递归块连续复用同一层，如 $[(0,0,0),(1,1,1),(2,2,2)]$。
- **Middle-Cycle / Middle-Sequence**：保留第一层和最后一层的独立参数（$\Phi_0$、$\Phi_{L-1}$），仅对中间层共享权重。
- **结论**：Middle-Cycle 在 135M 和 360M 规模、$N_r=2$ 和 $3$ 下均取得最低验证 NLL 和最高平均少样本准确率，被选为所有 MoR 与 Recursive 基线的默认配置。

### 2.3 路由策略

论文提出并对比两种路由方式：

- **Expert-choice routing**（图 2a）：
  - 每个递归深度视为一个“专家”，在每个递归步骤 $r$ 用路由器计算 token 得分 $g_t^r = G(\theta_r^\top H_t^r)$。
  - 选择 top-k token 通过递归块：
    $$H_t^{r+1} = \begin{cases} g_t^r f(H_t^r, \Phi') + H_t^r, & \text{if } g_t^r > P_\beta(G^r) \\ H_t^r, & \text{otherwise} \end{cases}$$
  - 采用**层次过滤**：只有上一轮被选中的 token 才进入下一轮评估。
  - **优点**：静态计算预算、完美负载均衡；**缺点**：top-k 选择需要未来 token 信息，违反因果性，需辅助路由器或辅助损失缓解。
- **Token-choice routing**（图 2b）：
  - 每个 token 在初始阶段一次性选择完整递归路径（top-1 gating）：
    $$H_t^{r+1} = \begin{cases} g_t^r f(H_t^r, \Phi') + H_t^1, & \text{if } r = i \\ g_t^r f(H_t^r, \Phi'), & \text{otherwise} \end{cases}$$
  - **优点**：无信息泄漏；**缺点**：负载不均衡，需平衡损失或 loss-free 算法。
- **计算对齐**：为公平比较，将 expert-choice 的 top-k 容量校准为 token-choice 完美负载均衡下的期望分布（$N_r/N_r, \cdots, 1/N_r$）。

### 2.4 KV 缓存策略

- **Recursion-wise KV caching**（图 2c 上）：
  - 仅缓存当前递归步骤被选中 token 的 KV 对，注意力限制在这些局部缓存条目上。
  - 效果：KV 内存和 IO 降至约 $(N_r+1)/2N_r$，每层注意力 FLOPs 降至 $(k/N_{ctx})^2$。
- **Recursive KV sharing**（图 2c 下）：
  - 仅在第一次递归时缓存全部 token 的 KV 对，后续递归复用。
  - 效果：KV 内存降至 $1/N_r$，但注意力 FLOPs 仅降至 $k/N_{ctx}$，且 KV IO 仍较高。
- **设计取舍**：expert-choice 路由下递归式缓存更优；token-choice 路由下 KV 共享可弥补路由不精确带来的上下文缺失。

## 3. 实验设计

- **数据集**：FineWeb-Edu（SmolLM-Corpus 的去重子集，约 220B tokens）。
- **模型架构**：基于 Llama 的 Transformer，参考 SmolLM 配置，词表 49K，最大序列长度 2K。
- **模型规模**：135M、360M、730M、1.7B 参数。
- **评估 benchmark**：
  - 验证集负对数似然（NLL / 困惑度）；
  - 六个少样本任务：LAMBADA（LD）、HellaSwag（HS）、PIQA（PQ）、WinoGrande（WG）、ARC（Easy + Challenge）、MMLU。
- **对比方法**：
  - **Vanilla Transformer**（全容量、无共享）；
  - **Recursive Transformer**（固定递归深度，Middle-Cycle 共享）；
  - **MoR 变体**：expert-choice vs. token-choice、recursion-wise caching vs. recursive KV sharing。
- **实验设置**：
  - **等 FLOPs 实验**：16.5e18 FLOPs 下对比不同模型；
  - **等 token 实验**：固定 20B 训练 token，比较实际消耗 FLOPs；
  - **IsoFLOP 分析**：四个规模 × 三个 FLOPs 预算（2e18、5e18、16.5e18）；
  - **推理吞吐评估**：360M 模型，递归深度 2/3/4，固定 batch=32 与最大 batch 两种设置；
  - **消融实验**：参数共享策略、路由设计（辅助损失/辅助路由器、激活函数、路由器架构、z-loss）、KV 缓存策略。

## 4. 资源与算力

- 论文明确提到：
  - 预训练使用 **4 块 H100 或 A100 GPU**；
  - 评估使用 **单块 H100 或 A100 GPU**；
  - 感谢 Google Cloud Platform 提供云积分，以及 Mila、Calcul Québec、Digital Research Alliance of Canada 提供的计算资源。
- **未明确说明**：总训练时长、总 GPU 小时数、各实验的具体能耗。
- 训练采用 **Trapezoid 学习率调度**（约 5% warmup、稳定阶段、20% cooldown），并通过中间 checkpoint 复用减少重复训练。

## 5. 实验数量与充分性

- **实验规模**：
  - 主实验：4 个模型规模 × 3 个 FLOPs 预算的 IsoFLOP 分析（表 9）；
  - 等 FLOPs / 等 token 对比（表 3）；
  - 1.7B 规模扩展验证（表 7）；
  - 固定参数下增加递归深度（表 8）；
  - 参数共享策略消融：4 种策略 × 2 个规模 × 2 个递归深度（表 10）；
  - 路由策略消融：expert-choice 约 14 组配置、token-choice 约 12 组配置（表 13、14）；
  - KV 缓存策略消融：Vanilla / Recursive / MoR 多组对比（表 15、16）；
  - 吞吐量实验：多种递归深度与 batch 设置（图 4a）；
  - 路由分析与测试时缩放分析（图 5）。
- **充分性评价**：
  - 覆盖了从 135M 到 1.7B 的多个规模，消融维度较全面（共享策略、路由、缓存、训练稳定性）。
  - 对比基线包括 Vanilla 和 Recursive，且进行了 FLOPs 对齐，公平性较好。
  - **不足**：
    - 未报告误差棒或统计显著性（作者解释为固定数据顺序、随机性小）；
    - 最大规模仅到 1.7B，未验证 3B 以上；
    - 1.7B 规模下 Vanilla 略优于 MoR（表 7），作者承认可能需要更多验证；
    - 吞吐量测量排除了 KV 缓存更新时间，实际部署性能可能被高估。

## 6. 主要结论与发现

- **等 FLOPs 下 MoR 更优**：在 16.5e18 FLOPs 预算下，MoR（expert-choice，$N_r=2$）验证 NLL 为 2.7511，优于 Vanilla 的 2.7824；平均少样本准确率 43.1% vs. 42.3%，且参数少约 50%。
- **等 token 下 MoR 更省算力**：固定 20B token，MoR-$N_r=2$ 使用约 12.3e18 FLOPs（比 Vanilla 少 25%），仍取得更低 NLL 和更高准确率；训练时间减少 19%，峰值内存减少 25%。
- **IsoFLOP 可扩展性**：在 360M 及以上规模，MoR 匹配或超越 Vanilla；135M 规模因递归容量瓶颈略逊，但差距随规模缩小。
- **推理吞吐提升**：结合连续深度批处理，MoR-4 在最大 batch 设置下实现最高 **2.06×** 加速；递归深度越大，早退 token 越多，KV 缓存越小，吞吐越高。
- **Middle-Cycle 是最佳共享策略**：在多数设置下取得最低 NLL 和最高准确率。
- **Expert-choice + 辅助损失 + 线性路由器**表现最佳；token-choice 需平衡损失才能稳定。
- **KV 共享的取舍**：递归式缓存在 expert-choice 下性能更好；KV 共享在 token-choice 下可弥补路由不精确，但 expert-choice 下性能下降明显。
- **路由可解释性**：递归深度反映 token 的可预测性——简单子词（如词缀）早退，功能词的闭合部分或复杂 token 需要更深递归。
- **测试时缩放**：增加推理时的递归深度可提升 log-likelihood，表明 MoR 支持“思考更久”的测试时缩放。

## 7. 优点

- **统一框架**：首次在同一架构中同时实现参数共享、token 级自适应深度和内存高效 KV 缓存。
- **端到端训练路由器**：无需后处理阶段，避免传统早退方法因分离训练导致的性能退化。
- **递归式 KV 缓存**：仅缓存活跃 token 的 KV 对，同时降低注意力 FLOPs 和内存 IO，且与连续深度批处理天然兼容。
- **实验设计较严谨**：
  -
