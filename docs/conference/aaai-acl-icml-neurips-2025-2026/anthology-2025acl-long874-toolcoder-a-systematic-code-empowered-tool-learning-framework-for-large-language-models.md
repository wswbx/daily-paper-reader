---
title: "ToolCoder: A Systematic Code-Empowered Tool Learning Framework for Large Language Models"
title_zh: ToolCoder：一种系统性代码赋能的大型语言模型工具学习框架
authors: "Hanxing Ding, Shuchang Tao, Liang Pang (庞亮), Zihao Wei, Jinyang Gao, Bolin Ding, Huawei Shen (沈华伟), Xueqi Cheng (程学旗)"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.874.pdf"
tags: ["query:cli-agent"]
score: 8.0
evidence: 将自然语言查询转化为Python代码以使用工具，支持命令行自动化
tldr: 论文提出ToolCoder，将工具学习转化为代码生成任务。它将自然语言查询映射为结构化的Python函数框架，并结合描述性注释分解任务，使LLM能够通过编程范式进行推理和规划。该方法适用于包括命令行操作在内的工具使用场景，显著提升了多步规划和错误诊断能力。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.874/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 804, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.874/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1598, \"height\": 872, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.874/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 791, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.874/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 737, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.874/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 810, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.874/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1648, \"height\": 1168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.874/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1642, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.874/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1643, \"height\": 2024, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.874/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1655, \"height\": 627, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.874/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 809, \"height\": 371, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.874/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 806, \"height\": 977, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.874/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 649, \"height\": 341, \"label\": \"Table\"}]"
motivation: 现有工具学习依赖手工提示，难以处理多步规划和错误诊断。
method: 将工具学习转化为代码生成，从自然语言生成Python函数支架。
result: 在多个工具使用基准上实现了更高的任务成功率。
conclusion: ToolCoder为LLM工具学习（包括CLI代理）提供了代码驱动的有效方案。
---

## Abstract
Tool learning has emerged as a crucial capability for large language models (LLMs) to solve complex real-world tasks through interaction with external tools. Existing approaches face significant challenges, including reliance on hand-crafted prompts, difficulty in multi-step planning, and lack of precise error diagnosis and reflection mechanisms. We propose ToolCoder , a novel framework that reformulates tool learning as a code generation task. Inspired by software engineering principles, ToolCoder transforms natural language queries into structured Python function scaffold and systematically breaks down tasks with descriptive comments, enabling LLMs to leverage coding paradigms for complex reasoning and planning. It then generates and executes function implementations to obtain final responses. Additionally, ToolCoder stores successfully executed functions in a repository to promote code reuse, while leveraging error traceback mechanisms for systematic debugging, optimizing both execution efficiency and robustness. Experiments demonstrate that ToolCoder achieves superior performance in task completion accuracy and execution reliability compared to existing approaches, establishing the effectiveness of code-centric approaches in tool learning.

---

## 论文详细总结（自动生成）

# 论文详细中文总结：ToolCoder

## 1. 核心问题与整体含义（研究动机和背景）

大型语言模型（LLM）通过与外部工具交互来解决复杂现实任务（即工具学习）已成为关键能力。然而，现有方法存在三大局限：

- **弱规划（Weak Planning）**：依赖手工构造的提示（hand-crafted prompts），在复杂多步任务中难以形成可靠的执行计划。
- **缺乏错误处理（Lack of Error Handling）**：当工具调用失败时，无法精准定位错误根因，也无法提出有针对性的修正措施。
- **无经验复用（No Experience Reuse）**：每个查询被孤立处理，成功执行的方案无法积累和复用，导致重复解决类似问题。

当前主流方法（如 ReAct、Chameleon）遵循“规划-执行-观察”的循环范式，但上述局限严重制约了工具学习系统的鲁棒性、适应性和可扩展性。

## 2. 方法论：核心思想、关键技术细节、流程

### 2.1 核心思想
**将工具学习重新定义为代码生成任务**，借鉴软件工程原则，利用 LLM 的代码生成能力来驱动工具规划、执行和调试。

### 2.2 整体流程（四个阶段）

1. **任务到代码转换（Task-to-Code Transformation）**  
   - 将自然语言查询 \(q\) 转换为结构化的 **Python 函数支架（scaffold）** \(c\)，包括函数名、参数列表、返回类型和完整的文档字符串（docstring）。函数体初始为空，作为后续规划与实现的占位符。
   - 形式化：\(c = M_{T2C}(q)\)，其中 \(M_{T2C}\) 是任务-代码转换模块。

2. **子任务规划与工具选择（Subtask Planning & Tool Selection）**  
   - **子任务规划** \(M_{TP}\)：分析支架 \(c\) 和候选工具箱 \(T\)，生成一系列描述性子任务 \(s = \{s_1, s_2, \dots, s_m\}\)，并嵌入为代码注释，形成带注释的支架 \(c_s\)。
   - **工具选择** \(M_{TS}\)：根据子任务计划 \(c_s\) 和工具文档 \(D\)，生成伪代码 \(c_p\)，其中包含工具调用序列和数据流路径，工具调用以 `call_api(api_path, params)` 占位符表示。

3. **实现与执行（Implementation & Execution）**  
   - **代码生成** \(M_{CG}\)：根据伪代码 \(c_p\)、所选工具子集 \(T_s\) 和可复用的函数仓库 \(F\)，生成完整可执行的 Python 程序 \(F\)。仓库中的成功函数可直接复用。
   - **执行**：在 Python 环境 \(\mathbb{E}\) 中执行 \(F\)，得到响应 \(r\) 或异常 \(e\)。成功则返回最终答案，失败则触发错误反射。

4. **错误反射（Error Reflection）**  
   - **计划重构**：检测并替换无效的工具调用，确保所有工具存在于候选工具箱。
   - **代码审查**：利用 Python 异常回溯（traceback）识别错误位置和原因，迭代修正并重新执行（最多 3 次），直至成功或达到尝试上限。

### 2.3 关键组件
- **可复用函数仓库（Reusable Function Repository）**：存储已成功执行的子函数片段，支持跨任务复用，提升效率和可靠性。
- **错误诊断机制**：利用 Python 清晰详尽的回溯信息，实现对规划错误和执行错误的精准定位与自修正。

## 3. 实验设计

### 3.1 数据集与场景
- **RestBench**：包含两个真实场景：
  - **TMDB**：100 个电影相关任务，54 个工具。
  - **Spotify**：40 个音乐相关任务。
- **API-Bank**：73 个常用 API，314 个工具使用对话，753 个人工标注的 API 调用，分为 LV1（简单）和 LV2（复杂多步）。
- **ToolAlpaca-Real**：用于评估泛化能力的真实 API 任务数据集。

### 3.2 基准方法（Baselines）
- 文本式工具学习：ReAct、Chameleon、ConAgents、RestGPT、EasyTool。
- 代码式工具学习：ATC、CodeAct（最先进代码基线）。

### 3.3 评估指标
- **RestBench**：Success%（人工评估成功）、Accuracy%（答案正确性）、Path%（工具路径覆盖率）。
- **API-Bank**：Correctness%（API 调用正确性）。
- **ToolAlpaca**：Procedure、Response、Overall（综合流程与回答质量）。

## 4. 资源与算力

文中**未明确说明**实验所使用的 GPU 型号、数量或训练/推理时长。作者仅提到所有方法基于 `gpt-4o-mini` 实现，部分实验使用了开源模型（Qwen2.5 系列），未提供硬件配置细节。

## 5. 实验数量与充分性

论文进行了多组实验，全面且较为充分：

| 实验类型 | 数量 | 说明 |
|---------|------|------|
| 主实验结果（表1） | 4个数据集×10种方法 | 覆盖 RestBench-TMDB、Spotify、API-Bank LV1/LV2，对比7种基线 + 3种消融。 |
| 消融实验 | 3组 | 去除代码支架、去除可复用仓库、去除错误反射，分别在多个数据集上验证。 |
| 泛化实验（表2） | 新数据集 ToolAlpaca | 对比 ReAct、Chameleon、CodeAct 及自身消融。 |
| 开源模型实验（表3） | 4种 Qwen 模型（14B/32B，base/coder） | 验证跨模型和代码专用模型上的效果。 |
| 效率分析（表4） | 平均每问题 API 调用次数 | 对比 ReAct、Chameleon 等，证明 ToolCoder 效率相当。 |

实验设计客观：统一基础模型（gpt-4o-mini），对比了最先进基线；消融实验清晰展示了各组件贡献；开源模型实验增加了泛化说服力。但缺少对超参数（如错误反射迭代次数为3）的敏感性分析。

## 6. 主要结论与发现

1. **ToolCoder 在所有基准测试上取得最优性能**，显著超越文本式和代码式基线方法。例如在 RestBench-Spotify 上，Success% 比 CodeAct 提高 10.79%，Accuracy% 提高 22.22%；在 API-Bank LV2 上 Correctness% 提高 8.34%。
2. **代码支架（scaffold）是提升规划精度的关键**：去除后路径正确率大幅下降（图4）。
3. **可复用仓库持续提升累积成功率与精度**：随着推理过程推进，累积指标逐步上升（图5）。
4. **错误反射机制显著增强鲁棒性**：去除后所有指标下降，尤其在复杂任务上表现明显。
5. **代码专用模型（coder）比通用模型更适合 ToolCoder**：在不同参数量（14B/32B）上均体现出更大提升。
6. **ToolCoder 在效率上不额外消耗 API 调用**，与基线方法持平。

## 7. 优点

- **创新性**：首次系统地将软件工程原则（需求分析、模块化设计、错误诊断、代码复用）融入工具学习，转化为代码生成范式。
- **强实证**：在多个基准、多种模型（闭源+开源）上验证，消融和泛化实验设计完整。
- **可解释性与鲁棒性**：通过结构化代码、明确的错误回溯和函数仓库，使过程更可控、可调试。
- **实践高效**：无需额外训练，直接利用 LLM 推理，且效率不降低。

## 8. 不足与局限

- **依赖高质量的 API 文档**：当文档不完整、歧义或不一致时，模型推断工具行为的能力受限，这在真实场景中常见。
- **全局规划策略缺乏动态适应性**：采用一次性规划，难以应对任务需求变化或部分可观察环境中的实时调整。
- **可扩展性挑战**：当任务涉及大量工具和复杂交互时，可能面临组合爆炸，导致次优计划。
- **错误反射次数硬编码为3次**：未探讨不同迭代次数的影响，可能非最优。
- **未提供详细算力开销和训练成本**：虽然声明无需训练，但推理时多次调用 LLM 的 token 消耗未量化。
- **实验未涵盖多轮对话或持续学习场景**：仓库复用仅在同一会话内有效，跨会话持久化未验证。

（完）
