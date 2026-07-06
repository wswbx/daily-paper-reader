---
title: "MARS: Multi-Agent Adaptive Reasoning with Socratic Guidance for Automated Prompt Optimization"
title_zh: MARS：基于苏格拉底引导的多智能体自适应推理自动提示优化
authors: "Jian Zhang, Zhangqi Wang, Haiping Zhu, Kangda Cheng, Kai He, Bo Li, Qika Lin, Jun Liu, Erik Cambria"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38668/42630"
tags: ["query:cli-agent"]
score: 4.0
evidence: 多智能体提示优化系统，与智能体自动化相关
tldr: 本文提出MARS框架，利用五个互补智能体将自动提示优化建模为部分可观测马尔可夫决策过程，通过苏格拉底式引导进行自适应推理。MARS克服了现有方法模板僵化、探索低效的问题，在多个LLM任务上提升了提示质量。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有自动提示优化方法受限于固定模板和低效搜索，需要更灵活的框架。
method: 提出MARS，包含五个智能体，将优化过程形式化为POMDP，通过显式状态建模实现自适应提示调整。
result: 在多个自然语言处理任务上，MARS生成的提示优于现有自动优化方法。
conclusion: 多智能体协同与POMDP建模为提示优化提供了有效方案。
---

## Abstract
Large language models (LLMs) typically operate in a question-answering paradigm, where the quality of the input prompt critically affects the response. Automated Prompt Optimization (APO) aims to overcome the cognitive biases of manually crafted prompts and explore a broader prompt design space. However, existing APO methods often suffer from rigid template structures and inefficient exploration in the prompt space. To this end, we propose a Multi-Agent Adaptive Reasoning with Socratic guidance framework (MARS) for APO. MARS consists of five complementary agents and formulates the optimization process as a Partially Observable Markov Decision Process (POMDP), enabling adaptive prompt refinement through explicit state modeling and interactive feedback. Specifically, a Planner agent generates flexible optimization trajectories, a Teacher-Critic-Student triad engages in Socratic-style dialogue to iteratively optimize the prompt based on pseudo-gradient signals in the text space, and a Target agent executes the prompt in downstream tasks to provide performance feedback. MARS integrates reasoning, feedback, and state transition into a unified hidden-state evolution process, improving both the effectiveness and interpretability of optimization. Extensive experiments on multiple datasets demonstrate that MARS outperforms existing APO methods in terms of optimization performance, search efficiency, and interpretability.

---

## 论文详细总结（自动生成）

# MARS：基于苏格拉底引导的多智能体自适应推理自动提示优化 - 详细中文学术总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大语言模型（LLM）的性能高度依赖于输入提示（prompt）的质量。自动提示优化（Automated Prompt Optimization, APO）旨在克服人工设计提示的认知偏差，探索更广阔的提示设计空间。
- **核心问题**：现有APO方法存在两大局限：
  - **模板僵硬**：基于元提示（meta-prompt）的方法使用固定优化模板，无法动态适配不同任务，导致引入偏差或丢失任务特定信息。
  - **探索低效**：基于生成-搜索（generate-search）的方法仅在初始候选附近局部搜索，容易过早收敛或遗漏更优prompt，提示空间覆盖率不足。
- **整体含义**：本文提出MARS框架，通过多智能体协作与部分可观测马尔可夫决策过程（POMDP）建模，将APO转化为结构化、可解释、自适应的优化过程，同时提升优化效果、效率与可解释性。

## 2. 论文提出的方法论

### 2.1 核心思想
- 构建五个互补的LLM智能体（Planner、Teacher、Critic、Student、Target），将APO形式化为POMDP。
- 优化过程被建模为隐藏状态（Student内部推理状态）的演化，通过智能体间的苏格拉底式对话（Socratic dialogue）模拟伪梯度信号，实现离散文本空间中prompt的迭代精炼。

### 2.2 关键技术细节

#### (1) POMDP建模
- **状态空间S**：Student agent的潜在推理状态。
- **动作空间A**：Teacher和Critic发出的指令信号（如问题、批评）。
- **转移函数T**：S × A → S，更新学生状态。
- **观测函数O**：S → P，将隐藏状态映射为prompt。
- **奖励函数R**：基于Target agent在下游任务上的性能（如准确率）。

#### (2) Planner智能体
- 根据任务目标、输入样本和初始prompt，生成一系列子目标（sub-goal）轨迹 \( ST = [st_1, st_2, \dots, st_n] \)。
- 通过潜在规划变量 \( z \) 建模任务语义，使轨迹生成具有全局一致性，避免固定模板的僵化。

#### (3) Teacher-Critic-Student苏格拉底对话机制
- **Teacher**：针对当前子目标和历史prompt，提出苏格拉底式问题 \( q_i \)，引导推理方向。
- **Critic**：评估问题质量（清晰度、相关性、一致性），输出反馈 \( c_i \)；若不如意，Teacher可修订直至满意。
- **Student**：综合\( (q_i, c_i) \)和历史prompt，更新自身状态并生成新prompt \( p_i \)。
- 每个智能体均考虑对话历史 \( H_{<i} \)，实现记忆式推理。
- 联合优化目标：最大化累计奖励 \( R(\Pi) \) 并最小化语义漂移损失 \( L_{align} \)。

#### (4) Target评估与自适应终止
- 最终prompt由Target agent在测试集上评估，获得奖励 \( R^{(t)} \)。
- 若奖励增益 \( \Delta R^{(t)} < \delta \)（阈值0.01）或达到最大迭代 \( I=10 \)，则提前停止，避免过度精炼。

### 2.3 算法流程（文字说明）
1. Planner生成子目标轨迹 \( ST \)。
2. 对每次迭代 \( t \)：
   - 对每个子目标 \( st_i \)：
     - Teacher生成问题 → Critic评估并反馈 → 循环直至满意 → Student更新prompt。
   - 最终prompt在测试集上由Target评估获得奖励。
3. 若奖励增益小于阈值或达到最大迭代，终止并返回最优prompt。

## 3. 实验设计

### 3.1 数据集与场景
- **通用任务**（12个）：
  - Big-Bench Hard (BBH) 中6个子任务：Boolean Expressions, Dyck Languages, Formal Fallacies, Geometric Shapes, Ruin Names, Sports Understanding。
  - MMLU中6个子任务：College Biology, College Medicine, Electrical Engineering, World History, High School Anatomy, Machine Learning。
- **领域特定任务**（5个）：
  - 中文领域：C-Eval中的3个子任务（Accounting, University Physics, College Mathematics）。
  - 法律领域：LSAT-AR。
  - 数学领域：GSM8K。

### 3.2 基准方法（Baselines）
- **Origin**：原始提示（无优化）。
- **CoT(ZS)**：零样本思维链。
- **CoT(FS)**：少样本思维链。
- **APE** (Zhou et al., 2022)
- **ProTeGi** (Pryzant et al., 2023)
- **OPRO** (Yang et al., 2024)
- **PE2** (Ye et al., 2023)

### 3.3 对比方式
- 主实验：在12个通用任务和5个领域任务上对比所有方法，采用准确率（Accuracy）作为指标。
- 效率分析：绘制推理时间计算成本（输出token数）与平均性能的关系曲线。
- 消融实验：分别移除Planner、Socratic模块、Critic，观察性能变化。
- 收敛分析：在4个BBH任务上绘制迭代过程中的奖励曲线，与OPRO等对比。
- 跨模型泛化：将MARS优化后的prompt迁移到Deepseek-R1、GPT-3.5、GPT-4、GPT-4o上进行评估。

## 4. 资源与算力

- **主骨干LLM**：deepseek-v2.5-1210，设置生成温度0.6，最大迭代 \( I=10 \)，早停阈值 \( \delta=0.01 \)。
- **评估模型**：除主骨干外，跨模型泛化实验中使用了Deepseek-R1、GPT-3.5、GPT-4、GPT-4o。
- **未明确说明**：论文未提及具体使用的GPU型号、数量及训练时长等算力资源细节。实验可能基于API调用或自有集群完成，但未披露。

## 5. 实验数量与充分性

- **主实验**：两大表（表1：12通用任务；表2：5领域任务），涵盖多样场景，所有对比方法均在同一设置下评估，统计结果清晰。
- **消融实验**：表3在6个BBH任务上测试了移除Planner、Socratic模块、Critic的效果，验证了各组件贡献。
- **收敛分析**：图6在4个BBH任务上展示了MARS与4种对比方法迭代过程，证明收敛更快。
- **效率分析**：图5展示推理时间效率，MARS在相同计算成本下性能最高。
- **跨模型泛化**：表4在5种不同Target LLM上测试，验证模型无关性。
- **充分性评价**：实验覆盖通用与领域任务、不同类型baseline、多角度分析（消融、收敛、效率、泛化），设计严谨，对比公平，结论可信。

## 6. 论文的主要结论与发现

- MARS在所有12个通用任务和5个领域任务上均优于所有对比方法，通用任务平均性能提升6.04%以上，领域任务提升6.42%以上。
- 在效率方面，MARS以更少的输出token达到更高性能（图5），推理时间缩放定律表现最佳。
- 消融实验表明，苏格拉底对话机制贡献最大（移除后平均下降11.31%），Planner次之（-6.77%），Critic不可或缺（-3.55%）。
- 收敛分析显示，MARS通常在5-6次迭代内达到最优，而对比方法如OPRO在10次后仍未收敛。
- 跨模型泛化表现优异，在Deepseek-R1、GPT-4o等不同模型上仍保持高收益。
- 理论证明（命题1、命题2）支持了苏格拉底策略改进边界和单调奖励稳定性。

## 7. 优点

- **创新性**：首次将多智能体协作与POMDP结合用于APO，突破固定模板和局部搜索的局限。
- **可解释性**：苏格拉底对话机制提供了透明的推理链，每一步都有明确问题、批评和响应，便于调试和理解。
- **自适应性**：Planner生成任务特定轨迹，避免“一刀切”模板；早期停止机制根据性能自动终止，节省资源。
- **效率与性能兼得**：相比生成-搜索方法，MARS以更少迭代和计算成本达到更高准确率。
- **泛化能力强**：在通用、领域、中文、法律、数学等多类型任务上一致领先，且跨模型迁移成功。
- **实验充分严谨**：全面消融、收敛、效率、跨模型等分析，理论支撑与实证结果相互印证。

## 8. 不足与局限

- **黑盒依赖性**：所有智能体均基于LLM（Deepseek-v2.5），自身推理成本可能较高，且对基座模型质量敏感。虽然验证了跨模型迁移，但未探索更小或开源模型的适用性。
- **未说明算力消耗**：缺少GPU型号、运行时间等量化指标，难以评估实际部署门槛。
- **阈值选择**：早停阈值 \( \delta=0.01 \) 和最大迭代 \( I=10 \) 可能并非通用最优，对不同任务可能需要自适应调节。
- **任务类型覆盖有限**：虽然涵盖17个数据集，但主要集中于分类、推理等，未涉及生成式任务（如摘要、翻译）的详细评估。LLM作为优化器本身也需消耗token，大规模应用时的成本平衡未定量分析。
- **对比方法时效性**：对比的baseline多发表于2022-2024年，未与更新近的APO方法（如Prompt-R1, DPO-based等）比较，但论文发表于2026年，可理解。
- **潜在偏差**：优化过程依赖LLM自身输出评估，可能引入自我强化偏差；虽然Teacher-Critic循环有内部纠错，但Critic同样基于LLM，无法保证完全客观。

（完）
