---
title: "SMART: Self-Aware Agent for Tool Overuse Mitigation"
title_zh: SMART：自我感知的智能体以减少工具过度使用
authors: "Cheng Qian, Emre Can Acikgoz, Hongru Wang, Xiusi Chen, Avirup Sil, Dilek Hakkani-Tur, Gokhan Tur, Heng Ji"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.239.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: 自我感知的智能体减少工具过度使用，适用于明智使用工具的CLI智能体
tldr: 当前LLM智能体缺乏自我意识，常过度依赖外部工具增加计算开销。受人类元认知启发，本文提出SMART范式提升智能体自我意识以优化任务处理并减少工具滥用。同时构建SMART-ER数据集，包含多领域推理步骤及何时使用工具的理性解释。实验表明SMART有效降低了工具调用频率，同时保持了任务性能。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.239/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 785, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.239/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 793, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.239/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 790, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.239/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 801, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.239/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1641, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.239/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 808, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.239/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1652, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.239/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 738, \"height\": 1068, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 803, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 800, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 799, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1651, \"height\": 1095, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1651, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 783, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 832, \"height\": 643, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 793, \"height\": 144, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 798, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1649, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.239/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 799, \"height\": 190, \"label\": \"Table\"}]"
motivation: LLM智能体缺乏自我意识导致不必要的工具过度使用。
method: 提出SMART范式，通过元认知增强智能体自我意识，优化任务处理。
result: 在多个领域数据集上，SMART减少了工具调用频率并维持了性能。
conclusion: 自我感知机制为构建高效、经济的智能体提供了新方向。
---

## Abstract
Current Large Language Model (LLM) agents demonstrate strong reasoning and tool use capabilities, but often lack self-awareness, failing to balance these approaches effectively. This imbalance leads to **Tool Overuse**, where models unnecessarily rely on external tools for tasks solvable with parametric knowledge, increasing computational overhead. Inspired by human metacognition, we introduce **SMART** (Strategic Model-Aware Reasoning with Tools), a paradigm that enhances an agent’s self-awareness to optimize task handling and reduce tool overuse. To support this paradigm, we introduce **SMART-ER**, a dataset spanning three domains, where reasoning alternates between parametric knowledge and tool-dependent steps, with each step enriched by rationales explaining when tools are necessary. Through supervised training, we develop **SMARTAgent**, a family of models that dynamically balance parametric knowledge and tool use. Evaluations show that SMARTAgent reduces tool use by 24% while improving performance by over 37%, enabling 7B-scale models to match its 70B counterpart and GPT-4. Additionally, SMARTAgent generalizes to out-of-distribution test data like GSM8K and MINTQA, maintaining accuracy with just one-fifth the tool calls. These highlight the potential of strategic tool use to enhance reasoning, mitigate overuse, and bridge the gap between model size and performance, advancing intelligent and resource-efficient agent designs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

当前大型语言模型（LLM）智能体虽然展现了强大的推理和工具使用能力，但普遍缺乏自我意识，无法有效平衡这两种方式。这种失衡导致**工具过度使用（Tool Overuse）**问题——模型在仅凭自身参数知识即可完成的任务上不必要地调用外部工具，增加了计算开销。受人类元认知（metacognition）启发，作者提出**SMART（Strategic Model-Aware Reasoning with Tools）范式**，旨在增强智能体的自我意识，使其能够识别自身知识边界，在适当时候依赖内在参数知识，从而优化任务处理并减少工具滥用。

## 2. 方法论

### 核心思想
通过数据驱动的方式校准智能体的决策边界，将人类元认知中隐含的“何时使用工具、何时依靠自身知识”的启发式策略转化为显式的语言推理步骤，引导模型发展出对自身知识边界的校准意识。

### 关键技术细节
- **SMART-ER数据集构建**：
  - 覆盖三个领域：Math（数学推理）、Time（时效性知识）、Intention（用户意图理解），每个问题都包含模型擅长和困难的子问题。
  - 将问题分解为原子子目标（subgoal），区分“参数知识驱动步骤”和“工具依赖步骤”。
  - 为每个子步骤提供显式的**合理性解释（justification）**，说明为何需要工具或为何不需要。
  - 工具集包括：Code（代码执行）、Search（实时搜索）、AskUser（询问用户）。

- **SMARTAgent训练**：
  - 采用监督微调（SFT），将SMART-ER训练集中的每个问题生成多个输入-输出对，让模型学会在推理链中交互调用工具并给出合理判断。
  - 基座模型包括Llama-3.1-8B/70B、Mistral-7B/12B(Nemo)/24B(Small)等。

### 算法流程
1. 对查询Q分解为子目标序列S={s1,...,sn}。
2. 用辅助模型M（GPT-4o）标注每个子目标是否需要工具（A(si)=1或0）。
3. 若A(si)=0，M基于参数知识推理得到ki；若A(si)=1，M生成工具参数pi，执行工具获取输出oi。
4. 为每一步生成合理性解释ji = M(si, A(si))，将隐含启发式转化为显式语言。
5. 合并所有步骤形成完整推理链R={(r1,j1),...,(rn,jn)}，用于训练SMARTAgent。

## 3. 实验设计

### 数据集/场景
- **域内测试**：SMART-ER测试集，包含Math（MATH改编）、Time（FreshQA改编）、Intention（IN3改编）。
- **域外测试（OOD）**：GSM8K（数学推理）、MINTQA（多跳问答，含新旧知识）。

### Benchmark与对比方法
- **正常推理训练**：仅用原始答案训练模型推理，不给工具。
- **基础模型推理提示**：直接让模型用思维链求解，不给工具。
- **基础模型工具提示**：给模型提供工具，让其自主决定是否使用。
- 对比闭源模型GPT-4o、GPT-4o-mini，以及多个开源基座模型。

### 评估指标
- **工具使用次数（Tool Used↓）**：平均每次查询调用工具次数。
- **准确率（Accuracy↑）**；对于Intention领域额外使用Missing Details Recovery和Summarized Intention Coverage。

## 4. 资源与算力

文中明确说明：使用**4块NVIDIA A40 GPU**进行训练，采用LoRA（秩16，Alpha 32，作用于所有层），序列长度4096 tokens，批大小每设备2，梯度累积4步，学习率1e-4，余弦调度，warmup比例0.1，训练3个epoch，精度bf16。每次评估间隔100步，使用1%数据验证。未提及训练总时长，但给出了详细的超参数表。

## 5. 实验数量与充分性

- **数量**：在3个域内数据集（每个400/100/100条测试样本）、2个OOD数据集（GSM8K全量、MINTQA随机10%）上进行评估。涉及5种开源基座模型（Mistral-7B, Llama-3.1-8B, Mistral-Nemo 12B, Mistral-Small 24B, Llama-3.1-70B）以及两个闭源模型（GPT-4o-mini, GPT-4o）作为对比。此外还进行了置信度验证实验（特殊token设计）、错误分析（表5）、案例研究（图7）、附加实验（AMC'23基准、DeepSeek-R1蒸馏模型）。

- **充分性与公平性**：
  - 对比了三种不同基线的变体（无工具、有工具、仅推理），且在同一基座模型上比较，控制变量较好。
  - 域内外测试覆盖了不同难度和知识类型，消融分析（错误分类、置信度）增强了结论可信度。
  - 但消融实验不够全面，例如未单独验证“合理性解释”组件的贡献、未做更细致的工具类型对比。域内测试样本量较小（Time和Intention各100条），可能存在随机波动风险。

## 6. 主要结论与发现

1. **SMARTAgent显著降低工具过度使用**：相比“基础模型工具提示”基线，平均工具使用次数减少**24%**，同时性能提升**超过37%**。

2. **小规模模型可匹敌大规模模型**：7B/8B的SMARTAgent在Time和Intention域上表现超过GPT-4o和70B模型，显示策略性工具使用可以弥合模型大小差距。

3. **良好泛化能力**：在OOD任务GSM8K和MINTQA上，SMARTAgent仅用五分之一的工具调用即保持或提升准确率。

4. **工具使用不当反而降低性能**：部分任务中过度或不当的工具调用会引入噪声，导致性能下降。

5. **自我意识校准**：通过logits置信度分析，SMARTAgent在工具选择时的决策更自信、更准确。

## 7. 优点

- **问题定义清晰**：首次明确定义“工具过度使用”并量化，注重资源效率与性能平衡。
- **方法创新**：引入元认知启发，将隐含的决策边界转化为显式语言推理，可解释性强、可操作性好。
- **数据构造精细**：SMART-ER数据集通过组合“模型擅长”和“模型困难”的子问题，有效模拟了真实世界中需要权衡的场景。
- **实验覆盖面较广**：多种基座模型、多个领域（数学、时效、意图）、域内外测试，展示了方法的鲁棒性和通用性。
- **资源效率高**：使用LoRA微调，计算成本可控，但在小模型上即获得显著提升，实用价值高。

## 8. 不足与局限

- **领域覆盖有限**：仅聚焦数学、时效知识、用户意图三个领域。LLM在长尾知识、专业领域知识等场景也存在工具需要，未纳入扩展。
- **样本量偏小**：域内测试的Time和Intention各仅100条，统计显著性可能不足；MINTQA仅取10%样本，可能存在偏差。
- **消融实验不够**：未单独剥离“合理性解释”、不同工具类型的影响，也未与基于阈值的动态调用方法（如Self-DC）对比。
- **工具集简化**：仅使用Code、Search、AskUser三种，现实中工具类型更丰富；且AskUser的后端由GPT-4o模拟，与真实用户交互可能有差距。
- **未能完全消除工具过度使用**：虽然大幅减少，但仍存在一定比率（如7-24%的查询仍有非必要调用），错误分析中“反馈忽视”和“过度谨慎”问题尚未根本解决。
- **对推理型模型（如DeepSeek-R1蒸馏版）的初步测试显示其倾向于“工具不足使用”，SMART方法虽可缓解，但未系统研究不同模型类型的适配性。

（完）
