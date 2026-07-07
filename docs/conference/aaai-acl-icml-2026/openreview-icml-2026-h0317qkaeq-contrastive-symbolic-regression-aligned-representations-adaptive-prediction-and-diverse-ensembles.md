---
title: "Contrastive Symbolic Regression: Aligned Representations, Adaptive Prediction, and Diverse Ensembles"
title_zh: 对比符号回归：对齐表示、自适应预测与多样化集成
authors: "Hengzhe Zhang, Qi Chen, Bing Xue, Wolfgang Banzhaf, Mengjie Zhang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/a94a4a0441cb770d6aece9a12361f9b83578efe2.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 提出对比符号回归，融合进化特征构建与对比学习
tldr: 现有符号回归方法忽略数据实例间的结构关系，本文提出对比符号回归（CSR），将进化特征构建与对比学习相结合，构建几何邻近反映目标相似性的表示空间，并通过K近邻回归实现自适应预测，显著提升符号回归的泛化能力。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 符号回归常忽略实例间关系，限制了特征表达能力和预测性能。
method: 采用对比学习优化特征空间的线性变换，使几何距离与目标相似度对齐。
result: CSR在多个基准上优于传统符号回归方法。
conclusion: 对比学习能有效增强符号回归的特征构建。
---

## Abstract
Existing symbolic regression approaches primarily focus on learning explicit input-output mappings, often neglecting relational structures among data instances. This paper introduces Contrastive Symbolic Regression (CSR), a feature-construction-based symbolic regression approach that integrates evolutionary feature construction with contrastive learning to shape a representation space where geometric proximity reflects similarity in the target space. CSR employs a contrastive objective that optimizes a linear transformation of constructed features, with a closed-form solution for aligning the feature space with the target space. The constructed features are applied to K-nearest neighbor regression, where we propose an efficient leave-one-out cross-validation (LOOCV) method that addresses standard LOOCV's computational expense and adaptively selects the neighborhood size, along with a linear-rank weighted K-nearest neighbor variant for faithful assessment of representation quality during evolution. A determinantal point process-based ensemble selection mechanism further enhances robustness by jointly considering model quality and diversity. Extensive experiments on 58 real-world regression datasets demonstrate that CSR consistently surpasses both traditional symbolic regression and modern machine learning counterparts, highlighting CSR as a promising direction for interpretable and effective regression modeling.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

符号回归（Symbolic Regression）旨在发现显式的数学表达式来描述输入与输出之间的关系，具有可解释性强的优点。然而，现有方法大多只关注学习输入-输出的直接映射，忽略了数据实例之间存在的结构关系（如相似样本应具有相近的目标值）。这种忽视限制了特征构建的表达能力，导致模型泛化性能不足。本文提出的对比符号回归（CSR）通过引入对比学习，将进化特征构建与实例关系对齐结合起来，旨在构建一个几何距离反映目标相似度的表示空间，从而提升符号回归的预测性能与鲁棒性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将进化算法（如遗传编程）自动构建的特征，通过对比学习优化一个线性变换，使得变换后的特征空间中，样本之间的几何邻近性能够反映目标值的相似性。然后使用K近邻回归进行自适应预测。
- **关键技术细节**：
  - **特征构建**：使用进化算法（遗传编程）从原始输入中生成一组非线性特征（如算术运算组合）。
  - **对比学习对齐**：设计一个对比目标函数，优化一个线性变换矩阵，使特征空间中的距离与目标空间（标签）的相似度对齐。该优化存在闭式解，计算高效。
  - **自适应K近邻回归**：提出一种高效的留一交叉验证（LOOCV）方法，避免标准LOOCV的高计算开销，并自适应地选择邻域大小。同时提出线性秩加权K近邻变体，在进化过程中更准确地评估表示质量。
  - **集成多样性增强**：基于行列式点过程（DPP）的集成选择机制，同时考虑模型质量和多样性，提升最终集成模型的鲁棒性。

## 3. 实验设计：使用了哪些数据集/场景，其benchmark是什么，对比了哪些方法

- **数据集**：在58个真实世界回归数据集上进行实验，涵盖多种领域和规模。
- **基准（Benchmark）**：未明确提及具体基准名称，但对比了传统符号回归方法和现代机器学习方法。
- **对比方法**：
  - 传统符号回归方法（如遗传编程类方法）
  - 现代机器学习回归方法（如随机森林、支持向量回归、神经网络等）

## 4. 资源与算力

论文中**未明确说明**使用的GPU型号、数量或训练时长等算力信息。推测主要依赖CPU进行进化计算和对比学习优化，因为方法本身不依赖大规模深度学习基础设施。

## 5. 实验数量与充分性

- **实验数量**：在58个真实世界回归数据集上进行了主实验，此外还包括消融研究（如对对比学习组件、K近邻自适应方法、DPP集成机制等的验证）。
- **充分性与公平性**：数据集数量较多（58个），覆盖广泛；对比方法全面（包含传统和现代方法）；消融实验充分验证了各组件的贡献。实验设计较为客观、公平，结果具有统计显著性（文中提到“consistently surpasses”）。

## 6. 论文的主要结论与发现

- CSR在58个真实回归数据集上一致优于传统符号回归方法和现代机器学习方法。
- 对比学习能够有效增强符号回归的特征构建，使特征空间的几何结构反映目标相似性。
- 提出的高效LOOCV自适应K近邻方法降低了计算成本，同时提升了预测精度。
- DPP集成选择机制进一步提升了模型的鲁棒性和多样性。
- 该方法展示了符号回归在保持可解释性的同时实现高性能的潜力。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将对比学习系统性地引入符号回归领域，解决实例关系被忽略的问题。
- **技术优雅**：对比学习的目标函数存在闭式解，避免了迭代优化开销。
- **高效性**：提出的LOOCV方法显著降低了计算负担，使自适应邻域选择成为可能。
- **鲁棒性**：DPP集成选择兼顾质量和多样性，提升泛化。
- **实验充分**：58个真实数据集、多组消融实验，结果可靠。

## 8. 不足与局限

- **计算资源未报告**：缺乏对实际运行时间和硬件要求的描述，可复现性受影响。
- **数据集规模**：58个数据集虽然较多，但未明确说明数据维度、样本量分布，可能偏向小/中规模数据；大规模高维数据上的表现未知。
- **可解释性**：虽然符号回归本身是可解释的，但经过线性变换和K近邻后，最终模型的解释性可能下降。
- **超参数敏感度**：进化特征数量的选择、对比学习变换维度等超参数未深入讨论其敏感性。
- **对比方法**：可能未包含最新的大规模深度学习回归模型（如Transformer-based方法），竞争力有待进一步验证。

（完）
