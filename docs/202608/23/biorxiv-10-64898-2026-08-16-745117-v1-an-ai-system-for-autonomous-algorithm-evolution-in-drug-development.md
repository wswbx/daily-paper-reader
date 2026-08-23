---
title: An AI System for Autonomous Algorithm Evolution in Drug Development
title_zh: 用于药物开发中自主算法进化的人工智能系统
authors: "Zhou, Z., Nan, Y., Mou, M., Qian, Y., Liu, Y., Zuo, Z., Yang, H., Xu, W., Li, B., Jiang, W., Ren, Y., Liao, Y., Wang, Y., Li, Y., Yang, Q., Xi, Z., Mi, T., Sun, H., Liu, P., Zhu, F."
date: 2026-08-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.16.745117v1.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 多角色大语言模型系统自主进化药物研发算法，属于自主研究范畴
tldr: 药物研发算法高度依赖专家设计与任务特定优化，且各阶段算法协同效应显著，亟需自主进化机制。DrugEvolve作为多角色大语言模型系统，通过研究者、工程师、分析师三个角色实现闭环迭代，自动设计、实现、评估并优化算法。在覆盖靶点识别、药物发现、临床前及临床试验的11个代表性任务、120个基准测试集上取得显著性能提升，并展现出跨数据模态及预测生成任务的强泛化能力。该系统为药物研发提供算法基础设施，亦为更广科学领域提供可迁移范式。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有药物研发算法依赖专家手工设计，难以跨阶段协同进化，需自动化系统实现整体提升。
method: DrugEvolve整合多角色大语言模型，驱动闭环进化流程，迭代设计、实现、评估并优化算法。
result: 在11个任务120个基准集上性能大幅提升，跨模态泛化，预测与生成任务均受益。
conclusion: 提供药物研发自主进化算法基础设施，可作为更广科学领域的可迁移范式。
---

## 摘要
人工智能（AI）正日益渗透到药物开发流程中。人们已构建了许多算法来加速这一多阶段、多任务的过程，但这些算法高度依赖专家设计和劳动密集型的特定任务优化。鉴于AI驱动的药物开发加速被认为是跨多个阶段的累积性、通常具有协同效应的过程，因此需要对整个流程中的现有算法进行自主进化，以实现整体推进。在此，我们提出了DrugEvolve，一个用于药物开发中系统性和自主算法进化的多角色大语言模型系统。DrugEvolve通过整合研究员、工程师和分析师领域，实现了闭环进化过程，并利用科学知识和积累的进化经验，实现算法的迭代设计、实现、评估和优化。在覆盖靶点识别、药物发现、临床前研究和临床试验的十一个代表性任务中，DrugEvolve自主进化出相应的任务特定算法，并在120个基准测试集上实现了显著的性能提升。此外，它在异构数据模态（从生物序列和图到分子拓扑和文本语言）上展现出强大的泛化能力，并在预测和生成任务中都取得了收益。总的来说，这一人工智能系统不仅可以作为药物开发的算法基础设施，还可以作为更广泛科学领域的可迁移范式。

## Abstract
Artificial intelligence (AI) is increasingly permeating the drug development pipeline. Numerous algorithms for accelerating this multi-stage and multi-task process have been constructed, which depends heavily on expert design and labor-intensive task-specific optimization. Given that AI-driven acceleration of drug development is recognized as a cumulative, often synergistic, effect across multiple stages, the autonomous evolution of existing algorithms across the entire pipeline is demanded to achieve a holistic advancement. Here, we present DrugEvolve, a multi-role large language model system for systematic and autonomous algorithm evolution in drug development. DrugEvolve realizes a closed-loop evolution process by incorporating Researcher, Engineer, and Analyst domains, and enables an iterative design, implementation, evaluation, and refinement of algorithm by leveraging scientific knowledge and accumulated evolutionary experience. Across eleven representative tasks spanning target identification, drug discovery, preclinical study, and clinical trial, DrugEvolve autonomously evolved the corresponding task-specific algorithms and achieved substantial performance enhancement on 120 benchmark test sets. Moreover, it showed robust generalizabilities across heterogeneous data modalities (ranging from biological sequence and graph to molecular topology and textual language), and realized gains in both predictive and generative tasks. Collectively, this AI system can serve not only as an algorithmic infrastructure for drug development, but also as a transferable paradigm for broader scientific domains.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- **领域瓶颈**：药物研发是一个多阶段、多任务的过程（靶点识别、药物发现、临床前研究、临床试验），每个阶段都需要大量领域特定的计算工具。然而传统算法设计高度依赖人类专家的经验直觉与反复试错，迭代周期长、成本高昂，严重制约了算法发现的规模和效率。
- **自主进化的必要性**：AI驱动的药物开发加速被认为是一个跨阶段的累积性、协同性过程，仅优化单一任务难以带来整体效率提升，需要在整条研发管线中系统性地自主进化已有算法。
- **现有方法的不足**：LLM编码代理（如 Codex、AlphaCode）多为“一次性生成”，缺乏系统性迭代优化能力；虽然 ERA、AlphaEvolve、CodeEvolve、MLEvolve 等系统已在特定“AI for AI”领域实现自主进化，但尚无系统尝试覆盖**整个药物研发管线**的自主算法进化。
- **研究目标**：提出 DrugEvolve——一个多角色大语言模型（LLM）系统，能够以人类已建立的强算法为起点，“站在巨人肩膀上”进行闭环、持续、自主的算法进化，从而在药物研发各阶段实现性能提升，并提供可迁移到更广泛科学领域的范式。

## 2. 方法论

- **总体框架**：DrugEvolve 由四个紧密集成的组件构成：多角色 LLM 架构、Cognition Library（外部知识库）、Evolutionary Database（进化记忆库）、可选的采样策略。形成“设计→实现→评估→分析→再设计”的闭环进化流程。
- **多角色 LLM 架构**：
  - **Researcher 领域**：Generator 从 Cognition Library 检索科学知识，从 Evolutionary Database 检索历史进化经验，结合人类给定的任务目标和约束提出候选算法；Inspector 检查方案是否与已有方案冗余；Implementer 将获批设计转化为可执行代码。
  - **Engineer 领域**：Trainer 执行训练与验证；Debugger 处理运行时错误；Judger 用任务特定的定量指标评估，可选 LLM-as-a-judge 提供定性补充评价。
  - **Analyst 领域**：系统分析进化结果，评估与目标/基线的差距，解释设计背后的生物学/化学原理，识别系统性局限和未来改进方向，将分析报告写入 Evolutionary Database 供后续迭代复用。
- **Cognition Library**：将文献、领域专家知识、实验/计算研究结论整理成结构化条目，指导算法设计，增强 LLM 的科学背景和机制性理解。
- **Evolutionary Database**：基于 JSON 的实验存储，记录每一轮的算法设计、性能评估和分析报告，支持按实验 ID、执行顺序和上下文相似性检索，实现持久记忆，防止信息丢失和重复探索。
- **采样策略**：
  - **UCB1**：基于上置信界框架，平衡高效用候选的利用与低频率候选的探索，适用于可用标量效用排序的场景。
  - **Island-based 采样器**：针对高度异构、崎岖的搜索空间（如蛋白可成药位点预测），将候选划分为岛屿子群并轮换偏好岛屿，通过全局档案共享信息；可选配 MAP-Elites 风格的行为特征归档，在每个特征区域保留最高效用候选。
- **进化流程**：以人类提供的任务描述、基线模型、数据集和预定义评估指标为起点，系统自动迭代。整个过程不需要人工干预，测试集严格保留用于最终评估。

## 3. 实验设计

- **总体覆盖**：选取了覆盖药物研发四个阶段的 **11 个代表性任务**，合计 **120 个基准测试集**。
- **各阶段任务与基线**：
  - **靶点识别**：
    - 癌症基因模块检测：基于 MCF-7 乳腺癌多组学数据集，以 CGMega 为基线，10 折交叉验证。
    - 基因-疾病关联预测：基于 DisGeNET-EVAL 基准，以 FusionGDA 为基线，5 个独立随机划分；并额外用 TDC 数据集做外部泛化评估。
    - 蛋白可成药位点注释：以 ALLSites 为基线，6 种非共价结合位点数据集用于进化优化，79 个独立测试集用于泛化评估，涵盖共价结合位点、催化位点、隐蔽位点和翻译后修饰位点等未见过类型。
  - **药物发现**：
    - 分子对接：以 EquiBind 为基线，PDBbind 测试集为优化基准，PoseBusters 和 Astex Diverse Set 为外部基准。
    - 药物-靶点相互作用预测：以 DrugBAN 为基线，BindingDB 数据集，包含随机划分、unseen-drug、unseen-protein 以及更严格的 Human-cold 设置。
    - 从头分子生成：以 CharRNN 为基线，MOSES 基准（随机测试集 Test 和 scaffold 测试集 TestSF）。
    - 靶点特异性肽结合剂设计：以 PepMLM 为基线，PepBench 基准；额外用 PepNN 基准做独立泛化；并用 AlphaFold3 做结构层面的 ipTM 评估。
    - ADMET 性质预测：以 FragNet 为基线，admetSAR 3.0 的 17 个数据集（12 个分类任务、5 个回归任务），采用基于分子相似性的严格划分。
  - **临床前研究**：
    - 动物毒理学评估：自建 AnimalMLP 基线，用前人研究数据，化合物级 3 折交叉验证，包含随机、低相似度结构、ATC 治疗类别和时间四种划分。
  - **临床试验**：
    - 药物相互作用预测：以 MeTDDI 为基线，采用原协议中的两种难度递增的 unseen-drug 设置，同时评估分类和定量 PK 变化预测。
    - 药物副作用预测：以 SDPred 为基线，SIDER 数据集，包含原始 10 折交叉验证以及随机对划分和 unseen-drug 划分。
- **对比方法**：各任务与自身基线模型对比，同时在蛋白位点注释等任务中与专门方法（如 CovalentLab、Squidly 等）对比；对接任务中与 EquiBind 原始版本（含/不含构象修正）对比。
- **评估指标**：根据任务类型使用 AUROC、AUPRC、MCC、F1、Accuracy、RMSE、R²、FCD、Scaff、IntDiv2、Novelty、ipTM、RMSD、centroid distance、cosine similarity 等。

## 4. 资源与算力

- 文中提及：除用于进化轨迹分析的蛋白可成药位点注释任务外，**每个任务的平均计算成本约为 180 GPU 小时**，部分任务仅需几 GPU 小时。
- 蛋白可成药位点注释任务进行了长期自主进化实验，**累计超过 2,200 GPU 小时**，生成了 331 个优于基线的架构。
- **未明确说明**：GPU 的具体型号、数量、训练时长分布、并行策略等详细信息，因此无法从文中获知更细粒度的硬件配置。

## 5. 实验数量与充分性

- **实验数量**：11 个任务、120 个基准测试集，覆盖多个药物研发阶段；每个任务通常包含多个数据集和多种划分方式，部分任务还有外部独立基准（如 TDC、PoseBusters、Astex、PepNN、CryptoBank 等），数量相当充足。
- **覆盖广度**：数据模态涵盖生物序列、图、分子拓扑和文本语言；任务类型同时包括预测任务（分类/回归）和生成任务（分子生成、肽设计、构象预测），评估维度多元。
- **客观性/公平性**：
  - 进化过程中仅使用训练集和验证集，测试集严格保留，避免数据泄露。
  - 遵循原基线论文的评估协议（如 10 折交叉验证、unseen-drug 设置等），并在多个独立外部基准上验证泛化能力。
  - 对基线模型使用标准的构象修正等后处理，进化模型也在同等条件下比较。
- **充分性**：实验较充分，但论文本身为预印本，尚未经过同行评审；此外，部分任务中某些指标提升有限（如 DDI 分类性能与基线相当），进化算法的稳定性和偏差风险仍需更多独立验证。

## 6. 主要结论与发现

- **自主进化有效**：DrugEvolve 在 11 个任务的 120 个基准集上实现了几乎全面的性能提升，证明多角色 LLM 驱动闭环进化在跨任务、跨模态场景中的可行性和通用性。
- **跨越整个管线**：从靶点识别到临床试验均观察到一致改进，支持了“全管线协同加速”的必要性。
- **强泛化能力**：
  - 在未见过的新数据分布（如 unseen-drug/unseen-protein、低相似度分子划分、外部数据集）上保持或扩大收益。
  - 在蛋白位点注释中，进化模型能够泛化到进化过程中未见过的位点类型（共价、催化、隐蔽、PTM 位点）。
  - 在肽设计中，序列多样性大幅提升，且 AlphaFold3 结构评估显示结合置信度（ipTM）更高。
- **进化动力学**：随着计算资源增加，优于基线的架构数量呈近线性增长，best score 持续上升，体现“架构发现的 scaling law”；进化树分析表明模型通过迭代继承和修改逐步改进，同时保留失败经验用于指导后续搜索。
- **代表性架构改进**：进化发现的设计包括多尺度特征提取、残差修正、物理启发的交互模块（如哈密顿相互作用）、迭代掩码去噪、对比学习、多视图分子表示、稀疏注意力、低秩交互等，涵盖表征学习、特征融合、预测头重设计等多个层面。
- **可作为基础设施**：DrugEvolve 不仅能作为药物研发的计算工具基础设施，也提供了一个可迁移到合成生物学、材料信息学、蛋白质工程等数据密集型学科的自主进化范式。

## 7. 优点

- **系统设计新颖**：将多角色 LLM（Researcher/Engineer/Analyst）与外部知识库、进化记忆库、采样策略有机结合，形成透明、可记忆、持续改进的闭环进化框架。
- **覆盖面广**：首次尝试在整条药物研发管线上进行自主算法进化，跨越多阶段、多数据模态、多任务类型（预测与生成）。
- **实验严谨**：严格分离训练/验证/测试集，遵循原基线协议，多指标、多划分、多外部基准共同验证，提高结论可信度。
- **深度机制分析**：通过对 ALLSites 的长期进化（2200+ GPU 小时）对进化动态、scaling law、进化树、失败经验利用等进行了详细剖析，提供了对系统内部机制的理解。
- **实用性强**：每个任务平均约 180 GPU 小时、部分只需数小时，计算成本相对可控，且进化所得架构改进易于复现和重用。
- **泛化潜力**：模块化设计使其可迁移至其他科学领域，不局限于药物研发。

## 8. 不足与局限

- **计算成本仍高**：进化总时间与基线模型的训练/评估开销紧密相关，资源密集的基线会显著延长进化周期；论文没有给出详细 GPU 型号、数量和并行策略，难以评估硬件可移植性。
- **性能提升不均衡**：部分任务（如 DDI 分类）性能与基线基本持平，提升主要体现在回归或定量预测；一些指标（如 scaffold 随机划分上的 Scaff）甚至略有下降，说明进化效果存在任务和指标差异。
- **依赖人工设定**：系统仍需要人类提供任务定义、基线模型、数据集和评估目标，并非完全从零开始的无监督发现；基线质量直接影响进化上限。
- **LLM 行为敏感性**：系统由 LLM 驱动，提示方案、LLM 选择等可能影响代理行为和最终进化结果；论文虽提及相关分析，但未提供完全消融或敏感性量化。
- **长期进化稳定性**：虽然观察到 scaling law 和持续改进，但进化过程中大量后代性能劣于父代，存在搜索效率问题；是否会出现平台期或过拟合进化目标仍需更长周期验证。
- **验证尚属初步**：作为预印本，未经同行评审；多数性能提升仅在计算层面验证，动物毒理学、副作用预测等任务缺乏实验验证；肽设计的结构评估依赖 AlphaFold3 预测，尚未有湿实验确认。
- **数据偏差风险**：使用的基准数据（如 DisGeNET、SIDER、PDBbind 等）本身可能存在偏倚，进化模型可能放大或继承这些偏倚，论文未深入讨论。

（完）
