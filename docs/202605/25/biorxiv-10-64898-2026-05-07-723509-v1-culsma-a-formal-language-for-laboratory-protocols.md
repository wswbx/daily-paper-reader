---
title: "Culsma: A Formal Language for Laboratory Protocols"
title_zh: "Culsma: 一种实验室协议的形式化语言"
authors: "Chen, Y., Sun, M., Tadepally, L., Wang, J., Barcenilla, H., Gonzalez, L., Brodin, P."
date: 2026-05-12
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.07.723509v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 8.0
evidence: 实验室协议的形式化语言，支持AI驱动的科学
tldr: 为满足生物医学研究中AI系统对实验室协议的人机可读与可执行需求，本文提出形式语言Culsma及其执行框架，将自然语言协议转化为语义明确的工作流程序，支持分析、验证、自动执行和跨环境转移。端到端实现验证了其实用性。
source: biorxiv
selection_source: carryover_cache
motivation: 自然语言描述的实验室协议无法同时满足人类可读与机器可执行的双重需求。
method: 设计并实现形式语言Culsma及其执行框架，将协议转化为语义明确的工作流程序。
result: 通过端到端实现证明了Culsma在实际环境中的可用性。
conclusion: Culsma使协议能够被分析、验证、执行并在不同实验室间转移。
---

## 摘要
人工智能在生物医学研究中的应用日益依赖于迭代循环，其中AI系统分析实验数据、提出后续条件并驱动大规模自动化执行，这是生物AI和自主实验室科学的核心范式。为了运行这样的循环，实验室协议必须以同时可读和可执行的形式表达。自然语言描述作为当前实验室实践的标准，无法满足这一双重需求。我们提出Culsma，一种形式化语言和执行框架，将实验室协议从非正式散文提升为语义明确的工作流程序，可进行分析、验证、执行和跨环境转移。同一协议可由实验室科学家阅读和验证，并由自动化流水线解析、验证和执行，无需重新翻译。我们展示了端到端实现，提供了实际可行性的具体证据。

## Abstract
The application of artificial intelligence to biomedical research increasingly depends on iterative cycles in which AI systems analyze experimental data, propose follow-up conditions, and drive automated execution at scale, a paradigm central to Bio-AI and autonomous laboratory science. For such cycles to operate, laboratory protocols must be expressed in a form that is simultaneously human-readable and machine-executable. Natural-language descriptions, the current standard in laboratory practice, do not satisfy this dual requirement. We present Culsma, a formal language and execution framework that elevates laboratory protocols from informal prose to semantically explicit workflow programs that can be analyzed, validated, executed, and transferred across settings. The same protocol can be read and verified by a bench scientist, and parsed, validated, and executed by an automated pipeline without re-translation. We demonstrate an end-to-end implementation providing concrete evidence of practical viability.