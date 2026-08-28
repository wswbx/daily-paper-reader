---
title: An AI System for Autonomous Algorithm Evolution in Drug Development
title_zh: 一种用于药物开发中自主算法进化的人工智能系统
authors: "Zhou, Z., Nan, Y., Mou, M., Qian, Y., Liu, Y., Zuo, Z., Yang, H., Xu, W., Li, B., Jiang, W., Ren, Y., Liao, Y., Wang, Y., Li, Y., Yang, Q., Xi, Z., Mi, T., Sun, H., Liu, P., Zhu, F."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.16.745117v1.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 面向药物开发的自主算法进化AI系统
tldr: 药物开发各阶段算法依赖专家设计与任务特定优化，且多阶段收益具有累积协同效应，亟需全流程自主进化。DrugEvolve构造多角色大语言模型系统，集成研究员、工程师、分析员，在科学知识与演变经验引导下闭环迭代，实现算法设计、实现、评估、精炼。在覆盖靶点识别、药物发现、临床前及临床试验的十一个任务上，于一百二十个基准集获得显著性能提升，并展示跨序列、图、拓扑、文本等模态及预测、生成双类泛化能力。该系统不仅为药物研发提供可自主进化的算法基础设施，也为更广泛科学领域提供可迁移范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有药物开发算法依赖专家设计与任务特定优化，且多阶段效益具有累积协同性，亟需面向全流程的自主算法进化。
method: DrugEvolve使大语言模型扮演研究员、工程师、分析员，在科学知识与历史经验辅助下，闭环迭代执行算法设计、实现、评估与精炼。
result: 在十一个任务一百二十个基准集上性能显著提升，并跨序列、图、拓扑、文本模态及预测、生成任务泛化。
conclusion: 可作为药物研发的自主进化算法基础设施，亦为更多科学领域提供可迁移范式。
---

## 摘要
人工智能（AI）正日益渗透到药物开发流程中。人们已经构建了许多用于加速这一多阶段、多任务过程的算法，这在很大程度上依赖于专家设计和劳动密集型的特定任务优化。鉴于AI驱动的药物开发加速被认为是跨多个阶段的累积、通常是协同效应，需要在全流程中实现现有算法的自主进化，以达成整体性进步。在这里，我们提出了DrugEvolve，一个用于药物开发中系统和自主算法进化的多角色大语言模型系统。DrugEvolve通过整合研究员、工程师和分析师领域，实现了闭环进化过程，并利用科学知识和累积的进化经验，实现了算法的迭代设计、实现、评估和优化。在涵盖靶点识别、药物发现、临床前研究和临床试验的十一个代表性任务中，DrugEvolve自主进化出相应的任务特定算法，并在120个基准测试集上实现了显著的性能提升。此外，它在异构数据模态（从生物序列和图到分子拓扑和文本语言）中显示出强大的泛化能力，并在预测和生成任务中都取得了收益。总的来说，这一人工智能系统不仅可以作为药物开发的算法基础设施，也可以作为更广泛科学领域的可迁移范式。

## Abstract
Artificial intelligence (AI) is increasingly permeating the drug development pipeline. Numerous algorithms for accelerating this multi-stage and multi-task process have been constructed, which depends heavily on expert design and labor-intensive task-specific optimization. Given that AI-driven acceleration of drug development is recognized as a cumulative, often synergistic, effect across multiple stages, the autonomous evolution of existing algorithms across the entire pipeline is demanded to achieve a holistic advancement. Here, we present DrugEvolve, a multi-role large language model system for systematic and autonomous algorithm evolution in drug development. DrugEvolve realizes a closed-loop evolution process by incorporating Researcher, Engineer, and Analyst domains, and enables an iterative design, implementation, evaluation, and refinement of algorithm by leveraging scientific knowledge and accumulated evolutionary experience. Across eleven representative tasks spanning target identification, drug discovery, preclinical study, and clinical trial, DrugEvolve autonomously evolved the corresponding task-specific algorithms and achieved substantial performance enhancement on 120 benchmark test sets. Moreover, it showed robust generalizabilities across heterogeneous data modalities (ranging from biological sequence and graph to molecular topology and textual language), and realized gains in both predictive and generative tasks. Collectively, this AI system can serve not only as an algorithmic infrastructure for drug development, but also as a transferable paradigm for broader scientific domains.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究背景**：药物开发是一个漫长且成本高昂的多阶段过程（靶点识别、药物发现、临床前研究、临床试验），每一阶段都依赖高度专业化的计算工具和算法来加速。然而，现有算法的设计严重依赖人类专家的直觉与劳动密集型的任务特定优化，开发周期漫长（例如 AlphaFold 从 1.0 到 3.0 耗时近六年）。同时，AI 对药物开发的加速是跨阶段累积且协同的效应，仅优化单个任务不足以实现整体效率提升，亟需覆盖全流程的算法自主进化能力。
- **核心问题**：能否构建一个 AI 系统，在药物开发的全流程中自主、持续地进化现有算法，从而摆脱对人工反复“设计-训练-评估-改进”闭环的依赖？
- **整体含义**：论文提出 **DrugEvolve**，一个多角色大语言模型（LLM）系统，能够以人类已建立的算法为起点，自主完成算法设计、实现、评估和精炼的闭环迭代。该系统在 11 个代表性任务、120 个基准测试集上取得了显著性能提升，不仅为药物开发提供了可自主进化的算法基础设施，也为更广泛科学领域提供了可迁移的自主算法进化范式。

## 2. 论文提出的方法论

- **核心思想**：DrugEvolve 将算法开发视为一个可自动化的闭环进化过程，模拟人类科研团队中研究员、工程师与分析员的分工协作，借助科学知识（Cognition Library）和累积进化经验（Evolutionary Database）实现算法的持续迭代优化。
- **系统框架**：
  - **Researcher 领域**：由 Generator、Inspector、Implementer 三个智能体组成。Generator 从 Cognition Library 和 Evolutionary Database 中检索相关知识，提出候选算法设计方案；Inspector 评估方案的概念新颖性与科学性；Implementer 将验证通过的方案转化为可执行代码。
  - **Engineer 领域**：负责算法实现、调试、模型训练与性能评估。Trainer 执行训练流程，Debugger 处理运行错误，Judger 依据任务特定的定量指标评估候选算法性能，并可结合 LLM 定性评估。
  - **Analyst 领域**：系统分析进化结果，识别成功或失败的因素，推断后续优化方向，并将分析报告存入 Evolutionary Database，供后续迭代复用。
- **关键组件**：
  - **Cognition Library（认知库）**：收录已整理的文献知识、领域专业知识和既往实验/计算研究结论，为 LLM 提供补充科学上下文，支撑有依据、可解释的算法进化。
  - **Evolutionary Database（进化数据库）**：以 JSON 格式存储算法设计、性能评估结果和分析报告，支持按实验 ID、执行顺序和上下文相似度检索，实现进化知识的持续积累。
  - **采样策略**：提供两种互补策略——UCB1 算法（平衡高效用候选的利用与低频候选的探索）和基于岛屿的进化采样（适用于高度异构、崎岖的搜索空间，并整合 MAP-Elites 风格行为特征归档），以支持不同任务特征的进化搜索。
- **闭环流程**：人类科学家定义任务描述、基线模型、数据集和评估指标 → DrugEvolve 自主循环执行“问题解析 → 算法设计 → 实现调试 → 评估 → 反馈 → 迭代优化”，直至达到预设目标。

## 3. 实验设计

论文选取了覆盖药物开发四大阶段的 **11 个代表性任务**，共 **120 个基准测试集**：

- **靶点识别阶段**：
  - 癌症基因模块检测：使用 MCF-7 乳腺癌多组学数据集，10 折交叉验证，对比基线 CGMega。
  - 基因-疾病关联预测：使用 DisGeNET-EVAL 基准（5 次独立随机划分）及外部 TDC 数据集，对比基线 FusionGDA。
  - 蛋白可药性位点注释：使用 6 类非共价结合位点数据集（DNA、RNA、蛋白、肽、小分子、糖类相互作用）进行进化优化，并额外在 79 个独立测试集（覆盖共价结合位点、催化位点、隐秘位点、翻译后修饰位点等未在进化中出现的类型）上评估泛化能力，对比基线 ALLSites 及其他专用方法（如 CovalentLab、Squidly）。
- **药物发现阶段**：
  - 分子对接：使用 PDBbind（时间分割测试集）、PoseBusters、Astex Diverse Set 三个基准，对比基线 EquiBind。
  - 药物-靶点相互作用预测：使用 BindingDB 随机划分及更具挑战性的 Human-cold 数据集，对比基线 DrugBAN。
  - 从头分子生成：使用 MOSES 基准（随机划分与支架划分 TestSF），对比基线 CharRNN。
  - 靶点特异性肽结合物设计：使用 PepBench 和 PepNN 基准，对比基线 PepMLM，并用 AlphaFold3 ipTM 分数进行结构层面的评估。
  - ADMET 性质预测：使用 admetSAR 3.0 的 17 个数据集（12 个分类任务、5 个回归任务），采用基于分子相似性的严格划分，对比基线 FragNet。
- **临床前研究阶段**：
  - 动物毒理学评估：使用先前研究构建的 38 个大鼠病理指标数据集，在随机（Random）、低相似性结构留出（Structure）、ATC 治疗类别（ATC）、时间（Time）四种划分下进行 3 折交叉验证，对比基线 AnimalMLP。
- **临床试验阶段**：
  - 药物-药物相互作用预测：使用 MeTDDI 基准，在“仅一种未见药物”和“两种均未见药物”两种难度设置下评估分类与回归性能，对比基线 MeTDDI。
  - 药物副作用预测：使用 SIDER 数据集，10 折交叉验证、随机对划分、未见药物划分三种设置，对比基线 SDPred。

## 4. 资源与算力

- 论文未明确说明使用的 GPU 型号和具体数量。
- 除用于进化轨迹分析的可药性位点注释任务外，**每个任务的平均计算成本约为 180 GPU 小时**，部分任务仅需数小时。
- 蛋白可药性位点注释任务开展了超过 **2,200 GPU 小时** 的长期自主进化实验，共生成 331 个超越基线 ALLSites 的架构。

## 5. 实验数量与充分性

- **实验覆盖面广**：11 个任务横跨四种数据模态（生物序列、图、分子拓扑、文本语言），同时涵盖预测（分类/回归）与生成（分子生成、肽设计）两类任务，验证了系统的通用性。
- **多基准交叉验证**：多个任务在独立外部基准上进行了泛化评估（如 FusionGDA-Evo 在 TDC 上、EquiBind-Evo 在 PoseBusters/Astex 上、ALLSites-Evo 在 79 个独立测试集上），增强了结论的可靠性。
- **多种数据划分策略**：包括随机划分、时间划分、结构相似性划分、未见药物划分、ATC 类别划分等，从多个角度考察模型的泛化能力。
- **与专用方法的对比**：在可药性位点任务中，ALLSites-Evo 不仅对比了基线 ALLSites，还与 CovalentLab、Squidly 等专用方法进行了对比。
- **长期进化动力学分析**：专门设计了超过 2,200 GPU 小时的长期进化实验，分析了架构发现的规模定律、最佳得分的阶段性提升、进化树的继承与变异关系，深入揭示了 DrugEvolve 的进化机制。
- **总体评价**：实验设计较为全面和客观，数据划分严格（测试集在进化过程中未被使用），并采用多种划分策略降低偏差风险，充分性较高。但部分任务（如 DDI 分类）性能提升有限，主要收益集中在定量预测，说明不同任务上的改进幅度存在差异。

## 6. 论文的主要结论与发现

1. **自主进化可行且有效**：DrugEvolve 在几乎所有选定的任务上都实现了超过基线模型的性能提升，证明以人类成熟算法为起点、由 LLM 驱动的闭环自主进化是可行的。
2. **出色的泛化能力**：进化后的模型不仅在原始基准上表现优秀，还能泛化到未见过的数据类型（如可药性位点中的共价位点、催化位点、隐秘位点等），以及跨数据集的迁移场景，表明系统学到的是可迁移的算法设计原则。
3. **预测与生成任务兼顾**：系统在分类、回归等预测任务和分子生成、肽设计等生成任务上均取得了显著增益。
4. **进化具有规模定律**：长期实验表明，发现优质架构的累积数量与计算资源呈近似线性增长，最佳性能随计算增加持续改善，说明 DrugEvolve 能持续探索而非过早收敛。
5. **进化知识可累积复用**：进化数据库和采样策略使得成功和失败的经验都能指导后续迭代，减少冗余搜索，防止过早收敛。
6. **可迁移范式**：DrugEvolve 的模块化设计可推广到合成生物学、材料信息学、蛋白质工程等其他数据密集型科学领域。

## 7. 优点

- **方法创新性**：将 LLM 多智能体系统引入药物开发算法进化，实现了真正的“AI for AI”；相比一次性的代码生成代理（如 Codex、AlphaCode），支持持续迭代和记忆积累。
- **系统设计完整**：多角色分工（Researcher/Engineer/Analyst）+ 认知库 + 进化数据库 + 多样化采样策略，形成了设计良好的闭环系统，兼具知识驱动与经验驱动。
- **验证规模大且系统**：11 个任务 × 120 个基准集，覆盖药物开发全链条，是目前在药物开发领域最全面的自主算法进化验证之一。
- **泛化分析深入**：特别设计了针对“未在进化中出现的位点类型”的评估（如催化位点、共价位点），以及对同源序列不同功能的区分案例（溶菌酶 vs α-乳白蛋白），有力证明了进化模型学到了通用原理而非简单的任务模式匹配。
- **进化的可解释性**：长期进化轨迹分析、进化树可视化、架构创新类型的归纳，为理解 LLM 自主进化的内在机制提供了珍贵视角。
- **实际可用性**：平均 180 GPU 小时/任务的计算成本表明系统具备可执行性和应用潜力。

## 8. 不足与局限

- **预印本性质**：论文发表于 bioRxiv，尚未经过同行评审，部分结论需经专业审阅确认。
- **算力依赖**：进化时长与基线模型的计算开销直接相关，训练/评估成本高的模型会显著拉长进化周期；论文也承认在有限算力下部分任务性能提升有限。
- **基线选择的偏差风险**：所选基线均为已发表的高性能模型（CGMega、ALLSites、EquiBind 等），性能提升幅度在强基线上可能较难体现；而对于较弱基线是否也能取得如此提升，论文未进行系统验证。
- **部分任务改进不均衡**：某些任务（如 DDI 分类）的性能提升有限或基本持平，主要收益集中在回归/定量预测上，说明自主进化的收益在不同任务间并不均匀。
- **定性评估依赖 LLM 的潜在不确定性**：引入 LLM 定性评估和算法设计决策，可能受 LLM 固有偏差和提示方案差异的影响（论文在补充材料中有所讨论）。
- **跨物种/临床适用性有限**：动物毒理学评估和副作用预测等任务的数据来自历史实验，外推到人类临床场景仍需谨慎。
- **方法复现门槛**：系统涉及多个 LLM 角色、复杂的工作流和采样策略，代码已开源但复现完整实验仍需大量工程与算力投入。

（完）
