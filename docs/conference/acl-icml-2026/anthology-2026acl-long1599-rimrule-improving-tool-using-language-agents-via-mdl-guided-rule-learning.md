---
title: "RIMRULE: Improving Tool-Using Language Agents via MDL-Guided Rule Learning"
title_zh: RIMRULE：通过MDL引导的规则学习改进使用工具的LLM代理
authors: "Xiang Gao, Yuguang Yao, Qi Zhang, Kaiwen Dong, Avinash Baidya, Ruocheng Guo, Hilaf Hasson, Kamalika Das"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.acl-long.1599.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: 通过规则学习改进使用工具的LLM代理，可应用于CLI代理
tldr: 本文针对LLM在领域特定工具使用中不可靠的问题，提出RIMRULE方法：从失败轨迹中提取简洁可解释规则，通过最小描述长度（MDL）目标进行合并，并在推理时动态注入提示中。规则以自然语言和结构化符号形式存储，支持高效检索。实验表明该方法在多个工具使用任务上显著提升性能，尤其适用于API文档不完善的场景。
source: ACL-2026-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1599/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 691, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-long/anthology-2026.acl-long.1599/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1573, \"height\": 668, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1599/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 725, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1599/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1201, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1599/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1119, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1599/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1162, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1599/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1176, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1599/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 847, \"height\": 720, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1599/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 585, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-long/anthology-2026.acl-long.1599/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 544, \"height\": 208, \"label\": \"Table\"}]"
motivation: LLM在领域特定工具API使用中常因文档不足而不可靠。
method: RIMRULE采用神经符号方法，从失败轨迹蒸馏规则，用MDL目标优化并动态注入提示。
result: 在多个工具使用数据集上，RIMRULE显著提高了任务成功率。
conclusion: 为LLM适应工具提供了一种高效、可解释的规则学习框架。
---

## Abstract
Large language models (LLMs) often struggle to use tools reliably in domain-specific settings, where APIs may be idiosyncratic, under-documented, or tailored to private workflows. This highlights the need for effective adaptation to task-specific tools. We propose RIMRULE, a neuro-symbolic approach for LLM adaptation based on dynamic rule injection. Compact, interpretable rules are distilled from failure traces and injected into the prompt during inference to improve task performance. These rules are proposed by the LLM itself and consolidated using a Minimum Description Length (MDL) objective that favors generality and conciseness. Each rule is stored in both natural language and a structured symbolic form, supporting efficient retrieval at inference time. Experiments on tool-use benchmarks show that this approach improves accuracy on both seen and unseen tools without modifying LLM weights. It outperforms prompting-based adaptation methods and complements finetuning, offering an interpretable layer of inference-time generalization. Moreover, rules learned from one LLM can be reused to improve others, including long reasoning LLMs, highlighting the portability of symbolic knowledge across architectures.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的结构化、深入且客观的中文总结。

### 论文核心问题与整体含义（研究动机和背景）

*   **核心问题**：大型语言模型（LLM）在领域特定的工具使用场景中表现不可靠，尤其是当API文档不完善、功能特殊或针对私有工作流时。传统的模型适应方法（如少样本学习、全局提示优化、模型微调）在**抽象性、可重用性和可解释性**方面存在不足。
*   **研究动机**：受人类从经验中学习（试错、压缩经验为启发式规则）的启发，论文探索一种新的LLM适应范式——将适应过程外部化为可解释的规则，而非存储在内隐的模型权重中。
*   **整体含义**：旨在探索一种模块化、可解释的LLM适应方法，使其能更有效地处理领域专用工具，同时知识（规则）能够在不同模型间轻松共享和重用。

### 论文提出的方法论：核心思想、关键技术细节

*   **核心思想**：RIMRULE（Reusable, Interpretable, and MDL-guided Rules）是一种神经符号方法。它从LLM代理的失败执行轨迹中，自动提炼出简洁、可解释的规则，并在推理时动态注入到模型提示中，以纠正相似错误。
*   **关键技术细节（两阶段流程）**：
    1.  **局部规则生成**：
        *   **经验收集**：让LLM代理在训练集上运行，记录所有导致错误或不完整结果的执行轨迹。
        *   **基于解释的规则生成（EBL）**：将失败轨迹与正确轨迹对比，让LLM（作为“规则生成器”）识别根本原因，并生成一个抽象的、可重用的“如果-那么”规则。规则被分为**分解（dec）**、**工具选择（sel）** 或**参数构建（arg）** 三类。
        *   **符号化表示**：为了便于合并和检索，每条自然语言规则被转换成包含五个固定语义字段（领域、限定符、动作、强度、工具类别）的符号化形式，词汇来源于一个由LLM构建的封闭集合。
    2.  **基于最小描述长度（MDL）的全局规则合并**：
        *   **动机**：直接生成的规则池庞大、冗余且过度具体。
        *   **MDL目标函数**：目标是找到一个紧凑的规则子集 **H**，能最大化地修正训练失败案例，同时最小化规则本身的复杂度。其目标函数为 **MDL(H) = L(H) + L(D|H)**。
            *   **模型代价 L(H)**：衡量规则库的复杂度，与规则符号化后的总长度成正比（正则化项，由超参数 α 控制）。
            *   **数据代价 L(D|H)**：衡量规则库修正失败案例的效果，由修正成功的案例数量决定。
        *   **贪心合并算法**：从完整规则池开始，通过评估“剪枝”和“泛化”等局部编辑操作对MDL目标的改善，逐步减少规则数量，提高规则的普适性。

### 实验设计

*   **数据集**：
    *   **ToolHop**：包含需要多步推理的组合型多轮查询。
    *   **BFCL (Berkeley Function Calling Leaderboard)**：包含**Live-Multiple**（单步、工具选择多样）和**Multi-Turn-Base**（小样本）子集。
*   **数据集划分**：
    *   **Test-Rand**：随机划分的测试集，用于评估**分布内**性能。
    *   **Test-Unseen**：包含训练中未见工具的测试集，用于评估**分布外**（OOD）泛化能力。
*   **对比方法 / 基准**：
    *   **零样本 (Zero-shot)**：基线方法。
    *   **少样本学习 (Few-shot)**：通过语义相似度检索示例。
    *   **提示优化 (SEE)**：全局优化指令和示例。
    *   **监督微调 (SFT)**：使用LoRA对开源模型进行微调。
    *   **原生函数调用模型 (Function Calling Model)**：针对特定任务微调过的闭源模型。
*   **评估模型**：
    *   Llama3.2, Llama4, GPT-4o, O1（代表不同规模和推理能力的模型）。
*   **评估指标**：
    *   准确率 (Accuracy，含标准差) 和最终规则数量。

### 资源与算力

*   **论文未明确说明**使用了多少GPU型号、数量或训练时长。由于该方法不涉及模型权重微调，其主要算力消耗可能集中在规则生成（调用LLM作为生成器）、符号化翻译和MDL合并的评估上。根据其“在候选规则池上线性扩展”的描述，其计算资源需求相对于大规模训练来说应该是较小的。

### 实验数量与充分性

*   **实验数量与覆盖度**：论文进行了多组系统性实验，覆盖了：
    *   **主实验**：在ToolHop和BFCL两个数据集上验证了该方法从初始到合并的学习过程。
    *   **跨模型复用实验**：将从一个LLM（如Llama3.2）学到的规则应用于另一个LLM（如GPT-4o, O1），并展示了**双向**的泛化能力（强-弱，弱-强）。
    *   **与现有方法对比**：与少样本学习、提示优化方法进行了对比。
    *   **与微调模型互补性实验**：将规则应用于微调后的模型，验证其能带来额外提升。
    *   **小样本场景实验**：在仅90个样本的BFCL子集上验证了方法的数据高效性。
    *   **消融实验**：对比了不同的**检索策略**（自然语言 vs. 符号化检索）和**合并策略**（Prompt-based vs. MDL-guided）。
*   **充分性与公平性**：
    *   **充分性**：实验设计较为全面，不仅评估了标准性能，还深入探讨了泛化性（OOD）、可迁移性、数据效率以及与微调的互补性，论证充分。
    *   **客观性**：实验呈现了带有标准差的准确率，并使用多种模型（开源、闭源、不同规模）进行对比，提升了结论的可靠性。与多种主流方法（少样本、提示优化、微调）的对比也体现了公平性。
    *   **公平性**：所有方法（包括RIMRULE）都使用了相同的ReAct提示框架，控制变量，确保了对比的公平。规则是由失败模型自身生成的，避免了使用外部知识。

### 论文的主要结论与发现

1.  **性能提升**：RIMRULE的规则注入法在**分布内（Test-Rand）** 和**分布外（Test-Unseen）** 场景中均能显著提升LLM代理的工具使用性能。
2.  **规则可迁移性**：从一个LLM（无论是弱模型还是强模型）学到的符号规则可以有效地**迁移**到另一个LLM上，无需重新训练，这证明了符号知识的可移植性。
3.  **数据高效**：在非常小的训练数据集（90个样本）上，该方法仍能学习到少量高价值规则并带来显著提升。
4.  **方法论优势**：RIMRULE在性能上**显著优于**基于提示的适应方法（如少样本学习、提示优化）。
5.  **与微调互补**：将RIMRULE应用于经过微调的模型可以**带来额外的性能增益**，表明规则学习提供了一条与参数微调正交的泛化轴。
6.  **核心组件有效**：通过消融实验证明了**符号化检索策略**和**MDL引导的合并策略**是该方法成功的关键。

### 优点

*   **可解释性**：生成的规则是“如果-那么”形式的自然语言和结构化符号，易于人类理解和审计。
*   **可移植性**：学习的知识（规则）与模型解耦，可以像“经验手册”一样在不同模型间轻松共享和复用。
*   **与微调互补**：提供了一条与参数微调相互正交、可以叠加的泛化路径。
*   **数据高效且不修改权重**：无需昂贵的重新训练，也能解决系统的错误模式，处理OOD样本。
*   **方法严谨**：采用MDL原则对候选规则进行优化，避免了过度拟合和冗余，是一个理论驱动的合并策略。

### 不足与局限

*   **对失败信号的依赖**：方法假设在训练时能访问到失败信号（如执行轨迹或性能反馈），这在某些完全黑盒或无法获得反馈的部署场景中可能不成立。
*   **贪心合并的非最优性**：使用的MDL合并是贪心算法，不保证能找到全局最优的规则子集，未来可能需要更复杂的优化策略。
*   **符号模式的领域依赖性**：当前使用的五字段符号模式是为自然语言工具使用任务设计的，可能不适用于所有领域，其他领域可能需要设计不同的符号抽象。
*   **规则质量依赖故障多样性**：生成规则的有效性很大程度上取决于观察到的失败的**质量和多样性**。如果错误模式稀疏或高度特化，规则的增益可能会减小。
*   **潜在的过度泛化风险**：学习到的规则如果在其预期范围之外应用，可能会过度泛化或反映训练数据中的偏见。虽然可解释性提供了审计的可能，但在高风险场景中仍需人工介入。
*   **实验规模与重复性**：论文未明确说明规则生成和合并过程中的计算资源消耗，这可能会影响其他研究者的重复。同时，实验仅在两个基准上（ToolHop, BFCL）进行，其在不同领域（如代码生成、机器人控制）的泛化性有待验证。

（完）
