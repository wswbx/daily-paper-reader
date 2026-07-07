---
title: "Influence-Guided Symbolic Regression: Scientific Discovery via LLM-Driven Equation Search with Granular Feedback"
title_zh: 影响引导的符号回归：基于LLM方程搜索的粒度反馈科学发现
authors: "Evgeny Saveliev, Samuel Holt, Nabeel Seedat, David L. Bentley, Jim Weatherall, Mihaela van der Schaar"
date: 2026-04-30
pdf: "https://openreview.net/pdf/954ce510d1a5902db51e49c098151be23811c8df.pdf"
tags: ["query:sr"]
score: 10.0
evidence: 基于LLM的符号回归，带粒度反馈
tldr: 该论文针对LLM进行符号回归时搜索效率低的问题，提出了IGSR方法，将方程发现建模为迭代的两步过程：LLM生成候选基函数，然后利用粒度反馈进行选择。相比仅依赖全局MSE的方法，IGSR能更有效地引导搜索，在多个基准上取得更优结果，推动了符号回归在科学发现中的应用。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有LLM符号回归依赖全局MSE，无法反馈方程各组分好坏。
method: 提出IGSR，LLM生成候选基函数，通过粒度反馈迭代选择。
result: 在多个符号回归基准上优于基线方法，搜索效率显著提升。
conclusion: 粒度反馈能有效引导LLM进行符号回归，增强可解释发现。
---

## Abstract
Large Language Models (LLMs) offer a promising avenue for scientific discovery, yet their application to symbolic regression is often constrained by inefficient search strategies and coarse feedback signals. Current methods typically guide LLMs using scalar metrics (e.g., global Mean Squared Error), which fail to identify which components of a proposed equation are driving performance or causing error. We introduce \textit{Influence-Guided Symbolic Regression} (IGSR), a method that frames equation discovery as an iterative two-step process combining diverse term generation with rigorous selection: an LLM generates candidate basis functions $\psi_j(\mathbf{x})$ for a linear model, which are then evaluated using granular influence scores $\Delta_j$. These scores quantify each term's marginal contribution to generalization accuracy, enabling an influence-guided pruning process that systematically refines the model structure. Integrating this mechanism into a Monte Carlo Tree Search (MCTS) enables navigating the combinatorial search space while balancing exploration of novel functional forms with exploitation of high-influence components. We demonstrate IGSR's effectiveness on a diverse suite of benchmarks, including LLM-SRBench, pharmacological PKPD models, an epidemiological simulation, and real-world genomic data. Notably, we validate the framework's capacity for genuine discovery in a case study using a high-dimensional biological dataset, in which IGSR identified a novel relationship between DNA methylation and RNA Polymerase II pausing; a hypothesis that was subsequently supported via wet-lab experimentation.

---

## 论文详细总结（自动生成）

以下是对论文《Influence-Guided Symbolic Regression: Scientific Discovery via LLM-Driven Equation Search with Granular Feedback》的详细中文总结。

---

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在科学发现（如符号回归）中展现出潜力，但现有方法面临两大障碍：① **搜索策略低效**——LLM在巨大的候选方程空间中随机探索，难以收敛；② **反馈信号粗糙**——通常仅使用全局均方误差（MSE）作为唯一评价指标，无法区分方程中不同组分的好坏，导致模型难以识别哪些项真正驱动性能、哪些项引入误差。
- **整体含义**：论文旨在通过引入**粒度反馈**（即每个基函数对泛化准确度的边际贡献）来引导LLM生成和选择方程，从而提高符号回归的搜索效率与科学性，使LLM能够发现更准确、更可解释的数学表达式，助力真实科学发现。

## 2. 论文提出的方法论

- **核心思想**：将方程发现建模为**迭代的两步过程**：① LLM生成候选基函数（basis functions）ψⱼ(x)；② 利用**影响分数（influence scores）** Δⱼ 量化每个基函数对模型泛化性能的边际贡献，并基于此进行粒度反馈驱动的剪枝，从而系统性地精炼模型结构。
- **关键技术细节**：
    - **线性模型假设**：方程表示为基函数的线性组合 y = Σ aⱼ ψⱼ(x)，基函数由LLM自动生成（如三角函数、指数函数、多项式等）。
    - **影响分数计算**：Δⱼ 衡量删除或添加基函数ψⱼ后，模型在验证集上泛化误差的变化（类似特征重要性或leave-one-out影响）。该分数为正表示该项有益（降低误差），为负表示有害。
    - **粒度反馈**：将Δⱼ作为反馈信号返回给LLM，告知哪些生成的基函数有效、哪些无效，从而引导LLM在下一轮生成中更聚焦于高影响项，舍弃低影响项。
    - **结合蒙特卡洛树搜索（MCTS）**：将整个迭代过程嵌入MCTS框架，平衡探索（尝试新颖的函数形式）与利用（保留高影响现有组分），高效导航组合搜索空间。
- **算法流程（文字说明）**：
    1. 初始化：LLM基于问题描述生成一组候选基函数。
    2. 评估：拟合当前基函数构成的线性模型，计算每个基函数的影响分数Δⱼ。
    3. 反馈：将Δⱼ（及其对应基函数）作为查询-响应形式反馈给LLM，LLM根据反馈生成新的基函数候选（或修改现有项）。
    4. 剪枝：基于影响分数去除低分/负分项，保留高影响项。
    5. 迭代：重复步骤2-4，直到模型收敛或达到最大迭代次数。整个搜索由MCTS驱动，确保全局高效探索。

## 3. 实验设计

- **使用的数据集/场景**：
    - **LLM-SRBench**：符号回归标准基准，包含多类人工合成与真实世界的数学关系。
    - **药代动力学/药效学（PKPD）模型**：模拟药物浓度-效应关系。
    - **流行病学仿真**：模拟疾病传播动态。
    - **真实世界基因组数据**：高维生物学数据集（DNA甲基化与RNA聚合酶II暂停的关系）。
- **Benchmark**：对照方法包括标准符号回归方法（如Eureqa、PySR、基于遗传编程的SR）以及仅依赖全局MSE反馈的LLM基线方法。
- **对比方法**：包括直接使用LLM生成方程而不加粒度反馈、以及使用全局MSE作为唯一反馈的变体。

## 4. 资源与算力

- 论文中**未明确说明**所使用的GPU型号、数量、训练时长等具体算力信息。仅提及方法基于LLM（可能调用预训练模型API或本地部署），未提供详细的硬件配置或计算成本分析。

## 5. 实验数量与充分性

- **实验数量**：实验覆盖了**多类场景**（4个主要基准/案例），包括：
    - LLM-SRBench上的量化对比（多组方程）
    - PKPD模型
    - 流行病学仿真
    - 基因组数据案例研究（含湿实验验证）
- **消融实验**：论文进行了消融研究，例如比较有无粒度反馈、有无MCTS的版本，以验证各组件贡献。
- **充分性与客观性**：
    - 实验设计较为全面，覆盖了合成数据、模拟数据及真实数据，且包含一个经湿实验验证的真实发现案例，可信度高。
    - 对比方法选择合理，包括传统SR方法和LLM基线。
    - 但未提供统计显著性检验或多次运行结果方差（可能隐含在标准误差中），且缺少对更高维或更大搜索空间场景的扩展测试。

## 6. 论文的主要结论与发现

- **主要结论**：粒度反馈（影响分数）能显著提升LLM进行符号回归的搜索效率与准确性，相比仅依赖全局MSE的方法，IGSR在多个基准上取得更优结果，并发现真实、可验证的科学假设。
- **具体发现**：
    - 在LLM-SRBench上，IGSR恢复真实方程的成功率更高，收敛更快。
    - 在真实基因组案例中，IGSR自动发现DNA甲基化与RNA聚合酶II暂停之间的新关系，经湿实验室实验支持，证明其具备**真实科学发现能力**。

## 7. 优点

- **方法创新**：首次将**影响分数**作为粒度反馈注入LLM搜索，克服了全局MSE反馈的粗糙性，显著提升了搜索引导的精准度。
- **通用性强**：方法不依赖特定LLM，可灵活集成多种预训练语言模型。
- **可解释性**：生成的方程为显式线性组合，透明可理解，符合科学发现的可解释要求。
- **实验验证坚实**：包含湿实验支持的案例研究，验证了方法的实际科学价值，而不仅是数值指标提升。
- **算法框架清晰**：将MCTS与粒度反馈结合，在探索-利用平衡上设计合理。

## 8. 不足与局限

- **实验覆盖**：主要集中在中低维度方程（基函数数量有限），对极高维空间（如数百个变量）的扩展性未充分验证。
- **偏差风险**：LLM的生成能力可能偏向于常见函数形式（如多项式、三角函数），对罕见但重要的形式探索不足。
- **计算成本**：虽未详细报告，但每次迭代需拟合线性模型并计算影响分数，且需多次调用LLM（可能产生较高API费用或推理延迟），实际部署需考虑成本。
- **线性模型假设**：方法假设最终方程为基函数的线性组合，对非线性系数或嵌套结构（如分式、复合函数）无法直接处理，可能限制某些科学问题的表达能力。
- **未讨论超参数选择**：影响分数阈值、MCTS参数等对性能的影响未系统分析，调参可能依赖经验。
- **可复现性**：论文未提供代码或具体LLM标识，公开复现存在一定障碍。

---

（完）
