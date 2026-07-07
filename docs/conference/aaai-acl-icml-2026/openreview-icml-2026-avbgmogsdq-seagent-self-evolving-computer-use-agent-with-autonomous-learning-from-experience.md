---
title: "SEAgent: Self-Evolving Computer Use Agent with Autonomous Learning from Experience"
title_zh: "SEAgent: 具有自主经验学习的自进化计算机使用智能体"
authors: "Zeyi Sun, Ziyu Liu, Yuhang Zang, Yuhang Cao, Xiaoyi Dong, Tong Wu, Dahua Lin, Jiaqi Wang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/82abdbced9d1bf9b03f3b3c2378f1567bec05198.pdf"
tags: ["query:cli-agent"]
score: 6.0
evidence: SEAgent通过经验学习使智能体自主掌握软件使用，可应用于CLI智能体
tldr: 当前计算机使用智能体依赖人工标注数据，难以处理不熟悉软件。SEAgent通过自主探索和迭代试错，让智能体在无标注场景下逐步学习新软件环境，并自动生成从简单到复杂的课程任务。该框架可推广至CLI智能体等特定软件场景。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有计算机使用智能体依赖人工标注，难以适应不熟悉软件。
method: 提出自进化框架，通过经验学习、课程任务生成实现自主进化。
result: 在多个新型软件环境中，智能体实现了高效的自主适应和任务执行。
conclusion: 自主经验学习范式可显著提升软件使用智能体的泛化能力。
---

## Abstract
Repurposing large vision-language models (LVLMs) as computer use agents (CUAs) has led to substantial breakthroughs, primarily driven by human-labeled data. However, these models often struggle with novel and specialized software, particularly in scenarios lacking human annotations. To address this challenge, we propose SEAgent, an agentic self-evolving framework enabling CUAs to autonomously evolve through interactions with unfamiliar software. Specifically, SEAgent empowers computer-use agents to autonomously master novel software environments via experiential learning, where agents explore new software, learn through iterative trial-and-error, and progressively tackle auto-generated tasks organized from simple to complex. To achieve this goal, we design a World State Model for step-wise trajectory assessment, along with a Curriculum Generator that generates increasingly diverse and challenging tasks. The agent's policy is updated through experiential learning, comprised of adversarial imitation of failure actions and Group Relative Policy Optimization (GRPO) on successful ones. Furthermore, we introduce a specialist-to-generalist training strategy that integrates individual experiential insights from specialist agents, facilitating the development of a stronger generalist CUA capable of continuous autonomous evolution. This unified agent ultimately achieves performance surpassing ensembles of individual specialist agents on their specialized software. We validate the effectiveness of SEAgent across five professional software of OSWorld, ScienceBoard and AndroidWorld. Our approach achieves a significant improvement over a competitive open-source CUA, UI-TARS. All the code and models will be made publicly available to foster further research.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：当前大视觉语言模型（LVLMs）作为计算机使用智能体（CUA）已取得显著突破，但这些突破主要依赖于人工标注数据。当面对新颖、专业化的软件环境时（尤其缺乏人工标注），现有CUA表现不佳。
- **核心问题**：如何让CUA在没有人类标注的情况下，自主适应并掌握陌生软件的操作，实现自进化式的学习。
- **整体含义**：SEAgent提出了一种自进化框架，使CUA能够通过与软件的自主交互、试错学习、课程任务生成和策略优化，在不依赖人类示范的情况下逐步提升能力。该范式有望显著增强CUA的泛化能力，使其适用于更广泛的专用软件场景（如CLI智能体）。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：将计算机使用智能体的学习过程建模为“自主探索 → 经验积累 → 课程任务生成 → 策略优化”的自进化循环，使智能体在没有人类标注的环境中也能持续进步。
- **关键技术细节**：
  - **World State Model（世界状态模型）**：用于对智能体每步轨迹进行细粒度评估，判断动作成功与否，为后续学习提供监督信号。
  - **Curriculum Generator（课程生成器）**：自动生成从简单到复杂、多样化的任务序列，引导智能体渐进式学习。
  - **经验学习（Experiential Learning）**：包含两个组件：
    - 对抗性模仿失败动作（Adversarial Imitation of Failure Actions）：从失败中学习，避免重复错误。
    - 基于成功动作的组相对策略优化（GRPO）：利用成功轨迹进行强化学习，优化策略。
  - **专家到通才训练策略（Specialist-to-Generalist Training）**：先训练多个针对特定软件的专家智能体，再将其个体经验整合到统一的通才智能体中，使其在多个软件上均能表现优异，甚至超过专家集成。
- **算法流程（文字说明）**：
  1. 智能体在陌生软件环境中进行自主探索，执行动作并观察状态变化。
  2. World State Model评估每一步动作的成功/失败。
  3. 根据评估结果，Curriculum Generator动态生成新任务，难度逐步提升。
  4. 在成功轨迹上应用GRPO更新策略，在失败轨迹上应用对抗模仿学习，避免重蹈覆辙。
  5. 对于多个软件环境，分别训练专家智能体，然后通过知识蒸馏或参数集成形成通才智能体。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：使用了五个专业软件环境，分别来自：
  - **OSWorld**（操作系统级别应用）
  - **ScienceBoard**（科学计算/模拟软件）
  - **AndroidWorld**（Android移动端应用）
  - 具体软件名称未在摘要详细列出，但表明覆盖桌面和移动端、通用及科学领域。
- **Benchmark**：以各软件环境中的任务完成成功率作为主要评估指标。
- **对比方法**：对比了当前具有竞争力的开源CUA——**UI-TARS**（推测为基线模型）。实验表明SEAgent在该基线上取得了显著性能提升。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长等具体算力资源。仅提及“所有代码和模型将公开”，但未提供训练成本细节。这可能是因为论文更多聚焦方法理念和实验效果，资源消耗信息通常会在正文中补充，但当前摘要未包含。

## 5. 实验数量与充分性

- **实验数量**：在5个不同的专业软件环境中进行了验证，覆盖OS、科学计算、移动端等多个领域。但未详细说明每个环境内的任务数量、重复次数等。
- **充分性判断**：
  - **积极方面**：对比了单一开源基线（UI-TARS），并声称超过其集成性能，提供了比较。同时通过专家到通才策略验证了泛化能力。
  - **不足**：未报告与传统监督学习方法（如人工标注训练）的对比；未展示消融实验（如去除World State Model或课程生成器的影响）；缺少与更多SOTA方法的比较（例如商业模型如GPT-4V作为CUA）。因此实验充分性有限，但符合学术论文初步验证的常规。

## 6. 主要结论与发现

- SEAgent框架使CUA能够在不依赖人类标注的条件下，通过自主经验学习适应并掌握全新软件环境。
- 课程任务生成（从简单到复杂）有效引导了智能体逐步提升能力。
- 结合失败模仿和成功策略优化（GRPO）的经验学习效果优于单一优化方法。
- 专家到通才训练策略使得一个统一模型在多个专用软件上的表现甚至超过了多个专有专家模型的集成。
- 在五个专业软件上，SEAgent显著优于开源基线UI-TARS。

## 7. 优点：方法或实验设计上的亮点

- **自主性**：完全消除了对人类标注数据的依赖，实现了真正的自进化，极具实用价值。
- **课程学习设计**：Curriculum Generator按难度自动生成任务，符合学习规律，提升学习效率。
- **双重优化机制**：同时利用失败（对抗模仿）和成功（GRPO）经验，全方位利用交互数据。
- **专家到通才整合策略**：解决了多软件场景下泛化与专业化之间的平衡问题，且最终模型性能优于专家集成。
- **跨领域验证**：涵盖了桌面、科学、移动端等多种软件类型，证明了方法的普适性。

## 8. 不足与局限

- **实验覆盖偏窄**：对比方法仅有一个开源基线（UI-TARS），未与更多先进CUA（如商业模型或其他强化学习方法）比较，难以全面定位性能水平。
- **缺乏消融实验细节**：未在摘要中展示各组件的贡献度（如除去课程生成器或World State Model会如何），使得因果推断不够清晰。
- **潜在偏差风险**：五个软件环境的选择可能偏向于适合该方法特性的场景，对于更复杂、噪音更大的真实软件（如频繁错误交互、状态不可观察等）泛化能力未知。
- **资源需求未说明**：训练成本可能较高（需要迭代探索、RL优化），缺乏算力信息会影响可复现性评估。
- **对基础模型的依赖**：该方法需要初始的LVLM作为基础，若基础模型能力不足，自进化可能效果有限。未讨论基础模型选择的影响。

（完）
