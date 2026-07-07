---
title: "Just Ask: Curious Code Agents Reveal System Prompts in Frontier LLMs"
title_zh: Just Ask：好奇的代码智能体揭示前沿大语言模型的系统提示
authors: "Xiang Zheng, Yutao Wu, Hanxun Huang, Yige Li, Xingjun Ma, Bo Li, Yu-Gang Jiang, Cong Wang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/f540a91552dcfe08092a5cc896831b344b46a6e1.pdf"
tags: ["query:cli-agent"]
score: 6.0
evidence: 从自主代码智能体中提取系统提示，与CLI智能体安全相关
tldr: 自主代码智能体（如基于LLM的CLI智能体）在执行任务时可能暴露隐藏的系统提示。本工作发现这是一个尚未被认识的安全漏洞，并构建了JustAsk框架，通过智能体交互自动发现有效提取策略。无需手工提示或监督，JustAsk成功从多个前沿模型中提取了系统提示，揭示了代码智能体攻击面的扩展。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 代码智能体的自主交互扩大了攻击面，使系统提示可能被探测和恢复，但此前未被充分认识。
method: 提出JustAsk框架，通过智能体交互自动发现有效提取策略，无需手工设计提示或标注。
result: 在多个前沿LLM上成功提取系统提示，验证了该漏洞的普遍性和严重性。
conclusion: JustAsk揭示了代码智能体（包括CLI智能体）的系统提示提取风险，需引起安全重视。
---

## Abstract
Autonomous code agents built on large language models are reshaping software and AI development through tool use, long-horizon reasoning, and self-directed interaction. However, this autonomy introduces a previously unrecognized security risk: agentic interaction fundamentally expands the LLM attack surface, enabling systematic probing and recovery of hidden system prompts that guide model behavior. We identify system prompt extraction as an emergent vulnerability intrinsic to code agents and present JustAsk, a self-evolving framework that autonomously discovers effective extraction strategies through interaction alone. Unlike prior prompt-engineering or dataset-based attacks, JustAsk requires no handcrafted prompts, labeled supervision, or privileged access beyond standard user interaction. It formulates extraction as an online exploration problem, using Upper Confidence Bound-based strategy selection and a hierarchical skill space spanning atomic probes and high-level orchestration. These skills exploit imperfect system-instruction generalization and inherent tensions between helpfulness and safety. Evaluated on 41 black-box commercial models across multiple providers, JustAsk consistently achieves full or near-complete system prompt recovery, revealing recurring design- and architecture-level vulnerabilities. Our results expose system prompts as a critical yet largely unprotected attack surface in modern agent systems.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：自主代码智能体（如基于大语言模型构建的CLI智能体）在与环境交互时，可能被恶意利用来窥探或恢复其隐藏的**系统提示（system prompt）**，这是一种此前未被充分认识的安全漏洞。
- **研究动机**：随着LLM从简单对话转向具备工具使用、长期推理和自我交互能力的自主代码智能体，其攻击面显著扩大。系统提示作为控制模型行为的隐藏指令，一旦泄露，可能导致模型被逆向工程、越狱或安全机制失效。
- **整体含义**：该工作揭示了“系统提示提取”是代码智能体本体固有的安全风险，而非仅通过手工提示工程才能实现的攻击，需引起业界对智能体接口安全的重新审视。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：提出**JustAsk**框架，一种**自演化（self-evolving）**的自动化提取方法，通过智能体与模型的交互，自主发现有效的提取策略，无需手工设计提示、标注数据或特权访问。
- **关键技术细节**：
  - **在线探索问题建模**：将系统提示提取形式化为在线探索问题，利用**上置信界（UCB）**策略选择最优动作，平衡探索与利用。
  - **层次化技能空间**：设计包含**原子探测（atomic probes）**和**高层编排（high-level orchestration）**的两层技能体系。原子探测指单次提示模板，高层编排则负责组合多个原子探测形成完整攻击流程。
  - **利用模型弱点**：这些技能充分利用了系统指令泛化不完善（模型对指令边界模糊）以及“有帮助性（helpfulness）”与“安全性（safety）”之间的固有冲突，从而逐步诱使模型泄露系统提示。
- **算法流程（文字描述）**：
  1. 初始化技能池（包含多种探测策略）。
  2. 在每次交互回合中，基于UCB选取一个技能执行。
  3. 根据模型回复是否包含系统提示片段获得奖励信号。
  4. 更新UCB分数，并动态调整技能权重；若某技能有效，则生成衍生技能扩展技能空间。
  5. 重复直至系统提示完全恢复或达到预算上限。

（文中未提供具体公式，以上基于摘要的“Upper Confidence Bound-based strategy selection”和“hierarchical skill space”推断。）

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集/场景**：实验在**41个黑盒商业模型**上进行，涵盖多家提供商（如OpenAI、Anthropic等），但论文未公开模型的具体名称和版本列表。没有使用常见的公开数据集或基准测试集，而是直接在真实API上评估。
- **Benchmark**：论文未定义独立的benchmark，而是以“能否完整或近完整恢复系统提示”作为成功标准。
- **对比方法**：文中明确提到“Unlike prior prompt-engineering or dataset-based attacks”，但**未提供任何基线方法**的直接对比。也就是说，JustAsk的评估是单独进行的，没有与已有手工提示攻击或数据集攻击做定量比较，仅通过自述“一致实现完全或近完全恢复”来证明有效性。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）

- **文中未说明**：摘要及元数据中均未提及任何关于计算资源（GPU型号、数量、训练/推理时长）的信息。因此无法评估其算力开销。

### 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平

- **实验数量**：仅有一组主实验：在41个黑盒模型上运行JustAsk，报告了成功提取的结果。**未提及任何消融实验**（如不同UCB参数、技能空间大小的影响）、鲁棒性测试或针对不同系统提示复杂度的分类分析。
- **充分性**：从覆盖模型数量看（41个），具有一定广度，能够说明漏洞的普遍性。但缺乏对比基线、缺乏消融实验、缺乏对失败案例的分析，使得实验的**深入性不足**。此外，论文未说明如何定义“完全恢复”或“近完全恢复”的度量标准，客观性有待验证。
- **公平性**：由于没有对比方法，无法评估JustAsk相对于现有方法的优势。且“一致成功”的表述可能过于乐观，需考虑模型可能更新或防御机制变化的影响。

### 6. 论文的主要结论与发现

- **主要结论**：
  - 系统提示提取是代码智能体（包括CLI智能体）**固有且普遍存在的安全漏洞**，在41个前沿商业LLM中均可实现。
  - JustAsk无需人工干预即可自动发现有效提取策略，揭示了系统提示作为**重要的但缺乏保护的攻击面**。
  - 漏洞根源在于智能体交互中**系统指令泛化不完善**以及**帮助性与安全性的冲突**，属于设计/架构层面的脆弱性。
- **发现**：
  - 多模型间存在重复的提取漏洞模式，表明该问题并非个别产品缺陷。
  - 即使模型经过安全对齐，仍难以抵抗逐步交互式的提取。

### 7. 优点：方法或实验设计上的亮点

- **方法上的亮点**：
  - **完全自动化**：无需手工构造提示词或依赖外部数据集，降低了攻击门槛，也使得评估更为系统化。
  - **自演化能力**：通过UCB和层次化技能空间，框架能动态调整策略，适应不同模型的行为模式，提高可迁移性。
  - **揭示新攻击面**：首次系统性地将系统提示提取与代码智能体的自主性关联起来，为AI安全研究开辟了新的方向。
- **实验设计上的亮点**：
  - **大规模黑盒测试**：覆盖41个商业模型，跨多个提供商，实证了问题的广泛性。
  - **现实场景模拟**：仅通过标准用户接口与模型交互，符合真实攻击场景，结果具有参考价值。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖不足**：
  - 未测试开源模型（如Llama、Mistral）或小型模型，无法判断漏洞是否限于商业大型模型。
  - 未提供模型具体版本号，结果无法复现。
  - 缺少消融实验，无法判断各组件（UCB、技能空间等）的贡献。
- **偏差风险**：
  - 摘要中声称“一致实现完全或近完全恢复”，但未给出具体成功率、失败案例或提取完整度的分布，可能存在选择性报告。
  - 未说明如何避免过度拟合特定模型（如测试集可能与训练交互策略相关）。
- **应用限制**：
  - 方法高度依赖代码智能体的交互能力，对于纯对话API（如普通ChatGPT）可能效果有限（论文聚焦于“代码智能体”）。
  - 未讨论对抗防御措施（如提示混淆、过滤、使用虚拟系统提示等），因此无法评估JustAsk的鲁棒性。
  - 未提供伦理讨论或负责任披露细节，可能带来双用途治理风险。
- **其他**：论文未提及算力消耗，难以判断实际部署代价。

（完）
