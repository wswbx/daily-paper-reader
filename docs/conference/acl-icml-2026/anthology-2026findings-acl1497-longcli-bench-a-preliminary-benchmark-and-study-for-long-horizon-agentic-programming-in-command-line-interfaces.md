---
title: "LongCLI-Bench: A Preliminary Benchmark and Study for Long-horizon Agentic Programming in Command-Line Interfaces"
title_zh: LongCLI-Bench：命令行界面长程代理编程的初步基准与研究
authors: "Yukang Feng, Jianwen Sun, Zelai Yang, Jiaxin Ai, Chuanhao Li, Zizhen Li, Fanrui Zhang, Kang He, Rui Ma, Jifan Lin, Jie Sun, Yang Xiao, Sizhuo Zhou, Wenxiao Wu, Yiming Liu, Pengfei Liu, Shenglin Zhang, Kaipeng Zhang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1497.pdf"
tags: ["query:cli-agent"]
score: 10.0
evidence: 直接评估CLI代理的长程编程能力
tldr: 本文针对现有CLI代理评测在任务时长、数据污染和细粒度评估方面的不足，提出了LongCLI-Bench基准，包含20个来源于真实作业和工作流的长时间序列工程任务，覆盖四个领域。该基准通过精细的评估指标和防污染设计，能够更有效地衡量代理的长程规划与执行能力，为CLI代理研究提供了标准化评测平台。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1497/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1648, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1497/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 783, \"height\": 177, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1497/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 763, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1497/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1635, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1497/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1627, \"height\": 330, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1497/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 767, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1497/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 797, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1497/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1620, \"height\": 472, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1497/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 796, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1497/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 794, \"height\": 430, \"label\": \"Table\"}]"
motivation: 现有CLI代理基准任务短、存在数据污染且评估粒度粗。
method: 构建20个长程、真实的CLI任务，覆盖多个领域，并设计细粒度评估指标。
result: 在多个先进代理模型上评测，揭示了长程任务中的关键挑战。
conclusion: 为CLI代理长程能力评估提供了可靠基准。
---

## Abstract
Recent advances in AI-assisted programming have empowered agents to execute complex workflows via command-line interfaces, however, existing benchmarks are limited by short task horizons, data contamination from GitHub scraping, and a lack of fine-grained evaluation metrics, fail to rigorously evaluate the long-horizon planning and execution capabilities essential for realistic software engineering. To address these gaps, we introduce LongCLI-Bench , a comprehensive benchmark designed to evaluate agentic capabilities across long-horizon , realistic, sequential engineering tasks. We curated 20 high-quality, long-horizon tasks from over 1,000 computer science assignments and real-world workflows, covering four engineering categories: from scratch, feature addition, bug fixing, and refactoring. LongCLI-Bench employs a dual-set testing protocol, which measures requirement fulfillment (fail(→)pass) and regression avoidance (pass(→)pass) , and incorporates step-level scoring to pinpoint execution failures. Extensive experiments reveal that even state-of-the-art agents achieve pass rates below 20% in LongCLI-Bench. Step-level analysis further indicates that the majority of tasks stall at less than 30% completion, highlighting that critical failures often occur in the early stages. Although self-correction offers marginal gains, human-agent collaboration through plan injection and interactive guidance yields significantly higher improvements. These results highlight that future research must emphasize the development of synergistic human-agent workflows alongside advances in agents’ planning and execution capabilities to overcome key challenges in long-horizon task performance.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：AI辅助编程正从代码生成向自主软件工程演进，现代Agent（如SWE-agent、OpenHands、Codex等）能通过命令行界面（CLI）执行多步骤工作流。然而，现有基准（如HumanEval、SWE-bench、Terminal-Bench）存在三大局限：
  - **任务时限短**：缺乏长程、连续依赖的真实场景。
  - **数据污染**：从GitHub爬取的任务易被模型记忆。
  - **评估粒度粗**：仅提供二值通过/失败，无法诊断中间步骤失败点。
- **核心问题**：如何构建一个能严格评估Agent在长程、真实CLI环境中规划与执行能力的基准。
- **整体含义**：提出LongCLI-Bench，填补长程代理编程评估空白，揭示当前最先进Agent在长程任务上的严重不足（通过率<20%），并指出人机协同是未来突破方向。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 从**计算机科学课程作业（958个）** 和**真实研发工作流（50个）** 中手工筛选20个高质量长程任务，覆盖四种工程类别，并设计双测试集与步骤级评分，实现细粒度、抗污染评估。

### 关键技术细节
- **数据构建流程**：
  1. 候选池收集（1000+） → 使用Codex初步执行过滤（<50个） → 人工审查保留复杂任务。
  2. 为每个任务编写需求文档（避免简单检索匹配）、构建Docker隔离环境、构建人类参考答案（确保可解性）。
  3. 测试套件编写（仅基于需求文档，不依赖参考答案）：
     - **F2P（Fail → Pass）**：检测新需求是否实现。
     - **P2P（Pass → Pass）**：检测是否破坏原有功能（回归测试）。
  4. 双集验证：初始repo上F2P必须失败、P2P必须通过；解决方案repo上两者必须通过。未通过则迭代修正（最多3轮），否则丢弃。
  5. 专家最终审查。

- **任务组成**：初始仓库、需求文档、隔离环境、参考答案、双测试套件、评分解析器、元数据（类型、领域、难度、预估时间）。

- **评估指标**：
  - **步骤级得分**（Step Score）：F2P和P2P各子步骤完成百分比。
  - **通过率**（Pass Rate）：F2P和P2P步骤得分均达100%才算通过。
  - **Pass@3**：3次独立运行中至少一次通过的比例。
  - **额外设置**：多轮自修正（利用上一轮测试反馈重新执行）、人机协作（静态计划注入、动态交互指导）。

- **工程类别**：From Scratch (0→1)、Feature Addition (N→N+1)、Bug Fix (No→Yes)、Refactor (A→A′)。
- **领域覆盖**：系统编程、Web开发、数据工程、机器学习、应用（游戏/仿真）、DevOps。

## 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**：
  - **LongCLI-Bench**：20个任务，平均每个任务104个文件、15,000+行代码、专家完成时间1000+分钟（对比Terminal-Bench@2：0.69文件、227.7行、206.7分钟）。
  - 来源：CS课程作业（108门课程）和真实研发工作流，经严格过滤。

- **Benchmark对比**：LongCLI-Bench vs Terminal-Bench@2（表1），突出任务规模与复杂度差异。

- **对比方法**：
  - **商业CLI助手**：
    - Codex（GPT-5.1/5.2/5.3-Codex-Max）
    - Claude Code（Claude-Sonnet-4.5、Claude-Opus-4.5/4.6）
  - **开源框架**（OpenHands + 开源模型）：
    - DeepSeek-V3.1、GLM-4.6、Qwen3-235B-A22B

- **实验设置**：统一系统提示，每个模型运行3次独立尝试，报告平均结果。

## 4. 资源与算力

- **未明确说明**：论文未提供训练或推理所使用的GPU型号、数量、训练时长等具体算力信息。实验主要涉及推理（调用已训练好的API或开源模型），未涉及模型训练。因此无法统计。

## 5. 实验数量与充分性

- **主实验**（表2）：9种模型×3次运行=27组结果，覆盖商业和开源。
- **步骤级分析**（表3）：统计F2P得分分布（按[0,30)、[30,60)、[60,80)、[80,100)、[100]五个区间）。
- **自修正实验**（图4）：对Codex GPT-5.3-Codex和Claude-Opus-4.6进行T1→T2→T3多轮自修正（每组3次运行）。
- **人机协作实验**（表4）：两种模型×4种模式（Base、Self-Correction、Plan、Interactive、Plan & Interactive），报告通过率、F2P得分、时间和干预次数。
- **错误分析**：手动检查50条失败轨迹，归纳三类主要原因。
- **充分性评估**：
  - **优点**：多维度实验（不同模型、多轮、人机协作）；步骤级指标揭示失败模式；错误分析提供定性洞察。
  - **不足**：
    - 数据集仅20个任务，统计显著性有限。
    - 仅评估了有限数量的模型和框架（特别是开源模型只有3个）。
    - 每次运行仅3次，可能存在随机波动。
    - 缺乏对模型规模、推理成本等消融实验。
    - 人机协作实验的干预次数上限为3次，可能未充分探索。
  - **总体评价**：实验设计较全面，但受限于基准规模，结论需要更大样本验证。

## 6. 论文的主要结论与发现

- **所有Agent通过率均低于20%**：最优模型Claude-Opus-4.6仅16.7%，Codex GPT-5.3-Codex为15.0%。表明长程CLI任务远未解决。
- **早期阶段失败主导**：步骤级分析显示，大部分任务在完成度<30%时即失败（商业模型~40%运行处于该区间，开源模型~60%）。早期规划能力是瓶颈。
- **回归风险高**：P2P步骤得分很高（>98%），但P2P通过率仅70%-88%，说明Agent在修改时容易破坏已有功能。
- **自修正提升有限**：自修正可从T1到T2提升5-15%通过率，但后期增益递减，且可能引入新回归。
- **人机协作显著提升**：
  - 静态计划注入（Plan）优于自修正，且时间成本更低。
  - 动态交互指导（Interactive）进一步改善。
  - 两者结合最优（Claude-Opus-4.6达61.7%通过率，F2P得分69.3%）。
- **错误主要原因**：弱策略适应导致的重复循环、环境接地与验证差距、长期不一致与回归。

## 7. 优点

- **任务真实性与长程性**：每个任务平均15K+代码行、104文件，远超现有基准，极大提升评估难度和生态效度。
- **抗污染设计**：不使用GitHub公开数据，而是从课程作业和自建工作流中手工筛选并改写需求，降低数据污染风险。
- **细粒度评估**：提出步骤级得分，区分早期失败与接近成功，定位具体断点。
- **双测试集**：同时评估新需求实现（F2P）和回归保护（P2P），更全面反映工程能力。
- **多类别覆盖**：涵盖四种工程类别和六种技术领域，评估维度丰富。
- **人机协作实验设计**：量化计划注入和交互指导各自贡献，为未来发展提供具体方向。

## 8. 不足与局限

- **任务创建成本高**：平均每个任务需40小时人工投入，导致数据集小（仅20个任务），统计效力有限，可能引入选择偏差。
- **评估指标不够全面**：仅依赖测试通过率，未考虑代码质量、执行效率、可维护性、合理性等。
- **领域覆盖有限**：虽提及六个领域，但20个任务可能无法代表所有软件工程场景，泛化性受限。
- **人机协作实验受限**：
  - 只测试了两种模型，且干预次数上限为3次。
  - 交互指导的具体内容由人类实验者决定，可能存在主观性。
- **自修正设置简化**：仅使用同一测试反馈，未探索更复杂的反馈形式（如结构化错误定位）。
- **缺乏对模型规模/推理策略的消融**：未比较不同规模模型或不同推理预算下的性能差异。
- **数据来源单一**：主要来自CS课程和学术研究场景，工业级大型项目（如大型商业系统）未覆盖。

（完）
