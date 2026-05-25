---
title: "sxLaep: a Lightweight and Accurate Enzyme Predictorfor High-throughput Mining of Metagenomic Sequences"
title_zh: sxLaep：一种轻量且精确的酶预测器，用于宏基因组序列的高通量挖掘
authors: "Duan, H., Han, X., Mo, Y., Ren, B., Xia, L. C."
date: 2026-05-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.06.723393v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 7.0
evidence: 用于宏基因组挖掘的轻量级酶预测器
tldr: "本文提出sxLaep，一种轻量级且准确的酶预测工具，用于高通量挖掘宏基因组序列。它使用轻量级理化特征进行酶预筛选，速度比Diamond快22.9倍，内存减少54.4%，准确率达99.34%，并能检测到比对方法遗漏的远程同源酶，成功应用于海洋宏基因组酶挖掘。"
source: biorxiv
selection_source: fresh_fetch
motivation: 宏基因组测序产生海量数据，现有深度学习或比对工具计算资源消耗大，急需轻量快速的预筛选工具。
method: 提出sxLaep框架，采用轻量级理化特征进行酶预测。
result: "外部验证集上，预测速度0.002秒/序列，比Diamond快22.9倍，峰值内存372.16MB，减少54.4%，准确率99.34%，远程同源检测召回率最高。"
conclusion: sxLaep已成功应用于海洋宏基因组酶挖掘工作流，证明其在大规模宏基因组序列高通量发现中的实用性。
---

## 摘要
动机：宏基因组测序生成PB级序列数据集，给基于深度学习和对齐的酶注释工具带来压力。在资源密集的功能预测之前，需要一种轻量、快速且精确的过滤工具来筛选和识别酶序列。

结果：我们提出了sxLaep（轻量且精确的酶预测器），一种利用轻量理化特征进行酶预筛选的资源高效框架。在外部验证集上，sxLaep仅需0.002秒/序列即可完成预测，比Diamond（0.0457秒/序列）快22.9倍。其峰值内存使用为372.16 MB，相对于Diamond（815.64 MB）减少了54.4%的内存。sxLaep实现了99.34%的准确率，并在远程同源性检测中获得了最高召回率，包括基于对齐方法遗漏的酶候选。我们进一步成功将sxLaep应用于海洋宏基因组酶挖掘流程，展示了其从大规模宏基因组序列中进行高通量发现的实用性。

可用性与实现：sxLaep以Python包形式提供，位于https://pypi.org/project/sxlaep，并作为开源软件仓库维护于https://github.com/labxscut/sxLaep。GitHub仓库中提供了详细的安装、使用和Docker部署说明，以支持可重复的酶预测和模型执行。

联系：lcxia@scut.edu.cn

## Abstract
MotivationMetagenomic sequencing generates petabyte-scale sequence datasets that strain both deep learning and alignment based enzyme annotation tools. A lightweight rapid and accurate filter tool is needed to filter and identify enzymatic sequences prior to resource-intensive functional prediction.

ResultsWe present sxLaep (Lightweight and Accurate Enzyme Predictor), a resource-efficient framework using lightweight physicochemical features for enzyme pre-screening. On the external validation set, sxLaep completed prediction in only 0.002 s/sequence, which is 22.9-fold faster than Diamond (0.0457 s/sequence). It used 372.16 MB peak memory, corresponding to a 54.4% memory reduction relative to Diamond (815.64 MB). sxLaep achieved an accuracy of 99.34% and the highest recall in remote homology detection, including enzyme candidates missed by alignment-based methods. We further successfully applied sxLaep to a marine metagenomic enzyme-mining workflow, demonstrating its utility for high-throughput discovery from large-scale metagenomic sequences.

Availability and ImplementationsxLaep is available as a Python package at https://pypi.org/project/sxlaep and is maintained as an open-source software repository at https://github.com/labxscut/sxLaep. Detailed installation, usage, and Docker deployment instructions are provided in the GitHub repository to support reproducible enzyme prediction and model execution.

Contactlcxia@scut.edu.cn