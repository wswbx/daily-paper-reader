---
title: Benchmarking and behavioral characterization of LLM agents for protein design
title_zh: 蛋白质设计大语言模型智能体的基准测试与行为特征描述
authors: "Kim, J., Romero, P. A."
date: 2026-05-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.06.723381v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 9.0
evidence: LLM智能体用于蛋白质设计这一科学发现任务
tldr: 蛋白质设计工作流复杂，缺乏标准化评估LLM智能体的框架。本文构建BioDesignBench基准，含76个专家任务及人类/非LLM基线，通过工具使用痕迹评估四个前沿LLM智能体。发现最强智能体超越硬编码但不及专家，行为受限（评估浅、少对比、早终止），强制深度评估可显著提升性能。开源基准、参考智能体和排行榜作为社区资源。
source: biorxiv
selection_source: fresh_fetch
motivation: 缺乏标准化框架评估LLM智能体在蛋白质设计等科学工作流中的表现和行为。
method: 构建BioDesignBench基准（76个专家任务、人类/非LLM基线、行为指标），评估四个前沿LLM智能体在不同蛋白质设计工作流中的工具使用痕迹。
result: 最强智能体优于确定性硬编码但不及专家实践；智能体工具选择适当但候选评估过浅、少有比较、过早终止探索；强制多指标深度评估大幅提升性能。
conclusion: 智能体的局限性是行为性的而非能力性的，深度评估可缓解；开源BioDesignBench、参考智能体和排行榜以推动AI蛋白质工程进展。
---

## 摘要
大语言模型（LLMs）正越来越多地被部署为科学发现的智能体，但缺乏在科学工作流程中评估其性能和行为的标准化框架。蛋白质设计提供了一个要求严格的测试案例，因为现代工作流程结合了随机生成模型、结构预测系统和基于物理的评估工具，需要进行广泛的候选探索和筛选。在此，我们介绍了BioDesignBench，一个包含76个专家策划的蛋白质设计任务的基准测试，涵盖抗体、酶、荧光蛋白、结合剂和支架，以及人类和非LLM基线以及源自工具使用痕迹的行为指标。我们评估了四个前沿LLM智能体在多种蛋白质设计工作流程中的表现，发现最强的智能体超越了确定性硬编码流水线，但始终低于专家实践水平。尽管智能体通常能选择合适的工具，但它们对候选设计的评估过于肤浅，很少比较备选方案，且过早终止探索。引导式工作流程提高了工具覆盖率，但未提升评估深度。强制执行更深入的多元评估显著提高了智能体性能，表明这些限制是行为性的而非基本能力约束。我们发布了BioDesignBench、开源参考智能体以及一个公共排行榜，作为评估和改进蛋白质工程AI智能体的社区资源。

## Abstract
Large language models (LLMs) are increasingly deployed as agents for scientific discovery, but standardized frame-works for evaluating their performance and behaviour in scientific workflows are lacking. Protein design provides a demanding test case because modern workflows combine stochastic generative models, structure prediction systems, and physics-based evaluation tools that require extensive candidate exploration and filtering. Here we introduce BioDesignBench, a benchmark of 76 expert-curated protein design tasks spanning antibodies, enzymes, fluorescent proteins, binders, and scaffolds, together with human and non-LLM baselines and behavioural metrics derived from tool-use traces. We evaluate four frontier LLM agents across diverse protein design workflows and find that the strongest agents surpass deterministic hardcoded pipelines but consistently underperform expert practice. Although agents generally select appropriate tools, they evaluate candidate designs too shallowly, rarely compare alternatives, and terminate exploration prematurely. Guided workflows improve tool coverage but not evaluation depth. Enforcing deeper multi-metric evaluation substantially improves agent performance, demonstrating that these limitations are behavioural rather than fundamental capability constraints. We release BioDesignBench, open-source reference agents, and a public leaderboard as a community resource for evaluating and improving AI agents for protein engineering.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLMs）正被越来越多地部署为科学发现智能体，但**缺乏标准化框架**来评估其在科学工作流中的性能和**行为**。蛋白质设计是一个严苛的测试案例，因为现代工作流结合了随机生成模型、结构预测系统和基于物理的评估工具，需要广泛的候选探索和筛选。
- **整体含义**：本文旨在构建一个**标准化的基准测试平台**，以系统评估LLM智能体在蛋白质设计任务中的表现，并揭示其行为局限性，最终推动AI在蛋白质工程中的应用。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：构建一个包含**专家策划任务**、**人类/非LLM基线**以及**工具使用痕迹行为指标**的基准测试（BioDesignBench），通过对四个前沿LLM智能体在多种蛋白质设计工作流中的评估，量化其性能和行为特征。
- **关键技术细节**：
  - **BioDesignBench基准**：包含76个专家策划的蛋白质设计任务，覆盖抗体、酶、荧光蛋白、结合剂和支架等类别。
  - **行为指标**：从工具使用痕迹中提取，包括**工具选择适当性**、**候选评估深度**（是否使用多指标）、**比较备选方案的频率**、**探索终止的时机**。
  - **评估方法**：对比智能体 vs. 人类专家 vs. 非LLM基线（确定性硬编码流水线）。还设计了**引导式工作流**（提供工具覆盖指导）和**强制深度评估**（强制执行多指标评估）两种条件。
- **算法流程**（文字描述）：
  1. 定义蛋白质设计任务（目标序列/结构特性）。
  2. 允许LLM智能体调用一组工具（如生成模型、结构预测、物理评估）。
  3. 记录智能体的每一步工具调用、评估结果、决策（继续/终止）。
  4. 根据最终设计的蛋白质与任务目标的匹配程度评分。
  5. 同时计算行为指标（评估深度、比较次数、探索步数等）。
  6. 对比人类专家基准和非LLM确定性流水线的结果。

## 3. 实验设计：使用的数据集/场景、基准、对比方法

- **数据集/场景**：BioDesignBench基准中的**76个蛋白质设计任务**，涵盖：
  - 抗体设计（亲和力、特异性优化）
  - 酶设计（催化活性改造）
  - 荧光蛋白设计（光谱特性调整）
  - 结合剂设计（靶标亲和力）
  - 支架设计（稳定性、结构完整性）
- **基准（Baseline）**：
  - **人类专家**：由经验丰富的蛋白质工程研究人员手动完成任务。
  - **非LLM基线**：确定性硬编码流水线（如固定顺序调用生成+预测+评估工具，无回溯）。
- **对比方法**：评估**四个前沿LLM智能体**（文中未具体点名，但通常指GPT-4、Claude等）。实验包括：
  - 基础工作流下的智能体表现。
  - 引导式工作流（提供工具使用顺序建议）。
  - 强制深度评估（要求智能体必须使用多指标评估候选设计）。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅描述了评估过程（调用LLM API、运行工具），未提及底层计算资源。因此无法总结具体算力消耗。

## 5. 实验数量与充分性

- **实验数量**：
  - 主要实验：76个任务 × 4个智能体 × 至少3种工作流条件（基础、引导、强制评估） ≈ 约912次评估（未计重复次数）。
  - 还包括人类专家基线（76次）和非LLM基线（76次）。
  - 行为分析基于工具使用痕迹，对每个智能体每种条件均提取指标。
  - 消融实验：引导式工作流 vs. 基础工作流；强制深度评估 vs. 基础工作流。
- **充分性与公平性**：
  - **充分**：任务覆盖多个蛋白质设计领域，基线设置合理（人类专家为黄金标准，非LLM为硬编码参考）。
  - **客观**：使用工具使用痕迹作为行为指标，可复现。
  - **公平**：所有智能体使用相同工具集、相同任务定义、相同评分标准。
  - **局限**：未提及统计显著性检验（如置信区间、p值）；未评估智能体对工具使用错误的鲁棒性。

## 6. 论文的主要结论与发现

- **主要结论**：
  1. **最强智能体超越确定性硬编码流水线**，但**始终低于专家实践水平**。
  2. **行为特征**：
     - 智能体通常能**选择合适的工具**。
     - 但对候选设计的**评估过于肤浅**（仅用单一或少数指标）。
     - **很少比较备选方案**（极少进行多候选对比）。
     - **过早终止探索**（当遇到第一个“不错”的方案就停止）。
  3. **引导式工作流**提高了工具覆盖率（使用更多工具），但**未提升评估深度**。
  4. **强制执行多元深度评估**（要求使用多个指标评价每个候选）**显著提高了智能体性能**，表明这些限制是**行为性的而非基本能力约束**。

## 7. 优点

- **方法亮点**：
  - 构建了**首个标准化蛋白质设计智能体基准**，任务涵盖广泛，专家策划分保证任务质量。
  - 引入**行为指标**（工具选择、评估深度、比较频率、终止时机），超越了单纯性能评分，揭示了智能体工作方式的根本缺陷。
  - 通过**强制深度评估**实验，证明了行为干预可以提升性能，具有实用指导意义。
- **实验设计亮点**：
  - 同时包含**人类专家和非LLM基线**，提供了上下限参考。
  - **开源**了基准、参考智能体和排行榜，推动社区共建。
- **贡献**：为评估和改进AI蛋白质工程智能体提供了标准化资源。

## 8. 不足与局限

- **实验覆盖**：
  - 任务数量有限（76个），可能未覆盖所有蛋白质设计场景（如膜蛋白、大规模设计空间）。
  - 仅测试了**4个LLM智能体**，代表性有限（未包含更广泛的开源模型或专用蛋白质模型）。
- **偏差风险**：
  - 人类专家基线来自少数专家，可能存在个体偏差。
  - 智能体调用API结果可能受版本更新影响，复现性需注意。
  - 行为指标依赖于工具使用痕迹的定义，可能遗漏隐式推理。
- **应用限制**：
  - 未评估智能体在**真实实验验证**中的成本（如湿实验费用）。
  - 未讨论**安全性与伦理**（如设计有害蛋白质）。
  - 未提供**计算资源成本**分析，实用性评估不足。

（完）
