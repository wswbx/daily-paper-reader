---
title: "biomeStat: Using Agentic AI for Scalable Genomic Epidemiology Demonstrated Through End-to-End Analysis of 1,000 Asian Dengue Virus Genomes"
title_zh: "biomeStat: 使用智能体AI实现可扩展的基因组流行病学——通过对1000个亚洲登革病毒基因组的端到端分析进行演示"
authors: "Ariyaratne, D., Somaratna, N., Malavige, G. N."
date: 2026-06-23
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.10.731380v1.full.pdf"
tags: ["query:cli-agent"]
score: 8.0
evidence: 自主AI代理自动执行工具，无需命令行专业知识
tldr: 基因组流行病学工作流通常依赖专家手动调参和异构计算，而标准生成式AI易产生幻觉。biomeStat作为自主AI代理，通过自动编写代码执行确定性生物信息学工具，并动态分配CPU/GPU资源，保证可重复性。在1000个亚洲登革病毒基因组分析中，它23小时内完成系统发育、贝叶斯动力学和选择压力分析，发现1869个免疫逃逸位点并验证176个保守药物靶点。该方法将专家数周工作压缩为单次全透明分析，显著提升了可扩展性与可用性。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决基因组流行病学工作流需要专家手动调参和异构计算，且标准AI易幻觉的问题。
method: biomeStat作为自主AI代理，自动编写代码调用确定性工具（如IQ-TREE、BEAST2）并动态分配CPU/GPU资源。
result: 全自动分析1000个亚洲登革病毒基因组，发现1869个免疫逃逸位点，并验证176个保守药物靶点。
conclusion: 证明该代理可将数周专家工作压缩为单次全透明分析，显著提升基因组流行病学研究的效率与可重复性。
---

## 摘要
基因组流行病学工作流程通常需要专家对多种专用工具进行筛选、大量手动参数调整以及访问异构计算基础设施。虽然标准生成式AI模型在复杂生物领域常出现幻觉，我们引入了biomeStat：一个自主AI智能体，作为严格的确定性编排器。通过自动编写代码在沙箱环境中执行已建立的生物信息学工具，biomeStat动态配置计算资源（CPU和GPU）并保证可重复性，使其无需命令行专业知识即可直接为科学家所用。为演示该平台，我们对2000年至2025年间从16个亚洲国家采集的1000个登革病毒（DENV）基因组进行了完全自主的基因组流行病学和结构分析。该智能体无缝编排了系统发育重建（IQ-TREE、TreeTime）、贝叶斯系统动力学（通过NVIDIA H200 GPU的BEAST2）、选择压力分析（HyPhy）和结构映射（PyMOL）。分析在不到24小时的实际时间内完成，揭示了地方性稳定状态（R_e ~1.0），并识别出1,869个与B细胞和T细胞表位在结构上共定位的候选免疫逃逸位点。此外，该智能体验证了病毒复制复合体上176个高度保守的药物靶点残基，确认新兴抗病毒药物JNJ-1802和NITD-688的耐药相关位点在所有四种血清型中均绝对保守。通过弥合自然语言意图与确定性计算执行之间的鸿沟，biomeStat将数周的专家工作简化为一次会话分析，并具有完全的方法透明度。

## Abstract
Genomic epidemiology workflows typically require expert curation of multiple specialized tools, extensive manual parameter tuning, and access to heterogeneous compute infrastructure. While standard generative AI models often hallucinate in complex biological domains, we introduce biomeStat: an autonomous AI agent that functions as a strict deterministic orchestrator. By automatically writing code to execute established bioinformatics tools in sandboxed environments, biomeStat dynamically provisions compute resources (CPU and GPU) and guarantees reproducibility, making it immediately useful for scientists without requiring command-line expertise. To demonstrate the platform, we performed a fully autonomous genomic epidemiology and structural analysis of 1,000 Dengue virus (DENV) genomes sampled from 16 Asian countries between 2000 and 2025. The agent seamlessly orchestrated phylogenetic reconstruction (IQ-TREE, TreeTime), Bayesian phylodynamics (BEAST2 via NVIDIA H200 GPU), selection pressure analysis (HyPhy), and structural mapping (PyMOL). The analysis was completed in under 24 hours of wall-clock time, revealing endemic stability (R_e ~1.0) and identifying 1,869 candidate immune escape sites structurally colocalized with B-cell and T-cell epitopes. Furthermore, the agent validated 176 highly conserved drug target residues across the viral replication complex, confirming that resistance-associated positions for emerging antivirals JNJ-1802 and NITD-688 remain absolutely conserved across all four serotypes. By bridging the gap between natural language intent and deterministic computational execution, biomeStat reduces weeks of expert effort into a single-session analysis with full methodological transparency.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：基因组流行病学工作流通常依赖专家手动筛选多种专用工具、大量参数调优，并需要异构计算基础设施支持。标准生成式AI模型在复杂生物领域容易产生幻觉，无法保证计算结果的可靠性和可重复性。
- **整体含义**：为了弥合自然语言意图与确定性计算执行之间的鸿沟，作者提出biomeStat——一个自主AI智能体，作为严格的确定性编排器。它通过自动编写代码调用已建立的生物信息学工具，在沙箱环境中执行，动态分配CPU/GPU资源，无需使用者具备命令行专业知识，从而将数周的专家工作量压缩为一次会话分析，并实现完全的方法透明度。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：biomeStat作为一个自主AI代理，不是直接生成分析结果（避免幻觉），而是作为编排器自动生成和执行代码，调用成熟的确定性生物信息学工具（如IQ-TREE、TreeTime、BEAST2、HyPhy、PyMOL），确保计算过程严格可重复。
- **关键技术细节**：
  - **自动代码编写**：接收自然语言指令后，自动生成Python/R/Shell脚本，在沙箱环境中运行。
  - **动态资源配置**：根据任务需求自动分配CPU和GPU资源（例如BEAST2通过NVIDIA H200 GPU加速）。
  - **确定性工具链**：编排的系统发育重建（IQ-TREE、TreeTime）、贝叶斯系统动力学（BEAST2）、选择压力分析（HyPhy）和结构映射（PyMOL）均为成熟计算工具，输出可验证。
  - **端到端流程**：从数据预处理到最终结果报告，全自动完成，无需人工干预参数调优。

## 3. 实验设计：数据集、场景、基准、对比方法

- **数据集**：2000年至2025年间从16个亚洲国家采集的**1,000个登革病毒（DENV）基因组**，覆盖四种血清型。
- **实验场景**：全自动基因组流行病学和结构分析，包括系统发育树构建、贝叶斯动力学推断、选择压力检测、免疫逃逸位点识别和药物靶点保守性验证。
- **基准与对比方法**：文中未明确设立传统方法作为基准，也未与其他AI代理或手动分析进行对比。实验本质上是biomeStat平台的功能演示，而非比较性评估。主要验证其能否在合理时间内完成复杂分析链。

## 4. 资源与算力

- **明确提及的算力**：
  - BEAST2 通过 **NVIDIA H200 GPU** 加速运行。
  - 整个分析的实际墙钟时间（wall-clock time）**少于24小时**（实际23小时内完成）。
- **未明确说明**：GPU的具体数量、CPU核心数、内存大小、训练时长（所用BEAST2是推断而非训练），以及是否涉及分布式计算。

## 5. 实验数量与充分性

- **实验数量**：仅进行了一组端到端分析（1,000个基因组），未设置多组不同规模的数据集、消融实验或不同参数配置的对比。
- **充分性评估**：
  - 作为平台演示，该实验足以证明biomeStat能够自动化完成复杂的基因组流行病学分析流程。
  - 但缺乏**多场景验证**（例如不同病毒、不同数据量级）、**稳定性测试**（重复运行结果一致性）以及**与手动专家工作流的量化比较**（时间、准确性、资源消耗等）。
  - 无法全面评估该方法在更广泛任务中的泛化能力和鲁棒性。

## 6. 主要结论与发现

- **核心结果**：
  - 登革热流行呈现地方性稳定状态（有效再生数 R_e ≈1.0）。
  - 识别出 **1,869个候选免疫逃逸位点**，这些位点在结构上与B细胞和T细胞表位共定位。
  - 验证了病毒复制复合体上 **176个高度保守的药物靶点残基**，其中新兴抗病毒药物JNJ-1802和NITD-688的耐药相关位点在所有四种血清型中**绝对保守**。
- **方法学结论**：biomeStat成功将通常需要数周的专家工作量压缩为一次**23小时的全自动会话**，且过程完全透明、可重复，无需用户具备命令行专业知识。

## 7. 优点

- **自动化程度高**：从数据输入到结果报告全自动，降低使用门槛（无需编程技能）。
- **可重复性保障**：确定性工具链+沙箱环境，避免生成式AI的幻觉风险。
- **资源动态适配**：自动分配CPU/GPU，优化计算效率。
- **透明性与可审计性**：所有代码自动生成并记录，方法学完全公开。
- **效率提升显著**：将数周人工分析缩短至一天以内，对大规模基因组流行病学研究意义重大。
- **应用价值明确**：在真实数据上验证了关键生物学发现（保守药物靶点、免疫逃逸位点），具有实际公共卫生意义。

## 8. 不足与局限

- **实验覆盖不足**：仅使用单一病毒（登革热）和固定数据规模（1,000个基因组），未测试其他病原体或更大/更小数据集，通用性存疑。
- **缺乏对比基准**：未与手动专家分析耗时、准确性、资源消耗进行量化对比，难以评估其相对于传统方法的优势幅度。
- **偏差风险**：依赖所选工具链的固有限制（如BEAST2的模型假设、HyPhy的选择压力模型），且代理自动编写代码时可能忽略某些最佳实践或参数优化。
- **应用限制**：
  - 需要访问NVIDIA H200等高端GPU，算力门槛高。
  - 沙箱环境可能限制某些需要系统级调用的工具。
  - 仅支持已封装的工具列表，无法处理全新或非标准分析需求。
  - 缺乏错误处理与人工干预机制，若某步骤出错可能导致全流程失败。

（完）
