---
title: "ChatGEM: An Agentic Architecture Enabling Interactive Simulation of Genome-Scale Metabolic Models"
title_zh: ChatGEM：一种实现基因组规模代谢模型交互式模拟的智能体架构
authors: "Chowdhury, N., George, A., Purohit, S., Contolesi, A., Bredeweg, E. L., Czajka, J., Stratton, K. G., Gao, Y., Stephenson, M., Elmore, J. R., Scott, A., Leach, D. T., Jerger, A., Lemmon, T., Piehowski, P., Tate, K., Fulcher, J. M., Beliaev, A., Burnum-Johnson, K., Rigor, P., Bardhan, J."
date: 2026-07-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.20.739662v1.full.pdf"
tags: ["query:ar"]
score: 6.0
evidence: 用于科学模拟的自主智能体
tldr: 基因组规模代谢模型（GEM）预测细胞表型但需大量计算专业知识，限制广泛应用。为此提出ChatGEM，基于多智能体ADEPT框架、集成COBRApy与检索增强生成（RAG），支持自然语言驱动代谢模拟。基准测试表明RAG将平均性能从2.63提升至4.20，并缩短执行时间；应用酶约束ecGEM于恶臭假单胞菌，准确识别组成型菌株为琥珀酸最优底盘，被实验验证。ChatGEM使无计算背景的研究人员能通过自然语言进行复杂GEM分析，从而加速科学发现。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1533, \"height\": 790}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1733, \"height\": 1237}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1723, \"height\": 1346}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1725, \"height\": 1969}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-07-20-739662-v1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1757, \"height\": 1626}]"
motivation: 降低使用基因组规模代谢模型的门槛，让非计算专家也能通过自然语言进行交互式模拟。
method: 基于ADEPT多智能体框架，集成COBRApy和检索增强生成（RAG），通过专门智能体协调代码生成与执行。
result: 基准测试中RAG使性能从2.63提升至4.20，在酶约束ecGEM应用中准确预测琥珀酸最优菌株。
conclusion: ChatGEM民主化代谢建模，无需计算专业知识即可进行复杂分析，加速科学发现。
---

## 摘要
基因组规模代谢模型（GEM）是预测细胞表型和指导微生物菌株工程的强大工具，但由于需要计算专业知识，其广泛应用仍面临挑战。为此，我们提出ChatGEM，一个通过自然语言实现GEM交互式模拟的智能体平台。基于多智能体ADEPT框架，ChatGEM将COBRApy集成到检索增强生成（RAG）架构中，通过专门智能体协调代码生成与执行。在三个复杂度递增的任务上的基准测试表明，启用RAG的代码生成将平均总体性能分数从2.63提升至4.20，并从常规任务到复杂任务均显著缩短了执行时间。使用基于酶约束的GEM（ecGEM）对四种工程改造的恶臭假单胞菌KT2440菌株应用ChatGEM，通过琥珀酸泄漏指数识别出组成型菌株是琥珀酸过量生产的最佳底盘——这一预测在实验中得到验证。因此，ChatGEM通过使无计算专业背景的研究人员能够通过自然语言执行复杂的基于GEM的分析，从而民主化了代谢建模，加速了科学发现。

## Abstract
Genome-scale metabolic models (GEMs) are powerful tools for predicting cellular phenotypes and guiding microbial strain engineering, yet broad adoption remains challenging due to the computational expertise required. To overcome that, we present ChatGEM, an agentic platform that enables interactive GEM simulation through natural language. Built on the multi-agent ADEPT framework, ChatGEM integrates COBRApy within a retrieval-augmented generation (RAG) architecture that coordinates code generation and execution through specialized agents. Benchmarking across three tasks of increasing complexity showed that RAG-enabled code generation improved the mean overall performance score from 2.63 to 4.20 while reducing the execution time significantly starting from routine to complex tasks. Application of ChatGEM using an enzyme-constrained GEM (ecGEM) for four engineered Pseudomonas putida KT2440 strains identified the constitutive strain as the optimal chassis for succinate overproduction using a succinate leakage index - a prediction observed experimentally. Therefore, ChatGEM democratizes metabolic modeling by enabling researchers without computational expertise to perform sophisticated GEM-based analyses through natural language, and, hence, accelerating scientific discovery.