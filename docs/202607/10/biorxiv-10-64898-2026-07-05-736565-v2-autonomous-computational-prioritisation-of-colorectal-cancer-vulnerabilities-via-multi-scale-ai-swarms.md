---
title: Autonomous computational prioritisation of colorectal cancer vulnerabilities via multi-scale AI swarms
title_zh: 通过多尺度人工智能群体自主计算优先级排序结直肠癌脆弱性
authors: "Baker, C., Ren, T., Rafferty, K., Wang, H., McDade, S."
date: 2026-07-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.05.736565v2.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 多智能体自主科学发现
tldr: 针对大语言模型与复杂生物学之间的认知差距，提出多尺度自主发现引擎Octopus，通过本地多智能体群与正则化预测环境，自动优先化结直肠癌脆弱性。系统在无监督筛选中将IGF2识别为5-氟尿嘧啶耐药关键候选，经Benjamini-Hochberg校正和Log-Rank检验显著，并在独立小鼠队列中验证了肿瘤体积缩小。该框架建立了自动化生物医学发现的可验证本地化范式。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 921, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1851, \"height\": 678, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 921, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 906, \"height\": 838, \"label\": \"Figure\"}]"
motivation: 现有AI科学发现框架缺乏多尺度临床翻译所需的统计约束，且算法数字孪生可解释性不足。
method: 构建神经符号框架Octopus，结合本地化多智能体群、CRISPR依赖数据、XGBoost SHAP特征归因和数字孪生预测，实现从体外到体内跨尺度的自动假设优先化。
result: 在结直肠癌中无监督筛选发现IGF2是5-FU耐药候选，经FDR校正显著（q=0.0292），并成功预测小鼠体内肿瘤体积缩小（p=0.0373）。
conclusion: Octopus实现了从假设生成到临床生存统计验证的自动化，为可信生物医学发现提供了可复制范式。
---

## 摘要
大规模语言模型（LLM）的语义推理能力与哺乳动物生物学复杂、非线性的现实之间的认知差距，从根本上制约了自动化科学发现的加速。尽管近年来多智能体框架已实现自主假设生成和体外实验分析，但它们往往缺乏多尺度临床转化所需的严格统计约束。此外，算法临床数字孪生虽能成功预测生物学状态，但常依赖不透明的潜在空间，以牺牲机制可解释性换取预测准确性。本文提出多尺度自主发现引擎（Octopus），这是一种神经符号框架，将完全本地化、保护隐私的多智能体群体与正则化预测算法环境相结合。该系统不止步于孤立的细胞实验，而是自主地根据体外CRISPR依赖性数据（CCLE）对治疗假设进行优先级排序，利用XGBoost SHAP向量追踪特征归因级联，并正交地将涌现的脆弱性从计算机模拟转化以预测体内哺乳动物肿瘤轨迹（PDX）和人类总生存期（Marisa）。在对结直肠癌转录组进行完全无监督扫描时，该流程自主地将胰岛素样生长因子2（IGF2）确定为5-氟尿嘧啶耐药性的重要候选脆弱性。该发现在经过严格的Benjamini-Hochberg错误发现率校正后仍保持显著性（q = 0.0292，对数秩检验 p = 0.0007），并成功预测了独立小鼠队列中显著的体内肿瘤体积缩小（混合效应线性混合模型 p = 0.0373）。通过将智能体假设生成与统计有界的临床生存相结合，该框架为生物医学发现的自动化计算优先级排序建立了一个可验证的本地范式。

## Abstract
The acceleration of automated scientific discovery has been fundamentally bottlenecked by the epistemic gap between the semantic reasoning of large language models (LLMs) and the complex, non-linear reality of mammalian biology. While recent multi-agent frameworks have achieved autonomous hypothesis generation and in vitro experimental analysis, they frequently lack the rigorous statistical constraints required for multi-scale clinical translation. Furthermore, while algorithmic clinical digital twins successfully forecast biological states, they often rely on opaque latent spaces, sacrificing mechanistic interpretability for predictive accuracy. Here, we introduce the Multi-Scale Autonomous Discovery Engine (Octopus), a neuro-symbolic framework that unites a fully localised, privacy-preserving multi-agent swarm with regularised predictive algorithmic environments. Rather than stopping at isolated cellular assays, the system autonomously prioritises therapeutic hypotheses against in vitro CRISPR dependency data (CCLE), traces feature attribution cascades using XGBoost SHAP vectors, and orthogonally translates emergent vulnerabilities in silico to predict in vivo mammalian tumour trajectory (PDX) and human overall survival (Marisa). In a fully unsupervised sweep of colorectal cancer transcriptomes, the pipeline autonomously prioritised Insulin-like Growth Factor 2 (IGF2) as a significant candidate vulnerability to 5-Fluorouracil resistance. The discovery maintained significance after rigorous Benjamini-Hochberg false discovery rate correction (q = 0.0292, Log-Rank p = 0.0007) and successfully predicted significant in vivo tumour volume shrinkage in an independent mouse cohort (Mixed-Effects LMM p = 0.0373). By bridging agentic hypothesis generation with statistically bounded clinical survival, this framework establishes a verifiable, local paradigm for the automated computational prioritisation of biomedical discoveries.

---

## 论文详细总结（自动生成）

### 论文详细中文总结

#### 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：当前基于大语言模型（LLM）的多智能体自动化科学发现框架在生物医学应用中存在两大瓶颈：一是缺乏从体外实验到临床转化的严格统计约束，导致发现难以在复杂哺乳动物生理系统中复现；二是算法数字孪生虽预测能力强，但依赖不透明的潜在空间，牺牲了机制可解释性。此外，现有系统多依赖云API，带来数据隐私和治理隐患，无法在受监管的临床环境中部署。
- **整体含义**：本文旨在构建一个**神经符号框架（Octopus）**，将完全本地化、隐私保护的多智能体LLM群体与正则化的算法预测环境（数字孪生）相融合，实现从假设生成到多尺度临床验证的端到端自动化，从而缩小“语义推理与生物学现实”之间的认知差距。该框架在结直肠癌中自主将**IGF2**识别为5-FU敏感性的预测性生物标志物，并跨体外、体内动物和人类临床队列验证。

#### 2. 方法论：核心思想、关键技术细节（算法流程）
- **核心思想**：采用**有向无环图多智能体架构**，限制LLM推理仅与数学上可验证的参数交互；同时构建一个**高度正则化的XGBoost数字孪生**作为“算法世界模型”，智能体必须通过该模型产生可量化的特征归因和生存统计结果。
- **关键技术细节**：
  - **本地化多智能体群体**：使用4-bit量化的**Gemma-4**模型，通过**llama.cpp**后端完全本地运行；使用CrewAI编排，采用单行对话模板和精确停止标记（`<end_of_turn>`）防止分词器幻觉；在每次假设生成周期后自动清空GPU VRAM上下文窗口。
  - **算法世界模型（数字孪生）**：基于**XGBoost**回归器，预测5-FU耐药性（AUC）。严格正则化：树数量≤80，最大深度=1，学习率=0.05，L1 α=0.1，L2 λ=1.0；特征空间通过方差阈值筛选至Top 300高变异转录本。
  - **因果SHAP级联（模拟CRISPR敲除）**：智能体自动将目标基因特征**零掩码**，然后迭代通过预测器；将转录本矩阵视为动态状态向量，施加递归衰减系数（λ=0.5），模拟三个离散时间步的生物学信号传递退化；计算每一步SHAP值绝对离差，生成可验证的、有向的机制级联。
  - **统计翻译与验证**：采用**中位数分层**（避免截止值优化偏差）划分高/低表达组；使用**Kaplan-Meier**生存曲线和对数秩检验；多变量**Cox比例风险回归**调整年龄、分期、MSI、CMS，并检验PH假设；全部p值经**Benjamini-Hochberg FDR校正**（q<0.05为显著）；体内数据使用**线性混合效应模型（LMM）** 按患者线分组。
- **算法流程（文字描述）**：
  1. 数据获取与标准化（CCLE/PDX/Marisa）→ Polars列式数据湖。
  2. 方差阈值筛选Top 300高变异基因。
  3. 训练XGBoost数字孪生（预测5-FU耐药性）。
  4. 智能体扫描高变异基因空间，选择待测试基因。
  5. 执行SHAP归因和模拟CRISPR敲除级联。
  6. 在Marisa临床队列中计算KM生存、Cox回归、FDR校正。
  7. 若候选基因通过FDR校正，则在PDX小鼠队列中验证肿瘤体积变化（LMM）。
  8. 输出最终优先化的生物标志物和统计证据。

#### 3. 实验设计
- **使用数据集**：
  - **体外（in vitro）**：CCLE（癌症细胞系百科全书）中肠系细胞系的转录组数据（Log2(TPM+1)）和GDSC2药物敏感性（5-FU AUC值）。
  - **体内（in vivo）**：独立的小鼠患者源性异种移植（PDX）队列，包含原始计数和肿瘤体积随时间变化数据（N=86只小鼠）。
  - **临床（in clinico）**：Marisa人结肠癌队列（GSE39582），包含微阵列基因表达和585名患者的总生存期数据。
- **Benchmark与对比**：
  - 论文**未设置显式的定量基准对比**。但在讨论中与近期框架（Robin、Co-Scientist、AI Scientist）进行了定性比较，指出它们止步于体外实验或缺乏统计约束。
  - Octopus本身作为一个端到端的自主发现系统被评估，验证了IGF2从体外到体内再到临床的全链条显著性。
- **对照条件**：
  - 数字孪生预测性能：R²=0.50。
  - 体内验证：高/低IGF2表达组的肿瘤体积变化差异（LMM p=0.0373）。
  - 临床验证：高/低IGF2表达组的生存差异（对数秩p=0.0007，FDR q=0.0292）；多变量Cox HR=1.09。

#### 4. 资源与算力
- **明确说明**：论文提到使用了**4-bit量化的Gemma-4模型**，通过**llama.cpp**后端**完全本地运行**，未使用任何云API。计算资源在作者机构内部。
- **未明确**：GPU具体型号、数量、训练时长、显存大小等细节未给出。仅提及在推理循环间自动清除GPU VRAM。训练XGBoost数字孪生和统计分析均使用标准CPU/GPU环境。

#### 5. 实验数量与充分性
- **实验组数**：主要“发现实验”为一次完全无监督的扫描，从高变异基因空间中筛选出IGF2。后续验证包括：
  - 数字孪生拟合（单个R²值）。
  - SHAP特征重要性可视化（Top 10特征）。
  - 模拟CRISPR敲除的时间级联（3个时间步）。
  - 临床生存分析（KM曲线、多变量Cox、FDR校正）。
  - 体内PDX小鼠肿瘤体积变化分析（LMM）。
- **是否充分**：
  - **优点**：实验覆盖了体外→体内→临床三个尺度，使用多个独立数据集（CCLE、PDX、Marisa），并且采用了严格的统计校正（FDR、PH假设检验），具有一定的严谨性。
  - **不足**：
    - 仅验证了一个基因（IGF2），未报告扫描过程中其他候选基因的统计结果（如有多少基因通过FDR校正），也未进行消融实验（如数字孪生的不同正则化参数、不同时间步长的影响）。
    - 未与传统的基于统计的优先化方法（如差异表达分析、单变量Cox筛选）进行对比。
    - 未进行重复随机种子实验或交叉验证（数字孪生仅报告了out-of-fold R²）。
    - 体内验证仅有一个小鼠队列，且样本量不算大（86只小鼠，但通过LMM考虑了非独立性）。
  - **公平性**：整体实验设计遵循了“先筛选-后验证”的原则，避免了对同一数据集的过度优化。但缺乏与现有方法的系统比较，因此不能断定Octopus优于其他自动化系统。

#### 6. 主要结论与发现
- 论文提出的**Octopus框架**能够完全自主地、以本地化方式完成从假设生成到多尺度统计验证的全流程。
- 在结直肠癌的**无监督扫描**中，系统优先将**IGF2**识别为5-FU敏感性的**预测性生物标志物**。
- **临床意义**：高IGF2表达与**更差的总生存期**相关（HR=1.09，经多变量调整），但同时却**增强了对5-FU的肿瘤体积响应**（体内验证），提示IGF2是潜在的化疗增敏靶点。
- 该研究证明了通过将LLM群体严格绑定于正则化数字孪生和严格的生存统计，可以实现**可信的、可解释的**自动化生物医学发现，且能在保护数据隐私的前提下部署。

#### 7. 优点
- **架构设计**：首次将**本地化、隐私保护的多智能体**与**正则化XGBoost数字孪生**结合，通过有向无环图约束和SHAP因果级联，强制智能体输出可验证的数学证据，克服了LLM语义幻觉和黑箱不可解释的问题。
- **多尺度验证**：不局限于体外细胞系，而是自动进行**跨物种（小鼠）和跨临床（人类）** 的独立验证，极大增强了发现的临床转化潜力。
- **统计严谨性**：引入Benjamini-Hochberg FDR校正、多变量Cox回归、PH假设检验、线性混合效应模型等，避免了多假设检验和混淆因素的干扰。
- **可复现性与部署友好**：所有组件均开源或可本地部署（Gemma-4、llama.cpp、Polars、XGBoost、lifelines），代码可应要求提供，有助于在受监管的医疗IT基础设施中应用。

#### 8. 不足与局限
- **实验覆盖有限**：仅在一个癌症类型（结直肠癌）和一种药物（5-FU）上进行了全自动发现，未在其他癌症类型或药物上测试通用性。
- **模拟CRISPR的近似性**：SHAP归因和零掩码级联仅模拟了转录水平影响，未考虑翻译后修饰、表观遗传调控、肿瘤微环境空间动态等真实生物学复杂性，且无法模拟CRISPR-Cas9双链断裂导致的动态补偿机制。
- **未与基线方法对比**：没有与简单的统计优先级排序（如单变量Cox p值排序）或其他机器学习优先化方法（如随机森林特征重要性）进行定量比较，无法明确量化Octopus的增量优势。
- **潜在的偏差风险**：数字孪生仅在CCLE肠系细胞系（N未知，但属于小样本）上训练，可能无法完全代表原发肿瘤的异质性；PDX小鼠模型也存在物种差异。
- **前瞻性验证缺失**：所有验证均为回顾性队列分析，需要前瞻性随机临床试验来确认IGF2作为治疗靶标的有效性。
- **未报告阴性结果**：扫描过程中有多少基因未通过FDR校正？这些阴性结果对于评估假阳性率至关重要。

（完）
