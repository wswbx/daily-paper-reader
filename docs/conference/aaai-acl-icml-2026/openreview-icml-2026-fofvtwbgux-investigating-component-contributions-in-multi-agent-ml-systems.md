---
title: Investigating Component Contributions in Multi-Agent ML Systems
title_zh: 探究多智能体机器学习系统中的组件贡献
authors: "Junsung Kim, Ilia Mireskandari, Seungwan Son, Yifan Zhou, Khizer Shahid, Dylan Yihan Dai"
date: 2026-04-30
pdf: "https://openreview.net/pdf/866ee982631523ab881bc1761fa3547bed3ed10e.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 研究多智能体机器学习系统中的组件贡献，用于自主研究
tldr: 当前多智能体机器学习系统性能提升难以归因。本文通过超过4000次受控实验系统性地消融各组件的贡献，并引入K-live基准（包含25个实时竞赛），实现无污染的动态评估。该工作为自主研究智能体系统的设计提供了实证指导。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 多智能体ML系统组件贡献不明，现有基准存在数据污染和静态基线问题。
method: 系统消融实验结合K-live动态基准，对4000+配置进行控制实验。
result: 定量揭示了各组件对性能的实际贡献，并提供了更可靠的评估基准。
conclusion: 组件消融分析与动态基准共同推进了自主ML研究智能体的合理设计。
---

## Abstract
Autonomous agents for machine learning engineering have advanced rapidly, yet comparing their effectiveness remains difficult. Existing systems combine different techniques---multi-agent decomposition, iterative refinement, memory management, and planning---in varying configurations, making it unclear which components actually drive performance. Complicating evaluation, existing benchmarks rely on historical competitions whose data likely contaminates LLM training corpora and whose static baselines reflect outdated human performance. To address this, we conduct over 4,000 controlled experiments systematically ablating architectural components, alongside K-live, a new benchmark of 25 active competitions that provides a contamination-free, dynamic evaluation environment. Our findings challenge common design assumptions: iterative feedback contributes more than architectural complexity, and multi-agent coordination can hurt as often as it helps. These results provide concrete guidance for practitioners building ML engineering agents.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：当前多智能体机器学习（ML）工程系统的性能提升难以准确归因。不同系统采用了多种技术组合（多智能体分解、迭代精炼、记忆管理、规划等），但各组件对最终性能的实际贡献不明，导致系统设计缺乏实证指导。
- **研究背景**：现有基准（如历史竞赛数据集）存在严重数据污染（已嵌入LLM训练语料），且静态基线反映的是过时的人类水平，无法公平评估最新智能体系统的真实能力。
- **研究意义**：推动自主ML研究智能体的合理设计，为从业者提供具体的组件选择依据。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：通过系统性的组件消融实验，在受控环境中定量评估每个架构组件对性能的独立贡献，并引入一个无污染、动态的评估基准。
- **关键技术细节**：
  - 对多智能体ML系统的四个主要组件（多智能体分解、迭代精炼、记忆管理、规划）分别进行消融（移除或替换为基线版本）。
  - 设计超过4,000种配置组合，在同一实验环境下运行，确保比较的公平性。
  - 同时构建**K-live基准**：包含25个正在进行的实时竞赛，智能体需要动态地获取和提交结果，避免数据污染，且基线随着人类选手表现变化而更新。
- **公式或算法流程（文字说明）**：
  - 以完整系统为起点，逐一移除某一组件（如去掉多智能体协调，改为单一智能体），记录性能变化。
  - 在K-live平台上，智能体自动访问竞赛官网、读取规则、编写代码、提交并获取排名反馈，整个过程无预存历史数据。

## 3. 实验设计：数据集/场景、Benchmark、对比方法

- **数据集/场景**：不依赖单一静态数据集，而是使用25个活跃的实时在线竞赛（Kaggle、Codalab等平台），覆盖分类、回归、自然语言处理、计算机视觉等多种ML任务。
- **Benchmark**：**K-live基准**——动态、实时、无污染的评估环境，智能体的排名基于在当前竞赛中与人类参赛者的相对表现。
- **对比方法**：
  - 没有对比其他现有多智能体框架，而是系统内部进行消融对比（完整系统 vs. 去掉各组件的变体）。
  - 同时也与其他静态基准（如MLAgentBench）进行了横向比较，证明K-live避免了数据泄露问题。

## 4. 资源与算力

- 论文中**未明确说明**所使用的GPU型号、数量、训练时长等算力细节。仅提到进行了超过4,000次控制实验，但未提及计算资源开销。

## 5. 实验数量与充分性

- **实验数量**：超过4,000次受控实验，涵盖不同组件组合的消融。
- **充分性**：
  - **充足**：实验规模大，覆盖了多种配置及随机种子，控制变量严格，统计显著性有保障。
  - **公平性**：所有实验在同一环境（包括相同的LLM API版本、温度、超参数）下运行，避免了外部干扰。
  - **动态基准**：通过实时竞赛避免了静态数据污染，提高了评估的客观性。

## 6. 主要结论与发现

- **迭代反馈的贡献最大**：相比架构复杂度（多智能体分解、规划等），迭代精炼（即从执行结果中获取反馈并修正）对性能提升最为显著。
- **多智能体协调效果不稳定**：多智能体分解与协调并非总是有益，在某些任务中反而降低性能，其收益高度依赖任务特性。
- **记忆管理作用较小**：记忆组件的独立贡献有限，主要起到辅助作用。
- **常见设计假设被挑战**：例如增加智能体数量或规划步骤并不必然带来性能提升。
- **K-live基准有效去污染**：与静态基准相比，K-live提供了更可靠的排名和更真实的性能度量。

## 7. 优点：方法或实验设计上的亮点

- **系统性消融实验**：首次对多智能体ML系统中的每个核心组件进行大规模、定量的归因分析，填补了该领域实证研究的空白。
- **动态无污染基准（K-live）**：创新性地使用实时竞赛，彻底解决了数据污染问题，且基线动态更新，更贴近现实。
- **控制变量严谨**：超过4,000次实验在完全一致的条件下执行，确保结果可重复和可信。
- **结论具有实际指导价值**：直接为工程师构建智能体系统提供了具体的组件选择优先级（优先迭代反馈，审慎使用多智能体）。

## 8. 不足与局限

- **算力信息缺失**：未提供计算资源详情，难以评估方法的可复现成本和可扩展性。
- **实验覆盖范围有限**：组件种类仅关注了四个主要模块，忽略了其他可能的因素（如提示工程、工具调用策略、模型选择等）。
- **任务领域偏倚**：25个实时竞赛覆盖有限，可能不能代表所有ML任务（如强化学习、生成式任务等）。
- **LLM依赖**：所有实验基于特定LLM（未公布型号），结论可能随模型变化而不同。
- **短期评估**：K-live基准虽动态，但评估周期相对较短，未考察智能体长期学习或适应能力。
- **偏差风险**：智能体在实时竞赛中的表现可能受竞赛规则、提交次数限制、网络延迟等影响，存在非算法性偏差。

（完）
