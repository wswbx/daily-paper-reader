---
title: A Multi-Agent Framework for High-Interaction Terminal Simulation
title_zh: 面向高交互终端仿真的多智能体框架
authors: "Kai Wei, Yuwen Cui, Kehan Shen, Hua Wei, Guangjing Wang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.1515.pdf"
tags: ["query:cli-agent"]
score: 9.0
evidence: 终端仿真框架用于命令生成
tldr: 本文提出MANTIS，一个多智能体终端仿真框架，用于生成真实且鲁棒的终端命令序列。MANTIS集成了基于过滤的路由模型，安全地派发命令到外部工具或LLM智能体，支持交互式命令并防御提示注入。该方法直接面向终端任务自动化，与CLI智能体需求高度契合。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1515/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1503, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1515/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 634, \"height\": 311, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1515/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1652, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1515/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 745, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1515/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 767, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1515/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 780, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1515/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 813, \"height\": 816, \"label\": \"Table\"}]"
motivation: 现有终端仿真方法缺乏灵活性，LLM方法易出错且易被注入攻击。
method: 提出MANTIS框架，结合多智能体架构和基于过滤的路由模型，安全处理命令派发。
result: 在终端仿真任务上提升了真实感、一致性和鲁棒性。
conclusion: MANTIS为终端级智能体提供了安全高效的仿真与交互框架。
---

## Abstract
Terminal simulation, framed as a terminal command-level Turing test, is a long-standing problem of symbolic language generation in dialogue and interactive systems. Prior scripted simulators lack the flexibility needed for complex, multi-turn interactions, while LLM-based approaches often misinterpret commands, break output formats, drift from system state, and remain vulnerable to prompt injection. In this work, we propose MANTIS, a terminal simulation framework that improves realism, consistency, and robustness in command-language generation. MANTIS integrates a multi-agent architecture with a filter-based routing model that safely dispatches commands to external tools or an LLM-based agent, enabling support for interactive commands while defending against prompt injection attacks. In addition, we design an agentic file system with history pruning to preserve long-term state consistency. We release three datasets: 28,045 real terminal input-output pairs, a 1,000-session multi-turn interaction dataset, and a 25,849-instance labeled classification dataset. MANTIS outperforms state-of-the-art baselines by more than 9%, achieving over 95% accuracy on multi-turn terminal simulation. The dataset and source code are available at https://github.com/kaiwei666a/MANTIS_Terminal_Simulation

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：终端仿真（Terminal Simulation）本质上是命令行层级的图灵测试，是对话系统和交互系统中长期存在的符号语言生成问题。现有仿真方法面临两大瓶颈：
  - **脚本式仿真**：依赖预定义规则，缺乏灵活性，难以处理复杂、多轮交互。
  - **LLM 直接仿真**：大语言模型在终端环境中常误解命令、破坏输出格式、偏离系统状态，且容易被提示注入攻击（prompt injection）。
- **研究动机**：终端仿真在网络安全（尤其是蜜罐系统）中至关重要——通过模拟真实终端吸引攻击者、收集威胁情报。因此需要同时保证 **输出格式真实**、**跨轮状态一致**、**对抗鲁棒**。
- **整体含义**：该工作提出 MANTIS 框架，以多智能体架构和可路由的命令处理引擎替代传统单一模型，首次在终端仿真任务上达到 95%+ 的准确率，并开源了大规模数据集。

#### 2. 方法论：核心思想、关键技术细节
- **核心思想**：采用多智能体协同架构，将终端仿真分解为**路由决策、状态管理、输出生成**三个子任务，各智能体专业化分工，并通过动态路由防御恶意输入。
- **关键技术细节**：
  - **多智能体架构**（三智能体）：
    - **仲裁智能体（Arbiter Agent）**：控制平面，负责命令路由（读/写/拒绝）、维护系统快照和各类日志（系统日志、认证日志、会话日志）。
    - **策略智能体（Strategic Agent）**：管理上下文信息，包括**状态感知的历史剪枝算法**，仅保留对当前环境有影响的交互记录，并可选地生成漏洞模拟计划。
    - **响应智能体（Response Agent）**：基于当前快照、剪枝后的历史以及可选计划，生成最终终端输出，专注于格式和状态一致性。
  - **动态路由模型**：基于 encoder（如 ModernBERT）的命令三分类器，将输入分为`Read`（只读，直接工具执行）、`Write`（改状态，交给 LLM 仿真）、`Rejection`（非法/注入，返回标准 shell 错误），确保安全。
  - **Agentic 文件系统**：模仿 Unix “一切皆文件”理念，统一管理系统日志、认证日志、会话日志，并引入 Docker 沙箱隔离攻击者上传的文件。
  - **历史剪枝算法**（Algorithm 2）：通过优先级向量 `U = (U_dup, U_std, U_stale)` 逐条评估：
    - `U_dup`：冗余（相同命令出现次数），越高越优先删除；
    - `U_std`：状态改变等级（0=关键，1=敏感配置，2=文件修改，3=无变化）；
    - `U_stale`：时效性（按轮次递增）。
    维护剪枝历史窗口大小 `K`（计算为 50 条交互），保留高信息量、低重复、新近的交互。
- **算法流程**（Algorithm 1）：接收命令 → 路由决策 → 若拒绝返回错误；若只读则直接工具执行；若写则并行执行快照更新、历史剪枝、响应生成，最终输出和轨迹记录。

#### 3. 实验设计
- **数据集构建**：
  - **Response Dataset**：28,045 条来自 Kali Linux 的真实命令-输出对，用于监督微调响应模型。
  - **Multi-turn Dataset**：1,000 个多轮会话（3~20 轮），覆盖导航、文件操作、配置修改等行为。
  - **Routing Dataset**：25,849 条指令（读占 79.14%、写 11.71%、拒绝 9.13%），含人工标注的注入样本。
  - 额外 20 个长会话（50~100 轮，共 1,403 条命令）用于测试剪枝效果。
- **Benchmarks**：与三个前沿 LLM 蜜罐系统对比：ShellLM、HoneyLLM、HoneyGPT（均重新实现为 GPT-4o 版本）。
- **评价指标**：
  - **CAW**（正常命令准确率）、**ROB**（语法错误鲁棒性）、**PI-RES**（注入攻击抵抗）、**CTX**（多轮一致性）。
  - 自动评估：精确字符串匹配（排除时间戳、PID 等非确定性字段）。
  - 用户研究：20 名有经验的 Linux 用户，对交互性、延迟、一致性、格式、鲁棒性进行 1~5 打分。

#### 4. 资源与算力
- **明确说明的数量**：
  - 响应模型微调：**单块 NVIDIA RTX 4090 GPU**，使用 LoRA 方法，训练 3 个 epoch，AdamW 优化器，学习率 5e-5，梯度累积步数 8，批次大小 2。
  - 路由模型微调：**单块 NVIDIA RTX 5090 GPU**，训练 4 个 epoch，学习率 3e-5，批次未明但另有说明。
  - 用户研究部署：Ubuntu 服务器 + **NVIDIA RTX 5090 GPU**。
- **未说明**：具体训练耗时（小时数）未提及；也不清楚是否使用了多卡并行等其他 GPU。

#### 5. 实验数量与充分性
- **实验数量**：
  - **响应模型基准测试**（表 1）：5 个商用 API（Claude-4、DeepSeek-R1-0528、Gemini-2.5-Pro、GPT-OSS-120B、Qwen3-Coder）在 Multi-turn Dataset 上的对比。
  - **系统整体对比**（图 2）：在 4 个测试集（CAW=200, ROB=500, PI-RES=570, CTX=1,000）上对比 3 个基线，并统计准确率。
  - **路由模型消融**（表 3）：6 种不同的 encoder（DistilBERT、RoBERTa、DeBERTa、ModernBERT、Electra、ALBERT）在 Routing Dataset 上的准确率和 Macro F1。
  - **历史剪枝评价**（表 4）：20 个长会话的完整历史 vs 剪枝后的一致性、延迟、Token 消耗，并额外用 GPT-5.2 验证。
  - **响应模型消融**（表 5）：10 种基础/微调模型在 200 条命令上的准确率、响应时间和 Token 数。
  - **用户研究**（表 2）：20 名参与者的 5 维度打分。
- **充分性评价**：实验覆盖了组件级消融、鲁棒性测试、用户真实体验等维度，对比基线包括最先进方法，评价指标全面（准确率、延迟、Token、用户评分），且使用统计指标（P50/P95 延迟）展示方差。但测试集规模较小（CAW 仅 200 条），多轮会话仅 1,000 轮（细粒度变化可能不足），且未见跨平台或跨 shell 泛化实验。

#### 6. 主要结论与发现
- MANTIS 在所有评价维度上**明显优于**所有基线，多轮会话准确率达 95.36%（高于 HoneyGPT 的 86.16%）。语法错误处理 97.53% vs 89.26%。
- 历史剪枝在保持/提升一致性（96.07% vs 92.01%）同时，节省约 18% Token，降低延迟。
- 路由模型最佳候选 ModernBERT-base 达到 98.64% 准确率、Macro F1 0.976。
- 用户评分中“格式”得分最高（4.80/5），说明输出格式真实性表现突出；整体交互性与一致性均超过 4.6。
- 商用 API 的准确率普遍在 90% 以下，LLM 直接仿真仍不可靠。

#### 7. 优点
- **新颖的多智能体分工设计**：仲裁、策略、响应三智能体各司其职，既保证了专业分工又兼顾协作，且通过路由模型实现安全性。
- **状态感知的历史剪枝**：提出基于优先级向量的确定性剪枝，透明可解释，同时显著降低 Token 开销，适合长对话场景。
- **高鲁棒性**：对语法错误和提示注入的防御能力强（PI-RES 准确率远超基线），适合蜜罐等对抗环境。
- **开源大规模数据集**：共计约 55k 指令/对话对，填补了终端仿真领域的数据空白，有助于社区复现和进一步研究。
- **实际部署验证**：用户研究采用真实外部连接和多样化探索任务，生态效度高。

#### 8. 不足与局限
- **环境泛化性有限**：数据集基于固定 Kali Linux 环境和固定工作区布局，未验证其他系统（如 Ubuntu、Windows WSL）或不同 shell（如 zsh、fish）的表现。
- **历史剪枝的覆盖缺陷**：规则驱动的剪枝可能遗漏隐式依赖（如管道命令的副作用、环境变量间接影响），虽然可解释，但可能牺牲极端情况下的状态一致性。
- **成本-延迟-准确率权衡**：强 backbone（如 Qwen3-8B（FT））获得更高准确率（85%）但延迟显著上升；而轻量模型（如 Llama3.2-3B）匹配准确率但鲁棒性可能不足。文中未探讨自适应模型选择或混合精度优化等缓解策略。
- **实验规模偏小**：多轮测试仅 1,000 轮，用户研究仅 20 人，且被试均为研究生（可能偏向技术背景），需更大规模、更多样化用户群体验证。
- **未报告关键算力消耗细节**：如训练总时间、能效数据，不利于可复现性评估。

（完）
