---
title: "AgencyBench: Benchmarking the Frontiers of Autonomous Agents in 1M-Token Real-World Contexts"
title_zh: AgencyBench：百万级Token真实世界上下文中自主代理前沿的基准测试
authors: "Keyu Li, Junhao Shi, Yang Xiao, Mohan Jiang, Jie Sun, Yunze Wu, Dayuan Fu, Shijie Xia, Xiaojie Cai, Tianze Xu, Weiye Si, Wenjie Li, Dequan Wang, Pengfei Liu"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.337.pdf"
tags: ["query:ar"]
score: 9.0
evidence: 面向长上下文真实世界任务的自主代理综合基准
tldr: 现有自主代理基准局限于单一能力，缺乏对长时期真实场景的评估。AgencyBench从日常AI使用中衍生，涵盖6种核心代理能力，包含32个真实场景共138个任务，每个任务平均需90次工具调用和百万级token上下文。实验揭示了当前代理在长期规划和多工具协调上的不足，为自主代理研究提供了全面且可扩展的评估平台。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.337/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 788, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.337/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1633, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.337/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1646, \"height\": 768, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.337/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1496, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.337/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1498, \"height\": 939, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.337/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1478, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.337/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1638, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.337/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 830, \"height\": 559, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.337/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1419, \"height\": 574, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.337/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 779, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.337/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 562, \"height\": 486, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.337/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 663, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.337/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1676, \"height\": 730, \"label\": \"Table\"}]"
motivation: 现有自主代理基准只关注单一能力，无法捕捉长跨度真实场景，且依赖人工反馈导致扩展困难。
method: 构建AgencyBench基准，从日常AI使用中提取32个真实场景，评估6种核心能力，共138个任务。
result: 实验显示当前代理在长期规划和多工具协调方面仍有显著不足。
conclusion: AgencyBench为自主代理提供了更具现实挑战的评估基准。
---

## Abstract
Large Language Models (LLMs) based autonomous agents demonstrate multifaceted capabilities to contribute substantially to economic production. However, existing benchmarks remain focused on single agentic capability, failing to capture long-horizon real-world scenarios. Moreover, the reliance on human-in-the-loop feedback for realistic tasks creates a scalability bottleneck, hindering automated rollout collection and evaluation. To bridge this gap, we introduce AgencyBench, a comprehensive benchmark derived from daily AI usage, evaluating 6 core agentic capabilities across 32 real-world scenarios, comprising 138 tasks with specific queries, deliverables, and rubrics. These scenarios require an average of 90 tool calls, 1 million tokens, and hours of execution time to resolve. To enable automated evaluation, we employ a user simulation agent to provide iterative feedback, and a Docker sandbox to conduct visual and functional rubric-based assessment. Experiments reveal that closed-source models significantly outperform open-source models (48.4% vs 32.1%). Further analysis reveals significant disparities across models in resource efficiency, feedback-driven self-correction, and specific tool-use preferences.

---

## 论文详细总结（自动生成）

# AgencyBench 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前基于大型语言模型（LLM）的自主代理（agent）在经济生产、科学研究、软件开发和日常使用中展现出巨大潜力，但现有评测基准存在两大严重局限：
  - **任务尺度过短**：多数基准聚焦于单一能力（如工具使用、软件工程、研究），缺乏能够反映真实世界长期、多步骤、高复杂度的长时域（long-horizon）任务。
  - **依赖人工反馈瓶颈**：完成真实任务往往需要不断的人工反馈来引导代理进行多轮交互，这严重限制了自动化的数据收集和评估扩展性。
- **整体含义**：为了突破上述瓶颈，作者提出了 **AgencyBench**，一个全面、高难度的自主代理评测基准，旨在通过模拟日常AI使用的真实场景，评估代理在**百万级Token上下文**中的综合能力，推动代理从简单工具调用向长期规划与多工具协调进化。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个分层结构的基准，包含6种核心代理能力、32个真实场景、138个具体任务；并设计**自动化评估框架**，通过用户模拟代理（User Simulation Agent）和Docker沙箱实现无需人工介入的评估。
- **关键技术细节**：
  - **层级设计**：
    - **能力（Capabilities）**：6类 —— 游戏开发、前端开发、后端开发、代码生成、研究、MCP工具使用。
    - **场景（Scenarios）**：32个真实场景，例如开发五子棋游戏、项目级代码调试、企业研究等。
    - **任务（Tasks）**：每个场景包含1~5个顺序任务，难度递增，前一个任务的完成影响后续任务；总共138个任务。
  - **工作区与评估空间**：
    - **Workspace**：每个任务在隔离的工作区内运行，配备完整工具套件（文件操作、命令行、搜索等），代理与环境多轮交互生成交付物。
    - **Eval-space**：交付物同步到远程Docker沙箱，模拟人类操作（点击、渲染等），生成视觉评估制品；再返回本地评估空间，通过可执行脚本自动评分。
  - **用户模拟代理**：当交付物未达到阈值时，用户模拟代理（基于Claude-4-Sonnet，温度0.0）提供针对性反馈，模拟人类指导。通过人类验证实验，其反馈与人类专家的一致性得分为4.69/5。
  - **评估方法**：
    - **基于规则的评估**：用于可客观验证的任务（如工具执行正确性、数学优化），直接翻译断言逻辑。
    - **LLM作为裁判（LLM-as-Judge）**：用于主观或视觉任务（如游戏美学、前端布局）。
      - **文本裁判**：评估代码质量和逻辑（Claude-4-Sonnet）。
      - **视觉裁判**：评估动态行为和视觉正确性（Gemini-2.5-pro）。
      - 最终得分取文本和视觉裁判的平均值；仅文本任务则仅用文本裁判。
  - **Rollout形式化定义**：每个场景的rollout τ 由顺序任务轨迹拼接而成，包含初始查询、代理推理与工具调用、用户模拟代理反馈等，捕获了长期性和迭代性。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集/场景**：
  - AgencyBench自身包含32个场景、138个任务，覆盖6种能力。
  - 示例：五子棋游戏开发（5个递进任务）、全栈前端开发、后端开发、代码调试、企业研究、MCP工具使用等。
- **Benchmark对比**：
  - 与现有基准对比（见表1）：AgencyBench在平均Token（1000k）、平均轮次（90）、多样化能力、用户模拟、Docker沙箱等方面全面超越Browsecomp、Terminal-bench、SWE-bench-verified、MCPUniverse、GAIA2、Toolathlon、UltraHorizon等。
- **对比方法（模型）**：
  - **闭源模型**：GPT-5.2、Claude-4.5-Opus、Claude-4.5-Sonnet、Gemini-3-Pro、Grok-4.1-fast。
  - **开源模型**：GLM-4.6、Kimi-K2-Thinking、DeepSeek-V3.2、Qwen-3-235B-A22B-Thinking。
  - 所有模型通过OpenRouter API访问，温度设为0.7。
  - 使用自研代理脚手架（带完整工具集），另外在10个代表性场景上消融了Claude-Agent-SDK和OpenAI-Agents-SDK。

## 4. 资源与算力

- **文中明确说明**：未提及使用的GPU型号、数量、训练时长等信息。仅提到所有模型通过OpenRouter API调用，未描述本地计算资源。
- **论文指出**：AgencyBench的每个场景平均消耗100万token、90次工具调用、数小时执行时间（见表5：GPT-5.2平均3.4M token、0.6h；Grok-4.1-fast平均1.2M token、0.3h等），但未说明计算集群规模。
- → **算力信息缺失**，未提供具体硬件配置，仅能从token消耗和运行时间间接推断计算需求较大。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验：8个模型在138个任务上的完整评估（每个任务评分0-10，计算平均分等）。
  - 消融实验：3种不同脚手架在10个代表性场景上的对比（表4）。
  - 用户模拟代理有效性验证：50个随机样本，4名人类专家评分，进行一致性分析（Kappa=0.93）。
  - LLM裁判可靠性验证：50个任务的文本与视觉裁判对比人类注释，Kappa=0.93。
  - 效率分析：Token效率、尝试效率等（图4）。
  - 工具调用频率分析（表8）。
  - 反馈驱动自纠正分析（Pass@1, Pass@2 – 表3）。
- **充分性与公平性**：
  - 实验设计较为全面：覆盖不同规模、不同闭源/开源模型，且涉及多种指标（平均分、尝试次数、通过率、效率等）。
  - 消融实验考虑了脚手架影响，揭示“生态协同”效应。
  - 交叉验证了评估器（LLM裁判和人类一致性高）。
  - **潜在局限**：只评估了部分代表性模型，未覆盖所有最新变体；场景仅限数字环境，不包含物理世界任务；开放性任务（如研究）的评分可能存在主观偏差。

## 6. 论文的主要结论与发现

- **闭源模型显著优于开源模型**：平均分48.4% vs 32.1%。
- **性能排名**：GPT-5.2 (56.5%) > Claude-4.5-Opus (47.7%) > Gemini-3-Pro (46.9%) > Claude-4.5-Sonnet (46.4%) > Grok-4.1-fast (44.3%)；开源中GLM-4.6最高 (38.6%)。
- **能力专长差异**：Gemini-3-Pro在游戏和前端任务领先；GPT-5.2在后端和代码任务最强；Claude-4.5-Sonnet在研究能力突出。
- **反馈驱动自纠正能力**：GPT-5.2和Claude系列提升显著（>80%），而DeepSeek-V3.2提升为0%，固守错误路径。
- **资源效率**：Grok-4.1-fast在Token效率上最优（37.2%），GPT-5.2在尝试效率上最优（38.7%）；Claude-4.5-Sonnet Token效率最低（11.4%）。
- **工具使用偏好**：Claude和GPT偏好Shell执行；Gemini擅长记忆工具；GLM偏好文件写入；Grok和GLM依赖网络搜索。
- **脚手架影响显著**：模型与原生脚手架有“生态协同”（如Claude-4.5-Opus在Claude-Agent-SDK上提升20.5%），开源模型对脚手架敏感。
- **整体表现仍不理想**：最佳模型仅56.5%，说明当前代理在长期真实任务中仍有巨大提升空间。

## 7. 优点

- **任务设计真实且长时**：平均100万Token、90次工具调用、数小时执行，远超现有基准，更好地反映实际应用。
- **自动化评估框架**：通过用户模拟代理和Docker沙箱实现完全自动化，避免人工干预瓶颈，具有可扩展性。
- **多维度评估指标**：不仅报告平均分，还引入尝试次数、通过率、效率、工具调用模式等，全面刻画代理行为。
- **脚手架消融实验**：揭示了模型与框架的耦合效应，提升了对代理性能来源的理解。
- **分层结构**：任务从简单到复杂递进，自然模拟真实项目开发流程。
- **人类验证**：对用户模拟代理和LLM裁判均进行了人工一致性检验，确保评估可靠性。

## 8. 不足与局限

- **模型覆盖不全**：仅评估了部分代表性模型，未包含所有最新模型、中间检查点或微调版本，不能反映全貌。
- **领域特异**：仅限数字环境中的任务（游戏开发、软件开发、研究等），未扩展到具身代理或物理世界交互（如机器人）。
- **开放任务主观偏差**：对于研究、美学等主观性任务，LLM裁判虽有较高一致性，但仍有潜在偏差。
- **算力信息缺失**：未报告训练或评估使用的具体GPU数量、型号、资源消耗，影响可复现性和成本估计。
- **安全风险**：代理生成可执行代码和Shell操作，虽通过隔离Docker容器缓解，但仍有潜在的恶意使用风险（作者已声明反对）。
- **静态基准**：任务固定，不能像在线环境那样动态演化，可能无法完全反映代理的泛化能力。

（完）
