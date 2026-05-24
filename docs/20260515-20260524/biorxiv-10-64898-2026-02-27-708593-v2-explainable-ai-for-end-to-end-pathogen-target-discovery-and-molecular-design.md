---
title: Explainable AI for end-to-end pathogen target discovery and molecular design
title_zh: 面向端到端病原体靶点发现与分子设计的可解释人工智能
authors: "Jimenez-Castro, L., Fernandez-Ortuno, D., Perez-Garcia, A., Polonio, A."
date: 2026-05-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.02.27.708593v2.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 10.0
evidence: 可解释AI用于病原体靶点发现和分子设计
tldr: 针对药物发现中靶点识别瓶颈，提出可解释AI框架APEX，结合ESM-2、GAT和MLP训练病原体特异性必需性预测器APEX-Tar与通用成药性模型APEX-Drug，利用注意力机制和子图解释指导扩散模型生成抑制剂。在真菌和细菌中识别新靶点（如ADSL、YadV）并设计抑制剂，加速抗菌药物研发。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统药物发现受限于靶点识别，迫切需要跨物种的可解释AI方法以加速抗菌药物开发。
method: 结合ESM-2嵌入、图注意力网络和MLP，训练病原体特异性必需性预测器与通用成药性模型，利用注意力图和子图解释指导结构扩散模型生成抑制剂。
result: APEX-Tar识别真菌腺苷酸琥珀酸裂解酶（ADSL）和细菌粘附素YadV等新靶点；APEX-Drug重现已知结合位点，指导设计ADSL抑制剂并发现YadV新口袋。
conclusion: APEX提供跨物种、可解释的靶点优先排序与分子设计管线，有望加速下一代抗菌药物发现。
---

## 摘要
药物研发受限于靶点识别，这是抗菌药物开发以及应对新型杀菌剂耐药性过程中的主要瓶颈。我们提出了APEX（基于注意力的蛋白质解释器），一个用于跨物种、蛋白质组规模的靶点发现和口袋引导分子设计的可解释人工智能框架。APEX将ESM-2嵌入、图注意力网络（GAT）和多层感知机（MLP）相结合，训练病原体特异性必需性预测器（APEX-Tar）以及一个通用成药性模型（APEX-Drug）。注意力图谱和GNNExplainer导出的子图突出显示驱动预测的残基，从而能够直接条件化基于结构的扩散模型以生成抑制剂。APEX-Tar识别已知真菌靶点中的关键残基，并提名新候选靶点，包括真菌中的腺苷酸琥珀酸裂解酶（ADSL）和细菌黏附素YadV。APEX-Drug重现了已确立的杀菌剂结合位点，指导利用真菌特异性活性位点残基设计ADSL抑制剂，并在YadV中发现了与已知菌毛抑制剂位点不同的先前未被描述的袋状结构。总体而言，APEX提供了一个跨界、可解释的流水线，用于靶点优先级排序和引导分子设计，加速了下一代抗菌药物的寻找。

## Abstract
Drug discovery is limited by target identification, a major bottleneck in antimicrobial development and in combating emerging fungicide resistance. We present APEX (Attention-based Protein EXplainer), an explainable AI framework for cross-species, proteome-scale target discovery and pocket-guided molecular design. APEX combines ESM-2 embeddings, GAT, and a MLP to train pathogen-specific essentiality predictors (APEX-Tar) alongside a universal druggability model (APEX-Drug). Attention maps and GNNExplainer-derived subgraphs highlight residues driving predictions, enabling direct conditioning of structure-based diffusion models for inhibitor generation. APEX-Tar identifies key residues in known fungal targets and nominates new candidates, including adenylosuccinate lyase (ADSL) in fungi and the bacterial adhesin YadV. APEX-Drug recapitulates established fungicide binding sites, guides the design of ADSL inhibitors exploiting a fungal-specific active-site residue, and uncovers in YadV a previously undescribed pocket distinct from known pilicide sites. Together, APEX provides a kingdom-agnostic, explainable pipeline for target prioritization and guided molecular design, accelerating the search for next-generation antimicrobials.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **背景**：抗菌药物和杀菌剂的研发面临严重的耐药性问题，而传统药物发现流程中**靶点识别是主要瓶颈**。现有方法通常局限于单一物种或缺乏可解释性，难以快速筛选和优先排序新靶点。
- **核心问题**：如何实现**跨物种、蛋白质组规模**的靶点发现，并**可解释地指导**针对新靶点的分子设计，以加速下一代抗菌药物的开发。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：构建一个可解释人工智能框架 **APEX**，将蛋白质必需性预测与成药性评估相结合，并通过注意力机制和子图解释直接条件化结构扩散模型，实现靶点优先级排序和口袋引导的抑制剂生成。
- **关键技术细节**：
  - **APEX-Tar**：使用ESM-2提取蛋白质序列嵌入，通过图注意力网络（GAT）建模残基间相互作用，结合多层感知机（MLP）进行二分类（必需/非必需），训练病原体特异性必需性预测器。
  - **APEX-Drug**：训练一个通用**成药性模型**，用于评估蛋白质口袋的可成药性。
  - **可解释性**：利用**注意力图谱**和**GNNExplainer**导出的子图，突出显示驱动预测的关键残基，从而揭示靶点优势结合位点。
  - **分子生成**：将注意力图和子图解释作为条件，输入到**基于结构的扩散模型**中，直接生成针对特定口袋的抑制剂分子。

### 3. 实验设计：数据集、基准与对比方法
- **数据集与场景**：
  - 病原体特异性必需性预测：使用**真菌**（如*Aspergillus fumigatus*）和**细菌**（如*Escherichia coli*）的蛋白质组数据，结合已有必需基因数据库进行训练。
  - 成药性模型：使用已知的成药蛋白/非成药蛋白数据集进行训练。
  - 分子设计：针对新候选靶点**腺苷酸琥珀酸裂解酶（ADSL）**和**细菌黏附素YadV**进行抑制剂生成实验。
- **Benchmark**：验证了APEX-Tar能否识别已知真菌靶点（如CYP51）的关键残基；APEX-Drug能否重现已确立的杀菌剂结合位点（如唑类药物的靶点口袋）。
- **对比方法**：未明确提及与其他方法的定量对比，主要展示自身框架在不同物种和靶点上的定性/定量结果。

### 4. 资源与算力
- **文中未明确说明**使用的GPU型号、数量、训练时长等计算资源信息。仅提到结合ESM-2、GAT等模型，推测需要中等规模GPU（如V100或A100），但具体细节缺失。

### 5. 实验数量与充分性
- **实验数量**：论文主要展示了两个新候选靶点（ADSL、YadV）的案例分析，以及已知靶点的验证实验。未列出大量消融实验或不同病原体的大规模对比。
- **充分性与公平性**：实验相对充分，覆盖了真菌和细菌两个界，验证了可解释性、靶点发现和分子生成的贯通性。但**缺乏与现有靶点预测或分子生成方法（如AlphaFold、Rosetta、传统分子对接）的定量比较**，也未在独立测试集上评估ROC/AUC等指标，客观性有待加强。

### 6. 论文的主要结论与发现
- APEX-Tar成功识别出**真菌腺苷酸琥珀酸裂解酶（ADSL）**和**细菌黏附素YadV**作为具有潜力的新靶点，并在已知靶点上再现了关键结合残基。
- APEX-Drug能够重现已知杀菌剂结合位点，指导生成针对ADSL活性位点（利用真菌特异性残基）的抑制剂，并且在YadV中发现了**与已知菌毛抑制剂位点不同的先前未描述的新口袋**。
- 整体上，APEX提供了一个**跨物种、可解释的靶点优先级排序与分子设计管线**，有望显著加速下一代抗菌药物的发现。

### 7. 优点
- **可解释性突出**：通过注意力图和子图解释揭示关键残基，为靶点选择提供了生物学可理解的信息，增强了AI方法的可信度。
- **跨物种通用性**：框架适用于真菌和细菌，具有扩展到其他病原体的潜力。
- **端到端贯通**：从蛋白质序列到靶点识别，再到口袋引导的分子生成，形成了完整闭环，无需手动特征工程或多个独立步骤。
- **口袋引导扩散模型**：创新性地利用可解释性输出直接条件化扩散模型，实现了针对性的抑制剂设计。

### 8. 不足与局限
- **缺乏湿实验验证**：所有预测和分子设计均停留在计算层面，未进行体外或体内实验验证新靶点的必需性及生成抑制剂的活性，实用性尚需证明。
- **评估不完整**：未与现有SOTA方法（如RoseTTAFold、Tiberius、PocketMiner等）进行定量对比，无法判断性能优势。
- **依赖高质量结构数据**：扩散模型需要蛋白质三维结构，对于缺乏实验结构的蛋白依赖AlphaFold预测，可能引入不确定性。
- **数据集偏差**：必需性和成药性训练数据可能偏向于已知保守通路，对稀有病原体或新机制靶点覆盖不足。
- **算力与复现**：未提供计算资源细节，且源码是否开源未说明，影响可复现性。

（完）
