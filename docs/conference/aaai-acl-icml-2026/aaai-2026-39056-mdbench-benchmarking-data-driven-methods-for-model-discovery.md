---
title: "MDBench: Benchmarking Data-Driven Methods for Model Discovery"
title_zh: MDBench：模型发现数据驱动方法基准
authors: "Amirmohammad Ziaei Bideh, Aleksandra Georgievska, Jonathan Gryak"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39056/43018"
tags: ["query:sr"]
score: 9.0
evidence: 包含符号回归的模型发现方法基准
tldr: 模型发现领域缺乏统一基准，本文提出MDBench，评估12种算法在14个PDE和63个ODE上的表现，涵盖符号回归等方法，评价指标包括导数预测精度和模型复杂度，为比较符号回归方法提供了标准化平台。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有基准多关注单一方程，缺乏对动力学系统模型发现的全面评估。
method: 构建包含多种微分方程和噪声水平的基准，评估12种算法。
result: 揭示了不同方法在噪声下的性能权衡。
conclusion: MDBench为模型发现方法选择提供参考。
---

## Abstract
Model discovery aims to uncover governing differential equations of dynamical systems directly from experimental data. Benchmarking such methods is essential for tracking progress and understanding trade-offs in the field. While prior efforts have focused mostly on identifying single equations, typically framed as symbolic regression, there remains a lack of comprehensive benchmarks for discovering dynamical models. To address this, we introduce MDBench, an open-source benchmarking framework for evaluating model discovery methods on dynamical systems. MDBench assesses 12 algorithms on 14 partial differential equations (PDEs) and 63 ordinary differential equations (ODEs) under varying levels of noise. Evaluation metrics include derivative prediction accuracy, model complexity, and equation fidelity. We also introduce seven challenging PDE systems from fluid dynamics and thermodynamics, revealing key limitations in current methods. Our findings illustrate that linear methods and genetic programming methods achieve the lowest prediction error for PDEs and ODEs, respectively. Moreover, linear models are in general more robust against noise. MDBench accelerates the advancement of model discovery methods by offering a rigorous, extensible benchmarking framework and a rich, diverse collection of dynamical system datasets, enabling systematic evaluation, comparison, and improvement of equation accuracy and robustness.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：数据驱动的模型发现旨在从实验数据中直接揭示动力系统的控制微分方程，但该领域缺乏统一、标准化的基准来评估不同算法在**动力学系统**（ODE 和 PDE）上的表现。现有基准大多关注单一方程（符号回归）或仅评估黑箱预测模型，忽视了可解释性、方程结构恢复以及噪声鲁棒性等重要维度。
- **整体含义**：MDBench 填补了这一空白，通过构建涵盖多种微分方程类型、噪声水平、算法类别的综合性基准，为模型发现方法的公平比较、进展追踪和算法改进提供了基础平台。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：构建一个可扩展的、标准化的基准框架，统一数据格式、噪声模拟、超参数调优和评估流程，系统评估模型发现方法在 ODE 和 PDE 上的预测精度、方程复杂度和保真度。
- **关键技术细节**：
  - **数据预处理**：对 PDE 系统，使用二阶精度有限差分（通过 `findiff` 库）计算状态变量及其空间导数（最高四阶），构建符号特征库 $\{u_1, u_2, ..., u_d\} \cup \{ \partial^j u_i / \partial x_k^j \}$。
  - **噪声模拟**：采用乘性高斯噪声，信噪比（SNR）分别为 40 dB、30 dB、20 dB、10 dB，噪声施加在状态变量上，导数通过有限差分从噪声数据计算。
  - **超参数调优**：对于每个方法-数据集组合，遍历预定义网格，使用复合适应度函数 $s = 1/(1+NMSE) + \phi \exp(-\ell(f)/L)$ 选择最佳配置（$\phi=1, L=200$），平衡精度和复杂度。
  - **训练与评估**：时间维度上 60% 训练、20% 验证、20% 测试；选定超参数后合并训练+验证集重新训练，在测试集上评估。
  - **评价指标**：
    - NMSE（归一化均方误差）：衡量预测时间导数的精度。
    - 复杂度（Complexity）：符号表达式树的节点、常数和操作总数（使用 SymPy 解析）。
  - **扩展泛型方法到 PDE**：为将原用于标准监督学习的方法（如 GP、DL）应用于 PDE，预处理阶段计算空间导数作为输入特征，目标为时间导数。

## 3. 实验设计
- **数据集**：
  - ODE：63 个系统（源自 ODEBench，来自 Strogatz 教材和 Wikipedia），1~4 个状态变量。
  - PDE：14 个系统，包括已有常用系统（Advection, Burgers, KdV, KS, NLS, Reaction-Diffusion, Advection-Diffusion）以及 **7 个新挑战性系统**（Heat (Laser), Heat (Solar) 1D/2D/3D, Navier-Stokes (Channel), Navier-Stokes (Cylinder), Reaction-Diffusion (Cylinder)），涉及空间依赖强迫函数、六状态变量等特点。
- **基准对比**：对比了现有基准如 SRBench、PDEBench、Gilpin 2021 等，指出其局限性。
- **对比方法**（12 种，分为四类）：
  - **线性模型（LM）**：PDEFIND, SINDy, WSINDy, ESINDy/EWSINDy, Bayesian, DeepMoD
  - **遗传编程（GP）**：PySR, Operon
  - **深度学习（DL）**：EQL, uDSR
  - **大规模预训练（LSPT）**：ODEFormer, End2end
- **噪声设置**：5 种噪声水平（clean, 40, 30, 20, 10 dB），每个方法-数据集-噪声组合重复实验。

## 4. 资源与算力
- **计算平台**：Ubuntu 22.04.3 服务器，24 核 Intel Core Ultra 9 285K @ 1.44 GHz CPU，96 GB RAM。
- **GPU**：对于需要 GPU 的方法（EQL, uDSR, ODEFormer, End2end, DeepMoD），使用单块 NVIDIA RTX 4000 Ada Generation GPU（20 GB 显存）。
- **时间限制**：每个实验（含训练和超参数调优）限定 **12 小时**。文中明确给出了各方法的平均运行时（Table 3 中 last row: 26±53 min 等），具体数据在补充材料中。
- **说明**：算力资源相对有限（单GPU，CPU主频低），但 12 小时超时机制保证了公平性。

## 5. 实验数量与充分性
- **实验数量**：共 63（ODE）× 12（方法）× 5（噪声水平） + 14（PDE）× 12（方法）× 5（噪声水平）≈ 约 4620 个主要实验（部分方法因失败或超时未完成）。补充材料还有超参数调优实验和消融（如不同的复杂度权重）。
- **充分性**：
  - 数据集覆盖广泛（从简单线性到复杂湍流），多样性高。
  - 噪声水平多样，且使用乘性噪声更贴近实际。
  - 超参数调优采用同一协议，提升了公平性。
  - 统计检验（Wilcoxon signed-rank）用于判断方法间显著差异。
- **客观性**：所有实验均公开代码和数据集，结果可复现。但部分方法因代码问题未能在所有 PDE 上运行，可能引入选择偏差（仅在成功运行的数据集上比较）。

## 6. 论文的主要结论与发现
1. **ODE 结果**：
   - 低噪声下，GP 方法（PySR）NMSE 显著低于线性方法。
   - 高噪声下，线性模型（SINDy, ESINDy）鲁棒性更强，方程更简洁。
   - ODEFormer 在低噪声下精度高但对噪声敏感；End2end 误差最高。
   - 随状态变量维度增加，大多数方法训练时间增长，SINDy 和 Operon 计算效率最高。
2. **PDE 结果**：
   - 线性方法（WSINDy, PDEFIND）在低噪声下 NMSE 低于 GP 方法。
   - PDE 系统相比 ODE 对噪声更敏感（log(noise/clean) 误差比为 3.13±2.09 vs 0.88±2.12）。
   - 高维数据（Heat Solar 3D）导致所有方法性能下降，线性方法因函数库膨胀显著变慢，GP 方法扩展相对更好。
   - 新挑战性系统（Heat Laser, RD Cylinder）成功率极低，揭示现有方法无法处理空间依赖或分段强迫函数。
3. **一般性结论**：
   - 没有任何单一方法在所有场景下最优，方法选择需根据噪声水平、系统维度、可解释性需求权衡。
   - 线性方法更适合 PDE 和高噪声场景，GP 方法在低噪声 ODE 上有优势。

## 7. 优点
- **全面性**：首次在单个基准中同时覆盖 ODE 和 PDE 系统，方法类别涵盖 GP、LM、DL、LSPT，共 12 种算法。
- **标准化**：统一的数据处理、噪声添加、超参数调优、评价指标和训练协议，提高公平性和可重复性。
- **新增挑战性数据**：引入 7 个真实物理 PDE 系统（包含空间依赖强迫、多变量），推动方法向实际应用迈进。
- **开源可扩展**：代码和数据集公开，鼓励社区贡献新方法和新数据集。
- **统计严谨**：使用 Wilcoxon 符号秩检验支持结论，非仅报告平均值。

## 8. 不足与局限
- **实验覆盖偏差**：部分方法（End2end, DeepMoD, EQL）因实现限制或超时未能完成所有 PDE 实验，导致比较的完整性受损。
- **假设与简化**：现有算法普遍假设均匀物理参数（如扩散系数不随空间变化），无法处理 Heat Laser、RD Cylinder 等异质性系统。
- **高维可扩展性**：对所有方法，随状态变量或空间维度增加，误差和运行时间显著上升，尤其线性方法面临函数库组合爆炸。
- **噪声敏感性**：基于有限差分的导数估计在高噪声下误差放大严重，缺少鲁棒的降噪或弱形式整合。
- **保真度度量缺失**：NMSE 和复杂度无法准确反映方程的结构正确性；例如 GP 方法在 NS Channel 上 NMSE 虽低但未恢复真方程。论文提出需要 Sobolev 半范数等更好的度量。
- **计算资源限制**：仅使用单 GPU 和有限 CPU，未评估大规模并行或分布式训练的影响。
- **方法选择**：未包含最新基于 LLM 的符号回归方法（如 LLM-SR），可能未涵盖最前沿。

（完）
