---
title: "Orion: Towards Lab Automation with Computer-Using Agents"
title_zh: Orion：迈向使用计算机代理的实验室自动化
authors: "Ma, C., Trinh, L., Bucci, M., Regev, A., Wang, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.13.732095v1.full.pdf"
tags: ["query:cli-agent"]
score: 9.0
evidence: 结合大型语言模型与终端执行实现实验室自动化
tldr: "实验室计算工作流依赖人工操作专用软件和视觉检查，效率低下。为此，提出Orion，一个结合大语言模型与终端执行、GUI控制的计算机使用智能体，可操作软件、挖掘网络资源并执行端到端分析。在生物医学检索任务上准确率超90%，学会了CellProfiler和QuPath进行图像分析。100小时自主探索生成52份研究报告中，22个假设被优先考虑。证明了计算机使用AI可扩展实验室自动化，提供可审计路径。"
source: biorxiv
selection_source: fresh_fetch
motivation: 实验室计算工作流受限于劳动密集型软件操作和跨源知识整合，现有自动化方案缺乏通用性。
method: Orion结合大语言模型与终端执行、GUI控制和自适应多步推理，在共享计算环境中操作软件、检查图像和挖掘网络资源。
result: "在检索任务上准确率超90%，学会CellProfiler和QuPath；100小时自主探索生成52份报告，其中22个假设被优先考虑。"
conclusion: 计算机使用AI智能体能扩展实验室自动化，为从实验数据到分析、报告和假设提供可审计路径。
---

## 摘要
实验室发现越来越依赖于将实验数据连接到分析、解释和后续假设的计算工作流程。然而，这些工作流程仍然受到使用专业软件的劳力密集型操作、通过图形用户界面进行视觉检查以及跨多个来源的知识整合的制约。在这里，我们介绍Orion，一个用于生物医学图像分析和解释的计算机使用型AI代理，它通过自动化实验室工作的计算层迈向实验室自动化。Orion在共享计算环境中结合了大型语言模型与终端执行、GUI控制和自适应多步推理。它可以检查视觉数据、操作标准科学软件、挖掘网络资源并进行端到端的分析和解释工作流程，无需定制的软件集成。在基准测试中，Orion在生物医学数据库和文献检索任务上实现了超过90%的准确率，学会了使用流行工具CellProfiler和QuPath分别进行细胞和组织图像的定量分析，并促进了实验成像数据中的自主发现。在100小时的大规模扰动成像数据集自主探索中，Orion生成了52份研究报告，其中人类科学家审阅后优先选择了22个合理的机制假设。这些结果表明，使用计算机的AI代理可以显著扩大实验室自动化的范围，提供从实验成像数据到定量分析、报告和生物学基础假设的可扩展且可审计的路径。

## Abstract
Laboratory discovery increasingly depends on computational workflows that connect experimental data to analysis, interpretation and follow-up hypotheses. Yet these workflows remain constrained by labor-intensive use of specialized software, visual inspection through graphical user interfaces, and integration of knowledge across multiple sources. Here, we present Orion, a computer-using AI agent for biomedical image analysis and interpretation that moves towards lab automation by automating this computational layer of laboratory work. Orion combines large language models with terminal execution, GUI control and adaptive multi-step reasoning in a shared computing environment. It can inspect visual data, operate standard scientific software, mine web resources and conduct end-to-end analysis and interpretation workflows without requiring bespoke software integrations. Across benchmarks, Orion achieved over 90% accuracy on biomedical database and literature retrieval tasks, learned to use the popular tools CellProfiler and QuPath for quantitative analysis of cellular and tissue images, respectively, and facilitated autonomous discovery in experimental imaging data. In 100 hours of autonomous exploration of a large-scale perturbation imaging dataset, Orion generated 52 research reports, of which human scientist review prioritized 22 plausible mechanistic hypotheses. These results show that computer-using AI agents can substantially expand the reach of laboratory automation, providing a scalable and auditable route from experimental imaging data to quantitative analysis, reports and biologically grounded hypotheses.

---

## 论文详细总结（自动生成）

# 论文总结：Orion：迈向使用计算机代理的实验室自动化

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：实验室计算工作流（如生物医学图像分析、数据解释、假设生成）严重依赖人工操作专业软件、通过图形用户界面（GUI）进行视觉检查、以及跨多个来源的知识整合，效率低下且难以规模化。
- **研究动机**：现有实验室自动化方案多聚焦于物理实验步骤（如液体处理），缺乏对“计算层”的通用自动化能力；定制化的软件集成成本高、可迁移性差。
- **整体含义**：提出一种“计算机使用AI代理”（Computer-Using Agent），通过直接操纵标准科学软件的GUI和终端，实现端到端的分析、报告和假设生成，有望显著扩大实验室自动化的范围，并提供可审计的实验路径。

## 2. 论文提出的方法论：核心思想、关键技术细节、流程

- **核心思想**：结合大型语言模型（LLM）与终端执行、GUI控制和自适应多步推理，在共享计算环境中模拟人类科学家的操作流程——观察视觉数据、操作软件、挖掘网络资源、生成分析报告。
- **关键技术细节**：
  - 采用LLM作为决策核心，接收环境反馈（屏幕截图、终端输出、文件内容）并生成下一步动作（键盘/鼠标操作、命令执行）。
  - 支持终端执行（命令行工具、脚本）和GUI控制（通过视觉定位点击、输入），无需专属API或定制集成。
  - 具备自适应多步推理能力：可分解复杂任务，根据中间结果动态调整计划。
- **流程示例**：用户给定目标（如“分析某细胞图像中特定蛋白质的表达”），Orion自动启动CellProfiler，加载图像、设置分析模块、运行并导出结果；随后可能调取网络知识库解释发现的差异，最终生成研究报告。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集与场景**：
  - 生物医学数据库和文献检索任务（基准测试）。
  - 细胞与组织图像分析：使用流行的CellProfiler（细胞定量分析）和QuPath（组织图像分析）作为工具。
  - 大规模扰动成像数据集：对100小时的自主探索，生成研究报告中筛选生物学假设。
- **Benchmark**：未明确说明具体基准名称，但对应生物医学检索任务准确率超90%。
- **对比方法**：论文未提及与其他AI代理或自动化工具的直接对比，主要展示Orion自身能力（学会使用新工具并自主发现）。可能缺乏系统性的SOTA对比。

## 4. 资源与算力

- **论文未明确说明使用的GPU型号、数量或训练时长**。仅提到“100小时自主探索”，但这是推理时间而非训练时间。模型可能基于现有LLM（如GPT-4或类似）进行微调或仅用提示工程，但具体算力细节缺失。

## 5. 实验数量与充分性

- **实验数量**：主要涉及三类实验——①检索任务（准确率>90%）；②工具学习（CellProfiler和QuPath）；③100小时自主探索（生成52份报告，优先22个假设）。未提及消融实验或消融变量。
- **充分性与公平性**：
  - 实验覆盖了端到端能力的关键环节（检索、工具操作、假设发现），但缺乏与已有实验室自动化方法（如基于API的集成系统）的定量对比。
  - 检索任务的准确率数据可能来自内部构建的测试集，未见公开基准的评估。
  - 假设筛选依赖人类科学家审阅，具有一定主观性，但提供了可复现的审计路径。
  - 总体实验设计偏向于演示可行性而非严格对比，充分性一般。

## 6. 论文的主要结论与发现

- **结论**：计算机使用AI代理（如Orion）可以显著扩大实验室自动化的范围，实现从实验成像数据到定量分析、报告和生物学基础假设的可扩展、可审计路径。
- **关键发现**：
  - 在生物医学数据库和文献检索任务上准确率超过90%。
  - 成功学会使用CellProfiler和QuPath进行图像分析，无需定制集成。
  - 100小时自主探索中，生成52份研究报告，其中22个假设被人类科学家视为合理并优先考虑，证明了自主发现潜力。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 无需定制软件集成：通过GUI+终端控制，直接操纵现有科学软件，通用性强。
  - 可审计性：每一步操作都有迹可循（屏幕截图、命令日志），便于复现和验证。
  - 端到端自动化：从原始数据到研究报告、假设生成，覆盖科学发现全流程。
- **实验设计亮点**：
  - 使用真实科研工具（CellProfiler、QuPath）和实际扰动成像数据集，具有实际应用价值。
  - 长时间自主探索（100小时）展示了系统稳定性和持续发现能力。
  - 人类科学家优先级排序引入了真实科研判断，验证了假设的合理性。

## 8. 不足与局限

- **实验覆盖不足**：
  - 缺乏与现有自动化方法（如基于API的脚本、传统机器人实验室）的定量对比。
  - 未在多样化基准（如多个公开数据集、不同领域软件）上系统评估。
  - 检索任务仅报告准确率，未包含召回率、F1等指标，也未与其他检索系统对比。
- **偏差风险**：
  - 假设筛选依赖人类科学家，可能存在主观偏差；论文未说明审阅人员的背景及一致性问题。
  - 模型可能从训练数据中学习到特定偏好，导致假设偏向已知知识。
- **应用限制**：
  - 依赖LLM的推理能力，对于需要高精度物理操作（如显微镜自动聚焦）的场景可能不适用。
  - GUI控制依赖截图质量，在低分辨率或复杂界面下可能出错。
  - 科研软件的多样性和版本更新可能带来适配挑战。
- **资源与重复性**：
  - 未公开模型权重、具体提示模板或运行环境，复现困难。
  - 算力消耗虽未提及，但长时间推理（100小时）可能成本较高。

（完）
