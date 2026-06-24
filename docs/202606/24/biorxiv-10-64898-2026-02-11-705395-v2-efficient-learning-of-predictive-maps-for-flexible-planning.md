---
title: Efficient Learning of Predictive Maps for Flexible Planning
title_zh: 高效学习用于灵活规划的预测地图
authors: "Bazarjani, A., Piray, P."
date: 2026-06-22
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.11.705395v2.full.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 带重要性采样的继任表示用于策略无关的预测地图
tldr: 认知地图通过可重用表征支持灵活行为，但现有后继表示（SR）因策略依赖性限制了规划。本文提出SR-IS模型，结合时序差分学习与重要性采样，学习策略无关的预测地图，并能在环境变化时高效更新。实验证明SR-IS在规划任务中优于现有方法，并首次解释了人类重规划中的分级偏差，桥接了预测地图理论与规划行为。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有后继表示策略依赖性强，无法灵活支持规划，且无法解释人类重规划中的分级偏差。
method: 提出SR-IS，结合时序差分学习与重要性采样，构建策略无关的预测地图，支持环境变化后的快速更新。
result: SR-IS在规划任务中优于现有模型，并能解释人类重规划中其他模型无法解释的梯度偏差。
conclusion: SR-IS实现了策略无关的预测地图学习，为灵活规划提供了新机制，并深化了对大脑灵活决策的理解。
---

## 摘要
认知地图通过提供可重复使用的任务结构内部表征来实现灵活行为。后继表征是一种预测地图，编码预期的未来状态占用，已被提出作为大脑中计算此类地图的一种方式，但其策略依赖性严重限制了灵活规划。我们引入了一个新模型——带重要性采样的后继表征（SR-IS），它结合了时序差异学习与重要性采样来构建策略无关的预测地图。SR-IS学习环境结构而不受智能体当前决策策略的约束。当环境变化时，这些表征可以高效更新，从而实现快速的行为适应。我们表明，SR-IS在规划任务中优于现有模型，并为先前模型无法解释的人类重新规划中的分级偏差提供了更好的解释。这项工作将预测地图理论与观察到的规划行为联系起来，并为大脑中的灵活决策提供了新见解。

## Abstract
Cognitive maps enable flexible behavior by providing reusable internal representations of task structure. The successor representation, a predictive map that encodes expected future state occupancy, has been proposed as one way such maps might be computed in the brain, but its policy dependence severely limits flexible planning. We introduce a new model, the successor representation with importance sampling (SR-IS), which combines temporal-difference learning with importance sampling to construct policy-independent predictive maps. SR-IS learns the structure of the environment without being constrained by the agent's current decision policy. These representations can be efficiently updated when the environment changes, enabling rapid behavioral adaptation. We show that SR-IS outperforms existing models in planning tasks and provides a better account of the graded biases in human replanning that previous models could not explain. This work bridges theories of predictive maps with observed planning behavior and offers new insights into flexible decision making in the brain.