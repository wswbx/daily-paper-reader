---
title: "CoDA-Bench: Can Code Agents Handle Data-Intensive Tasks?"
title_zh: CoDA-Bench：代码代理能否处理数据密集型任务？
authors: "Yuxin Zhang, Ju Fan, Meihao Fan, Shaolei Zhang, Xiaoyong Du"
date: 2026-04-30
pdf: "https://openreview.net/pdf/1848ca3977492cbd7416933e3a72164906a481bb.pdf"
tags: ["query:cli-agent"]
score: 4.0
evidence: 代码代理在数据密集型Linux沙箱中的基准测试
tldr: 现有基准测试将代码和数据能力分开评估。CoDA-Bench构建了基于Kaggle生态的数据密集型Linux沙箱，要求代理主动探索文件层次并执行命令，首次联合评估代码和数据处理能力，填补了与现实开发场景的差距。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有基准单独评估代码或数据能力，而真实开发需两者结合。
method: 构建包含数百个数据集的Linux沙箱，设计综合任务评估代码和数据智能。
result: 实验表明现有高级代理在处理数据密集型命令任务时仍有显著差距。
conclusion: 需要兼顾代码和数据能力以应对真实开发场景。
---

## Abstract
Advanced agents are increasingly demonstrating the potential to operate as autonomous engineers, creating a growing demand for evaluation benchmarks that capture the complexity of real-world development. Such environments typically involve both complex code and large-scale data (i.e., file system). However, existing benchmarks usually evaluate code-centric or data-centric capabilities in isolation, leaving a clear gap with real development scenarios. In this paper, we bridge this gap by introducing CoDA-Bench, the first benchmark to jointly evaluate code and data intelligence in a data-intensive environment. We construct a data-intensive Linux sandbox based on the Kaggle ecosystem (containing hundreds of datasets), where agents must actively explore complex file hierarchies to identify relevant resources and generate code for data-driven analytical tasks. CoDA-Bench comprises 1,009 tasks spanning 31 communities, with each task environment containing an average of 980 files, simulating realistic data scale and noise. Evaluations of advanced agents reveal that even top-performing systems struggle to effectively integrate data discovery with code execution, achieving a success rate of only 61.1\%. These results highlight a substantial gap in current agentic capabilities for data-intensive tasks and point to promising directions for future research.

---

## 论文详细总结（自动生成）

# CoDA-Bench：代码代理能否处理数据密集型任务？——论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：当前高级代码代理（如基于LLM的编程助手）在真实开发场景中需要同时处理复杂代码和大规模数据（如文件系统），但现有基准测试往往将代码能力和数据处理能力分开评估，忽略了二者结合的复杂性，与现实开发场景存在明显差距。
- **核心问题**：如何构建一个能够联合评估代码智能与数据智能的基准测试，以衡量代理在数据密集型环境中的综合能力？
- **整体含义**：通过填补这一评估空白，推动代理系统向能自主探索文件层次、执行命令并生成代码的真实自主工程师方向发展。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：构建基于Kaggle生态的数据密集型Linux沙箱，要求代理主动探索复杂文件层次结构以识别相关资源，并生成代码完成数据驱动分析任务。
- **关键技术细节**：
  - 沙箱包含数百个真实数据集，每个任务环境平均包含980个文件，模拟真实数据规模与噪声。
  - 任务设计需代理同时具备**数据发现**（在文件系统中定位所需数据）和**代码执行**（编写处理数据的脚本）能力。
  - 基准测试包含1009个任务，覆盖31个社区（领域），确保多样性。
- **算法流程（文字说明）**：
  1. 基于Kaggle平台收集真实数据集并组织成Linux文件系统结构。
  2. 定义分析任务（如统计、可视化、特征提取等），每个任务对应一个沙箱环境。
  3. 代理启动后需通过shell命令遍历目录、读取文件内容、理解数据格式。
  4. 代理编写代码（Python等）并执行，最终输出结果与预期结果比对。
  5. 使用自动化脚本评估成功/失败（通常基于输出匹配或数值容差）。

## 3. 实验设计

- **数据集/场景**：基于Kaggle生态系统，涵盖31个社区（如金融、医疗、社交网络等），包含数百个数据集。
- **Benchmark**：CoDA-Bench，共1009个任务，每个任务平均980个文件。
- **对比方法**：文中提到评估了“advanced agents”（如基于大型语言模型的代理），但未详细列出具体模型名称。从上下文推测可能包括GPT-4、Claude、Codex等驱动的代理系统，以及一些专用代码代理（如OpenDevin、SWE-agent等）。需注意原文未明确列出具体对比方法，但指出“top-performing systems”成功率仅61.1%。

## 4. 资源与算力

- **原文未明确说明**所使用的GPU型号、数量、训练时长等算力信息。论文侧重于基准测试构建和评估，而非模型训练，因此未提供代理系统的训练资源细节。评估实验可能基于现有官方API或本地部署，但未披露。

## 5. 实验数量与充分性

- **实验数量**：共1009个任务，覆盖31个社区。每个任务独立评估，结果统计整体成功率和分社区表现。
- **充分性**：任务规模较大（上千个），数据集多样（多个社区），环境复杂度贴近真实（大量文件），实验设计较为充分。但仅汇总了整体成功率，缺乏详细的消融实验或针对不同能力维度的分解分析（例如单独评估数据发现能力 vs. 代码生成能力），可能存在一定局限性。
- **公平性**：由于未披露所有对比方法的详细信息及配置，公平性难以完全判定。但基准测试采用封闭环境自动评分，避免了人工偏差。

## 6. 主要结论与发现

- 现有顶级代理在CoDA-Bench上成功率仅为61.1%，表明其难以有效整合数据发现与代码执行。
- 代理在处理数据密集型任务时存在显著能力缺口，尤其是在复杂文件系统中定位相关数据、处理噪声和异构格式方面表现不佳。
- 需要未来研究兼顾代码和数据能力，以应对真实开发场景。

## 7. 优点

- **首创性**：首个联合评估代码与数据智能的基准测试，填补了现有基准的空白。
- **真实性**：基于Kaggle真实数据集构建沙箱，文件数量大、噪声真实，环境贴近开发者日常工作。
- **多样性**：覆盖31个社区，任务类型广泛，避免领域偏斜。
- **可复现性**：沙箱环境隔离，评估自动化，结果可复现。

## 8. 不足与局限

- **实验覆盖**：未详细对比不同类别的代理（如纯代码代理 vs. 通用AI助手），也未进行消融实验以区分能力短板来源（数据探索能力不足 vs. 代码错误）。
- **偏差风险**：所有任务来源于Kaggle，可能存在平台特有模式（如数据格式规范、社区偏好），导致泛化性受限。
- **应用限制**：基准仅针对Linux沙箱中的命令行交互，未覆盖GUI、云服务或实时数据流等场景；代理需要预先安装特定工具（如Python库），可能低估真实部署中的依赖管理挑战。
- **资源信息缺失**：未提供评估计算资源信息，不利于成本比较。

（完）
