---
title: Discriminative Site-Directed Protein Engineering via Lightweight CASPE Platform
title_zh: 基于轻量级CASPE平台的判别性定点蛋白质工程
authors: "Deng, Q., Qiao, J., Wang, C., Ni, X., Chang, Y., Zhao, N., Zhai, R., Cui, H., Li, X., Jin, M."
date: 2026-05-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.24.720551v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 使用蛋白质语言模型的轻量级蛋白质工程平台
tldr: "蛋白质语言模型在挖掘序列共进化信息方面有潜力，但零样本预测与工业需求不匹配且训练成本高。本文提出轻量级CASPE平台，包含CAS模块（利用梯度激活映射和多层注意力提取关键位点）和APCNet（点云分类网络），无需结构或先验知识。CASPE在热稳定性（31.3-60%）和pH耐受性（40-80%）上取得高命中率，植酸酶定向进化成功率33.3%，优于FoldX（6.7%）和ESM2-t33（13.3%），提供精准高效的酶优化框架。"
source: biorxiv
selection_source: fresh_fetch
motivation: 解决蛋白质语言模型零样本预测与工业应用需求不匹配及训练成本高的问题。
method: 提出CASPE平台，包含CAS模块（梯度激活映射与多层注意力提取关键氨基酸位点）和APCNet（点云分类网络用于残基预测）。
result: "热稳定性命中率31.3-60%，pH耐受性命中率40-80%；植酸酶定向进化成功率33.3%，优于FoldX和ESM2-t33。"
conclusion: CASPE实现了精准位点靶向的酶进化，为工业酶开发提供了高效计算框架。
---

## 摘要
蛋白质大语言模型为序列共进化信息的深度挖掘提供了一种新颖的计算范式，显著加速了用于生物技术和医学应用的功能蛋白的生成。然而，零样本预测的进化适应度与工业应用需求之间的错位导致获取有益突变成功率有限，同时高训练成本是大模型的另一个缺点。在此，我们开发了CASPE（关键氨基酸流线型蛋白质进化），一个轻量级蛋白质工程平台，用于精确定位和适应关键残基，由CAS（关键氨基酸位点）和APCNet（氨基酸点云分类网络）组成。CAS利用梯度激活映射和多层注意力矩阵，从PLM中直接提取决定靶标特性的关键信息，并将其转化为显式的位点重要性指标，无需依赖额外的结构信息或先验知识。与APCNet协同工作，CASPE建立了一个涵盖从位点定位到残基预测的完整轨迹的工作流程。CASPE在识别耐热性（31.3%-60%）和pH耐受性（40%-80%）的有益变体方面取得了显著命中率，进一步揭示了这些关键靶点位点的潜在作用机制。植酸酶的定向进化进一步验证了CASPE的普适性。CASPET-植酸酶在获得有益突变体方面实现了33.3%的成功率，显著优于FoldX（6.7%）和ESM2-t33（13.3%）。CASPE引导酶进化朝向精确的、位点靶向优化，为开发工业酶提供了高效的计算框架。

## Abstract
Protein large language models (PLMs) provide a novel computational paradigm for the deep mining of sequence co-evolutionary information, significantly accelerating the generation of functional proteins for biotechnological and medical applications. However, the misalignment between zero-shot predicted evolutionary fitness and industrial application requirements leads to a limited success rate in acquiring beneficial mutations, while the high training cost presents another drawback of large models. Here, we developed CASPE (Critical Amino acids Streamline Protein Evolution), a lightweight protein engineering platform for the precise localization and adaptation of critical residues, consisting of the CAS (Critical amino acid sites) and APCNet (Amino acid Point Cloud Classification Network). CAS utilizes gradient activation mapping and multi-layer attention matrices to directly extract key information determining target properties from PLMs and transform it into explicit site importance indicators, without relying on additional structural information or prior knowledge. Working in tandem with APCNet, CASPE establishes a workflow encompassing the entire trajectory from site localization to residue prediction. CASPE achieved remarkable hit rates in identifying beneficial variants for thermostability (31.3-60%) and pH tolerance (40-80%), further uncovering the potential mechanisms of action at these key target sites. Directed evolution of phytase further validated the generalizability of CASPE. CASPET-Phytase achieved a 33.3% success rate in obtaining beneficial mutants, which was significantly better than FoldX (6.7%) and ESM2-t33 (13.3%). CASPE guides enzyme evolution towards precise, site-targeted optimization, providing an efficient computational framework for developing industrial enzymes.