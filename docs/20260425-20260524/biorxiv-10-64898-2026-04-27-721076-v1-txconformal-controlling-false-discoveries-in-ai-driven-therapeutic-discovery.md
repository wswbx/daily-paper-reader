---
title: "TxConformal: Controlling False Discoveries in AI-Driven Therapeutic Discovery"
title_zh: TxConformal：控制AI驱动的治疗发现中的错误发现
authors: "Jin, Y., Huang, K., Diamant, N., Buchholz, K. R., Rutherford, S. T., Skelton, N., Biancalani, T., Scalia, G., Leskovec, J., Candes, E. J."
date: 2026-04-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.27.721076v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 9.0
evidence: AI驱动治疗发现，控制错误发现
tldr: 论文提出TxConformal框架，用于AI驱动治疗发现中控制假发现率。通过平衡AI模型隐藏表示来调整分布偏移，输出可解释为p值的置信度，结合多重检验控制假阳性。在六个真实任务中验证，在组合遗传扰动中假阳性减半，在蛋白质结构选择中识别率提高10倍，并支持资源受限场景的灵活误差度量。
source: biorxiv
selection_source: fresh_fetch
motivation: AI评分在治疗发现中假阳性率高，现有共形预测方法难以处理高维生物数据的分布偏移，亟需可靠框架控制错误发现。
method: TxConformal通过平衡AI模型隐藏表示调整分布偏移，生成类似p值的置信度，结合多重检验过程控制假阳性率。
result: 在六个任务中，TxConformal显著降低假阳性，如组合遗传扰动假阳性减半，蛋白质选择识别率提升10倍，且预测与实验一致。
conclusion: TxConformal提供了一种通用、可靠的决策框架，有效控制AI驱动治疗发现中的错误发现，降低实验成本并提高候选筛选效率。
---

## 摘要
人工智能正在通过为大量有前景的候选方案评分并优先列出短名单以供进一步研究，从而改变治疗发现过程。量化AI分数的可靠性并防止所选候选方案中的假阳性，是提高发现过程效率的关键。共形预测已成为指导此类优先排序的流行工具，特别是通过共形选择框架在分布偏移下控制选择排名靠前候选方案时的错误发现率。然而，在现实世界的治疗发现中部署这些进展仍然具有挑战性：在高维生物医学数据中，分布偏移难以量化和纠正，而实际工作流程通常需要灵活的误差指标。在这里，我们提出了TxConformal，这是一个在使用AI分数构建短名单时进行可信决策的通用框架。TxConformal通过平衡AI模型中的隐藏表示来调整分布偏移，然后为目标生物学特性的真实发现提供置信度度量。这些置信度度量可解释为p值，可以与统计多重检验程序结合使用，以在有限假阳性下得出选择决策，或估计给定选择决策中的误差。TxConformal在涵盖不同治疗发现阶段、模态和AI模型的六个实际任务中，使用真实数据分割控制了假阳性率。在选择有前景的组合遗传扰动时，与基线方法相比，TxConformal几乎将假阳性选择减半，从而大幅减少了数万美元的不必要实验成本。在选择突变偏移下稳定的蛋白质结构时，当目标FDR水平为10%时，TxConformal在严格阈值下识别出的蛋白质数量约为基线方法的10倍，恢复了基线方法因未考虑分布偏移而遗漏的90%以上有价值候选物。此外，我们证明TxConformal强大地支持适用于资源受限环境的多种替代误差指标。最后，在一项针对新型抗生素发现的前瞻性固定预算虚拟筛选活动中，TxConformal预测的假阳性与实验结果高度一致，相比简单基线有显著改进。

## Abstract
Artificial Intelligence (AI) is transforming therapeutic discovery by scoring a large set of promising candidates and prioritizing a shortlist for further investigation. Quantifying the reliability of AI scores and preventing false positives among selected candidates is key to the efficiency of the discovery process. Conformal prediction (CP) has emerged as a popular tool for guiding such prioritization, especially via the conformal selection framework to control false discovery rates (FDR) in selecting top-ranked candidates under distributional shift1, 2. However, deploying these advances in real-world therapeutic discovery remains challenging: distribution shifts are difficult to quantify and correct in high-dimensional biomedical data, and practical workflows often require flexible error metrics. Here, we present TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW, a general framework for trustworthy decision making when building shortlists using AI scores. TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW adjusts for distribution shift by balancing the hidden representations in AI models and then provides confidence measures for true discoveries of target biological properties. These confidence measures, interpretable as p-values, can be used in conjunction with statistical multiple testing procedures to derive selection decisions with limited false positives or to estimate the errors in given selection decisions. TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW controls the false positive rate in six real-world tasks spanning various therapeutic discovery stages, modalities, and AI models with realistic data splits. When selecting promising combinatorial genetic perturbations, TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW nearly halves false-positive selections compared to baseline methods, substantially reducing unnecessary experimental costs by tens of thousands of dollars. When selecting stable protein structures under mutant shifts, TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW identifies about 10 times more proteins than baseline methods at stringent thresholds when running at a target FDR level of 10%, recovering over 90% of valuable candidates that baseline methods miss due to unaccounted distribution shifts. Furthermore, we demonstrate that TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW robustly supports various alternative error metrics suitable for resource-constrained settings. Finally, in a prospective fixed-budget virtual screening campaign for novel antibiotic discovery, TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW predicted false positives in close agreement with experimental outcomes, with substantial improvements over simple baselines.

---

## 论文详细总结（自动生成）

好的，这是根据您提供的论文《TxConformal: Controlling False Discoveries in AI-Driven Therapeutic Discovery》生成的中文总结。

# 论文总结：TxConformal：控制AI驱动的治疗发现中的错误发现

## 1. 核心问题与整体含义
- **研究动机**：在AI驱动的治疗发现中，模型会从海量候选物（如分子、蛋白质）中筛选出少量“最有前景”的候选项进行实验验证。然而，AI预测存在不确定性，筛选出的高评分候选物中可能包含大量“假阳性”，即实际无效的候选物。这会浪费宝贵的实验资源和时间。因此，亟需一个能可靠量化AI预测不确定性并控制筛选错误率的框架。
- **核心挑战**：主要面临两个挑战：1）**选择效应**：被选中的候选物通常是模型预测值最高的，其表现与总体不同，导致传统统计保证失效；2）**分布偏移**：用于训练的已知数据与需要探索的新数据（如新化学空间、新生成序列）之间存在分布差异，导致模型预测不可靠。

## 2. 方法论
- **核心思想**：TxConformal 框架旨在提供一种“可信任的”选择决策，确保在筛选出的候选物短名单中，假阳性率（FDR）被严格控制在预设水平以下。它结合了因果推断中的**熵平衡**和统计学的**共形推断**及**多重假设检验**。
- **关键技术细节（三个模块）**：
    1.  **熵平衡**：用于估计和调整校准数据与测试数据之间的分布偏移。它利用AI模型（如GNN、Transformer）的潜在嵌入（hidden representations）作为特征，通过寻找一组权重，使得加权后的校准数据在特征分布上与测试数据相匹配，从而纠正未知的分布偏移。
    2.  **共形p值**：在调整了分布偏移后，为每个测试样本计算一个“共形p值”。该p值量化了该样本的真实标签超过用户指定阈值的统计置信度。p值越小，表明该候选物是真正发现的证据越强。这些p值在统计上是有效的，满足 \( P(p \le \alpha | 样本为假发现) \le \alpha \) 的性质。
    3.  **多重假设检验**：将计算出的共形p值输入到标准的多重检验程序（如Benjamini-Hochberg过程）中，从而得到一个可以在给定水平上控制多种错误度量（如FDR）的选择集。
- **理论保证**：论文提供了理论证明，证明在熵平衡能准确捕捉分布偏移或预测模型足够完美的情况下，TxConformal能渐近地达到预期的错误控制目标。

## 3. 实验设计
- **数据集/场景**：在六个真实世界的治疗发现任务中进行验证，每个任务都模拟了不同的分布偏移场景：
    - **蛋白质稳定性选择**（突变偏移）
    - **组合遗传扰动选择**（均匀采样，无偏移）
    - **增强子序列选择**（染色体偏移）
    - **AI生成启动子序列选择**（生成偏移）
    - **临床试验结果选择**（时间偏移）
    - **ADMET（CYP2D6）化合物选择**（骨架偏移）
- **基准/对比方法**：
    - **Conformal Baseline**: 使用标准的共形预测集进行选择，未考虑选择效应或分布偏移。
    - **TxConformal-Unweighted**: 仅使用共形p值（权重设为1），只处理选择效应，但未调整分布偏移。
    - **其他基线**：在ADMET任务中，还对比了仅依靠预测值简单选择的方法。
- **额外场景**：在CYP2D6任务上，展示了TxConformal在四种不同部署场景下的灵活性：控制FDR、确保最小真阳性数、控制期望假阳性数、以及估算给定选择集中的假阳性数。
- **前瞻性验证**：在一个全新的抗菌分子发现项目中，前瞻性地使用TxConformal预测后续实验的假阳性数，并最终与湿实验（wet-lab）结果进行对比验证。

## 4. 资源与算力
- **未明确说明**：论文中没有明确提及使用的GPU型号、数量或训练时长等算力信息。文中仅提到使用了如ESM、Enformer、GEARS等现有模型进行微调或直接应用，这些模型的原始训练可能需要大量资源，但在本研究的实验部分，主要强调模型结构和实验数据，未对算力投入进行量化描述。

## 5. 实验数量与充分性
- **实验数量**：实验非常充分。在六个核心任务的每个任务中，都进行了大量重复实验（通常是N=500次独立运行）以评估方法稳定性。针对ADMET任务的四种部署场景也各有详细展示和结果。
- **充分性与客观性**：
    - **多样性**：实验覆盖了蛋白质、基因、DNA序列、小分子、临床试验等多个不同的治疗发现模态，以及均匀采样、突变、染色体、时间、生成、骨架等多种分布偏移类型。这有力地证明了该方法的通用性和鲁棒性。
    - **公平性**：与两个核心基线方法（Conformal Baseline和TxConformal-Unweighted）进行了明确对比。
    - **客观性**：论文不仅报告了在回顾性数据集上的表现（伪标签），还进行了一次**前瞻性（prospective）**的湿实验验证，将模型预测结果与真实的实验结果直接对比，这是评估模型实用价值的黄金标准，极大地增强了结论的可信度。

## 6. 主要结论与发现
- **显著降低假阳性**：在所有任务中，TxConformal都能严格控制FDR在目标水平以下，而基线方法要么低估误差（导致假阳性过多），要么高估误差（错过大量有价值的候选物）。
- **提高发现效率**：例如，在蛋白质稳定性任务中，TxConformal在10% FDR目标下，识别出的稳定蛋白数量是基线方法的10倍以上，挽回了90%以上被基线方法遗漏的有价值候选者。
- **经济价值**：在组合遗传扰动任务中，TxConformal几乎将假阳性选择减半，显著减少了数万美元的不必要实验成本。
- **前瞻性验证成功**：在前瞻性的抗生素筛选实验中，TxConformal对假阳性数量的预测与最终实验结果高度吻合，而基线方法则严重低估了错误率，凸显了其在实际场景中的巨大价值。
- **灵活性和通用性**：TxConformal不仅限于控制FDR，还能灵活应用于其他资源受限的决策场景（如控制假阳性绝对数量）。

## 7. 优点
- **理论坚实**：框架基于共形推断和多重检验等严谨的统计学理论，并提供了渐近理论保证。
- **实用性强**：直接解决了AI在治疗发现中的核心痛点——假阳性控制，并能与现有AI模型无缝结合。
- **高度通用**：不依赖于特定的AI模型，适用于多种治疗发现阶段、生物模态和分布偏移类型。
- **前瞻性验证**：通过前瞻性实验证明了方法的实际有效性，而不仅仅是回顾性分析，说服力强。
- **灵活性**：支持多种用户定义的错误度量，能适应不同的实验预算和决策需求。

## 8. 不足与局限
- **依赖AI模型质量**：框架的性能（特别是熵平衡步骤）依赖于AI模型的潜在嵌入质量。如果模型表征能力差，无法捕捉关键结构特征，则调整分布偏移的效果会受限。
- **校准数据依赖性**：需要有足够且具有代表性的校准数据。在极少数或高度偏倚的实验观测数据下，其有效性可能打折扣。
- **计算开销**：熵平衡和多重检验的计算量可能随着测试集规模增大而显著增加。
- **需要预设阈值**：用户需要预先定义什么是“理想的”生物特性阈值，这可能与动态变化的发现目标不完全一致。
- **应用门槛**：虽然框架本身通用，但其成功应用仍需要对共形推断和多重检验有基本理解。

（完）
