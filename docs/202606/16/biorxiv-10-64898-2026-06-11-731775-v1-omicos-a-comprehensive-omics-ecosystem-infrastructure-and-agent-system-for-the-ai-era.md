---
title: "OmicOS: A Comprehensive Omics Ecosystem Infrastructure and Agent System for the AI Era"
title_zh: OmicOS：面向人工智能时代的综合组学生态系统基础设施与智能体系统
authors: "Zeng, Z., Meng, X., Hu, L., Li, C., Liu, P., Shi, Y., Ma, X., Gao, L., Wang, X., Luo, Z., Zheng, Y., Xian, J., Lin, Z., Zhu, H., Jiang, Z., Mao, S., Lu, Y., Tang, W., Peng, Q., Ma, Y., Zhou, L., Xing, C., Zhang, X., Xiong, Y., Du, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731775v1.full.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: 面向组学的命令行代理基础设施
tldr: "生物组学方法分散在Python、R等多种工具中，难以被AI系统可靠调用。OmicOS基于OmicVerse V2生态，将分析函数注册为状态感知能力合约，构建可编程组学环境，使智能体能够检查数据、选择合法方法并记录出处。在基准测试BiomniBench上达到81.2%准确率，添加OmicVerse后模型任务完成率提升最高34.2个百分点，并成功复现R工作流、扩展病理软件为智能体可用技能。该工作为AI时代的组学分析提供了开放、可扩展的基础设施，将社区方法转化为可操作的发现系统。"
source: biorxiv
selection_source: fresh_fetch
motivation: 组学方法碎片化，现有生态面向专家而非AI，导致智能体难以可靠选择、执行和验证分析。
method: 将OmicVerse V2的分析函数注册为状态感知能力合约，支持智能体检查数据对象、选择合法方法并控执行和记录出处。
result: "在BiomniBench上排名第一（81.2%），添加OmicVerse使任务完成率提升最高34.2个百分点，复现R工作流并发现阿尔茨海默病相关结肠上皮风险轴。"
conclusion: 定义了AI时代组学的开放基础，将社区方法转化为可靠、可扩展的智能体操作发现系统。
---

## 摘要
生物学积累了庞大的组学方法生态系统，但其中大部分仍是为人类专家而非科学智能体构建的。这些方法散布在Python包、R/Bioconductor和CRAN工作流、命令行工具、不兼容的数据容器以及隐式对象状态中，使得即使是常规分析对于AI系统来说也难以可靠地选择、执行和验证。为此，我们介绍OmicOS——一个综合的组学生态系统基础设施与智能体系统，它将开源组学社区OmicVerse V2转变为可执行的智能体生物学基础。OmicVerse V2提供了社区基质：可扩展的AnnDataOOM兼容Rust后端、面向单细胞、空间、bulk和多组学分析的智能体友好型Python算法、与单细胞基础模型的接口，以及历史上以R为中心的Bioconductor/CRAN风格工作流的Python原生重构。OmicOS通过将分析函数注册为状态感知的能力契约，使该基质可操作，允许智能体检查实时数据对象、选择有效方法、执行受控工作流并记录来源。结果并非固定的管道，而是一个可编程的组学环境，智能体在其中基于经过验证的社区方法组合真实分析，而非发明工具。在外部及特定构建的基准测试中，OmicOS在评估系统中排名第一，在BiomniBench上达到81.2%。将OmicVerse添加到最小智能体中，使用qwen-3.6-35b模型时任务完成度提升了高达34.2个百分点，而受控消融实验表明，这种提升来自基于注册的执行，而非更大的模型、文档检索或不受限制的工具暴露。同一基础设施可扩展至图谱规模的数据，在Python中复现以R为中心的工作流，并将外部病理软件转换为智能体可用的技能。在一项从全身空间图谱和术语“阿尔茨海默病”开始的发现任务中，OmicOS组合了一个非标准工作流，整合了空间表达、遗传关联、eQTL和共定位证据，提名了一个以PICALM、CD2AP和CR1为中心的结肠上皮风险轴。总之，OmicVerse和OmicOS共同定义了AI时代组学的开放基础，展示了如何将生物学方法社区转变为可靠、可扩展且智能体可操作的科学发现系统。

## Abstract
Biology has accumulated a vast ecosystem of omics methods, but much of this ecosystem remains built for expert humans rather than scientific agents. Methods are scattered across Python packages, R/Bioconductor and CRAN workflows, command-line tools, incompatible data containers and implicit object states, making even routine analyses difficult for an AI system to choose, execute and verify reliably. Here we introduce OmicOS, a comprehensive omics ecosystem infrastructure and agent system that turns OmicVerse V2, an open-source omics community, into an executable foundation for agentic biology. OmicVerse V2 provides the community substrate: scalable AnnDataOOM-compatible rust backends, agent-friendly Python algorithms for single-cell, spatial, bulk and multi-omics analysis, interfaces to single-cell foundation models, and Python-native reconstructions of historically R-centred Bioconductor/CRAN-style workflows. OmicOS makes this substrate actionable by registering analytical functions as state-aware capability contracts, allowing agents to inspect live data objects, select valid methods, execute controlled workflows and record provenance. The result is not a fixed pipeline, but a programmable omics environment in which agents compose real analyses from verified community methods rather than inventing tools. Across external and purpose-built benchmarks, OmicOS ranked first among the evaluated systems, reaching 81.2% on BiomniBench. Adding OmicVerse to a minimal agent improved task completion by up to 34.2 percentage points with qwen-3.6-35b, and controlled ablations showed that the gains came from registry-grounded execution rather than from larger models, documentation retrieval or unrestricted tool exposure. The same infrastructure scaled to atlas-sized data, reproduced R-centred workflows in Python and converted external pathology software into agent-usable skills. In a discovery task starting from a whole-body spatial map and the term Alzheimer disease, OmicOS composed a non-canonical workflow that integrated spatial expression, genetic association, eQTL and colocalization evidence to nominate a colon epithelial risk axis centred on PICALM, CD2AP and CR1. Together, OmicVerse and OmicOS define an open foundation for AI-era omics, showing how a community of biological methods can be transformed into a reliable, extensible and agent-operable system for discovery.