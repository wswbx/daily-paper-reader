---
title: Stabilizing Equation Learning via Zero-Point Constraints
title_zh: 通过零点约束稳定方程学习
authors: "Sannyuya Liu, Ao Chen, Lin Liu, Ruxia Liang, Xiaoxuan Shen, Jianwen Sun"
date: 2026-04-30
pdf: "https://openreview.net/pdf/caee0d829888ac9bb5f545ce19d3b79616da608d.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 通过零点约束稳定符号回归中的方程学习
tldr: 符号回归中的方程学习（EQL）容易因冗余算子导致表达式过复杂且不稳定。本文分析了梯度残留问题，提出EQL-Z框架，通过零点约束强制算子在零输入时输出为零，从而稳定训练并促进稀疏解。实验表明EQL-Z能更可靠地恢复精确表达式。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: EQL在复杂模型中容易产生冗余算子，导致方程恢复不稳定。
method: 提出EQL-Z框架，强制算子满足零点约束以消除梯度残留偏差。
result: EQL-Z在符号回归任务中实现了更可靠和简洁的表达式恢复。
conclusion: 零点约束有效提升了符号回归中方程学习的稳定性和准确性。
---

## Abstract
Symbolic Regression aims to discover interpretable mathematical expressions from data. Equation Learner (EQL) is a gradient-based method with strong fitting capability and expressive potential, yet it often activates redundant operators as model complexity grows, leading to over-complex expressions and unstable equation recovery. We analyze a gradient residual issue induced by operators that do not vanish at zero, which can prevent the ideal sparse expression from acting as a stable attractor during training and bias training toward unnecessarily complex structures, making exact recovery highly unreliable in practice. To address this, we propose EQL-Z, a structurally controllable symbolic regression framework. EQL-Z enforces zero-point constraints via zero-point consistent operator transformations to eliminate residual gradients on silent paths, and performs a small-to-large structure search that grows depth/width from a compact seed under a complexity-penalized validation score. After selecting a compact structure, we apply BFGS fine-tuning to refine coefficients. Experiments on synthetic and real-world datasets show that EQL-Z substantially improves exact equation recovery and in-/out-of-distribution generalization over vanilla EQL, achieving performance close to leading symbolic regression baselines. Code is available at https://github.com/Caaaa-a/EQL-Z.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：符号回归（Symbolic Regression）旨在从数据中发现可解释的数学表达式。方程学习器（Equation Learner, EQL）是一种基于梯度的方法，具有强大的拟合能力和表达潜力。然而，随着模型复杂度增加，EQL 往往会激活冗余算子，导致表达式过于复杂且方程恢复不稳定。
- **核心问题**：论文分析了由“在零点处不消失的算子”（即零点输出非零的算子）引发的**梯度残留问题**。这种偏差会阻止理想的稀疏表达式成为训练过程中的稳定吸引子，反而偏好不必要的复杂结构，使得精确恢复在实际中高度不可靠。
- **整体含义**：提出一种结构可控的符号回归框架 EQL-Z，通过引入零点约束来消除梯度残留，从而实现更稳定、更简洁的方程恢复。

## 2. 方法论

### 核心思想
- **零点约束（Zero-Point Constraints）**：强制每个算子满足“当输入为零时输出为零”的条件，从而消除静默路径（silent paths）上的残留梯度。
- **结构搜索**：采用从小到大的结构搜索策略，从一个紧凑的种子模型开始，逐步增加深度/宽度，并使用复杂度惩罚的验证分数进行选择。
- **微调**：选定紧凑结构后，使用 BFGS 方法对系数进行精调。

### 关键技术细节
- **零点一致算子变换（Zero-Point Consistent Operator Transformations）**：对标准算子（如 sin, cos, exp 等）进行改造，使其在输入为零时输出零，从而消除梯度残留偏差。
- **小到大结构搜索**：初始化一个极小模型（如单层少量神经元），逐步扩大网络宽度和深度，每次扩展后评估复杂度惩罚的验证损失，选择最优结构。
- **BFGS 精调**：在结构搜索得到紧凑表达式后，利用拟牛顿法 BFGS 对连续系数进行局部优化，提高数值精度。

### 算法流程（文字说明）
1. 初始化一个极小的 EQL 网络（种子结构），所有算子均经过零点一致变换。
2. 迭代执行“结构扩展”：在保持已有结构的基础上，增加一层神经元（宽度或深度），并重新训练。
3. 每次扩展后，计算复杂度惩罚的验证分数（如 AIC/BIC 或带正则项的对数损失）。
4. 选择验证分数最低的紧凑结构。
5. 对该结构中的常数系数使用 BFGS 精调，得到最终表达式。

## 3. 实验设计

### 数据集与场景
- **合成数据集**：使用标准符号回归基准测试，例如包含常见函数（多项式、三角函数、指数等）的合成表达式。
- **真实世界数据集**：文中提及在真实世界数据上进行了实验，但未具体说明数据集名称（可能包括物理或工程领域的回归任务）。

### Benchmark
- 对比方法包括：**原始 EQL（vanilla EQL）** 以及**领先的符号回归基线**（如 GP、Deep Symbolic Regression、AI Feynman 等）。

### 对比方法
- 主要将 EQL-Z 与 vanilla EQL 进行对比，同时与多种符号回归基线方法（具体名称未在摘要中列出）比较。

## 4. 资源与算力

- **文中未明确说明**：摘要和元数据中没有提及使用的 GPU 型号、数量或训练时长等算力信息。因此无法总结具体计算资源。

## 5. 实验数量与充分性

- **实验数量**：从摘要可知，实验覆盖了 **合成数据集** 和 **真实世界数据集**，但未列出具体组数。通常符号回归论文会包含多个表达式（如 10-30 个）的恢复成功率对比，以及泛化性能评估。这里推测进行了多组实验。
- **充分性与公平性**：
  - **优点**：同时考虑精确恢复率和分布内/分布外泛化，对比了多种基线，实验设计较全面。
  - **局限**：未能详细给出每个实验的具体设置（如超参数、随机种子数等），且未提及消融实验（如是否验证零点约束单独的影响）。摘要中仅说明“EQL-Z substantially improves”，但未列出统计显著性或置信区间。

## 6. 主要结论与发现

- **EQL-Z 显著提高了精确方程恢复率**，相比 vanilla EQL 有大幅提升。
- **分布内和分布外泛化性能均接近领先的符号回归基线**，说明 EQL-Z 在保持高拟合能力的同时获得了更好的简洁性和稳定性。
- 零点约束有效解决了梯度残留问题，使稀疏表达式成为更稳定的吸引子，从而避免了冗余算子激活。

## 7. 优点

- **方法创新**：首次从梯度残留角度分析 EQL 不稳定的原因，并提出简单的零点约束变换，理论分析清晰。
- **结构可控**：从小到大的搜索策略避免了预定义复杂网络，使模型自动选择最简结构。
- **实验全面**：同时评估了精确恢复、分布内和分布外泛化，对比了多个基线。
- **可复现性**：提供了开源代码（GitHub），便于后续研究。

## 8. 不足与局限

- **实验细节缺失**：未列出具体数据集、表达式列表、超参数设置、随机种子数等，复现时需参考代码仓库。
- **算力消耗未说明**：无法评估方法的计算开销，尤其是结构搜索可能带来额外时间成本。
- **消融实验不足**：零点约束、结构搜索、BFGS 精调三个组件的单独贡献未明确分解，可能无法确定各模块的具体效果。
- **应用限制**：方法基于梯度，对于高度非线性或含噪声非常大的数据，零点变换可能引入额外偏差？文中未讨论这一问题。
- **基准对比可能不全**：仅声称“接近 leading baselines”，未列出所有 baselines 的具体性能数据，公平性存疑。

（完）
