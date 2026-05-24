---
title: Harnessing AI to Build Virtual Cells
title_zh: 利用人工智能构建虚拟细胞
authors: "Cheng, X., Li, P., Guo, H., Liang, Y., Gong, J., de Vazelhes, W., Gou, C., Xie, P., Song, L., Xing, E. P."
date: 2026-04-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.11.717183v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 9.0
evidence: 自主AI系统构建虚拟细胞用于科学发现
tldr: 本文提出虚拟细胞作为细胞的世界模型，能跨模态和尺度预测、模拟和编程细胞过程。VCHarness是一个自主AI系统，结合AI编码代理和多模态生物基础模型，自动构建扰动-响应模型，在多个基准测试中超越专家设计，将开发时间从数月缩短至数天，并发现非显而易见的架构模式。
source: biorxiv
selection_source: fresh_fetch
motivation: 当前构建细胞扰动-响应模型依赖专家经验，耗时长且难以扩展。
method: VCHarness利用AI编码代理自动搜索架构和训练流程，迭代生成、评估和优化候选模型。
result: 在多个基准测试中，VCHarness识别出超越专家设计的架构，开发时间从数月降至数天，并发现非直观的改进模式。
conclusion: 该工作表明从手动工程模型转向自主系统构建虚拟细胞世界模型是可扩展且数据驱动的方向。
---

## 摘要
虚拟细胞是细胞的一种世界模型：一个能够跨模态和尺度预测、模拟和编程细胞过程的计算系统。实现这一目标的重要途径是建模遗传和化学扰动如何引发转录响应，这是疾病理解和药物发现的核心能力。然而，当前的方法仍然依赖专家，需要数月时间进行迭代的手动模型设计、训练和调试。

本文提出VCHarness，一个自主AI系统，通过结合AI编码代理与多模态生物基础模型来构建扰动-响应模型。该系统在最小人工干预下探索庞大的架构和训练流程空间，迭代生成、评估和优化候选模型。在多个扰动-响应基准测试中，VCHarness识别出优于专家设计方法的架构，同时将开发时间从数月缩短至数天。它进一步发现了与性能提升相关的非显而易见的架构模式，表明自动搜索可以超越传统设计策略。这些结果表明，从手动工程模型向用于构建虚拟细胞世界模型组件的自主系统转变，能够实现对细胞系统的可扩展、数据驱动的探索。

## Abstract
A virtual cell is a world model of a cell: a computational system that predicts, simulates and programs cellular processes across modalities and scales. An important path toward this goal is to model how genetic and chemical perturbations give rise to transcriptional responses, a core capability for disease understanding and drug discovery. However, current approaches remain expert-intensive, relying on iterative manual model design, training and debugging over months.

Here we present VCHarness, an autonomous AI system that constructs perturbation-response models by combining an AI coding agent with multimodal biological foundation models. The system explores large spaces of architectures and training pipelines with minimal human intervention, iteratively generating, evaluating and refining candidate models. Across multiple perturbation-response benchmarks, VCHarness identifies architectures that outperform expert-designed approaches while reducing development time from months to days. It further uncovers non-obvious architectural patterns associated with improved performance, indicating that automated search can extend beyond conventional design strategies. These results suggest a shift from manually engineered models toward autonomous systems for constructing components of virtual cell world models, enabling scalable and data-driven exploration of cellular systems.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，现根据您提供的论文内容，生成以下结构化、深入且客观的中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：当前构建“虚拟细胞”这一能够预测、模拟细胞过程的计算系统，其关键子任务——构建“遗传或化学扰动下的转录响应预测模型”——严重依赖领域专家。整个过程涉及手动设计架构、反复调试、调参和迭代，开发周期长达数月，效率低下，成为虚拟细胞技术发展的瓶颈。
*   **研究动机**：为了摆脱对专家经验的依赖，实现模型构建的自动化和规模化，从而加速虚拟细胞技术的研发进程。
*   **整体含义**：本文提出了一种全新的范式，即**将模型开发本身转化为一个数据驱动的自动化搜索问题**，而非由专家手动设计。这标志着从“手动工程模型”向“自主构建模型”的关键转变，为实现更广泛、更全面的虚拟细胞系统铺平了道路。

### 2. 论文提出的方法论：核心思想、关键技术细节

*   **核心思想**：VCHarness 是一个**端到端的自主AI系统**，它将模型构建的完整流程（程序生成、调试、执行、评估和优化）缝合在一个可搜索的闭环中。其核心是**用自动化搜索替代人工试错**。
*   **关键技术细节**：
    1.  **多模态生物基础模型库**：系统内置一系列预训练的生物基础模型（如 AIDO.DNA, AIDO.Protein, AIDO.Cell, ESM2, scGPT 等），作为可复用的“乐高积木”，覆盖了基因组、蛋白质、单细胞等多个层面。
    2.  **AI编码代理（Coding Agent）**：一个大型语言模型（文中特指 Claude Sonnet 4.6）充当“程序员”，负责生成、调试和改进代码。它能够根据任务描述和搜索历史，生成定义完整训练流程的程序。
    3.  **蒙特卡洛树搜索（MCTS）**：作为搜索策略，MCTS 负责平衡探索（尝试新架构）和利用（优化高潜力架构）。它使用上置信界（UCB）公式选择下一个要探索的程序节点。
    4.  **闭环反馈机制**：系统运行后，评估结果（如验证集 F1 分数）和运行日志等反馈信息会被写回共享记忆，并用于指导AI编码代理在下一次迭代中生成更好的程序，形成一个持续改进的闭环。
    5.  **分布式执行**：使用Kubernetes、Ray等基础设施，支持在多GPU上并行训练和评估多个候选模型，以提高效率。
*   **核心公式**：MCTS的节点选择策略遵循 UCB 公式：
    `UCB(i) = J̄_i + c * sqrt( log(N) / n_i )`
    *   `J̄_i`: 节点 `i` 的平均表现得分。
    *   `n_i`: 节点 `i` 的访问次数。
    *   `N`: 父节点的访问次数。
    *   `c`: 控制探索与利用平衡的超参数。

### 3. 实验设计：数据集、基准、对比方法

*   **数据集**：使用 **Essential 数据集**[23, 22]，该数据集包含大规模CRISPR基因敲除筛选的转录组数据。实验在**四种不同细胞系**上进行：**HepG2**（肝癌）、**Jurkat**（T细胞）、**K562**（红白血病）、**hTERT-RPE1**（视网膜色素上皮）。
*   **任务**：**差异表达基因（DEG）分类**任务，即预测在给定基因敲除后，其他基因表达是上调、下调还是不变。
*   **基准（Benchmark）**：系统的性能基准是一个名为 `foundation-models-perturbation` 的公开代码库，其包含了由人类专家设计的多种基线模型。
*   **对比方法**：对比的方法非常全面，涵盖了：
    *   **基础模型**：如 AIDO.Cell (3M/10M/100M), scGPT, Geneformer, ESM2, scFoundation 等。
    *   **专家设计模型**：如 GNN Simple, TranscriptFormer 等。
    *   **控制组**：如随机嵌入（Random Embeddings）、无变化（No Change）、训练均值（Train Mean）等，以验证模型是否学到有效信息。
    *   总计超过20种不同的基线。

### 4. 资源与算力

*   论文没有给出训练整个系统的**总GPU时长或GPU型号/总数**。然而，文中提供了部分成本细节：
    *   在K562搜索实验中，每个MCTS节点的运行时间约为 **59% 用于模型训练/执行**（平均35分钟），**41%** 用于代码生成、调试、评估等。
    *   每个节点的平均预算（成本）约为 **6.67美元**，其中模型训练（H100 GPU）约占24%（1.63美元），而LLM调用（Claude Sonnet）在代码生成和调试上占主导，合计约51%。
    *   这表明，虽然系统可以全天候自主运行，但其计算成本集中在模型训练和LLM推理上。

### 5. 实验数量与充分性

*   **实验数量**：系统在每种细胞系上运行了**约100-150次搜索迭代**（见图2b横轴），生成并评估了上百个不同的模型架构。论文中未提供统计意义上的绝对实验总数。
*   **充分性与公平性**：
    *   **充分性**：实验覆盖了四种截然不同的细胞类型和扰动环境，证明了方法的**通用性和可迁移性**。对比方法种类繁多，充分展示了VCHarness相较于人类专家设计的优势。此外，论文还通过**消融分析**（图3e, 4e, 5e, 6e）探讨了成功架构的共同模式。
    *   **客观性**：论文展示了验证集与测试集分数的高度正相关（图3d），表明系统在搜索过程中使用的验证集指标是可靠的，降低了过拟合风险。同时，对比的所有基线均来自公开、单一的基准平台，确保了对比的公平性。
    *   **不足**：虽然搜索了数百个架构，但缺乏对**超参数对最终性能影响**的深度消融实验。所有实验均基于同一算法（MCTS）和编码代理（Claude Sonnet），未对比其他搜索策略（如贝叶斯优化）或不同LLM的性能，这是未来研究的一个方向。

### 6. 论文的主要结论与发现

1.  **性能超越专家**：在四个CRISPR扰动预测任务上，VCHarness 自主发现的架构在Macro-F1指标上**一致且显著地优于**所有由人类专家设计的基线模型。
2.  **效率显著提升**：模型开发时间从人类专家所需的**数月缩短至数天**。
3.  **发现非显而易见模式**：VCHarness 发现了人类直觉难以触及的高效架构模式。例如，在多数最佳模型中，将**蛋白质相互作用网络（STRING-GNN）**作为核心组件，并采用了**部分微调**、**门控融合**、**双线性预测头**等技术组合，而非简单的单一模态模型。
4.  **可迁移性**：该自动化搜索循环能直接应用到不同的细胞类型和数据集，并找到各自适用的最优架构，证明了其强大的可迁移性。

### 7. 优点

1.  **方法新颖性**：首次将自动化程序搜索（通过AI编码代理+MCTS）成功应用于生物模型的构建，解决了专家驱动的瓶颈问题，具有开创性意义。
2.  **实用性强**：系统输出的是可直接执行的、可复现的代码和模型，不仅仅是报告。它将开发时间从月缩短到天，具有极高的实际应用价值。
3.  **结果可解释**：通过MCTS的搜索树和架构分析，揭示了哪些设计选择对性能至关重要，提供了宝贵的洞察（例如STRING GNN的普遍重要性）。
4.  **实验设计全面**：在多种细胞系上进行测试，并与海量基线对比，有力地证明了方法的普适性和优越性。

### 8. 不足与局限

1.  **跨任务经验复用有限**：系统在单个任务上积累的经验（如成功的架构模式）还不能高效地迁移到其他新任务上，仍需要从零开始进行大量搜索。
2.  **搜索空间依赖先验知识**：搜索空间的设计（如使用了哪些基础模型、哪些融合方法）仍然隐含了先验知识，这个空间本身可能不是最优的。
3.  **计算成本**：虽然比人工开发快，但数百次运行LLM和训练模型仍是一笔不小的开销，尤其对于资源有限的实验室而言。论文没有对总成本进行量化。
4.  **验证范围有限**：目前仅在CRISPR基因敲除的**转录组响应**这一单一任务上验证。对于更广泛的虚拟细胞任务（如预测细胞动态、细胞-细胞相互作用、多模态响应等），其有效性有待验证。
5.  **搜索策略单一**：仅使用了MCTS，未探索其他更先进的搜索策略。且“探索-利用”的平衡完全依赖UCB公式，可能在某些情况下陷入局部最优。

（完）
