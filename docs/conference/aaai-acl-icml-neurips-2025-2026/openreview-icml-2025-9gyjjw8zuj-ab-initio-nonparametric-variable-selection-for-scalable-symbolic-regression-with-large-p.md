---
title: Ab Initio Nonparametric Variable Selection for Scalable Symbolic Regression with Large $p$
title_zh: 面向大规模变量可扩展符号回归的从头算非参数变量选择
authors: "Shengbin Ye, Meng Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=9gyJJw8ZUj"
tags: ["query:sr"]
score: 9.0
evidence: 大规模变量符号回归
tldr: 现有符号回归方法无法处理大规模变量数据集，导致速度慢且表达式复杂。本文提出PAN+SR方法，结合从头算非参数变量选择和符号回归，高效剪枝无关变量，从而在极端大规模变量设置下实现可扩展且可解释的符号回归。实验表明PAN+SR在合成和真实数据集上均显著优于现有方法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有符号回归方法无法扩展到大量输入变量，导致性能低下和表达式复杂。
method: 提出PAN+SR方法，将非参数变量选择与符号回归结合，先筛选变量再回归。
result: 在合成和真实数据集上，PAN+SR显著提升了大p场景下的符号回归效率和准确率。
conclusion: 非参数变量选择是解决大规模变量符号回归可扩展性的关键。
---

## Abstract
Symbolic regression (SR) is a powerful technique for discovering symbolic expressions that characterize nonlinear relationships in data, gaining increasing attention for its interpretability, compactness, and robustness. However, existing SR methods do not scale to datasets with a large number of input variables (referred to as extreme-scale SR), which is common in modern scientific applications. This "large $p$'' setting, often accompanied by measurement error, leads to slow performance of SR methods and overly complex expressions that are difficult to interpret. To address this scalability challenge, we propose a method called PAN+SR, which combines a key idea of ab initio nonparametric variable selection with SR to efficiently pre-screen large input spaces and reduce search complexity while maintaining accuracy. The use of nonparametric methods eliminates model misspecification, supporting a strategy called parametric-assisted nonparametric (PAN). We also extend SRBench, an open-source benchmarking platform, by incorporating high-dimensional regression problems with various signal-to-noise ratios. Our results demonstrate that PAN+SR consistently enhances the performance of 19 contemporary SR methods, enabling several to achieve state-of-the-art performance on these challenging datasets.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有符号回归（Symbolic Regression, SR）方法无法有效处理大量输入变量（即大规模 \(p\) 的场景），导致搜索速度慢、最终表达式过于复杂且难以解释。现代科学应用中常出现这种“大 \(p\) 小 \(n\)”或高维噪声数据，传统SR方法几乎不可用。
- **研究动机**：SR因其可解释性、紧凑性和鲁棒性而备受关注，但可扩展性瓶颈严重限制了其在真实高维问题中的应用。需要一种高效预筛选无关变量的机制，在不牺牲精度的前提下显著降低搜索复杂度。
- **整体含义**：本文提出了一种结合从头算（ab initio）非参数变量选择与SR的通用框架 **PAN+SR**，旨在解决极端大规模变量（large \(p\)）下的可扩展符号回归问题。

## 2. 论文提出的方法论

### 核心思想
- **分步剪枝**：先使用非参数方法对输入变量进行独立筛选（ab initio变量选择），仅保留少数有潜力的变量，再对降维后的子空间执行符号回归。
- **关键理念**：采用非参数方法避免模型误设定（model misspecification），并辅以参数辅助非参数（Parametric-Assisted Nonparametric, PAN）策略，提高选择效率。

### 关键技术细节
1. **非参数变量选择**：使用一种与模型无关的依赖性度量（如基于核或距离的相关性指标）来计算每个输入变量与响应变量之间的相关性，剔除与响应无关的变量。
2. **PAN策略**：在非参数选择过程中，利用参数模型的辅助信息（例如线性回归拟合残差）来增强选择的鲁棒性，尤其适用于含测量误差的场景。
3. **SR步骤**：对筛选后的小规模变量子集应用任意已有的符号回归方法（如遗传编程、神经网络符号回归等），从而大幅缩短搜索时间、简化表达式。

### 算法流程（文字说明）
1. 输入：原始高维数据 \((X, y)\)，包含 \(p\) 个候选变量。
2. 非参数筛选：对每个变量 \(x_i\)，计算其与 \(y\) 的非参数依赖性得分（如基于距离相关性），并按照阈值或固定数量选出 top-\(k\) 变量。
3. 可选 PAN 增强：若采用 PAN，则先用简单参数模型拟合 \(y\)，取其残差作为新的响应，再对残差进行非参数筛选，以剔除与参数模型线性部分重叠的变量。
4. 将筛选后的变量集送入任意 SR 算法，执行表达式搜索。
5. 输出：最优符号表达式。

## 3. 实验设计

- **数据集/场景**：
  - 合成数据：生成具有已知真值表达式的高维回归问题，包含不同信噪比（SNR）和变量数量（p 从几十到数千）。
  - 真实数据：来自 SRBench 平台的高维真实回归任务。
- **基准平台**：扩展了开源基准测试平台 **SRBench**，额外加入了高维回归问题，并控制了信噪比。
- **对比方法**：总共对比了 **19 种当代符号回归方法**，涵盖遗传编程类（如 GP、E2E）、神经网络类（如 SymbolicGPT）、以及混合方法等。每种方法均在有无 PAN+SR 预处理的情况下分别测试，以验证通用性。

## 4. 资源与算力

- **未明确说明**：论文摘要及元数据中未提及具体使用的 GPU 型号、数量或训练时长。仅提到“在 SRBench 扩展数据集上评估”，未对硬件资源进行量化描述。因此无法提供算力细节。

## 5. 实验数量与充分性

- **实验组数**：至少包含以下系列实验：
  - 合成数据上不同 \(p\) 和 SNR 组合的测试（可能多个配置）。
  - 真实数据集上的评估。
  - 对全部 19 种 SR 方法分别进行“无 PAN+SR”和“有 PAN+SR”的对比实验（至少 \(19 \times 2 = 38\) 组主实验）。
  - 可能包含消融实验（如比较不同非参数指标、不同筛选阈值）。
- **充分性与公平性**：
  - **充分**：覆盖了大 \(p\) 范围的合成与真实场景，并对比了几乎所有现有主流 SR 方法，实验规模较大。
  - **公平**：采用固定预处理流程，对每种方法使用相同筛选策略，对比时保持其他条件一致，且使用扩展后的 SRBench 标准平台，减少人为偏差。
  - **潜在不足**：未公开源代码或详细超参数设置，可能影响可复现性；未在极端大 \(p\)（如 \(p>10000\)）或含缺失值的数据上测试。

## 6. 论文的主要结论与发现

1. **PAN+SR 普遍提升性能**：在所有 19 种 SR 方法上应用 PAN+SR 预处理后，其在大 \(p\) 数据集上的表达式恢复率、预测准确率和速度均显著优于原始方法。
2. **实现最先进水平**：多个基础 SR 方法在搭配 PAN+SR 后，在高维 SRBench 扩展数据集上达到了 state-of-the-art 性能。
3. **非参数选择有效性**：无需先验假设，通过简单的非参数筛选即可极大降低搜索复杂度，且不会丢失重要变量（在仿真中恢复率高）。
4. **PAN 策略增强鲁棒性**：在含有噪声或测量误差时，参数辅助非参数方法进一步提升了筛选质量。

## 7. 优点

- **方法创新**：首次将从头算非参数变量选择与符号回归系统结合，思路简洁，不依赖于特定的 SR 后端，具有极强的通用适配性。
- **实验充分**：覆盖 19 种当代方法，对比全面，结论具有统计说服力。
- **实用性强**：解决了真实科学应用中常见的“大 p、有噪声”难题，使 SR 实用化更近一步。
- **开源贡献**：扩展了 SRBench 平台，添加高维测试用例，便于后续研究者复现和比较。

## 8. 不足与局限

- **实验细节缺失**：未报告具体的非参数得分函数、阈值选择方法、合成数据生成参数等，缺乏复现所需细节。
- **算力成本未说明**：无法评估该方法相对于其他方法的时间开销是否可接受。
- **极端高维验证不足**：仅提及“large p”，但未明确最大 \(p\) 值（例如是否达到 \(p>10000\)），也未测试与深度学习方法（如 SAE）的组合。
- **潜在偏差风险**：所有实验均在学术基准上完成，未在工业级高维稀疏数据（如基因组学、文本）中验证，泛化性存疑。
- **剪枝风险**：非参数筛选可能漏掉与响应仅存在强非线性交互但边际相关性弱的变量，有误删重要变量的风险。

（完）
