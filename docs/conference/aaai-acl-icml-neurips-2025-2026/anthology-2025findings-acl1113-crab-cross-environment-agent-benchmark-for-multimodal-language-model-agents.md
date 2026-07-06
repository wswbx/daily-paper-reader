---
title: "CRAB: Cross-environment Agent Benchmark for Multimodal Language Model Agents"
title_zh: CRAB：多模态语言模型代理的跨环境基准
authors: "Tianqi Xu, Linyao Chen, Dai-Jie Wu, Yanjun Chen, Zecheng Zhang, Xiang Yao, Zhiqiang Xie (谢志强), Yongchao Chen, Shilong Liu, Bochen Qian, Anjie Yang, Zhaoxuan Jin, Jianbo Deng, Philip Torr, Bernard Ghanem, Guohao Li"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.1113.pdf"
tags: ["query:cli-agent"]
score: 6.0
evidence: 多模态语言模型代理的跨环境基准，可用于评估类CLI智能体
tldr: 现有智能体基准局限于单一环境且评估方法不精细。本文提出CRAB，首个跨环境智能体基准框架，包含基于图的细粒度评估方法和高效任务生成方法。框架支持多种设备并易于扩展，在多个交互环境下对多模态语言模型代理进行了系统评估，揭示了跨环境泛化的关键挑战。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1313, \"height\": 969, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 810, \"height\": 595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1630, \"height\": 981, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1615, \"height\": 1827, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1614, \"height\": 1740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1614, \"height\": 1748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1611, \"height\": 1742, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1616, \"height\": 1821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1591, \"height\": 1824, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1590, \"height\": 1737, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1593, \"height\": 1744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1570, \"height\": 950, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1572, \"height\": 1883, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1569, \"height\": 1722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1569, \"height\": 1794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1582, \"height\": 1824, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1587, \"height\": 1750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1113/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1584, \"height\": 1746, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1663, \"height\": 747, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 806, \"height\": 597, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1622, \"height\": 802, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1590, \"height\": 802, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1049, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1538, \"height\": 802, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1655, \"height\": 758, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1653, \"height\": 757, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1113/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1654, \"height\": 758, \"label\": \"Table\"}]"
motivation: 现有智能体基准局限于单一环境，缺乏细粒度通用评估方法。
method: 提出CRAB框架，包含基于图的细粒度评估和高效任务生成。
result: 在多个交互环境下评估了多模态语言模型代理，显示跨环境泛化差距。
conclusion: CRAB为评估和提升智能体的跨环境能力提供了统一基准。
---

## Abstract
The development of autonomous agents increasingly relies on Multimodal Language Models (MLMs) to perform tasks described in natural language with GUI environments, such as websites, desktop computers, or mobile phones. Existing benchmarks for MLM agents in interactive environments are limited by their focus on a single environment, lack of detailed and generalized evaluation methods, and thecomplexities of constructing tasks and evaluators. To overcome these limitations, we introduce CRAB, the first cross-environment agent benchmark framework, incorporating a graph-based fine-grained evaluation method and an efficient task generation method. Our framework supports multiple devices and can be easily extended to any environment with a Python interface. Leveraging CRAB, we develope CRAB Benchmark-v0 comprising 120 tasks in computer desktop and mobile phone environments. We evaluated 6 advanced MLMs using different single and multi-agent system configurations on this benchmark. The experimental results demonstrate that the single agent with GPT-4o achieves the best completion ratio of 38.01%.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **现有不足**：当前面向多模态语言模型（MLM）智能体的基准测试大多局限于单一环境（如仅网页、桌面或手机），缺乏跨环境的泛化评估；同时评估方法不够细粒度，通用性差；任务构造和评估器构建复杂且成本高。
- **研究动机**：为了解决上述问题，需要建立一个支持多种交互环境、提供统一细粒度评估、并能高效生成任务的基准框架，从而系统衡量MLM智能体的跨环境泛化能力。
- **整体含义**：CRAB框架是**首个跨环境智能体基准**，为衡量和提升智能体在不同GUI环境中的表现提供标准化平台，揭示了当前模型在跨环境任务上的显著差距。

### 2. 论文提出的方法论

- **核心思想**：构建一个统一的跨环境智能体评估框架，通过引入**基于图的细粒度评估方法**和**高效任务生成方法**，支持灵活扩展至任意具有Python接口的环境。
- **关键技术细节**：
  - **基于图的细粒度评估**：将任务执行过程抽象为图结构（如状态转换图），能够捕捉中间步骤和完成度，而非仅依赖最终结果。
  - **高效任务生成**：利用任务模板和环境动态组合，自动生成带有明确子目标和检查点的任务，降低人工标注成本。
- **算法流程**（文字说明）：  
  ① 定义环境接口（Python接口）  
  ② 生成任务图（节点为子状态，边为动作）  
  ③ 智能体在环境中交互，记录动作序列和状态变化  
  ④ 将执行轨迹与任务图匹配，计算细粒度完成率（如节点覆盖率、正确动作比例）  
  ⑤ 汇总得到最终评分。

- **框架扩展性**：支持台式机、手机等设备，并可通过添加新环境Python接口轻松扩展。

### 3. 实验设计

- **使用的数据集/场景**：论文构建了**CRAB Benchmark-v0**，包含**120个任务**，覆盖两个环境：**计算机桌面**和**手机环境**。
- **基准对比**：评测了6种先进多模态语言模型（MLMs），包括GPT-4o等。采用不同**单智能体系统**和**多智能体系统**配置进行对比。
- **对比方法**：未明确列出其他基线，但通过不同配置（单/多智能体、不同模型）进行了内部对比。

### 4. 资源与算力

- **文中未明确说明**：论文摘要和元数据中没有提及使用的GPU型号、数量、训练时长或推理算力。因此无法总结具体算力消耗，只能指出这一信息缺失。

### 5. 实验数量与充分性

- **实验数量**：仅包含**120个任务**、**6个模型**，以及**多种系统配置**（单/多智能体）。实验规模相对较小，但作为跨环境基准的初步建立，数量可以接受。
- **充分性与公平性**：
  - 任务数量较少，可能不足以覆盖多样化的跨环境场景。
  - 对比了不同模型和配置，但缺乏与现有单一环境基准的直接对比。
  - 未公开消融实验（如评估方法不同组件的影响），因此充分性有待加强。
  - 客观性较好，因为是标准化框架下的统一评估。

### 6. 论文的主要结论与发现

- 最佳成绩：**单智能体GPT-4o**在CRAB Benchmark-v0上的**完成率仅为38.01%**，表明当前MLM智能体在跨环境任务上表现仍然较弱。
- 跨环境泛化存在显著差距：多智能体系统并未显著优于单智能体，不同环境间的迁移能力不足。
- CRAB框架能够有效区分不同模型的跨环境能力，为后续研究提供了可靠评估基础。

### 7. 优点

- **跨环境性**：首次实现桌面端和移动端的统一基准，打破单一环境局限。
- **细粒度评估**：基于图的方法可量化部分完成程度，优于传统二元成功/失败判断。
- **高效任务生成**：降低人工构建成本，便于扩展更大规模任务。
- **扩展性好**：通过Python接口可快速适配新环境，具备通用性。

### 8. 不足与局限

- **任务规模有限**：仅120个任务，且只覆盖两个环境，缺乏复杂多样场景（如多应用程序交互、真实用户操作细节）。
- **环境代表性不足**：未包含网页浏览器、智能家居等常见GUI环境，跨环境广度受限。
- **评估维度单一**：主要衡量完成率，缺乏对效率、鲁棒性、安全性等维度的评测。
- **未提供算力成本**：不利于复现和比较实用性。
- **模型覆盖不全**：仅6个MLM，最先进但未包含最新开源模型（如LLaVA-NeXT等）或专业智能体框架。
- **无消融实验**：未验证图评估方法和任务生成方法各自贡献，科学性略显不足。

（完）
