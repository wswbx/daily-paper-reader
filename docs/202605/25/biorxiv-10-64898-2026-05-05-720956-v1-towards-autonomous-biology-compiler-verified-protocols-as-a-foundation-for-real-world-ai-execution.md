---
title: "Towards autonomous biology: Compiler-Verified Protocols as a Foundation for Real World AI Execution"
title_zh: 迈向自主生物学：编译器验证的协议作为现实世界AI执行的基础
authors: "Song, R., Fu, Y., Zhao, Z., Yu, J., Yuan, Q., Chen, C.-T."
date: 2026-05-07
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.05.720956v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 编译器验证协议实现生物学自主闭环发现
tldr: "针对生物学实验协议依赖自然语言导致低可重复性的问题，本文提出生物学协议语言(BPL)及其编译器BPL-COGEN。BPL具有物理单位、试剂形态和容器状态等原生类型，可在编译时检测错误。BPL-COGEN结合大语言模型与编译器迭代修正自然语言到BPL的翻译。在300篇Nature Protocols测试中达到95.1%保真度，跨平台湿实验验证了可重复性，为实体AI执行奠定了基础。"
source: biorxiv
selection_source: carryover_cache
motivation: 现有生物学实验协议依赖模糊的自然语言，导致在准确性、验证和跨平台可移植性上存在可重复性问题，需要一种编译器验证的形式化语言。
method: 设计具备物理单位、试剂形态和容器状态类型系统的领域特定语言BPL，并开发BPL-COGEN管道，利用大语言模型和编译器在生成-验证-修复循环中自动将自然语言SOP转化为BPL。
result: "在300篇Nature Protocols基准上达到95.1%保真度，并通过荧光蛋白表达文库构建和HPLC到UHPLC方法转换等实验验证了跨平台可重复执行。"
conclusion: BPL与BPL-COGEN提供了生成编译器可验证协议的自动化管道，是迈向生物学自主实体AI的关键基础。
---

## 摘要
人工智能已从分析实验数据发展到自主生成假设、设计实验和协调闭环发现。然而，从计算推理到物理执行的转化仍受限于实验协议，在生物学中，实验协议仍依赖于模糊的自然语言描述：其他工程学科数十年前就已放弃这种媒介，转而采用编译器验证的规范语言。这一缺陷沿三个维度破坏了可重复性：协议准确性、执行前验证和跨平台可移植性。现有的形式化方法仅解决这些挑战的子集，用表达力换取严谨性，用可移植性换取标准化，或用可用性换取溯源。在此，我们引入生物学协议语言（BPL），这是一种领域特定语言，具有生物学原生类型系统，其中每个量都带有物理单位，每个试剂都声明其物理形式，每个容器都保持编译器跟踪的状态，从而隐含的假设必须明确陈述，物理上不可能的操作在编译时被拒绝。我们进一步开发了BPL-COGEN，这是一个将微调的300亿参数语言模型与确定性编译器结合在闭合的生成-验证-修复循环中的流水线，通过编译器诊断迭代地纠正从自然语言SOP到BPL的翻译，直到所有物理、维度、状态约束得到满足。在300篇已发表的Nature Protocols论文基准上，BPL-COGEN相对于源协议作为地面实况实现了95.1的整体保真度分数。在GFP表达文库构建和HPLC到UHPLC方法迁移中的湿实验和跨平台验证确认，单个BPL源可在手动和液体处理器辅助环境下产生可重复的执行。结果建立了一条生成编译器验证协议的新颖流水线，这是生物学中物理体现AI的必要前提。

## Abstract
Artificial intelligence has advanced from analyzing experimental data to autonomously generating hypotheses, designing experiments, and coordinating closed loop discovery. Yet the translation from computational reasoning to physical execution remains bottlenecked by the experimental protocol, which in biology still relies on ambiguous natural-language descriptions: a medium other engineering disciplines abandoned decades ago in favor of compiler verified specification languages. This deficit fragments reproducibility along three axes: protocol accuracy, pre execution verification, and cross platform portability. Existing formalisms address only subsets of these challenges, trading expressiveness for rigor, portability for standardization, or usability for provenance. Here we introduce the Biology Protocol Language (BPL), a domain specific language with a biology-native type system in which every quantity carries physical units, every reagent declares its physical form, and every container maintains compiler-tracked state, so that implicit assumptions must be stated explicitly and physically impossible operations are rejected at compile time. We further develop BPL-COGEN, a pipeline that couples a fine tuned 30 billion parameter language model with the deterministic compiler in a closed generate validate repair loop, iteratively correcting the translation from natural language SOPs to BPL through compiler diagnostics until all physical, dimensional, and state constraints are satisfied. On a benchmark of 300 published Nature Protocols papers, BPL COGEN achieved an overall fidelity score of 95.1 against the source protocols as ground truth. Wet-lab experiment and cross-platform validation in GFP expression library construction and HPLC to UHPLC method translation confirmed that a single BPL source yielded reproducible execution across manual and liquid handler assisted contexts. The results established a novel pipeline that generates compiler-verified protocols, which is an essential prerequisite for physically embodied AI in biology.