---
title: Discovering data-driven microbial growth models with symbolic regression
title_zh: 用符号回归发现数据驱动的微生物生长模型
authors: "Sun, T. A., Kiciatovas, D., Aapalampi, I.-K., Kuosmanen, T., Hiltunen, T., Mustonen, V."
date: 2026-04-30
pdf: "https://www.biorxiv.org/content/10.1101/2025.06.02.657040v4.full.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 应用符号回归从数据中发现微生物生长模型
tldr: 本研究开发了一种基于符号回归的数据驱动方法，从微生物生长数据中自动推断显式动力学模型。该方法不预设模型结构，通过随机森林发现累积种群增益比种群大小更具信息量，并与恒定资源消耗率相关。理论指导下的符号回归平衡了数据拟合、简洁性和生物学相关性，优选线性近似和基于Monod动力学的模型。在E. coli和16种物种的实验验证中成功识别生长规律，为数据驱动建模提供了新见解。
source: biorxiv
selection_source: fresh_fetch
motivation: 连接数学模型与实验微生物生长仍具挑战，现有竞争模型均能拟合数据，需自动从数据中发现生长模型。
method: 采用符号回归直接从生长数据推断动力学模型，结合随机森林特征分析并引入理论约束以增强生物学可解释性。
result: 符号回归发现线性近似和Monod动力学模型（单或双资源）最佳平衡数据拟合、简洁性与生物学相关性；累积种群增益优于种群大小作为特征。
conclusion: 数据驱动方法能从批量培养中有效读取生长规律，为微生物生长建模提供实用途径。
---

## 摘要
O_LI将数学模型与经验测量的微生物生长联系起来仍然具有挑战性，因为基于不同理论方法的众多竞争模型都能拟合观测数据。因此，我们开发了一种方法，仅从微生物数据自动提出生长模型。我们利用一个已知资源上培养的大肠杆菌数据集验证了该方法，并研究了十六种物种在不同浓度的丰富培养基中的生长。
C_LIO_LI符号回归这种本质上可解释的方法直接从生长数据推断显式动力学模型。原生使用符号回归并不倾向于选择生物可解释模型，但我们发现累积种群增益比种群大小是一个更具信息量的机器学习特征。
C_LIO_LI随机森林机器学习使我们能够将这一发现与恒定速率的人均资源消耗近似联系起来。这表明常规实验中测量的生长曲线下面积（AUC）提供了关于控制微生物生长的有效资源动态的信息。最后，我们利用理论见解指导符号回归算法，并倾向于生物可解释模型。
C_LIO_LI总体而言，我们发现平衡数据拟合、简约性和生物学相关性有利于最简单的线性近似模型以及基于莫诺动力学的模型（具有一个或两个基础资源）。因此，我们读取微生物批次培养中生长规律的方法为数据驱动建模提供了见解。
C_LI

## Abstract
O_LIConnecting mathematical models with empirically measured microbial growth has remained challenging, as numerous competing models based on different theoretical approaches can fit observations. Therefore, we develop a method to automatically propose growth models from microbial data alone. We validate this approach using an available dataset of E. coli grown on known resources, and study sixteen species across various concentrations of a rich medium.
C_LIO_LIThe inherently interpretable approach of symbolic regression infers explicit dynamical models directly from growth data. Using symbolic regression natively, does not favour biologically interpretable models, but we find cumulative population gain to be a more informative machine learning feature than population size.
C_LIO_LIRandom Forest machine learning allows us to relate this finding to the approximation of a constant-rate per capita resource consumption. This suggests that the area under the growth curve (AUC) measured in routine experiments provides information on the effective resource dynamics governing microbial growth. Finally, we use theoretical insights to inform the symbolic regression algorithm and favour biologically interpretable models.
C_LIO_LIOverall, we found that balancing between data fit, parsimony and biological relevance favoured both the simplest, linear approximation, and models based on a Monod dynamics, with either one or two underlying resources. Therefore, our approach to read growth laws off of microbial batch cultures provides insights on data-driven modelling.
C_LI

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义
- **研究动机**：微生物生长是生态和进化中的关键过程，但将数学模型与实验测量联系起来面临挑战，因为基于不同理论的众多竞争模型（如 Logistic、Monod、多资源模型）都能拟合相同的观测数据，导致无法区分真实生成机制。
- **核心问题**：如何从微生物数据中自动发现可解释的生长模型，而不依赖强先验假设？传统方法先假设模型族再拟合，模型选择阶段不受数据批判；该工作提出相反思路：先数据驱动地生成候选模型，再通过生物学可解释性筛选。
- **整体含义**：这项工作为从常规批次培养数据中“读取生长规律”提供了实用框架，可推断有效资源维度（即微生物如何感知复杂培养基），有助于理解微生物代谢互作、种群动态和生态位理论。

## 2. 方法论
- **核心思想**：使用符号回归（Symbolic Regression）直接从生长数据中搜索数学表达式，以最小化均方误差为优化目标，同时控制表达式复杂度；随后结合理论约束（如正数常量、整数幂次、恒定资源消耗率假设等）筛选生物可解释模型。
- **关键技术细节**：
  - **特征构造**：除种群大小 \(N\) 和时间 \(t\) 外，引入累积种群增益 \(N_c = \int N dt\)（即 AUC）。随机森林实验显示 \(N_c\) 比 \(N\) 更优预测生长率。
  - **理论支撑**：基于质量作用定律，假设资源消耗速率为常数，则资源浓度 \(S \propto C \cdot e^{-\nu N_c}\)，这解释了 \(N_c\) 的信息价值。
  - **表达式模板**：使用两种模板引导搜索：  
    (1) \(\rho_{obs} = \frac{q}{q+e^{-mt}} \cdot \hat{\rho}(C, N_c)\)  
    (2) \(\rho_{obs} = \frac{q}{q+e^{-mt}} \cdot \hat{\rho}(C \times \hat{h}(N_c))\)  
    其中 \(q,m\) 为滞后调整参数，\(\hat{\rho}\) 和 \(\hat{h}\) 由符号回归自动发现。
  - **算法**：使用 PySR (Cranmer, 2023) 作为符号回归工具，操作集包括 \(+,\times,/,\; \hat{k}\)（\(k>0\)），禁止负常量和非整数幂。归一化 \(N_c\) 并采用指数变换 \(U=e^{-t}, F=e^{-N_c}\) 作为特征。
- **流程**：实验数据 → 随机森林特征重要性分析 → 符号回归搜索表达式 → 手动标注生物学可解释模型。

## 3. 实验设计
- **数据集**：
  - **验证数据**：Held et al. (2024) 公开的大肠杆菌在已知资源（葡萄糖和铵）上的批次培养数据。
  - **主要数据**：16 种细菌（HAMBI 库）在 R2A 丰富培养基中，20 种不同初始浓度（2.8%–200%），4 个生物重复，共 1280 条生长曲线（实际分析 14 种，因两种未达稳定期）。
  - **模拟数据**：通过一维/二维 Monod 动力学生成，用于测试符号回归能否正确推断资源可替代性。
- **Benchmark**：无外部基准方法对比。论文本身将“无约束符号回归”与“理论引导符号回归”对比，以及将特征集 \(N\) vs \(N_c\) 对比。
- **对比方法**：主要比较不同特征集合（{C,N}、{C,N,t}、{C,Nc}、{C,Nc,t}）在符号回归和随机森林上的性能；未对比其他模型发现方法（如 GP、SINDy 等）。

## 4. 资源与算力
- **未明确说明**：文中未提及使用的 GPU 型号、数量或训练时长。仅在致谢中提到 CSC – IT Center for Science 提供了计算资源，但无具体硬件细节。

## 5. 实验数量与充分性
- **实验数量**：
  - 真实实验：14 种细菌 × 20 浓度 × 4 重复（平均后分析）。
  - 模拟实验：生成多个场景（一维/二维 Monod，可替代/不可替代资源）。
  - 随机森林实验：对每种细菌数据集，在 5 种最大树深度下测试 4 种特征集。
  - 符号回归：针对每个数据集运行多次搜索，产生 1068 个候选模型。
- **充分性评估**：
  - 实验设计较为系统，覆盖多种物种和浓度梯度，模拟数据用于验证方法在已知真相下的表现。
  - **客观性**：随机森林特征分析独立于符号回归，结论一致；验证数据（E. coli）来自独立团队，增加了可信度。
  - **局限性**：未与其他数据驱动方法（如 GP、SINDy、深度学习）进行系统对比，未测试在不同培养基类型（如化学限定培养基）以外的推广性。仅基于 OD600 测量，可能存在测量噪声和有限时间分辨率的影响。

## 6. 主要结论与发现
- **核心发现**：
  - 累积种群增益 \(N_c\)（AUC）比瞬时种群大小 \(N\) 能更有效预测生长率，且与恒定资源消耗率的理论假设一致。
  - 无约束符号回归虽拟合性能好，但缺乏生物学可解释性；引入理论约束后，能优先提出生物相关模型。
  - 在大多数物种中，最简单的线性模型（资源消耗率恒定）或一维 Monod 模型足以描述实验数据；少数需要二维 Monod（乘法形式，非替代资源）。
- **有效资源维度**：即使在复杂 R2A 培养基中，生长动力学通常可用 1–2 个有效资源解释，表明微生物感知的“资源空间”是低维的。
- **模型选择建议**：平衡拟合、简约性和生物学相关性后，建议采用线性模型（极简）或一维 Monod 模型（小幅改进）；多维模型仅在特定物种中提供额外改善。

## 7. 优点
- **新颖方法**：首次将符号回归系统应用于微生物生长模型发现，避免先验假设，允许数据驱动假设生成。
- **可解释性强**：输出为显式数学公式，可直接与 Monod、多资源理论对应，优于黑箱神经网络。
- **结合领域知识**：巧妙引入累积种群增益特征和理论模板，在保持自动化的同时提升生物学意义。
- **广泛验证**：涵盖多种细菌和模拟数据，验证了方法在已知/未知资源下的有效性。
- **实用价值**：揭示 AUC 的信息价值，为常规生长曲线分析提供新视角，可推广到其他微生物系统。

## 8. 不足与局限
- **模型不可发现性**：作者承认，符号回归无法保证发现真实生成模型（参数不可辨识性、Richardson 定理等），只能提供“充分”的近似。
- **实验覆盖偏差**：仅使用一种培养基（R2A）和 OD600 测量，未测试其他环境（如厌氧、不同 pH、多物种共培养）；可能高估 Monod 模型的一般性。
- **缺乏对比基准**：未与 SINDy、差分进化、贝叶斯模型选择等现有方法比较，难以量化本方法的优劣势。
- **算力信息缺失**：未报告符号回归的计算开销，实际应用时可能面临高复杂度（尤其当模型空间大时）。
- **生物学注释主观**：模型“可解释性”通过人工标注判断，可能引入研究者偏差；自动化筛选标准尚不严格。
- **适用范围限制**：仅针对批次培养的单种群生长，未考虑空间结构、代谢物协作、进化动态等复杂因素。

（完）
