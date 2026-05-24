---
title: "OmniCellAgent: An AI Scientist for Omic-Driven Scientific Discovery"
title_zh: OmniCellAgent：用于组学驱动科学发现的AI科学家
authors: "Huang, D., Li, H., Li, W., Zhang, H., Xu, T., Lu, Y., Fang, K., Xu, Z., Chen, J., Dickson, P., Sardiello, M., Buchser, W., Cooper, J. D., Cruchaga, C., Eghtesady, P., Li, G., Goedegebuure, P., DeNardo, D., Ding, L., Fields, R. C., Zhan, M., Miller, J. P., Province, M., Chen, Y., Payne, P., Li, F."
date: 2026-05-20
pdf: "https://www.biorxiv.org/content/10.1101/2025.07.31.667797v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 9.0
evidence: AI科学家用于组学科学发现
tldr: OmniCellAgent是一个基于大规模单细胞RNA-seq的多智能体AI框架，能自主检索、整合和分析疾病相关数据集，并结合先验知识和专家智能体生成结构化报告及数据驱动假设，减少组学发现障碍，加速精准医学假设生成。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有AI需用户手动定义疾病数据集，过程繁琐耗时，尤其对非计算研究人员不友好。
method: 构建多智能体框架，利用大规模scRNA-seq资源自主检索分析数据，整合生物医学先验知识智能体和领域专家智能体进行系统注释与下游解释。
result: 在多种疾病中成功识别相关数据集、优先排序生物学意义靶点并生成证据支持的假设。
conclusion: 多智能体AI系统能有效降低组学驱动发现的障碍，加速精准医学中的假设生成。
---

## 摘要
在生物医学科学发现中，识别相关的组学数据集并利用数据库和文献中的先验知识解释分析结果，对于产生新假说至关重要。尽管最近的AI代理支持自动化组学分析和文献检索，但它们通常需要用户预定义和策划疾病特定数据集，这一过程对于非计算研究人员而言仍然具有挑战性且耗时。为此，我们提出OmniCellAgent，一个基于大规模单细胞RNA测序（scRNA-seq）资源的多代理AI框架，能够自主检索、整合和分析跨组织与疾病状态的不同细胞类型相关的疾病与对照数据集。此外，OmniCellAgent整合了一个生物医学先验知识代理，用于利用策划数据库和文献进行系统靶点注释，以及针对下游高优先级靶点解释的领域专家代理。通过跨代理聚合证据，该框架生成结构化的分析报告和数据驱动的假说。我们在多种疾病场景下评估了OmniCellAgent，展示了其识别相关数据集、优先选择生物学意义靶点以及生成全面、有证据支持的假说的能力。我们的结果表明，多代理AI系统可以降低组学驱动发现的障碍，并加速精准医学中的假说生成。

## Abstract
In biomedical scientific discovery, identifying relevant omics datasets and interpreting analysis results using prior knowledge from databases and literature are essential for generating novel hypotheses. Although recent AI agents support automated omics analysis and literature retrieval, they typically require users to predefine and curate disease-specific datasets, which is a process that remains challenging and time-consuming, particularly for non-computational researchers. Herein we present OmniCellAgent, a multi-agent AI framework built on large-scale single-cell RNA sequencing (scRNA-seq) resources that autonomously retrieves, integrates and analyzes disease and control-related datasets of diverse cell types across tissues and conditions. Moreover, OmniCellAgent incorporates a biomedical prior knowledge agent for systematic target annotation using curated databases and literature, as well as domain-specific expert agents for downstream interpretation of high-priority targets. By aggregating evidence across agents, the framework generates structured analytical reports and data-driven hypotheses. We evaluate OmniCellAgent across multiple disease settings, demonstrating its ability to identify relevant datasets, prioritize biologically meaningful targets and produce comprehensive, evidence-supported hypotheses. Our results suggest that multi-agent AI systems can reduce barriers to omics-driven discovery and accelerate hypothesis generation in precision medicine.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：生物医学科学发现中，研究人员需要识别相关组学数据集并利用先验知识解释结果，从而生成新假设。然而，现有的AI代理虽然支持自动化组学分析和文献检索，但通常**要求用户预先定义和策划疾病特定数据集**，这一过程对非计算研究人员而言**既困难又耗时**，成为组学驱动发现的瓶颈。
- **整体意义**：本文提出OmniCellAgent，一个**基于大规模单细胞RNA测序（scRNA-seq）资源的多智能体AI框架**，能够**自主完成从数据检索、整合、分析到假设生成的完整流程**，从而**降低组学发现的技术门槛，加速精准医学中的假设生成**。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将组学驱动科学发现分解为多个子任务，构建**多智能体协作系统**，每个智能体负责特定环节，通过**跨智能体证据聚合**生成结构化报告和数据驱动的假设。
- **关键技术细节**：
  - **数据检索与整合智能体**：基于大规模scRNA-seq资源，**自动检索**跨组织和疾病状态的不同细胞类型的疾病与对照数据集，并进行整合。
  - **生物医学先验知识智能体**：利用策划数据库和文献，对分析出的靶点进行**系统性注释**（如基因功能、疾病关联等）。
  - **领域专家智能体**：针对下游高优先级靶点，进行**领域特定的解释**（如细胞类型特异性、信号通路等）。
  - **证据聚合机制**：将各智能体的输出汇总，生成**结构化分析报告**和**数据驱动的可检验假设**。

> 注：论文未提供具体算法或公式，上述描述基于摘要提取。

## 3. 实验设计：使用了哪些数据集/场景、benchmark及对比方法

- **使用场景**：在**多种疾病场景**下评估OmniCellAgent，但摘要中**未明确列出具体疾病名称或数据集来源**（可能涉及常见疾病如癌症、神经退行性疾病等，但无法确认）。
- **Benchmark**：**未提及任何标准benchmark**。评估标准为自身能力：识别相关数据集、优先选择生物学意义靶点、生成有证据支持的假设。
- **对比方法**：**未提及与其他方法（如现有AI代理、经典分析流程）进行定量对比**。实验主要展示框架本身的可行性与效果，缺乏直接的性能对比。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量、训练时长等算力信息。作为基于大型语言模型和多智能体调用的框架，可能依赖预训练基础模型（如LLM），但具体计算资源未披露。

## 5. 实验数量与充分性

- **实验数量**：摘要仅提及在“多种疾病场景”下评估，但**未给出具体实验次数**、涉及的数据集数目或消融实验设计。
- **充分性分析**：
  - **优点**：覆盖了不同疾病，体现了框架的泛化能力。
  - **不足**：
    - 缺少**消融实验**验证各智能体模块的贡献度。
    - 缺少**与基线方法的定量对比**（如人工分析耗时、假设准确性等），无法客观说明性能提升。
    - 评估指标较为**定性描述**（“识别”、“优先选择”、“生成”），缺乏可重复的量化指标（如召回率、精度、假设验证成功率等）。
  - **客观性/公平性**：由于缺乏对比实验，难以判断结论的稳健性。实验设计存在**偏差风险**（可能选择有利疾病场景展示）。

## 6. 论文的主要结论与发现

- 多智能体AI系统OmniCellAgent能够**自主完成从数据检索到假设生成的完整链条**，有效降低组学驱动发现的障碍。
- 在多种疾病场景中，该框架成功**识别了相关数据集**、**优先选择了具有生物学意义的靶点**，并生成了**全面且有证据支持的假设**。
- 结论：多智能体协作是**加速精准医学假设生成**的可行途径。

## 7. 优点：方法或实验设计上的亮点

- **自动化程度高**：无需用户手动定义疾病数据集，显著降低非计算研究者的使用门槛。
- **多智能体协作**：将先验知识（数据库、文献）与领域专家知识整合，提升解释的深度和可信度。
- **证据聚合**：跨智能体汇总证据，生成结构化的报告和可检验假设，具有实用价值。
- **聚焦关键瓶颈**：直接针对“数据检索与先验知识整合”这一组学发现的核心痛点，问题定义清晰。

## 8. 不足与局限

- **实验覆盖有限**：未公开具体疾病场景、数据集规模，且缺乏与现有方法的定量对比，影响可复现性和泛化性评估。
- **评估指标主观**：主要依靠定性描述，缺少假说验证或错误率分析等客观度量。
- **资源依赖未说明**：未提及基础模型的计算成本，可能隐含较高算力需求，实际部署存在门槛。
- **偏差风险**：仅展示成功案例，未报告失败情况或局限性分析（如数据多样性不足、先验知识库覆盖不全等）。
- **无消融研究**：各智能体模块的独立贡献未量化，难以判断框架设计的必要性。
- **应用限制**：框架目前专注于scRNA-seq数据，对其他组学类型（如蛋白质组、代谢组）的扩展性未讨论。此外，依赖公开数据库的完整性和准确性。

（完）
