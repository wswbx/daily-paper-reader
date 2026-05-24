---
title: Do Larger Models Really Win in Drug Discovery?A Benchmark Assessment of Model Scaling in AI-Driven Molecular Property and Activity Prediction
title_zh: 更大模型真的在药物发现中胜出吗？AI驱动分子性质与活性预测中模型规模的基准评估
authors: "Guo, J."
date: 2026-05-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.29.721568v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: AI模型在药物发现中的基准评估
tldr: 本文评估了AI在药物发现中的模型缩放假设，比较了经典ML、GNN、预训练序列模型和LLM在26个分子性质端点上的表现。结果显示经典ML（如RF）在多数情况下胜出，尤其在随机分裂下；更大模型在低数据场景下对SAR推理有价值，但预测性能取决于模型、任务和验证场景的匹配，而非仅模型规模。
source: biorxiv
selection_source: fresh_fetch
motivation: 验证更大预训练模型是否必然优于紧凑专用模型在分子性质预测中的表现。
method: 构建包含78个端点和分裂条目的基准，比较ML、GNN、预训练序列和LLM四类模型在不同难度分裂下的性能。
result: 经典ML在156个折叠均值比较中胜出116次，GNN和预训练序列模型次之，LLM表现最弱但对分裂不敏感。
conclusion: 紧凑专用模型仍然高效，更大模型在低数据时增强SAR解释，但预测性能不单纯取决于规模。
---

## 摘要
分子基础模型和大语言模型的快速发展鼓励了AI在药物发现中以规模为中心的观点，即更大的预训练模型有望取代为单个任务训练的紧凑化学信息学模型和图神经网络（GNN）。我们在26个终点上测试了这一假设，这些终点涵盖分子性质、毒性、安全性责任和生物活性，分为ADME、毒性和生物活性类别。该基准包含78个终点和分裂条目，涵盖随机、Murcko骨架和结构分离的五折交叉验证。按从易到难排序，这些分裂近似于封闭库的回顾性评估、苗头化合物到先导化合物的骨架扩展以及新型化学型的库扩展。每个条目包括ML、GNN、预训练分子序列和基于LLM的SAR系列。在156个折的均值比较中，经典ML（如RF(ECFP4)和ExtraTrees(RDKit)）获胜116次，GNN（如GIN和Ligandformer）获胜25次，预训练序列模型（如MoLFormer和ChemBERTa2）获胜12次，基于LLM的SAR基线获胜3次。ML在随机分裂插值中占主导地位，但在更困难的分裂下失去部分优势；GNN和序列模型也有所下降，但获得了相对地位，而基于LLM的SAR在绝对意义上较弱，但对分裂轴不太敏感。配对bootstrap分析对家族级趋势的支持强于单个模型排名。来自训练折叠的SAR知识改善了许多GPT5.5-SAR和Opus4.7-SAR指标，但并未使基于规则的推理成为监督预测器的普遍替代品。紧凑的专门模型在分子性质和活性预测中仍然非常有效。更大的模型在低数据环境下为SAR解释和推理增加了价值，但预测性能取决于模型、任务和验证场景之间的契合，而不仅仅取决于规模。

## Abstract
The rapid growth of molecular foundation models and large language models has encouraged a scale centred view of AI in drug discovery, in which larger pretrained models are expected to supersede compact cheminformatics models and graph neural networks (GNNs) trained for individual tasks. We test this assumption across 26 endpoints for molecular properties, toxicity, safety liabilities and biological activity, grouped into ADME, toxicity and bioactivity classes. The benchmark contains 78 endpoint and split entries spanning random, Murcko scaffold and structure separated 5-fold CV. Ordered from easiest to hardest, these splits approximate retrospective evaluation on a closed library, scaffold expansion in hit to lead, and library expansion on novel chemotypes. Each entry includes ML, GNN, pretrained molecular sequence and LLM based SAR families. Across 156 fold mean comparisons, classical ML such as RF(ECFP4) and ExtraTrees(RDKit) win 116, GNNs such as GIN and Ligandformer win 25, pretrained sequence models such as MoLFormer and ChemBERTa2 win 12, and LLM based SAR baselines win three. ML dominates random split interpolation but loses part of this advantage under harder splits; GNN and sequence models also decline but gain relative ground, whereas LLM based SAR is weaker in absolute terms yet less sensitive to the split axis. Paired bootstrap analyses support family level trends more strongly than individual model rankings. SAR knowledge derived from training folds improves many GPT5.5-SAR and Opus4.7-SAR metrics but does not make rule based reasoning a universal substitute for supervised predictors. Compact specialized models remain highly effective for molecular property and activity prediction. Larger models add value for SAR interpretation and reasoning in low data settings, but predictive performance depends on the fit among model, task and validation scenario, not on scale alone.