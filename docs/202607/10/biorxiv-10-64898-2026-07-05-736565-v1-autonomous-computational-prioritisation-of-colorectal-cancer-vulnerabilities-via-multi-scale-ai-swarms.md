---
title: Autonomous computational prioritisation of colorectal cancer vulnerabilities via multi-scale AI swarms
title_zh: 基于多尺度人工智能群体的结直肠癌脆弱性自主计算优先级排序
authors: "Baker, C., Ren, T., Rafferty, K., Wang, H., McDade, S."
date: 2026-07-10
pdf: "https://www.biorxiv.org/content/10.64898/2026.07.05.736565v1.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: 用于癌症生物学科学发现的自主AI群体
tldr: 自动科学发现受限于大语言模型与复杂生物学间的认知差距，现有框架缺乏统计约束。提出Octopus神经符号框架，结合本地化多智能体群与正则化预测环境，利用CRISPR数据自主优先排序脆弱性。在结直肠癌转录组无监督扫描中自动识别IGF2为5-FU耐药候选脆弱性，经BH校正显著，并预测小鼠肿瘤体积缩小。建立了可验证的本地化自动计算优先排序范式，桥接假设生成与临床生存统计约束。
source: biorxiv
selection_source: fresh_fetch
figures_json: "[{\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 921, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1851, \"height\": 678, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 922, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/biorxiv/biorxiv-10-64898-2026-07-05-736565-v1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 906, \"height\": 838, \"label\": \"Figure\"}]"
motivation: 克服大语言模型与复杂生物学间的认知差距，解决现有框架缺乏统计约束和可解释性的问题。
method: 提出Octopus框架，融合本地化多智能体群与正则化预测环境，通过XGBoost SHAP和CRISPR数据自主优先排序脆弱性。
result: 自动识别IGF2为结直肠癌5-FU耐药脆弱性，BH校正q=0.0292，预测小鼠肿瘤体积缩小p=0.0373。
conclusion: 建立了可验证的本地化自动计算优先排序范式，桥接假设生成与临床生存统计约束。
---

## 摘要
自动化科学发现的加速从根本上受到大型语言模型的语义推理与哺乳动物生物学复杂非线性现实之间认知差距的阻碍。尽管最近的多智能体框架实现了自主假设生成和体外实验分析，但它们通常缺乏多尺度临床转化所需的严格统计约束。此外，虽然算法临床数字孪生成功预测了生物学状态，但它们往往依赖不透明的潜在空间，牺牲机制可解释性以换取预测准确性。在此，我们引入了多尺度自主发现引擎（Octopus），这是一种神经符号框架，将完全本地化、保护隐私的多智能体群体与正则化预测算法环境相结合。该系统不局限于孤立的细胞分析，而是根据体外CRISPR依赖性数据（CCLE）自主优先排序治疗假设，使用XGBoost SHAP向量追踪特征归因级联，并通过正交方式将在硅学中出现的脆弱性转化为预测体内哺乳动物肿瘤轨迹（PDX）和人类总生存期（Marisa）。在对结直肠癌转录组进行完全无监督的扫描中，该流程自主将胰岛素样生长因子2（IGF2）优先排序为5-氟尿嘧啶耐药性的重要候选脆弱性。该发现在经过严格的Benjamini-Hochberg假发现率校正后仍保持显著性（q = 0.0292，对数秩检验p = 0.0007），并成功预测了独立小鼠队列中体内肿瘤体积的显著缩小（混合效应LMM p = 0.0373）。通过将智能体假设生成与统计约束的临床生存相结合，该框架为生物医学发现的自动化计算优先级排序建立了一个可验证的本地范式。

## Abstract
The acceleration of automated scientific discovery has been fundamentally bottlenecked by the epistemic gap between the semantic reasoning of large language models (LLMs) and the complex, non-linear reality of mammalian biology. While recent multi-agent frameworks have achieved autonomous hypothesis generation and in vitro experimental analysis, they frequently lack the rigorous statistical constraints required for multi-scale clinical translation. Furthermore, while algorithmic clinical digital twins successfully forecast biological states, they often rely on opaque latent spaces, sacrificing mechanistic interpretability for predictive accuracy. Here, we introduce the Multi-Scale Autonomous Discovery Engine (Octopus), a neuro-symbolic framework that unites a fully localised, privacy-preserving multi-agent swarm with regularised predictive algorithmic environments. Rather than stopping at isolated cellular assays, the system autonomously prioritises therapeutic hypotheses against in vitro CRISPR dependency data (CCLE), traces feature attribution cascades using XGBoost SHAP vectors, and orthogonally translates emergent vulnerabilities in silico to predict in vivo mammalian tumour trajectory (PDX) and human overall survival (Marisa). In a fully unsupervised sweep of colorectal cancer transcriptomes, the pipeline autonomously prioritised Insulin-like Growth Factor 2 (IGF2) as a significant candidate vulnerability to 5-Fluorouracil resistance. The discovery maintained significance after rigorous Benjamini-Hochberg false discovery rate correction (q = 0.0292, Log-Rank p = 0.0007) and successfully predicted significant in vivo tumour volume shrinkage in an independent mouse cohort (Mixed-Effects LMM p = 0.0373). By bridging agentic hypothesis generation with statistically bounded clinical survival, this framework establishes a verifiable, local paradigm for the automated computational prioritisation of biomedical discoveries.