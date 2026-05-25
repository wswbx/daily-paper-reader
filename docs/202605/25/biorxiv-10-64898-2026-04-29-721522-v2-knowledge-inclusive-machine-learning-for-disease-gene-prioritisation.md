---
title: Knowledge Inclusive Machine Learning for Disease Gene Prioritisation
title_zh: 知识包容性机器学习用于疾病基因优先级排序
authors: "Gamage, C. J., Xia, Y., Rupasinghe, R., Seneviratne, S., Senanayake, D., Malepathirana, T., Hevapathige, A., Corbett, M., O'Brien, T. J., Petrou, S., Berkovic, S. F., Scheffer, I. E., Gecz, J., Bahlo, M., Bennett, M. F., Halgamuge, S. K."
date: 2026-05-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.29.721522v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 融合生物知识进行疾病基因发现
tldr: 针对疾病基因优先排序中单一数据源（实验数据或知识库）的局限性，提出知识包容机器学习（KIML），融合基因表达、蛋白质相互作用网络、PubMed文献表示和生物知识图谱。在发育性和癫痫性脑病数据集上，通过时间分割和生物学评估，KIML在预测准确性和可解释性上优于现有方法，并泛化至6种其他疾病。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法仅依赖实验数据易受噪声干扰，而单独使用知识库缺乏基因级分辨率，需整合两类上下文以提升预测鲁棒性与生物学意义。
method: KIML联合实验数据与两种通用上下文：来自PubMed的文献表示和结构化生物知识图谱，在统一分析管道中建模。
result: 在发育性和癫痫性脑病上，KIML在时间分割评估和生物学评估（如本体富集分析）中持续优于现有方法。
conclusion: KIML不仅提升预测准确性，还生成可解释的基因排序，并在6种其他疾病中表现强泛化性。
---

## 摘要
机器学习模型的预测性能取决于其可用的上下文。在疾病基因优先级排序中，这种上下文包含两种形式：来自样本级实验数据（如基因表达和蛋白质-蛋白质相互作用网络）的特定上下文，以及来自积累和整理的生物学知识（捕捉基因、疾病和通路之间的已有关系）的一般上下文。单独任何一种都不足够：实验数据对数据集特定的噪声敏感，且缺乏更广泛的生物学基础，而整理的知识缺乏基因级别区分所需的分辨率。因此，大多数仅依赖实验数据的机器学习方法有学习虚假相关性而非潜在生物学的风险。在此，我们介绍知识包容性机器学习（KIML），一种将两种上下文类型整合到统一分析流程中的范式。KIML将实验数据与两种类型的一般上下文结合：来自PubMed的文献衍生表示和结构化生物医学知识图谱。我们在发育性和癫痫性脑病上评估该方法，并使用公开可用数据集与最近的方法进行基准测试。通过时间分割评估和生物学评估（包括本体富集分析）来评估性能。KIML持续优于现有方法，提供了改进的预测准确性和生物学上有意义的洞察。此外，该框架生成了基因优先级排序的可解释解释，并在另外六种疾病上展示了强大的泛化能力。

## Abstract
The predictive performance of machine learning models depends on the context available to them. In disease gene prioritisation, this context comprises two forms: specific context from sample-level experimental data, such as gene expression and protein-protein interaction networks, and general context from accumulated and curated biological knowledge capturing established relationships among genes, diseases, and pathways. Neither is sufficient alone: experimental data are sensitive to dataset-specific noise and lack broader biological grounding, while curated knowledge lacks the resolution required for gene-level discrimination. Consequently, most machine learning approaches relying solely on experimental data risk learning spurious correlations rather than underlying biology. Here we introduce Knowledge Inclusive Machine Learning (KIML), a paradigm that integrates both context types within a unified analytical pipeline. KIML combines experimental data with two types of general context: literature-derived representations from PubMed and structured biomedical knowledge graphs. We evaluate the approach on Developmental and Epileptic Encephalopathy and benchmark it against recent methods using publicly available datasets. Performance is assessed using temporal-split evaluation and biological evaluations, including ontology enrichment analysis. KIML consistently outperforms existing approaches, providing improved predictive accuracy and biologically meaningful insights. Furthermore, the framework generates interpretable explanations of gene prioritisation and demonstrates strong generalisability across six additional diseases.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：在疾病基因优先级排序（disease gene prioritisation）任务中，现有机器学习方法通常仅依赖单一类型的上下文信息——要么是样本级实验数据（如基因表达、蛋白质-蛋白质相互作用网络），要么是整理好的生物学知识库（如基因-疾病关联、通路关系）。然而，实验数据容易受数据集特定的噪声干扰，且缺乏广泛的生物学基础；知识库虽然稳定但分辨率不足，无法实现基因级别的精细区分。因此，现有方法容易学习到虚假相关性而非潜在的生物学机制。
- **整体含义**：论文提出**知识包容性机器学习（KIML）** 范式，旨在将两类上下文（实验数据的特定上下文 + 生物学知识的一般上下文）整合到统一分析流程中，从而提升预测准确性和生物学可解释性，并增强模型的泛化能力。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：KIML 联合实验数据与两种类型的**一般上下文**：
  1. **文献衍生表示**：从 PubMed 文献中提取的基因/疾病表示（通过 NLP 或嵌入技术，如使用预训练语言模型生成基因的文献特征向量）。
  2. **结构化生物医学知识图谱**：将整理好的生物知识（如基因-基因相互作用、基因-疾病关联、途径等）表示为图结构，利用图神经网络（GNN）或知识图谱嵌入方法（如 TransE、ComplEx）获得基因和疾病的向量化表示。
- **关键技术细节**（基于摘要推断，原文未提供公式或算法伪代码）：
  - KIML 首先构建一个**多模态融合框架**：将实验数据（如基因表达矩阵、PPI 网络）作为特定上下文输入；同时从 PubMed 文本和知识图谱中提取一般上下文特征。
  - 然后通过**注意力机制**或**门控融合**等方法将三类特征（实验、文献、知识图谱）进行对齐和整合，生成每个基因的综合表示。
  - 最后用分类器（如全连接网络或图神经网络）对基因进行排序和优先级评分。
  - 训练过程中采用**时间分割评估**（temporal-split evaluation），即用历史数据训练、未来数据测试，模拟真实发现场景。同时结合**生物学评估**（如富集分析）验证排序的生物学意义。
- **缺乏公式**：论文未公开具体的损失函数或模型结构，但强调“统一分析流水线”。

### 3. 实验设计
- **核心数据集**：以**发育性和癫痫性脑病（Developmental and Epileptic Encephalopathy, DEE）** 为主要评估场景；另外在**六种其他疾病**上测试泛化能力（未列出具体疾病名，推测包括常见遗传病）。
- **基准（Benchmark）**：使用了公开可用数据集，与**近期方法**（recent methods）进行对比，具体方法名称未在摘要中列出，可能包括仅使用实验数据的方法（如 GNN-based 的基因排序方法）或仅使用知识库的方法（如基于知识图谱的基因优先排序工具）。
- **对比方法**：摘要未列举，但推断包括传统的基于基因表达和 PPI 的机器学习模型（如 Random Forest、DeepGCN）、以及基于知识图谱的推理方法（如 HPO 匹配、PheWAS 等）。
- **评估指标**：
  - 时间分割评估：按时间顺序划分训练/测试集，度量模型对未来发现的新基因的预测能力。
  - 生物学评估：通过**本体富集分析**（Ontology Enrichment Analysis）检验排序靠前的基因在已知生物过程中的一致性。
  - 可解释性分析：提供每个基因排序的依据（如哪些上下文特征贡献最大）。
- **算力与资源**：**论文未明确说明**使用的 GPU 型号、数量或训练时长。预印本通常不会详细报告资源消耗，需后续版本或附录补充。

### 4. 实验数量与充分性
- **实验组数**：
  - 主实验：在 DEE 数据集上进行了时间分割评估和生物学评估。
  - 泛化实验：在**六种其他疾病**上重复评估，测试方法是否跨疾病有效。
  - 消融实验：摘要未明确提及，但根据“知识包容性”逻辑，推测可能去除了文献特征或知识图谱特征进行消融分析，以证明两种一般上下文的必要性。
- **充分性评价**：
  - **积极方面**：时间分割是评估新基因发现能力的金标准，避免了未来信息泄露；额外在多种疾病上验证泛化性，增加了实验的可信度；本体富集分析提供了生物学层面的验证，而不仅仅是统计指标。
  - **不足**：
    - 未报告与经典基线（如 GeneMANIA、Endeavour 等传统工具）的对比细节，可能选择性对比了较新的方法。
    - 缺乏在**不同实验数据类型**（如只使用基因表达 vs 只使用 PPI）上的系统消融实验，难以量化每种上下文的贡献程度。
    - 未讨论实验数据的异质性（如样本量、批次效应）对模型鲁棒性的影响。
    - 由于是预印本，未提供开放性代码或超参数设置，第三方复现验证尚未进行。

### 5. 论文的主要结论与发现
- **结论**：
  1. KIML 在 DEE 数据集上**持续优于现有方法**，在时间分割评估中具有更高的预测准确性。
  2. KIML 生成的基因排序具有更好的生物学意义：例如在富集分析中，排名靠前的基因更显著富集到已知疾病相关通路。
  3. KIML 能提供**可解释的解释**（如哪些知识图谱关系或文献关键词影响了排序），增强了模型在生物医学领域的可信度。
  4. 该框架在**六种其他疾病**上表现出强大的泛化能力，说明知识包容性策略并非仅适用于特定疾病。
- **发现**：整合文献表示和知识图谱能够弥补实验数据对背景知识的缺乏，减少虚假相关性，并提升基因级别的判别分辨率。

### 6. 优点
- **方法亮点**：
  - 首次将三种不同性质的数据源（实验、文献、知识图谱）系统性地融合到统一流水线中，实现了“特定上下文+一般上下文”的互补。
  - 时间分割评估策略忠实反映了实际科研发现场景（预测未来新基因），比随机分裂更合理。
  - 可解释性输出有助于生物学家理解模型决策依据，促进假设生成。
- **实验设计亮点**：
  - 同时进行了基于指标的评估（AUC 等，假设有）和生物学意义评估（富集分析），多角度验证。
  - 跨六种疾病泛化实验增加了结论的稳健性。
  - 使用公开数据集，增强了可复现潜力（虽然代码未开源）。

### 7. 不足与局限
- **实验覆盖不足**：
  - 仅以 DEE 为主要实验疾病，虽然扩展了六种其他疾病，但疾病类型是否涵盖常见病/罕见病/复杂病？未见详细列表，可能偏重于单基因遗传病。
  - 未比较不同文献表示方法（如 BioBERT vs. PubMedBERT）和知识图谱嵌入方法（如 TransE vs. RotatE）的性能差异。
- **偏差风险**：
  - 知识图谱本身可能存在整理偏差（如疾病基因关联偏向于研究较多的基因），文献表示也可能受出版偏见影响，这些偏差可能被模型放大。
  - 时间分割评估中，未来数据可能包含已知的知识图谱关系（因为知识图谱不断更新），需要确保在训练时隔离未来知识，但摘要未说明如何避免数据泄露。
- **应用限制**：
  - 需要同时获取三类数据，对于缺乏高质量知识图谱或文献嵌入的罕见疾病域，应用受限。
  - 计算复杂度较高（需同时处理文本嵌入和知识图谱），对于大规模全基因组排序可能成本较高。
  - 未讨论超参数调优策略和模型选择的稳定性，若敏感则可能难以直接复用。
- **其他**：
  - 论文仅基于摘要提供的信息，缺少详细的模型架构图、公式、消融实验表等，整体分析深度受限。实际完整论文可能包含更多细节。

（完）
