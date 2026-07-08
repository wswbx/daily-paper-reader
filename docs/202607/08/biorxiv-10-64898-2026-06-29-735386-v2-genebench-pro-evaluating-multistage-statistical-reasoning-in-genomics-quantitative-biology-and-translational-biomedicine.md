---
title: "GeneBench-Pro: Evaluating Multistage Statistical Reasoning in Genomics, Quantitative Biology, and Translational Biomedicine"
title_zh: GeneBench-Pro：评估基因组学、定量生物学和转化医学中的多阶段统计推理
authors: "Li, J. H., Ho, A. J."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735386v2.full.pdf"
tags: ["query:ar"]
score: 6.0
evidence: AI智能体多阶段科学分析基准
tldr: "基因学、定量生物学和转化生物医学领域的AI代理需执行多阶段科学分析。GeneBench-Pro扩展了GeneBench，包含129个评估问题，覆盖10个主领域21个子领域，要求代理在多个决策点中正确选择分析路径。GPT-5.6 Sol达到28.7%的通过率，GPT-5.6 Sol Pro为31.5%，而最强非GPT模型Claude Opus 4.8仅16.0%。该基准衡量长期生物推理能力，揭示了模型在行动与认知之间的差距。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准缺乏对多阶段统计推理和实际科学决策复杂性的评估，需要更真实的基准。
method: GeneBench-Pro包含129个问题，涉及10个主领域，每个问题提供上下文和估计目标，代理需自主导航多个依赖决策点。
result: "GPT-5.6 Sol通过率28.7%，GPT-5.6 Sol Pro 31.5%，GPT-5.5 12.0%，Claude Opus 4.8 16.0%。"
conclusion: 模型在局部诊断信号识别上表现良好，但难以将信息传播至后续分析决策，长时程生物推理仍不可靠。
---

## 摘要
我们推出了GeneBench-Pro，这是GeneBench的扩展和改进版本，涵盖了更广泛领域中更困难的问题。GeneBench-Pro是一个基准测试，用于评估AI代理在基因组学、定量生物学和转化医学中执行逼真的多阶段科学分析的能力，旨在捕捉计算生命科学家在需要得出科学或转化决策所依赖的结论时所面临的现实问题的复杂性。该基准包含129个评估问题，针对10个主要领域和21个终端子领域中直接实际相关的数量，以基因组学为核心。与GeneBench类似，每个问题为代理提供简要背景、目标估计量以及极少的其他指导；代理必须导航多个依赖决策点，即存在实质性推断分叉（一个看似合理的错误选择会改变下游分析）的地方，以识别并执行正确的分析工作流程并得出正确答案。相对于GeneBench，GeneBench-Pro新增了29个问题，删除了3个问题，并对剩余100个重叠问题中的54个进行了显著重新设计。129个问题中的82个由外部领域专家评审，根据评审结果对提示/数据进行了修改，并对那些目标不够明确的问题进行了重新设计。十个经过外部评审的问题公开发布，50个保留的问题提供给Artificial Analysis进行独立的第三方模型基准测试，其余问题作为内部保留。在完整的129个问题套件评估中，GPT-5.6 Sol在最大推理级别达到了28.7%的评估级通过率，而在单独报告的GPT Pro运行中，GPT-5.6 Sol Pro达到了31.5%。GPT-5.5达到12.0%，GPT-5.4达到8.9%，最强的非GPT基线Claude Opus 4.8达到16.0%。与GeneBench类似，模型通常能完成工作流程的大部分内容，但在注意到局部诊断信号并将其影响传播到相应的分析决策方面表现出持续的差距。因此，模型经常选择错误的估计量，或者坚持最初看似合理但实际不正确的分析路径。因此，GeneBench-Pro衡量了长期生物推理的一种新兴能力，这种能力目前仍然不可靠。



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="Figure 1">
View larger version (13K):
org.highwire.dtl.DTLVardef@1abbf01org.highwire.dtl.DTLVardef@88edf9org.highwire.dtl.DTLVardef@1bf8e4dorg.highwire.dtl.DTLVardef@1177183_HPS_FORMAT_FIGEXP  M_FIG C_FIG

## Abstract
We introduce GeneBench-Pro, an expanded and improved version of GeneBench that comprises harder problems across a wider breadth of domains. GeneBench-Pro is a benchmark for AI agents performing realistic multi-stage scientific analyses in genomics, quantitative biology, and translational biomedicine which seeks to capture the complexity of real-world problems that computational life scientists face when tasked with producing a conclusion upon which a downstream scientific or translational decision is contingent. The benchmark comprises 129 evaluations targeting quantities of direct practical relevance across 10 primary domains and 21 terminal subdomains, with a genomics-centered core. Similarly to GeneBench, each problem provides the agent with brief context, a target estimand, and minimal guidance otherwise; the agent must then navigate multiple dependent decision points; i.e., substantive inferential forks where a plausible wrong choice changes the downstream analysis, to identify and execute the correct analysis workflow and arrive at the correct answer. Relative to GeneBench, GeneBench-Pro adds 29 new problems, drops three, and introduces significantly redesigned versions of 54 of the remaining 100 overlapping problems. 82 of the 129 problems were reviewed by external domain experts, whose findings led to prompt/data modifications and redesign of those problems whose targets were not sufficiently identifiable. Ten externally reviewed problems are released publicly, 50 held-out problems were provided to Artificial Analysis for independent third-party model benchmarking, and the remainder are retained as an internal holdout. In evaluations over the full 129-problem suite, GPT-5.6 Sol reaches an eval-level pass rate of 28.7% at the max reasoning level, and GPT-5.6 Sol Pro reaches 31.5% in separately reported GPT Pro runs. GPT-5.5 reaches 12.0%, GPT-5.4 reaches 8.9%, and the strongest non-GPT baseline, Claude Opus 4.8, reaches 16.0%. As with GeneBench, models often complete substantial portions of the workflow but exhibit a consistent gap between noticing and acting by identifying local diagnostic signals but failing to propagate the implications to the corresponding analysis decision. As a result, models often select wrong estimators or persist on initially plausible but incorrect analysis paths. GeneBench-Pro therefore measures an emerging capability of long-horizon biological reasoning that remains unreliable.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="Figure 1">
View larger version (13K):
org.highwire.dtl.DTLVardef@1abbf01org.highwire.dtl.DTLVardef@88edf9org.highwire.dtl.DTLVardef@1bf8e4dorg.highwire.dtl.DTLVardef@1177183_HPS_FORMAT_FIGEXP  M_FIG C_FIG