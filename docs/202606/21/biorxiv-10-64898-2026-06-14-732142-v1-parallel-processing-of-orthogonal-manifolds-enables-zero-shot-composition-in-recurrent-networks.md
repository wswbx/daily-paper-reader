---
title: Parallel processing of orthogonal manifolds enables zero-shot composition in recurrent networks
title_zh: 正交流形的并行处理使循环网络实现零样本组合
authors: "Osako, Y., Arango, A., Asabuki, T."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.14.732142v1.full.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 循环网络中零样本行为组合与RL技能组合相关
tldr: 动物能灵活组合已学行为，但计算机理未知。通过循环网络训练发现，反馈几何结构决定零样本并行组合能力：局部预测塑性规则训练的网络，反馈向量将不同任务嵌入可分离子空间，支持组合；而BPTT训练的网络则不能。该原理复现了运动皮层加性姿势几何，并泛化到高维动作基元，揭示反馈几何是学习系统结构化动态以实现未来组合复用的关键原则。
source: biorxiv
selection_source: fresh_fetch
motivation: 探索动物无需联合训练即可灵活组合已学行为的计算机制。
method: 训练循环网络使用局部预测塑性规则，分析反馈向量几何对零样本组合能力的影响。
result: 不同反馈向量将学习嵌入可分离子空间，支持并行组合；对齐向量或BPTT训练则不能。
conclusion: 反馈几何是结构化循环动态以实现未来组合复用的计算原则。
---

## 摘要
动物能够灵活地将习得的行为组合成新动作，而无需练习它们的组合，但使独立获取的计算能够并行表达的神经机制仍不清楚。本文表明，学习过程中的反馈几何结构决定了循环动态是否能够通过零样本并行组合进行重组。通过使用局部预测可塑性规则训练的循环网络，我们发现不同的反馈向量将独立学习的计算嵌入到可分离的动力学子空间中，使得新的输入组合能够共同激活这些组件，并在无需联合训练的情况下生成复合输出。相反，对齐的反馈向量以及通过时间反向传播训练的网络，虽然表现出准确的单任务性能，但无法支持并行组合，这表明任务获取和未来可重用性是学习的可分离特性。一个组合输入会引发单一的复合群体轨迹，其向反馈塑造的任务子空间的投影恢复了独立学习的组件动态。同样的原理再现了运动皮层中观察到的加性伸手-姿势几何结构，并推广到更高维度的运动基元。这些结果将反馈几何结构确定为一个计算原理，学习系统通过它来构建循环动态以便未来进行组合重用。

## Abstract
Animals flexibly combine learned behaviors into novel actions without practicing their combinations, yet the computational mechanisms that enable independently acquired computations to be expressed in parallel remain unclear. Here we show that feedback geometry during learning determines whether recurrent dynamics can be recombined through zero-shot parallel composition. Using recurrent networks trained by a local predictive plasticity rule, we found that distinct feedback vectors embed independently learned computations in separable dynamical subspaces, allowing novel input combinations to co-activate these components and generate composite outputs without joint training. In contrast, aligned feedback vectors, as well as networks trained by backpropagation through time, exhibited accurate single-task performance but failed to support parallel composition, demonstrating that task acquisition and future reusability are dissociable properties of learning. A combined input evoked a single composite population trajectory, whose projections onto feedback-shaped task subspaces recovered the independently learned component dynamics. The same principle reproduced additive reach-posture geometry observed in motor cortex and generalized to higher-dimensional movement primitives. These results identify feedback geometry as a computational principle by which learning systems structure recurrent dynamics for future compositional reuse.