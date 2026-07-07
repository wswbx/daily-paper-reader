---
title: A Survey on Evaluation of LLM-based Agents
title_zh: LLM智能体评估综述
authors: "Asaf Yehudai, Lilach Eden, Alan Li, Guy Uziel, Yilun Zhao, Roy Bar-Haim, Arman Cohan, Michal Shmueli-Scheuer"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1330.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 关于LLM智能体评估的综述，涵盖自主研究
tldr: LLM智能体在自主研究等场景中至关重要，但其评估缺乏系统性。本文首次全面综述了LLM智能体的评估方法，从核心能力、特定应用基准、通用智能体评估、基准维度分析和评估工具五个视角展开。揭示了评估向更真实、更连续更新的基准发展的趋势。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1330/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1656, \"height\": 984, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1330/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1656, \"height\": 1979, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1330/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 815, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1330/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1654, \"height\": 294, \"label\": \"Table\"}]"
motivation: LLM智能体评估分散且不统一，需要系统化梳理。
method: 从五个维度综述现有评估方法，包括核心能力、应用基准、通用评估等。
result: 总结了当前评估趋势，指出现有方法的不足。
conclusion: 提供了LLM智能体评估的全面参考，推动自主研究评估规范化。
---

## Abstract
LLM-based agents represent a paradigm shift in AI, enabling autonomous systems to plan, reason, and use tools while interacting with dynamic environments. This paper provides the first comprehensive survey of evaluation methods for these increasingly capable agents. We analyze the field of agent evaluation across five perspectives: (1) Core LLM capabilities needed for agentic workflows, like planning, and tool use; (2) Application-specific benchmarks such as web and SWE agents; (3) Evaluation of generalist agents; (4) Analysis of agent benchmarks’ core dimensions; and (5) Evaluation frameworks and tools for agent developers. Our analysis reveals current trends, including a shift toward more realistic, challenging evaluations with continuously updated benchmarks. We also identify critical gaps that future research must address—particularly in assessing cost-efficiency, safety, and robustness, and in developing fine-grained, scalable evaluation methods.

---

## 论文详细总结（自动生成）

# LLM智能体评估综述——详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：LLM基础模型是静态的，无法自主规划、使用工具或与动态环境交互。LLM智能体通过将LLM作为骨干，集成外部工具和多步工作流，实现了自主决策能力。然而，传统的LLM评估仅关注文本输出，无法衡量智能体在序列决策、环境交互方面的表现。因此，需要全新的评估范式。
- **整体含义**：本文是首篇系统综述LLM智能体评估的论文，为开发者、基准创建者、从业者和研究者提供了当前评估格局的全面地图，并指出了关键研究空白和未来方向。它标志着智能体评估从孤立能力测试向真实、动态、多维度评估的转变。

## 2. 论文提出的方法论

- **核心思想**：采用**五维度分析框架**，对智能体评估进行全面分类与剖析：
  1. **核心LLM能力评估**：规划与多步推理、函数调用与工具使用、自我反思、记忆。
  2. **特定应用智能体评估**：网络智能体、软件工程智能体、科学智能体、对话智能体。
  3. **通用智能体评估**：如GAIA2、OSWorld、AgentBench等跨域基准。
  4. **基准核心维度分析**：数据策展、环境动态性、交互界面、评估指标、安全性与鲁棒性。
  5. **评估框架与工具**：开发框架（LangSmith、Langfuse等）和类Gym环境（BrowserGym、SWE-Gym等）。
- **关键技术细节**：
  - 对每个能力领域，梳理了从早期简化基准（如BFCL v1）到现代复杂基准（如BFCL v3、ComplexFuncBench）的进化路径。
  - 在应用层面，对比了静态环境（如Mind2Web）与动态环境（如WebArena）的优缺点，分析了不同接口（代码/终端、工具、GUI）的适用场景。
  - 在基准维度分析中，引入了“安全性与鲁棒性”作为独立维度，指出当前基准普遍缺乏对策略合规、风险规避的评估。
- **算法流程**：本文主要是分类学综述，没有提出新算法，但提供了结构化图谱（图1）和比较表格（表1、表2）来组织知识。

## 3. 实验设计

- **数据与场景**：本文为综述，自身不进行实验，但系统梳理了超过100个现有基准和框架，覆盖以下主要类别：
  - **核心能力**：PlanBench、BFCL、LLM-Evolve、StreamBench等。
  - **应用基准**：
    - 网络：WebShop、Mind2Web、WebArena、WebVoyager。
    - 软件工程：SWE-bench、SWE-bench Verified、SWE-Lancer、Terminal-Bench。
    - 科学：SciCode、ScienceAgentBench、PaperBench、AAAR-1.0。
    - 对话：τ-Bench、τ²-Bench、IntellAgent、ALMITA。
  - **通用智能体**：GAIA2、OSWorld、AppWorld、AgentBench、HAL。
- **对比方法**：论文对比了不同基准在数据策展方式（人工 vs 混合 vs 合成）、环境类型（静态 vs 动态）、交互接口（代码、工具、GUI）、评估指标（单元测试、状态匹配、答案匹配）以及是否包含安全约束等维度的差异（见表1）。
- **框架对比**：表2对比了LangSmith、Langfuse、Vertex AI、Galileo等8个框架在分步评估、监控、轨迹评估、人机协同、A/B比较等能力上的支持情况。

## 4. 资源与算力

- **未提及**：作为综述论文，本文没有报告任何自身实验的算力消耗（GPU型号、数量、训练时长等）。所有引用的基准和框架各自在其原始论文中可能有算力说明，但本文未汇总。

## 5. 实验数量与充分性

- **数量**：本文自身没有实验，但覆盖了**超过100个**基准/框架，涵盖5个主要维度、4类应用领域、多种评估框架。引用文献超过200篇。
- **充分性**：
  - **充分**：分类体系涵盖从基础能力到应用、从静态到动态、从能力到安全的完整链条，具有一定系统性。
  - **客观性**：论文基于公开文献和已知基准，分析基于事实和引用，无明显偏向。但部分分类边界可能存在主观性（如“通用智能体”与“应用特定”的划分）。
  - **局限性**：由于领域发展极快，论文承认其“快照”性质，可能遗漏最新（截止2026年中期）的进展。同时，深度受限于广度，每个基准的细节分析有限。

## 6. 论文的主要结论与发现

- **趋势1：真实性与挑战性增强**。智能体评估从简化静态环境转向动态、真实世界的复杂场景（如WebArena、SWE-bench使用真实GitHub issue）。
- **趋势2：基准持续更新（Live Benchmarks）**。为避免过时和饱和，基准不断迭代（如BFCL v1→v3，SWE-bench→Verified→Pro），并采用MCP等新生态。
- **关键空白**：
  - **粒度不足**：大多数基准只给出粗粒度的端到端成功/失败，缺乏对中间步骤（工具选择、推理质量）的细粒度诊断。
  - **成本与效率缺失**：当前评估几乎不考虑token消耗、API费用、推理时间等资源成本，导致鼓励过度消耗。
  - **安全与合规薄弱**：很少有基准明确测试策略合规、数据隐私、对抗鲁棒性等安全维度。
  - **LLM与Harness耦合**：现有基准无法区分性能提升来自骨干LLM还是智能体管道（scaffold）设计，需要解耦评估。
- **评估框架不足**：虽然现有框架支持轨迹级评估，但缺乏大规模因果归因和成本感知能力。

## 7. 优点

- **全面性**：首次将LLM智能体评估的五个关键维度系统化，覆盖从能力、应用到工具，结构清晰。
- **实用性**：在附录E中给出了面向不同场景的基准推荐（如WebArena用于动态网络，SWE-bench Verified用于编码），为实践者提供直接指导。
- **前瞻性**：识别了粒度评估、成本度量、安全合规、解耦评估等未来方向，对领域发展有引导意义。
- **分析深度**：不仅列举基准，还深入剖析了基准的维度（数据策展、环境、接口、指标、安全），揭示了结构性的共性与漏洞。
- **更新机制**：设立了持续更新的GitHub仓库，以跟踪最新工作，缓解综述的时效性问题。

## 8. 不足与局限

- **快照性**：领域发展极快，部分最新基准（如截止2026年6月后出现的）可能未被纳入，论文本身承认这一点。
- **深度受限**：由于覆盖范围极广，对每个基准/框架的详细实现、优缺点分析不够深入，读者需查阅原始文献获取细节。
- **主观分类**：五个维度的划分虽合理，但边界模糊（如“通用智能体”与“应用特定”之间存在重叠），可能导致不同视角解读。
- **缺乏实证**：作为综述，本文没有进行任何跨基准的复现实验或元分析，无法提供量化比较结果（如各模型在不同基准上的实际得分排序）。
- **安全与合规分析尚浅**：虽然指出了安全是缺失维度，但未提供系统的安全基准分类或构建建议，仅停留在呼吁层面。
- **未讨论评估偏差**：没有深入探讨LLM作为评判者（LLM-as-a-judge）的可靠性、基准数据泄漏、测试集污染等评估偏差问题。

（完）
