---
title: "Tree-Notebook: A Context-Aware Agent with Tree Search and Entropy-Aware Data Shadow for Interactive Data Science"
title_zh: "Tree-Notebook: 具有树搜索和熵感知数据影子的上下文感知智能体用于交互式数据科学"
authors: "Junkun Qiu, Min Huang, Qinghai Miao"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.783.pdf"
tags: ["query:ar"]
score: 8.0
evidence: Tree-Notebook通过树搜索和上下文管理实现交互式数据科学自动化
tldr: LLM智能体在数据科学中面临上下文管理低效和错误传播问题。Tree-Notebook将笔记本单元建模为树节点，将问题求解形式化为POMDP，结合熵感知数据影子策略，显著提高任务成功率并减少无效操作。该框架推动了数据科学任务的自主化。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.783/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1648, \"height\": 898, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.783/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 815, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.783/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 801, \"height\": 772, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.783/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 814, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.783/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 815, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.783/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 796, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.783/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 795, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.783/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 801, \"height\": 248, \"label\": \"Table\"}]"
motivation: 现有智能体在数据科学任务中上下文管理低效且易传播错误。
method: 将Jupyter单元构建为树结构，基于POMDP和熵感知数据影子进行决策。
result: 在多个数据科学基准上提升了任务成功率并降低了错误率。
conclusion: 树结构与熵感知方法有效提升了数据科学智能体的自主性。
---

## Abstract
While LLM-based agents have emerged as a focal point for automating data science tasks, they continue to grapple with inefficient context management, "silent failures" (where code executes correctly but fails the task objectives), and error propagation inherent in sequential generation. In this paper, we propose Tree-Notebook, an agentic framework designed to mimic the iterative cognitive process of human data scientists. At its core, Tree-Notebook conceptualizes Jupyter Notebook cells as nodes within a tree structure, facilitating organized and efficient context retrieval. We formalize the task-solving process as a Partially Observable Markov Decision Process (POMDP) over a dynamic tree, utilizing an entropy-based information gain function for path evaluation to enhance adaptability in real-world environments. Furthermore, we introduce the "Data Shadow" system, which resolves silent failures by performing real-time tracking of data distributions, provenance, and semantic constraints. Experimental results demonstrate that Tree-Notebook achieves state-of-the-art (SOTA) performance on both InfiAgent-DABench and DSBench. To further evaluate robustness, we introduce an augmented version of InfiAgent-DABench to simulate complex environments, where Tree-Notebook consistently maintains its SOTA standing. Code is available at: https://github.com/QJK-BUAA/Tree-Notebook

---

## 论文详细总结（自动生成）

# 论文总结：Tree-Notebook

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：基于大语言模型的智能体在自动化数据科学任务中虽已成为焦点，但仍面临三个关键问题：
  - **“静默失败”**：代码执行无错误，但实际损害了数据（如 `df.dropna()` 静默丢弃90%数据），现有智能体依赖文本输出（stdout）无法感知底层数据分布变化。
  - **非线性探索的僵化**：真实数据科学任务需要分支假设（如比较多种缺失值填充策略），而线性框架只能走单一执行路径，一旦犯错难以回溯，且上下文窗口易被污染。
  - **现有基准的不足**：主流基准过于“干净”，难以暴露这些脆弱性；在真实场景的环境噪声（无关文件、歧义模式）下，线性智能体容易产生幻觉。
- **整体含义**：本文旨在提出一种能够模拟人类数据科学家迭代认知过程（试错、分支探索、回溯）的非线性框架，以解决上述问题，提升数据科学任务自动化的鲁棒性与效率。

## 2. 方法论：核心思想、关键技术细节
### 核心思想
- 将Jupyter Notebook单元（单元格）视为树结构中的节点，通过动态树搜索替代线性生成。
- 将问题求解形式化为一个在动态树上的**部分可观察马尔可夫决策过程（POMDP）**。
- 引入**数据影子（Data Shadow）** 实时追踪数据分布、谱系和语义约束，解决“状态不可见”问题。
- 使用**熵正则化**的双目标优化函数平衡任务效用与执行风险。

### 关键技术细节
1. **状态定义**：每个节点 `s_t = (c_t, r_t, o_t, M_t)`，其中 `c_t` 为代码，`r_t` 为执行结果，`o_t` 为数据影子（提取DataFrame元信息：维度、模式、统计摘要等），`M_t` 包含任务完成分数 `v_t` 和主观语义熵 `h_t`。
2. **优化目标**：
   `τ* = argmax Σ [v_t(s_t) - λ·h_t(s_t)]`
   - `v_t`：任务效用（基于答案正确性或流程完整性）。
   - `h_t`：语义熵（通过LLM评估器对代码效果分类为“有效/无效/破坏性”后计算Shannon熵），λ控制风险厌恶。
3. **动态树搜索**：
   - **原子扩展**：在低熵状态下，根据历史、观测和负约束集 `K^-` 生成下一个代码单元。
   - **分支突变**：当熵超过阈值 `δ` 时，进入规划模式，生成K个互斥策略意图，并分别生成子节点。
   - **同构合并**：若两个节点的数据影子相同，则合并为DAG，避免冗余计算。
   - **剪枝**：基于执行错误、效用崩溃、语义非法性剪枝。
4. **非线性时空回溯**：
   - 第一阶段：原位修正（若错误轻微）。
   - 第二阶段：回滚到父节点，利用检查点恢复环境，并将失败动作加入负约束集，重新生成新分支。

## 3. 实验设计
### 使用的数据集/场景
- **InfiAgent-DABench**：数据问答任务（257题，分Easy/Medium/Hard）。
- **DSBench**：端到端建模任务（74个Kaggle竞赛任务）。
- **InfiAgent-DABench（增强版）**：在原始数据中注入环境噪声（无关文件）和数据噪声（随机列、空白行），用于测试鲁棒性。

### Benchmark
- 每个基准均使用标准评价指标：
  - InfiAgent-DABench：**准确率**（Accuracy）。
  - DSBench：**任务成功率（Success Rate）** 和**相对性能差距（RPG）**。

### 对比方法
- ReAct、AutoGen、TaskWeaver、Data Interpreter、Jupiter、Datawise Agent（均为SOTA基线）。
- 使用多个后端模型：GPT-4o、GPT-4o-mini、Qwen2.5-72B-Instruct、Qwen2.5-14B（部分对比需考虑）。

## 4. 资源与算力
- **未明确说明**使用的GPU型号、数量或训练时长。文中仅提及使用了GPT系列API（gpt-4o-2024-08-06、gpt-4o-mini-2024-07-18）以及Qwen2.5模型。计算开销主要通过**平均token消耗**和**LLM调用次数**衡量，例如Tree-Notebook在InfiAgent-DABench上平均每次任务消耗14,977 tokens（GPT-4o），低于TaskWeaver（15,069）但高于Datawise Agent（8,557）。在DSBench上完整版本平均调用10.37次、24,873 tokens。未涉及模型训练。

## 5. 实验数量与充分性
- **实验组数**：
  - 两个主要基准测试（InfiAgent-DABench 3种模型设置、DSBench 4种设置）。
  - 增强噪声数据集上的鲁棒性对比（3种模型，含Data Interpreter和Datawise Agent）。
  - 消融实验：去除动态分支、时空回溯、数据影子三个组件，分别在基准和噪声集上测试。
  - 成本与效率分析（token消耗、调用次数对比）。
- **充分性评价**：
  - **充分**：覆盖了多个SOTA基线，不同模型规模，标准与噪声环境，各核心组件的独立贡献。
  - **客观公平**：实验设置清晰，评价指标标准化；对Jupiter等模型因模型版本不同做了备注（如Jupiter使用14B版）。
  - **略有不足**：仅在表格数据上验证，未涉及图片、文本等非结构化数据；鲁棒性测试仅针对InfiAgent-DABench，未对DSBench做类似增强。

## 6. 主要结论与发现
- Tree-Notebook在InfiAgent-DABench上达到**SOTA准确率89.49%**（GPT-4o），显著优于TaskWeaver和Datawise Agent（均为85.99%）。
- 在DSBench上，任务成功率与多数先进模型持平（98.64%），但**RPG指标最优**（GPT-4o下54.20），表明模型性能更接近金牌表现。
- 在噪声增强数据上，Tree-Notebook的准确率（80.54%）和保留率（0.9000）均远高于对比模型，验证了其强鲁棒性。
- 消融实验表明：
  - **动态分支**对复杂任务和噪声环境贡献最大（去掉后准确率从89.49%降至85.99%/73.15%）。
  - **时空回溯**防止错误传播，对长链推理至关重要。
  - **数据影子**解决了状态不可见问题，并支持同构合并降低冗余。

## 7. 优点
- **创新性**：首次将数据科学代码生成形式化为熵正则化POMDP，并将Notebook结构化为动态树，模拟人类迭代试错过程。
- **实用性**：数据影子机制无需生成额外探索代码（如`df.info()`），直接从内核提取元信息，降低冗余LLM调用。
- **鲁棒性**：通过分支、回溯、剪枝、合并，有效应对静默失败和错误传播，在噪声环境下表现突出。
- **全面性**：在标准基准和增强基准上均进行验证，消融实验设计合理，成本分析详实。

## 8. 不足与局限
- **计算开销增加**：动态树搜索、多分支探索、数据影子重复提取以及LLM评估器调用，相比线性方法（如Datawise Agent）token消耗和调用次数显著增加（特别是DSBench上完整版本调用10.37次 vs Datawise的10.19次，差距不大；但在简单任务上线性方法更轻量）。
- **依赖LLM评估器准确性**：分支触发和熵计算依赖底层LLM对语义分类的准确性，若模型能力不足可能导致无效探索。
- **数据影子仅限于表格元数据**：当前实现仅针对DataFrame类型，对图像、文本等非结构化数据或超大规模分布式数据的感知能力和性能瓶颈尚未探索。
- **实验覆盖有限**：未在更多真实世界噪声场景下验证（如DSBench未做增强测试），且仅在英语数据集上评估，跨语言泛化性未知。
- **未提及并行化或分布式扩展**：当前框架是单智能体顺序执行，对于大规模任务可能扩展性受限。

（完）
