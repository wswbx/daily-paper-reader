---
title: "AXIS: Efficient Human-Agent-Computer Interaction with API-First LLM-Based Agents"
title_zh: AXIS：采用API优先的LLM代理实现高效人机交互
authors: "Junting Lu, Zhiyang Zhang, Fangkai Yang, Jue Zhang, Lu Wang, Chao Du, Qingwei Lin, Saravan Rajmohan, Dongmei Zhang, Qi Zhang"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.381.pdf"
tags: ["query:cli-agent"]
score: 8.0
evidence: API优先的LLM代理自动化计算机任务
tldr: "基于多模态大模型的代理通过UI交互完成复杂任务时存在高延迟和低可靠性。本文提出AXIS框架，优先使用API而非UI操作，并支持自动探索和扩展现有API。在Microsoft Word上的实验表明，任务完成时间减少65%-70%，认知负荷降低38%-53%，准确率保持在97%-98%。"
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1642, \"height\": 873, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1633, \"height\": 890, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1617, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1616, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1001, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1002, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1652, \"height\": 924, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 652, \"height\": 946, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 645, \"height\": 936, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 603, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 636, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 672, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1568, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.381/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1660, \"height\": 688, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 716, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 744, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 984, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1240, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1288, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1445, \"height\": 1096, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1226, \"height\": 1658, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1370, \"height\": 1110, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1034, \"height\": 1116, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.381/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 749, \"height\": 772, \"label\": \"Table\"}]"
motivation: 多模态大模型代理直接操作UI导致高延迟和低可靠性。
method: 提出AXIS框架，优先通过API执行操作并自动探索应用以扩展API。
result: "在Word任务上，完成时间降低65-70%，认知负荷降低38-53%，准确率97-98%。"
conclusion: API优先策略能显著提升LLM代理在计算机任务中的效率和可靠性。
---

## Abstract
Multimodal large language models (MLLMs) have enabled LLM-based agents to directly interact with application user interfaces (UIs), enhancing agents’ performance in complex tasks. However, these agents often suffer from high latency and low reliability due to the extensive sequential UI interactions. To address this issue, we propose AXIS, a novel LLM-based agents framework that prioritize actions through application programming interfaces (APIs) over UI actions. This framework also facilitates the creation and expansion of APIs through automated exploration of applications. Our experiments on Microsoft Word demonstrate that AXIS reduces task completion time by 65%-70% and cognitive workload by 38%-53%, while maintaining accuracy of 97%-98% compared to humans. Our work contributes to a new human-agent-computer interaction (HACI) framework and explores a fresh UI design principle for application providers to turn applications into agents in the era of LLMs, paving the way towards an agent-centric operating system (Agent OS). The code and dataset will be available at https://aka.ms/haci_axis.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）

现有的多模态大语言模型（MLLM）驱动的智能体（UI Agent）通过逐一操作图形界面（UI）来完成用户指令，但其面临三大挑战：  
- **高延迟**：每一步交互都需要一次 LLM 调用，且需传递大量 UI 信息，导致响应缓慢。  
- **低可靠性**：长链 UI 操作易累积幻觉和错误，导致任务失败。  
- **UI 泛化性差**：模型在训练阶段未见过的 UI 布局上表现不佳。  

论文提出一种**新的人–智能体–计算机交互（HACI）范式**，主张 **API-first**：LLM 智能体应优先通过应用程序编程接口（API）执行操作，而非模仿人类的 UI 点击，从而从根本上解决上述问题。

---

### 2. 方法论：核心思想、关键技术细节

**AXIS（Agent Exploring API for Skill Integration）** 是一个自动探索应用、学习并构建 API 技能的框架，其核心流程分为三个阶段：

- **阶段 I：轨迹收集（Trajectory Collection）**  
  - **Follower 模式**：基于官方帮助文档提取的步骤，让智能体严格跟随指令进行 UI 交互，收集执行轨迹。  
  - **Explorer 模式**：无预设指令，由 LLM 自主头脑风暴生成探索路径；通过初始状态多样性（随机重放中间文档）、垂直/水平探索策略、以及基于 MOS 认证等级的技能熟练度提示来实现广泛探索。

- **阶段 II：技能生成（Skill Generation）**  
  - **Monitor**：从轨迹中提取有意义的片段，合并为自然语言技能描述。  
  - **Generator**：将技能描述与对应轨迹片段结合，生成可执行的 Python 代码（内含 UI 操作）。  
  - **Translator**：借助检索增强生成（RAG）模块，将 UI 操作代码转换为直接操作应用对象模型的 API 调用（例如将 `click_input` 替换为 `Selection.Range.HighlightColorIndex` 属性赋值）。

- **阶段 III：技能验证（Skill Validation）**  
  - **静态验证**：检查代码语法、参数完整性、技能依赖正确性。  
  - **动态验证**：由 Validator Agent 生成多种测试参数，在实际文档环境中执行技能，经 Evaluator Agent 检查最终状态，确保技能能够泛化到新场景。

技能库初始包含 6 个基础动作（如 `click_input`、`select_text` 等），后续可不断扩充。技能分为原子 UI/API、复合 UI/API 以及混合型，支持嵌套调用。

---

### 3. 实验设计

- **可行性研究（Feasibility Study）**  
  - **数据**：从 WikiHow “Use Microsoft Word” 和 Microsoft 官方支持网站提取 **50 个 Word 任务**，按复杂度分为低难度（L1）和高难度（L2）。  
  - **基准（Baseline）**：UI Agent 代表方法 **UFO**（Zhang et al., 2024a）。  
  - **对比指标**：任务完成时间、成功率、所需步骤数、LLM 调用成本（GPT‑4o 版本 20240513）。  
  - **结果**：AXIS 平均完成时间 29.9s（UFO 为 59.5s），成功率 84%（UFO 52%），步骤和成本均显著降低。API 使用率 55.7%（其中高级 API 占 23.1%），而 UFO 仅 8.1%。

- **用户研究（User Study）**  
  - **参与者**：20 名自愿者（年龄 18–40，含学生、工程师、研究人员等），均有 Word 使用经验。  
  - **任务**：**5 个 Word 任务**（3 个 L1，2 个 L2），例如设置标题格式、插入页眉页脚、插入表格并调整纸张等。  
  - **三种方法**：纯手动操作、UI Agent（UFO）辅助、AXIS 辅助。  
  - **主观指标**：NASA‑TLX 六维度量表 + 学习努力度；对 Agent 的感知速度、流畅性、可靠性、决策一致性、UI 依赖度。  
  - **客观指标**：完成时间、成功率、步骤、成本、UI 交互次数。  
  - **结果**：  
    - AXIS 在 L1 和 L2 任务上均显著快于手动和 UI Agent（p < 0.001）；成功率接近手动（98.3% / 95.0%），远高于 UI Agent（75% / 45%）。  
    - NASA‑TLX 显示 AXIS 显著降低了心理/体力需求、挫折感和学习努力（尤其 L2 任务）。  
    - 用户偏好调查中，AXIS 在感知速度、流畅性、可靠性方面均优于 UI Agent，且随着任务复杂度提升，偏好差距更大。

---

### 4. 资源与算力

论文 **未明确说明** 使用的具体 GPU 型号、数量或训练时长。实验中提到所有 LLM 调用均使用 **GPT‑4o**（版本 20240513）作为后端，未涉及模型微调或分布式训练，因此算力需求主要体现在推理阶段。AXIS 的探索与技能验证均为在线过程，消耗由 API 调用数决定。

---

### 5. 实验数量与充分性

- **数量**：可行性研究 50 任务（L1 26，L2 24）；用户研究 20 参与者 × 5 任务 × 3 方法 = 300 条执行记录。  
- **充分性**：  
  - **优点**：同时包含客观（时间、成功率）和主观（认知负荷、偏好）指标；任务覆盖不同复杂度；对比了手动、UI Agent 和 AXIS 三种方式。  
  - **不足**：  
    - 仅针对 **Microsoft Word** 一个应用，泛化性存疑。  
    - 未进行 **消融实验**（如去掉 Explorer 模式或 Translator 的效果）。  
    - UI Agent 仅对比了 UFO，未包含其他主流方法（如 CogAgent、AppAgent）。  
    - 用户研究样本量较小（20 人），且未控制参与者的 Word 熟练程度差异。  
  - **总体评价**：在现有资源下实验设计较全面，但覆盖面和消融分析尚可补充。

---

### 6. 主要结论与发现

1. **API‑first 智能体能够大幅降低任务完成时间和认知负荷**：相比 UI Agent，AXIS 在 Word 任务上时间减少 65–70%，认知负荷降低 38–53%，同时保持 97–98% 的准确率。  
2. **自动技能生成与验证是可行的**：AXIS 通过 Follower/Explorer 模式成功挖掘了 73 个技能（包括 44 个原子技能和 29 个复合技能），并通过静态+动态验证保证了质量。  
3. **用户偏好显著偏向 API-first 方案**：在感知速度、流畅性、可靠性上 AXIS 均胜出，且用户认为 AXIS 的“侵入感”更低，控制感更好。  
4. **HACI 新范式为未来 Agent OS 提供了设计原则**：应用提供商可借助 AXIS 将应用包装成 API 集合，简化甚至裁剪不必要的 UI 组件。

---

### 7. 优点

- **创新性**：首次系统性地提出 **API-first** 的 HACI 范式，并设计了完整的自动探索–生成–验证框架。  
- **实用性**：实验结果（时间、成功率、认知负荷）差异显著，且在实际 Word 任务上验证，具有很强的应用价值。  
- **可扩展性**：框架设计通用，理论上可迁移到任何具备基础 API 和文档的应用。  
- **用户研究设计**：结合主观（NASA‑TLX）和客观指标，并收集用户偏好，提供了多维度的证据。  
- **技能验证机制**：静态+动态验证有效减少了 LLM 幻觉导致的错误技能入库。

---

### 8. 不足与局限

- **应用范围有限**：目前仅针对 Microsoft Word，且依赖 Python 接口（win32com），无法直接用于无 Python API 的应用。  
- **探索效率与稳定性**：作者承认 Explorer 模式在多样性和稳定性上还需改进，可能产生重复或无效轨迹。  
- **通用性验证不足**：未在多个操作系统、不同应用上评估；UI Agent 对比仅选 UFO，未涵盖更多 SOTA。  
- **用户研究局限**：样本量较小（20 人）、任务数量少（5 个），且未控制参与者英文程度对 GPT 指令理解的影响。  
- **消融分析缺失**：未单独分析 Follower vs Explorer、Translator 效果、技能层级深度等对最终性能的影响。  
- **无开源实现验证**：代码和数据集标注为“即将发布”，当前无法复现。  
- **成本依赖**：整个框架高度依赖 GPT‑4o 这类商业模型，实际部署成本可能较高。

---

（完）
