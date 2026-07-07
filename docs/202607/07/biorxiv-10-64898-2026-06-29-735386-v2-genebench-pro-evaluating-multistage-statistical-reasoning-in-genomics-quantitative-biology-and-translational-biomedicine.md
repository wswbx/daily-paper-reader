---
title: "GeneBench-Pro: Evaluating Multistage Statistical Reasoning in Genomics, Quantitative Biology, and Translational Biomedicine"
title_zh: GeneBench-Pro：评估基因组学、定量生物学和转化医学中的多阶段统计推理
authors: "Li, J. H., Ho, A. J."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735386v2.full.pdf"
tags: ["query:ar"]
score: 7.0
evidence: 人工智能智能体多阶段科学推理基准
tldr: "基因学、定量生物学和转化生物医学中的多阶段统计推理任务对AI模型构成挑战。GeneBench-Pro扩展了GeneBench，包含129个覆盖10个领域的实际问题，要求模型自主导航多个决策点。评估显示最强模型GPT-5.6 Sol仅达到28.7%的通过率，Claude Opus 4.8为16.0%，模型常识别局部信号但无法全局传播。该基准衡量了长周期生物推理能力，指出当前AI在该任务上仍不可靠。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准缺乏现实多阶段推理问题，无法反映计算生物学家面临的实际决策复杂性。
method: 构建129个跨10个领域的问题，每个问题提供上下文和目标估计量，模型需自主规划并执行正确分析流程。
result: "GPT-5.6 Sol通过率28.7%，Claude Opus 4.8为16.0%，模型常陷于局部正确但全局错误的分析路径。"
conclusion: GeneBench-Pro揭示了AI在长周期生物推理中的持续不足，模型在注意到关键信号与采取正确行动之间存在显著差距。
---

## 摘要
我们推出了GeneBench-Pro，这是GeneBench的扩展和改进版本，包含跨更广泛领域的更难问题。GeneBench-Pro是一个基准测试，用于评估AI代理在基因组学、定量生物学和转化医学中执行现实多阶段科学分析的能力，旨在捕捉计算生命科学家在需要得出下游科学或转化决策所依赖的结论时所面临的真实世界问题的复杂性。该基准测试包含129个评估，针对10个主要领域和21个终端子领域中直接实际相关的量，以基因组学为核心。与GeneBench类似，每个问题为代理提供简要背景、目标估计量以及最低限度的指导；代理随后必须导航多个依赖决策点，即实质性的推理分叉——在这些分叉中，一个看似合理的错误选择会改变下游分析——以识别并执行正确的分析工作流，并得出正确答案。相对于GeneBench，GeneBench-Pro增加了29个新问题，删除了3个问题，并对剩余100个重叠问题中的54个进行了大幅重新设计。129个问题中的82个由外部领域专家审查，其发现导致了对那些目标不够明确的问题的提示/数据修改和重新设计。十个经外部审查的问题公开发布，50个保留问题被提供给Artificial Analysis进行独立的第三方模型基准测试，其余问题作为内部保留。在对全部129个问题的评估中，GPT-5.6 Sol在最大推理水平上达到28.7%的评估级通过率，GPT-5.6 Sol Pro在单独报告的GPT Pro运行中达到31.5%。GPT-5.5达到12.0%，GPT-5.4达到8.9%，最强的非GPT基线Claude Opus 4.8达到16.0%。与GeneBench一样，模型通常完成工作流的绝大部分，但在注意到和采取行动之间始终存在差距：模型能识别局部诊断信号，但未能将影响传播到相应的分析决策。因此，模型经常选择错误的估计量，或坚持起初看似合理但不正确的分析路径。因此，GeneBench-Pro衡量了一种新兴的长期生物推理能力，而这种能力目前仍不可靠。



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="图1">
查看大图 (13K)：
org.highwire.dtl.DTLVardef@113198borg.highwire.dtl.DTLVardef@f2225corg.highwire.dtl.DTLVardef@ae01fforg.highwire.dtl.DTLVardef@52f92_HPS_FORMAT_FIGEXP  M_FIG C_FIG

## Abstract
We introduce GeneBench-Pro, an expanded and improved version of GeneBench that comprises harder problems across a wider breadth of domains. GeneBench-Pro is a benchmark for AI agents performing realistic multi-stage scientific analyses in genomics, quantitative biology, and translational biomedicine which seeks to capture the complexity of real-world problems that computational life scientists face when tasked with producing a conclusion upon which a downstream scientific or translational decision is contingent. The benchmark comprises 129 evaluations targeting quantities of direct practical relevance across 10 primary domains and 21 terminal subdomains, with a genomics-centered core. Similarly to GeneBench, each problem provides the agent with brief context, a target estimand, and minimal guidance otherwise; the agent must then navigate multiple dependent decision points; i.e., substantive inferential forks where a plausible wrong choice changes the downstream analysis, to identify and execute the correct analysis workflow and arrive at the correct answer. Relative to GeneBench, GeneBench-Pro adds 29 new problems, drops three, and introduces significantly redesigned versions of 54 of the remaining 100 overlapping problems. 82 of the 129 problems were reviewed by external domain experts, whose findings led to prompt/data modifications and redesign of those problems whose targets were not sufficiently identifiable. Ten externally reviewed problems are released publicly, 50 held-out problems were provided to Artificial Analysis for independent third-party model benchmarking, and the remainder are retained as an internal holdout. In evaluations over the full 129-problem suite, GPT-5.6 Sol reaches an eval-level pass rate of 28.7% at the max reasoning level, and GPT-5.6 Sol Pro reaches 31.5% in separately reported GPT Pro runs. GPT-5.5 reaches 12.0%, GPT-5.4 reaches 8.9%, and the strongest non-GPT baseline, Claude Opus 4.8, reaches 16.0%. As with GeneBench, models often complete substantial portions of the workflow but exhibit a consistent gap between noticing and acting by identifying local diagnostic signals but failing to propagate the implications to the corresponding analysis decision. As a result, models often select wrong estimators or persist on initially plausible but incorrect analysis paths. GeneBench-Pro therefore measures an emerging capability of long-horizon biological reasoning that remains unreliable.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="Figure 1">
View larger version (13K):
org.highwire.dtl.DTLVardef@113198borg.highwire.dtl.DTLVardef@f2225corg.highwire.dtl.DTLVardef@ae01fforg.highwire.dtl.DTLVardef@52f92_HPS_FORMAT_FIGEXP  M_FIG C_FIG