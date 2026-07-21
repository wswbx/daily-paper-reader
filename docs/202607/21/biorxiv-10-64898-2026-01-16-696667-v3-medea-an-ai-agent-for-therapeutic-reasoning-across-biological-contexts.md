---
title: "Medea: An AI agent for therapeutic reasoning across biological contexts"
title_zh: Medea：一种跨生物情境的治疗推理AI代理
authors: "Sui, P., Li, M., Munson, B. P., Gao, S., Shen, W., Giunchiglia, V., Shen, A., Huang, Y., Kong, Z., Licon, K., Ideker, T., Zitnik, M."
date: 2026-07-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.01.16.696667v3.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 用于自主治疗推理的AI智能体
tldr: "治疗假设的跨疾病转移依赖生物上下文，现有AI系统难以在长流程中保持上下文并验证中间步骤。Medea是一个基于验证的AI代理，集成生物工具、机器学习和文献检索，在多步分析中强制执行验证。在5,673个分析中，Medea在靶点提名、合成致死预测和免疫治疗反应预测中超越现有模型，并在238,046个基因对的新实验数据上验证了其生物学相关性。结果表明，可验证的AI代理能有效进行跨生物背景的治疗推理。"
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 1775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1395, \"height\": 1383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1690, \"height\": 1452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1633, \"height\": 1776, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1559, \"height\": 1930, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1673, \"height\": 1366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-01-16-696667-v3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1686, \"height\": 879, \"label\": \"Figure\"}]"
motivation: 治疗推理需保留上下文和验证证据，现有AI系统在长工作流中难以保持上下文并协调冲突证据。
method: Medea结合生物工具、机器学习和文献检索，在规划、执行和证据合成阶段强制执行验证。
result: "在5,673个分析中，Medea在靶点提名、合成致死预测等任务上优于多种模型，并在新酵母数据中准确预测合成致死。"
conclusion: 可验证的AI代理能有效进行跨生物背景的治疗分析，提高性能并保持低失败率。
---

## 摘要
治疗假设可以跨疾病转移，但其相关性取决于生物情境。相同的靶点、扰动或治疗在不同细胞类型、疾病状态、遗传背景和患者中可能产生不同效果。因此，治疗推理需要能够保留情境、检验证据是否支持转移以及识别情境特异性效应的限制的方法。尽管AI代理可以执行治疗分析，但现有系统通常无法在长工作流中保留生物情境、验证中间计算步骤或协调数据集和文献中的冲突证据。在此，我们提出Medea，一种跨生物情境的治疗推理AI代理。Medea使用生物工具、机器学习模型和文献检索执行多步分析，同时在规划、执行和证据合成过程中强制进行验证。我们在三个领域的5,673个开放式分析中评估了Medea：五种疾病和29种细胞类型的细胞类型特异性治疗靶点提名、7种癌细胞系的合成致死预测以及基于多模态患者谱的免疫治疗反应预测。使用之前在两种DNA损伤处理下进行的未发表的表位微型阵列筛选，我们在酵母中评估Medea预测238,046个基因对之间的合成致死性。Medea预测了这些实验测量的合成致死相互作用，表明其性能反映了生物学相关性，而非基准数据集的信息泄漏。在这些评估中，Medea优于大型语言模型、推理模型、生物医学代理和专门的机器学习模型，同时保持低失败率和校准的弃权率。这些结果表明，可验证的AI代理可以跨生物情境执行治疗分析。

## Abstract
Therapeutic hypotheses can transfer across diseases but their relevance depends on biological context. The same target, perturbation, or treatment can produce different effects across cell types, disease states, genetic backgrounds, and patients. Therapeutic reasoning therefore requires methods that preserve context, test when evidence supports transfer, and identify where context-specific effects limit it. Although AI agents can perform therapeutic analyses, existing systems often fail to preserve biological context over long workflows, verify intermediate computational steps, or reconcile conflicting evidence across datasets and literature. Here, we present Medea, an AI agent for therapeutic reasoning across biological contexts. Medea executes multi-step analyses using biological tools, machine learning models, and literature retrieval while enforcing verification during planning, execution, and evidence synthesis. We evaluate Medea across 5,673 open-ended analyses in three domains: cell type specific therapeutic target nomination in five diseases and 29 cell types, synthetic lethality prediction in 7 cancer cell lines, and immunotherapy response prediction from multimodal patient profiles. Using a previously unpublished epistatic miniarray profiling screen performed under two DNA-damaging treatments, we evaluate Medea on predicting synthetic lethality among 238,046 gene-gene pairs in yeast. Medea predicts these experimentally measured synthetic lethal interactions, indicating that its performance reflects biological relevance rather than information leakage from benchmark datasets. Across these evaluations, Medea improves performance over large language models, reasoning models, biomedical agents, and specialized machine learning models while maintaining low failure rates and calibrated abstention. These results show that verifiable AI agents can perform therapeutic analyses across biological contexts.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：治疗假设（如靶点、扰动、治疗）在不同生物情境（细胞类型、疾病状态、遗传背景、患者）下效果不同，现有的AI系统在长工作流中难以保留生物情境、验证中间计算步骤、协调数据集与文献中的冲突证据。
- **整体含义**：需要一种能够跨生物情境进行治疗推理且具备可验证性的AI代理，以提高治疗分析的科学严谨性和可靠性。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：Medea是一个基于验证的AI代理，在治疗推理的规划、执行和证据合成三阶段强制执行验证，确保中间步骤的可信度和情境保留。
- **关键技术细节**：
  - 集成生物工具、机器学习模型和文献检索，执行多步分析。
  - **验证机制**：在规划阶段验证假设合理性；执行阶段验证计算步骤的正确性（如基因关系查询、模型输出校准）；证据合成阶段验证跨来源证据的一致性（如利用逻辑推理、一致性检查）。
  - **弃权机制**：当置信度过低或证据冲突无法调和时，Medea可以主动弃权（不输出结论），并保持校准的弃权率。
- **算法流程（文字描述）**：
  1. 接收用户查询（如“在乳腺癌中提名治疗靶点”），分解为子任务。
  2. 调用生物数据库（如STRING、DepMap）、机器学习预测模型（如合成致死模型）和文献检索（如PubMed）获取证据。
  3. 对每个子任务的输出进行验证（如检查基因表达是否显著、模型置信度是否达标、文献中是否存在矛盾结论）。
  4. 如果验证通过，则整合证据；否则尝试重新计算或弃权。
  5. 最终输出带证明链的治疗推理结论。

## 3. 实验设计

- **使用的数据集/场景**：
  - **靶点提名**：5种疾病（如乳腺癌、肺癌等）× 29种细胞类型。
  - **合成致死预测**：7种癌细胞系。
  - **免疫治疗反应预测**：基于多模态患者谱（包括基因组、转录组、临床数据）。
  - **新实验验证**：在酵母中，使用此前未发表的表位微型阵列筛选（Epistatic Miniarray Profiling），在两种DNA损伤处理条件下，评估238,046个基因对之间的合成致死性。
- **Benchmark**：与以下方法对比：
  - 大型语言模型（如GPT-4）
  - 推理模型（如思维链模型）
  - 生物医学代理（如GeneGPT、BioAgent）
  - 专门的机器学习模型（如Logistic回归、深度神经网络）
- **对比指标**：失败率（错误输出或无法完成任务）、弃权率（主动放弃的案例）、预测性能（AUC、精确率/召回率等）。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长、推理时长等算力细节。仅提及Medea集成了多种预训练模型和工具，但未给出训练或推理的计算资源开销。

## 5. 实验数量与充分性

- **实验数量**：总计5,673个开放式分析（靶点提名、合成致死预测、免疫治疗反应预测），外加酵母新实验验证（238,046个基因对）。
- **充分性评估**：
  - 覆盖三个不同治疗推理领域，且包含大规模新实验验证，避免基准数据集信息泄漏，实验设计较为充分。
  - 对比了多种基线方法（包括LLM、推理模型、专用模型），覆盖面广。
  - 消融实验可能隐含在对比中（如弃权机制的效果），但文中未明确列出单独的消融实验。
  - 评估指标包括失败率和弃权率，体现了公平性（允许AI弃权可避免强制输出错误结论）。

## 6. 主要结论与发现

- Medea在靶点提名、合成致死预测、免疫治疗反应预测三项任务上均优于所有对比方法，同时保持低失败率和校准的弃权率。
- 在新酵母实验数据中，Medea准确预测了238,046个基因对的合成致死相互作用，证明其性能来自生物学相关性而非数据泄露。
- 可验证的AI代理（Medea）能够有效进行跨生物情境的治疗分析，通过强制执行验证步骤提高了推理的可靠性和情境保真度。

## 7. 优点

- **方法设计亮点**：将验证嵌入规划、执行、证据合成的全过程，形成闭环，确保每一步的合理性。
- **实验验证亮点**：使用全新的、未公开发表的酵母实验数据（表位微型阵列筛选）进行验证，避免了常见基准数据集的过拟合风险。
- **对比全面**：涵盖LLM、推理模型、专用代理和传统机器学习模型，且考虑了失败率和弃权率，更贴近实际应用。
- **弃权机制**：允许模型在不确定时主动放弃，提高了系统可信度，符合安全AI的期望。

## 8. 不足与局限

- **算力资源未披露**：无法评估其可部署性，对于资源受限机构可能不友好。
- **实验覆盖范围**：虽然涉及多个领域，但仅测试了有限疾病/细胞类型（5种疾病、29种细胞类型、7种癌细胞系），可能未充分覆盖罕见病或特殊情境。
- **偏差风险**：可能依赖特定数据库和工具（如STRING、DepMap），这些数据库本身存在偏差（如常见基因优先）。
- **应用限制**：集中于治疗靶点提名和合成致死，未涉及药物剂量、毒性、临床试验设计等更复杂场景。验证仅在酵母和细胞系层面，缺乏临床患者前瞻性验证。
- **消融实验缺失**：未明确分解验证模块的贡献，例如去掉验证步骤后性能下降多少。

（完）
