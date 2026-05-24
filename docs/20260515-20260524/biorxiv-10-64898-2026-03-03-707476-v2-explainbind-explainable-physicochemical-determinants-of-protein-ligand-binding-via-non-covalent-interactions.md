---
title: "ExplainBind: Explainable Physicochemical Determinants of Protein-Ligand Binding via Non-Covalent Interactions"
title_zh: ExplainBind：通过非共价相互作用解释蛋白质-配体结合的物理化学决定因素
authors: "Meng, Z., Bai, Z., Yuan, K., Cheah, J. H., Jiang, W., Skepner, A., Leahy, K. J., Ounis, I., Oldham, W. M., Xu, H., Loscalzo, J."
date: 2026-05-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.03.707476v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: AI用于药物发现中的蛋白质-配体结合预测
tldr: 蛋白质-配体结合预测对药物发现至关重要，但现有AI方法多为黑箱，无法解释结合机制。本文提出ExplainBind，无需三维结构即可预测结合可能性、定位结合残基并解码非共价相互作用模式。该方法在多种蛋白质和配体上优于基线，成功识别ACE抑制剂和L2HGDH的抑制剂/激活剂，并通过相互作用图谱解释效力差异，为机制指导的药物发现提供了通用工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AI方法无法解析哪些残基介导结合以及哪些非共价力驱动分子识别。
method: 提出交互感知框架ExplainBind，无需三维结构输入，同时预测结合可能性、定位特定结合残基并解码非共价相互作用模式。
result: 在从密切相关到高度新颖的序列和骨架中一致优于基线，成功识别ACE抑制剂并解释效力差异，以及发现L2HGDH的抑制剂和激活剂。
conclusion: ExplainBind作为机制性药物发现的通用工具，能够解析结合决定因素并指导功能调节。
---

## 摘要
蛋白质-配体结合控制着酶催化、代谢调节和治疗调控，其预测是药物发现的基础。然而，现有的人工智能方法大多是黑箱预测器，无法解析哪些残基介导结合，或哪些非共价力驱动分子识别。我们提出了ExplainBind，一种交互感知框架，可以预测结合可能性、定位具体的结合残基（而非粗略的口袋级区域），并解码潜在的非共价相互作用模式，且无需三维结构输入。ExplainBind在从密切相关到高度新颖的序列和骨架的蛋白质和配体中，始终优于代表性基线方法。应用于两个未知靶标时，ExplainBind成功对有效的血管紧张素转化酶（ACE）抑制剂进行了排序，并通过亲和力分层相互作用景观解释了效力差异，同时前瞻性地发现了L-2-羟基戊二酸脱氢酶（L2HGDH）的抑制剂和激活剂，其机制不同的相互作用特征合理地解释了它们不同的功能结果，使其成为机制性药物发现的广泛应用工具。

## Abstract
Protein-ligand binding governs enzymatic catalysis, metabolic regulation, and therapeutic modulation, and its prediction underpins drug discovery. However, existing AI approaches broadly function as black-box predictors that cannot resolve which residues mediate binding or which non-covalent forces drive molecular recognition. We present ExplainBind, an interaction-aware framework that predicts binding likelihood, localizes specific binding residues rather than coarse pocket-level regions, and decodes the underlying non-covalent interaction patterns, all without requiring three-dimensional structural inputs. ExplainBind consistently outperforms representative baselines across proteins and ligands ranging from closely related to highly novel sequences and scaffolds. Applied to two unseen targets, ExplainBind successfully ranks potent angiotensin-converting enzyme (ACE) inhibitors and explains potency differences via affinity-stratified interaction landscapes, and prospectively discovers both inhibitors and activators of L-2-hydroxyglutarate dehydrogenase (L2HGDH), with mechanistically distinct interaction profiles rationalizing their divergent functional outcomes, establishing it as a broadly applicable tool for mechanistically informed drug discovery.