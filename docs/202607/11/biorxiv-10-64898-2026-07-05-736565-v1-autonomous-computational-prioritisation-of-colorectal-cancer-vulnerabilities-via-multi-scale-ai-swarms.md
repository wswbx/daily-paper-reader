---
title: Autonomous computational prioritisation of colorectal cancer vulnerabilities via multi-scale AI swarms
title_zh: 基于多尺度人工智能群落的结直肠癌脆弱性自主计算优先级排序
authors: "Baker, C., Ren, T., Rafferty, K., Wang, H., McDade, S."
date: 2026-07-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.05.736565v1.full.pdf"
tags: ["query:ar"]
score: 9.0
evidence: 提出多尺度自主发现引擎（Octopus），实现自动化科学发现
tldr: 大语言模型的语义推理与复杂生物学现实之间存在认知鸿沟，现有自动科学发现框架缺乏严格统计约束。本文提出多尺度自主发现引擎Octopus，通过神经符号框架整合局部多智能体群体与正则化预测环境，自动优化治疗假设。在结直肠癌转录组无监督扫描中，系统自主将胰岛素样生长因子2（IGF2）优先为5-氟尿嘧啶耐药的关键脆弱点，经多重检验校正后仍显著，并成功预测独立小鼠模型的肿瘤体积缩小。该工作建立了从假设生成到临床生存统计验证的可验证局部范式，推动了自动化生物医学发现。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 921, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1851, \"height\": 678, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 922, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 906, \"height\": 838, \"label\": \"Figure\"}]"
motivation: 现有LLM多智能体框架缺乏严格的统计约束，且临床数字孪生可解释性差，阻碍了自动化科学发现向临床转化。
method: Octopus框架结合局部隐私保护多智能体群体、XGBoost SHAP特征归因及正则化预测数字环境，实现神经符号推理与统计约束。
result: 自主优先IGF2为结直肠癌候选脆弱点，Benjamini-Hochberg校正后q值0.0292，Log-Rank p=0.0007，体外CRISPR数据验证并成功预测体内肿瘤缩小。
conclusion: 桥接假设生成与统计有界临床生存验证，建立了可验证的自动化计算优先范式，适用于多尺度生物医学发现。
---

## 摘要
自动化科学发现的加速从根本上受到大语言模型（LLMs）的语义推理与哺乳动物生物学复杂非线性现实之间认知鸿沟的瓶颈制约。尽管最近的多智能体框架已实现自主假设生成和体外实验分析，但它们通常缺乏多尺度临床转化所需的严格统计约束。此外，虽然算法临床数字孪生成功预测了生物学状态，但它们往往依赖不透明的潜在空间，为了预测准确性而牺牲了机制可解释性。在此，我们引入多尺度自主发现引擎（Octopus），这是一种神经符号框架，将完全本地化、保护隐私的多智能体群落与正则化预测算法环境相结合。该系统不局限于孤立的细胞检测，而是自主针对体外CRISPR依赖性数据（CCLE）对治疗假设进行优先级排序，使用XGBoost SHAP向量追踪特征归因级联，并正交地将计算机中出现的脆弱性转化为预测体内哺乳动物肿瘤轨迹（PDX）和人类总生存期（Marisa）。在对结直肠癌转录组进行完全无监督扫描时，该流程自主将胰岛素样生长因子2（IGF2）确定为5-氟尿嘧啶耐药性的重要候选脆弱性。该发现在经过严格的Benjamini-Hochberg错误发现率校正后仍保持显著性（q = 0.0292，对数秩检验p = 0.0007），并成功预测了独立小鼠队列中显著的体内肿瘤体积缩小（混合效应LMM p = 0.0373）。通过将智能体假设生成与统计有界的临床生存相结合，该框架为生物医学发现的自动计算优先级排序建立了一种可验证的本地范例。

## Abstract
The acceleration of automated scientific discovery has been fundamentally bottlenecked by the epistemic gap between the semantic reasoning of large language models (LLMs) and the complex, non-linear reality of mammalian biology. While recent multi-agent frameworks have achieved autonomous hypothesis generation and in vitro experimental analysis, they frequently lack the rigorous statistical constraints required for multi-scale clinical translation. Furthermore, while algorithmic clinical digital twins successfully forecast biological states, they often rely on opaque latent spaces, sacrificing mechanistic interpretability for predictive accuracy. Here, we introduce the Multi-Scale Autonomous Discovery Engine (Octopus), a neuro-symbolic framework that unites a fully localised, privacy-preserving multi-agent swarm with regularised predictive algorithmic environments. Rather than stopping at isolated cellular assays, the system autonomously prioritises therapeutic hypotheses against in vitro CRISPR dependency data (CCLE), traces feature attribution cascades using XGBoost SHAP vectors, and orthogonally translates emergent vulnerabilities in silico to predict in vivo mammalian tumour trajectory (PDX) and human overall survival (Marisa). In a fully unsupervised sweep of colorectal cancer transcriptomes, the pipeline autonomously prioritised Insulin-like Growth Factor 2 (IGF2) as a significant candidate vulnerability to 5-Fluorouracil resistance. The discovery maintained significance after rigorous Benjamini-Hochberg false discovery rate correction (q = 0.0292, Log-Rank p = 0.0007) and successfully predicted significant in vivo tumour volume shrinkage in an independent mouse cohort (Mixed-Effects LMM p = 0.0373). By bridging agentic hypothesis generation with statistically bounded clinical survival, this framework establishes a verifiable, local paradigm for the automated computational prioritisation of biomedical discoveries.

---

## 论文详细总结（自动生成）

# 基于多尺度人工智能群落的结直肠癌脆弱性自主计算优先级排序——论文详细总结

## 1. 核心问题与研究动机

- **背景**：大语言模型（LLMs）在自动科学发现中展现出巨大潜力，多智能体系统已经能够自主生成假设并分析体外实验数据。然而，当前框架在从体外（in vitro）向体内（in vivo）及临床（in clinico）转化时存在根本性认知鸿沟：
  - 语义推理的“合理性”缺乏严格的统计约束，容易产生假阳性。
  - 临床数字孪生（如深度神经网络）虽然预测精度高，但依赖不透明潜在空间，牺牲了机制可解释性。
  - 现有系统多依赖云端API，无法在受数据隐私法规（如HIPAA、GDPR）约束的临床环境下部署。
- **核心问题**：如何构建一个既能利用LLM的生成推理能力，又能严格绑定统计验证和可解释机制的系统，实现从假设生成到多尺度临床生存验证的端到端自动化。
- **整体含义**：论文提出了一个神经符号框架“Octopus”，通过将局部隐私保护的LLM多智能体群落与正则化预测算法环境（XGBoost数字孪生）相结合，桥接语义推理与统计有界的临床生存验证，为自动化生物医学发现建立了可验证的本地范例。

## 2. 方法论：核心思想与关键技术细节

- **核心思想**：将LLM的语义推理严格约束在数学可验证的参数空间内。系统使用有向无环图（DAG）架构，LLM仅与数字孪生产生的数学输出交互，所有假设必须通过特征归因级联（SHAP）和生存统计验证。

- **关键技术细节**：
  1. **局部隐私保护的多智能体群体**：
     - 使用4位量化的Gemma-4模型，通过llama.cpp后端完全在本地离线运行。
     - 采用CrewAI编排器，使用单行对话模板和精确停止令牌匹配（<end_of_turn>），避免Tokenizer幻觉和JSON解析错误。
     - GPU VRAM上下文窗口在生成周期之间自动清空，确保数据隐私和计算稳定性。
  2. **算法世界模型（数字孪生）**：
     - 基于XGBoost构建。对CCLE肠道谱系细胞系训练，预测5-氟尿嘧啶（5-FU）耐药的AUC值。
     - 严格正则化：树数量N=80，最大深度=1，学习率=0.05，L1正则化α=0.5，L2正则化λ=1.0。
     - 高变异特征筛选：将特征空间过滤至前300个高变异转录本，避免小样本过拟合。
  3. **因果SHAP级联模拟CRISPR**：
     - 使用原生XGBoost SHAP向量（pred_contribs=True）。
     - 模拟基因敲除：自动将目标基因特征零掩码，通过预测器迭代传递。
     - 引入递归衰减系数（λ=0.5）模拟下游信号传导退化，在三个离散时间步（t1,t2,t3）计算SHAP值绝对散度级联，形成可验证的机制路径。
  4. **多尺度验证流程**：
     - 体外→体内→临床全自动管道。
     - 使用lifelines库自动计算Kaplan-Meier生存估计、Log-Rank检验、多变量Cox比例风险回归（校正年龄、分期、MSI、CMS），并验证PH假设。
     - 所有P值经Benjamini-Hochberg FDR校正（q<0.05为显著）。
     - 体内验证使用线性混合效应模型（LMM）按患者来源分组。

- **流程（文字说明）**：
  1. 数据输入：CCLE（体外）、PDX（体内小鼠）、Marisa（临床人类）三个队列。
  2. 建立数字孪生：训练XGBoost模型预测5-FU耐药性。
  3. 多智能体群体扫描高变异转录本，针对每个基因计算SHAP级联。
  4. 验证在临床队列中的生存显著性（Log-Rank+FDR校正）。
  5. 若显著，进一步在PDX小鼠队列中验证肿瘤体积响应。
  6. 输出最终优先排序的候选脆弱点。

## 3. 实验设计

- **数据集**：
  - 体外：CCLE（癌症细胞系百科全书）肠道谱系细胞系，包含转录组表达和GDSC2药物敏感性（AUC值）。
  - 体内：独立PDX（患者来源异种移植）小鼠队列（N=86只小鼠），包含基因表达和肿瘤体积变化轨迹。
  - 临床：Marisa队列（GSE39582），585名结直肠癌患者，含基因表达芯片和总生存时间。
- **数据管理**：使用严格类型的Polars列式数据湖，进行确定性模式对齐和低方差特征修剪。
- **任务**：无监督扫描高变异转录本（约300个），自主优先排序最显著的5-FU耐药候选脆弱点。
- **基准/对比方法**：论文未设置显式对比方法（如与其他多智能体框架的定量比较）。其主要对比对象是现有系统的局限性（缺乏统计验证、云端依赖、可解释性差）。
- **评估指标**：
  - 体外：XGBoost数字孪生的R²（0.50）。
  - 临床：Log-Rank p值、Benjamini-Hochberg校正q值、Cox比例风险HR及95% CI。
  - 体内：混合效应LMM p值。

**实验充分性与客观性**：
- 实验覆盖了从分子（转录组）到细胞（体外CRISPR模拟）再到动物（体内PDX）和人类临床生存的完整转化链条。
- 严格遵循了预先定义的分层策略（中位数表达分组），避免阈值优化偏倚。
- 使用FDR校正控制多重假设检验中的假阳性。
- 多变量Cox回归校正了关键临床混杂因素。
- 但缺乏与其他自动化发现系统（如Co-Scientist、Robin等）在相同任务上的直接定量对比。

## 4. 资源与算力

- **文中明确说明**：
  - 使用4位量化的Gemma-4模型，通过llama.cpp后端完全本地运行（无云端API调用）。
  - GPU VRAM上下文窗口在循环之间自动清空。
- **未明确说明**：
  - GPU型号、数量、训练XGBoost的算力需求、推理时间等具体细节未给出。
  - 因此无法评估算力开销的具体量级。

## 5. 实验数量与充分性

- **实验组数**：
  - 主要进行了**一次无监督扫描**：对300个高变异转录本逐一计算Log-Rank p值和FDR校正。
  - 最终自主优先候选为IGF2，并进行了全面的体内外验证。
  - 未包含消融实验（如去掉SHAP级联、去掉正则化等对结果的影响）。
  - 未在另一个独立癌症类型或药物上进行泛化性测试。
- **充分性评价**：
  - 优点：多尺度验证链条完整（体外、体内、临床），统计方法稳健。
  - 不足：仅验证了一个候选基因（IGF2）；缺乏与基线方法的对比；无超参数敏感性分析；未做交叉验证或其他重复实验以评估框架的稳定性。总体实验数量偏少，但作为概念验证和框架展示，其核心证据链是闭环的。

## 6. 主要结论与发现

- **主要发现**：Octopus框架在完全无监督条件下，自主将**胰岛素样生长因子2（IGF2）** 优先排序为结直肠癌5-氟尿嘧啶（5-FU）耐药的重要候选脆弱点。
- **统计证据**：
  - 临床：高IGF2表达组总生存期显著缩短（Log-Rank p=0.0007），经FDR校正后仍显著（q=0.0292）。
  - 多变量Cox回归：HR=1.09（95% CI 1.02–1.16），校正年龄、分期、MSI、CMS后仍显著。
  - 体内：PDX小鼠中，高IGF2表达组肿瘤体积缩小显著弱于低表达组（混合效应LMM p=0.0373）。
- **机制解释**：SHAP级联显示IGF2过表达通过激活PI3K/AKT/mTOR通路，抑制5-FU诱导的凋亡信号，形成代偿性生存机制。
- **总体结论**：该框架成功桥接了智能体假设生成与统计有界的多尺度临床生存验证，建立了可验证的本地自动化计算优先范式。

## 7. 优点

- **隐私安全**：完全本地化的量化LLM，避免敏感基因组数据外传，适合医院IT架构。
- **可解释性**：通过SHAP特征归因级联显式描绘机制路径，避免了黑箱问题。
- **统计严谨**：强制FDR校正、多变量Cox回归、PH假设检验，防止假阳性。
- **多尺度闭环**：一次性完成体外→体内→临床的自动化验证，而不仅仅是体外假设生成。
- **零语义幻觉**：通过DAG约束、停止令牌匹配和上下文清空，严格防止LLM推理循环和Token Hallucination。
- **技术堆栈**：使用Polars、XGBoost、lifelines等成熟开源库，可复现性好。

## 8. 不足与局限

- **模拟精度有限**：CRISPR模拟仅基于批量转录组数据，未包含翻译后修饰、表观遗传沉默、肿瘤微环境空间动力学等因素；也未模拟CRISPR双链断裂诱发的动态补偿机制。
- **混杂因素控制**：尽管Cox回归校正了年龄、分期、MSI、CMS等，但未来需要整合空间病理特征以排除微环境混杂。
- **缺乏前瞻性验证**：所有验证均基于回顾性队列（CCLE、PDX、Marisa），缺乏前瞻性随机临床试验。
- **实验范围窄**：
  - 仅针对结直肠癌和5-FU一种药物，泛化性未测试。
  - 仅在无监督扫描中确认了IGF2一个候选，未展示框架在其他基因上的表现。
- **未与基线方法对比**：没有量化相比现有方法（如单纯XGBoost+SHAP、或使用云端LLM的框架）的性能提升。
- **算力需求不透明**：未提供运行时间、GPU型号等细节，可复现性受限。
- **统计严格性代价**：高度正则化的XGBoost（max_depth=1）可能限制了对复杂互作用的捕捉（R²=0.50相对中等）。

（完）
