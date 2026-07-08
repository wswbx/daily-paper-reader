---
title: "GeneBench-Pro: Evaluating Multistage Statistical Reasoning\\\\in Genomics, Quantitative Biology, and Translational Biomedicine"
title_zh: GeneBench-Pro：评估基因组学、定量生物学与转化生物医学中的多阶段统计推理
authors: "Li, J. H., Ho, A. J."
date: 2026-06-30
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.29.735386v1.full.pdf"
tags: ["query:ar"]
score: 8.0
evidence: AI自主研究系统评估基准
tldr: "GeneBench-Pro是一个用于评估AI代理在基因组学、定量生物学和转化生物医学中进行多阶段统计推理的基准。它包含129个需要复杂决策链的问题，覆盖10个领域。评估显示最强模型GPT-5.6 Sol Pro仅达31.5% pass rate，且模型常在识别局部信号后未能正确传播决策。该基准揭示了当前模型在长程生物推理中的不足，为未来研究提供了重要测试平台。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有基准缺乏对AI在多步骤科学分析中依赖决策点的评估，GeneBench-Pro旨在填补这一空白。
method: 构建包含129个评估问题的基准，每个问题需代理在多阶段决策点中自主选择分析路径并得出正确答案。
result: "GPT-5.6 Sol Pro达31.5%最高通过率，Claude Opus 4.8为16.0%，模型普遍存在“发现但不行动”的决策失败模式。"
conclusion: GeneBench-Pro系统衡量了长程生物推理这一新兴但不可靠的能力，为AI在复杂科学分析中的进展设立了标杆。
---

## 摘要
我们推出了 GeneBench-Pro，这是 GeneBench 的扩展与改进版本，包含了跨更广泛领域的更难题。GeneBench-Pro 是一个面向 AI 智能体的基准测试，用于在基因组学、定量生物学和转化生物医学领域执行现实的多阶段科学分析，旨在捕捉计算生命科学家在需要得出一个影响下游科学或转化决策的结论时所面临现实问题的复杂性。该基准测试包含 129 项评估，针对 10 个主要领域和 21 个终端子领域中具有直接实际相关性的量，核心以基因组学为中心。与 GeneBench 类似，每个问题为智能体提供简要背景、目标估计量以及最少的其他指导；智能体随后必须处理多个相互依赖的决策点，即存在实质性的推理分岔，其中看似合理的错误选择会改变下游分析，从而识别并执行正确的分析工作流，得出正确答案。相比 GeneBench，GeneBench-Pro 新增了 29 个问题，移除了 3 个，并对剩余 100 个重叠问题中的 54 个进行了重大重新设计。129 个问题中有 82 个由外部领域专家审核，其发现导致了提示/数据修改，并重新设计了那些目标不够明确的问题。十个人工审核的问题已公开发布，50 个保留问题已提供给 Artificial Analysis 用于独立的第三方模型基准测试，其余问题作为内部保留。在全部 129 个问题的评估中，GPT-5.6 Sol 在最大推理水平上达到了 28.7% 的评估级通过率，而 GPT-5.6 Sol Pro 在单独报告的 GPT Pro 运行中达到了 31.5%。GPT-5.5 达到 12.0%，GPT-5.4 达到 8.9%，最强的非 GPT 基线模型 Claude Opus 4.8 达到 16.0%。与 GeneBench 类似，模型通常能完成工作流的很大一部分，但在注意到和行动之间始终存在差距：能够识别局部诊断信号，但未能将含义传播到相应的分析决策中。因此，模型经常选择错误的估计量，或者坚持最初看似合理但错误的分析路径。因此，GeneBench-Pro 衡量了一种新兴的长期生物学推理能力，该能力仍然不可靠。

## Abstract
We introduce GeneBench-Pro, an expanded and improved version of GeneBench that comprises harder problems across a wider breadth of domains. GeneBench-Pro is a benchmark for AI agents performing realistic multi-stage scientific analyses in genomics, quantitative biology, and translational biomedicine which seeks to capture the complexity of real-world problems that computational life scientists face when tasked with producing a conclusion upon which a downstream scientific or translational decision is contingent. The benchmark comprises 129 evaluations targeting quantities of direct practical relevance across 10 primary domains and 21 terminal subdomains, with a genomics-centered core. Similarly to GeneBench, each problem provides the agent with brief context, a target estimand, and minimal guidance otherwise; the agent must then navigate multiple dependent decision points; i.e., substantive inferential forks where a plausible wrong choice changes the downstream analysis, to identify and execute the correct analysis workflow and arrive at the correct answer. Relative to GeneBench, GeneBench-Pro adds 29 new problems, drops three, and introduces significantly redesigned versions of 54 of the remaining 100 overlapping problems. 82 of the 129 problems were reviewed by external domain experts, whose findings led to prompt/data modifications and redesign of those problems whose targets were not sufficiently identifiable. Ten externally reviewed problems are released publicly, 50 held-out problems were provided to Artificial Analysis for independent third-party model benchmarking, and the remainder are retained as an internal holdout. In evaluations over the full 129-problem suite, GPT-5.6 Sol reaches an eval-level pass rate of 28.7% at the max reasoning level, and GPT-5.6 Sol Pro reaches 31.5% in separately reported GPT Pro runs. GPT-5.5 reaches 12.0%, GPT-5.4 reaches 8.9%, and the strongest non-GPT baseline, Claude Opus 4.8, reaches 16.0%. As with GeneBench, models often complete substantial portions of the workflow but exhibit a consistent gap between noticing and acting by identifying local diagnostic signals but failing to propagate the implications to the corresponding analysis decision. As a result, models often select wrong estimators or persist on initially plausible but incorrect analysis paths. GeneBench-Pro therefore measures an emerging capability of long-horizon biological reasoning that remains unreliable.



O_FIG O_LINKSMALLFIG WIDTH=200 HEIGHT=46 SRC="FIGDIR/small/735386v2_ufig1.gif" ALT="Figure 1">
View larger version (13K):
org.highwire.dtl.DTLVardef@1abbf01org.highwire.dtl.DTLVardef@88edf9org.highwire.dtl.DTLVardef@1bf8e4dorg.highwire.dtl.DTLVardef@1177183_HPS_FORMAT_FIGEXP  M_FIG C_FIG