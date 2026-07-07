---
title: "AutoReproduce: Automatic AI Experiment Reproduction with Paper Lineage"
title_zh: AutoReproduce：利用论文谱系自动复现AI实验
authors: "Xuanle Zhao, Zilin Sang, Yuxuan Li, Qi Shi, Weilun Zhao, Shuo Wang, Duzhen Zhang, Xu Han, Zhiyuan Liu, Maosong Sun (孙茂松)"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.1001.pdf"
tags: ["query:ar"]
score: 9.0
evidence: 自动实验复现的多智能体框架
tldr: 该论文针对AI实验复现困难的问题，提出了基于论文谱系的多智能体框架AutoReproduce，能够端到端自动复现实验代码。通过采样单元测试策略快速验证代码可执行性。实验表明该方法有效提升了复现效率，对加速科学进步具有重要价值。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1001/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1590, \"height\": 866, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1001/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 775, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1001/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1577, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1001/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1609, \"height\": 971, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1001/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1557, \"height\": 1787, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1001/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1630, \"height\": 573, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1001/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1629, \"height\": 540, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1001/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 809, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1001/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 817, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1001/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1636, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1001/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 786, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1001/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1678, \"height\": 799, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1001/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1406, \"height\": 332, \"label\": \"Table\"}]"
motivation: 复现论文实验耗时且需要专业知识，亟需自动化方法。
method: 提出论文谱系挖掘引用文献隐含知识，构建多智能体框架实现自动代码复现。
result: 在基准测试上验证了框架的复现能力，提升了可执行代码的生成质量。
conclusion: AutoReproduce可显著降低复现成本，推动科研可重复性。
---

## Abstract
Efficient reproduction of research papers is pivotal to accelerating scientific progress. However, the increasing complexity of proposed methods often renders reproduction a labor-intensive endeavor, necessitating profound domain expertise.To address this, we introduce the paper lineage, which systematically mines implicit knowledge from the cited literature. This algorithm serves as the backbone of our proposed , a multi-agent framework designed to autonomously reproduce experimental code in a complete, end-to-end manner. To ensure code executability, incorporates a sampling-based unit testing strategy for rapid validation. To assess reproduction capabilities, we introduce , a benchmark featuring verified implementations, alongside comprehensive metrics for evaluating both reproduction and execution fidelity. Extensive evaluations on PaperBench and demonstrate that consistently surpasses existing baselines across all metrics. Notably, it yields substantial improvements in reproduction fidelity and final execution performance. The code is available at https://github.com/AI9Stars/AutoReproduce .

---

## 论文详细总结（自动生成）

# AutoReproduce：利用论文谱系自动复现AI实验——详细总结

## 1. 核心问题与研究动机
- **问题**：随着AI领域论文数量激增，实验方法日益复杂，手动复现实验需要大量专业知识和时间，严重阻碍科学进步。
- **背景**：现有LLM相关研究多聚焦于论文分析或离散复现任务（如环境搭建、代码重构），缺乏端到端的自动化实验复现框架。同时，论文中常隐含领域特定的实现惯例（如数据预处理管道、模块架构），这些“隐性知识”未被显式利用。
- **目标**：设计一个能自动、完整、可执行地复现论文实验代码的多智能体系统，并建立标准化的评估基准。

## 2. 方法论：AutoReproduce框架

### 核心思想
- 提出 **“论文谱系”（Paper Lineage）** 算法，通过追溯论文引用的文献及其代码仓库，系统性地挖掘领域内隐式知识（如常见架构、数据处理惯例），为代码生成提供参考。
- 基于此构建 **多智能体（Multi-Agent）框架**，包含两个角色：**研究Agent**（负责文本分析、论文摘要、相关文献审查）和 **代码Agent**（负责代码实现、调试、执行）。

### 关键技术细节
- **三个阶段**：
  1. **文献综述**：使用MinerU工具将PDF转换为Markdown，并由研究Agent生成三级分层摘要（整体、方法、实验设置）。
  2. **论文谱系生成**：
     - 研究Agent从源论文的参考文献中选出Top-k（默认k=3）相关论文（优先选择基线方法）。
     - 通过ArXiv API下载全文并提取代码仓库链接。
     - 代码Agent利用GitHub API克隆仓库，并根据论文摘要和指令过滤出相关代码文件，形成`<摘要, 代码>`元组作为领域参考。
  3. **代码开发**：
     - 包括三个子阶段：数据获取（分析数据集属性，生成加载代码）、方法复现（双Agent协作迭代实现）、实验执行（完整流水线+提前退出机制）。
     - 提出**基于采样的单元测试策略**：使用小批量数据快速验证代码可执行性；采用`EDIT`命令对文件按行替换，减少token开销。
     - 提供Docker容器预装PyTorch、NumPy等，允许代码Agent通过Bash安装缺失依赖。

## 3. 实验设计

### 基准（Benchmark）
- **REPRODUCEBENCH**：人工精选的13篇论文，覆盖计算机视觉、时间序列、知识蒸馏、视频预测、人体运动预测、图像去雾、求解PDE、医学图像分割、图神经网络、时间序列生成、低光照增强、协同过滤、图像超分等13个子领域。
- 每篇论文提供人工验证的参考代码和基线性能（在A100 GPU上重新运行得到）。
- **评估指标**：
  - **Align-Score**（对齐度）：分三个层面，由o1作为LLM Judge自动评分。
    - Paper-Level：提取5个关键点（3个方法点、1个超参数点、1个训练设置点），每点0-20分。
    - Code-Level：比对参考代码的4个维度（整体结构、模型细节、训练细节、实验完整性），各25分。
    - Mixed-Level：结合论文关键点和参考代码，对每点0-20分评分，最终加权。
  - **Exec-Score**（执行度）：
    - 执行率（Exec Rate）：可运行代码比例。
    - 性能差距（Perf Gap）：相对性能偏差，公式为 \( \frac{1}{n} \sum \frac{|P_{ref} - P_{agent}|}{\max(P_{ref}, P_{agent})} \)。不可执行实例设Pagent=0，差距最大1.0。

### 对比方法
- **ChatDev** (GPT-4o)：通用软件工程智能体
- **Agent Laboratory** (GPT-4o)：科研辅助智能体
- **PaperCoder** (o3-mini)：并发工作，单次生成代码但不考虑可执行性
- **AutoReproduce** 使用不同LLM骨干（Claude-3.5-Sonnet、o3-mini、Gemini-2.5-Pro）

### 额外基准
- **PaperBench Code-Dev**：专注于静态代码生成的独立基准（不要求可执行性），AutoReproduce去掉迭代调试阶段进行对比。

## 4. 资源与算力
- **硬件**：所有实验在Tesla A100 GPU上执行。
- **成本**：在REPRODUCEBENCH上，使用o3-mini骨干时，复现单篇论文平均成本约 **1.87美元**（包括API调用和计算）。
- **训练时长**：未明确报告每篇论文的完整训练时间，仅提到使用提前退出机制进行快速验证。
- **注意**：论文未披露总运行时间、GPU数量等算力细节。

## 5. 实验数量与充分性

### 实验数量
- **主实验**：在REPRODUCEBENCH上，对每种方法（5种）和每种LLM骨干（多个变体）均进行了 **3次独立运行**，报告平均值。
- **PaperBench实验**：一次运行。
- **消融实验**：5组（有/无视觉图、无MinerU、无线谱、无精炼、无调试+精炼），每组一次运行。
- **人类评估**：5名评估者（3名博士、1名硕士、1名高年级本科生）对每个案例评分，共15个案例（3种方法×5个模型变体？实际表格有4种方法，每种可能多个结果）。

### 充分性与公平性
- **全面性**：覆盖13个不同AI子领域，包括训练从零开始和微调预训练模型两种范式。
- **消融实验**：验证了论文谱系、视觉图、MinerU、调试与精炼各模块的贡献。
- **评估客观性**：Align-Score使用o1作为LLM Judge，但论文做了人类评估相关性分析，证明Mixed-Level评分与人类判断Pearson相关系数达0.78~0.83，优于Paper-Level和Code-Level。
- **局限性**：每个消融实验仅执行一次，未报告方差；消融实验数量较少（5组）。

## 6. 主要结论与发现
- **AutoReproduce在所有指标上显著优于现有基线**：在REPRODUCEBENCH上，使用o3-mini时执行率达92.31%，性能差距仅24.31%（对比ChatDev的Exec Rate 2.56%、Perf Gap 99.62%）。
- **论文谱系算法有效**：去除后Mixed-Level评分从69.97降至63.15，Perf Gap从31.62%升至39.59%。
- **调试与精炼至关重要**：去除后执行率大幅下降（Perf Gap升至88.78%）。
- **Mixed-Level评分优于单一层面评分**：与人类判断相关性最高。
- **LLM法官可能高估Paper-Level一致性**：因为文本描述较泛，而Code-Level又过于敏感；Mixed-Level平衡二者。
- **论文谱系选择的论文与专家标注高度一致**：Top-1 Recall@3达0.77，Hits@3平均3.73。

## 7. 优点
- **端到端自动化**：首次实现从论文输入到可执行代码的完全自动化，无需人工干预。
- **创新性地利用论文谱系**：通过挖掘引用文献中的隐性知识，显著提升代码生成质量。
- **可执行性保障**：采样单元测试+迭代调试，使执行率远高于竞争对手。
- **全面的评估体系**：从对齐度（多层面）和执行度两个维度设计指标，并验证与人类判断的一致性。
- **开源且实验可复现**：代码仓库公开，基准测试包含人工验证的参考实现。

## 8. 不足与局限
- **仅限于单任务级复现**：无法处理仓库级完整代码生成，对于多模块协作、完整训练脚本还需进一步扩展。
- **数据预处理未自动化**：对于自定义数据集，论文假设已提供预处理管道，实际中数据清洗仍依赖人工。
- **算力消耗未详细记录**：未报告GPU总数、训练小时数，影响复现成本评估。
- **消融实验次数少**：每组仅一次运行，未提供统计显著性检验。
- **对非常规论文可能失效**：若论文引用文献不充分或领域极度新颖，谱系挖掘效果会下降。
- **依赖于LLM的质量**：对齐度评估使用o1作为Judge，存在潜在偏差；且成本较高（每篇评估约0.5美元）。
- **人类评估样本有限**：仅5名评估者，可能存在主观性。

（完）
