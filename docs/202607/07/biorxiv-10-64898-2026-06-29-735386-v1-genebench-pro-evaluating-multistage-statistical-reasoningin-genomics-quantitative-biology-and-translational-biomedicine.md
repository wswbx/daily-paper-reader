---
title: "GeneBench-Pro: Evaluating Multistage Statistical Reasoning\\\\in Genomics, Quantitative Biology, and Translational Biomedicine"
title_zh: GeneBench-Pro：评估基因组学、定量生物学与转化生物医学中的多阶段统计推理
authors: "Li, J. H., Ho, A. J."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735386v1.full.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 人工智能智能体多阶段科学推理基准
tldr: "GeneBench-Pro是一个扩展的基准，用于评估AI代理在基因组学、定量生物学和转化生物医学中的多阶段统计推理能力。它包含129个实际问题，覆盖10个主要领域，要求模型在多个决策点自主导航。评估显示，GPT-5.6 Sol达到28.7%的通过率，而最强非GPT模型Claude Opus 4.8仅16.0%。模型常完成大部分工作流但未能正确做出关键分析决策，暴露出长期生物推理仍不可靠。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现实中的计算生物学家需要完成多步骤科学分析，现有基准无法反映这种复杂推理，因此需要更难的基准来推动AI发展。
method: 构建129个跨10个领域的问题，每个问题提供简短背景和目标，要求模型自主识别并执行正确的分析工作流，涉及多个关键决策点。
result: "GPT-5.6 Sol通过率28.7%，非GPT最强模型Claude Opus 4.8为16.0%，模型普遍存在识别局部信号但未能影响整体决策的“注意-行动”差距。"
conclusion: GeneBench-Pro衡量了长期生物推理的新兴能力，但当前模型在此任务上仍不可靠，提示需要提升多步推理和决策传播能力。
---

## 摘要
我们推出了GeneBench-Pro，这是GeneBench的扩展和改进版本，包含跨更广泛领域的更难问题。GeneBench-Pro是一个基准测试，用于评估在基因组学、定量生物学和转化生物医学中执行现实多阶段科学分析的AI代理，旨在捕捉计算生命科学家在需要为下游科学或转化决策提供结论时所面临的现实世界问题的复杂性。该基准包含129个评估，针对10个主要领域和21个终端子领域中直接具有实际相关性的量，以基因组学为核心。与GeneBench类似，每个问题为代理提供简要背景、目标估计量，以及极少的其他指导；代理必须导航多个依赖决策点，即实质性的推理岔路口——在这些岔路口，一个看似合理的错误选择会改变下游分析，从而识别并执行正确的分析工作流，并得出正确答案。相对于GeneBench，GeneBench-Pro增加了29个新问题，删除了3个，并对剩余100个重叠问题中的54个进行了显著重新设计。129个问题中有82个由外部领域专家审查，他们的发现导致了对那些目标不够可识别的问题的提示/数据修改和重新设计。十个经过外部审查的问题公开发布，50个保留问题提供给Artificial Analysis进行独立的第三方模型基准测试，其余保留为内部保留集。在完整129个问题套件的评估中，GPT-5.6 Sol在最大推理级别达到28.7%的评估级通过率，而GPT-5.6 Sol Pro在单独报告的GPT Pro运行中达到31.5%。GPT-5.5达到12.0%，GPT-5.4达到8.9%，最强的非GPT基线Claude Opus 4.8达到16.0%。与GeneBench类似，模型通常能完成工作流的相当大一部分，但在注意到和行动之间表现出一贯的差距：识别局部诊断信号，但未能将影响传播到相应的分析决策。因此，模型常常选择错误的估计量，或坚持最初看似合理但实际不正确的分析路径。因此，GeneBench-Pro衡量了一种新兴的长期生物学推理能力，该能力仍然不可靠。

## Abstract
We introduce GeneBench-Pro, an expanded and improved version of GeneBench that comprises harder problems across a wider breadth of domains. GeneBench-Pro is a benchmark for AI agents performing realistic multi-stage scientific analyses in genomics, quantitative biology, and translational biomedicine which seeks to capture the complexity of real-world problems that computational life scientists face when tasked with producing a conclusion upon which a downstream scientific or translational decision is contingent. The benchmark comprises 129 evaluations targeting quantities of direct practical relevance across 10 primary domains and 21 terminal subdomains, with a genomics-centered core. Similarly to GeneBench, each problem provides the agent with brief context, a target estimand, and minimal guidance otherwise; the agent must then navigate multiple dependent decision points; i.e., substantive inferential forks where a plausible wrong choice changes the downstream analysis, to identify and execute the correct analysis workflow and arrive at the correct answer. Relative to GeneBench, GeneBench-Pro adds 29 new problems, drops three, and introduces significantly redesigned versions of 54 of the remaining 100 overlapping problems. 82 of the 129 problems were reviewed by external domain experts, whose findings led to prompt/data modifications and redesign of those problems whose targets were not sufficiently identifiable. Ten externally reviewed problems are released publicly, 50 held-out problems were provided to Artificial Analysis for independent third-party model benchmarking, and the remainder are retained as an internal holdout. In evaluations over the full 129-problem suite, GPT-5.6 Sol reaches an eval-level pass rate of 28.7% at the max reasoning level, and GPT-5.6 Sol Pro reaches 31.5% in separately reported GPT Pro runs. GPT-5.5 reaches 12.0%, GPT-5.4 reaches 8.9%, and the strongest non-GPT baseline, Claude Opus 4.8, reaches 16.0%. As with GeneBench, models often complete substantial portions of the workflow but exhibit a consistent gap between noticing and acting by identifying local diagnostic signals but failing to propagate the implications to the corresponding analysis decision. As a result, models often select wrong estimators or persist on initially plausible but incorrect analysis paths. GeneBench-Pro therefore measures an emerging capability of long-horizon biological reasoning that remains unreliable.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="Figure 1">
View larger version (13K):
org.highwire.dtl.DTLVardef@113198borg.highwire.dtl.DTLVardef@f2225corg.highwire.dtl.DTLVardef@ae01fforg.highwire.dtl.DTLVardef@52f92_HPS_FORMAT_FIGEXP  M_FIG C_FIG