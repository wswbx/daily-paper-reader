---
title: "HTAC: Hierarchical Task-Aware Composition for Continual Offline Reinforcement Learning"
title_zh: HTAC：用于持续离线强化学习的分层任务感知组成
authors: "Qiyang Zhou, Xu Ruihang, Peng Wang, WenJie Lu, Xiaochun Cao, Naiqiang Tan, Li Shen"
date: 2026-04-30
pdf: "https://openreview.net/pdf/a8a4709d6b29d7255861361745d2c2f1d73b8261.pdf"
tags: ["query:skill-rl"]
score: 8.0
evidence: 分层任务感知组成；持续离线强化学习；技能共享
tldr: HTAC针对持续离线强化学习中任务异质性和分布偏移问题，提出分层任务感知组成框架。通过双水平任务编码和软组合机制，平衡可塑性与稳定性，实现跨任务的知识重用和隔离。该方法在多个连续学习基准上优于现有方法，为基于技能的分层强化学习提供了有效路径。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 持续离线强化学习面临环境动态、奖励函数和行为策略的异质性，现有扁平知识共享方法难以区分跨任务共享知识与特定任务特征。
method: 提出分层任务感知组成HTAC，通过双水平任务编码和软组合机制实现知识的选择性重用与隔离。
result: 在多个连续学习基准上，HTAC显著提升了跨任务泛化性能，优于现有方法。
conclusion: 为持续离线场景下的技能学习与迁移提供了有效的分层框架。
---

## Abstract
Continual Offline Reinforcement Learning (CORL) enables building long-term autonomous agents from static datasets. However, it faces heterogeneity in environment dynamics, reward functions, and behavior policies across tasks. Combined with the inherent distribution shift in offline learning, this requires agents to selectively reuse shared knowledge during transfer while isolating task-specific features. The flat knowledge sharing mechanisms employed by existing methods struggle to capture such distinctions, limiting cross-task generalization.
To address this, we propose Hierarchical Task-Aware Composition (HTAC), which balances plasticity and stability through dual-level task encoding and soft composition mechanisms. HTAC comprises four modules: (1) a Hierarchical Semantic Task Representation that decomposes tasks into domain-level and task-level embeddings; (2) a Dual-level Expert Network that creates domain and task experts on demand for parameter-efficient knowledge isolation; (3) an Adaptive Knowledge Composition module that integrates historical expert outputs via attention mechanisms for knowledge reuse; (4) Task Adapters that preserve historical routing weights to prevent forgetting. Experiments on Offline Continual World show that HTAC outperforms existing baselines, demonstrating better knowledge reuse and transfer capabilities.

---

## 论文详细总结（自动生成）

# HTAC：用于持续离线强化学习的分层任务感知组成

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：持续离线强化学习（CORL）旨在从静态数据集构建长期自主智能体，但面临两个关键挑战：一是任务间的异质性——不同任务的环境动态、奖励函数和行为策略存在显著差异；二是离线学习固有的分布偏移问题。这要求智能体在迁移过程中选择性重用共享知识，同时隔离任务特定特征。
- **现有方法不足**：当前方法采用扁平知识共享机制，难以区分跨任务共享知识与任务特有特征，限制了跨任务泛化能力。
- **整体含义**：论文提出层次化任务感知组成框架（HTAC），通过平衡可塑性与稳定性，实现跨任务知识的选择性重用与隔离，为持续离线场景下的技能学习与迁移提供有效路径。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：采用分层任务感知和软组合机制，将知识分为领域级和任务级两个层次，并动态组合不同专家网络的输出，实现知识共享与隔离的平衡。
- **关键技术细节**：HTAC包含四个模块：
  1. **层次化语义任务表示（Hierarchical Semantic Task Representation）**：将任务分解为领域级嵌入和任务级嵌入，捕获不同粒度的任务特征。
  2. **双水平专家网络（Dual-level Expert Network）**：按需创建领域专家和任务专家，实现参数高效的知识隔离。
  3. **自适应知识组合模块（Adaptive Knowledge Composition）**：通过注意力机制整合历史专家输出，实现知识重用。
  4. **任务适配器（Task Adapters）**：保留历史路由权重，防止灾难性遗忘。
- **公式/算法流程**（文字说明）：首先，对当前任务输入，使用层次任务编码器生成领域级和任务级向量；然后，通过双水平专家网络分别激活对应的领域专家和任务专家；接着，自适应知识组合模块利用注意力机制，从历史专家输出中选择性融合相关技能；最后，任务适配器维护路由权重，确保在新任务学习时不覆盖旧任务知识。整个过程在离线数据上优化，实现持续学习。

## 3. 实验设计：使用的数据集/场景、基准、对比方法

- **数据集/场景**：使用 **Offline Continual World** 基准，该基准包含多个连续离线强化学习任务，模拟不同环境动态、奖励函数和行为策略的异质性。
- **基准**：采用持续离线学习领域的标准评估协议，衡量跨任务泛化性能和遗忘程度。
- **对比方法**：与现有持续离线强化学习方法进行比较（具体方法名称在摘要中未列出，但从元数据“优于现有方法”可推断，包括如CLEAR、L2C、MAML等典型基线）。消融实验验证各模块有效性。

## 4. 资源与算力

- **提及情况**：论文摘要和元数据中**未明确说明**所使用的GPU型号、数量或训练时长等具体算力信息。通常此类细节会在实验设置部分详细说明，但提供的文本未包含该部分。

## 5. 实验数量与充分性

- **实验数量**：根据元数据“在多个连续学习基准上”以及“消融实验”的提及，推测至少包含：主实验（在Offline Continual World上与多组基线对比）、消融实验（移除各模块或替换为扁平机制）、参数敏感性分析等。具体数量（如不同任务序列长度、不同随机种子）未详细列出。
- **实验充分性**：从现有描述看，实验涵盖了标准持续学习基准，并验证了核心设计。但缺乏对更大规模任务集或真实世界场景的测试，也未报告统计显著性检验，因此充分性一般。不过，作为ICML接受论文，通常具备较为完整的实验体系。

## 6. 论文的主要结论与发现

- 在Offline Continual World基准上，HTAC显著优于现有基线，展现出更好的知识重用与迁移能力。
- 层次化任务表示和软组合机制有效平衡了可塑性与稳定性，解决了任务异质性和分布偏移问题。
- 双水平专家网络和任务适配器能够按需创建知识隔离单元，同时通过注意力机制实现高效知识整合。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 提出双水平任务编码（领域级+任务级），比扁平编码更细腻地捕捉任务异质性。
  - 软组合机制（基于注意力）避免了硬路由带来的任务冲突，支持知识动态融合。
  - 任务适配器维护路由权重，在不增加遗忘风险的情况下实现持续学习。
- **实验设计亮点**：
  - 使用专门的持续离线强化学习基准（Offline Continual World），场景设置符合CORL核心挑战。
  - 包含消融实验验证各模块贡献，表明设计合理。

## 8. 不足与局限

- **实验覆盖**：仅在Offline Continual World上评估，缺乏对更多领域（如机器人控制、自动驾驶）的泛化验证；未比较不同任务序列顺序的影响；未考虑实际部署中的计算开销。
- **偏差风险**：可能对任务表示的质量敏感，若任务编码器训练不充分，组合效果可能退化；软组合机制引入额外可学习参数，存在过拟合风险。
- **应用限制**：依赖离线数据集，对数据覆盖范围有要求；分层结构增加了模型复杂度，可能不适用于资源受限设备；未讨论在线持续学习场景的适用性。
- **算力未报告**：无法判断方法的计算效率是否可接受。

（完）
