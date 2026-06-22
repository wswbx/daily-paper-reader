---
title: Trustworthy agentic genomics through versioned skill libraries
title_zh: 通过版本化技能库实现可信的智能体基因组学
authors: "Corpas, M., Iacoangeli, A., Bourdenx, M., Aldraimli, M., Skene, N., Fatumo, S., Guio, H."
date: 2026-06-15
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.11.731523v1.full.pdf"
tags: ["query:skill-rl"]
score: 7.0
evidence: 基于技能的分层强化学习与版本化技能库用于智能体基因组学
tldr: "自主AI代理在基因组学中快速应用，但缺乏信任机制。本文在药理基因组学任务上，通过44,550次评估对比九种大语言模型，发现可信赖性是流水线架构的属性。将验证后的决策逻辑编码为版本化技能并作为代码执行，使临床映射精确、可审计且模型不变，而模型推理或检索均存在致命误差。这一架构为可信基因组解释提供了可推广的路径。"
source: biorxiv
selection_source: fresh_fetch
motivation: 自主AI代理在基因组学中缺乏信任机制，现有方法在临床尺度上存在致命错误风险。
method: 对比九种大语言模型在110个药理基因组学案例上的表现，提出将决策逻辑编码为版本化技能并作为代码执行。
result: 技能执行使临床映射精确、可审计、模型不变，将所有误差限制在输入解释步骤。
conclusion: 可信赖基因组解释应将正确性从随机模型转移到版本化执行技能，为临床部署提供可推广架构。
---

## 摘要
基因组学正在采用自主AI智能体，能够从自然语言指令中解读基因组，但其速度超过了建立信任手段的速度。我们报告了首次大规模对照评估，以确定在智能体基因组流水线中，正确性必须存在于何处，才能使系统在临床规模上可信。使用药物基因组学（一个错误可测量且有时致命的领域），我们在110个药物基因组学案例上对9个前沿大语言模型进行了44,550次评分评估，并测试了模型对来自三个祖先多样性人群中超过7000个个体的真实星等位基因双倍型的解读。可信性被证明是流水线架构的属性，而非模型的属性。让模型推理是随机且不安全的，通过检索将其置于正确指南中却矛盾地增加了致命类别错误。将验证过的决策逻辑编码为版本化技能并作为代码执行，使得药物基因组学映射精确、可审计且跨模型一致，将所有残余错误限制在单个输入解读步骤中。在个体基因组上，无保护的模型解读沿祖先梯度下降；执行从临床映射中移除了这一梯度，将其转移到输入调用者的可审计完整性上。这为大规模可信的智能体基因组解读建立了一个可泛化、可审计的架构。

亮点
• 正确性必须被执行，而非推理或检索，才能可信
• 检索提高了表型准确性，但增加了致命类别错误；技能则不会
• 执行使临床映射精确且模型不变；错误停留在输入
• 确定性输入调用者是预测的全正确输出答案的路径

简要概括
Corpas及其同事表明，可信的智能体基因组解读并非来自让语言模型正确推理生物学，而是来自将其限制在解读输入上，同时由版本化、验证过的技能作为执行代码进行推理。在9个大语言模型和110个药物基因组学案例中，执行技能使临床映射变得确定性、可审计且与模型无关。

意义
基因组学正在采用自主的、语言模型中介的智能体，但其速度超过了建立信任所需的标准。在一个具有致命后果的药物基因组学基准上，我们表明智能体的可信性不是模型的属性，而是智能体如何被约束的属性：正确性必须从随机模型转移到作为代码执行的版本化技能中，模型仅限于解读异构输入。这为该领域提供了一个可迁移的架构，用于可信的智能体基因组解读，一个预测的部署路径（执行验证过的技能，确定性调用输入，并对不可简化的残余弃权），以及一种将基因组技能开发为验证过的、可执行的、版本化单元（而非提示）的方法。遵循其他地方描述的验证框架，我们使用临床级来指确定性、可审计性、可追溯到版本化组件以及群体不变性能，所有这些都在技能约束执行下实现。我们区分了群体性能的两种含义：执行的临床映射通过构造是群体不变的，在欧洲、拉丁美洲和东非血統个体上验证，而模型对真实的、祖先多样双倍型的解读则不是，沿祖先梯度下降，这正是映射必须执行而非推理的原因。我们不声称完全的临床验证，这还需要非标准输入、真实世界的基因组和临床数据、人类比较者和多站点一致性。

## Abstract
Genomics is adopting autonomous AI agents that interpret genomes from natural-language instructions faster than it is building the means to trust them. We report the first large-scale controlled evaluation of where, in an agentic genomic pipeline, correctness must reside for the system to be trustworthy at clinical scale. Using pharmacogenomics, a domain where errors are measurable and sometimes lethal, we benchmarked nine frontier large language models across 44,550 scored evaluations on 110 pharmacogenomic cases, and tested model interpretation of real star-allele diplotypes from more than 7,000 individuals in three ancestrally diverse populations. Trustworthiness proved to be a property of pipeline architecture, not of the model. Letting the model reason was stochastic and unsafe, and grounding it in the correct guidelines by retrieval paradoxically increased lethal-class errors. Encoding the validated decision logic as a versioned skill and executing it as code made the pharmacogenomic mapping exact, auditable and identical across models, confining all residual error to a single input-interpretation step. On individual genomes, unguarded model interpretation degraded along an ancestry gradient; execution removes this gradient from the clinical mapping, relocating it to the auditable completeness of the input caller. This establishes a generalisable, auditable architecture for trustworthy agentic genome interpretation at scale.

HighlightsO_LICorrectness must be executed, not reasoned or retrieved, to be trustworthy
C_LIO_LIRetrieval raises phenotype accuracy yet increases lethal-class errors; skills do not
C_LIO_LIExecution makes the clinical mapping exact and model-invariant; error stays at input
C_LIO_LIA deterministic input caller is the predicted route to all-correct emitted answers
C_LI

In briefCorpas and colleagues show that trustworthy agentic genome interpretation comes not from making language models reason correctly about biology, but from confining them to interpreting input while versioned, validated skills do the reasoning as executed code. Across nine large language models and 110 pharmacogenomics cases, executing the skill makes the clinical mapping deterministic, auditable and model-invariant.

SignificanceGenomics is adopting autonomous, language-model-mediated agents faster than it is building the standards needed to trust them. On a pharmacogenomic benchmark with lethal-class consequences, we show that an agents trustworthiness is not a property of the model but of how the agent is constrained: correctness must be moved out of the stochastic model into a versioned skill executed as code, with the model confined to interpreting heterogeneous input. This gives the field a transferable architecture for trustworthy agentic genome interpretation, a predicted route to deploying it so that every emitted answer is correct (execute the validated skill, call the input deterministically, and abstain on the irreducible residual), and a way to develop genomic skills as validated, executable, versioned units rather than prompts. Following a validation framework described elsewhere, we use clinical-grade to mean determinism, auditability, traceability to versioned components and population-invariant performance, all achieved under skill-constrained execution. We distinguish two senses of population performance: the executed clinical mapping is population-invariant by construction, verified across European, Latin American and East African origin individuals, whereas the models interpretation of real, ancestrally diverse diplotypes is not, degrading along an ancestry gradient, which is precisely why the mapping must be executed rather than reasoned. We do not claim full clinical validation, which would additionally require non-canonical inputs, real-world genomic and clinical data, human comparators and multi-site concordance.