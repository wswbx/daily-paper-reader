---
title: Emergence of Biological Structural Discovery in General-Purpose Language Models
title_zh: 通用语言模型中生物结构发现的涌现
authors: "Wang, L."
date: 2026-07-09
pdf: "https://www.biorxiv.org/content/10.64898/2026.01.03.697478v2.full.pdf"
tags: ["query:ar"]
score: 6.0
evidence: 大语言模型用于生物结构发现属于自主研究
tldr: 传统观点认为生物学理解需要领域特定预训练，但本文发现通用语言模型具涌现的生物结构发现能力。仅靠英语语料预训练的小型GPT-2(124M)在严格控制的蛋白质同源性检测基准上零样本达到ROC-AUC 0.79，且从头训练的英语模型再现该结果。深层分析表明判别信号集中于第9层，包含模态无关的差异算子。这一发现挑战了领域预训练的必要性，揭示抽象语言结构可作为解码生物语法的认知先验。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1751, \"height\": 971}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1537, \"height\": 566}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1074, \"height\": 702}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 790, \"height\": 731}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 739, \"height\": 673}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 890, \"height\": 764}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1544, \"height\": 773}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 900, \"height\": 194}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1381, \"height\": 324}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-01-03-697478-v2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1553, \"height\": 283}]"
motivation: 挑战生物学理解需领域特定预训练的假设，探究通用语言模型是否无需生物数据就能进行结构发现。
method: 在BioPAWS基准上，用仅英语预训练的GPT-2(124M)零样本检测蛋白质同源性，并设置随机初始化、自训练等严格对照。
result: GPT-2零样本ROC-AUC达0.79，自训练模型达0.76，且判别信号定位到第9层，注意力分析显示差异算子。
conclusion: 语言预训练产生的抽象逻辑结构是解码生物序列语法的有效认知先验，无需领域数据即可迁移。
---

## 摘要
大型语言模型（LLM）正演变为科学发现引擎，但“生物学理解需要领域特定预训练”这一假设仍基本未被质疑。在此我们报告，通用LLM具备生物结构发现的涌现能力。在严格的、防捷径控制的评估下，仅通过英语释义辨别微调的小型GPT-2（124M）在防捷径控制的基准上以零样本方式检测蛋白质同源性，ROC-AUC为0.79。对照实验表明，该能力源自预训练而非架构：随机初始化的GPT-2表现接近随机（0.52）。为排除公开检查点可能被生物数据污染的可能性，我们仅使用英语网络语料从头训练自己的GPT-2；它重现了迁移效果（0.76），证明该效应完全源于语言预训练。基于网络的解释性揭示了深层结构同构性：判别信号集中在深层（第9层达0.97），注意力分析揭示了模态无关的“差异”算子。扩展到大规模指令调优模型进一步提升了性能，包括在远程同源性的“模糊区”，我们将其报告为探索性上限，因为这些模型的训练语料未公开。我们通过BioPAWS基准对这些任务进行了形式化。我们的受控结果——完全基于训练数据已知的模型获得——确立了从人类语言中提炼的抽象逻辑结构构成了解码生物语法的真实（尽管有限）认知先验。

## Abstract
Large language models (LLMs) are evolving into engines for scientific discovery, yet the assumption that biological understanding requires domain-specific pre-training remains largely unchallenged. Here we report that general-purpose LLMs possess an emergent capability for biological structural discovery. Under strict, shortcut-controlled evaluation, a small-scale GPT-2 (124M) fine-tuned solely on English paraphrase discrimination detects protein homology zero-shot at ROC-AUC 0.79 on a shortcut-controlled benchmark. Controls establish that the ability is conferred by pre-training, not architecture: a randomly initialized GPT-2 is at chance (0.52). To exclude the possibility that public checkpoints were contaminated with biological data, we train our own GPT-2 from scratch on an English-only web corpus; it reproduces the transfer (0.76), proving the effect arises from linguistic pre-training alone. Network-based interpretability reveals a deep structural isomorphism: the discriminative signal localizes to deep layers (0.97 at layer 9), and attention analysis surfaces modality-agnostic "difference" operators. Scaling to massive instruction-tuned models further improves performance, including in the remote-homology "twilight zone", which we report as an exploratory upper bound because those models training corpora are undisclosed. We formalize these tasks through the BioPAWS benchmark. Our controlled results--obtained entirely on models with known training data--establish that abstract logical structures distilled from human language constitute a genuine, if bounded, cognitive prior for decoding the syntax of biology.