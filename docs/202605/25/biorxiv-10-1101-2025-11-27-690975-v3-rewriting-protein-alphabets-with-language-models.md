---
title: Rewriting protein alphabets with language models
title_zh: 用语言模型重写蛋白质字母表
authors: "Pantolini, L., Studer, G., Engist, L., Pudziuvelyte, I., Pommerening, F., Waterhouse, A. M., Bienert, S., Tauriello, G., Steinegger, M., Schwede, T., Durairaj, J."
date: 2026-05-22
pdf: "https://www.biorxiv.org/content/10.1101/2025.11.27.690975v3.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 蛋白质语言模型用于生物发现的工具
tldr: 针对远程同源性检测的速度和灵敏度问题，提出利用对比学习将蛋白质语言模型嵌入转换为新型20字母字母表TEA，实现无需结构信息、兼具结构方法性能与序列搜索速度的大规模同源搜索，为生物信息学带来新工具。
source: biorxiv
selection_source: fresh_fetch
motivation: 为了提高远程同源性检测的速度和灵敏度，同时避免依赖结构信息。
method: 采用对比学习将蛋白质语言模型嵌入转化为新的20字母字母表TEA。
result: 新字母表在蛋白质同源搜索中达到与结构方法相当的性能，同时保持序列搜索的速度。
conclusion: 该方法融合了语言模型表示学习与经典序列算法，为生物发现提供了高效且强大的新工具。
---

## 摘要
快速且灵敏地检测远源同源关系对于功能注释和结构预测等任务至关重要。我们引入了一种新方法，使用对比学习将蛋白质语言模型嵌入转换为新的20字母字母表TEA，从而能够进行高效的大规模蛋白质同源性搜索。使用我们的字母表进行搜索的性能与基于结构的方法相当且互补，无需任何结构信息，同时具有序列搜索的速度。最终，我们将蛋白质语言模型表征学习中的激动人心的进展带到了过去一个世纪中开发的众多序列生物信息学算法中，为生物学发现提供了强大的新工具。

## Abstract
Detecting remote homology with speed and sensitivity is crucial for tasks like function annotation and structure prediction. We introduce a novel approach using contrastive learning to convert protein language model embeddings into a new 20-letter alphabet, TEA, enabling highly efficient large-scale protein homology searches. Searching with our alphabet performs on par with and complements structure-based methods without requiring any structural information, and with the speed of sequence search. Ultimately, we bring the exciting advances in protein language model representation learning to the plethora of sequence bioinformatics algorithms developed over the past century, offering a powerful new tool for biological discovery.