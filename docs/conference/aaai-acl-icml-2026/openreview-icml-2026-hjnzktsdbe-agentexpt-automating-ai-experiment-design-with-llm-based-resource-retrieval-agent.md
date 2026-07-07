---
title: "AgentExpt: Automating AI Experiment Design with LLM-based Resource Retrieval Agent"
title_zh: AgentExpt：利用基于LLM的资源检索智能体自动化AI实验设计
authors: "Yu Li, Lehui Li, Lin Chen, Qingmin Liao, Fengli Xu, Yong Li"
date: 2026-04-30
pdf: "https://openreview.net/pdf/c709129daec7922ae2860586823c282d79f1a387.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 利用LLM智能体自动化AI实验设计，属于自主研究核心任务
tldr: "该论文提出AgentExpt，一个基于LLM的资源检索智能体，用于自动化AI实验设计中的基线和数据集选择。它构建了包含108,825篇已接收论文及其使用基线和数据集的大规模知识库，并在此基础上进行智能推荐。该系统直接支持自主研究中的关键环节——实验设计，减轻了研究人员手动选择的负担，提高了实验的可比性和有效性。"
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 实验设计中基线和数据集选择至关重要且日益困难。
method: 构建大规模知识库链接论文与使用资源，并设计推荐框架AgentExpt。
result: 在推荐准确性上表现良好，能够辅助研究人员快速做出合适选择。
conclusion: 该工作为自主实验设计提供了有效工具，推动自动化研究流程。
---

## Abstract
In modern AI research, baseline and dataset selection is a high-stakes decision in experimental design.
It operationalizes a research idea into a concrete evaluation protocol and largely determines the validity and comparability of empirical conclusions.
However, making appropriate choices is increasingly difficult as baselines and datasets proliferate, while suitability is inherently context-dependent and rarely captured by baseline and dataset metadata.
To address these challenges, we present \textbf{AgentExpt}, a comprehensive framework for baseline and dataset recommendation.
We first curate a large-scale, high-quality knowledge base that links 108{,}825 accepted papers to their used baselines and datasets. 
Based on this resource, we design a \textit{collective perception-enhanced retriever} that represents each baseline or dataset by integrating first-person self-descriptions with third-person citation contexts, thereby effectively positioning them within the scholarly network. 
We further design a \textit{reasoning-augmented reranker} that encodes baseline-dataset interaction chains as a reasoning prior to fine-tune an LLM, producing refined rankings with interpretable justifications.
Experiments show that our framework outperforms the strongest baseline, with average gains of +5.85\% in Recall@20 and +7.90\% in HitRate@10, and ablation studies confirm the effectiveness of our designed components.
Overall, AgentExpt advances the efficient and reliable automation of experimental design. 
Our code is available at \url{https://anonymous.4open.science/r/Agentexpt-DD3E}.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在人工智能研究中，实验设计的关键环节——基线和数据集的选择——变得越来越困难。随着新模型和数据集层出不穷，研究人员需要手动筛选大量候选，而候选的适用性高度依赖研究上下文，且现有元数据无法体现这种上下文依赖。这导致实验设计的效率低下，且容易影响研究结论的可比性和有效性。
- **研究动机**：为了解决这一瓶颈，作者提出利用大规模知识库结合LLM智能体，自动化推荐合适的基线和数据集，从而辅助研究人员快速做出科学、合理的实验设计决策。
- **整体含义**：该工作直接支持自主研究中的核心实验设计环节，有助于提升AI研究的可重复性和效率，推动自动化研究流程。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个包含已接收论文与其所用基线和数据集对应关系的大规模知识库，并设计基于LLM的检索与排序框架（AgentExpt），实现上下文感知的基线和数据集推荐。
- **关键组件**：
  - **大规模知识库**：从108,825篇已接收论文中，提取每篇论文使用的具体基线和数据集，形成“论文-使用资源”的链接知识库。
  - **集体感知增强检索器（Collective Perception-enhanced Retriever）**：对每个基线或数据集，融合第一人称的自我描述（如官方论文摘要）与第三人称的引用上下文（其他论文中的描述），从而在学术网络中有效定位该资源的语义角色。
  - **推理增强重排序器（Reasoning-augmented Reranker）**：将基线-数据集交互链（即一篇论文中同时使用的基线和数据集组合）编码为推理先验，用于微调一个LLM，使排序结果附带可解释的理由，提升推荐的可信度。
- **算法流程**（文字说明）：
  1. **知识库构建**：从大规模论文集合中抽取每篇论文引用的基线方法、使用的数据集，建立三元组（论文, 基线, 数据集）。
  2. **检索阶段**：给定一个研究问题或描述，使用集体感知增强检索器，从知识库中召回一组候选基线和数据集。
  3. **重排序阶段**：使用推理增强重排序器，对候选列表进行重新排序，输出带解释的最终推荐。

### 3. 实验设计：数据集、benchmark、对比方法

- **数据集/场景**：论文使用自己构建的大规模知识库（108,825篇论文）作为实验基础。具体评测场景并未在摘要中详述，但可能包括对基线和数据集推荐任务的准确率、召回率等指标。
- **Benchmark**：未明确指定外部公共基准，但使用了Recall@20和HitRate@10作为主要评估指标。
- **对比方法**：与最强基线（baseline）进行了比较。摘要指出框架在Recall@20上平均提升+5.85%，在HitRate@10上平均提升+7.90%。但未列出具体对比方法名称（如传统检索模型、未使用知识库增强的LLM等），需要查看全文才能得知。

### 4. 资源与算力

- **文中未明确说明**：在提供的摘要和元数据中，没有提及使用的GPU型号、数量、训练时长等具体算力信息。可能原文实验部分有提及，但这里无法获取。暂记为：**文中未明确报告具体算力消耗**。

### 5. 实验数量与充分性

- **实验数量**：摘要仅报告了整体性能提升及消融实验结果（消融实验确认了各组件的有效性），但没有给出具体的实验组数（如在不同子集、不同任务上重复实验的次数）。可能原文包含更多实验（如对不同领域、不同规模知识库的测试），但需查阅全文。
- **充分性评价**：基于摘要，实验展示了主要指标上的提升，并进行了消融研究，验证了每个组件的贡献。但未提及跨领域泛化测试、对不同LLM基座的鲁棒性测试等。总体而言，实验设置合理，但全面性有限。

### 6. 论文的主要结论与发现

- **主要结论**：AgentExpt框架在基线和数据集推荐任务上显著优于最强基线，证明了利用大规模知识库结合基于LLM的检索-重排序机制能够有效辅助AI实验设计。
- **具体发现**：
  - 集体感知增强检索器通过融合自述和引用上下文，能更精准地定位资源。
  - 推理增强重排序器通过编码交互链，提升了排序的准确性和可解释性。
  - 消融实验确认了各设计组件的必要性。

### 7. 优点

- **方法创新**：首次将大规模“论文-使用资源”知识库与LLM结合，实现上下文感知的基线和数据集推荐，填补了自动化实验设计的一个关键空白。
- **可解释性**：重排序器提供可解释的理由，有助于研究人员理解推荐依据。
- **实用性**：直接减轻了研究人员的搜索负担，提升实验设计的效率与质量。
- **社区贡献**：公开了代码，便于复现和扩展。

### 8. 不足与局限

- **实验覆盖有限**：只评估了推荐准确率，未考虑推荐后对实际实验设计效果（如最终论文质量、公平性）的长期影响。
- **知识库偏差风险**：知识库仅包含已接收论文，可能存在发表偏差（如更偏好热门方法），且未包含未被引用的新方法或新兴领域，可能导致推荐结果偏向主流，忽略创新性选择。
- **应用限制**：框架依赖预先构建的知识库，对于全新研究领域或缺少论文积累的细分方向，推荐效果可能下降。
- **未说明算力需求**：未提供资源消耗，难以评估实际部署成本。

（完）
