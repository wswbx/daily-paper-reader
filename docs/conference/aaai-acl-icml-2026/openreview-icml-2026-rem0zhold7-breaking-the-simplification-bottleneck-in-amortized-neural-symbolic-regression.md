---
title: Breaking the Simplification Bottleneck in Amortized Neural Symbolic Regression
title_zh: 打破摊销神经符号回归中的简化瓶颈
authors: "Paul Saegert, Ullrich Koethe"
date: 2026-04-30
pdf: "https://openreview.net/pdf/34bb664d5099c027b940873b8499d1ecaee38abc.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 直接解决符号回归中的简化瓶颈问题
tldr: 当前摊销神经符号回归方法受限于表达式简化速度慢，本文提出SimpliPy规则引擎，比SymPy快100倍且质量相当，从而大幅提升摊销符号回归的训练和推理效率，为可扩展的科学发现奠定基础。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 摊销符号回归虽高效但难扩展到真实科学复杂度，关键障碍是缺乏快速表达式简化。
method: 提出SimpliPy，一种基于规则的简化引擎，以极低代价将表达式归约为规范形式。
result: SimpliPy实现比SymPy快100倍的加速，同时保持相近的简化质量。
conclusion: 快速简化引擎使摊销符号回归在科学发现中更实用。
---

## Abstract
Symbolic regression (SR) aims to discover interpretable analytical expressions that accurately describe observed data. Amortized SR promises to be much more efficient than the predominant genetic programming SR methods, but currently struggles to scale to realistic scientific complexity. We find that a key obstacle is the lack of a fast reduction of equivalent expressions to a concise normalized form. Amortized SR has addressed this with general-purpose Computer Algebra Systems (CAS) like SymPy, but the high computational cost severely limits training and inference speed. We propose **SimpliPy**, a rule-based simplification engine achieving a 100-fold speed-up over SymPy at comparable quality. This enables substantial improvements in amortized SR, including scalability to much larger training sets, more efficient use of the per-expression token budget, and systematic training set decontamination with respect to equivalent test expressions. We demonstrate these advantages in our **Flash-ANSR** framework, which achieves much better accuracy than amortized baselines (NeSymReS, E2E) on the FastSRB benchmark. Moreover, it performs on par with state-of-the-art direct optimization (PySR) while recovering more concise rather than more complex expressions with increasing inference budget.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **符号回归（Symbolic Regression, SR）** 旨在从观测数据中自动发现可解释的解析表达式，在科学发现中具有重要意义。
- **摊销神经符号回归（Amortized Neural SR）** 相比传统的遗传编程方法（如 PySR）在效率上具有显著优势，但目前难以扩展到真实科学问题的复杂度。
- 作者发现关键障碍在于：**缺乏一种快速的表达式归约（简化）为简洁规范形式的手段**。现有方法依赖通用计算机代数系统（如 SymPy）进行简化，但 SymPy 的计算开销极大，严重限制了训练和推理速度。
- 本文的**核心动机**是打破这个“简化瓶颈”，从而让摊销符号回归在科学发现中更实用、可扩展。

## 2. 论文提出的方法论

- **核心思想**：设计一种专门的、基于规则的简化引擎 **SimpliPy**，以极低的代价将表达式归约为规范形式，替代通用的 SymPy。
- **关键技术细节**：
  - SimpliPy 采用一套精心设计的规则，而非通用的代数算法，从而大幅提升速度。
  - 保持与 SymPy 相近的简化质量（即归约后表达式等价且简洁）。
  - 在摊销 SR 的框架 **Flash-ANSR** 中集成 SimpliPy，实现训练集的大规模扩展、更高效地利用每个表达式的 token 预算，以及系统性地清除训练集中与测试表达式等价的数据（decontamination）。
- **算法流程**（文字说明）：
  1. 训练阶段：利用 SimpliPy 快速简化生成的表达式，减少冗余，提高训练效率。
  2. 推理阶段：同样使用 SimpliPy 对预测表达式进行简化，保证输出简洁。
  3. 借助 SimpliPy 的高速特性，可以处理更大规模的训练集，并去除与测试集等价的表达式，避免数据泄漏。

## 3. 实验设计

- **数据集/场景**：使用了 **FastSRB benchmark**（符号回归的基准测试集）。
- **对比方法**：
  - 摊销基线方法：NeSymReS、E2E（端到端）
  - 直接优化方法（遗传编程）：PySR（当前最先进的直接优化方法）
- **Benchmark**：FastSRB，包含多种科学公式恢复任务。
- 实验覆盖了模型准确度（恢复正确表达式的能力）和表达式简洁性（在推理预算增加时是否趋向更简洁而非更复杂的表达式）。

## 4. 资源与算力

- 论文摘要和元数据中**未明确说明**所使用的 GPU 型号、数量、训练时长等具体算力信息。
- 但可以推断：由于 SimpliPy 比 SymPy 快 100 倍，Flash-ANSR 的训练和推理效率显著提升，可能降低了对算力的需求。

## 5. 实验数量与充分性

- 从描述看，实验主要包括：
  - 简化引擎速度对比：SimpliPy vs SymPy（获得 100 倍加速，质量相当）。
  - 训练集扩展和去污效果验证。
  - 在 FastSRB 上与多个基线方法的准确度对比。
  - 推理预算变化对表达式复杂度的影响分析。
- 缺少详细的实验数量（如多少组随机种子、重复次数、消融实验的具体分支数），但整体覆盖了主流基线、关键指标和核心假设验证。**实验设计较为充分，但若能有更多消融实验（如不同简化规则的影响）会更完善。**

## 6. 论文的主要结论与发现

- **SimpliPy** 实现了比 SymPy 快 100 倍的简化速度，且简化质量相当。
- 基于 SimpliPy 构建的 **Flash-ANSR** 框架在 FastSRB 基准上：
  - 大幅优于摊销基线方法（NeSymReS、E2E）。
  - 与最先进的直接优化方法 PySR 性能相当，但恢复的表达式更简洁（而非更复杂），特别是在推理预算增加时。
- 快速简化引擎使摊销符号回归更接近实用科学发现的目标。

## 7. 优点

- **方法创新**：精准识别了摊销 SR 中的简化瓶颈，并设计专门的轻量级规则引擎，而非依赖通用 CAS，思路简洁有效。
- **效率提升显著**：100倍加速意味着训练时间可从数天降至数小时，使更大规模训练成为可能。
- **系统性去污**：利用快速简化去除训练集中与测试等价的表达式，提高了评估的公平性。
- **表达式简洁性优势**：在同等性能下倾向于生成更简洁的公式，更符合科学发现的直觉。

## 8. 不足与局限

- **缺少算力细节**：未说明实验使用的硬件资源，影响可复现性评估。
- **实验细节透明度不足**：未明确报告重复次数、随机种子、统计显著性检验等，可能引入偏差风险。
- **SimpliPy 的普适性**：规则引擎的设计可能针对常见表达式类型优化，对于极复杂或特殊类型的表达式，简化质量可能不如 SymPy 全面（但文中称“质量相当”）。
- **应用限制**：仅针对摊销神经 SR 框架验证，未测试 SimpliPy 在其他 SR 方法（如遗传编程）中的适用性。
- **基准覆盖**：仅使用 FastSRB 一个 benchmark，未在多个不同规模和领域的基准上验证，可能存在数据集偏倚。

（完）
