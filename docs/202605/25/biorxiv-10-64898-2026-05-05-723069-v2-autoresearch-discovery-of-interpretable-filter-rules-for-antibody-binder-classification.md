---
title: Autoresearch Discovery of Interpretable Filter Rules for Antibody Binder Classification
title_zh: 自动研究发现可解释的抗体结合物分类过滤规则
authors: "Landajuela, M."
date: 2026-05-19
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.723069v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 自动研究循环用于抗体设计的科学发现
tldr: "该研究利用自动研究循环系统，通过迭代提出并评估抗体结合子分类的过滤规则，发现了一种简洁的RMSD-Tuned Triad规则，将ROC-AUC从0.6371提升至0.8060，相对改进26.5%，性能优于逻辑回归和GPT-4o基线，且无需训练数据或LLM推理。"
source: biorxiv
selection_source: fresh_fetch
motivation: 抗体设计中候选者众多但实验测试有限，亟需无需训练的筛选过滤器来高效分类结合子。
method: 采用自动研究循环，迭代提出规则变体，在固定留一系统外协议下评估，记录实验结果并指导下一轮。
result: RMSD-Tuned Triad规则实现了0.8060的ROC-AUC，比初始基线提升0.1689，优于逻辑回归和GPT-4o提示基线，接近最强GPT-5结果。
conclusion: 系统性自动研究能将简单的结构置信度信号转化为紧凑、可解释的过滤器，在目标特异性训练数据稀少时非常有用。
---

## 摘要
抗体设计活动通常会产生许多候选物，但只有一小部分能够进行实验测试，使得候选物过滤成为核心瓶颈。我们研究自动研究循环是否能够通过迭代提出规则变体、在固定的留一系统协议下评估它们、将每次实验记录在版本控制中，并利用结果指导下一轮迭代，从而发现更好的无训练抗体结合物分类过滤器。在七个抗体-抗原系统上的75个独特的记录过滤器变体中，该循环将平均ROC-AUC从初始基线的0.6371提升到一个紧凑的最终规则（我们称之为RMSD调谐三元组规则）的0.8060，绝对增益为0.1689，相对改进26.5%。该发现的过滤器与在同一系统上评估的有监督机器学习基线和提示LLM基线相比具有竞争力：它超过了逻辑回归（0.7144）、特征选择的平衡逻辑回归（0.7536）以及GPT-4o表格少样本提示（0.7640），并且与最强的GPT-5表格少样本结果（0.8104）的ROC-AUC差距仅为0.0044。与LLM基线不同，最终规则一旦获得基于数值结构的特征，就不需要提示示例和LLM推理。这些结果表明，系统性自动研究可以将简单的结构置信度信号转化为紧凑、可解释的过滤器，在目标特异性训练数据稀缺时非常有用。

## Abstract
Antibody design campaigns increasingly generate many candidates before only a small subset can be tested experimentally, making candidate filtering a central bottleneck. We study whether an autoresearch loop can discover better training-free filters for antibody binder classification by iteratively proposing rule variants, evaluating them under a fixed Leave-One-System-Out protocol, recording each experiment in version control, and using the results to guide the next iteration. Across 75 unique logged filter variants on seven antibody-antigen systems, the loop improves average ROC-AUC from 0.6371 for the initial baseline to 0.8060 for a compact final rule that we call the RMSD-Tuned Triad rule, an absolute gain of 0.1689 and a relative improvement of 26.5%. The discovered filter is competitive with supervised machine learning baselines and prompted LLM baselines evaluated on the same systems: it exceeds logistic regression (0.7144), feature-selected balanced logistic regression (0.7536), and GPT-4o tabular few-shot prompting (0.7640), and it comes within 0.0044 ROC-AUC of the strongest GPT-5 tabular few-shot result (0.8104). Unlike the LLM baseline, the final rule requires no prompted examples and no LLM inference once the numeric structure-derived features are available. These results show that systematic autoresearch can turn simple structural-confidence signals into compact, interpretable filters that are useful when target-specific training data are scarce.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：抗体设计活动通常产生大量候选结合子，但受限于实验测试能力，仅能筛选极小部分。因此，需要高效、无需额外训练数据的过滤规则，以在实验前准确分类结合子与非结合子。
- **整体含义**：该研究探索自动研究循环（autoresearch loop）是否能够自主发现可解释的过滤规则，从而在不依赖目标特异性训练数据的情况下提升分类性能，为抗体计算筛选提供一种可复现、系统化的新范式。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：构建一个迭代的自动研究循环，由系统自动提出规则变体、在固定评估协议下测试、记录结果，并基于历史实验结果指导下一轮规则改进。
- **关键技术细节**：
  - 初始基线规则未明确说明（可能是简单阈值或领域启发式规则）。
  - 最终发现的规则称为 **RMSD-Tuned Triad 规则**，一种紧凑的三元组过滤条件，基于数值结构特征（如RMSD等结构置信度指标）。
  - 评估协议采用 **留一系统外（Leave-One-System-Out, LOSO）** 交叉验证，确保同一抗体-抗原系统的数据在训练/推理中不出现泄漏。
- **算法流程**（文字说明）：
  1. 定义一个初始过滤规则作为基线。
  2. 在LOSO协议下评估该规则在所有系统中的平均ROC-AUC。
  3. 基于历史实验数据和规则表现，自动提出规则变体（例如调整阈值、组合特征、添加或删除条件）。
  4. 将每个变体作为一次实验记录到版本控制系统中。
  5. 重复步骤2-4，直到性能收敛或达到预设迭代次数。
  6. 选择表现最佳的规则作为最终输出。

### 3. 实验设计：使用的数据集、基准与对比方法

- **数据集**：7个抗体-抗原系统，涉及多个抗体结合子分类任务。未提供具体系统名称及样本量，但总数覆盖75个独特过滤器变体的记录。
- **基准对比方法**：
  - 初始基线规则（性能：平均ROC-AUC 0.6371）
  - 逻辑回归（0.7144）
  - 特征选择的平衡逻辑回归（0.7536）
  - GPT-4o 表格少样本提示（0.7640）
  - GPT-5 表格少样本提示（最强结果 0.8104）
- **评估指标**：ROC-AUC，在LOSO协议下计算平均值。

### 4. 资源与算力

- **未明确说明**：论文摘要及元数据未提及所使用的GPU型号、数量、训练时长或总计算资源。可能由于自动研究循环主要基于规则枚举与评估，计算开销相对较小，但具体算力细节缺失。

### 5. 实验数量与充分性

- **实验数量**：记录了75个独特的过滤器变体，覆盖7个系统，每个变体均进行LOSO交叉验证。
- **充分性评价**：
  - **优点**：进行了系统的迭代探索，与多种监督学习和LLM基线对比，且在同协议下公平比较；实验过程被版本控制，可复现。
  - **不足**：仅基于一种结构特征（RMSD相关）进行规则搜索，未探索其他类型特征（如能量项、序列特征等）；未报告统计显著性检验（如配对t检验）或方差；样本量（7个系统）偏小，可能限制泛化性。

### 6. 论文的主要结论与发现

- 自动研究循环发现的 **RMSD-Tuned Triad 规则** 将平均ROC-AUC从0.6371提升至0.8060，绝对增益0.1689，相对改进26.5%。
- 该规则 **超过** 逻辑回归（0.7144）、特征选择逻辑回归（0.7536）和GPT-4o少样本提示（0.7640）；与最强GPT-5结果（0.8104）仅差0.0044 AUC。
- 最终规则无需训练数据或LLM推理，一旦获得数值结构特征即可直接使用，兼具可解释性与计算高效性。

### 7. 优点：方法或实验设计的亮点

- **无需目标特异性训练数据**：规则完全基于结构置信度信号，避免了对大量标注数据的依赖。
- **系统性与自动化**：自动研究循环实现了假设生成的自动化，减少人工试错，且通过版本控制保证可复现性。
- **紧凑可解释**：最终规则（三元组结构）易于理解和验证，适合生物学家直接应用。
- **公平对比**：与多种基线在相同LOSO协议下比较，保证了评估的客观性。

### 8. 不足与局限

- **特征空间局限**：仅使用了RMSD等结构置信度特征，可能忽略了其他重要信号（如静电作用、疏水性等），导致性能天花板。
- **泛化能力未充分验证**：仅基于7个抗体-抗原系统，系统间差异大，实验结果可能受特定系统分布影响，需在更大规模、更多样化数据集上验证。
- **无统计显著性分析**：未报告多次运行的误差棒或置信区间，无法判断改进是否具有统计显著性。
- **自动循环的探索成本**：虽然较传统机器学习轻量，但75次迭代仍需要人工参与（定义搜索空间），且可能陷入局部最优。
- **与LLM对比的局限性**：LLM基线使用了少样本提示，而发现规则未使用任何提示，两者比较的公平性依赖于提示设计质量；未评估更先进的LLM（如GPT-5）在更多提示策略下的表现。

（完）
