---
title: "TogoMCP: Natural Language Querying of Life-Science Knowledge Graphs via Schema-Guided LLMs and the Model Context Protocol"
title_zh: TogoMCP：通过模式引导的大语言模型和模型上下文协议对生命科学知识图谱进行自然语言查询
authors: "Kinjo, A. R., Yamamoto, Y., Bustamante-Larriet, S., Labra-Gayo, J. E., Fujisawa, T."
date: 2026-05-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.03.19.713030v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 基于LLM的知识图谱查询用于生命科学发现
tldr: "TogoMCP利用大语言模型通过模型上下文协议(MCP)查询包含约60个生命科学数据库的RDF Portal知识图谱。系统通过MIE文件动态提供数据库模式上下文，并采用两阶段工作流（实体解析和SPARQL生成）。在50个生物问题的基准测试中，相比未辅助的基线有显著提升（Cohen's d=1.82），消融实验表明MIE模式文件贡献最大。结论：简洁动态的模式上下文优于复杂编排逻辑。"
source: biorxiv
selection_source: fresh_fetch
motivation: 查询RDF Portal知识图谱需要SPARQL和数据库特定RDF模式专业知识，大多数研究者无法使用该资源。
method: 将LLM作为协议驱动的推理引擎，通过MCP协调专用工具；使用MIE文件提供模式上下文，两阶段工作流分离实体解析和SPARQL生成。
result: "在50个生物问题上，TogoMCP相比未辅助基线有大幅改进（Cohen's d=1.82，Wilcoxon p<0.001），准确回答类型胜率超80%；消融实验显示MIE文件贡献最大边际收益。"
conclusion: 简洁、动态传递的模式上下文对平均分数性能比复杂编排逻辑更有价值，而程序性指导在缩小方差方面起补充作用。
---

## 摘要
查询由DBCLS维护的RDF Portal知识图谱——该图谱聚合了约60个生命科学数据库——需要熟练掌握SPARQL和特定于数据库的RDF模式，这使得大多数研究人员难以利用这一资源。大语言模型（LLM）原则上可以将自然语言问题转换为可执行的SPARQL，但如果没有模式级上下文，它们常常编造不存在的谓词或无法将实体名称解析为特定于数据库的标识符。我们提出了TogoMCP，一个将LLM重新定位为协议驱动的推理引擎的系统，通过模型上下文协议（MCP）协调专用工具。其设计有两个关键机制：（i）MIE（元数据-互操作性-交换）文件，一个简洁的YAML文档，在查询时动态地向LLM提供每个目标数据库的结构和语义上下文；（ii）一个两阶段工作流，将外部REST API的实体解析与模式引导的SPARQL生成分离。在涵盖五种类型和23个数据库的50个生物学基础问题的基准测试中，TogoMCP相比无辅助基线取得了大幅改进（Cohen's d = 1.82，Wilcoxon p < 0.001），对于具有精确、可验证答案的问题类型，胜率超过80%。消融研究表明，所有组件配置都带来了显著改进，其中MIE模式文件在每个问题平均得分上提供了最大的边际贡献（相对于无MIE条件，Δ = +0.50，双边Wilcoxon p = 0.067；90% Bootstrap CI [+0.04, +0.94] 不含零）；一条加载相关MIE文件的一行指令恢复了与完整程序化协议相同的平均改进，而该协议还额外降低了下行风险（损失率1.6% vs. 4.8%，Fisher p = 0.036）。这些结果表明一个通用设计原则：简洁、动态传递的模式上下文对于平均得分性能比复杂的编排逻辑更有价值，而程序化指导在缩小方差方面发挥补充作用。

数据库URL：https://togomcp.rdfportal.org/

## Abstract
Querying the RDF Portal knowledge graph maintained by DBCLS--which aggregates approximately 60 life-science databases--requires proficiency in both SPARQL and database-specific RDF schemas, placing this resource beyond the reach of most researchers. Large Language Models (LLMs) can, in principle, translate natural-language questions into executable SPARQL, but without schema-level context, they frequently fabricate non-existent predicates or fail to resolve entity names to database-specific identifiers. We present TogoMCP, a system that recasts the LLM as a protocol-driven inference engine orchestrating specialized tools via the Model Context Protocol (MCP). Two mechanisms are essential to its design: (i) the MIE (Metadata-Interoperability-Exchange) file, a concise YAML document that dynamically supplies the LLM with each target databases structural and semantic context at query time; and (ii) a two-stage workflow separating entity resolution via external REST APIs from schema-guided SPARQL generation. On a benchmark of 50 biologically grounded questions spanning five types and 23 databases, TogoMCP achieved a large improvement over an unaided baseline (Cohens d = 1.82, Wilcoxon p < 0.001), with win rates exceeding 80% for question types with precise, verifiable answers. An ablation study shows that all component configurations deliver significant improvements, with MIE schema files providing the largest marginal contribution on mean per-question score ({Delta} = +0.50 relative to a no-MIE condition, two-sided Wilcoxon p = 0.067; 90% bootstrap CI [+0.04, +0.94] excludes zero); a one-line instruction to load the relevant MIE file recovers the same mean improvement as a full procedural protocol, while the protocol additionally reduces downside risk (loss rate 1.6% vs. 4.8%, Fisher p = 0.036). These results suggest a general design principle: concise, dynamically delivered schema context is more valuable than complex orchestration logic for mean-score performance, while procedural guidance plays a complementary role in narrowing variance.

Database URLhttps://togomcp.rdfportal.org/