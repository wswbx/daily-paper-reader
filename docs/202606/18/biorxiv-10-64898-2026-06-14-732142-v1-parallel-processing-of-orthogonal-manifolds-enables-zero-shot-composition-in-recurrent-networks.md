---
title: Parallel processing of orthogonal manifolds enables zero-shot composition in recurrent networks
title_zh: 正交流形的并行处理使循环网络中的零样本组合成为可能
authors: "Osako, Y., Arango, A., Asabuki, T."
date: 2026-06-17
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.14.732142v1.full.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 展示了通过正交反馈向量实现学习行为的零样本组合，与强化学习技能迁移相关
tldr: 动物能灵活组合习得行为却无需联合训练，其计算机制不明。本研究通过局部预测可塑性规则训练循环网络，发现反馈向量的几何结构决定零样本组合能力：正交反馈向量将独立计算嵌入可分离子空间，新输入组合可协同激活生成复合输出；对齐反馈向量或BPTT训练则失败。该原理复现运动皮层加性到达-姿态几何并推广至高维运动基元，揭示了反馈几何是结构化循环动力学以实现未来组合复用的关键。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究动物如何在不经联合训练的情况下，零样本并行组合独立习得行为的计算机制。
method: 使用局部预测可塑性规则训练循环网络，通过控制反馈向量对齐方式，分析子空间可分离性对零样本组合的影响。
result: 正交反馈向量将独立计算嵌入可分离子空间，实现零样本组合；对齐反馈向量及BPTT训练仅支持单任务，组合输入轨迹投影可恢复组件动力学。
conclusion: 反馈几何是学习系统结构化循环动力学以实现零样本组合复用的通用计算原理。
---

## 摘要
动物能够灵活地将习得的行为组合成新的动作，而无需练习它们的组合，然而使独立获取的计算能够并行表达的机制仍不清楚。本文表明，学习过程中的反馈几何结构决定了循环动力学是否能够通过零样本并行组合进行重组。使用由局部预测可塑性规则训练的循环网络，我们发现不同的反馈向量将独立学习的计算嵌入到可分离的动态子空间中，使得新的输入组合能够共同激活这些组件，并在无需联合训练的情况下产生复合输出。相比之下，对齐的反馈向量以及通过时间反向传播训练的网络，虽然能够准确执行单一任务，但无法支持并行组合，这表明任务获取和未来可重用性是学习中可分离的特性。组合输入引发了一个单一的复合群体轨迹，该轨迹在反馈塑造的任务子空间上的投影恢复了独立学习的组件动力学。同一原理再现了运动皮层中观察到的加性到达-姿势几何结构，并推广到更高维度的运动基元。这些结果将反馈几何结构确定为一种计算原理，学习系统通过该原理组织循环动力学以实现未来的组合重用。

## Abstract
Animals flexibly combine learned behaviors into novel actions without practicing their combinations, yet the computational mechanisms that enable independently acquired computations to be expressed in parallel remain unclear. Here we show that feedback geometry during learning determines whether recurrent dynamics can be recombined through zero-shot parallel composition. Using recurrent networks trained by a local predictive plasticity rule, we found that distinct feedback vectors embed independently learned computations in separable dynamical subspaces, allowing novel input combinations to co-activate these components and generate composite outputs without joint training. In contrast, aligned feedback vectors, as well as networks trained by backpropagation through time, exhibited accurate single-task performance but failed to support parallel composition, demonstrating that task acquisition and future reusability are dissociable properties of learning. A combined input evoked a single composite population trajectory, whose projections onto feedback-shaped task subspaces recovered the independently learned component dynamics. The same principle reproduced additive reach-posture geometry observed in motor cortex and generalized to higher-dimensional movement primitives. These results identify feedback geometry as a computational principle by which learning systems structure recurrent dynamics for future compositional reuse.