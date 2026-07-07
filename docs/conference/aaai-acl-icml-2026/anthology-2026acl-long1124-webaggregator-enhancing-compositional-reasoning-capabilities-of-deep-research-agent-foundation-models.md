---
title: "WebAggregator: Enhancing Compositional Reasoning Capabilities of Deep Research Agent Foundation Models"
title_zh: WebAggregator：增强深度研究智能体基础模型的组合推理能力
authors: "Rui Wang, Ce Zhang, Jun-Yu Ma, Jianshu Zhang, Hongru Wang, Yi Chen, Boyang Xue, Tianqing Fang, Zhisong Zhang, Hongming Zhang, Haitao Mi, Dong Yu (于东), Kam-Fai Wong"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.1124.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 增强深度研究智能体的组合推理能力以自主聚合信息
tldr: 该论文提出WebAggregator，一种数据合成流水线，旨在增强深度研究智能体的组合推理能力。通过先行的探索者收集互联知识，再由合成逻辑提案者编织复杂问题，将范式从检索中心转向聚合中心。该方法解决了当前智能体在复杂推理中聚合稀疏证据的弱点，为自主研究中的信息综合提供了关键技术。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 802, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1635, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1646, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1648, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1505, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 631, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 650, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1505, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1644, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1632, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 243, \"height\": 241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1589, \"height\": 1096, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1508, \"height\": 139, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1512, \"height\": 142, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1124/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1529, \"height\": 1348, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1548, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1481, \"height\": 1490, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 667, \"height\": 544, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 607, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1525, \"height\": 1299, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 678, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1373, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1417, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1414, \"height\": 143, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1334, \"height\": 132, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1441, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1124/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1444, \"height\": 180, \"label\": \"Table\"}]"
motivation: 现有深度研究智能体重检索轻推理，难以进行多步分散证据聚合。
method: 设计数据合成流水线WebAggregator，包含主动探索者和合成逻辑提案者两个阶段。
result: 提升了模型在需要组合推理的任务上的表现。
conclusion: 该方法推动智能体从简单检索向复杂逻辑聚合演进。
---

## Abstract
The hallmark of Deep Research agents lies in compositional reasoning, the capacity to aggregate distributed, heterogeneous information into coherent logical insights. However, current agentic systems are often retrieval-heavy but reasoning-light, where success is predominantly determined by simple entity-seeking rather than the multi-step aggregation of scattered evidence. To address this, we propose a data synthesis pipeline WebAggregator, designed to shift the agentic paradigm from retrieval-centric to compositional aggregation. Our approach first employs Proactive Explorer to collect interconnected knowledge, then Compositional Logic Proposer to weave knowledge into complex questions using over 12 composition guidelines derived from a rigorous deconstruction of the Deep Research problem setting. Fine-tuning on this corpus fundamentally transforms agent behavior, fostering deliberate composition reasoning and reduced tool redundancy. The resulting WebAggregator-32B surpasses GPT-4.1 and matches Claude-3.7-Sonnet on GAIA, WebWalkerQA, and XBench. To address the lack of benchmarks that emphasize both reasoning and retrieval, we introduce the WebAggregatorQA testbed, which reveals that even with perfect retrieval, top-tier models still underperformed. These results demonstrate that compositional reasoning, not retrieval, is the true performance ceiling for next-generation research agents.

---

## 论文详细总结（自动生成）

# 论文详细中文总结：WebAggregator：增强深度研究智能体基础模型的组合推理能力

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有深度研究（Deep Research）智能体系统在推理能力上存在严重失衡——它们擅长检索（retrieval），但缺乏组合推理（compositional reasoning），即无法将分散、异质的信息聚合为连贯的逻辑洞察。
- **背景**：当前多跳数据集（如HotpotQA）逻辑跳跃较浅，而网页智能体基准（如WebWalkerQA、TaskCraft）偏向于简单实体定位（实体查找型问题占30%~43%），使智能体倾向于频繁调用工具而非进行深层推理。这种“重检索轻推理”的范式限制了智能体完成真实科学研究任务的能力。
- **研究含义**：论文旨在推动智能体范式从检索中心转向聚合中心，真正实现自主发现与证据综合。

## 2. 论文提出的方法论

- **核心思想**：构建一个自动化的数据合成流水线**WebAggregator**，通过两个阶段生成需要组合推理的、可验证的问答对，并用这些数据微调基础模型，从而改变智能体行为。

- **关键技术细节**：

  - **阶段1：主动探索者（Proactive Explorer）**
    - 从锚点URL出发，利用多种工具（搜索、访问、截图、文件读取、动态交互等）自主探索网页，收集互联的多样化信息。
    - 强制要求访问至少若干不同网站（通常5-8个），确保知识广度。
    - 工具库包括：Search, Visit, StrFind, Input, Click, Scroll, Goback, FileRead, Screenshot, ImageCaption。

  - **阶段2：组合逻辑提案者（Compositional Logic Proposer）**
    - 基于12种组合逻辑操作指南（分为4大类：Element、Set、Scientific Analysis、Temporal Reasoning），将收集到的原始知识编织成复杂问题。
    - 操作示例：Element → Math（加、减、比率）、Set → Filter（过滤）、Set → Intersection、Scientific Analysis → Statistic（求标准差/均值）、Correlation（皮尔逊系数）、Prediction（指数平滑）等。
    - 并非使用固定模板，而是将操作作为高层指导，由提案者实例化为具体问题。

  - **质量控制**：
    - 自我细化工具：内置检查清单，自动修正问题。
    - 数据检查代理：另一个智能体求解问题并验证URL、答案、引用的对齐性，过滤掉约11.72%的不合格样本。
    - 多样性约束：平衡领域分布（12个领域）和操作类型分布，动态调整提示词增加稀缺操作的比例。

  - **训练数据收集**：使用GPT-4.1智能体（基于SmolAgents）完成任务并记录轨迹，通过拒绝采样筛选出约6,184条高质量轨迹（要求答案正确、格式正确、保留异常页面以增强鲁棒性）。

- **数据集构建结果**：WebAggregatorQA包含9,883个任务（其中200个保留用于测试），覆盖54,064个独特URL，12个领域。

## 3. 实验设计

- **使用的数据集/场景**：
  - 训练集：WebAggregatorQA训练集（约9,683个QA对）。
  - 评估基准：GAIA-text（三个难度级别）、WebWalkerQA、XBench、WebAggregatorQA测试集（159个手工标注样本，分Level 1/2/3）。

- **对比方法**：
  - 非智能体基础模型：GPT-4.1、Claude-3.7-Sonnet、Qwen2.5/3系列（7B/32B）。
  - 零样本基础模型：同样模型通过SmolAgents初始化为智能体。
  - 微调基础模型：WebThinker、WebDancer、WebSailor、WebShaper、CognitiveKernel-Pro。
  - 主要评估指标：Pass@1和Pass@3（由GPT-4.1评估）。

- **实验设置**：
  - 模型：基于Qwen2.5和Qwen3的7B/8B/32B版本进行SFT。
  - 训练数据格式：(question, a1, o1, ..., an, on, answer)，其中a为动作代码，o为环境观察，训练时掩码问题和观察。
  - 每任务步数预算30步。

## 4. 资源与算力

- **论文未明确说明训练所使用的GPU型号、数量及训练时长**。
- 数据合成阶段依赖GPT-4.1作为智能体（每次任务约30步交互），成本较高但远低于人工标注。
- 模型微调基于Qwen2.5和Qwen3系列，使用标准SFT流程，但具体计算资源未提及。

## 5. 实验数量与充分性

- **主实验**：在GAIA、WebAggregatorQA（Table 1）、WebWalkerQA、XBench（Table 2）上对比多个模型，报告Pass@1和Pass@3。
- **分析实验**：
  - 工具使用密度与步骤分析（Figure 6, Table 5）：对比微调前后模型的行为变化（推理比例、工具调用密度）。
  - 完美检索情境下的准确率（Table 3）：仅保留访问了所有参考URL的轨迹，评估组合推理瓶颈。
  - 组合操作类型的困难度分析（Figure 7）：计算Phi系数，显示科学分析、集合操作是最大挑战。
  - 数据效率实验：仅用500/1200条轨迹微调Qwen3-8B，在GAIA上达到36.9%/38.8%。
  - 失败模式定性分析（Section 4.4）：人工检查50个案例，归纳出信息检索、智能体基础能力、组合推理三类失败。
- **充分性评估**：实验设计较为全面，覆盖了多个主流基准、多维度分析（行为、瓶颈、失败模式），对比了多种现有方法，结果客观公平。但测试集规模较小（159个），可能影响部分结论的统计显著性。

## 6. 论文的主要结论与发现

- **WebAggregatorQA训练有效提升组合推理能力**：微调后的WebAggregator-32B在GAIA上超越GPT-4.1，与Claude-3.7-Sonnet持平；在WebWalkerQA和XBench上也取得更好或相当的结果。
- **WebAggregatorQA测试集极具挑战性**：即便拥有完美检索（访问所有参考URL），Claude-3.7-Sonnet准确率仅42.1%，说明当前模型在组合推理上仍存在严重瓶颈。
- **微调改变智能体行为**：从“检索中心”转向“推理中心”——工具调用密度降低，内部推理步骤（如信息综合、逻辑推导）比例上升，总token消耗增加但主要由推理贡献。
- **组合推理是性能天花板**：检索正确并不保证任务成功，未来进步需超越检索中心的范式，专注组合推理能力。

## 7. 优点

- **自动化数据合成流水线**：无需人工标注即可生成大规模、包含深度组合推理的训练数据，可扩展性强。
- **弥补现有数据集不足**：现有数据集侧重实体查找或简单跳跃，WebAggregatorQA强调多步聚合与计算密集型推理，填补重要空白。
- **微调简单有效**：仅使用SFT+拒绝采样即可获得显著性能提升，小模型（8B）也能接近GPT-4.1，成本效益高。
- **提供新基准**：WebAggregatorQA测试集专门用于评估组合推理，揭示了当前模型的真正瓶颈。
- **深入的行为分析**：通过工具密度、推理比例、Phi系数、失败模式定性分析，提供了对智能体能力短板的细致理解。

## 8. 不足与局限

- **资源评估不透明**：未报告训练GPU型号、数量及时长，难以评估可复现性和资源需求。数据合成本身成本较高（依赖GPT-4.1的多次交互）。
- **训练方法局限**：仅使用SFT，未尝试强化学习、过程奖励模型等更先进的训练策略，可能未能充分释放数据潜力。
- **测试集规模较小**：仅159个手工标注样本，可能不足以涵盖所有组合推理类型和难度，统计显著性受限。
- **环境动态性**：Web环境（CAPTCHA、页面更新、文件下载变化）可能导致测试数据随时间失效，需持续维护。
- **模型绝对性能仍低**：即便最佳模型在WebAggregatorQA测试集上Pass@1仅约20-30%，提示组合推理难题远未解决。
- **潜在偏差**：锚点URL来源于现有QA和科学数据集，可能导致领域覆盖不均衡（如体育、金融较多，法律、艺术较少）。

（完）
