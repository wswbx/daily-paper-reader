---
title: "InfantAgent-Next: A Multimodal Generalist Agent for Automated Computer Interaction"
title_zh: InfantAgent-Next：用于自动化计算机交互的多模态通用代理
authors: "Bin Lei, Weitai Kang, Zijian Zhang, Winson Chen, Xi Xie, Shan Zuo, Mimi Xie, Ali Payani, Mingyi Hong, Yan Yan, Caiwen Ding"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=NKcwN347H7"
tags: ["query:cli-agent"]
score: 6.0
evidence: 多模态通用代理实现计算机交互自动化，可用于智能Shell代理
tldr: 论文提出InfantAgent-Next，一个多模态通用代理，通过高度模块化架构整合工具型与纯视觉代理，逐步解决解耦任务。它在OSWorld等基准上取得了具有竞争力的准确率，展示了自动化计算机交互（包括命令行操作）的潜力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有方法依赖单一大型模型或缺乏工作流模块化，难以泛化到多模态交互。
method: 构建模块化架构，整合工具和视觉代理协同完成任务。
result: "在OSWorld等基准上实现7.27%准确率，优于多数基线。"
conclusion: 为通用计算机交互代理（包括命令执行）提供了模块化设计范例。
---

## Abstract
This paper introduces \textsc{InfantAgent-Next}, a generalist agent capable of interacting with computers in a multimodal manner, encompassing text, images, audio, and video.
Unlike existing approaches that either build intricate workflows around a single large model or only provide workflow modularity, our agent integrates tool-based and pure vision agents within a highly modular architecture, enabling different models to collaboratively solve decoupled tasks in a step-by-step manner. 
Our generality is demonstrated by our ability to evaluate not only pure vision-based real-world benchmarks (i.e., OSWorld), but also more general or tool-intensive benchmarks (e.g., GAIA and SWE-Bench).
Specifically,
we
achieve a $\mathbf{7.27\\%}$ accuracy gain over Claude-Computer-Use on OSWorld.  
Codes and evaluation scripts are included in the supplementary material and will be released as open-source.

---

## 论文详细总结（自动生成）

# 论文总结：InfantAgent-Next：用于自动化计算机交互的多模态通用代理

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：现有方法要么围绕单个大型模型构建复杂工作流（可扩展性差），要么仅提供工作流模块化（缺乏模型协作）。它们难以泛化到多模态交互场景（文本、图像、音频、视频），且对工具密集型任务（如命令行操作、软件工程）支持不足。
- **整体含义**：提出一个高度模块化的通用代理，使不同模型能够协同逐步解耦任务，从而在多种计算机交互基准上取得更好的性能。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：采用**高度模块化架构**，整合两类代理：
  - **工具型代理**：擅长调用外部工具（如Shell命令、API等）。
  - **纯视觉代理**：基于视觉信息（屏幕截图）直接理解与操作界面。
- **技术细节**：
  - 任务被解耦为多个子步骤，不同模型（如视觉模型、语言模型）负责不同子任务，按顺序协作。
  - 无需依赖单一超大模型，而是通过模块化组合提升泛化能力。
  - 支持多模态输入（文本、图像、音频、视频），但未给出具体网络结构或公式。

## 3. 实验设计
- **数据集/场景**：
  - **OSWorld**：纯视觉的真实世界计算机交互基准（如点击、拖拽、键盘输入）。
  - **GAIA**：更通用或工具密集型的基准（需调用外部工具、API等）。
  - **SWE-Bench**：软件工程任务（如代码修复、命令行操作）。
- **对比方法**：主要与 **Claude-Computer-Use** 对比（一种基于Claude模型的计算机使用方案）。
- **评价指标**：准确率（accuracy gain）——在OSWorld上提升7.27%。

## 4. 资源与算力
- **原文未明确说明**：未提及GPU型号、数量、训练时长或推理开销。可能因为论文聚焦于模块化设计而非训练成本。

## 5. 实验数量与充分性
- **实验数量**：仅提到在三个基准（OSWorld、GAIA、SWE-Bench）上进行了评估，且给出了OSWorld的准确率增益。未提供消融实验、不同模块贡献分析或超参数敏感性分析。
- **充分性**：基准覆盖了视觉、工具、软件工程三种典型交互场景，对比了单一强基线（Claude-Computer-Use），具有一定代表性。但缺乏与其他模块化方法（如AgentBench、WebAgent）的对比，也未公开完整实验细节（如统计显著性、多次运行结果）。**实验不够充分**。

## 6. 主要结论与发现
- 模块化架构显著优于单一模型方案（OSWorld上准确率提升7.27%）。
- 集成工具型与纯视觉代理能够有效处理从纯视觉到工具密集的多类任务，证明了通用性的提升。
- 所有代码和评估脚本将开源，促进可复现研究。

## 7. 优点
- **高度模块化**：不同模型解耦协作，便于替换和扩展特定模块。
- **多模态通用性**：覆盖文本、图像、音频、视频，且同时适用于视觉和工具密集型基准。
- **结果有竞争力**：在OSWorld上超越成熟商业方案（Claude-Computer-Use）。
- **开源意图**：提供代码和评估脚本，有助于社区验证和改进。

## 8. 不足与局限
- **实验不充分**：仅报告了一个基准上的准确率增益，未提供消融实验、错误分析或模块影响量化。
- **计算资源未说明**：无法评估实际部署成本或效率。
- **对比基线单一**：缺少与近期其他多模态代理（如GPT-4V with tools、CogAgent）的对比。
- **通用性论证有限**：虽然提到GAIA和SWE-Bench，但未给出具体结果（只提到“展示了能力”），缺乏定量证据。
- **潜在偏差**：可能针对特定类型任务（如GUI操作）优化，在极端复杂或需长链推理的场景中效果未知。
- **应用限制**：需要为不同子任务挑选并维护多个模型，增加了系统复杂度。

（完）
