---
title: "Cosine Similarity Conflates Clinically Distinct Cancer Variants: A Case for Typed-Graph Retrieval in Precision Oncology Decision Support"
title_zh: 余弦相似度混淆了临床不同的癌症变异：精准肿瘤学决策支持中类型图检索的案例
authors: "Khan, U. A."
date: 2026-05-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.723102v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 7.0
evidence: 通过类型化图检索改进知识发现
tldr: "本文研究检索增强生成（RAG）在肿瘤精准决策中的应用，发现基于余弦相似度的向量检索会混淆临床不同的癌症变异（如EGFR L858R和T790M），而类型图检索通过将每个变异作为离散节点保留变异身份。实验表明，生物医学嵌入模型导致100%的临床不同变异对高度相似（≥0.95），而类型图结合归一化层可实现零错误检索。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有RAG系统使用余弦相似度检索，可能混淆临床意义不同的癌症变异，导致治疗建议错误。
method: 对比9对临床不同的癌症变异，使用三种嵌入模型和多种文本格式计算余弦相似度，并设计类型图检索管道。
result: "生物医学嵌入模型导致100%的临床不同变异对余弦相似度≥0.95，而类型图检索结合归一化层实现零错误检索。"
conclusion: 类型图检索或带严格变异ID护栏的向量检索应作为变异级临床决策支持的基础方法。
---

## 摘要
检索增强生成（RAG）越来越多地应用于肿瘤学临床决策支持，其中治疗选择取决于从NGS报告中识别患者的特定体细胞变异，并将其与证据分级治疗选项相匹配。大多数RAG系统基础的向量检索使用文本嵌入上的余弦相似度，这是一种针对语言邻近性而非实体级身份优化的架构。我们假设基于余弦相似度的检索以临床相关的比率混淆了临床不同的癌症变异，而一种类型图方法（其中每个变异是一个离散节点）通过构造保留了变异级别的身份。

我们评估了9个具有不同FDA批准治疗适应症的癌症变异对，变异身份由CIViC临床变异证据数据库和主要临床文献提供。这些变异对涵盖BRAF、EGFR、KRAS、ERBB2、PIK3CA和NTRK1，包括经典的EGFR L858R vs T790M敏感性vs耐药性对，以及KRAS G12C vs G12D（只有G12C有FDA批准的靶向治疗）。我们计算了三个开源嵌入模型（PubMedBERT、MedCPT、BGE-large-en-v1.5）和三种文本格式下的成对余弦相似度，并在本次修订中增加了模板匹配的阴性对照、形式分离度量、变异特异性长文本、语料库级排序检索、精确ID防护基线以及端到端类型图管线。

在中等格式（基因+变异+肿瘤类型）下，100%的临床不同变异对（9/9）在两种生物医学编码器（PubMedBERT、MedCPT）下余弦相似度≥0.95（精确二项式95% CI [66.4%, 100%]）；通用编码器（BGE-large-en-v1.5）混淆了11%。生物医学预训练编码器比通用编码器表现更差，而不是更好。模板匹配但生物学无关的阴性对照得分低于临床不同对，证实高相似度是真正的混淆而非模板伪影，并且等效表示的正例无法通过余弦阈值与临床不同对区分（中等格式ROC-AUC ≤ 0.54，生物医学编码器低于0.5）。在52个文档的语料库级排序检索中，生物医学编码器下错误的配对变异出现在前5名的概率为75%至100%。在余弦检索中添加精确变异ID防护，并通过端到端类型图管线路由检索，均将错误变异检索减少到零。我们认为，在将变异字符串规范化为规范节点的归一化层条件下，类型图检索或结合严格变异ID防护的向量检索应成为变异级临床决策支持的默认基础。我们在相同的九对基准上端到端经验验证了类型图基线，展示了95.8%的归一化准确率和0%的错误变异检索率。

## Abstract
Retrieval-augmented generation (RAG) is increasingly applied to clinical decision support in oncology, where treatment selection depends on identifying a patients specific somatic variant from an NGS report and matching it to evidence-graded therapy options. The vector retrieval that underlies most RAG systems uses cosine similarity over text embeddings, an architecture optimized for linguistic proximity rather than entity-level identity. We hypothesize that cosine-similarity-based retrieval conflates clinically distinct cancer variants at clinically relevant rates, while a typed-graph approach in which each variant is a discrete node preserves variant-level identity by construction.

We evaluated 9 cancer variant pairs with differential FDA-approved therapy indications, variant identity informed by the CIViC clinical variant evidence database and primary clinical literature. The pairs span BRAF, EGFR, KRAS, ERBB2, PIK3CA, and NTRK1, including the canonical EGFR L858R vs T790M sensitivity-versus-resistance pair and KRAS G12C vs G12D (only G12C has an FDA-approved targeted therapy). We computed pairwise cosine similarity across three open-source embedding models (PubMedBERT, MedCPT, BGE-large-en-v1.5) and three text formats, and in this revision added template-matched negative controls, formal separation metrics, variant-specific long-format text, corpus-level ranked retrieval, an exact-ID guardrail baseline, and an end-to-end typed-graph pipeline.

Across the medium format (gene + variant + tumor type), 100% of clinically distinct variant pairs (9/9) had cosine similarity [&ge;] 0.95 under both biomedical encoders (PubMedBERT, MedCPT; exact binomial 95% CI [66.4%, 100%]); the general-purpose encoder (BGE-large-en-v1.5) conflated 11%. The biomedically pre-trained encoders performed worse, not better, than the general-purpose encoder. Template-matched but biologically unrelated negative controls scored lower than the clinically distinct pairs, confirming the high similarities are genuine conflation and not a template artifact, and equivalent-notation positives were not separable from clinically distinct pairs by a cosine threshold (medium-format ROC-AUC [&le;] 0.54, below 0.5 for the biomedical encoders). In corpus-level ranked retrieval over a 52-document corpus, the wrong paired variant appeared in the top 5 for 75% to 100% of queries under the biomedical encoders. Adding an exact variant-ID guardrail to cosine retrieval, and routing retrieval through an end-to-end typed-graph pipeline, both reduced wrong-variant retrieval to zero. We argue that, conditional on a normalization layer that resolves variant strings to canonical nodes, typed-graph retrieval, or vector retrieval coupled with strict variant-ID guardrails, should be the default substrate for variant-level clinical decision support. We empirically validate the typed-graph baseline end-to-end on the same nine-pair benchmark, demonstrating 95.8% normalization accuracy and a 0% wrong-variant retrieval rate.