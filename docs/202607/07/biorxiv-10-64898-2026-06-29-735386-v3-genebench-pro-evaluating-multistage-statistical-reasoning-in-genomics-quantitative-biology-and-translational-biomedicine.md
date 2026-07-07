---
title: "GeneBench-Pro: Evaluating Multistage Statistical Reasoning in Genomics, Quantitative Biology, and Translational Biomedicine"
title_zh: GeneBench-Pro：评估基因组学、定量生物学和转化医学中的多阶段统计推理
authors: "Li, J. H., Ho, A. J."
date: 2026-07-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735386v3.full.pdf"
tags: ["query:ar"]
score: 6.0
evidence: 评估AI代理在科学发现中表现的基准，与自主研究主题相关
tldr: "AI在基因组学、定量生物学等领域的多阶段科学推理评估不足。GeneBench-Pro通过129个实际问题，覆盖10个主领域，要求模型自主完成多步分析工作流。结果显示最强模型GPT-5.6 Sol Pro仅达31.5%通过率，模型常能识别局部诊断信号却无法传播至全局决策。该基准衡量了长期生物推理的涌现能力，揭示了注意与行动之间的可靠差距。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准无法评估AI在真实多阶段科学分析中的统计推理能力，尤其涉及多个依赖决策点的场景。
method: 构建GeneBench-Pro基准，包含129个多步分析问题，覆盖10个主领域和21个子领域，要求模型自主选择正确工作流并给出结论。
result: "GPT-5.6 Sol Pro在最大推理水平下达到31.5%通过率，GPT-5.5仅12.0%，最強非GPT模型Claude Opus 4.8为16.0%。"
conclusion: 模型在长程生物推理中普遍存在局部诊断正确但无法全局传播的差距，该能力仍不可靠。
---

## 摘要
我们推出了GeneBench-Pro，这是GeneBench的扩展和改进版本，包含更广泛领域中更困难的问题。GeneBench-Pro是一个基准，用于评估AI智能体在基因组学、定量生物学和转化医学中执行逼真的多阶段科学分析的能力，旨在捕捉计算生命科学家在需要得出下游科学或转化决策所依赖的结论时所面临的现实问题的复杂性。该基准包含129个评估问题，针对10个主要领域和21个终端子领域中具有直接实际意义的量，以基因组学为核心。与GeneBench类似，每个问题为智能体提供简要背景、目标估计量和极少的指导；智能体必须导航多个依赖决策点，即实质性的推断分叉，其中看似合理的错误选择会改变下游分析，以识别并执行正确的分析工作流并得出正确答案。相对于GeneBench，GeneBench-Pro新增了29个问题，删除了3个，并对剩余100个重叠问题中的54个进行了重大重新设计。129个问题中有82个由外部领域专家评审，其发现导致对提示/数据修改以及目标不够可识别的问题进行重新设计。十个外部评审的问题已公开发布，50个保留问题提供给Artificial Analysis进行独立的第三方模型基准测试，其余保留为内部保留集。在全部129个问题的评估中，GPT-5.6 Sol在最大推理级别上达到28.7%的评估级通过率，而GPT-5.6 Sol Pro在单独报告的GPT Pro运行中达到31.5%。GPT-5.5达到12.0%，GPT-5.4达到8.9%，最强的非GPT基线Claude Opus 4.8达到16.0%。与GeneBench一样，模型通常能完成工作流的很大一部分，但在识别局部诊断信号后未能将影响传播到相应的分析决策，从而在注意和行动之间存在一致的差距。因此，模型常常选择错误的估计量或坚持最初看似合理但错误的分析路径。因此，GeneBench-Pro衡量了一种新兴的长期生物推理能力，该能力仍然不可靠。

## Abstract
We introduce GeneBench-Pro, an expanded and improved version of GeneBench that comprises harder problems across a wider breadth of domains. GeneBench-Pro is a benchmark for AI agents performing realistic multi-stage scientific analyses in genomics, quantitative biology, and translational biomedicine which seeks to capture the complexity of real-world problems that computational life scientists face when tasked with producing a conclusion upon which a downstream scientific or translational decision is contingent. The benchmark comprises 129 evaluations targeting quantities of direct practical relevance across 10 primary domains and 21 terminal subdomains, with a genomics-centered core. Similarly to GeneBench, each problem provides the agent with brief context, a target estimand, and minimal guidance otherwise; the agent must then navigate multiple dependent decision points; i.e., substantive inferential forks where a plausible wrong choice changes the downstream analysis, to identify and execute the correct analysis workflow and arrive at the correct answer. Relative to GeneBench, GeneBench-Pro adds 29 new problems, drops three, and introduces significantly redesigned versions of 54 of the remaining 100 overlapping problems. 82 of the 129 problems were reviewed by external domain experts, whose findings led to prompt/data modifications and redesign of those problems whose targets were not sufficiently identifiable. Ten externally reviewed problems are released publicly, 50 held-out problems were provided to Artificial Analysis for independent third-party model benchmarking, and the remainder are retained as an internal holdout. In evaluations over the full 129-problem suite, GPT-5.6 Sol reaches an eval-level pass rate of 28.7% at the max reasoning level, and GPT-5.6 Sol Pro reaches 31.5% in separately reported GPT Pro runs. GPT-5.5 reaches 12.0%, GPT-5.4 reaches 8.9%, and the strongest non-GPT baseline, Claude Opus 4.8, reaches 16.0%. As with GeneBench, models often complete substantial portions of the workflow but exhibit a consistent gap between noticing and acting by identifying local diagnostic signals but failing to propagate the implications to the corresponding analysis decision. As a result, models often select wrong estimators or persist on initially plausible but incorrect analysis paths. GeneBench-Pro therefore measures an emerging capability of long-horizon biological reasoning that remains unreliable.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="Figure 1">
View larger version (13K):
org.highwire.dtl.DTLVardef@113198borg.highwire.dtl.DTLVardef@f2225corg.highwire.dtl.DTLVardef@ae01fforg.highwire.dtl.DTLVardef@52f92_HPS_FORMAT_FIGEXP  M_FIG C_FIG