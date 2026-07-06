---
title: "TAI3: Testing Agent Integrity in Interpreting User Intent"
title_zh: "TAI3: 测试代理在解释用户意图中的完整性"
authors: "Shiwei Feng, Xiangzhe Xu, Xuan Chen, Kaiyuan Zhang, Syed Yusuf Ahmed, Zian Su, Mingwei Zheng, Xiangyu Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Gf4oPoluAV"
tags: ["query:cli-agent"]
score: 9.0
evidence: 系统性地揭示用于任务自动化的LLM代理中的意图完整性违反
tldr: 本文提出TAI3，一个以API为中心的应力测试框架，用于系统性地发现LLM代理在解释用户意图时的完整性违反。通过基于工具包文档生成真实任务并应用针对性变异，TAI3能揭示代理的细微错误，确保在任务自动化中代理行为与用户意图一致。该方法对于部署可靠的CLI代理至关重要。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: LLM代理在自动化任务时经常误解用户意图，传统软件测试无法处理自然语言歧义。
method: 提出TAI3框架，基于工具包文档生成真实任务，并应用针对性变异来暴露代理意图错误。
result: TAI3能系统性地发现LLM代理在意图理解上的违规行为，比现有方法更全面。
conclusion: TAI3提供了一种有效的测试方法，确保LLM代理在任务自动化中的意图完整性，对CLI代理安全部署有重要意义。
---

## Abstract
LLM agents are increasingly deployed to automate real-world tasks by invoking APIs through natural language instructions. While powerful, they often suffer from misinterpretation of user intent, leading to the agent’s actions that diverge from the user’s intended goal, especially as external toolkits evolve. Traditional software testing assumes structured inputs and thus falls short in handling the ambiguity of natural language. We introduce TAI3, an API-centric stress testing framework that systematically uncovers intent integrity violations in LLM agents. Unlike prior work focused on fixed benchmarks or adversarial inputs, TAI3 generates realistic tasks based on toolkits’ documentation and applies targeted mutations to expose subtle agent errors while preserving user intent. To guide testing, we propose semantic partitioning, which organizes natural language tasks into meaningful categories based on toolkit API parameters and their equivalence classes. Within each partition, seed tasks are mutated and ranked by a lightweight predictor that estimates the likelihood of triggering agent errors. To enhance efficiency, TAI3 maintains a datatype-aware strategy memory that retrieves and adapts effective mutation patterns from past cases. Experiments on 80 toolkit APIs demonstrate that TAI3 effectively uncovers intent integrity violations, significantly outperforming baselines in both error-exposing rate and query efficiency. Moreover, TAI3 generalizes well to stronger target models using smaller LLMs for test generation, and adapts to evolving APIs across domains.

---

## 论文详细总结（自动生成）

好的，我将基于您提供的论文元数据和摘要内容，以Markdown格式输出详细的中文总结，并遵守所有要求。

---

# TAI3: 测试代理在解释用户意图中的完整性 —— 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：随着LLM代理被广泛部署用于通过自然语言指令调用API来自动化真实任务，一个严重问题逐渐显现——代理经常误解用户的意图，导致其采取的行动与用户期望的目标背离。这种“意图完整性违反”在外部工具包频繁演进时尤为突出。
- **背景挑战**：传统软件测试方法假设输入是结构化的（如固定格式、参数），无法处理自然语言固有的模糊性和语义不确定性。现有工作要么依赖固定基准，要么集中于对抗性输入，未能系统性地暴露代理在真实任务中的意图错误。
- **整体含义**：本文旨在填补这一空白，提出一种以API为中心的应力测试框架，能够系统地、高效地发现LLM代理在解释用户意图时的完整性违反，从而确保代理行为与用户真实意图一致，这对于CLI（命令行接口）等任务自动化代理的安全部署至关重要。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：TAI3框架以工具包的文档为基础，生成逼真的任务，并应用针对性变异来揭示代理的细微错误，同时保持用户意图不变。通过“语义分区”将自然语言任务按API参数及其等价类划分为有意义的类别，在每个分区内生成种子任务，然后进行变异并排序。
- **关键技术细节**：
  - **语义分区（Semantic Partitioning）**：根据工具包API参数及其等价类将自然语言任务分组，使得同一分区内的任务具有相似的语义结构，便于针对性测试。
  - **种子任务变异与排序**：对每个分区内的种子任务应用变异，并利用一个轻量级预测器估计该任务触发代理错误的可能性，从而优先测试高风险任务。
  - **数据类型感知的策略记忆（Datatype-aware Strategy Memory）**：维护一个记忆模块，记录过去案例中有效的变异模式，并能根据当前任务的数据类型检索和自适应调整变异策略，提升测试效率。
- **算法流程**（文字说明）：
  1. 输入：目标LLM代理及其可调用的工具包API文档。
  2. 语义分区：基于API参数类型和等价类创建多个任务分区。
  3. 种子生成：从每个分区中生成初始的“无歧义”任务（代表用户真实意图）。
  4. 变异：对种子任务施加保持意图的变异（例如替换同义词、改变参数格式等），生成变体任务。
  5. 排序与选择：使用轻量级预测器对变体任务打分，选取高概率触发错误的任务。
  6. 执行测试：将选定的任务作为输入送交给LLM代理，观察其行为是否偏离用户意图。
  7. 策略记忆更新：将触发错误的变异模式存入记忆，供未来测试复用。
- **公式/模型**：文中未给出具体数学公式，但强调了轻量级预测器和模型无关的测试生成方式（用小LLM生成测试，测试更强模型）。

## 3. 实验设计：数据集/场景、基准、对比方法

- **数据集/场景**：实验使用了来自多个领域的80个工具包API（如CLI命令、数据处理API等），覆盖不同复杂度。
- **基准（Benchmark）**：没有明确说明固定基准数据集，但作者构建了基于这些API的真实任务集合作为测试基础。
- **对比方法**：与多种基线方法比较，包括：
  - 现有的固定基准测试（如特定任务集）。
  - 对抗性输入生成方法（如基于扰动的攻击）。
  - 随机变异方法。
- **评价指标**：错误暴露率（Error-exposing Rate）和查询效率（Query Efficiency）。

## 4. 资源与算力

- **未明确说明**：论文摘要和元数据中没有提及具体使用的GPU型号、数量、训练时长等算力信息。可能只在完整论文的实验部分有详细描述，但此处无法获取。结论中指出“用小LLM生成测试”，暗示测试生成成本较低，但具体数值未知。

## 5. 实验数量与充分性

- **实验数量**：仅从摘要可知，在80个工具包API上进行了实验。但具体实验组数（如不同变体、不同LLM模型、消融实验数量）未在摘要中给出。
- **充分性判断**：
  - **优点**：覆盖了80个API，涉及多个领域，具有一定的广度。使用大小模型对比，验证了泛化能力。
  - **不足**：缺乏消融实验（如移除策略记忆、移除语义分区等效果）的具体说明；未报告统计显著性；仅一个抽象摘要难以全面评估实验设计的公平性。需要完整论文才能判断。

## 6. 论文的主要结论与发现

- **主要结论**：TAI3能够系统性、高效地发现LLM代理在意图理解上的违规行为，其在错误暴露率和查询效率上显著优于基线方法。
- **其他发现**：
  - TAI3可以很好地泛化到更强的目标模型（即使测试生成使用了更小的LLM）。
  - TAI3能够适应不同领域演进的API，具有较好的可扩展性。
- **启示**：该框架对于确保CLI代理等任务自动化系统的安全部署具有重要实用价值。

## 7. 优点（方法或实验设计亮点）

- **创新方法论**：提出语义分区和数据类型感知策略记忆，使得测试生成具有针对性和高效性，而不是盲目随机。
- **实践导向**：聚焦于真实API文档生成任务，贴近实际部署场景。
- **模型无关性**：测试生成可以使用小型LLM，而目标代理可以是更强模型，降低了测试成本。
- **错误暴露率高**：实验证明比现有方法更能触发细微错误。
- **自适应能力**：能够根据过往经验调整变异策略，提升持续测试效率。

## 8. 不足与局限

- **信息不完整**：基于摘要，无法获知具体实验重复次数、统计检验、消融实验等细节，难以全面评估方法的稳健性。
- **覆盖范围有限**：仅测试了80个API，虽然涉及多个领域，但未说明是否覆盖了所有常见类型（如图像、文本、音频等）。
- **依赖文档质量**：测试生成基于工具包文档，如果文档不准确或过时，会影响测试有效性。
- **未讨论安全性**：虽然提升了意图完整性，但未考虑对抗性攻击或恶意用户输入可能导致的安全风险。
- **未见开源代码或数据集**：未提及是否公开，影响可复现性。
- **计算资源未披露**：无法评估其实际部署成本。

（完）
