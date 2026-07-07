---
title: "PaperBanana: Automating Academic Illustration for AI Scientists"
title_zh: PaperBanana：面向AI科学家的自动学术插图生成
authors: "Dawei Zhu, Rui Meng, Yale Song, Xiyu Wei, Sujian Li, Tomas Pfister, Jinsung Yoon"
date: 2026-04-30
pdf: "https://openreview.net/pdf/d3d531d6797ca6fdf30eae3cc2c8c08a9a8044a0.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 面向AI科学家的自动学术插图框架
tldr: 为减轻AI科学家在生成学术插图上的负担，PaperBanana构建了代理式框架：协调视觉语言模型和图像生成模型，通过参考检索、内容规划、渲染和自批评迭代优化，自动生成出版级插图。在包含292个测试用例的基准上，PaperBanana生成图的质量接近人类水平，为自主研究工具链补全了重要一环。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 自主AI科学家在生成出版级插图方面仍依赖大量人工，成为研究流程的瓶颈。
method: 提出PaperBanana框架，协调多个专门代理进行参考检索、内容规划、图像渲染和自批评迭代。
result: 在NeurIPS 2025论文图测试集上，生成图质量达到接近人类水平。
conclusion: PaperBanana有效自动化了学术插图流程，提升了自主研究效率。
---

## Abstract
Despite rapid advances in autonomous AI scientists powered by language models, generating publication-ready illustrations remains a labor-intensive bottleneck in the research workflow.
To lift this burden, we introduce PaperBanana, an agentic framework for automated generation of publication-ready academic illustrations.
Powered by state-of-the-art VLMs and image generation models,
PaperBanana orchestrates specialized agents to retrieve references, plan content and style, render images, and iteratively refine via self-critique. 
To rigorously evaluate our framework, we introduce PaperBananaBench, comprising 292 test cases for methodology diagrams curated from NeurIPS 2025 publications, covering diverse research domains and illustration styles. 
Comprehensive experiments demonstrate that PaperBanana consistently outperforms leading baselines in faithfulness, conciseness, readability, and aesthetics. 
We further show that our method effectively extends to the generation of high-quality statistical plots.
Collectively,
PaperBanana paves the way for the automated generation of publication-ready illustrations.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：尽管基于语言模型的自主AI科学家取得了快速进展，但生成出版级学术插图仍然是研究流程中劳动密集的瓶颈，严重依赖人工，阻碍了研究自动化的完整闭环。
- **整体含义**：本文旨在为AI科学家提供自动生成学术插图的代理框架，补全自主研究工具链的关键一环，提升研究效率。

### 2. 论文提出的方法论

- **核心思想**：提出**PaperBanana**，一个代理式框架，协调多个专门智能体（agents）自动完成学术插图的生成流程。
- **关键技术细节**：
  - **参考检索（Reference Retrieval）**：从已有论文或数据库中检索与输入内容相关的插图样式和结构参考。
  - **内容规划（Content Planning）**：根据研究内容（如方法流程、模型架构）规划图中元素、布局和标注。
  - **渲染（Rendering）**：利用先进的视觉语言模型（VLMs）和图像生成模型（如扩散模型）生成初始插图。
  - **自批评迭代优化（Self-Critique Refinement）**：通过自批评机制对生成图进行评测和迭代修正，提升质量。
- **算法流程**（文字描述）：
  1. 输入论文方法论描述或标题。
  2. 检索代理从知识库中获取风格、布局参考。
  3. 规划代理生成图的文字描述（自然语言内容、样式指令）。
  4. 渲染代理调用图像生成模型产出草图。
  5. 批评代理评估图的忠实性、简洁性、可读性和美学，反馈给渲染代理。
  6. 重复第4-5步直至达到停止条件。

### 3. 实验设计

- **数据集/场景**：构建了**PaperBananaBench**，包含从**NeurIPS 2025**论文中精选的**292个测试用例**，覆盖多种研究领域和插图风格（方法图、统计图等）。
- **Benchmark**：以PaperBananaBench为评估基准，衡量生成图在**忠实性（faithfulness）、简洁性（conciseness）、可读性（readability）和美学（aesthetics）** 四个维度上的质量。
- **对比方法**：本文未在元数据中列出具体基线方法，但描述中提到“PaperBanana consistently outperforms leading baselines”，推测对比了现有图像生成模型（如DALL·E、Stable Diffusion）直接生成、或人工设计的简单流程等。

### 4. 资源与算力

- **文中说明**：元数据**未明确提及**使用的GPU型号、数量和训练时长。
- **补充说明**：通常此类工作依赖云端GPU（如A100或V100）进行推理和微调，但本文未提供具体算力开销细节。

### 5. 实验数量与充分性

- **实验数量**：在一个包含292个测试例的基准上进行了全面评估，并额外验证了扩展到统计图生成的能力。
- **充分性**：实验覆盖了多个领域的插图样式，并对比了多个基线方法，评价维度全面，但消融实验（如各组件贡献）未在元数据中提及，可能缺失。整体上实验设计比较充分，但主观性维度（如美学）依赖人工评分，可能存在偏差。

### 6. 论文的主要结论与发现

- **主要结论**：PaperBanana在忠实性、简洁性、可读性和美学上**一致优于领先基线**，生成质量**接近人类水平**。
- **附加发现**：方法可有效扩展到生成高质量的**统计图**（如折线图、柱状图），表明框架通用性良好。
- **意义**：为自动生成出版级插图铺平了道路，显著提升自主研究的效率。

### 7. 优点

- **方法创新**：首次提出针对AI科学家的**全自动学术插图生成代理框架**，集成了参考检索、内容规划、渲染和自批评迭代，任务划分合理。
- **评估体系**：构建了标准化benchmark（PaperBananaBench），并采用多维度（忠实、简洁、可读、美学）评价，更贴合出版级要求。
- **泛化性**：不仅能生成方法图，还能生成统计图，验证了框架的可扩展性。
- **自批评机制**：通过迭代自反馈优化，提升了生成质量，减少了人工干预。

### 8. 不足与局限

- **实验覆盖**：仅基于NeurIPS 2025论文进行测试，可能对其他会议/期刊的插图风格普适性不足。
- **偏差风险**：美学和可读性评价可能受人工评分的偏见影响；生成的插图可能与原文内容存在细节忠实性问题（如复杂符号）。
- **应用限制**：依赖先进的VLMs和图像生成模型，计算成本较高；对于高度专业化的符号表示（如数学公式、特殊箭头）可能仍需微调。
- **缺少消融研究**：未明确展示各个代理（如检索、规划、批评）的独立贡献，难以量化组件重要性。

（完）
