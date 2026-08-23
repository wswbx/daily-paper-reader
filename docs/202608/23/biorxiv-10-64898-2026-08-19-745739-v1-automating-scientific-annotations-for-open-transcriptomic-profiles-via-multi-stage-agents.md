---
title: Automating scientific annotations for open transcriptomic profiles via multi-stage agents
title_zh: 通过多阶段智能体实现开放转录组谱的自动化科学注释
authors: "Zhang, X., Paithankar, S., Pu, J., Murtaza, M. S., Shankar, R., Leshchiner, D., Koirala, S., Palmer, Z., Nault, R., Li, X., Xie, Y., Chen, B."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.19.745739v1.full.pdf"
tags: ["query:ar"]
score: 9.0
evidence: 多阶段LLM智能体自动化科学元数据注释，属于自主研究的一种形式
tldr: 公共转录组数据库中大量样本因元数据不完整、格式不一而难以复用。提出GEOMeta，一种基于大语言模型的多阶段代理流程，将元数据检索、信息抽取、字段标准化、本体映射和质量控制分离。利用该流程为约60万个人类bulk RNA-seq样本生成标准化注释，并前瞻性验证了22个前沿大模型，开源Flash模型性能接近顶尖推理模型，成本降低一个数量级。
source: biorxiv
selection_source: fresh_fetch
motivation: 公共转录组数据库元数据异质且不一致，严重阻碍大规模数据复用。
method: GEOMeta采用多阶段代理流程，分步完成检索、抽取、标准化、本体映射与质控。
result: 为约60万人类样本生成标准化注释，并验证22个LLM，Flash模型性价比突出。
conclusion: 提供可扩展的元数据策展框架与资源，支持转录组学下游分析与模型评测。
---

## 摘要
公共转录组数据库中包含数百万个样本，然而由于其元数据报告异构且不一致，大规模重用受到阻碍。在基因表达综合数据库（GEO）中，关键生物学信息通常分布在研究级和样本级记录中，需要依赖上下文的解释。这里我们提出GEOMeta，一种基于大型语言模型（LLM）的多阶段工作流程，配备任务专用智能体，用于自动化的GEO元数据整理。该流程将元数据检索、任务特定信息提取、字段标准化、本体映射和质量控制分离。利用GEOMeta，我们为约600,000个人类批量RNA-seq样本生成了标准化注释。为展示其实用性，我们基准测试了转录组表示模型，用于从转录组嵌入中预测性别、年龄、组织和疾病。我们进一步前瞻性地注释了新提交的GEO研究，并评估了22个前沿LLM。最近的开源Flash模型在注释质量上与领先的推理模型相当，同时将成本降低了一个数量级。GEOMeta为元数据整理提供了可扩展资源和可重复框架。

## Abstract
Public transcriptomic repositories contain millions of samples, yet their large-scale reuse is hindered by heterogeneous and inconsistently reported metadata. In the Gene Expression Omnibus (GEO), key biological information is often distributed across study- and sample-level records, requiring context-dependent interpretation. Here we present GEOMeta, a large language model (LLM)-based multi-stage workflow with task-specialized agents for automated GEO metadata curation. The pipeline separates metadata retrieval, task-specific information extraction, field standardization, ontology mapping and quality control. Using GEOMeta, we generated standardized annotations for approximately 600,000 human bulk RNA-seq samples. To demonstrate its utility, we benchmarked transcriptome representation models for predicting sex, age, tissue and disease from transcriptome embeddings. We further prospectively annotated newly submitted GEO studies and evaluated 22 frontier LLMs. Recent open-source Flash models achieved annotation quality comparable to leading reasoning models while reducing costs by an order of magnitude. GEOMeta provides a scalable resource and reproducible framework for metadata curation.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究背景**：公共转录组数据库（如 GEO）包含数百万样本，是生物医学研究的重要资源。然而，这些样本的元数据（如性别、年龄、组织、疾病等）通常以非结构化、异构、不一致的方式报告，严重阻碍了大规模数据复用和下游分析。
- **核心问题**：如何自动、准确、规模化地将 GEO 中的原始元数据整理为标准化、结构化、可机器读写的注释，从而支撑大规模转录组学分析与模型评测？
- **整体含义**：论文提出了一种基于大语言模型（LLM）的自动化元数据策展框架 GEOMeta，将人工策展的高成本、低扩展性问题转化为可复用的自动化流程，为公共转录组数据的二次利用提供了关键基础设施。

## 2. 方法论：GEOMeta 多阶段智能体流程

- **核心思想**：将复杂的元数据策展任务拆分为多个阶段，每个阶段由任务专用的 LLM 智能体负责，从而实现模块化、可控制和可追溯的自动化处理。
- **流程分解**（共五个阶段）：
  1. **元数据检索（Retrieval）**：从 GEO 的研究级（series）和样本级（sample）记录中获取原始文本元数据。
  2. **任务特定信息抽取（Extraction）**：针对不同字段（如性别、年龄、组织、疾病）设计专用提示，让 LLM 从上下文相关的文本中提取目标信息。
  3. **字段标准化（Standardization）**：将抽取得到的自由文本统一为标准格式（如年龄单位、性别枚举等）。
  4. **本体映射（Ontology Mapping）**：将标准化字段映射到既有生物本体（如 UBERON 组织本体、疾病本体等），保证语义一致性。
  5. **质量控制（Quality Control）**：对生成注释进行规则或模型校验，过滤低置信度结果，确保注释可靠性。
- **关键技术细节**：没有公开具体提示词或模型精调细节，但强调流程可插拔，不同 LLM（22 个前沿模型）均可作为每个阶段的执行引擎，因此框架与具体模型解耦。

## 3. 实验设计

- **数据集**：
  - **主数据集**：约 60 万个人类 bulk RNA-seq 样本，来自 GEO。
  - **前瞻性验证集**：新近提交的 GEO 研究（论文中称“prospectively annotated newly submitted GEO studies”）。
- **Benchmark 任务**：
  - 使用生成的标准化注释，评估转录组表示模型（transcriptome representation models）在下游预测任务中的表现。
  - 具体预测任务：性别（sex）、年龄（age）、组织（tissue）和疾病（disease），输入为转录组嵌入。
- **对比方法**：
  - **LLM 对比**：评估了 22 个前沿大语言模型（包括专有推理模型和开源 Flash 系列模型），比较了注释质量与成本。
  - 文中未提及与传统 NLP/规则方法或人工策展的定量对比，但暗示 GEOMeta 优于非自动化方法（通过质量控制和标准化实现）。
- **实验场景**：
  - 回顾性大规模注释（60 万样本）。
  - 前瞻性新研究注释（测试泛化性与时效性）。
  - 下游任务实用性验证（嵌入预测）。

## 4. 资源与算力

- **论文未明确报告**所用 GPU 型号、数量或具体训练/推理时长。
- 仅提及**成本对比**：开源 Flash 模型将注释成本降低了一个数量级（相对于领先推理模型），但未给出绝对数值（如美元或 GPU 小时数）。
- 根据研究性质，该流程主要依赖 LLM API 或本地推理，不需要传统深度学习训练，算力需求以推理为主，但论文未展开。

## 5. 实验数量与充分性

- **实验数量**：
  - 大规模回顾性注释：1 个（覆盖约 60 万样本）。
  - 下游任务基准：4 个预测任务（性别、年龄、组织、疾病）。
  - 模型对比：22 个 LLM。
  - 前瞻性评估：1 个新研究集。
  - 表面上实验组数不多，但每个任务在 60 万规模样本上运行，统计效力充足。
- **充分性评估**：
  - **优点**：数据集规模大，覆盖多类常见元数据字段，前瞻性验证增强了外部有效性；22 个模型的横向对比提供了对不同模型的洞察。
  - **客观公平性**：
    - 作者未披露具体抽样方法、排除标准、人工评估（如果有）的细节，也没有提供消融实验（如去掉质量控制或本体映射对结果的影响）。
    - 下游预测任务仅用转录组嵌入，未与原始序列或传统特征对比，可能不能完全体现注释的增益。
    - 缺少与人工策展结果的直接一致性分析（如 Cohen's Kappa），主观质量评估不透明。
  - 总体而言，实验设计可支撑主要结论，但在透明性和对照细节上存在不足。

## 6. 主要结论与发现

- GEOMeta 能够以全自动化方式为约 60 万个人类 bulk RNA-seq 样本生成标准化注释，证明框架可扩展性。
- 生成的注释可有效用于训练/评测转录组表示模型的预测任务（性别、年龄、组织、疾病），说明注释实用价值高。
- 在前瞻性新提交 GEO 研究上表现良好，表明框架具有时间泛化能力。
- 模型对比发现：**新近开源 Flash 模型的注释质量与领先推理模型相当，而成本低一个数量级**，为低成本高质量元数据策展提供了现实选择。

## 7. 优点

- **模块化多阶段设计**：将检索、抽取、标准化、映射、质控分离，便于错误定位、模型替换和流程优化。
- **规模化扩展性**：成功应用于 60 万样本，远超人工能力范围。
- **前瞻性验证**：非仅在历史数据上测试，还验证了对新提交数据的适配能力，降低过拟合风险。
- **成本洞察**：对 22 个前沿 LLM 进行实操对比，为社区提供了明确的经济性选择依据，具有实用指导价值。
- **下游实用性闭环**：不只是生成注释，还通过真实转录组预测任务验证注释质量，形成“策展→建模→评测”闭环。
- **框架与模型解耦**：不依赖特定模型，未来新模型可即插即用。

## 8. 不足与局限

- **细节缺失**：作为预印本，未提供提示词设计、智能体内部实现、质控规则、人工评估协议等可复现关键细节。
- **未报告算力/能耗**：没有 GPU 或 API 调用量等具体资源信息，难以估算整体成本。
- **基准对比有限**：未与传统元数据整理方法（如文本挖掘工具、规则系统）或人工策展结果进行系统比较，缺少“无 GEOMeta”对照。
- **潜在偏差**：
  - GEO 样本本身存在提交偏差（如研究群体偏向特定疾病/人群），生成的注释可能会继承这种偏差。
  - 本体映射可能受别名、同义词和版本影响，未讨论映射错误率。
  - 质量控制阶段可能过度剔除样本，造成系统性缺失，但未给出剔除比例。
- **下游任务局限**：仅验证了性别/年龄/组织/疾病四个粗粒度字段，对于更细粒度（如细胞类型、处理条件、生存信息）的注释效果未经验证。
- **模型时效性**：22 个 LLM 的结论是当前时刻的快照，LLM 迭代迅速，结论可能随时间变化。
- **域泛化**：当前仅针对人类 bulk RNA-seq，对单细胞、其他物种或不同平台（如 Affymetrix、Nanostring）的适配性未说明。

（完）
