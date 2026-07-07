---
title: "Safety Sidecar: Reflection-Driven Runtime Control for Safer Agents"
title_zh: 安全边车：基于反射的运行时控制实现更安全的代理
authors: "Wang Bin, Quan Jiazheng, Xingrui Yu, Hu Hansen, Yu Hao, Anjun Gao, Zhenglin Wan, Hui LI, Ivor Tsang"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.1542.pdf"
tags: ["query:cli-agent"]
score: 5.0
evidence: LLM代理的运行时安全控制，可应用于CLI代理
tldr: 本文针对LLM代理在复杂环境中安全脆弱的挑战，提出Safety Sidecar模块。该模块采用模型无关的即插即用设计，通过反射机制作为闭环控制器，动态监控决策轨迹，从反射记忆中检索证据修补示例，并强制执行安全约束。实验表明Safety Sidecar能有效降低有害动作发生率，同时保持任务性能，为代理安全部署提供了标准化解决方案。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1542/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1657, \"height\": 901, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.1542/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 767, \"height\": 590, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1482, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 651, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 608, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 733, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 781, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 747, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 732, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1660, \"height\": 1202, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1655, \"height\": 683, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1524, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.1542/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 742, \"height\": 187, \"label\": \"Table\"}]"
motivation: LLM代理的微小错误可能放大为危险行为，现有防御缺乏运行时干预。
method: Safety Sidecar通过反射闭环控制器动态监控、检索并强制安全约束。
result: 在多个代理任务上减少了有害动作，且不影响任务成功率。
conclusion: 为LLM代理提供了标准化的运行时安全保障。
---

## Abstract
Autonomous LLM agents are increasingly deployed in complex environments as tool-using systems. However, their safety remains fragile, as minor reasoning or retrieval errors can be amplified into hazardous actions within the agentic workflow. Existing defenses, often limited to static prompts or post-hoc guardrails, fail to provide runtime intervention or cross-architecture portability. In this paper, we propose Safety Sidecar , a model-agnostic, plug-and-play module designed to provide standardized runtime safety control and auditability for arbitrary agent workflows. Safety Sidecar operationalizes reflection as a closed-loop controller: it dynamically monitors decision traces, retrieves evidence-based repair exemplars from a reflective memory, and enforces risk-mitigating revisions before execution. Crucially, it employs external verifiers to gate both action release and memory updates, producing a transparent, auditable trail of retrieved evidence and applied constraints.We instantiate and systematically evaluate Safety Sidecar in secure code generation—a high-stakes domain with objective vulnerability signals. Experimental results across eight CWE scenarios and four representative LLMs demonstrate that Safety Sidecar consistently improves the secure-solution rate by 2.9–11.2 percentage points while maintaining competitive functional correctness. Efficiency analysis shows the framework is practical for deployment, with reflection adding only 3.2s to end-to-end latency and a negligible average cost of 5.37 × 10 -4 per scenario. Our findings position Safety Sidecar as a portable and efficient control layer for enhancing the safety, compliance, and auditability of LLM-based agents.

---

## 论文详细总结（自动生成）

# 论文总结：Safety Sidecar: Reflection-Driven Runtime Control for Safer Agents

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：自主 LLM 代理在复杂环境中执行多步骤任务时，微小的推理或检索错误可能被放大的危险行为（如不安全工具调用、外部状态修改），而现有防御（静态提示、事后过滤）缺乏运行时干预能力，也难以跨架构移植。
- **整体含义**：需要一种**标准化、即插即用、运行时**的安全控制机制，在动作执行前进行检测与修正，并提供可审计的决策证据，从而提升 LLM 代理的安全性与可信度。

## 2. 方法论：核心思想、关键技术细节与流程

### 核心思想
- 将**反射**作为闭环控制器：在代理的决策-动作循环中插入一个控制回路，实现“风险检测 → 反射修复 → 验证 → 记忆更新”的闭环。

### 关键技术细节
- **三个核心组件**：
  1. **轻量级自检器（Lightweight Self-Checker）**：基于 LLM 的二元路由（SAFE/UNSAFE），仅做初步筛选，低风险输出直接通过，高风险输出触发完整修复流程。
  2. **反射提示引擎（Reflective Prompt Engine）**：构造多轮链式思考提示，引导模型进行漏洞识别、原因分析、安全替代方案生成和代码修订。
  3. **反射记忆库（Reflective Memory Repository）**：分为动态记忆（向量数据库存储已验证修复案例）和静态记忆（安全编码标准等先验知识）。采用分层检索策略：优先从动态记忆检索高相似度案例，不足时回退至静态记忆。

### 算法流程（文字说明）
- 输入代码 x 和上下文 c；
- 轻量级自检器给出判定：若 SAFE，直接输出并存入动态记忆；若 UNSAFE，从记忆库检索相关修复经验 E 和安全约束 K，构造结构化反射提示 Φ；
- 模型在 Φ 指导下生成修复输出 y；
- 外部验证器（编译检查、静态分析工具如 CodeQL）验证 y：若通过，输出并写入动态记忆；否则标记为 PENDING 或进一步处理。

## 3. 实验设计：数据集、Benchmark 与对比方法

### 数据集 / 场景
- 基于 He & Vechev (2023) 的数据集，包含 **8 个 CWE 场景**（来自 MITRE Top 25）：
  - 内存安全类：CWE-125（越界读）、CWE-787（越界写）、CWE-476（空指针解引用）、CWE-416（释放后使用）、CWE-190（整数溢出）
  - 逻辑与注入类：CWE-089（SQL 注入）、CWE-079（XSS）、CWE-022（路径遍历）
- 每个场景包含 2-3 个编程环境，C/C++ 和 Python 混合。

### Benchmark 与方法对比
- **基线与改进**：在 4 个代表性 LLM 上测试：`gpt-3.5-turbo`、`gpt-4o`、`qwen3-coder-plus`、`gemini-2.5-pro`。
- 对比设置：**Base**（原始模型） vs **Base + Safety Sidecar**。
- 额外跨域评估：HotpotQA（多跳问答）验证泛化性。

### 评估指标
- **定量**：安全率（Sec.Rate，仅对可编译样本计算）、通过率（Pass Rate）、编译样本数、未解决数等。
- **定性**：代码质量、安全完备性、合规性（人工审查）。

## 4. 资源与算力

- **未明确说明 GPU 型号、数量或训练时长**：因为 Safety Sidecar 不需要微调模型，仅使用冻结 LLM 进行推理。
- **成本与延迟**：
  - 货币成本：平均每个场景 5.37×10⁻⁴ 美元（基于 GPT-4o 定价），总计 125 个场景约 0.067 美元。
  - 延迟：反射阶段仅增加 3.2 秒，总端到端延迟约 28.8 秒（以 LLM 推理 24.3 秒为主）。

## 5. 实验数量与充分性

- **实验规模**：
  - 每组 25 个代码样本，5 次独立运行 → 每个模型每场景 125 个样本，4 个模型×8 场景 ≈ 4000 次生成。
  - 跨域实验在 HotpotQA 上同样进行完整比较。
- **消融实验**：分别移除动态记忆库和轻量级自检器，分析每个组件的贡献。
- **反射深度分析**：测试不同迭代轮次（Run1-5）对安全率和检索质量的影响。
- **充分性评价**：
  - 实验覆盖了多种模型、多种漏洞类型、多个运行随机种子，统计稳健。
  - 但主要局限于 **代码生成** 领域，跨域验证仅一个问答任务，泛化性证据有限。
  - 对比基线只有原始模型，未与其他运行时安全方法（如 Guardrails、监测过滤器）比较。

## 6. 主要结论与发现

1. **安全提升显著**：Sidecar 使各模型的安全率提升 2.9~11.2 个百分点，且将不同模型拉至 94.9%~97.1% 的同等高水平。
2. **功能保持**：通过率（正确性）基本持平或略有下降，但总体可接受。
3. **反射深度**：**单轮反射已足够**捕获约 90% 的关键修复模式；多轮（约 4 轮）用于预热记忆库，但后续可能过度修正。
4. **检索质量与修复效果正相关**：相似度 >0.70 时修复准确率 >93.8%，>0.95 时达 100%。
5. **低成本**：反射增加延迟仅 11.1%，经济成本极低。

## 7. 优点（方法与实验亮点）

- **模型无关即插即用**：无需修改模型参数或代理规划逻辑，仅需拦截输出通道，易于集成。
- **运行时干预**：在动作执行前进行检测与修复，比事后过滤更安全。
- **可审计性**：外部验证器决策和记忆更新均记录证据链，支持透明追溯。
- **轻量级路由设计**：自检器减少不必要计算，验证器确保安全决定权。
- **跨域初步验证**：在 HotpotQA 上也显示提升（EM+2%，F1+2.36%），表明潜在泛化能力。
- **实验充分性**：多模型、多漏洞、多随机运行，统计分析可信。

## 8. 不足与局限

- **领域覆盖面窄**：主要验证在安全代码生成，其他代理任务（如 Web 浏览、机器人规划）仅尝试一个问答任务，泛化力需要更多证据。
- **未与现有运行时防御系统对比**：例如 Guardrails、Interceptors 等，缺乏横向比较。
- **成本/延迟在极低延迟场景可能受限**：即使 3.2 秒反射，对于实时控制任务仍可能过高。
- **未考虑自适应攻击者**：论文假设“良性但易错”的代理，未评估攻击者针对 Sidecar 本身（如 prompt injection 污染记忆库）的鲁棒性。
- **跨模型表现高度依赖验证器**：若验证器（如 CodeQL）无法检测的漏洞，Sidecar 无法覆盖。
- **未消融静态记忆 vs 动态记忆的具体贡献**：仅整体移除记忆库，未区分层。

（完）
