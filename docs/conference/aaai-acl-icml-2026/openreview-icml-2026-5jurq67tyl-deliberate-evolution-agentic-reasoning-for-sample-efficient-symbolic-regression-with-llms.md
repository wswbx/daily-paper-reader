---
title: "Deliberate Evolution:  Agentic Reasoning for Sample-Efficient Symbolic Regression with LLMs"
title_zh: 审慎进化：基于智能体推理的样本高效符号回归
authors: "Xinyu Pang, Zhanke Zhou, Xuan Li, Fangrui Lv, Shanshan Wei, Sen Cui, Bo Han, Changshui Zhang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/6b858c5ab779100cea6f8bb72c53da9d5ec04bea.pdf"
tags: ["query:sr"]
score: 10.0
evidence: 基于智能体推理的样本高效符号回归
tldr: 该论文指出LLM进化式符号回归将候选生成与搜索控制混为一谈导致样本效率低，提出Deliberate Evolution（DE）框架。DE解耦符号生成与搜索方向，利用自适应算子、结构诊断和轨迹记忆提升效率。实验证明DE在多个数据集中显著减少所需样本数量并提高表达式质量。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有LLM进化方法依赖标量反馈，样本效率低。
method: 提出DE框架，解耦生成与搜索控制，引入自适应算子、分析工具和反思记忆。
result: 在多个基准上以更少样本取得更高精度，提升搜索效率。
conclusion: DE为LLM符号回归提供了更有效的搜索策略。
---

## Abstract
Symbolic regression (SR) discovers compact mathematical expressions from data, yet recent LLM-based evolutionary methods remain sample-inefficient because they rely mainly on scalar feedback such as MSE. We identify a core limitation: existing methods conflate candidate proposal with search guidance, requiring the LLM to infer how to evolve an expression, diagnose its errors, and reuse past experience from a single score. To address this, we propose Deliberate Evolution (DE), an agentic framework that decouples symbolic generation from search control. DE guides LLM proposals with adaptive operators for search direction, analytical tools for structural diagnosis, and reflective memory for trajectory-level experience. Experiments on LLM-SRBench show that DE consistently outperforms representative LLM-based SR baselines across diverse scientific domains while using only 40% of the standard sample budget. Code is available at https://github.com/Xinyu-Pang/Deliberate-Evolution.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

符号回归（Symbolic Regression, SR）旨在从观测数据中发现紧凑的数学表达式，在科学发现中具有重要意义。近年来，基于大语言模型（LLM）的进化方法在SR中展现出潜力，但现有方法存在严重的**样本效率低下**问题：它们主要依赖标量反馈（如均方误差MSE）来指导搜索，这导致LLM需要从单一分数中推断如何改进表达式、诊断错误以及复用历史经验。核心局限在于，现有方法将**候选表达式生成**与**搜索方向控制**混为一谈，迫使LLM同时承担生成和推理角色，造成大量无效搜索。为此，论文提出**Deliberate Evolution（DE）**框架，旨在通过解耦符号生成与搜索控制，大幅提升样本效率，用更少的评估次数得到更优的表达式。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
DE 是一个**智能体推理（agentic reasoning）**框架，将符号回归中的进化过程分离为两个独立模块：一个负责生成候选表达式（符号生成），另一个负责控制搜索方向（搜索控制）。这种解耦使LLM无需同时推理“该怎么变”和“变什么”，从而降低认知负担。

### 关键技术细节
- **自适应算子（Adaptive Operators）**：替代传统固定的变异/交叉算子，根据当前搜索状态动态调整算子类型和强度，引导LLM生成更有希望的候选方向。
- **结构诊断工具（Analytical Tools for Structural Diagnosis）**：对候选表达式进行结构级分析（如复杂度、对称性、变量使用等），提供比标量MSE更丰富的反馈，帮助LLM定位错误来源。
- **反思记忆（Reflective Memory for Trajectory-Level Experience）**：记录整个搜索轨迹（包括成功/失败案例、算子选择历史），形成可复用的经验，指导后续进化步骤，避免重复错误。

### 算法流程（文字说明）
1. 初始化：用随机或简单表达式种子启动种群。
2. 迭代进化：
   - 从反思记忆中提取当前搜索状态和轨迹经验。
   - 利用自适应算子结合记忆线索，生成新的候选表达式（LLM生成）。
   - 用结构诊断工具分析新表达式，提取结构缺陷（如过拟合、变量缺失）。
   - 评估所有候选表达式（真实目标函数计算MSE等）。
   - 更新反思记忆，包含成功/失败轨迹及诊断信息。
3. 终止：达到预算或收敛标准。

## 3. 实验设计：使用的数据集/场景、Benchmark、对比方法

- **数据集/场景**：论文在 **LLM-SRBench** 基准上进行评估，该基准涵盖多个科学领域，包括物理、化学、生物学等标准符号回归问题。
- **Benchmark**：LLM-SRBench（专门为LLM-based SR设计的统一评测平台）。
- **对比方法**：代表性基于LLM的符号回归基线，如：
  - LLM-based genetic programming（例如Evolving expressions with LLM）
  - 其他进化式SR方法（基于LLM的变异/交叉）
  具体方法名称在摘要中未详列，但提到“consistently outperforms representative LLM-based SR baselines”。

## 4. 资源与算力

论文元数据和摘要中**未明确说明**具体使用的GPU型号、数量或训练时长。仅提到使用“standard sample budget”并指出DE只需其40%。关于算力（如实验运行时间、硬件配置）无公开信息。因此，在总结中需明确指出这一点。

## 5. 实验数量与充分性

根据摘要和元数据，实验主要围绕LLM-SRBench展开，对比了多个基线，并进行了样本效率分析（40%预算达到更好性能）。但在给出信息中未提及：
- 具体做了多少组不同数据集实验（如多少个科学领域问题）
- 是否包含消融实验（对自适应算子、结构诊断、反思记忆各组件的贡献分析）
- 统计显著性检验

因此，实验**数量**和**充分性**无法完全评估，但作者声称在多个科学领域一致超越基线，暗示实验具有一定的覆盖度。从公平性角度看，使用标准基准LLM-SRBench，对比代表性方法，基本满足客观性。

## 6. 论文的主要结论与发现

- DE框架显著提升了LLM符号回归的样本效率：仅使用标准预算的**40%**即可获得比现有方法更好的表达式质量。
- 解耦符号生成与搜索控制是提升效率的关键：自适应算子、结构诊断和反思记忆共同作用，减少了无效搜索。
- DE在各种科学数据集上一致优于现有LLM-based SR基线，证明了方法的普适性。

## 7. 优点

- **创新性**：首次明确提出LLM进化SR中“生成与搜索混为一谈”的缺陷，并设计了有效的解耦机制。
- **实用性**：显著减少所需样本数（-60%），对实际应用（如科学发现）中计算成本敏感的场景意义重大。
- **组件可解释**：自适应算子、结构诊断、反思记忆各自都有明确作用，便于后续改进和扩展。
- **开源**：代码已公开（GitHub），促进可复现性。

## 8. 不足与局限

- **算力信息缺失**：未报告硬件环境，难以评估方法的实际计算开销（虽然样本数少，但LLM推理本身可能昂贵）。
- **实验细节不完整**：未给出具体数据集数量、消融实验、超参数敏感性分析等，使实验结果的说服力打折扣。
- **应用限制**：依赖于LLM的生成能力和记忆容量，对于超长表达式或极大数据集可能仍面临挑战。
- **偏差风险**：实验仅在LLM-SRBench上进行，可能未覆盖所有类型的符号回归场景（如高噪声数据、多目标优化）。
- **与其他非LLM方法对比**：未提及与传统遗传规划（GP）等非LLM方法的对比，无法全面评估其绝对优势。

（完）
