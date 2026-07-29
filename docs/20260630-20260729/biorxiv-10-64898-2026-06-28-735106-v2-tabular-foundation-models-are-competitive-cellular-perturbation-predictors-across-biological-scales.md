---
title: Tabular Foundation Models Are Competitive Cellular Perturbation Predictors Across Biological Scales
title_zh: 表格基础模型在跨生物尺度的细胞扰动预测中具有竞争力
authors: "Palla, G., Hillsley, A., Kim, Y.-J., Royer, L. A."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.28.735106v2.full.pdf"
tags: ["query:tabular-fm"]
score: 9.0
evidence: 表格基础模型用于细胞扰动预测
tldr: 细胞扰动预测是药物发现的关键挑战。研究评估了TabICL、TabPFN等通用表格基础模型与scGPT等专用模型在多个数据集上的表现。结果显示，表格基础模型在跨细胞类型、伪批量预测及全胚胎细胞类型组成预测中表现相当或更优。这表明通用表格上下文学习可替代生物专用架构，具有强可扩展性。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 783, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1447, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1440, \"height\": 985, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1434, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1430, \"height\": 987, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1433, \"height\": 950, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1437, \"height\": 780, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1515, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 971, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1105, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1314, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 596, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 774, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 889, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1632, \"height\": 972, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1315, \"height\": 972, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1505, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/biorxiv/biorxiv-10-64898-2026-06-28-735106-v2/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 867, \"height\": 835, \"label\": \"Table\"}]"
motivation: 检验通用表格基础模型相比领域特定模型在细胞扰动预测中的有效性，以探索更简洁的建模方案。
method: 对比TabICL、TabPFN与PRESAGE、scGPT等模型在四个跨尺度评估场景（含Perturb-seq、CRISPR筛选等）上的性能。
result: 表格基础模型在细胞级别跨细胞类型预测与伪批量预测中一致优于或持平专用模型，在全胚胎预测中具竞争力。
conclusion: 通用表格上下文学习可成为细胞扰动响应建模的强有力、可扩展替代方案，无需专用架构。
---

## 摘要
预测细胞如何响应遗传和化学扰动是药物发现和功能基因组学中的一个核心挑战。为了解决这个问题，已经开发了日益增多的专门化单细胞基础模型生态系统，然而它们相比领域无关方法的实际优势仍不明确。在这里，我们评估了表格基础模型（如TabICL和TabPFN，通用预训练回归模型）与领域特定架构（包括PRESAGE、scGPT、scLAMBDA、STACK和Prophet）在四个互补评估设置中的能力：细胞层面上下文内跨细胞类型预测、基于五个Perturb-seq细胞系数据集的伪批量扰动预测、原代人CD4+ T细胞的全基因组CRISPR筛选，以及斑马鱼发育扰动图谱中的胚胎水平细胞类型组成预测。在细胞层面跨细胞类型扰动预测中，表格基础模型的表现与专门模型相当或更优。在伪批量扰动预测中，表格基础模型在多个评估指标和数据集上 consistently 优于专门基线。在全胚胎细胞类型组成预测中，表格基础模型与专门基线具有竞争力。这些结果表明，通用表格上下文内学习为跨细胞系统和尺度的扰动响应建模提供了一种强大且可扩展的替代方案，取代了定制化的生物架构。

## Abstract
Predicting how cells respond to genetic and chemical perturbations is a central challenge in drug discovery and functional genomics. A growing ecosystem of specialized single-cell foundation models has been developed to address this problem, yet their practical advantage over domain-agnostic approaches remains unclear. Here we evaluate the power of Tabular Foundation Models such as TabICL and TabPFN, general-purpose pre-trained regression models, against domain-specific architectures including PRESAGE, scGPT, scLAMBDA, STACK and Prophet across four complementary evaluation settings: cell-level in-context cross-cell-type prediction, pseudobulk perturbation prediction on five Perturb-seq datasets of cell-lines, a genome-wide CRISPR screen in primary human CD4+ T cells, and embryo-level cell-type composition prediction in a zebrafish developmental perturbation atlas. In the cell-level cross-cell type perturbation prediction, Tabular Foundation Models perform on par or better than specialized models. On pseudobulk perturbation prediction, Tabular Foundation Models consistently outperform specialized baselines across multiple evaluation metrics and datasets. On whole-emrbryo cell-type composition prediction, Tabular Foundation Models are competitive with specialized baselines. These results demonstrate that general-purpose tabular in-context learning provides a strong and scalable alternative to bespoke biological architectures for perturbation response modeling across cell systems and scales.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：预测细胞在遗传或化学扰动下的响应是药物发现和功能基因组学中的关键挑战。当前，大量专门化的单细胞基础模型（如scGPT、PRESAGE、scLAMBDA、STACK、Prophet等）被设计用于该任务，这些模型通常包含生物先验（如基因网络、注意力机制、单细胞预训练）。然而，通用且“生物学无知”的表格基础模型（Tabular Foundation Models, TFMs，例如TabICL、TabPFN）是否也能达到甚至超越这些专门模型，尚不清楚。
- **研究动机**：作者将各种扰动预测问题统一为回归框架——给定细胞环境c和扰动p，预测条件均值响应μ(c,p)。表格基础模型（尤其是Prior-Fitted Networks）在测试时通过少量样本的上下文学习进行近似贝叶斯后验预测，天然适合这种小样本、异构特征的回归问题。因此，作者假设：强后验预测回归能力比手工设计的生物归约更重要。
- **宏观含义**：如果通用表格基础模型能在多个生物尺度（从单细胞到胚胎）上匹敌或超越专门模型，则意味着扰动预测领域可能不需要复杂、昂贵的生物预训练架构；简单的PCA分解 + 零样本表格回归即可作为高效、可扩展的替代方案。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将各类扰动预测任务统一转化为“表格回归”问题。每个样本（行）对应一个细胞、一个扰动或一个时间点-扰动对，特征向量包含生物上下文和扰动表征，目标是预测一个标量（通过PCA分解高维输出）。利用预训练的表格基础模型（TabICL、TabPFN）零样本执行上下文学习，无需微调或梯度更新。
- **关键技术细节**：
  - **输出空间分解**：为处理高维目标（如数千基因的表达），采用PCA将输出投影到低维主成分空间（d_y=128）。对每个主成分分别训练一个独立的标量回归器（TFM），然后逆PCA重构完整预测。
  - **细胞层面的跨细胞类型预测**：
    - 源细胞（如T细胞）和目标细胞（如NK细胞）的对照样本先进行PCA联合嵌入。
    - 使用最优传输（OT）将源对照细胞与目标对照细胞配对（基于PCA空间中的欧氏距离）。
    - 对每个PCA主成分k，TFM从源细胞PCA得分预测目标细胞PCA得分，从而学习跨细胞类型的翻译映射。
    - 测试时，将药物处理的源细胞投影到PCA空间，通过TFM预测目标细胞PCA得分，再逆PCA得到表达谱。
  - **伪批量（Pseudobulk）级别预测**：
    - 对每个扰动，计算治疗效应向量（处理均值减去对照均值），并PCA降维。
    - 构建每个扰动的特征向量：包括基因共表达嵌入（通过训练集logFC矩阵转置后PCA得到）以及多个模态的嵌入（ESM2、BioGPT、CellProfiler、STRING-DB、DepMap等）。对于Perturb-seq设置，还拼接来自非留出细胞系的伪批量参考特征。
    - 对每个输出主成分k，TFM将特征向量映射到该主成分值，训练集为所有训练扰动。
  - **斑马鱼胚胎级别预测**：
    - 目标为每个（扰动，时间点）条件下的98种细胞类型比例向量。
    - 特征由干预嵌入（通过控制细胞SVD得到）、细胞状态嵌入（控制细胞均值）、表型嵌入（控制细胞比例）拼接而成，总维度398。
    - 对X和Y均独立进行PCA降维到d_x=d_y=32，然后使用TFM逐成分回归。
  - **使用的TFM**：TabICLv2和TabPFN 2.6，均为冻结权重、零样本应用，无需任务特定训练。

### 3. 实验设计

- **数据集/场景**：四个互补基准测试，覆盖三个生物尺度：
  1. **细胞级别跨细胞类型预测**：OpenProblems化学扰动基准（298K细胞，3个供体，4种细胞类型，144种药物条件）。模型在T细胞上训练，预测NK、B细胞和髓系细胞对药物的响应。基因面板为2k HVGs。
  2. **伪批量扰动预测（细胞系）**：五个Perturb-seq数据集（Nadig HepG2, Jurkat；Replogle K562 Essential, K562 GW, RPE1 Essential）。使用5折扰动留出交叉验证。评价指标：相对MSE（top-20 DE基因）、余弦相似度（top-20 DE）、表型AUROC、Recall@10。
  3. **全基因组CRISPR筛选（原代CD4+ T细胞）**：来自Zhu et al. 2025，两个供体，约11k个扰动。保留on-target显著敲低的约7k个扰动。使用5折扰动留出CV，指标同上。
  4. **斑马鱼发育扰动图谱**：zscape数据集（2.7M细胞，28个遗传扰动，5个时间点，98种细胞类型）。5折严格时间点留出（每折留出一个时间点的所有行）。
- **对比方法**：
  - **表格基础模型**：TabICL、TabPFN（零样本）。
  - **通用表格基线**：CatBoost（梯度提升树，训练于每个fold）。
  - **领域特定模型**：STACK（细胞级别）、PRESAGE（伪批量）、scGPT、scLAMBDA（伪批量）、Prophet（斑马鱼）。
  - **基本基线**：均值基线、Bootstrap（实验噪声上限，通过从留出扰动自身细胞重采样得到）。
- **公平性**：所有模型使用相同的特征（除非有各自专有输入），相同的交叉验证划分，相同的评价指标。TabICL/TabPFN和CatBoost通过相同的PCA管道进行预处理，STACK使用其标准输入，PRESAGE使用其多模态嵌入。

### 4. 资源与算力

- **计算环境**：主要运行在单个NVIDIA L40或A40 GPU上。
- **运行时间**：
  - TabICL/TabPFN（零样本）：每个fold约3秒（仅推理）。
  - CatBoost：每个fold约4-7秒（训练+推理）。
  - PRESAGE：每个fold约253秒（训练10,000 epoch，从零训练）。
  - STACK：需要128GB RAM、8 CPU、每个供体最多6小时墙钟时间。
- **总算力未明确**：论文未报告所有实验的GPU时总数，但根据规模（5个数据集×5折×多个模型/消融）估算工作量较大，且主要消耗在PRESAGE和STACK上。
- **结论**：TFM在计算上极高效，预训练成本已摊销，每轮实验成本比领域特定模型低两个数量级。

### 5. 实验数量与充分性

- **实验数量**：非常丰富。包括：4个主要场景 × 多个模型对比（至少6种方法）→ ~20个实验；消融实验包括：OT vs NN匹配、支撑集采样策略（Random vs FPS）、输出分解几何消融（PCA tail, PCA随机旋转, ICA, NMF, 高斯投影）、输入/输出PCA维度扫描、数据效率扫描（25%~100%训练扰动）、模态留一消融（6种模态）等。附录中包含大量表格和图（共30页），每个实验均报告均值±标准差（5折）。
- **充分性与公平性**：
  - **充分**：覆盖了从单细胞到胚胎的三个生物尺度，包括细胞系和原代细胞，扰动类型包括化学和遗传，目标包括基因表达和细胞组成。消融实验系统性地验证了关键决策（匹配方法、输出子空间、支撑集多样性）。
  - **客观**：所有对比使用相同交叉验证划分，指标公开，且代码已开源（github）。Bootstrap基线提供了理论上限，有助于解释模型差距。
  - **可能不足**：CD4+ T细胞全基因组筛选的绝对指标较低（余弦接近0），论文归因于信号弱，但未进一步分析模型在小信号场景下的局限性；斑马鱼实验仅使用5折时间点留出，时间点数量少（5个），可能对随机分割敏感；未与最新的深度回归模型（如Dense神经网络）对比，但主要目标是证明TFM的竞争力而非绝对SOTA。

### 6. 论文的主要结论与发现

- **主要结论**：通用表格基础模型（TabICL, TabPFN）在所有四个生物尺度上与领域特定模型相当或更优，且无需生物特定预训练。
  - 细胞级别跨细胞类型预测：TabICL在Pearson delta、DE Spearman、判别分数上领先；TabPFN接近；STACK仅在方向匹配和E-距离上占优（表1）。OT匹配优于NN匹配（消融）。
  - 伪批量扰动预测（细胞系）：TabICL和TabPFN在五个数据集上 consistently 优于PRESAGE、scGPT、scLAMBDA，接近Bootstrap上界（图2，表8）。在CD4+ T细胞全基因组筛选中，TabPFN是唯一产生正余弦的模型（表2），但绝对指标仍低。
  - 斑马鱼胚胎预测：TabPFN在Spearman和R²上最佳；CatBoost次之；Prophet略低；TabICL介于之间（表5）。TabPFN在全留出时间点（18hpf）上泛化最好（图3）。
- **关键机制发现**：
  - PCA输出空间分解是负载支撑的：投影到底部PC或随机子空间会崩溃，但正交旋转（如ICA）几乎不影响性能，说明覆盖高方差方向是关键的（图9）。
  - 支撑集多样性（使用最远点采样FPS）可在小上下文量下接近甚至超越全量性能（图12，表11），说明TFM的优势来自上下文学习中的样例选择，而非固定编码。
  - 数据效率：TFM在少量训练扰动（25%）下即可匹配或超越PRESAGE和CatBoost在100%数据上的性能（图8）。

### 7. 优点

- **方法简洁高效**：无需生物特定预训练、无需微调、仅用PCA+零样本TFM即可达到或超越专门模型。
- **计算经济**：在推理时极快（每个fold数秒），适合低资源场景；同时跨尺度通用（代码库统一）。
- **实验设计全面**：系统对比多个尺度、多个数据集、多种基线，并进行丰富的消融实验，揭示关键作用机制（输出子空间、支撑集多样性）。
- **开源可复现**：代码和预训练模型可用，评估管道公开。
- **提出新视角**：将扰动预测统一到“表格回归”框架，有助于简化未来研究工作。

### 8. 不足与局限

- **实验局限**：
  - CD4+ T细胞全基因组筛选信号极弱（logFC标准差小），导致所有模型绝对指标差，该场景的结论代表性有限。
  - 斑马鱼实验仅使用5个时间点进行时间点留出，时间序列信息未被充分利用（未使用LSTM等时序模型），可能低估了带生物先验模型的潜力。
  - 领域特定模型（如scGPT, scLAMBDA）在伪批量任务上表现较差，可能与它们的设计（面向单细胞而非伪批量）有关，论文对此未充分讨论。
- **模型适用性**：
  - TFMs难以处理超出其预训练边界的输入尺寸（论文中通过PCA控制维度），大规模高维数据可能需要额外降维。
  - 方法依赖于将高维目标降维到128维，可能丢失稀有基因或弱信号的信息（尽管消融表明这一步骤不是瓶颈）。
  - 未评估模型的校准性或不确定性量化，而是仅关注点预测。
- **偏差风险**：
  - 对比PRESAGE时，使用的超参数来自原作者，但未进行重新调优，可能有利于TFM。
  - CatBoost作为强基线被很好覆盖，但没有考虑更现代的深度学习表格模型（如XGBoost、LightGBM或Transformer表格模型）。
- **应用限制**：
  - 细胞级别跨细胞类型预测假设“源→目标翻译对扰动不变”，对于强扰动可能失效（论文未测试）。
  - 斑马鱼任务中，目标为细胞比例向量，是一个组成数据；TFM直接回归各成分而未考虑Softmax归一化，可能导致预测不合逻辑（尽管PCA后重构可能自动满足）。
  - 结论可能不适用于其他生物任务（如空间转录组、时间序列扰动跟踪）。

（完）
