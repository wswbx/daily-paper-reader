---
title: "ChatDIA: A zero-shot large language model workflow for targeted analysis of data-independent acquisition mass spectrometry data"
title_zh: ChatDIA：一种用于数据非依赖采集质谱数据靶向分析的零样本大语言模型工作流程
authors: "Li, J., Charkow, J., Gao, M., Rost, H."
date: 2026-05-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.11.705360v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 7.0
evidence: 零样本大模型工作流用于靶向DIA蛋白质组学分析
tldr: "ChatDIA是一种基于零样本大语言模型的工作流，用于靶向分析数据非依赖性采集（DIA）质谱数据，通过显式推理决策框架自动识别肽段并支持自然语言交互。在专家注释的化脓性链球菌DIA基准数据集上，ChatDIA达到96.9%的准确率，与领域特定软件DIA-NN相当；在单细胞HEK-293T DIA蛋白质组学数据集中，其风险覆盖曲线下面积更低（0.06 vs. 0.12），在1%和5%假发现率下分别鉴定出38.75%和46.25%的库肽段。结果表明零样本大语言模型推理能自动化核心靶向DIA决策，并提供可解释的理由，支持交互式验证和数据探索。"
source: biorxiv
selection_source: fresh_fetch
motivation: DIA蛋白质组学分析面临复杂谱图和色谱干扰，现有方法依赖领域特定模型，缺乏透明性和交互性。
method: 提出ChatDIA，利用零样本大语言模型直接推理提取离子色谱图，生成人类可理解的决策理由。
result: "在基准数据集上准确率96.9%，在单细胞数据集中鉴定性能优于DIA-NN，且风险覆盖率更低。"
conclusion: 零样本大语言模型推理可自动化DIA决策，提供可解释、可交互的分析框架，推动蛋白质组学计算分析的通用性和可解释性。
---

## 摘要
数据非依赖采集（DIA）蛋白质组学能够实现可重复的大规模蛋白质鉴定和定量，但由于高度复杂的串联质谱图和色谱干扰，其分析仍然具有挑战性，尤其是在低信噪比的单细胞蛋白质组学中。在此，我们介绍ChatDIA，这是一种基于显式推理决策框架、用于靶向DIA分析的零样本大语言模型（LLM）工作流程。ChatDIA可自动进行肽段鉴定，并支持与DIA数据的自然语言交互。与依赖领域特定模型的专用DIA软件不同，ChatDIA在零样本设置中使用通用LLM，直接对提取的离子色谱图进行推理，并为每个决策生成人类可解释的理由。在一个经过专家注释的化脓性链球菌DIA基准数据集上，ChatDIA实现了96.9%的准确率，与领域最先进的软件DIA-NN（95.5%）相当。在一个具有挑战性的单细胞HEK-293T DIA蛋白质组学数据集中，ChatDIA进一步展现了卓越性能，其风险覆盖率曲线下面积低于DIA-NN（0.06 vs. 0.12），在1%和5%假发现率下分别鉴定出38.75%和46.25%的文库肽段，而DIA-NN为16.25%和48%。这些结果共同表明，零样本LLM推理能够竞争性地自动化核心靶向DIA决策，同时提供透明、可检查的理由，从而在噪声蛋白质组学应用中实现对话式、交互式的验证和数据探索。更广泛地，ChatDIA展示了基于推理的AI系统如何超越预测，生成基于证据的决策，为蛋白质组学中更通用和可解释的计算分析奠定了基础。

## Abstract
Data-independent acquisition (DIA) proteomics enables reproducible, large-scale protein identification and quantification but remains challenging to analyze due to highly complex MS/MS spectra and chromatographic interference, particularly in low signal-to-noise single-cell proteomics. Here, we introduce ChatDIA, a zero-shot large language model (LLM)-based workflow for targeted DIA analysis that operates through an explicit reasoning-based decision framework. ChatDIA performs automated peptide identification and supports natural-language interaction with DIA data. Unlike purpose-built DIA software that relies on domain-specific models, ChatDIA employs general-purpose LLMs in a zero-shot setting to reason directly over extracted ion chromatograms and generate human-interpretable rationales for each decision. On an expert-annotated Streptococcus pyogenes DIA benchmark dataset, ChatDIA achieved 96.9% accuracy, matching the domain-specific state-of-the-art software DIA-NN (95.5%). In a challenging single-cell HEK-293T DIA proteomics dataset, ChatDIA further demonstrated excellent performance, achieving a lower risk-coverage area under the curve than DIA-NN (0.06 vs. 0.12) and identifying 38.75% and 46.25% of library peptides at 1% and 5% false discovery rate, respectively, compared with 16.25% and 48% for DIA-NN. Together, these results demonstrate that zero-shot LLM reasoning can competitively automate core targeted DIA decision-making while providing transparent, inspectable rationales that enable conversational, interactive validation and data exploration in noisy proteomics applications. More broadly, ChatDIA illustrates how reasoning-based AI systems can move beyond prediction to generate evidence-based decisions, offering a foundation for more general and interpretable computational analysis in proteomics.