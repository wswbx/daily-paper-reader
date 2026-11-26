---
title: "Relaxed Recursive Transformers: Effective Parameter Sharing with Layer-wise LoRA"
title_zh: 松弛递归 Transformer：使用逐层 LoRA 的有效参数共享
authors: "Sangmin Bae, Adam Fisch, Hrayr Harutyunyan, Ziwei Ji, Seungyeon Kim, Tal Schuster"
date: 2025-01-22
pdf: "https://proceedings.iclr.cc/paper_files/paper/2025/file/54d6a55225cebbdc16fbb0e45c5bdf2b-Paper-Conference.pdf"
tags: ["query:looped-llm"]
score: 9.0
evidence: 将大模型转为单层块循环重复、参数共享的递归Transformer
tldr: 大语言模型部署成本高昂，而现有层绑定式参数共享在现代大模型上效果有限。作者重新审视层绑定，提出把标准预训练Transformer高效初始化为递归Transformer：只保留一个唯一的层块并循环重复多次，同时引入逐层LoRA构成松弛递归Transformer以恢复表达灵活性。实验表明该方法在几乎不损失性能的前提下显著压缩模型规模。其贡献在于为大模型提供了可落地的循环层复用压缩路径。
source: ICLR-2025-Accepted
selection_source: topic_research
id: openreview-iclr-2025-wwpysokkct
canonical_id: "work:7a4f3d884d76f774c056a2d4"
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
official_pdf_url: "https://proceedings.iclr.cc/paper_files/paper/2025/file/54d6a55225cebbdc16fbb0e45c5bdf2b-Paper-Conference.pdf"
official_link: "https://proceedings.iclr.cc/paper_files/paper/2025/hash/54d6a55225cebbdc16fbb0e45c5bdf2b-Abstract-Conference.html"
conference_acceptance_status: accepted
motivation: 现代大语言模型部署成本高，而层绑定式参数共享在实际大模型上效果有限。
method: 从预训练Transformer初始化递归Transformer，循环重复单个层块，并用逐层LoRA增强灵活性。
result: 在几乎不损失性能的情况下把大模型转换为层循环共享的小模型。
conclusion: 为循环层复用与参数共享提供了可实际部署的大模型压缩方案。
---

## 摘要
大型语言模型（LLM）的部署成本高昂。参数共享为减小其规模和成本提供了一条可能路径，但其在现代 LLM 中的有效性仍相当有限。在这项工作中，我们重新审视 Transformer 中作为参数共享形式的“层绑定”（layer tying），并引入新方法，将现有 LLM 转换为在层间共享参数的更小“递归 Transformer”，且性能损失最小。我们的递归 Transformer 从标准预训练 Transformer 高效初始化，但仅使用一个由独特层组成的块，然后在循环中重复多次。我们进一步通过深度方向低秩适配（LoRA）模块为层绑定约束增加灵活性，提出松弛递归 Transformer 以提升性能，同时仍保持整体模型的紧凑性。我们表明，我们的递归模型（例如递归 Gemma 1B）优于同等规模的原始预训练模型（如 TinyLlama 1.1B 和 Pythia 1B）以及知识蒸馏基线——甚至能够恢复原始“全尺寸”模型（例如无共享参数的 Gemma 2B）的大部分性能。最后，我们提出连续深度批处理（Continuous Depth-wise Batching），这是一种有前景的新推理范式，当递归 Transformer 与提前退出（early exiting）结合时即可启用。在理论分析中，我们表明这有可能带来推理吞吐量的显著提升（2-3 倍）。

## Abstract
Large language models (LLMs) are expensive to deploy. Parameter sharing offers a possible path towards reducing their size and cost, but its effectiveness in modern LLMs remains fairly limited. In this work, we revisit "layer tying" as form of parameter sharing in Transformers, and introduce novel methods for converting existing LLMs into smaller "Recursive Transformers" that share parameters across layers, with minimal loss of performance. Here, our Recursive Transformers are efficiently initialized from standard pretrained Transformers, but only use a single block of unique layers that is then repeated multiple times in a loop. We further improve  performance by introducing Relaxed Recursive Transformers that add flexibility to the layer tying constraint via depth-wise low-rank adaptation (LoRA) modules, yet still preserve the compactness of the overall model. We show that our recursive models (e.g., recursive Gemma 1B) outperform both similar-sized vanilla pretrained models (such as TinyLlama 1.1B and Pythia 1B) and knowledge distillation baselines---and can even recover most of the performance of the original "full-size" model (e.g., Gemma 2B with no shared parameters). Finally, we propose Continuous Depth-wise Batching, a promising new inference paradigm enabled by the Recursive Transformer when paired with early exiting. In a theoretical analysis, we show  that this has the potential to lead to significant (2-3$\times$) gains in inference throughput.

---

## 论文详细总结（自动生成）

# 论文总结：Relaxed Recursive Transformers: Effective Parameter Sharing with Layer-wise LoRA

## 1. 核心问题与整体含义

- **研究动机**：大语言模型（LLM）部署成本高，参数规模带来巨大内存与计算开销。参数共享/层绑定（layer tying）理论上可减少模型存储和部署成本，但在现代 LLM 上的效果此前并不理想。
- **核心问题**：能否将已有的标准预训练 Transformer 高效转换为更小的“递归 Transformer”，即只保留一个唯一的层块并循环复用多次，同时尽量不损失性能？
- **整体含义**：论文重新审视层绑定式参数共享，提出从预训练模型初始化递归结构，并通过逐层 LoRA 松弛严格权重绑定。该方法不主要减少前向层数/FLOPs，而是显著减少唯一参数存储，从而利于更大批量、早退出和新推理调度；最终为 LLM 压缩与高效服务提供一条可落地路径。

## 2. 方法论

### 2.1 Recursive Transformer：循环层绑定

- **核心思想**：采用 CYCLE 参数共享策略，将原本 L 层的 Transformer 压缩为 B 个循环块，每个块包含 K 个唯一层，整个模型只存储这 K 层，然后循环 N/K 次。
- **计算形式**：第 ℓ 层隐藏状态为  
  `hℓ_t = f(hℓ−1_t; Φ′_{((ℓ−1) mod L/B)+1})`，其中 `B` 是循环块数且为 `L` 的因子。
- **参数绑定范围**：绑定 Transformer 块内线性层权重以及 RMSNorm 权重。
- **初始化策略**：为减少容量下降带来的性能损失，论文提出三种从原全尺寸模型迁移权重的初始化方法：
  - **Stepwise**：固定首层和末层，按固定间隔选择中间层，通常对纯 Recursive Transformer 最优。
  - **Average**：对将被绑定的层权重取平均，通常对 Relaxed Recursive Transformer 最优。
  - **Lower**：直接使用原模型前 K 层权重。
- **示例**：Gemma 2B 有 18 层，可转换为 2 个循环块，只存前 9 层权重，前向传播循环两次。

### 2.2 Relaxed Recursive Transformer：逐层 LoRA 松弛

- **动机**：严格层绑定限制模型容量，且每层需服务多个深度角色。论文在共享层上为每个循环迭代添加独立的低秩适配（LoRA）模块，形成“松弛递归 Transformer”。
- **计算形式**：  
  `hℓ_t = f(hℓ−1_t; Φ′_{((ℓ−1) mod L/B)+1}, ΔΦ′_ℓ)`，  
  对共享线性变换 `h = W′x`，加入 LoRA 后为 `h = W′x + BAx`。
- **LoRA 组织方式**：每个共享层可挂多个 LoRA 模块；第一次循环使用第一个 LoRA，第二次循环使用第二个 LoRA，以此类推。
- **SVD 初始化**：不同于标准 LoRA 零初始化，论文对原层权重与共享层权重的残差矩阵做截断 SVD：  
  `Uℓ_r, Σℓ_r, Vℓ_r = TruncatedSVD(Wℓ − W′_{((ℓ−1) mod L/B)+1}; r)`，  
  令 `B = U_r Σ_r`，`A = V_r^T`，从而用低秩项近似原始全尺寸权重。
- **秩的作用**：秩 `r=0` 时退化为纯 Recursive Transformer；秩增大时逐渐逼近原始全尺寸模型，形成模型大小与性能之间的可调插值。若初始化层与原层完全一致，则对应 LoRA 采用标准零初始化。

### 2.3 Continuous Depth-wise Batching 与早退出

- **连续深度批处理**：传统连续序列批处理利用不同请求共享同一模型参数；递归 Transformer 还因不同循环深度共享层函数，可让不同样本在不同循环迭代上同批计算。新请求可在其他样本尚未完成全部循环时立即填入批次槽位。
- **与早退出结合**：部分高置信样本可在较早循环退出，空出的批次槽位立即调度新请求，缓解早退出在批量服务中的同步等待问题。
- **理论收益**：论文通过 oracle-exiting 模拟估计吞吐提升，声称可达 2–3×，甚至递归 Gemma 相对 vanilla Pythia 有接近 4× 的吞吐优势。注意这是理论/模拟分析，不是完整实际部署测量。

## 3. 实验设计

### 3.1 模型与数据

- **基础模型**：
  - Gemma 2B（18 层，预训练 3T tokens，数据未公开）
  - TinyLlama 1.1B（22 层，SlimPajama + Starcoderdata，约 105B 中间 checkpoint）
  - Pythia 1B（16 层，Pile，300B tokens）
- **转换设置**：主要转换为 2 个循环块，也测试 3 个循环块。
- **Uptraining 数据**：SlimPajama，主要使用 15B tokens；最终配置扩展到 60B tokens。
- **知识蒸馏**：教师为对应全尺寸模型（Gemma/Pythia 为在 SlimPajama 上继续 uptrain 的 full-size 模型），比较 forward KL、reverse KL、JSD、TVD，最终选 forward KL。
- **早退出训练**：在 uptrained 模型上继续训练 15B tokens，使用 aggressive coefficient 策略并对最终输出做自蒸馏。
- **额外小模型实验**：Pythia 410M 与 160M，在 Pile 上 uptrain，用于验证初始化方法。

### 3.2 评估 Benchmark

- **困惑度**：SlimPajama、RedPajama、PG19 测试集。
- **Few-shot 准确率**：LAMBADA、HellaSwag、PIQA、WinoGrande、ARC-easy、ARC-challenge、OpenBookQA，共 7 个任务，取平均。
- **吞吐模拟**：在 SlimPajama、RedPajama、PG19 上模拟生成，使用 oracle-exiting 轨迹和单 token 生成时间估计吞吐。

### 3.3 对比方法

- **Full-size 模型**：原始预训练模型；对 Gemma/Pythia 还使用同
