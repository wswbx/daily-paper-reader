---
title: Discovering data-driven microbial growth models with symbolic regression
title_zh: 通过符号回归发现数据驱动的微生物生长模型
authors: "Sun, T. A., Kiciatovas, D., Aapalampi, I.-K., Kuosmanen, T., Hiltunen, T., Mustonen, V."
date: 2026-04-30
pdf: "https://www.biorxiv.org/content/10.1101/2025.06.02.657040v4.full.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 符号回归应用于微生物生长建模
tldr: 本研究针对连接数学模型与微生物生长测量的挑战，提出一种基于符号回归的数据驱动方法，自动从生长数据中推断显式动态模型。发现累积种群增益比种群规模更有信息量，结合随机森林分析和理论指导，平衡数据拟合、简洁性与生物相关性后，得出最简单的线性模型和基于Monod动力学的模型，为微生物生长建模提供了新洞见。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决众多理论模型能拟合观测数据但难以连接数学模型与实测微生物生长的问题。
method: 使用符号回归直接从生长数据推断显式动态模型，并用随机森林机器学习分析特征重要性，结合理论洞见指导符号回归。
result: 发现累积种群增益比种群规模更有信息量，且平衡数据拟合、简洁性和生物相关性得出简单的线性模型和基于Monod动力学的模型。
conclusion: 本研究提供从微生物批量培养中读取生长规律的数据驱动建模方法，强调平衡数据拟合与生物可解释性。
---

## 摘要
O_LI将数学模型与经验测量的微生物生长联系起来仍然具有挑战性，因为基于不同理论方法的众多竞争模型都能拟合观测结果。因此，我们开发了一种方法，仅从微生物数据中自动提出生长模型。我们使用已知资源上生长的大肠杆菌的可用数据集验证了这种方法，并研究了在丰富培养基不同浓度下的十六种物种。C_LIO_LI符号回归这种本质可解释的方法直接从生长数据推断出显式的动力学模型。原生使用符号回归并不会偏向生物学可解释的模型，但我们发现累积种群增益比种群规模更是一个信息量更大的机器学习特征。C_LIO_LI随机森林机器学习使我们能够将这一发现与恒定速率的人均资源消耗近似联系起来。这表明常规实验中测量的生长曲线下面积（AUC）提供了关于控制微生物生长的有效资源动态的信息。最后，我们利用理论见解来指导符号回归算法，并偏好生物学可解释的模型。C_LIO_LI总体而言，我们发现数据拟合、简约性和生物学相关性之间的平衡有利于最简单的线性近似以及基于Monod动力学的模型（具有一个或两个潜在资源）。因此，我们从微生物分批培养中读取生长规律的方法为数据驱动建模提供了见解。C_LI

## Abstract
O_LIConnecting mathematical models with empirically measured microbial growth has remained challenging, as numerous competing models based on different theoretical approaches can fit observations. Therefore, we develop a method to automatically propose growth models from microbial data alone. We validate this approach using an available dataset of E. coli grown on known resources, and study sixteen species across various concentrations of a rich medium.
C_LIO_LIThe inherently interpretable approach of symbolic regression infers explicit dynamical models directly from growth data. Using symbolic regression natively, does not favour biologically interpretable models, but we find cumulative population gain to be a more informative machine learning feature than population size.
C_LIO_LIRandom Forest machine learning allows us to relate this finding to the approximation of a constant-rate per capita resource consumption. This suggests that the area under the growth curve (AUC) measured in routine experiments provides information on the effective resource dynamics governing microbial growth. Finally, we use theoretical insights to inform the symbolic regression algorithm and favour biologically interpretable models.
C_LIO_LIOverall, we found that balancing between data fit, parsimony and biological relevance favoured both the simplest, linear approximation, and models based on a Monod dynamics, with either one or two underlying resources. Therefore, our approach to read growth laws off of microbial batch cultures provides insights on data-driven modelling.
C_LI