---
title: The recount3 Python package for programmatic access to uniformly processed RNA-seq data
title_zh: recount3 Python包：用于统一处理RNA-seq数据的程序化访问
authors: "Alsalihi, A., Flight, R. M., Moseley, H. N. B."
date: 2026-06-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.17.732943v1.full.pdf"
tags: ["query:cli-agent"]
score: 6.0
evidence: 提供命令行接口用于数据自动检索
tldr: recount3资源提供了大量统一处理的RNA-seq数据，此前主要支持R/Bioconductor生态，Python用户难以直接利用。为此我们开发了recount3 Python包，提供API和命令行接口，实现数据的发现、下载和物化。该包自动解析URL、管理磁盘缓存，并输出Pandas DataFrame等分析就绪结构。这大大降低了在Python计算流程中大规模利用RNA-seq数据的门槛，促进了公共转录组数据与现代机器学习生态的融合。
source: biorxiv
selection_source: fresh_fetch
motivation: Python在生物信息学和机器学习领域日益重要，但recount3资源此前仅支持R/Bioconductor，需提供原生Python工具。
method: 开发了recount3 Python包，提供API和CLI，支持URL解析、磁盘缓存及自动解析数据为Pandas DataFrame和BiocPy对象。
result: 实现了从数据发现、下载到分析就绪数据结构的完整流程，使Python用户能高效获取统一处理的RNA-seq数据。
conclusion: 该包显著降低了在Python管道中大规模利用转录组数据的门槛，促进了公共测序数据与现代机器学习的融合。
---

## 摘要
recount3在线资源提供了来自序列读取档案等主要测序存储库的数十万个人类和小鼠统一处理的RNA-seq样本。虽然传统上这些数据集的访问主要集中在R/Bioconductor生态系统中，但Python在生物信息学和机器学习中的日益突出地位要求为Python用户提供原生的高效工具。因此，我们推出了recount3 Python包，它提供了强大的应用程序编程接口（API）和命令行界面（CLI），用于发现、下载和实现recount3资源。该软件协调统一资源定位符（URL）解析、持久化磁盘缓存，并自动将数据解析为可分析的数据结构，包括Pandas DataFrames和BiocPy RangedSummarizedExperiment对象。recount3 Python包极大地降低了在基于Python的计算管线中大规模利用RNA-seq数据的入门门槛，弥合了大规模公共转录组数据与现代机器学习生态系统之间的鸿沟。

## Abstract
The recount3 online resource provides tens of thousands of uniformly processed RNA-seq samples across human and mouse from major sequencing repositories like the Sequence Read Archive. While access to these datasets has traditionally been centered in the R/Bioconductor ecosystem, the growing prominence of Python in bioinformatics and machine learning necessitates native, efficient tooling for Python users. Therefore, we present the recount3 Python package with robust application programming interface (API) and command-line interface (CLI) for discovering, downloading, and materializing recount3 resources. The software orchestrates uniform resource locator (URL) resolution, persistent on-disk caching, and the automatic parsing of data into analysis-ready data structures, including Pandas DataFrames and BiocPy RangedSummarizedExperiment objects. The recount3 Python package drastically lowers the barrier to entry for large-scale utilization of RNA-seq data in Python-based computational pipelines, bridging the gap between massive public transcriptomic data and modern machine learning ecosystems.