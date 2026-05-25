---
title: Do Larger Models Really Win in Drug Discovery?A Benchmark Assessment of Model Scaling in AI-Driven Molecular Property and Activity Prediction
title_zh: 更大模型真的在药物发现中更胜一筹吗？关于AI驱动的分子性质与活性预测中模型规模扩展的基准评估
authors: "Guo, J."
date: 2026-05-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.04.29.721568v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 评估药物发现中AI模型缩放的基准
tldr: 该研究对比了传统机器学习、图神经网络、预训练序列模型和基于大语言模型的SAR方法在26个药物发现相关终点上的性能，发现经典ML（如RF(ECFP4)）在大多数情况下优于更大规模的模型，而大模型仅在低数据场景下对SAR解释有所贡献。
source: biorxiv
selection_source: carryover_cache
motivation: 验证药物发现中“更大模型必然更优”的假设。
method: 在78个端点-分裂组合上（涵盖ADME、毒性、生物活性），比较ML、GNN、预训练序列模型和LLM基线的预测性能。
result: 经典ML在156个均值比较中获胜116次，而LLM仅获胜3次；大模型在困难分裂下相对优势略有提升，但绝对性能仍弱。
conclusion: 模型性能取决于任务、分裂和模型的匹配，而非单纯规模；紧凑专用模型仍极具竞争力。
---

## 摘要
分子基础模型和大语言模型的快速发展推动了以规模为中心的AI药物发现观点，即更大的预训练模型有望取代为单个任务训练的紧凑型化学信息学模型和图神经网络（GNN）。我们在26个终点上测试了这一假设，这些终点涵盖分子性质、毒性、安全责任和生物活性，分为ADME、毒性和生物活性类别。该基准包含78个终点和拆分条目，涵盖随机、Murcko骨架和结构分离的五折交叉验证。按从易到难排序，这些拆分近似于对封闭库的回顾性评估、先导化合物优化中的骨架扩展以及新化学型的库扩展。每个条目包括基于机器学习的、GNN的、预训练分子序列的和基于LLM的SAR方法家族。在156个折均值比较中，经典机器学习方法（如RF(ECFP4)和ExtraTrees(RDKit)）获胜116次，GNN方法（如GIN和Ligandformer）获胜25次，预训练序列模型（如MoLFormer和ChemBERTa2）获胜12次，基于LLM的SAR基线方法获胜3次。机器学习在随机拆分插值中占主导地位，但在更难的拆分下失去部分优势；GNN和序列模型也有所下降，但相对地位提升；而基于LLM的SAR在绝对意义上较弱，但对拆分轴不敏感。配对Bootstrap分析支持家族水平趋势，且比单个模型排名更强烈。来自训练折的SAR知识改善了许多GPT5.5-SAR和Opus4.7-SAR指标，但并未使基于规则的推理成为监督预测器的通用替代品。紧凑的专门模型在分子性质和活性预测方面仍然非常有效。较大模型在低数据场景下为SAR解释和推理增加了价值，但预测性能取决于模型、任务和验证场景之间的匹配，而不仅仅是规模。

## Abstract
The rapid growth of molecular foundation models and large language models has encouraged a scale centred view of AI in drug discovery, in which larger pretrained models are expected to supersede compact cheminformatics models and graph neural networks (GNNs) trained for individual tasks. We test this assumption across 26 endpoints for molecular properties, toxicity, safety liabilities and biological activity, grouped into ADME, toxicity and bioactivity classes. The benchmark contains 78 endpoint and split entries spanning random, Murcko scaffold and structure separated 5-fold CV. Ordered from easiest to hardest, these splits approximate retrospective evaluation on a closed library, scaffold expansion in hit to lead, and library expansion on novel chemotypes. Each entry includes ML, GNN, pretrained molecular sequence and LLM based SAR families. Across 156 fold mean comparisons, classical ML such as RF(ECFP4) and ExtraTrees(RDKit) win 116, GNNs such as GIN and Ligandformer win 25, pretrained sequence models such as MoLFormer and ChemBERTa2 win 12, and LLM based SAR baselines win three. ML dominates random split interpolation but loses part of this advantage under harder splits; GNN and sequence models also decline but gain relative ground, whereas LLM based SAR is weaker in absolute terms yet less sensitive to the split axis. Paired bootstrap analyses support family level trends more strongly than individual model rankings. SAR knowledge derived from training folds improves many GPT5.5-SAR and Opus4.7-SAR metrics but does not make rule based reasoning a universal substitute for supervised predictors. Compact specialized models remain highly effective for molecular property and activity prediction. Larger models add value for SAR interpretation and reasoning in low data settings, but predictive performance depends on the fit among model, task and validation scenario, not on scale alone.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在AI驱动的药物发现中，“更大规模的模型是否必然带来更好的分子性质和活性预测性能？”当前研究界普遍认为分子基础模型和大语言模型（LLM）会取代传统紧凑模型，但该论文基于系统性基准测试挑战这一假设。
- **整体含义**：模型性能取决于**模型-任务-验证场景之间的匹配**，而非单纯参数或预训练规模。紧凑的专门模型（如基于指纹的随机森林）在大多数实际情况下仍然极其有效，大模型仅在低数据场景下的SAR（构效关系）解释和推理上有补充价值。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过统一基准，在多种药物发现终点上比较四类模型家族，评估模型缩放对预测性能的影响。特别关注不同数据拆分难度（从易到难：随机、Murcko骨架、结构分离）如何改变模型排名。
- **关键技术细节**：
  - **模型家族**：
    1. **经典机器学习（ML）**：基于固定分子指纹（ECFP4/6、MACCS）和RDKit描述符的树集成（RF、ExtraTrees、GBDT）及线性模型（LR、Ridge），参数极少。
    2. **图神经网络（GNN）**：GCN、GAT、GIN、Ligandformer，利用分子图结构学习任务特定表示，参数量10⁵~10⁶。
    3. **预训练分子序列模型（Sequence）**：ChemBERTa / ChemBERTa2（77M/10M参数）、MoLFormer（47M参数），基于大量SMILES语料预训练后针对每个任务微调。
    4. **LLM-SAR规则基线（LLM-SAR）**：由GPT5.5和Claude Opus 4.7生成固定的规则库（正则/SMARTS模式），本地应用评分；可选加上训练集派生SAR知识。不涉及微调或在线查询。
  - **评估策略**：
    - 三种5折交叉验证：随机（模拟回顾性评估）、Murcko骨架（模拟骨架扩展）、结构分离（按化学空间聚类分配折，模拟新化学型扩展）。
    - 分类任务以**PR-AUC**为主（对不平衡数据更稳健），辅助ROC-AUC、Top-K富集（EF@1%/5%/10%）、校准（Brier、ECE）。回归任务使用MAE和Pearson。
    - 统计显著性检验：配对Bootstrap（1000次重采样），使用Benjamini-Hochberg FDR校正（q=0.05），区分家族层和模型层比较。

### 3. 实验设计：数据集 / 场景、benchmark、对比方法

- **数据集与场景**：
  - **26个终点**，分为三类：
    - **ADME相关**（6个）：Caco-2渗透性、BBB穿透、CYP3A4抑制、PXR/NR1I2激活、脂溶性、水溶性。
    - **毒性相关**（17个）：AMES突变、DILI、hERG、DRD2、12个Tox21通路活性。
    - **生物活性相关**（3个）：EGFR激酶抑制、抗结核（H37Rv）、抗疟（P. falciparum 3D7/Dd2）。
  - 每个终点在三种拆分（随机、Murcko、结构分离）下形成共**78个任务条目**（部分终点非分类/回归混合）。
- **基准（Benchmark）**：统一评估协议，包括5折交叉验证、相同预处理（平衡类权重、标签清洗等）、固定训练超参数（GNN约30-50 epoch，序列模型3-5 epoch等）。
- **对比方法**：四个家族共23个具体模型变体（ML: RF/ExtraTrees/GBDT/LR/Ridge共16种；GNN: GCN/GAT/GIN/Ligandformer；Sequence: ChemBERTa/ChemBERTa2/MoLFormer；LLM-SAR: GPT5.5-SAR/Opus4.7-SAR，各带/不带训练知识）。

### 4. 资源与算力

- **未明确说明**：论文中未提及使用的GPU型号、数量、训练时长、总计算消耗等具体算力信息。仅提到了模型参数量级（GNN约10⁵~10⁶，序列模型10M~77M），但无硬件细节。这一信息缺失可能影响可复现性和资源预算估计。

### 5. 实验数量与充分性

- **实验数量**：
  - 总共**78个任务条目**（26端点 × 3拆分），每个条目含5折，共390次训练-测试周期。
  - 汇总为**156个折均值比较**（分类+回归指标），生成表2的胜出统计。
  - 配对Bootstrap检验：家族层378次、模型层189次（分类/回归合计），使用FDR校正。
  - 额外实验：数据规模分析（6个训练量水平 × 4个代表性任务）、Top-K富集（所有任务）、校准分析（所有分类任务）。
- **充分性与公平性**：
  - 实验设计覆盖了不同难度、不同药理类型、不同数据规模，较为全面。
  - 统一评估协议、相同拆分、相同统计检验，对比公平。
  - 注意点：部分终点高阳性率（如DRD2 88.9%）需谨慎解读PR-AUC，论文提供了质量调整lift；GNN/序列的超参数并非严格全局优化（每个家族内固定设置），但论文强调这是为了反映“典型部署做法”。
  - 结论支持家族层趋势，但对单个模型排名建议谨慎（仅24%的模型层比较显著）。实验设计较客观。

### 6. 论文的主要结论与发现

- **规模不是性能的可靠预测因素**：
  - 在156个折均值比较中，ML获胜116次（74%），GNN 25次，序列12次，LLM-SAR 3次。
  - 随机拆分下ML主导（48/52），但在更难的拆分下优势缩小；GNN和序列相对改善但绝对性能仍低于ML。
  - LLM-SAR绝对最弱，但对拆分难度最不敏感（毒性类drop仅0.009）。
- **紧凑模型依然极具竞争力**：基于指纹的RF/ExtraTrees在大多数ADME、毒性、生物活性任务上表现最佳，尤其在局部SAR数据丰富时。
- **GNN和序列模型仅在特定条件下有益**：当图拓扑与终点生物学对齐，或SMILES预训练特征可转移时。例如PXR/NR1I2在Murcko拆分下MoLFormer领先。
- **LLM-SAR作为推理层而非预测器**：规则库有助于理解SAR、生成假设，但无法替代监督模型；训练集知识可改善指标但仍远低于ML/GNN。
- **统计检验支持家族层结论强于模型层**：84%家族层比较显著，而模型层仅24%显著。
- **校准方面ML最优**：ML的Brier/ECE中位数远低于GNN和序列（毒性类中位数Brier 0.065 vs 0.110/0.179）。
- **数据规模影响**：在极低样本（500）下，预训练序列（MoLFormer）可能领先，但1000以上样本ML反超。

### 7. 优点

- **系统性覆盖**：26个终点、三种难度拆分、四类模型家族，构建了目前较全面的分子性能预测基准。
- **侧重实际场景**：使用化学空间结构分离拆分模拟真实库扩展，并强调PR-AUC对不平衡数据的适用性。
- **严格的统计检验**：配对Bootstrap和FDR校正，区分家族层与模型层结论，避免过度解读微小差异。
- **透明与可复现**：公开补充数据、代码和配置，提供数据质量标记（如小测试集、类不平衡）。
- **实践价值**：明确挑战了“越大越好”的假设，为AI药物发现中的模型选择提供了证据基础，指导优先使用紧凑模型+适当表示。

### 8. 不足与局限

- **仍未完全覆盖**：基准仅针对小分子（无生物药、肽等），且偏重分类任务（回归任务较少）。
- **计算资源缺失**：未报告GPU、总计算时等，影响可复现性和成本比较。
- **内部数据未公开**：抗结核和抗疟数据集部分来自机构，未完全开放原始结构文件。
- **超参数固定**：每个家族使用固定设置（如GNN 30 epoch、序列学习率2e-5），未进行全家族超参数搜索，可能未发挥各个模型最大潜力。
- **LLM-SAR基线粗糙**：仅由LLM生成一次性规则，未结合迭代优化或直接微调，不能代表最新LLM能力。
- **结论受基准约束**：仍为经验性比较，不能推广到所有药物发现任务或未来新模型架构。前瞻性验证有待补充。
- **阳性率问题**：高阳性率终点（如DRD2）下PR-AUC数值高但lift低，论文虽提供了调整，但解读仍需谨慎。

（完）
