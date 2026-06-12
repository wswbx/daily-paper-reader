---
title: "KBase Research Agent: Automated Multi-Agent Workflow Construction for Reproducible Genome Analysis"
title_zh: KBase研究代理：用于可重复基因组分析的自动化多代理工作流构建
authors: "Gupta, P., Riehl, W. J., Cashman, M., Chivian, D., Neely, C. J., Canon, S. R., Cottingham, R., Henry, C., Arkin, A. P., Dehal, P. S."
date: 2026-06-04
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.01.729336v1.full.pdf"
tags: ["query:cli-agent"]
score: 8.0
evidence: 自动化KBase工作流的多智能体系统，涉及命令行执行
tldr: 构建多步生物信息学工作流（从读段质控到功能注释）需要生物学和计算双重专业知识，成为可扩展可重复分析的瓶颈。KBase Research Agent是一个多智能体系统，基于KBase文档和知识图谱自动构建分析计划，选择、参数化并执行KBase应用，结果保存为可重复Narrative。在参考工作流评估中规划与执行质量高，并在100个未分析细菌基因组上全自动完成质控、组装、GTDB-Tk分类和下游分析，生成注释基因组、Narratives和草稿手稿，无需人类干预。该工作证明了在生产生物信息学平台中端到端科学工作流自动化的可行性，为大规模基因组分析提供了有力工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决多步基因组分析工作流构建对专业知识依赖导致的低效和不可重复问题。
method: 构建多智能体系统，利用KBase文档和知识图谱自动生成分析计划，选择并参数化KBase应用，验证执行后保存为可重复Narrative。
result: 在参考工作流评估和100个细菌基因组实验中，全自动完成读段质控、组装、分类和功能注释，生成基因组、可重复Narratives和草稿论文，无需人工干预。
conclusion: 证明了在KBase平台上实现端到端自动化基因组工作流的可行性，为大规模可重复分析提供了范例。
---

## 摘要
构建从读段质量控制、基因组组装到功能注释的多步骤生物信息学工作流，需要具备生物学和计算工具选择的专业知识，这为可扩展和可重复的分析造成了瓶颈。我们提出了KBase研究代理，这是一个在DOE系统生物学知识库（KBase）中自动化此类工作流的多代理系统。给定一组测序读段和研究目标，该代理基于KBase文档和KBase应用程序目录的知识图谱构建分析计划，然后选择、参数化、验证并执行合适的KBase应用程序以完成工作流。最终的分析结果被保存为可重复的KBase叙事。我们根据从同行评审的《微生物资源公告》中提取的参考工作流构建的地面真值，评估了系统的规划和执行质量。我们进一步将该代理应用于来自JGI IMG/M数据库的100个之前未分析的细菌分离株基因组，代理自主执行了读段质量控制、基因组组装、使用GTDB-Tk进行分类学分类以及下游分析，生成了注释基因组、可重复叙事和草稿手稿，无需人工干预。在这些实验中，KBase研究代理展示了在生产级生物信息学平台中实现基于领域知识的端到端科学工作流自动化的可行性。

## Abstract
Constructing multi-step bioinformatics workflows, from read quality control through genome assembly to functional annotation, requires expertise in both biology and computational tool selection, creating a bottleneck for scalable and reproducible analysis. We present the KBase Research Agent, a multi-agent system for automating such workflows within the DOE Systems Biology Knowledgebase (KBase). Given a set of sequencing reads and a research objective, the agent constructs an analysis plan grounded in KBase documentation and a Knowledge Graph (KG) of the KBase application catalog, then selects, parameterizes, validates and executes appropriate KBase applications to carry out the workflow. The resulting analysis is preserved as a reproducible KBase Narrative. We evaluate the systems planning and execution quality against ground truth constructed from reference workflows derived from peer-reviewed Microbiology Resource Announcements. We further apply the agent to 100 previously unanalyzed bacterial isolate genomes from the JGI IMG/M database, where it autonomously performed read quality control, genome assembly, taxonomic classification with GTDB-Tk, and downstream analysis producing annotated genomes, reproducible Narratives, and draft manuscripts without human intervention. Across these experiments, the KBase Research Agent demonstrates the feasibility of domain-grounded, end-to-end scientific workflow automation in a production bioinformatics platform.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义
- **研究动机**：多步骤生物信息学工作流（如从读段质控到基因组组装再到功能注释）的构建要求研究者同时具备生物学知识和计算工具选择经验，这成为可扩展、可重复分析的主要瓶颈。
- **背景**：DOE系统生物学知识库（KBase）是一个生产级生物信息学平台，支持可重复的叙事（Narrative）记录。但手动构建工作流仍依赖专家，限制了大规模基因组分析的自动化。
- **整体含义**：本文旨在展示在KBase平台上通过多智能体系统实现端到端科学工作流自动化的可行性，从而降低专业知识门槛、提高分析可重复性和规模化能力。

## 2. 方法论：核心思想与关键技术细节
- **核心思想**：构建一个多智能体系统（KBase Research Agent），利用KBase文档和应用程序目录的知识图谱（Knowledge Graph, KG），自动生成分析计划、选择并参数化合适的KBase应用，执行后保存为可重复的Narrative。
- **关键技术细节**：
  - 系统以一组测序读段和研究目标为输入。
  - 代理首先基于KBase文档和知识图谱构建分析计划。
  - 随后选择、参数化、验证并执行合适的KBase应用程序。
  - 分析结果被保存为可重复的KBase Narrative（包括中间结果和最终产出）。
  - 未涉及具体算法公式或数学推导，主要依赖知识检索、规划与执行循环。
- **流程概述**（文字描述）：
  - 输入：用户提供测序读段（如FASTQ）和任务描述（如“组装并注释细菌基因组”）。
  - 规划阶段：Agent查询KBase知识图谱和应用目录，生成多步计划（如质控→组装→分类→注释）。
  - 执行阶段：Agent为每个步骤选择合适的KBase应用，自动设置参数，监控执行状态，处理错误。
  - 输出阶段：所有步骤完成后，结果被整合到一个可重现的Narrative中，包括数据和手稿草稿。

## 3. 实验设计
- **数据集/场景**：
  - **评估场景1**：参考工作流地面真值——从同行评审的《Microbiology Resource Announcements》中提取的参考工作流，用于评估规划和执行质量。
  - **评估场景2**：100个之前未分析的细菌分离株基因组（来自JGI IMG/M数据库），系统自主执行读段质控、基因组组装、GTDB-Tk分类学分类以及下游分析。
- **基准（Benchmark）**：无明确对比方法；评估基于地面真值工作流的匹配度（规划与执行质量），以及100个基因组上的全自动结果（是否生成了注释基因组、可重复叙事和手稿草稿）。
- **对比方法**：文中未提及其他自动化工具或基线方法的对比，主要评估系统自身的规划准确性和执行成功率。

## 4. 资源与算力
- **文中未明确说明**：未提及使用的GPU型号、数量、训练时长、计算节点等硬件资源。系统运行在KBase生产平台上，但具体算力细节未给出。
- **提示**：由于是预印本且侧重于方法论验证，可能资源开销不是重点。

## 5. 实验数量与充分性
- **实验数量**：
  - 一组基于参考工作流地面真值的评估（未说明具体工作流数量，可能数十个）。
  - 一组100个细菌基因组的全自动分析实验。
- **充分性**：
  - 参考工作流评估提供了对规划和执行质量的客观度量。
  - 100个基因组实验展示了端到端自动化在大规模场景下的实用性。
  - 但缺少消融实验（如不同知识图谱构建方式、不同规划策略的对比）以及与其他自动化工具的定量对比，因此充分性一般，属于可行性验证阶段。
- **公平性**：参考工作流基于已发表文献，具有客观性；但100个基因组的选择未说明随机性，可能存在偏差风险。

## 6. 主要结论与发现
- 系统在参考工作流评估中展示了较高的规划和执行质量。
- 在100个细菌基因组全自动分析中，系统自主完成了读段质控、组装、GTDB-Tk分类和下游分析，生成了注释基因组、可重复Narratives和草稿手稿，无需任何人工干预。
- 这些实验证明了在生产级生物信息学平台上，基于领域知识的端到端科学工作流自动化是可行的，为大规模基因组分析提供了有力工具。

## 7. 优点
- **创新性**：首次在KBase生产平台上实现多智能体自动工作流构建，利用知识图谱指导分析计划生成。
- **实用性**：系统能输出可重复的Narrative和草稿手稿，直接服务于科研发表和结果共享。
- **自动化程度高**：从输入读段到最终输出标注基因组和论文草稿，完全无需人工介入，可扩展性强。
- **评估扎实**：使用真实发表的参考工作流作为地面真值，避免人为编写的测试用例偏差。

## 8. 不足与局限
- **对比缺失**：未与已有的工作流自动化工具（如Galaxy、Nextflow的自动化变体）或通用LLM代理（如AutoGPT）进行定量比较，难以评估相对优势。
- **消融实验缺乏**：未分析知识图谱、规划策略、多智能体协作等模块的贡献，无法判断各组件重要性。
- **偏差风险**：100个基因组来源单一（JGI IMG/M数据库），可能无法代表不同测序平台或复杂元基因组场景。
- **应用限制**：目前仅适用于KBase平台内的应用和流程，跨平台通用性未验证；对非细菌基因组（如真核生物）的适用性未说明。
- **资源细节缺失**：未报告计算成本和运行时间，难以判断实际部署的经济可行性。

（完）
