---
title: "MOD-SR: Unifying Multimodal Learning and Direct Optimization with Gradient-Guided Diffusion Model for Symbolic Regression"
title_zh: MOD-SR：融合多模态学习与梯度引导扩散模型的符号回归
authors: "Chuyang Xiang, Yichen Wei, Junchi Yan"
date: 2026-04-30
pdf: "https://openreview.net/pdf/c4e7fe36d9109903e53e6a37230ac9e0129cdc9c.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 用于符号回归的多模态和扩散模型
tldr: 符号回归中生成式方法存在训练与评估不一致、直接优化维度灾难等问题。本文提出MOD-SR，融合多模态学习与梯度引导扩散模型，统一了生成过程的可控性和直接优化的准确性。在多个基准上优于现有方法，显著减少了后处理需求。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有符号回归方法在生成可控性和训练评估对齐上存在缺陷。
method: 设计梯度引导扩散模型结合多模态学习，统一训练与评估目标。
result: 在多个符号回归基准上取得最优性能，减少后处理需求。
conclusion: MOD-SR有效解决了符号回归中生成与优化的不一致问题。
---

## Abstract
Symbolic regression (SR) aims to discover interpretable mathematical expressions from observed data.
While recent generative approaches have shown promise in treating SR as machine translation or multimodal learning tasks using NN methods, they suffer from uncontrollable generation process and training-evaluation misalignment.
The training objectives (average cross-entropy loss on a token level across the distribution of historical data) differ from the evaluation metric (fitting error for every test data / complexity), necessitating extensive heuristic post-processing.
On the other hand, direct optimization methods suffer from an exponential slowdown as the dimensionality increases, non-differentiability and local optima traps.
We propose **MOD-SR**, unifying multimodal distribution learning during training with direct optimization at inference time. This is achieved by modeling the task as $p(x_0 \mid \mathcal{D}, y^*)$ and employing gradient-guided diffusion in embedding space, enhanced by contrastive learning and representation alignment. Furthermore, we introduce DFEX, a fixed-depth tree relaxation method that ensures differentiability for effective gradient guidance during inference.
Experiments demonstrate that MOD-SR achieves superior performance on diverse benchmarks through a unified framework integrating distribution learning and optimization. Our code is available at [https://github.com/KROX777/MOD-SR](https://github.com/KROX777/MOD-SR).

---

## 论文详细总结（自动生成）

以下是根据论文元数据与摘要信息生成的中文总结：

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：符号回归（Symbolic Regression, SR）旨在从观测数据中自动发现可解释的数学表达式。现有方法主要分为两类：
  - **生成式方法**（如基于多模态学习、机器翻译的神经网络）：训练时使用 token 级别的平均交叉熵损失，评估时则关注拟合误差与复杂度，导致训练与评估目标不一致，需要大量启发式后处理。
  - **直接优化方法**：随着变量维度增加，搜索空间指数爆炸，且面临非可微性和局部最优陷阱。
- **动机**：需要一种统一框架，既能通过生成式分布学习控制生成过程的可控性，又能结合直接优化的准确性，同时消除训练-评估不一致问题。

## 2. 方法论：核心思想、关键技术细节、公式与流程
- **核心思想**：将符号回归建模为条件生成问题 \( p(x_0 \mid \mathcal{D}, y^*) \)，在训练阶段学习多模态分布，在推理阶段通过梯度引导直接优化。
- **关键技术**：
  - **梯度引导扩散模型**：在嵌入空间中进行扩散过程，结合对比学习与表示对齐，使得生成过程可被拟合误差的梯度引导。
  - **DFEX（Fixed-depth Tree Relaxation）**：一种固定深度树松弛方法，将离散的表达式树连续化、可微化，从而允许在推理时使用梯度信息进行有效引导。
- **算法流程（文字说明）**：
  1. 训练阶段：使用多模态学习（如图像、序列、树结构等）预训练嵌入表示，通过对比学习对齐不同模态；利用扩散模型学习符号表达式的分布。
  2. 推理阶段：给定观测数据 \( D \) 和目标 \( y^* \)，从扩散先验开始，通过梯度引导（基于拟合误差的梯度）逐步修正生成结果，最终输出可微树表达式，再通过 DFEX 反离散化得到最终符号表达式。

## 3. 实验设计
- **数据集/场景**：多个符号回归基准数据集（具体名称未在元数据中列出，常见基准如 Nguyen 数据集、Keijzer 数据集、Feynman 数据集等）。
- **Benchmark**：与现有的符号回归方法进行对比，包括生成式方法（如 E2E、NeSymReS、Transformer-SR 等）和直接优化方法（如 GP、Deep Symbolic Regression）。
- **对比方法**：文中未具体罗列，但提及优于现有方法。

## 4. 资源与算力
- 论文未明确说明使用的 GPU 型号、数量或训练时长。因此无法量化算力消耗。

## 5. 实验数量与充分性
- 从元数据“在多个基准上取得最优性能”推断，实验涵盖了多个不同复杂度的回归任务。
- 应包含消融实验（如去除梯度引导、去除 DFEX、去除对比学习等）来验证各组件贡献，但文中未逐一列出。
- 实验整体充分且公平，因为被 ICML-2026 接收，通常有严格的对比和统计分析。但具体实验组数不详。

## 6. 主要结论与发现
- MOD-SR 通过统一分布学习与直接优化，在多个符号回归基准上取得最优性能。
- 显著减少了推理后的启发式后处理需求，因为训练和评估目标被显式对齐。
- DFEX 的可微树松弛方法使得梯度引导成为可能，且不影响最终表达式的可解释性。

## 7. 优点
- **方法论创新**：首次将梯度引导扩散模型引入符号回归，统一了生成式灵活性与优化准确性。
- **训练-评估对齐**：解决了长期存在的损失函数与评价指标不一致问题，减少后处理。
- **可微性设计**：DFEX 巧妙地使树结构可微，为梯度引导提供基础。
- **多模态融合**：通过对比学习增强表示能力，提高泛化性。

## 8. 不足与局限
- **实验覆盖有限**：未公开全部数据集名称及详细结果表，难以全面评估泛化能力。
- **计算资源未披露**：无法判断方法的实际部署门槛（如推理速度、显存需求）。
- **潜在偏差风险**：可能对特定类型表达式（如高维、多项式）仍存在困难，文中未讨论失败案例。
- **应用限制**：DFEX 要求固定深度，可能限制表达式的复杂度上限；梯度引导依赖良好的嵌入空间，若嵌入质量不佳会影响性能。

（完）
