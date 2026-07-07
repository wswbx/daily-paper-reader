---
title: "JTPRO: A Joint Tool–Prompt Reflective Optimization Framework for Language Agents"
title_zh: JTPRO：面向语言智能体的联合工具-提示反思优化框架
authors: "Sandip Ghoshal, Anshul Mittal, Jyotika Singh, Miguel Ballesteros, Weiyi Sun, Fang Tu, Shailender Singh, Yassine Benajiba, Fahad Shah, Sujeeth Bharadwaj, Sujith Ravi, Dan Roth"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.2017.pdf"
tags: ["query:cli-agent"]
score: 8.0
evidence: 联合优化工具提示和模式以提高工具调用可靠性
tldr: 针对大语言模型智能体在大规模工具场景下工具选择和参数填充错误频发的问题，JTPRO提出联合优化工具提示和模式的框架，通过 rollout 驱动的反思迭代改进提示质量和模式设计，实验表明该方法显著提升了工具调用准确率和任务成功率，尤其适用于具有大量工具的环境。
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 763, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1328, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1234, \"height\": 854, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1467, \"height\": 760, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1645, \"height\": 754, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1644, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1108, \"height\": 967, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1474, \"height\": 907, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1344, \"height\": 1070, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1570, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1454, \"height\": 825, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1491, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1337, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.2017/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1640, \"height\": 810, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2017/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2017/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1696, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2017/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1387, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2017/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1718, \"height\": 646, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2017/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 689, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.2017/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 582, \"height\": 452, \"label\": \"Table\"}]"
motivation: 工具描述模糊和指令不明确导致智能体工具选择和参数填充错误。
method: 提出JTPRO框架，通过 rollout 驱动的反思迭代联合优化工具提示和模式。
result: 实验证明JTPRO显著提高了工具调用可靠性，降低了错误率。
conclusion: JTPRO为语言智能体提供了有效的工具使用优化方法，可支持CLI命令调用。
---

## Abstract
Large language model (LLM) agents augmented with external tools often struggle as number of tools grow large and become domain-specific. In such settings, ambiguous tool descriptions and under-specified agent instructions frequently lead to tool mis-selection and incorrect slot/value instantiation. We hypothesize that this is due to two root causes: generic, one-size-fits-all prompts that ignore tool-specific nuances, and underspecified tool schemas that lack clear guidance on when and how to use each tool and how to format its parameters. We introduce Joint Tool-Prompt Reflective Optimization (JTPRO), a framework for improving tool-calling reliability in trace-supervised settings by iteratively using rollout-driven reflection to co-optimize global instructions and per-tool schema/argument descriptions for accurate tool selection and argument instantiation in large tool inventories. JTPRO is designed to preserve only tool-local cues needed for correct disambiguation and slot filling. We evaluate JTPRO across multi-tool benchmarks, which account for different number of tools using three metrics: Tool Selection Accuracy (TSA), Slot Filling Accuracy(SFA), and Overall Success Rate(OSR) (correct tool + correct slots + correct values). JTPRO consistently outperforms strong baselines, including CoT-style agents, and reflective prompt optimizers such as GEPA by 5%–20% (relative) on OSR. Ablations show that joint optimization of instructions and tool schemas is more effective and robust than optimizing either component in isolation.

---

## 论文详细总结（自动生成）

# 中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）智能体在接入大量外部工具时，由于工具描述模糊、指令不够具体，频繁出现工具误选（tool mis-selection）和参数插槽/值实例化错误（incorrect slot/value instantiation）。
- **根因**：一是通用化的“一刀切”提示词忽略了工具特异性；二是工具模式（schema）缺乏明确的使用时机、格式和参数约束。
- **研究动机**：在大型、领域特定的工具库中，可靠的工具调用需要同时正确的工具选择和准确的参数填充，但现有方法通常只优化全局指令或工具文档之一，忽略了二者耦合。
- **整体含义**：提出JTPRO框架，通过**联合优化全局指令与每个工具的模式描述**，在不微调模型参数的前提下，提升工具调用可靠性，尤其适合大规模工具清单场景。

---

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **联合优化**：同时优化（i）全局指令提示（P）和（ii）每个工具的模式/参数描述{T_i}，目标是端到端调用正确性（工具+插槽+值），无需模型微调。
- **反思驱动**：基于rollout执行反馈，诊断失败原因（工具混淆、缺失约束、格式/值错误），并有针对性地编辑P和关联工具描述。
- **控制增长与避免膨胀**：将重复出现的跨工具插槽语义（如日期/时间、数值边界、布尔参数、排序规则、货币单位）抽象为全局规则放入P，并在工具本地替换为简短指针，既减少冗余又保持一致性。

### 关键技术细节
1. **候选池与帕累托选择**：维护候选上下文池，保留在不同训练实例上最优的候选，剔除严格支配的候选项。
2. **Rollout-诊断-编辑循环**：
   - 对小批量训练集执行rollout，计算TSA、SFA、OSR指标；
   - 通过诊断函数提取结构化失败信号（如工具混淆、缺少必选参数、格式/值错误）；
   - 反射器（reflector）根据失败信号提出局部编辑（ΔP, {ΔT_i}），生成草稿上下文。
3. **合并与增量适应**：将草稿P_d与验证最优P*合并，保留稳定规则并吸纳新规则，支持工具集逐步扩展。
4. **全球化语义（Globalize Slots）**：识别并提升重复插槽约定到全局层，减少模式冗余，统一语义解释，同时保留工具特定的例外与消歧线索。
5. **算法流程**（Algorithm 1）：
   - 初始化P和{T_i}，最优上下文C*，候选池C；
   - 迭代（最多I次）：从池中帕累托选择候选，抽样小批量B，执行rollout并收集反馈，提出编辑，合并，全球化，评估，若改进则加入候选池并更新最优。

### 损失函数（式3）
综合工具选择、插槽填充和整体成功：
\[
L(\hat{\tau}, \tau) = \lambda_{TSA}(1 - I[\hat{t}=t]) + \lambda_{SFA} I[\hat{t}=t] (1 - Rec(\hat{a}, a)) + \lambda_{OSR}(1 - I[\hat{t}=t \land \hat{a}=a])
\]
其中\(I[·]\)为示性函数，\(Rec\)为插槽/值召回率，权重可调。

---

## 3. 实验设计：数据集、基准、对比方法

### 数据集（三个互补基准）
| 数据集 | 特点 | 工具数 | 参数平均 | 分割 | 备注 |
|--------|------|--------|----------|------|------|
| **ETID**（企业工具清单数据集，内部合成） | 复杂、领域特定的参数填充，中等工具规模 | 124个工具，平均3.4参数/工具 | 训练/验证/测试（低监督：每工具1/2/4例，测试404查询） | 适合评估参数正确性瓶颈 |
| **ToolACE**（工具缩放） | 评估工具选择随工具宇宙扩大的退化 | 300/500/750/1000变体 | 2.0~2.2参数/工具 | 固定：训练199，验证76，测试121 | 突出工具选择困难 |
| **SEAL-Tools**（多工具并行调用） | 一个查询需调用多个并行工具，参数同时填充 | 1138个工具，平均2.41参数/工具 | 训练600，验证100，测试100；每个查询平均3.2个工具调用 | 强调联合选择与填充 |

### 基准与对比方法
- **Baseline**：标准CoT风格智能体（静态提示+静态工具模式）。
- **GEPA**（Agrawal et al., 2025）：反射式提示优化器，只优化全局指令。
- **MIPRO**（Opsahl-Ong et al., 2024）：优化模块提示和演示。
- 还对比了不同基础LLM：GPT-4o mini、o3-mini、GPT-5。

### 评价指标
- **TSA**（工具选择准确率）：正确选择工具的比例。
- **SFA**（插槽填充准确率）：在工具正确的前提下，正确插槽/值的召回率。
- **OSR**（整体成功率）：工具正确 + 所有插槽/值正确。

---

## 4. 资源与算力

- **文中未明确说明GPU型号、数量或训练时长**。
- 提到使用o3-mini作为反射器（reflector）模型，所有实验设置温度参数为1，优化预算（滚动次数、批量大小等）与GEPA匹配。
- 属于权重无调整（weight-free）方法，仅优化上下文文本，不需要大规模模型训练资源，但多次rollout仍需要推理成本。具体算力细节缺失。

---

## 5. 实验数量与充分性

### 实验数量
- **三大基准**：ETID（低监督3个训练规模×3模型~9组）、ToolACE（2个工具数×4模型~8组）、SEAL-Tools（3模型~3组），合计约20组主要对比。
- **消融实验**：单独优化指令 vs. 单独优化模式 vs. 联合优化（文中提到联合更优，但未给出详细表格，仅在正文陈述）。
- **额外分析**：工具描述消歧量化（余弦相似度变化）、实例级别修正统计、收敛曲线等。

### 充分性评价
- **优点**：覆盖了单工具、工具缩放、并行多工具三种典型场景，测试了不同基础模型（3种）和不同监督程度，实验设计较为全面。
- **客观性**：报告了多次独立运行的平均值（文中说明5-10次），使用相同优化预算，对比GEPA和基线。
- **不足**：缺少对**序列多工具调用**（需长期规划）的评估，也未包含嵌套参数结构或工具执行后响应验证。ETID为内部数据集未公开，可能影响外部复现。

---

## 6. 论文的主要结论与发现

1. **联合优化显著优于单独优化**：共同调整全局指令和工具模式能带来更高的OSR，消融显示单独优化任一部分都不如联合优化。
2. **参数填充是端到端成功的主要瓶颈**：尤其在ETID上，基线TSA已经很高（85-94%），但OSR远低（44-54%），JTPRO通过改进SFA（从~70%提升到~85%+）带来OSR大幅提升（+15-20个点）。
3. **在工具缩放和大规模多工具场景中也有效**：ToolACE上JTPRO的OSR提升主要来自更好的工具选择（TSA），而SFA本身已较高；SEAL-Tools上则同时提升选择和填充。
4. **工具描述消歧**：JTPRO修改了ToolACE-500中11%的工具描述，增加了偏好信号、负约束等，使得相似工具组的余弦相似度下降（如get_ip_*组从0.668降至0.502）。
5. **全球化槽语义减少冗余**：通过将重复参数规则抽象到全局指令，减少了模式文本冗余，同时保持一致性。
6. **收敛快速**：验证OSR在早期迭代快速上升，后期小幅精调。

---

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次明确将工具选择与参数填充的耦合作为核心问题，并设计联合优化框架，不同于以往仅优化提示或仅优化文档的方法。
- **实用性**：无需模型微调，只通过上下文文本调整，适应于工具清单频繁变化的生产环境，支持增量扩展。
- **可解释性**：使用结构化文本反馈（诊断信号、局部编辑）而不是标量奖励，编辑过程可追溯。
- **控制膨胀机制**：通过全球化重复语义避免上下文过长，同时保留工具本地特异性。
- **评估指标合理**：TSA、SFA、OSR分别捕捉不同阶段的错误，且强调条件概率（SFA|TSA），准确反映瓶颈。
- **实验设计全面**：覆盖三种典型工具调用场景（单工具、工具缩放、并行多工具），对比强基线（GEPA、MIPRO）。

---

## 8. 不足与局限

- **未覆盖序列多工具调用**：论文明确指出未评估需要长期规划、中间状态依赖的链式工具调用，这是真实场景常见需求。
- **未评估工具实际执行响应**：只检查调用级别正确性，未考虑工具后端返回错误或业务逻辑约束导致的后续失败。
- **嵌套参数结构缺失**：未系统性测试深层JSON对象、列表对象、依赖组合等复杂参数场景，未来需要嵌套槽正确性指标。
- **ETID未开源**：影响外部复现和社区基准比较。
- **基准覆盖有限**：仅使用三个基准（其中一个内部），未包含BFCL（因工具定义不稳定）和τ-bench（工具集太小），通用性需更多验证。
- **算力细节缺失**：未报告GPU型号、数量、训练时长，读者难以估计资源需求。
- **消融实验详细数据不足**：文中仅文字陈述联合优化优于单独优化，未给出具体表格。
- **潜在偏差**：合成数据集ETID可能无法完全反映真实企业环境中的分布，工具重叠模式由人工设定，可能引入特定偏差。

---

（完）
