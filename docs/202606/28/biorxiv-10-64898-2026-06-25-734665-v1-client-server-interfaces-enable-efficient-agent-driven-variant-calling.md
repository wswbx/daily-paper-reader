---
title: Client-server interfaces enable efficient agent-driven variant calling
title_zh: 客户端-服务器接口实现高效的智能体驱动变异检测
authors: "Yu, X., Zheng, Z., CHEN, L., QIn, Z., Guo, X., He, M., Luo, R."
date: 2026-06-28
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.25.734665v1.full.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: LLM代理自动化终端任务；用于变体调用的客户端-服务器接口
tldr: 大语言模型代理自动化生物信息学分析时，现有工具为人类设计导致效率低下。本文重新架构Clair3为客户端-服务器系统Clair3-Connect，客户端处理基因组数据并暴露模式定义工具，服务器仅做推理。在APOE二倍型任务中，所有代理运行正确，令牌使用减少6.8-14倍，时间约四分之一，稳定性提升。将算法重构成agentic工具可提高可靠性和效率，应作为生物信息学工具开发的一等交付物。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有生物信息学工具为人类专家设计，代理驱动时需大量令牌和调用，效率低且不稳定。
method: 将Clair3重构为客户端-服务器系统，客户端处理基因组数据并暴露模式定义工具，服务器仅运行神经网络推理。
result: "在APOE二倍型任务中，所有60次代理运行正确，令牌使用减少6.8-14倍，时间减少约75%，稳定性显著提高。"
conclusion: 重新构建设计agentic接口可提升代理驱动分析的效率和可靠性，应作为生物信息学工具开发的优先交付物。
---

## 摘要
背景：大型语言模型（LLM）智能体越来越多地自动化生物信息学分析，但大多数现有的生物信息学工具是为人类专家独立使用而构建的。驱动此类工具的智能体必须根据面向人类的文档推理其安装、配置和执行，每个结果需要大量回合、令牌和工具调用。因此，方法如何暴露给智能体可能与方法本身同样重要。通过为这些工具设计智能体接口，智能体可以减少此类开销并提高智能体驱动分析的可靠性。发现：为了测试这一设计，我们重新架构了Clair3（一个广泛使用的基于深度学习的长读长变异检测器），将其改造为客户端-服务器系统Clair3-Connect。客户端执行所有基因组学相关处理并持有可识别数据。服务器仅运行神经网络推理，客户端仅向服务器发送特征张量，而样本标识符和基因组上下文保留在客户端。客户端暴露了基于模式的面向智能体的工具，智能体通过单个结构化调用调用这些工具。在APOE单倍型分型任务中，所有60次智能体运行均正确。智能体工具在3次交互中使用了12K令牌，比基于shell的基线（81K-163K令牌）少6.8到14倍，运行时间约为四分之一，且稳定性更高（令牌使用变异率4%对比35%）。省略pileup和phasing阶段以保持客户端轻量，在50×覆盖度下，SNP F1值比标准Clair3低0.1-0.3个点，而相互TLS和AES-256-GCM加密增加了7.2%的端到端运行时间。结论：将既定算法重新构建为开发者构建的、位于安全客户端-服务器边界后的智能体工具，相较于第三方封装器（无法恢复仅开发者知道的默认和约定），使其对LLM智能体更高效、可靠且易于部署。智能体接口应成为生物信息学工具开发的一级交付物。

## Abstract
Background: Large language model (LLM) agents increasingly automate bioinformatics analyses, but most existing bioinformatics tools were built for standalone use by human experts. An agent driving such a tool must reason about its installation, configuration, and execution from documentation for human, spending many turns, tokens, and tool calls per result. How a method is exposed to an agent can therefore matter as much as the method itself. By designing agentic interfaces for these tools, agent can reduce such overhead and improve the reliability of agent-driven analyses. Findings: To test this design, we re-architected Clair3, a widely used deep-learning-based long-read variant caller, into a client-server system, Clair3-Connect. The client performs all genomics related processing and holds the identifiable data. The server runs only neural-network inference, and the client sends only feature tensors to the server, while sample identifiers and genomic context remain on the client. The client exposes schema-defined agent-facing tools that an agent invokes through single structured calls. On an APOE diplotyping task, all 60 agent runs were correct. The agentic tools used 12K tokens in 3 turns, 6.8 to 14 times fewer tokens than the shell-driven baselines (81K-163K tokens), at about a quarter the wall-clock time and far more stably (4% versus 35% token usage variation). Dropping the pileup and phasing stages to keep the client light left SNP F1 within 0.1-0.3 points of standard Clair3 by 50x coverage, while mutual TLS and AES-256-GCM encryption added 7.2% to end-to-end runtime. Conclusions: Recasting an established algorithm as developer-built, agentic tools behind a secure client-server boundary makes it more efficient, reliable, and easier to deploy for an LLM agent than a third-party wrapper, which cannot recover the defaults and conventions only its developers know. Agentic interfaces should be a first-class deliverable of bioinformatics tool development.