---
title: Automating Biomedical Knowledge Graph Construction For Context-Aware Scientific Inference
title_zh: 自动化构建生物医学知识图谱以实现上下文感知的科学推理
authors: "Zheng, Y., Liu, W., Zeng, B., Feng, Y., Du, X., Zhou, L., Li, Y."
date: 2026-08-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.01.14.699420v4.full.pdf"
tags: ["query:ar"]
score: 6.0
evidence: 自动化生物医学知识图谱构建以支撑科学推断，为自主研究提供使能工具
tldr: 生物医学交互随生理状态动态变化，现有抽取方法简化为上下文无关的二元关联，造成语义损失和矛盾证据。为此提出AutoBioKG，利用复合三元组编码环境条件和实体属性，并基于开放信息抽取模型与自训练伪标签构建上下文感知知识图谱。在DDI、ChemProt和BioRED零样本F1上均达最高，超基线3.6-17.8个百分点；BioASQ问答中尤其擅长细粒度查询。该框架可将非结构化文献转化为结构化、可扩展的上下文感知知识。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有抽取方法将动态生物医学机制简化为上下文无关的二元关联，造成语义丢失和矛盾证据。
method: 提出AutoBioKG，用复合三元组编码环境条件与实体属性，结合开放信息抽取和自训练伪标签构建上下文感知图谱。
result: 在DDI、ChemProt、BioRED零样本F1最高，超基线3.6-17.8个百分点；BioASQ问答中细粒度问题表现更优。
conclusion: AutoBioKG可扩展地将非结构化文献转化为结构化、上下文感知的生物医学知识，支持科学推理。
---

## 摘要
生物医学相互作用本质上是动态的，常常在特定生理状态下发生变化甚至逆转。然而，现有的抽取方法将这些复杂机制简化为与上下文无关的二元关联，导致语义丢失和矛盾证据。在此，我们提出AutoBioKG，一个端到端框架，通过利用复合三元组编码环境条件和实体属性以及核心关系来构建上下文感知的知识图谱。该框架基于在BioOpenIE上训练并进一步通过来自未标注文献的伪标签进行自训练优化的开放信息抽取模型，展现出广泛的泛化能力。值得注意的是，AutoBioKG在DDI、ChemProt和BioRED上取得了最高的零样本F1分数，比每个基准上表现最佳的基线高出3.6至17.8个百分点。此外，在BioASQ生物医学问答评估中，AutoBioKG生成的图谱在是/否、事实型和非正式列表问题上优于现有方法，尤其是在需要细粒度上下文信息的查询上。这些结果共同支持AutoBioKG作为一个可扩展的框架，用于将非结构化文献转化为结构化、上下文感知的生物医学知识。

## Abstract
Biomedical interactions are inherently dynamic, often shifting or even reversing under specific physiological states. However, existing extraction methods simplify these complex mechanisms into context-agnostic binary associations, resulting in semantic loss and contradictory evidence. Here, we present AutoBioKG, an end-to-end framework that constructs context-aware knowledge graphs by leveraging composite triples to encode environmental conditions and entity attributes alongside core relationships. Powered by an open information extraction model trained on BioOpenIE and further refined through self-training with pseudo-labels from unlabeled literature, the framework exhibits broad generalization. Notably, AutoBioKG achieved the highest zero-shot F1 across DDI, ChemProt, and BioRED, outperforming the best-performing baseline on each benchmark by 3.6-17.8 percentage points. Furthermore, AutoBioKG-derived graphs outperformed existing approaches on yes/no, factoid, and list questions in the BioASQ biomedical question-answering evaluation, particularly for queries requiring fine-grained contextual information. Together, these results support AutoBioKG as a scalable framework for transforming unstructured literature into structured, context-aware biomedical knowledge.