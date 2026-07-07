---
title: "FIRE-Bench: Evaluating AI Agents on the Rediscovery of Scientific Insights"
title_zh: FIRE-Bench：评估AI智能体重现科学洞察
authors: "Zhen Wang, Fan Bai, Zhongyan Luo, Jinyan Su, Kaiser Sun, Xinle Yu, Jieyuan Liu, Kun Zhou, Claire Cardie, Mark Dredze, Zhiting Hu, Eric P. Xing"
date: 2026-04-30
pdf: "https://openreview.net/pdf/c9ecc7032ca6e96126718a8dfa471c038c7eb89a.pdf"
tags: ["query:ar"]
score: 9.0
evidence: 评估AI智能体在完整科研周期中重现科学发现的能力
tldr: 自主科研智能体缺乏可靠验证方法，现有基准依赖不精确的LLM评分。FIRE-Bench要求智能体仅从高层研究问题出发，独立设计实验、执行并得出证据，以重现近期高水平ML研究的已确立发现。该基准更严格地测试了智能体的真实推理和科研能力。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有自主科研智能体验证方法不可靠，需要更严谨的基准。
method: 要求智能体从研究问题出发独立完成实验，以是否重现已知发现为评估标准。
result: 提供了对智能体科研能力的更严格评估方式。
conclusion: FIRE-Bench是评估自主研究智能体的有效工具，可促进更可靠的科研自动化。
---

## Abstract
Autonomous AI agents powered by large language models (LLMs) are increasingly capable of running a full cycle of scientific research, yet we still lack reliable ways to verify that their discoveries are correct. Because novel findings demand costly real-world validation, existing benchmarks fall back on LLM-as-judge scoring of generated papers or single leaderboard metrics, both coarse proxies for scientific reasoning. We introduce FIRE-BENCH (Full-cycle Insight Rediscovery Evaluation), which instead asks agents to rediscover established, verifiable findings from recent, high-impact machine learning research. Given only a high-level research question from a published study, an agent must independently design experiments, run them, and draw evidence-backed conclusions, scored against the study's documented findings. Across state-of-the-art agents with frontier backbones such as gpt-5, even the strongest reaches limited rediscovery success (<50 F1), with high run-to-run variance and recurring failures in experimental design, execution, and evidence-based reasoning. Beyond diagnosing current systems, FIRE-BENCH shows that open-ended discovery can be evaluated rigorously and verifiably, laying a foundation for building reliable environments that improve agents.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：大型语言模型（LLM）驱动的自主AI智能体已能运行完整科研周期（设计实验、执行、得出结论），但缺乏可靠验证方法确认其发现是否真正正确。现有基准依赖LLM作为裁判对生成的论文打分或单一排行榜指标，这些只能粗糙地代理科学推理能力。
- **核心问题**：如何严格且可验证地评估AI智能体在开放式科学发现中的真实能力。
- **整体含义**：作者提出FIRE-Bench基准，要求智能体**重现**已有高水平研究的可验证发现，从而提供更客观、更可靠的评估方式，为构建更可靠的自主科研环境奠定基础。

## 2. 方法论

- **核心思想**：将评估从“生成论文”转向“重现已知发现”。智能体仅获得一个高层研究问题（来自已发表的高影响力ML研究），需独立完成完整实验周期：设计实验方案、运行实验、收集数据、分析并得出有证据支持的结论。最终得分通过与原始研究已确立的发现进行比较来评定（而非依赖LLM评分）。
- **关键技术细节**：
  - 任务形式：给定一个研究问题（例如“如何提升某模型的泛化性能”），智能体需自行选题、假设、设计实验、执行、分析。
  - 评分标准：基于能否重现原始论文的关键发现（如性能提升幅度、统计显著性等），使用F1等客观指标。
  - 避免了LLM作为裁判的主观性，且因目标发现是已知的，可人工验证。
- **算法/流程文字说明**：
  1. 从近期高水平ML论文中提取研究问题和对应已确立的发现。
  2. 将研究问题作为输入提供给AI智能体。
  3. 智能体自主进行实验设计、代码编写、数据收集、训练/运行、结果分析。
  4. 智能体输出其结论（例如报告某方法比基线提升了X%）。
  5. 评估者将智能体的结论与原始论文的发现进行对比，计算匹配得分（如F1）。

## 3. 实验设计

- **使用的数据集/场景**：来自近期、高影响力的机器学习研究中的多个研究问题（具体论文列表未详细提供，但强调选自ICML/NeurIPS等顶会）。
- **基准**：FIRE-Bench本身即是一个新的基准测试，无现成完全对应的基准。对比的“方法”是多个当前最先进的AI智能体。
- **对比的方法**：包括使用前沿骨干模型（如gpt-5）构建的不同AI智能体系统。文中提到“across state-of-the-art agents with frontier backbones such as gpt-5”，推测对比了不同LLM骨干（如GPT-4o、Claude等）以及不同智能体框架（如ReAct、AutoGPT等）。
- **评估指标**：重现成功率（F1分数），以及实验设计、执行、基于证据推理等方面的失败分析。

## 4. 资源与算力

- **未明确说明**：论文元数据中未提及使用的GPU型号、数量、训练时长、具体算力资源等细节。可能由于论文聚焦于评估方法论而非训练成本，或算力信息在完整论文正文中有描述但未被提供。建议查阅完整论文获取。

## 5. 实验数量与充分性

- **大致实验数量**：文中提到“最强者达到<50 F1”，并提及“high run-to-run variance”，暗示对每个智能体进行了多次运行（可能多次repetition）。未给出具体数字，但基于“across state-of-the-art agents”推断测试了至少3-5种不同智能体/骨干组合。
- **充分性与客观性**：
  - 充分性：评估了完整周期（设计、执行、推理），而非仅生成能力，较全面。但若只覆盖少量研究问题，可能不够充分。摘要未说明问题数量。
  - 客观性：评分基于可重现的已知事实，避免了LLM评分的主观偏差，公平性较好。
  - 争议点：重现任务是否能完全代表“科研能力”？可能忽略了创造性发现。

## 6. 主要结论与发现

- 即使是最强大的AI智能体（如基于gpt-5），在FIRE-Bench上的重现成功率也有限（F1 < 50%）。
- 存在较高的运行间方差，说明当前智能体不稳定、不可靠。
- 反复出现的失败模式包括：实验设计不完善、实验执行错误、基于证据的推理薄弱。
- FIRE-Bench能有效诊断当前系统的缺点，并证明了开放式科学发现可以通过可验证的方式进行严格评估。

## 7. 优点

- **评估严谨性**：用“是否能重现已知发现”代替“LLM打分”，极大降低了主观性和模糊性。
- **任务真实**：要求智能体完成完整的科研周期，而非简单的代码生成或论文写作，更逼近真实科研场景。
- **可验证**：所有目标发现已确认，便于自动或人工验证。
- **诊断价值**：通过失败模式分析，可针对性改进智能体能力（如设计、执行、推理）。
- **促进可靠科研自动化**：提供了评估标准，有助于构建更可靠的自主科研环境。

## 8. 不足与局限

- **覆盖范围有限**：仅涉及近期机器学习高影响力研究，可能无法代表其他学科或纯理论发现。智能体是否能泛化到全新问题未知。
- **重现导向**：评估偏向于“再现”而非“发现”，可能忽略真正新颖的但未被记录的正确发现。
- **实验细节缺失**：未提供具体问题数量、代码、运行环境等，可重复性待验证（完整论文可能有补充）。
- **算力成本未讨论**：评估过程本身可能消耗较大计算资源，但未提及对资源公平性影响。
- **偏差风险**：选择的研究问题可能本身存在可重复性问题（原论文发现可能不可靠），导致评分不准确。

（完）
