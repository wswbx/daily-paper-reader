---
title: "Learning from Drops: AI-Guided Integration of Liquid Biopsy Features in Cancer Studies"
title_zh: 从液体活检中学习：人工智能引导下癌症研究中液体活检特征的整合
authors: "Andueza, M., Villoslada-Blanco, P., De Dreuille, B., Alonso, L., Sabroso-Lasa, S., Pantel, K., Alix-Panabieres, C., Lopez de Maturana, E., Malats, N."
date: 2026-05-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.12.724535v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: AI指导的液体活检特征整合用于癌症发现
tldr: 针对癌症液体活检（LB）特征整合中AI应用不足的问题，本文提出了一套AI引导的方法学指南，涵盖数据预处理（归一化、批次校正、异常值处理）、特征选择和模型验证，旨在提升LB多组学整合分析的鲁棒性和临床实用性。
source: biorxiv
selection_source: fresh_fetch
motivation: 癌症液体活检产生的海量高通量数据需要AI整合，但目前相关研究稀疏，缺乏系统方法指导。
method: 通过文献调研提出AI方法框架，包括研究设计、数据预处理（归一化、批次校正、缺失值处理）及机器/深度学习特征选择与严格内外验证。
result: 现有文献中整合多个LB特征并应用AI的研究很少，提出的方法学可弥补这一空白。
conclusion: 为液体活检研究界提供基于AI的方法学指南，以桥接两领域并增强LB特征的整合分析。
---

## 摘要
癌症是一个重大的全球性健康问题，发病率和死亡率不断上升。早期检测、肿瘤特征描述和疾病监测对于及时有效的治疗至关重要，最终降低死亡率。液体活检（LB）已成为一种有价值的检测工具，提供了一种非侵入性方法来检测体液中的肿瘤源性生物标志物，并显示出转化的潜力。为了提高生物标志物的敏感性，高通量测序平台提供了海量数据。人工智能（AI）在实现海量复杂数据整合中起着关键作用。本文旨在评估LB领域中基于AI的整合研究的现状，并提供方法学指导。首先，我们进行了PubMed检索，发现整合LB特征的研究很少，特别是应用AI的研究。当采用后一种方法时，定义研究目标对于指导后续方法学方面至关重要，包括研究设计、患者选择标准、样本量、LB特征的性质以及要收集的元数据。具体而言，我们提出了数据预处理的策略和工具，包括归一化和批次校正，以及处理异常值和缺失数据。此外，我们推荐了各种机器学习/深度学习方法用于特征选择技术，以确保模型的稳健性，并强调了所选模型进行严格内部和外部验证的重要性。评估临床效用和可解释性常常被忽视，但对于实际实施至关重要。总之，我们为LB科学界提供了基于AI的方法学指导，以桥接这两个领域并加强LB特征的整合分析。

图形摘要：液体活检领域多组学整合研究工作流程图。注：CTCs，循环肿瘤细胞；ctDNA，循环肿瘤DNA；TEPs，肿瘤教育血小板；miRNA，微小RNA；cfRNAs，游离RNA。

## Abstract
Cancer is a major global health issue with rising incidence and mortality. Early detection, tumor characterization, and disease surveillance are crucial for timely and effective treatment, ultimately reducing mortality rates. Liquid biopsy (LB) has emerged as a valuable detection tool offering a non-invasive method to determine tumor-derived biomarkers in body fluids with demonstrated translational potential. To increase biomarker sensitivity, high-throughput sequencing platforms deliver massive volumes of data. Artificial Intelligence (AI) is pivotal in enabling huge and complex data integration. This contribution aims to assess the current state of integrative AI-based research in the LB field and provide methodological guidance. First, we conducted a PubMed search and found that the literature is sparse in studies integrating LB features, particularly by applying AI. When adopting the latter approach, defining the study objectives is crucial to guide the subsequent methodological aspects, including study design, patient selection criteria, sample size, nature of the LB features, and metadata to collect. Specifically, we propose strategies and tools for data preprocessing, including normalization and batch correction, as well as handling outliers and missing data. Furthermore, we recommend various Machine/Deep Learning approaches for feature selection techniques to ensure model robustness, and we highlight the importance of undergoing rigorous internal and external validations of the selected models. Assessing clinical utility and interpretability is often overlooked but fundamental for real-world implementation. In conclusion, we provide the LB scientific community with an AI-based methodological guidance to bridge the two fields and enhance the integrative analysis of LB features.

Graphical abstractWorkchart for multiomics integrative studies in the liquid biopsy field. Note: CTCs, circulating tumor cells; ctDNA, circulating tumor-DNA; TEPs, tumor-educated platelets; miRNA, microRNA; cfRNAs, cell-free RNAs.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=159 SRC="FIGDIR/small/724535v1_ufig1.gif" ALT="Figure 1">
View larger version (45K):
org.highwire.dtl.DTLVardef@1f250b2org.highwire.dtl.DTLVardef@18fe36corg.highwire.dtl.DTLVardef@19c02b9org.highwire.dtl.DTLVardef@176f6e0_HPS_FORMAT_FIGEXP  M_FIG C_FIG