---
title: Benchmarking Agentic Newswriting via Journalistic Workflows
title_zh: 通过新闻工作流评估代理式新闻写作
authors: "Yen-Che Chien, Kuang-Da Wang, Wei-Yao Wang, Wen-Chih Peng"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1816.pdf"
tags: ["query:ar"]
score: 6.0
evidence: 代理式新闻写作工作流基准
tldr: 为评估自主代理在信息密集型新闻写作中的表现，NEWSAGENT基准要求代理根据写作指令和部分素材，自主规划、搜索、选择信息并迭代修改稿件。实验显示当前代理在复杂新闻写作中仍面临挑战，为自主研究代理在真实工作流中的应用提供了重要参考。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1816/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 767, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1816/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1631, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1816/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1638, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1816/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1535, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1816/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1638, \"height\": 944, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1816/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 806, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1816/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1661, \"height\": 513, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1816/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1661, \"height\": 382, \"label\": \"Table\"}]"
motivation: 现有自主代理在结构化任务上表现良好，但在新闻写作等真实信息密集型工作流中的能力尚不明确。
method: 提出NEWSAGENT基准，基于新闻写作流程设计多阶段评估任务，涵盖搜索、选择、迭代修改等环节。
result: 实验表明当前代理在新闻写作中需要进一步提升上下文推理和主动发现能力。
conclusion: 该基准为评估自主代理在真实工作流中的表现提供了新视角。
---

## Abstract
Recent advances in autonomous digital agents from industry (e.g., Manus AI and Gemini’s research mode) highlight their potential for structured tasks through autonomous decision-making and task decomposition, but it remains unclear how well such systems support real-world information-intensive workflows. We study this question in journalism, where newswriting requires iterative planning, contextual reasoning, and active discovery of missing background to produce a coherent article. We introduce NEWSAGENT, a benchmark for evaluating how agents search raw materials, select relevant information, and iteratively revise drafts through core journalistic functions. Given a writing instruction and partial firsthand materials, agents must identify narrative perspectives, issue keyword-based queries, retrieve historical context, and generate complete news articles. Unlike typical summarization or retrieval tasks, essential context is not directly available and must be actively discovered, reflecting real-world reporting constraints. NEWSAGENT consists of 6k human-verified examples derived from real news. We evaluate open- and closed-sourced LLMs with commonly-used agentic frameworks on NEWSAGENT, which shows that agents are capable of retrieving relevant facts but struggling with planning and narrative integration. We believe that NEWSAGENT serves a realistic testbed for iterating and evaluating agent capabilities in terms of web data manipulation to real-world productivity. The benchmark resources are publicly available at https://github.com/wywyWang/CoachAI-Projects.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：近年来，自主数字代理（如Manus AI、Gemini的深度研究模式）在结构化任务中展现了通过自主决策和任务分解完成复杂工作的潜力，但在真实世界信息密集型工作流中——例如新闻写作——的表现尚未被系统评估。
- **核心问题**：新闻写作要求迭代规划、上下文推理以及主动发现缺失背景信息，以构建连贯的叙事；这与传统的单次检索或摘要任务有本质区别。论文旨在衡量当前大型语言模型（LLM）能否模拟记者“从零散素材出发、主动搜索历史背景、迭代修改草稿”的完整工作流。
- **整体含义**：通过提出NEWSAGENT基准，论文填补了自主代理在真实新闻工作流评估中的空白，为未来研究提供了可复用的测试平台。

## 2. 论文提出的方法论

- **核心思想**：将新闻写作形式化为一个**迭代的观察-动作循环**，代理需要：①根据新闻标题和部分第一手素材（现场描述、引语、字幕等）识别叙事角度；②基于关键词查询检索在发布日期前可用的历史背景信息；③通过插入/删除操作编辑草稿；④最终将草稿重写为连贯的新闻文章。
- **关键技术细节**：
  - **数据集构建**：从BBC和APNews收集2025年6月1日至7月14日共31,097篇文章，经GPT-4分类、人工验证、程序化校验后得到6,237个人类已验证的样本。文章内容被分解为“对象”（描述、标题、引语/转录），按时间戳划分为“第一手信息”（出版时可用的原始材料）和“历史信息”（背景资料）。
  - **代理工作流（NEWSAGENT Pipeline）**：采用ReAct框架，每个时间步代理可执行以下动作之一：
    - `Search`：生成关键词查询，从历史信息库中检索最相关的前5个对象（余弦相似度阈值0.7）。
    - `Insert`：将检索到的对象添加到当前草稿（仅允许添加已检索的对象）。
    - `Remove`：从草稿中删除已有对象。
    - `Terminate`：结束循环，进入重写阶段。
  - **重写与可追溯性检查**：最终草稿经过重写步骤生成流畅段落，并进行后验可追溯性检查——若重写文本无法与任一已选对象匹配，则重新执行重写。
  - **两种执行模式**：1-step（直接选择操作并指定参数）和2-step（先选操作类型，下一步再指定参数），以隔离动作规范错误与决策本身。
- **评估协议**：
  - **功能级评估**：分别评估搜索和编辑的精确率、召回率、F1，与人类参考文章所选的证据集进行对齐比较。
  - **端到端评估**：采用GPT-4作为评判者，对候选文章进行六维（事实一致性、逻辑一致性、重要性、可读性、客观性、新闻风格）比较，合成总体偏好。经过人类验证，该维度式评估与人类判断的吻合度（72%）显著高于单轮整体评估（53%）。

## 3. 实验设计

- **数据集/场景**：NEWSAGENT基准包含6,237个真实新闻样本，涵盖政治、体育、科技、科学等领域。文章发布日期在2025年6-7月之间，所有模型训练数据均在此之前，避免数据泄露。
- **基准（Baseline）**：一个规则基线，不做规划或编辑，直接检索并插入前5条历史对象作为最终文章。
- **对比方法**：
  - 闭源模型：GPT-4o、GPT-4o-mini
  - 开源模型：Gemma-3-27b-it、Qwen3-32B、Llama-4-Scout-17B-16E-Instruct
  - 所有模型均在ReAct框架下运行，分别测试1-step和2-step设置。

## 4. 资源与算力

论文未明确提及使用的GPU型号、数量或训练时长。仅说明模型通过API调用（OpenAI API、DeepInfra API）进行评估，未涉及模型训练或微调。因此算力消耗体现为推理成本，而非训练资源。

## 5. 实验数量与充分性

- **实验数量**：
  - 功能级评估：在5个模型×2种设置（1-step/2-step）下分别报告Search和Edit的Precision、Recall、F1，共20组主要结果（表2）。
  - 端到端评估：生成了所有模型对的头部对比胜率矩阵（图3），并进行了维度级分析（图4）。
  - 人类验证实验：对100篇新闻文章生成3个候选（人类+两个模型），构建300对比较，剔除17个平局后保留283对，计算自动评判与人类的一致率。
  - 附加分析：工具使用统计（表3）和案例研究。
- **充分性与公平性**：
  - 覆盖了主流闭源和开源模型，且所有模型使用相同提示和动作接口，确保了比较的公平性。
  - 温度设为0以减少随机性，操作次数上限统一为20。
  - 数据时间与模型训练时间分离，避免记忆。
  - 功能级与端到端评估分离提供了双重诊断视角。
  - 但未进行消融实验（如去掉重写步骤、不同检索阈值等），也未评估不同agent框架（如仅用CoT或ToT）的影响。

## 6. 论文的主要结论与发现

- **代理选择的证据与人类记者存在显著差异**：功能级F1得分普遍较低（搜索F1最高0.233，编辑F1最高0.267），表明当前代理难以复制人类的证据选择策略。
- **闭源模型并非总是最优**：在端到端评估中，开源模型Qwen3-32B在新闻风格和重要性维度上表现突出，整体胜率超过GPT-4o；人类文章也并非胜率最高，说明对齐人类证据并不保证最终质量。
- **维度级分析揭示强弱项**：GPT-4o在可读性上占优，Qwen3-32B在新闻风格和重要性上胜出，人类文章在事实一致性和客观性上更有竞争力。
- **代理缺乏迭代修正能力**：在所有实验中，Remove操作从未被调用，表明代理几乎不进行自我纠正；2-step设置虽提高了搜索精度但降低了整体效率。

## 7. 优点

- **任务设计贴近现实**：将新闻写作建模为从部分素材出发、主动搜索背景、迭代修改的过程，比传统检索生成任务更符合记者实际工作流。
- **双层级评估体系**：功能级评估诊断证据选择行为，端到端评估衡量最终文章质量，两者互补，避免单一指标误导。
- **数据质量严格把控**：经过GPT-4分类和人工验证，并程序化确保提取的内容与原文逐字一致，保证了基准的可靠性。
- **评估协议经过人类验证**：维度式比较协议与人类判断的吻合度（72%）显著高于单轮评估（53%），提升了自动评估的可信度。
- **代码与数据开源**：提供了完整的基准资源，便于后续研究复现和扩展。

## 8. 不足与局限

- **数据覆盖有限**：仅使用英文、两个新闻源、一个狭窄时间窗口（2025年6月-7月），无法代表全球新闻生态的多样性。
- **简化了真实环境**：使用固定检索接口和严格相似度阈值，忽略了真实网络中的排序噪声、来源质量、时效性、可信度等问题。
- **重写阶段依赖单一模型**：虽然进行了可追溯性检查，但重写本身可能引入幻觉；论文未深入分析重写质量。
- **自动评判仍有偏差风险**：虽然进行了人类验证，但GPT-4作为判据可能对某些写作风格存在偏好，且验证样本量（100篇）相对有限。
- **未探索其他agent框架**：仅采用ReAct框架，未与CoT、ToT、Reflexion等更复杂的推理范式比较。
- **缺乏消融实验**：未单独分析搜索策略、编辑策略、重写步骤各自的贡献，也未研究不同操作预算的影响。
- **未涉及伦理讨论**：论文简要提及伦理考量（防止替代记者），但未深入探讨自动生成新闻可能带来的误导、抄袭或偏见风险。

（完）
