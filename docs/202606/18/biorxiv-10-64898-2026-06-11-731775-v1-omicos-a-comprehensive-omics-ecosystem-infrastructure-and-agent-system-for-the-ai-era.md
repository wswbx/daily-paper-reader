---
title: "OmicOS: A Comprehensive Omics Ecosystem Infrastructure and Agent System for the AI Era"
title_zh: OmicOS：面向人工智能时代的综合组学生态系统基础设施与智能体系统
authors: "Zeng, Z., Meng, X., Hu, L., Li, C., Liu, P., Shi, Y., Ma, X., Gao, L., Wang, X., Luo, Z., Zheng, Y., Xian, J., Lin, Z., Zhu, H., Jiang, Z., Mao, S., Lu, Y., Tang, W., Peng, Q., Ma, Y., Zhou, L., Xing, C., Zhang, X., Xiong, Y., Du, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731775v1.full.pdf"
tags: ["query:cli-agent"]
score: 8.0
evidence: 利用LLM代理自动执行组学命令行工具
tldr: "生物组学分析方法分散于Python、R、命令行等不同生态，AI系统难以可靠选择与执行。OmicOS将OmicVerse V2社区中的694种方法注册为状态感知能力合约，使智能体能实时检查数据对象、组合执行并记录溯源。在BiomniBench上达到81.2%准确率，为开源模型提升34.2个百分点任务完成度，并成功复现R工作流、整合病理软件。该方法将社区生态转化为可靠、可扩展的智能体可操作系统，为AI时代组学发现奠定开放基础。"
source: biorxiv
selection_source: fresh_fetch
motivation: 组学方法碎片化严重，现有工具专为人类设计，AI系统难以自主选择、执行和验证，亟需统一可执行基础设施。
method: 构建OmicVerse V2社区并注册分析函数为状态感知能力合约，智能体可动态检查数据对象、选择有效方法、执行工作流并记录溯源。
result: "在BiomniBench中排名第一（81.2%），添加OmicVerse使qwen-3.6-35b任务完成度提升34.2个百分点，可复现R工作流并集成外部病理软件。"
conclusion: OmicOS将零散组学方法转化为智能体可操作的可靠系统，为AI时代的发现提供开放、可扩展的基础。
---

## 摘要
生物学积累了庞大的组学方法生态系统，但其中大部分仍是为人类专家而非科学智能体设计的。这些方法分散在Python包、R/Bioconductor和CRAN工作流、命令行工具、不兼容的数据容器以及隐式对象状态中，使得AI系统难以可靠地选择、执行和验证常规分析。本文介绍OmicOS，一个全面的组学生态系统基础设施和智能体系统，它将开源组学社区OmicVerse V2转变为智能体生物学的可执行基础。OmicVerse V2提供社区基础：可扩展的AnnDataOOM兼容Rust后端、面向智能体的Python算法（用于单细胞、空间、批量和多组学分析）、单细胞基础模型接口，以及历史上以R为中心的Bioconductor/CRAN风格工作流的Python原生重构。OmicOS通过将分析函数注册为状态感知能力契约，使智能体能够检查实时数据对象、选择有效方法、执行受控工作流并记录来源，从而使该基础变得可操作。结果并非固定的流程，而是一个可编程的组学环境，智能体在其中从经过验证的社区方法而非自创工具组合真实分析。在外部和专门构建的基准测试中，OmicOS在评估系统中排名第一，在BiomniBench上达到81.2%。将OmicVerse添加到最小智能体中，使用qwen-3.6-35b将任务完成度提升了高达34.2个百分点，控制消融实验表明，收益来自基于注册的执行，而非更大的模型、文档检索或不受限制的工具暴露。同一基础设施可扩展到图谱规模数据，在Python中复现了以R为中心的工作流，并将外部病理软件转换为智能体可用的技能。在一个从全身空间图谱和“阿尔茨海默病”术语开始的发现任务中，OmicOS组合了一个非标准工作流，整合了空间表达、遗传关联、eQTL和共定位证据，提名了一个以PICALM、CD2AP和CR1为中心的结肠上皮风险轴。OmicVerse和OmicOS共同定义了AI时代组学的开放基础，展示了如何将生物方法社区转变为可靠、可扩展且可被智能体操作的发现系统。

亮点
OmicVerse 2.0将涵盖11个组学领域的694种方法整合为智能体可调用的高级API。
RebuildR自动将R/Bioconductor方法重建并演化为Python原生实现，并保持输出等价。
OmicOS建立了最先进的组学智能体框架，在通用组学基准测试中跨模型排名第一，显著提升了本地开源模型的分析能力。
生态系统模块的组合使用提名了一个与阿尔茨海默病风险相关的结肠上皮轴。
支持自动迭代演进的外部算法包可集成到OmicOS生态系统中。

## Abstract
Biology has accumulated a vast ecosystem of omics methods, but much of this ecosystem remains built for expert humans rather than scientific agents. Methods are scattered across Python packages, R/Bioconductor and CRAN workflows, command-line tools, incompatible data containers and implicit object states, making even routine analyses difficult for an AI system to choose, execute and verify reliably. Here we introduce OmicOS, a comprehensive omics ecosystem infrastructure and agent system that turns OmicVerse V2, an open-source omics community, into an executable foundation for agentic biology. OmicVerse V2 provides the community substrate: scalable AnnDataOOM-compatible rust backends, agent-friendly Python algorithms for single-cell, spatial, bulk and multi-omics analysis, interfaces to single-cell foundation models, and Python-native reconstructions of historically R-centred Bioconductor/CRAN-style workflows. OmicOS makes this substrate actionable by registering analytical functions as state-aware capability contracts, allowing agents to inspect live data objects, select valid methods, execute controlled workflows and record provenance. The result is not a fixed pipeline, but a programmable omics environment in which agents compose real analyses from verified community methods rather than inventing tools. Across external and purpose-built benchmarks, OmicOS ranked first among the evaluated systems, reaching 81.2% on BiomniBench. Adding OmicVerse to a minimal agent improved task completion by up to 34.2 percentage points with qwen-3.6-35b, and controlled ablations showed that the gains came from registry-grounded execution rather than from larger models, documentation retrieval or unrestricted tool exposure. The same infrastructure scaled to atlas-sized data, reproduced R-centred workflows in Python and converted external pathology software into agent-usable skills. In a discovery task starting from a whole-body spatial map and the term "Alzheimers disease", OmicOS composed a non-canonical workflow that integrated spatial expression, genetic association, eQTL and colocalization evidence to nominate a colon epithelial risk axis centred on PICALM, CD2AP and CR1. Together, OmicVerse and OmicOS define an open foundation for AI-era omics, showing how a community of biological methods can be transformed into a reliable, extensible and agent-operable system for discovery.

HighlightO_LIOmicVerse 2.0 consolidates 694 methods spanning 11 omics domains into agent-callable high-level APIs.
C_LIO_LIRebuildR automatically reconstructs and evolves R/Bioconductor methods as Python-native implementations under output-equivalence gates.
C_LIO_LIOmicOS establishes a state-of-the-art omics agent harness, ranking first on general omics benchmarks across models and substantially improving the analytical capability of local open-source models.
C_LIO_LICompositional use of ecosystem modules nominates a colon epithelial axis associated with Alzheimers disease risk.
C_LIO_LIExternal algorithm packages supporting automatic iterative evolution can be integrated into the OmicOS ecosystem.
C_LI

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：生物学积累了庞大的组学方法生态系统，但这些方法分散在 Python 包、R/Bioconductor 和 CRAN 工作流、命令行工具、不兼容的数据容器以及隐式对象状态中，绝大部分是为人类专家而非科学智能体设计的。
- **核心问题**：AI 系统（科学智能体）难以可靠地选择、执行和验证常规的组学分析，因为缺乏统一的、状态感知的可执行基础设施。
- **整体意义**：提出 OmicOS（组学生态系统基础设施与智能体系统），将开源组学社区 OmicVerse V2 转变为智能体生物学的可执行基础，使 AI 能够从经过验证的社区方法而非虚构工具组合真实分析，为 AI 时代的组学发现奠定开放、可靠、可扩展的基础。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将分散的组学方法注册为“状态感知能力合约”（state-aware capability contracts），使智能体能够实时检查数据对象、选择有效方法、执行受控工作流并记录来源。结果不是固定的流程，而是一个可编程的组学环境。
- **关键技术细节**：
  - **OmicVerse V2 社区基础设施**：
    - 提供可扩展的 AnnDataOOM 兼容 Rust 后端。
    - 面向智能体的 Python 算法，覆盖单细胞、空间、批量、多组学分析。
    - 单细胞基础模型接口。
    - **RebuildR**：自动将历史上以 R 为中心的 Bioconductor/CRAN 风格工作流重建为 Python 原生实现，并保证输出等价。
  - **OmicOS 智能体框架**：
    - 将分析函数注册为合约，状态感知使得智能体可动态检查当前数据对象（如维度、类型、缺失值等），只推荐有效的方法。
    - 支持组合执行与溯源记录。
    - 可集成外部算法包（支持自动迭代演进）。
- **总体流程**（文字描述）：智能体接收到任务 → 通过状态感知合约查询当前数据对象状态 → 从注册的 694 种方法中选择有效方法 → 执行受控工作流 → 记录溯源 → 输出结果，整个过程在 OmicOS 可编程环境中进行。

## 3. 实验设计：数据集/场景、基准、对比方法

- **数据集/场景**：
  - **BiomniBench**：外部和专门构建的通用组学基准测试。
  - 全身空间图谱 + “阿尔茨海默病”术语的发现任务。
  - 图谱规模数据（atlas-sized data）。
  - R 工作流复现场景。
  - 外部病理软件集成场景。
- **基准（Benchmark）**：
  - **BiomniBench**：整体评估系统在组学任务上的准确率，OmicOS 达到 81.2%，排名第一。
  - **任务完成度**：使用 qwen-3.6-35b 模型，添加 OmicVerse 后任务完成度提升高达 34.2 个百分点。
- **对比方法**：
  - 评估了多个系统，OmicOS 排名第一。
  - 消融实验：对比了无 OmicVerse 的最小智能体、更大模型（非 qwen-3.6-35b）、仅文档检索、无限制工具暴露等条件，证明收益来自“基于注册的执行”（registry-grounded execution）而非其他因素。

## 4. 资源与算力

- 论文摘要和元数据中**未明确说明**使用的 GPU 型号、数量、训练时长等算力信息。仅提到使用 qwen-3.6-35b 模型（开源大模型），但未提供运行该模型的具体硬件配置。因此无法总结算力细节。

## 5. 实验数量与充分性

- **实验数量**：
  - 主要在 BiomniBench 上评估，对比多系统。
  - 消融实验：多种条件（不同模型、有无注册、文档检索、无限制工具暴露等）至少 4 种控制实验。
  - 额外场景：图谱规模数据、R 工作流复现、外部病理软件集成、阿尔茨海默病发现任务。
- **充分性与客观性**：
  - 控制消融实验设计合理，能够归因收益来源。
  - 同时评估了外部基准（BiomniBench）和自建任务，覆盖不同规模与领域。
  - 但与方法的详细比较信息有限（未列出具体对比系统名称和所有指标），可能存在报告偏差。整体实验设计较为充分，客观性较好。

## 6. 论文的主要结论与发现

- OmicOS 在 BiomniBench 上达到 81.2%，在评估系统中排名第一。
- 将 OmicVerse 添加到最小智能体（使用 qwen-3.6-35b）后，任务完成度提升最高 34.2 个百分点，且消融证实提升来自注册式执行而非模型规模或文档检索。
- 基础设施可扩展到图谱规模数据，在 Python 中成功复现 R/Bioconductor 工作流，并集成外部病理软件。
- 在发现任务中，OmicOS 组合了非标准工作流，整合空间表达、遗传关联、eQTL 和共定位证据，提名了一个以 PICALM、CD2AP 和 CR1 为中心的结肠上皮风险轴，与阿尔茨海默病风险相关。
- OmicVerse 2.0 整合了 694 种方法（覆盖 11 个组学领域），可被智能体调用。

## 7. 优点：方法或实验设计上的亮点

- **方法创新**：首次将组学方法注册为“状态感知能力合约”，使智能体能够动态检查数据对象并选择有效方法，解决了 AI 系统在碎片化生态中盲目调用的问题。
- **生态整合**：OmicVerse V2 提供统一 Python 原生实现，并通过 RebuildR 自动将 R 工作流转化为 Python 等价实现，消除了跨语言障碍。
- **开源与可扩展**：支持外部算法包自动集成，促进社区共建。
- **实验设计亮点**：消融实验控制得当，清晰证明了核心贡献（注册式执行）而非混淆因素，结果有说服力。
- **实用性验证**：不仅通过基准测试，还通过真实的发现任务（阿尔茨海默病风险轴）展示了从数据到假设生成的全链条能力。

## 8. 不足与局限

- **实验覆盖有限**：基准测试仅提及 BiomniBench 和自行构建的任务，缺少与更多主流组学智能体系统（如 BioAgent、AutoML for omics 等）的详细对比数据，可能未能完全覆盖所有现有方法。
- **偏差风险**：OmicOS 的所有组件（OmicVerse V2）均由同一团队开发，存在自我评估的潜在偏见。虽然进行了消融，但缺乏独立第三方复现验证。
- **算力资源未报告**：未说明智能体运行所需 GPU 及内存要求，对可复现性和实际部署参考不足。
- **应用限制**：依赖于 OmicVerse 社区方法库，其覆盖度（694 种方法）虽有广度但仍可能遗漏特定领域专有方法或最新方法；对未在注册的方法，智能体无法自动使用。
- **发现任务的可信度**：虽然提名了风险轴，但摘要未提供后续实验验证（如动物模型或临床队列验证），仅为计算推测，生物学意义有限。

（完）
