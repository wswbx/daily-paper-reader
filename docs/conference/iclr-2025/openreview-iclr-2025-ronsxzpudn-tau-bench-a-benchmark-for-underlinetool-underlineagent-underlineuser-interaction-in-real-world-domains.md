---
title: "{$\\tau$}-bench: A Benchmark for \\underline{T}ool-\\underline{A}gent-\\underline{U}ser Interaction in Real-World Domains"
authors: "Shunyu Yao, Noah Shinn, Pedram Razavi, Karthik R Narasimhan"
date: 2025
pdf: "https://proceedings.iclr.cc/paper_files/paper/2025/file/1b126cc38b8638e07bef37e7b2bb72bf-Paper-Conference.pdf"
tags: ["query:user-sim"]
score: 8
source: ICLR-2025-Accepted
selection_source: long-range
publication_date: 2025
publication_date_precision: year
publication_date_source: conference year only; exact release date unverified
publication_date_kind: unknown
id: openreview-iclr-2025-ronsxzpudn
canonical_id: "work:6550e89a6610653112b09cf5"
research_run_id: 20261125-68a82e6ab836
research_mode: starter
reading_status: pending
---

## Abstract
Existing benchmarks for language agents do not set them up to interact with human users or follow domain-specific rules, both of which are vital to safe and realistic deployment. We propose $\tau$-bench, a benchmark with two domains (retail and airline) emulating dynamic conversations between a user (simulated by language models) and a customer service agent provided with domain-specific API tools and policy guidelines. We employ a efficient and faithful evaluation process that compares the database state at the end of a conversation with the annotated goal state, and propose a new metric (pass^k) to evaluate the reliability of agent behavior over multiple trials. Our experiments show that even state-of-the-art function calling agents (gpt-4o) succeed on $<50\%$ of the tasks, and are terribly inconsistent (pass^8 < 25\% in retail). Our findings point to the need for methods that can improve the ability of agents to act consistently and reliably follow rules.

## 专题评审

专题相关性评分：8/10。

论文构建基准并使用语言模型模拟用户与客服智能体交互，直接涉及用户模拟器。

<!-- research-reading-pending -->
中文总结与全文内容待生成；当前仅提供原始论文元数据与摘要。
<!-- /research-reading-pending -->
