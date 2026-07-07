---
title: "AgentRx: Diagnosing AI Agent Failures from Execution Trajectories"
title_zh: AgentRx：从执行轨迹诊断AI智能体故障
authors: "Shraddha Barke, Arnav Goyal, Alind Khare, Avaljot Singh, Suman Nath, Chetan Bansal"
date: 2026-01-23
pdf: "https://openreview.net/pdf/faa32b4b0c13f3f9b9ae12632edeb8a7eb9c8b6e.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: 从轨迹诊断AI智能体故障，可应用于CLI智能体
tldr: 该工作手动标注了115个失败的智能体轨迹并发布基准，提出AgentRx自动诊断框架，通过合成约束逐步评估来定位关键失败步骤。实验表明AgentRx能有效诊断包括API工作流、事件管理和开放web/文件任务在内的多领域智能体故障，有助于提高CLI智能体的可靠性。
source: ICML-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有方法难以定位概率性、长程、多智能体且受噪声工具输出干扰的智能体失败原因。
method: 手动标注失败轨迹构建基准，提出AgentRx框架，通过约束合成与逐步评估自动定位关键失败步骤。
result: AgentRx在115个跨越多个领域的失败轨迹上有效识别关键失败步骤，优于基线方法。
conclusion: AgentRx提供通用、无领域依赖的智能体故障诊断方法，可提升CLI智能体等代理系统的调试效率。
---

## Abstract
AI agents often fail in ways that are difficult to localize because executions are probabilistic, long-horizon, multi-agent, and mediated by noisy tool outputs. We address this gap by manually annotating failed agent runs and release a novel benchmark of 115 failed trajectories spanning structured API workflows, incident management, and open-ended web/file tasks. Each trajectory is annotated with a critical failure step and a category from a grounded-theory derived, cross-domain failure taxonomy. To mitigate the human cost of failure attribution, we present AgentRx, an \emph{automated domain-agnostic} diagnostic framework that pinpoints the critical failure step in a failed agent trajectory. It synthesizes constraints, evaluates them step-by-step, and produces an auditable validation log of constraint violations with associated evidence; an LLM-based judge uses this log to localize the critical step and category. Our framework improves step localization and failure attribution over existing baselines across three domains.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

AI智能体（AI Agent）在实际执行中常常出现难以定位的失败，原因包括：执行过程具有概率性、时间跨度长、涉及多智能体协作，以及受噪声工具输出干扰。现有的调试和故障定位方法通常需要大量人工干预，或者局限于特定领域，缺乏通用性。因此，该论文旨在解决**智能体失败步骤的自动、通用化诊断**问题，以减少人工成本、提高调试效率。

## 2. 方法论：核心思想、关键技术细节

**核心思想**：提出名为 **AgentRx** 的自动化、领域无关的故障诊断框架，通过合成约束、逐步评估和可审计的验证日志，定位轨迹中的关键失败步骤。

**关键技术细节**（基于摘要描述）：
- **约束合成**：将失败的智能体执行轨迹转化为一系列可验证的约束条件。
- **逐步评估**：对每个步骤（step）逐一检查这些约束是否被违反，生成约束违反的详细日志，并附上相关证据。
- **LLM-based 裁判**：利用一个基于大语言模型的判断器，根据验证日志，定位关键失败步骤并分类（使用从 grounded-theory 导出的跨领域失败分类体系）。

注：原文未提供具体的公式或算法伪代码，因此此处无法列出。

## 3. 实验设计

- **数据集/场景**：手动标注了 **115 个失败的智能体执行轨迹**，覆盖三个领域：
  1. **结构化 API 工作流**（structured API workflows）
  2. **事件管理**（incident management）
  3. **开放式 Web/文件任务**（open-ended web/file tasks）
- **基准（Benchmark）**：论文将该 115 条标注了关键失败步骤和失败类别的轨迹作为一个新的基准发布。
- **对比方法**：在摘要中提及与“现有基线方法”（existing baselines）进行对比，但未列出具体基线名称。AgentRx 在步骤定位和失败归因方面优于这些基线。

## 4. 资源与算力

**论文中未明确说明**所使用的GPU型号、数量、训练时长等算力信息。无法进行额外观测。

## 5. 实验数量与充分性

- 实验基于 **115 个失败轨迹**，涵盖三个领域，每个轨迹都有人工标注的关键步骤和类别。
- 提供了与基线的对比，但未提及消融实验或更多变体实验。
- **评价**：从摘要看，实验规模有限（115个样本），但覆盖了多领域，具有一定的多样性。未报告统计显著性或多次运行结果，因此充分性一般。公平性方面，需查看全文以确认基线设置是否对等，目前无法判断。

## 6. 主要结论与发现

1. AgentRx 能够**自动、无领域依赖地**诊断智能体失败轨迹中的关键失败步骤。
2. 在三个不同领域的失败轨迹上，AgentRx 在**步骤定位**和**失败归因**上均优于现有基线方法。
3. 该方法通过生成可审计的约束违反日志，提升了诊断的可解释性和可信度。

## 7. 优点

- **自动化与通用性**：无需领域特定知识，即可应用于API工作流、事件管理、开放任务等多种场景。
- **可审计性**：生成的验证日志带有关联证据，便于人类审查和后续修复。
- **基于真实数据**：手动标注115个实际失败轨迹，并建立了跨领域失败分类体系，具有实践价值。
- **解决痛点**：直接针对概率性、长程、多智能体、带噪声输出的复杂失败场景，填补了现有工具的空白。

## 8. 不足与局限

- **实验规模较小**：仅115个失败轨迹，可能不足以覆盖所有失败模式或验证泛化能力。
- **缺乏消融实验**：未对比不同组件（如约束合成策略、LLM评委类型等）的贡献。
- **算力与效率未报告**：无法评估实际运行成本或实时性。
- **潜在偏差**：手动标注可能引入主观性；LLM裁判的可靠性依赖于模型质量，可能存在幻觉或误判。
- **未说明失败类型分布**：115个轨迹中各类别是否均衡？若不平衡，可能影响结论稳健性。
- **缺少与人类诊断的对比**：仅对比其他自动化方法，未与人类专家定位的准确性、时间成本对比。

（完）
