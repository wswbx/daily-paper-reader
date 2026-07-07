---
title: "SciNet: Evaluating AI Agents in Relation-Aware Scientific Literature Retrieval"
title_zh: SciNet：评估AI智能体在关系感知科学文献检索中的表现
authors: "Chenyang Shao, Fengli Xu, Yong Li"
date: 2026-04-30
pdf: "https://openreview.net/pdf/f7951b13ddb995ee466f24f56eb86a2adfc833eb.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 关系感知科学文献检索中AI智能体的评估
tldr: 该论文指出现有检索智能体忽视论文间复杂关系网络（如印证、冲突、技术传承），提出SciNet数据集，用于评估关系感知的文献检索智能体。包含多种关系类型的检索任务，实验表明当前模型在关系理解上存在显著不足。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有检索智能体仅关注内容相似性，无法理解论文间关系网络。
method: 构建首个关系感知数据集SciNet，包含印证、冲突、技术传承等任务。
result: 实验揭示当前模型在关系感知检索中性能有限。
conclusion: SciNet推动了文献检索智能体向关系理解发展。
---

## Abstract
AI agents have seen widespread adoption in information retrieval for scientific research, giving rise to tools such as Deep Research. However, existing retrieval agents mainly rely on keyword- or embedding-based methods. While effective at capturing content-level similarities, they struggle to understand complex relational networks among scientific papers, such as identifying corroborating or conflicting studies and tracing technological lineages. This fundamental limitation often results in fragmented knowledge structures, misinterpreted research sentiment, and ineffective modeling of collective scientific progress. To address this limitation, we introduce **SciNet**, the first **Sci**entific **Net**work relation-aware dataset for information retrieval agents. Built on a meta-database of 269 million papers across 7 disciplines and containing 8,940 carefully designed tasks, SciNet systematically captures three levels of relational understanding: ego-centric retrieval of papers with novel knowledge structures, pairwise identification of scholarly relationships, and path-wise reconstruction of scientific evolution. Extensive evaluation of three categories of retrieval agents shows that their accuracy on relation-aware tasks often falls below 20%, highlighting a fundamental shortcoming of current retrieval paradigms. Importantly, in a downstream literature review application, agents empowered with SciNet achieve a 25.3% improvement in review quality, highlighting the critical value of relation-aware retrieval for deepening scientific insights. We publicly release SciNet at https://github.com/tsinghua-fib-lab/SciNet to support future research.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前AI智能体（如Deep Research）广泛用于科学文献检索，但它们主要依赖关键词匹配或嵌入相似度，只能捕捉内容层面的语义相似性，**无法理解论文之间复杂的结构关系**（例如：互相印证、观点冲突、技术传承等）。这种局限性导致检索结果呈现碎片化的知识结构，无法正确反映研究情感（如正面/负面引用），也难以有效建模科学进步的整体过程。
- **整体含义**：论文认为，真正的科学文献检索需要**关系感知**能力——不仅要找到“相关”论文，还要理解论文之间如何相互关联、如何构成知识网络。缺乏这种能力会限制AI智能体在辅助科研（如文献综述生成）中的深度和准确性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建第一个专门用于评估AI智能体**关系感知能力**的科学文献检索数据集——**SciNet**。通过设计多层次的检索任务，迫使智能体去理解论文间的学术关系网络，而不仅仅是内容相似性。
- **关键技术细节**：
  - **数据基础**：基于一个包含 **2.69亿篇论文** 的元数据库，覆盖 **7个学科领域**。
  - **任务设计**：共 **8,940个精心设计的任务**，按照关系理解复杂度分为三个层次：
    1. **自我中心检索（Ego-centric retrieval）**：针对一个给定论文，检索与其具有新颖知识结构关系的其他论文（例如：后续发展、颠覆性观点等）。
    2. **成对关系识别（Pairwise identification）**：判断两篇论文之间的具体学术关系类型（如：印证关系、冲突关系、技术传承关系）。
    3. **路径重建（Path-wise reconstruction）**：重建科学演化路径，例如从一个开创性工作出发，找出其技术传承链上的关键论文。
  - **关系标注**：所有任务基于论文间引文网络、文献计量学特征以及人工验证，确保关系标签的准确性。
- **算法流程**：论文未给出公式或伪代码，其方法论核心是**数据集构建与任务定义**。评估时，将不同检索智能体作为黑盒，输入任务要求（如“找出与论文A具有技术传承关系的论文”），输出结果，对比真实标注计算准确率。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集**：使用自建的**SciNet数据集**（8940个任务），并对不同类别的检索智能体进行测试。
- **Benchmark**：论文本身是提出一个评估基准，因此SciNet即为该领域的首个标准化benchmark。
- **对比方法**：论文提到评估了**三类检索智能体**（未在摘要中明确具体名称，推测包括：传统基于关键词的检索、纯嵌入向量检索、以及基于大语言模型的检索智能体）。此外，在**下游文献综述应用**中，将使用SciNet增强的智能体与未增强的智能体进行比较。
- **评估指标**：主要指标为**任务准确率**，以及下游任务中**文献综述质量**的提升比例。

## 4. 资源与算力

- 论文摘要及元数据中**未提及**任何关于计算资源的描述（如GPU型号、数量、训练时长、数据存储规模等）。因此无法总结具体算力信息。

## 5. 实验数量与充分性

- **实验数量**：主实验在 **8,940个任务** 上评估了三类智能体，每个任务对应一次检索判断。此外，包含一个下游文献综述应用实验，测量质量提升。
- **充分性**：
  - 任务数量较大且覆盖多种关系类型，具有一定的统计意义。
  - 但未提及**消融实验**（例如去除某类关系任务的影响）或**不同数据规模下的鲁棒性测试**。
  - 对比的方法仅限于三类，缺少更细粒度的模型变体比较。
  - 下游实验仅为一个文献综述应用，扩展性有限。
- **客观性**：论文公开了数据集（https://github.com/tsinghua-fib-lab/SciNet），有利于第三方重复验证，但当前摘要未提供详细的误差分析或统计显著性检验。

## 6. 论文的主要结论与发现

- **主要发现**：当前三类检索智能体在关系感知任务上的准确率**普遍低于20%**，表明现有检索范式在理解论文关系网络上存在根本性缺陷。
- **下游价值**：使用SciNet增强的智能体在文献综述质量上取得 **25.3%的提升**，证明关系感知检索对于深化科学洞察具有关键价值。
- **结论**：推动文献检索智能体从“内容匹配”向“关系理解”发展是必要的，SciNet数据集为这一方向提供了评估基础。

## 7. 优点：方法或实验设计上的亮点

- **首创性**：第一个专门针对**关系感知**的科学文献检索数据集，填补了现有基准的空白。
- **多层级任务设计**：从单篇论文的自我中心检索到双篇关系判别，再到路径重建，系统性地覆盖了不同复杂度的关系理解需求。
- **大规模、多学科覆盖**：基于2.69亿论文和7个学科，数据基础扎实，具有一定的代表性。
- **资源开放**：数据集已公开，便于社区使用和扩展。
- **下游验证**：通过文献综述应用的实际提升证明了关系感知的实用价值，增强了论文的说服力。

## 8. 不足与局限

- **实验局限性**：
  - 评估仅基于SciNet单一数据集，缺乏在已有标准检索基准（如MS MARCO、TREC等）上的对比实验，难以横向比较关系感知与常规检索的性能差异。
  - 未披露三类智能体的具体实现细节（如使用的语言模型、嵌入模型等），导致结果可复现性受限。
  - 缺少对关系标签质量的详细分析（如人工验证的一致性指标），可能存在标注偏差。
- **计算资源与效率**：未讨论训练或推理算力需求，无法评估该方法在实际部署中的成本。
- **应用限制**：
  - SciNet的构建基于引文网络，引文关系并不等同于真实的学术关系（可能遗漏隐含关联），覆盖范围有限。
  - 下游文献综述应用仅提及质量提升，未提供具体评价指标或用户研究，说服力仍显不足。
  - 当前版本的SciNet可能只支持英文论文，跨语言或多语种场景未涉及。

（完）
