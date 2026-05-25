---
title: "An Isoform-Centric, Structure-Aware Framework for Protein Function Prediction and Evaluation, Instantiated in 3DisoDeepPF"
title_zh: 一个基于异构体、结构感知的蛋白质功能预测与评估框架，以3DisoDeepPF实现
authors: "Jiang, F., Zhao, R., Liang, F., Zhang, Y., Cui, T., Zhao, X., Wang, X., Xu, m., Shuai, Y., Luo, T., Yao, H., Xu, C., Wang, Z., Zeng, W., Jiang, X., Tang, Z., Zhang, W., Heng, P. A., Li, Y., Radivojac, P."
date: 2026-05-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.24.720502v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 7.0
evidence: 深度学习预测蛋白质功能辅助生物发现
tldr: 针对蛋白异构体功能预测数据稀缺的问题，提出异构体中心框架3DisoDeepPF，整合序列与结构相似性图及多模态表示，在乳腺癌异构体数据上显著提升Pfam域和GO项预测性能，并具备证据追踪能力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有蛋白功能预测方法多基于单一参考序列，缺乏对异构体功能的精准建模。
method: 提出3DisoDeepPF模型，融合序列与结构相似性密集图和多模态表示，进行深度多标签学习。
result: 在常规和异构体解析设置下，3DisoDeepPF均优于所有基线及最先进模型，且在同源控制评估中保持稳健。
conclusion: 3DisoDeepPF为解析疾病相关异构体功能提供了有效框架，可支持假设生成和癌症异构体优先排序。
---

## 摘要
理解和准确预测蛋白质异构体的功能一直是一个长期挑战，对生物学和转化研究具有深远影响。然而，由于缺乏高质量的异构体解析注释，大多数蛋白质功能预测的计算方法都是基于每个基因的一个参考序列进行开发和基准测试。为了填补这一空白，我们提出了一个以异构体为中心的蛋白质家族（Pfam）结构域和基因本体（GO）术语预测框架。我们将该框架实现为3DisoDeepPF，一个深度多标签学习模型，该模型将序列和结构相似性的密集图与多模态表示相结合，并将其应用于乳腺癌异构体特异性图谱。在传统和异构体解析设置下，3DisoDeepPF在GO术语和Pfam结构域预测上均优于所有基线和最先进模型。在同源控制的异构体级别评估中，它仍然保持稳健，并能解析同一基因中异构体之间的定向Pfam重塑。一个证据追踪模块将预测标签与相关蛋白质关联起来，如CIB1乳腺癌异构体案例研究所示。总之，3DisoDeepPF为解决疾病相关的异构体功能提供了一个框架，并可以支持假设生成和未来癌症相关异构体的优先排序。

## Abstract
Understanding and accurately predicting function across protein isoforms has been a long-standing challenge with profound implications for both biological and translational research. However, due to the scarcity of high-quality isoform-resolved annotations, most computational methods for protein function prediction have been developed and benchmarked using a single reference sequence per gene. To address this gap, we present an isoform-centric framework for protein family (Pfam) domain and Gene Ontology (GO) term prediction. We implemented this framework in 3DisoDeepPF, a deep multi-label learning model that integrates a dense graph of sequence and structure similarity with multimodal representations, and applied it to a breast cancer isoform-specific atlas. 3DisoDeepPF improves GO-term and Pfam-domain prediction over all baselines and state-of-the art models in both conventional and isoform-resolved settings. It also remains robust under homology-controlled isoform-level evaluation and resolves directional Pfam remodeling among isoforms from the same gene. An evidence-tracing module links predicted labels to associated proteins, as illustrated by a CIB1 breast cancer isoform case study. Together, 3DisoDeepPF provides a framework for resolving disease-relevant isoform function, and can support hypothesis generation and future prioritization of cancer-associated isoform.