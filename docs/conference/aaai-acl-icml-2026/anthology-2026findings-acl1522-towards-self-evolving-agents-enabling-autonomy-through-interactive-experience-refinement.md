---
title: "Towards Self-Evolving Agents: Enabling Autonomy through Interactive Experience Refinement"
title_zh: 面向自演化智能体：通过交互经验精炼实现自主性
authors: "Cheng Yang, Xuemeng Yang, Licheng Wen, Daocheng Fu, Jianbiao Mei, Rong Wu, Pinlong Cai, Yufan Shen, Nianchen Deng, Jia Xu, Botian Shi, Yu Qiao, Haifeng Li"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1522.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 通过经验精炼实现自主演化的智能体
tldr: 该论文提出MUSE框架，使大语言模型智能体能够通过交互经验自我演化。MUSE采用分层记忆模块组织跨领域知识，并在子任务执行后自主分析操作日志，将原始执行数据蒸馏为结构化可复用知识。在TAC基准上，MUSE展示了动态演化能力，解决了静态模型无法从过去经验中学习的问题。这项工作为实现自主研究型智能体迈出了重要一步。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 795, \"height\": 637, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1584, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 789, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 443, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 937, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 830, \"height\": 158, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 309, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 356, \"height\": 203, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 856, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 876, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 864, \"height\": 254, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1374, \"height\": 1560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1535, \"height\": 749, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1522/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1535, \"height\": 749, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1469, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1472, \"height\": 421, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1503, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1527, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 794, \"height\": 1256, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 727, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1311, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1332, \"height\": 1826, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1280, \"height\": 1654, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1376, \"height\": 1017, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1455, \"height\": 2471, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1456, \"height\": 2541, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1456, \"height\": 2535, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1455, \"height\": 2535, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1522/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1464, \"height\": 814, \"label\": \"Table\"}]"
motivation: 大语言模型推理时静态不变，无法从过往经验中学习，难以处理复杂多步任务。
method: 提出MUSE框架，包含分层记忆模块和自主执行后批判机制，将日志转化为结构知识。
result: 在TAC基准上表现优于静态基线，展现了持续自我改进能力。
conclusion: 该方法为构建能动态演化的自主智能体提供了一种有效范式。
---

## Abstract
Large Language Models often struggle with complex, multi-step operational tasks because they remain static during inference and cannot learn from past experience. To address this, we propose MUSE, a framework that enables iterative self-improvement through a hierarchical Memory Module. MUSE organizes cross-domain insights to facilitate the orchestration of long-horizon workflows. The core of our approach is an autonomous post-execution critique mechanism: after completing each sub-task, the system analyzes its operational logs and distills raw execution data into structured, reusable knowledge. This allows the agent to evolve dynamically rather than relying on fixed parameters. Evaluated on the rigorous TAC productivity benchmark, MUSE achieves new state-of-the-art results, significantly outperforming previous methods using only the streamlined Gemini-2.5 Flash model. Our analysis demonstrates that MUSE’s performance scales with the accumulation of insights and exhibits strong cross-task transferability, marking a key step toward autonomous systems capable of lifelong learning in professional environments. Demo videos can be found in our supplementary materials.

---

## 论文详细总结（自动生成）

# 论文总结：Towards Self-Evolving Agents: Enabling Autonomy through Interactive Experience Refinement

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在推理时保持静态，无法从过往经验中学习，导致在处理复杂、多步骤的实操任务（如跨应用长流程办公任务）时表现不佳。现有智能体方法要么需要参数更新（如强化学习，样本效率低），要么依赖冻结的闭源模型，造成“一次性”交互模式——任务失败或成功都无法转化为可持续改进的知识。
- **整体含义**：论文提出 **MUSE**（Memory-Utilizing and Self-Evolving）框架，旨在让 LLM 智能体通过交互经验自主演化，实现“边工作边学习”的测试时持续改进能力，为构建可终身学习的自主系统迈出关键一步。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：围绕分层记忆模块构建“规划→执行→反思→记忆”的闭环迭代流程。智能体在执行每个子任务后自动分析操作轨迹，将原始执行数据蒸馏为结构化、可复用的知识，存储在三种类型的记忆中，从而在不修改模型权重的情况下实现动态演化。

- **关键技术细节**：
  - **记忆模块（M）** 分为三层：
    - **策略记忆（M_strat）**：存储高层行为范式，如“问题-解决方案”对，加载到系统提示中指导全局策略。
    - **过程记忆（M_proc）**：存储成功的子任务操作流程（SOP），按应用和操作步骤索引，支持主动检索，模仿人类查阅案例的方式。
    - **工具记忆（M_tool）**：存储单个工具的使用技巧和动态指令，包括静态描述和动态反馈，辅助下一步动作选择。
  - **规划-执行智能体（PE Agent）**：
    - 将主任务分解为有序子任务队列，每个子任务包含描述和目标。
    - 使用最小化工具集（浏览器、代码解释器、Shell、视觉提取器、记忆检索器）执行子任务，不依赖特定应用 API，强调通过组合基本工具实现智能。
    - 执行中通过记忆增强的 ReAct 循环（Thought-Action-Observation）进行，失败时由反思智能体干预并允许一次重试（鼓励探索新方法）。
  - **反思智能体（Reflect Agent）**：
    - 作为独立第三方监督者，在子任务完成后自动评估（真实性验证、交付物验证、数据保真度）。
    - 评估成功则蒸馏为新 SOP 加入过程记忆；失败则生成故障分析，触发重规划。
    - 任务全部完成后，升级策略记忆和工具记忆，并全局精炼（去重、泛化）记忆库。
  - **关键机制**：记忆以自然语言存储，因此模型无关，不同 LLM 之间可无缝迁移；记忆索引和内容分离，避免上下文爆炸。

## 3. 实验设计

- **数据集/场景**：使用 **TheAgentCompany (TAC)** 基准，包含 175 个任务，模拟高保真企业环境（6 种角色，如HR、PM、SDE），涉及跨应用长流程操作（平均约 40 步动作，最多超百步）。重点评估智能体的长程规划、跨工具集成和持续学习能力。
- **基准与对比方法**：
  - 对比了 **OpenHands**（多种模型）、**OpenHands-Versa**、**OWL-RolePlay** 等框架，使用 Gemini-2.5 Pro/Flash、Claude-4 Sonnet、GPT-4o 等模型。
  - 额外与基于开源模型（Llama-3.1 405B、DeepSeek-V3 等）的 OpenHands 对比。
- **评估指标**：主要指标为部分完成分数（S_partial = 0.5*完成检查点比例 + 0.5*完整完成指示变量），以及聚合检查点分数（S_ckpt）和完美完成率（PCR）。
- **实验设置**：PE Agent 和 Reflect Agent 使用 Gemini-2.5 Flash 模型（NPC 使用 GPT-4o）；子任务最大动作数 N=20。

## 4. 资源与算力

- **未明确说明**：论文未提及训练或推理所使用的具体 GPU 型号、数量及时长。仅指出使用闭源模型 Gemini-2.5 Flash（轻量级），未报告硬件资源消耗。实验中统计了 token 消耗，但未涉及硬件配置。

## 5. 实验数量与充分性

- **实验组数**：
  - **持续学习实验**：从 TAC 中选取 18 个任务（T_cl 集）进行 3 轮迭代，每轮 18 个任务，共进行 5 次独立运行取平均。
  - **泛化实验**：选取 12 个高难任务（T_hard 集），对比有/无记忆的零样本迁移。
  - **全基准实验**：在全部 175 个任务上评估，使用冻结的（从 T_cl 积累的）记忆。
  - **消融实验**：
    - 组件消融（PE/Reflect/记忆模块）在 T_cl 上。
    - 模型消融（DeepSeek-V3 有无记忆、不同闭源模型对比）。
- **充分性与公平性**：
  - 设计了多轮迭代和多次运行以降低随机性，报告平均值。
  - 在持续学习和零样本泛化两维度验证，覆盖了演化性和迁移性。
  - 消融实验清晰展示了各组件贡献。
  - 对比方法均使用相同或更强模型，实验设置公开。
  - 不足：T_cl 仅 18 个任务（约 10% 全量），但论文通过泛化实验弥补；部分评估脚本僵硬，对有效但非常规解可能误判（论文已指出）。

## 6. 主要结论与发现

- MUSE 在 TAC 全基准上达到 **新 SOTA**：S_partial 51.78%（首次突破 50%），相比前 SOTA（OpenHands-Versa w/ Claude-4 Sonnet）提升近 20%。
- **持续学习能力**：在 T_cl 上 3 轮迭代后，S_ckpt 和 S_partial 单调上升，最终超过无记忆基线 10% 以上。
- **零样本泛化能力**：在 T_hard 上，带记忆版本比无记忆版本提升约 10 个百分点（S_partial 从 23.65% 到 33.41%），证明记忆可迁移。
- **框架通用性**：MUSE 可与开源模型（DeepSeek-V3）结合，且记忆跨模型共享有效；即使用更轻量的 Gemini-2.5 Flash，性能也超过 OpenHands 搭配 Gemini-2.5 Pro 的结果。
- **效率与性能平衡**：记忆模块仅带来约 98 秒/任务的额外成本，却带来最大性能增益。

## 7. 优点

- **创新性**：提出“规划-执行-反思-记忆”闭环，无需人类标注或模型微调即可实现测试时持续学习。
- **实用性强**：采用最小化工具集（浏览器+代码解释器+Shell），避免依赖特定 API，通用性高。
- **记忆设计精巧**：三层记忆对应不同抽象层次，过程记忆支持主动检索和即时扩充，策略和工具记忆在任务后精炼，自然语言格式确保跨模型迁移。
- **实验设计全面**：覆盖持续学习、零样本泛化、全基准对比、组件消融、模型消融，且多次运行取平均减少随机性。
- **结果显著**：仅用 Lightweight Flash 模型超越所有之前方法，验证了“经验驱动演化”的有效性。

## 8. 不足与局限

- **记忆架构适用范围有限**：论文承认当前记忆对高层规划或多跳搜索任务处理仍存在局限，不能解决所有问题。成功主要归因于“避免失败路径”而非真正理解深层语义。
- **环境感知盲区**：智能体缺乏人类主动的多模态直觉，在处理非结构化数据（如图片嵌入PDF、Excel 中千位分隔符）时易失败，导致任务受阻。
- **评估僵化**：TAC 基准的部分评估脚本过于刚性，无法适应有效但非常规的解决路径（如建群讨论 vs 一对一聊天），可能导致分数低估。
- **算力资源未说明**：缺少硬件资源消耗报告，不利于复现和成本评估。
- **记忆积累规模**：T_cl 仅 18 个任务，长期大规模记忆的扩展性和检索效率尚未充分验证。
- **外部依赖**：依赖闭源模型（Gemini-2.5 Flash/Pro），虽然记忆模型无关，但核心推理仍受限于第三方 API 的稳定性和控制力。
- **潜在偏差**：TAC 环境相对理想化，真实企业场景可能包含更多噪音、权限变化和异常状态，泛化到真实部署尚需更多验证。

（完）
