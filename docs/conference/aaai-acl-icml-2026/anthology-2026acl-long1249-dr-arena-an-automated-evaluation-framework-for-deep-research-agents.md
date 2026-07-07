---
title: "DR-Arena: an Automated Evaluation Framework for Deep Research Agents"
title_zh: DR-Arena：深度研究代理的自动化评估框架
authors: "Yiwen Gao, Ruochen Zhao, Yang Deng, Wenxuan Zhang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.1249.pdf"
tags: ["query:ar"]
score: 9.0
evidence: 深度研究代理的自动化评估框架
tldr: 针对深度研究代理的评估瓶颈，DR-Arena提出了全自动化动态评估框架：通过实时构建网络信息树和自动出题器，生成与当前世界状态同步的结构化任务，从而克服静态基准的时效性低和污染问题。实验表明该框架能有效区分不同代理的性能，为深度研究代理的可靠性评估提供了新标准。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1249/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1534, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1249/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1555, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1249/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 717, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1249/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 485, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1249/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 759, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1249/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 789, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1249/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1437, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1249/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1622, \"height\": 649, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 817, \"height\": 465, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1647, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 801, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 801, \"height\": 394, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 794, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 793, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 792, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 802, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 767, \"height\": 1892, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 635, \"height\": 932, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1665, \"height\": 1270, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1249/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 782, \"height\": 838, \"label\": \"Table\"}]"
motivation: 现有深度研究代理评估依赖静态数据集，存在任务泛化性差、时间错位和数据污染问题。
method: 提出DR-Arena框架，利用实时信息树构建动态评估任务，并采用自动出题器生成结构化考题。
result: 框架能够动态生成与当前世界同步的评估任务，有效评估代理的自主调查和信息综合能力。
conclusion: DR-Arena为深度研究代理提供了更真实、更全面的自动化评估工具。
---

## Abstract
As Large Language Models (LLMs) increasingly operate as Deep Research (DR) Agents capable of autonomous investigation and information synthesis, reliable evaluation of their task performance has become a critical bottleneck. Current benchmarks predominantly rely on static datasets, which suffer from several limitations: limited task generality, temporal misalignment, and data contamination. To address these, we introduce DR-Arena, a fully automated evaluation framework that pushes DR agents to their capability limits through dynamic investigation. DR-Arena constructs real-time Information Trees from fresh web trends to ensure the evaluation rubric is synchronized with the live world state, and employs an automated Examiner to generate structured tasks testing two orthogonal capabilities: Deep reasoning and Wide coverage. DR-Arena further adopts Adaptive Evolvement Loop, a state-machine controller that dynamically escalates task complexity based on real-time performance, demanding deeper deduction or wider aggregation until a decisive capability boundary emerges. Experiments with six advanced DR agents demonstrate that DR-Arena achieves a Spearman correlation of 0.94 with the LMSYS Search Arena leaderboard. This represents state-of-the-art alignment with human preferences without any manual efforts, validating DR-Arena as a reliable alternative for costly human adjudication.

---

## 论文详细总结（自动生成）

# DR-Arena：深度研究代理的自动化评估框架——论文总结

## 1. 核心问题与整体含义

**研究动机与背景**  
随着大语言模型（LLM）作为深度研究（Deep Research, DR）代理的广泛应用，它们能够自主进行多步调查、跨源证据检索与综合，生成结构化的引证报告。然而，现有评估基准主要依赖静态数据集，存在三个根本局限：
- **任务泛化性差**：数据集受限于预定义调查模式，无法反映真实世界的多样化研究场景。
- **时间错位**：静态基准随事实演化而过时，评价结果与实际信息状态脱节。
- **数据污染**：被反复使用的数据可能出现在模型训练语料中，导致参数记忆而非真正推理。

**整体含义**  
为了可靠评估DR代理在动态、开放环境中的能力，本文提出了**DR-Arena**——一个全自动的、动态的评估框架，通过实时构建信息树、自动生成结构化任务，并采用自适应演化循环，推动代理达到能力极限。实验表明，DR-Arena能有效区分不同代理的性能，并与人类偏好高度对齐，可作为昂贵人工评估的可扩展替代方案。

## 2. 方法论

**核心思想**  
DR-Arena通过一个统一的LLM代理（称为“Examiner”），在闭环流程中模拟竞争性竞技场：Examiner负责出题、评分并动态调整难度，以同时测试代理的**深度推理（Depth）** 和**广域覆盖（Width）** 两种正交能力。

**关键技术细节**

1. **动态信息树构建**  
   - 从Google Trends选取种子主题，生成搜索查询，从开放网络抓取高质量网页作为根节点。
   - 递归构建有向图 \( G = (V, E) \)，其中节点为真实网页含全文本与元数据，边为超链接，并通过锚文本分析标记语义关系（如“变种”“过程”）。
   - 支持两种扩展：**深度扩展**（沿某分支递归爬取至指定深度d，用于多跳推理）和**宽度扩展**（捕获同父节点的兄弟节点，用于聚合比较）。

2. **自动任务生成**  
   - 基于信息树，Examiner随机选择一个目标节点，若节点深度或宽度不足则自动触发爬虫扩展。
   - 生成一个同时要求**逻辑推理**（隐藏实体名，通过推理链定位）和**信息聚合**（跨多个兄弟节点比较属性）的挑战性问题。
   - 同步生成事实正确的评分细则清单，包括深度清单（验证逻辑身份）和宽度清单（评估数据完整性），并严格禁止在问题中暴露文件名或网站标题（去上下文化策略）。

3. **自适应演化循环**  
   - 采用两级评估协议：**硬约束**（按清单核对，关键错误立即罚分）和**软约束**（评估呈现质量、信息密度、帮助性等）。
   - 判决结果分为：MUCH BETTER（+2）、BETTER（+1）、TIE（高质量/低质量）。对失败方进行失效类型诊断（深度失效、宽度失效、两者皆有、无硬性失败）。
   - 根据判决和诊断结果，通过状态转移矩阵动态调整任务复杂度（D↑1、W↑1或两者同时增加），直至出现明确的能力边界（如累计分差超过阈值或达成“MUCH BETTER”判决），或达到最大轮数。

**算法流程（文字说明）**  
- 初始化：从信息树随机采样起始路径，宽度约束W=2。
- 循环直至分差大于阈值或达最大轮数：
  1. 环境检查：若当前层兄弟节点数<W，则触发宽度扩展。
  2. 生成任务：提取祖先节点（深度链）和兄弟节点（宽度集），Examiner生成问题及评分清单。
  3. 代理执行与判决：两个代理分别回答，Examiner按清单给出判决和失效类型。
  4. 状态转移：若为高质量平局，则压力测试（D↑1, W↑1）；若为低质量平局，则回溯至父节点；若分出胜负，则根据失败类型针对性增加深度或宽度。

## 3. 实验设计

**使用的数据集/场景**  
- **信息树来源**：从Google Trends采样30个主题，覆盖游戏、法律、健康、科技、音乐等多样领域，主要源域包括Wikipedia、GameFAQs、Cleveland Clinic等权威网站。
- **评估代理**：选择LMSYS Search Arena榜单上的6个代表模型：GPT-5.1-Search、Gemini-2.5-Pro-Grounding、o3-Search、Grok-4-Search、Perplexity-Sonar-Pro-High、Claude-Opus-4.1-Search。

**Benchmark**  
- 参考**LMSYS Search Arena**（基于大规模盲人机比对）作为人类偏好的黄金标准。
- 对比的静态/动态基准包括：BrowseComp、DeepResearch Bench、LiveNewsBench、LiveSearchBench、LiveResearchBench、Deep Research Bench（FutureSearch）。

**对比方法**  
- 实验采用瑞士制锦标赛，每对代理在相同的30棵信息树上进行多轮对决，使用Elo评分（基于Bradley-Terry模型）动态更新排名。

## 4. 资源与算力

论文未明确说明训练或推理所用的具体GPU型号、数量或运行时长。仅提到选择Gemini-3-Pro作为固定Examiner，因为它在LMSYS Text Arena上表现最佳。其他运行成本未定量报告。

## 5. 实验数量与充分性

**实验组数**  
- 主要排名实验：6个模型，瑞士制4轮配对，共30场对决（每对模型在多棵树上比较），总计789个交互轮次。
- 消融实验：对比带/不带信息树、带/不带评分清单、带/不带演化循环共4种配置。
- 人类验证实验：2位专家对50个任务生成样本进行盲选偏好；对30个完整对决日志（共64轮）进行五维审计。
- 交叉Examiner验证：用GPT-5.2-Chat和Claude-Opus-4.6替换原Examiner重新判决50个采样对决。

**充分性判断**  
- 实验覆盖了多种主流模型家族，且使用实时网络数据避免了时间污染。
- 消融实验系统验证了三个核心组件（信息树结构、清单评分、自适应循环）的贡献。
- 人类研究提供了高一致性（Cohen's Kappa≥0.88），交叉Examiner实验证明了方法不依赖特定判断模型。
- 结论：实验设计客观、公平，充分验证了框架的有效性和鲁棒性。

## 6. 主要结论与发现

- DR-Arena取得了与LMSYS Search Arena **0.94 Spearman相关系数**的排名一致性，远超所有对比基准（甚至部分基线出现负相关）。
- 自适应演化循环能高效聚焦计算资源：技能差距小的模型对需要更多轮次（最高约3轮），差距大的对快速收敛（低于2轮），验证了“压力测试”机制的有效性。
- 失效类型分析揭示了各模型的能力剖面：GPT-5.1-Search展现最均衡的低错误率；o3-Search深度推理强但广度覆盖弱；PPL-Sonar-Pro和Grok-4则相反，检索能力强但逻辑推理薄弱。
- 人类审计表明自动出题（90.6%结构有效）、评分清单（89.1%事实正确）和判决（Cohen's κ=0.91）均高度可靠。

## 7. 优点

- **全自动化**：无需人工标注，通过实时信息树同步评估环境，消除时间错位和数据污染。
- **动态自适应**：多轮演化循环能主动探测代理的能力边界，并在技能差距小的场景中增加难度以揭示细微差异。
- **可解释性**：通过失效类型诊断（深度/宽度/两者），提供针对性的模型能力肖像，有助于指导模型改进。
- **与人类偏好高度对齐**：Spearman 0.94优于所有静态基准，且交叉Examiner验证显示方法稳健。
- **计算高效**：瑞士锦标赛设计将复杂度从\(O(n^2)\)降至\(O(n\log n)\)，自适应循环在确保区分度的同时控制轮数。

## 8. 不足与局限

- **单一Examiner依赖**：虽验证了交叉一致性，但主流水线仍使用单一判断模型，无法完全排除判断偏见。
- **参数知识冲突风险**：当生成的地面真相清单与Examiner的内部知识不一致时，Examiner可能错误地覆盖清单（尽管在某些情况下能正确纠正）。
- **计算可复现性**：基于实时网络爬取和商业搜索引擎，由于排名、地理封锁、页面可用性变化，精确复现可能困难。
- **对创造性综合不敏感**：严格基于事实清单的评分可能低估偏离逻辑路径但有价值的横向思维或创造性综合。
- **受限于信息树拓扑**：任务生成高度依赖初始爬取质量和树结构，若种子页面选择不当可能导致任务偏差。

（完）
