---
title: "SciExplore: Evaluating Autonomous Agents from Scientific Navigation to Information Integration"
title_zh: SciExplore：从科学导航到信息集成评估自主智能体
authors: "Yinhao Tang, Youqing Fang, Yanan Sun, Wenran Liu, Weiming Zhang, Bin Liu, Kuikun Liu, Wenwei Zhang, Kai Chen"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1117.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 评估科学研究中自主智能体的基准
tldr: 该论文针对现有基准缺乏评估真实科研工作流能力的问题，提出SciExplore基准。涵盖数据库导航、模糊文献检索、缺失引用补全和跨源知识合成等四大类103个专家精选任务，全面评估LLM和智能体的科学信息寻求与推理能力。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1645, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1615, \"height\": 843, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 787, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 747, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 738, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1636, \"height\": 595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1634, \"height\": 611, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 130, \"height\": 120, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 132, \"height\": 119, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 135, \"height\": 135, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 134, \"height\": 136, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 130, \"height\": 121, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 131, \"height\": 120, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 134, \"height\": 138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1117/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1473, \"height\": 736, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1117/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1653, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1117/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1653, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1117/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1655, \"height\": 778, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1117/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 689, \"height\": 725, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1117/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 802, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1117/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1108, \"height\": 777, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1117/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1264, \"height\": 628, \"label\": \"Table\"}]"
motivation: 现有基准侧重通用检索或静态问答，无法评估真实科研工作流。
method: 构建包含四大类103个跨学科任务的基准，评估科学信息寻求与推理。
result: 实验揭示了当前模型在复杂科学导航中的不足。
conclusion: SciExplore为评估自主科研智能体提供了标准化框架。
---

## Abstract
Scientific research involves complex information-seeking and reasoning workflows across heterogeneous sources. However, existing benchmarks primarily emphasize general-domain retrieval or static scientific question answering, and therefore fail to assess key capabilities required in realistic scientific research workflows. We introduce SciExplore, a benchmark designed to evaluate scientific information-seeking and reasoning capabilities of LLMs and agents. SciExplore comprises four task types covering 103 expert-curated tasks across more than ten scientific disciplines: scientific database navigation, ambiguous literature retrieval, missing reference completion, and cross-source structured knowledge synthesis, which probe progressively higher-level abilities from entity-level reasoning and document-level identification to evidence-level grounding and domain-level synthesis. We evaluate over ten state-of-the-art LLMs and autonomous agents on SciExplore, revealing substantial performance gaps with performance degrading sharply as task complexity increases and extremely low accuracy on the most challenging structured synthesis tasks. These results highlight significant limitations of current models and agents in realistic scientific information-seeking scenarios.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：科学发现日益数据密集和跨学科，大语言模型（LLM）及智能体被期望成为自主的科学助手，执行复杂的科研工作流。然而，现有评估基准主要侧重通用领域的检索（如 BrowseComp、WideSearch）或静态科学问答（如 GPQA、SciBench），未能涵盖真实科研流程中的关键能力：如导航专业数据库、根据模糊描述定位文献、将主张与证据对应、以及跨异构源综合结构化知识。因此，亟需一个能系统评测这些能力的标准化基准。
- **整体含义**：论文旨在弥合通用深度搜索基准与静态科学问答之间的鸿沟，提出 SciExplore 基准，对 LLM 和智能体的科学信息寻求与推理能力进行层次化、多维度的评估，揭示当前系统在真实科研场景中的显著不足，为下一代科学 AI 的发展方向提供指引。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：科学信息寻求是一个渐进的认知过程，从定位单个实体，到识别相关文档，再到将主张锚定于证据，最后综合形成领域层次的结构化知识。SciExplore 据此设计四种任务类型，依次考察从实体级到领域级的核心能力。
- **关键技术细节与任务定义**：
  - **T1：科学数据库导航（Scientific Database Navigation）**  
    考察实体级推理能力，要求智能体在多约束条件下遍历结构化科学数据库（如 PubChem、UniProt、Materials Project），通过多跳属性约束定位精确实体。构建采用“反向轨迹构建策略”，将显式实体标识逐步替换为嵌套的属性约束，迫使模型进行真正的多步推理，防止直接查找。
  - **T2：模糊文献检索（Ambiguous Literature Retrieval）**  
    考察文档级识别能力，为模拟早期探索性研究中的不确定性，专家通过“特征去噪和模糊化”故意掩盖表面线索，同时通过“验证约束注入”增加后验验证条件（如发表期刊、作者），迫使智能体在扩大搜索空间后严格验证。
  - **T3：缺失引用补全（Missing Reference Completion）**  
    考察证据级基础能力，从高影响力科学文献中选择引文密集的段落，系统改写上下文以消除与原始引用的表面文本重叠，迫使模型理解主张-证据关系，而非关键词匹配，准确补全缺失的参考文献。
  - **T4：跨源结构化知识综合（Cross-Source Structured Knowledge Synthesis）**  
    考察领域级综合能力，基于专家策划的比较模式，要求智能体从多篇文献中提取异质方法细节，填充到严格格式化的对比表格中，强调跨源一致性、模式遵从和高精度综合。

- **质量控制（Three-Stage Quality Control）**：
  - 查询难度校准：显式索引阻断（移除唯一标识符，迫使语义匹配）和长尾实体偏好（优先选择冷门实体），确保任务需要深度检索推理而非记忆。
  - 人工交叉验证：标注者尝试在10分钟内用搜索引擎解决问题，仅保留无法直接找到答案的任务。
  - 答案唯一性验证：使用搜索增强的 LLM 生成候选方案，再由人工审查是否存在替代答案，若有则丢弃该任务。

## 3. 实验设计：使用的数据集/场景、基准、对比方法

- **数据集/场景**：SciExplore 基准包含 103 个专家精心策划的任务，覆盖超过 10 个科学学科（材料科学、药理学、有机化学、基因组学、蛋白质组学、生态学、LLM、晶体学、物理化学、计算机视觉、微生物学、神经科学等），集成 16 个权威科学数据库（如 PubChem、Materials Project、Open Targets、UniProt、DrugBank、ChEMBL 等）。任务分为 T1（39 个）、T2（32 个）、T3（14 个）、T4（18 个），形成从简单到复杂的渐进评估套件。
- **基准（Benchmark）**：SciExplore 本身即作为基准，与现有基准的比较如表 1 所示（对比 HotpotQA、BrowseComp、WideSearch、DeepResearchBench、ScienceQA、SciBench、SuperGPQA、HLE 等），突出 SciExplore 在科学知识与推理深度、搜索宽度、搜索源（科学数据库与文献）和输出格式（短文本、引用、表格）方面的全面性。
- **对比方法**：评估了三大类共 12 个系统：
  - **基础 LLM**：开源模型（DeepSeek-V3.2、Qwen2.5-72B-Instruct、Qwen3-30B-A3B-Thinking、Qwen3-235B-A22B-Thinking）；闭源模型（GPT-5.1、Gemini-2.5-Pro、Gemini-3-Pro）。
  - **带搜索工具的 LLM**：为 GPT-5.1 和 Gemini-3-Pro 启用搜索 API 或网页浏览能力。
  - **专用深度研究智能体**：Tongyi-DeepResearch-30B-A3B（开源）、Gemini Deep Research（闭源）、OpenAI Deep Research（闭源）。
- **评估指标**：
  - T1/T2：精确匹配准确率（F_em）。
  - T3：基于精确率和召回率的 F_score。
  - T4：单元格级召回率（Item Recall）和行级召回率（Row Recall）。
  - 总体分：加权平均（T1/T2 各 0.2，T3/T4 各 0.3）。

## 4. 资源与算力

- **论文中未明确说明**所用 GPU 型号、数量、训练时长等硬件资源。实验主要基于 API 调用（GPT-5.1、Gemini-3-Pro 等）和开源模型权重推理，未涉及模型训练或大规模微调。因此无法提供具体的算力消耗数据。

## 5. 实验数量与充分性

- **实验数量**：主实验（表 3）覆盖了 12 个模型的完整 4 类任务结果。此外还包括：
  - 搜索调用次数分析（图 3）。
  - 多跳（hop）长度对比分析（表 6、图 4）。
  - T4 格式准确率和主键召回率分析（表 4）。
  - 运行间方差分析（表 7，每个模型 4 次重复）。
  - 误差分析：定性案例（图 8-12）和定量故障模式。
- **充分性与公平性**：实验设计较为充分，覆盖了主流模型类型（开源/闭源、有无搜索、深度研究智能体），并使用统一评估脚本和 LLM 裁判。通过多次重复运行验证稳定性（方差平均 0.78，表明噪声小）。但任务数量有限（103 个），可能对统计显著性有一定影响。论文自身承认规模与学科覆盖的权衡，但强调专家设计的质量控制保证了难度和独特性。总体而言，实验在给定基准下是客观、公平的。

## 6. 论文的主要结论与发现

- **整体性能不足**：即使最强系统（OpenAI Deep Research）总体分仅 49.39%，大多数系统低于 20%。性能随任务复杂度增加急剧下降。
- **跨源结构化综合（T4）是最大瓶颈**：顶级智能体在这类任务上的准确率低于 20%（行级），系统往往能恢复孤立事实但无法组装成完整、一致的输出。
- **搜索强度与性能正相关**：更多搜索调用的系统性能更优，深研究智能体优势明显。
- **多跳深度与人类理解不一致**：对 LLM 智能体而言，跳数并不简单对应难度，因其采用“猜测-验证”策略而非人类式结构化过滤。
- **典型失败模式**：过早放弃、幻觉（在搜索停滞时捏造细节）、长上下文信息丢失（关注摘要忽略正文细节）、指令遵循不匹配（表格格式错误）、主键召回不足（搜索广度不够）。

## 7. 优点：方法或实验设计上的亮点

- **层次化任务设计**：四大任务类型映射真实科研认知过程（实体→文档→证据→领域），全面覆盖信息寻求与推理的多层次能力。
- **严谨的数据构建与质量控制**：手动专家构造、反向轨迹构建、特征模糊化、多轮验证（难度校准、人工交叉验证、答案唯一性验证），确保高质量、防记忆、防捷径。
- **多维评估指标**：针对不同任务采用不同度量（准确率、F_score、单元格/行级召回），并设加权总体分，评估更细致。
- **深入的分析**：不仅报告主结果，还分析搜索努力、多跳难度错位、误差模式（含具体案例），提供宝贵见解。
- **开放式提示和代码**：论文提供完整 prompt 模板和 API 标识，可复现性高。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **规模有限**：只有 103 个任务，虽高质量但可能无法覆盖所有学科和科研风格，统计效力受限。
- **模态局限**：当前仅关注文本（数据库和文献），未包含图表、实验数据、代码等模态，而真实科研常涉及多模态。
- **依赖专家手动维护**：任务需专家持续更新以保证答案时效性，可扩展性差。
- **评估成本高**：需要多次 API 调用（尤其是深度研究智能体），且人工裁判和 LLM 裁判结合，评估流程复杂。
- **潜在领域偏差**：数据库和学科分布有一定长尾，某些专业领域样本过少（如只含1个任务），可能对特定领域的推广性不足。
- **缺乏因果推理**：基准侧重信息寻求和检索综合，未涵盖实验设计、假设生成等更高阶科研认知。

（完）
