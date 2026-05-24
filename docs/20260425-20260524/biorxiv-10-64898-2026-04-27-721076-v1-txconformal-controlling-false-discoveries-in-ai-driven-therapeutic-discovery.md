---
title: "TxConformal: Controlling False Discoveries in AI-Driven Therapeutic Discovery"
title_zh: TxConformal：在人工智能驱动的治疗发现中控制错误发现
authors: "Jin, Y., Huang, K., Diamant, N., Buchholz, K. R., Rutherford, S. T., Skelton, N., Biancalani, T., Scalia, G., Leskovec, J., Candes, E. J."
date: 2026-04-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.27.721076v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 在AI驱动的治疗发现中控制假发现
tldr: "AI在治疗发现中评分大量候选分子，但假阳性高且分布偏移难以处理。本文提出TxConformal框架，利用保形预测调整分布偏移，输出类p值置信度用于多重假设检验，控制错误发现率。在六个真实任务中，TxConformal减少近一半假阳性，节省数万美元实验成本；在蛋白质稳定性选择中恢复90%以上有价值候选。前瞻性抗生素筛选实验验证了其假阳性预测与实验结果高度一致。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AI评分在治疗发现中假阳性高，且分布偏移难以量化，导致错误发现率失控。
method: 通过平衡AI模型隐藏表征调整分布偏移，基于保形预测生成可解释为p值的置信度，结合多重检验控制FDR。
result: "在六个任务中假阳性减少约50%，节省数万美元；在严格阈值下蛋白质选择数量提升10倍，恢复超90%被基线遗漏的候选。"
conclusion: TxConformal有效控制假阳性，支持多种误差指标，显著提升AI驱动治疗发现的可靠性。
---

## 摘要
人工智能正在通过给大量有前景的候选者评分并优先列出候选名单以进行进一步研究，从而改变治疗发现的模式。量化人工智能评分的可靠性并防止所选候选者中的假阳性是提高发现过程效率的关键。共形预测（CP）已成为指导此类优先级排序的流行工具，特别是通过共形选择框架来控制分布偏移下选择排名靠前的候选者时的错误发现率（FDR）[1,2]。然而，将这些进展应用于现实世界的治疗发现仍然具有挑战性：在高维生物医学数据中，分布偏移难以量化和校正，并且实际工作流程通常需要灵活的错误度量。在这里，我们提出TxConformal，一个在使用人工智能评分构建候选名单时进行可信决策的通用框架。TxConformal通过平衡人工智能模型中的隐藏表示来调整分布偏移，然后为目标生物学特性的真实发现提供置信度度量。这些置信度度量（可解释为p值）可以与统计多重检验程序结合使用，以在有限假阳性的情况下得出选择决策，或估计给定选择决策中的错误。TxConformal在跨越不同治疗发现阶段、模态和人工智能模型的六个实际任务中，使用真实数据划分控制了假阳性率。在选择有前景的组合遗传扰动时，与基线方法相比，TxConformal几乎将假阳性选择减半，大幅减少了数万美元的不必要实验成本。在突变偏移下选择稳定的蛋白质结构时，TxConformal在目标FDR为10%的严格阈值下，识别出的蛋白质数量约为基线方法的10倍，恢复了基线方法因未考虑分布偏移而遗漏的超过90%的有价值候选者。此外，我们证明了TxConformal稳健支持适用于资源受限环境的各种替代错误度量。最后，在一项针对新型抗生素发现的前瞻性固定预算虚拟筛选活动中，TxConformal预测的假阳性与实验结果高度一致，相比简单基线有显著改进。

## Abstract
Artificial Intelligence (AI) is transforming therapeutic discovery by scoring a large set of promising candidates and prioritizing a shortlist for further investigation. Quantifying the reliability of AI scores and preventing false positives among selected candidates is key to the efficiency of the discovery process. Conformal prediction (CP) has emerged as a popular tool for guiding such prioritization, especially via the conformal selection framework to control false discovery rates (FDR) in selecting top-ranked candidates under distributional shift1, 2. However, deploying these advances in real-world therapeutic discovery remains challenging: distribution shifts are difficult to quantify and correct in high-dimensional biomedical data, and practical workflows often require flexible error metrics. Here, we present TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW, a general framework for trustworthy decision making when building shortlists using AI scores. TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW adjusts for distribution shift by balancing the hidden representations in AI models and then provides confidence measures for true discoveries of target biological properties. These confidence measures, interpretable as p-values, can be used in conjunction with statistical multiple testing procedures to derive selection decisions with limited false positives or to estimate the errors in given selection decisions. TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW controls the false positive rate in six real-world tasks spanning various therapeutic discovery stages, modalities, and AI models with realistic data splits. When selecting promising combinatorial genetic perturbations, TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW nearly halves false-positive selections compared to baseline methods, substantially reducing unnecessary experimental costs by tens of thousands of dollars. When selecting stable protein structures under mutant shifts, TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW identifies about 10 times more proteins than baseline methods at stringent thresholds when running at a target FDR level of 10%, recovering over 90% of valuable candidates that baseline methods miss due to unaccounted distribution shifts. Furthermore, we demonstrate that TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW robustly supports various alternative error metrics suitable for resource-constrained settings. Finally, in a prospective fixed-budget virtual screening campaign for novel antibiotic discovery, TO_SCPLOWXC_SCPLOWCO_SCPLOWONFORMALC_SCPLOW predicted false positives in close agreement with experimental outcomes, with substantial improvements over simple baselines.