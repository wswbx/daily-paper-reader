---
title: "Towards Effective Offensive Security LLM Agents: Hyperparameter Tuning, LLM as a Judge, and a Lightweight CTF Benchmark"
title_zh: 面向有效攻击性安全LLM代理：超参数调优、LLM评判与轻量级CTF基准
authors: "Minghao Shao, Nanda Rani, Kimberly Milner, Haoran Xi, Meet Udeshi, Saksham Aggarwal, Venkata Sai Charan Putrevu, Sandeep K. Shukla, Prashanth Krishnamurthy, Farshad Khorrami, Ramesh Karri, Muhammad Shafique"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40210/44171"
tags: ["query:cli-agent"]
score: 7.0
evidence: 用于CTF挑战的自动化LLM安全代理
tldr: 该论文系统研究了构建有效LLM安全代理的关键因素，包括超参数调优、LLM评判框架及轻量级CTF基准，提出CTFJudge和部分正确性指标，为自动化安全攻击任务提供了实用指南。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: LLM代理在自动化安全任务中潜力巨大，但缺乏系统调优和评估方法。
method: 提出CTFJudge框架进行轨迹分析，设计CTF能力指数(CCI)衡量部分正确性，并系统研究超参数影响。
result: 揭示了影响代理成功的关键因素，提供了构建安全代理的详细配方。
conclusion: 为LLM在安全自动化领域的应用提供了系统的优化和评估方法。
---

## Abstract
Recent advances in LLM agentic systems have improved the automation of offensive security tasks, particularly for Capture the Flag (CTF) challenges. We systematically investigate the key factors that drive agent success and provide a detailed recipe for building effective LLM-based offensive security agents. First, we present CTFJudge, a framework leveraging LLM as a judge to analyze agent trajectories and provide granular evaluation across CTF solving steps. Second, we propose a novel metric, CTF Competency Index (CCI) for partial correctness, revealing how closely agent solutions align with human-crafted gold standards. Third, we examine how LLM hyperparameters, namely temperature, top-p, and maximum token length, influence agent performance and automated cybersecurity task planning. For rapid evaluation, we present CTFTiny, a curated benchmark of 50 representative CTF challenges across binary exploitation, web, reverse engineering, forensics, and cryptography. Our findings identify optimal multi-agent coordination settings and lay the groundwork for future LLM agent research in cybersecurity.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在自动化攻击性安全任务（如CTF挑战）中展现出巨大潜力，但现有系统存在三方面瓶颈：(a) 超参数（温度、top-p、最大token长度）对代理行为的影响缺乏系统研究；(b) 评估方法仅采用“通过/失败”的粗粒度指标，无法反映部分进展、推理质量等细粒度能力；(c) 缺乏轻量级、标准化的基准，导致实验难以快速复现和资源受限场景下的测试。
- **整体含义**：本文旨在系统揭示影响LLM安全代理成功的关键因素，提供构建有效攻击性安全代理的“配方”。通过提出细粒度评估框架CTFJudge、部分正确性指标CTF Competency Index (CCI) 以及轻量级基准CTFTiny，为自动化安全评估和超参数调优奠定方法论基础。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将LLM代理的评估与超参数调优结合，采用“LLM作为评判”的思路对代理轨迹进行多维度打分，并设计轻量级基准以支持快速实验。
- **关键技术细节**：
  - **CTFTiny基准**：从NYU CTF Bench中精选50个挑战，涵盖二进制漏洞、Web、逆向工程、取证、密码学等6个领域。挑战难度基于12种不同配置（模型、规划策略、工具）的先前求解结果划分（0–3硬、4–6中等、6–9易、9–12极易），确保难度分布合理。
  - **CTFJudge框架**：将专家编写的解题步骤（参考方案）与代理执行轨迹分别抽象为结构化摘要，然后沿着6个维度（漏洞理解、侦察全面性、利用方法论、技术准确性、方法效率、适应性）进行对比评分，生成CTF能力指数（CCI）。
  - **CCI公式**：\( CCI(T,G) = \sum_{i=1}^{n} w_i F_i(T,G) \)，其中\( \sum w_i = 1 \)，初始设置 n=6，权重相等。得分在[0,1]之间，反映代理轨迹与专家方案的匹配程度。
- **超参数调优**：系统变化温度（0~1.0步长0.2）、top-p（0.25~1.0）、最大token长度（2048/4096/8192），使用D-CIPHER多代理框架作为被评估系统。

## 3. 实验设计：数据集、基准、对比方法

- **数据集/基准**：CTFTiny（50个CTF挑战），难度分布均衡（硬/中/易/极易）。
- **被评估系统**：D-CIPHER多代理框架（含规划、执行、反馈的专用代理）。
- **对比模型**：7个LLM，包括4个专有模型（Claude 4 Sonnet、GPT-4.1、Gemini 2.5 Pro、Gemini 2.5 Flash）和3个开源模型（Llama-4-Maverick-17B、Qwen3-235B、DeepSeek-V3-0324）。
- **评估指标**：
  - Pass@1：首次尝试成功率。
  - CCI：六个维度的加权平均得分。
  - 计算成本（美元）。
  - 类别级和难度级分解。
- **评判LLM设置**：固定使用Claude 3.7 Sonnet（温度0.1）作为CTFJudge。

## 4. 资源与算力

- 论文中未明确说明GPU型号、数量、训练时长等具体算力信息。仅提及使用官方API（Anthropic、OpenAI、Google）和Together AI平台调用模型，代理运行在Linux服务器环境。未给出训练或推理的总计算资源统计。

## 5. 实验数量与充分性

- **实验数量**：共评估7个模型在50个挑战上的基线性能，并对每个模型进行多组超参数扫描（温度×7个值、top-p×8个值、最大token×3个值，合计约18种配置，但仅对Claude和GPT-4.1展示了详细结果）。另外进行了CCI对比分析和失败原因分类（21个类别）。
- **充分性与客观性**：实验设计较为系统，覆盖多个模型家族、多个超参数维度，并采用CTFTiny确保难度多样性。失败分析通过CTFJudge自动标注21个原因，避免主观偏差。但缺乏对不同多代理框架（如单代理基线）的对比，且仅使用了D-CIPHER一种架构，可能限制了结论的泛化性。此外，部分模型（如LLaMA-4 Maverick）仅完成几次实验，超参数扫描未对所有模型完整展示。

## 6. 论文的主要结论与发现

- **模型性能排名**：Claude 4 Sonnet最优（76%），其次Gemini 2.5 Flash（64%）、Gemini 2.5 Pro（48%）、GPT-4.1（40%）；开源模型显著落后（DeepSeek V3 22%，Qwen3 28%，LLaMA-4 8%）。
- **超参数影响**：
  - **温度**：高温度（T=1.0）对强模型（Claude）有显著提升；GPT-4.1峰值在T=0.6。
  - **top-p**：p=1.0时Claude达到峰值38 solves；p在0.25~0.85间表现稳定。
  - **最大token**：4096为“黄金区间”，2048和8192均导致性能下降（过长上下文可能造成注意力稀释）。
- **CCI揭示真实能力**：成功轨迹的CCI高且方差低，失败轨迹主要在“利用方法论”“效率”“适应性”三个维度急剧下降。CCI比简单的通过/失败更能反映推理质量，且能区分暴力破解与结构化推理。
- **失败原因**：最常见的是“知识/领域专业知识差距”“利用开发失败”“侦察不足”；代理框架的“任务委派错误”和“环境故障”发生较少。
- **类别差异**：逆向工程、密码学任务表现较好；取证和混合类任务因文件类型多样且需要交互而表现较弱。

## 7. 优点：方法或实验设计上的亮点

- **细粒度评估**：CTFJudge提出CCI指标，解决传统pass/fail的粗粒度问题，能定位代理瓶颈（如效率低、适应性差）。
- **系统超参数研究**：首次在安全代理领域全面分析温度、top-p、最大token的联合影响，揭示“黄金窗口”现象。
- **轻量基准CTFTiny**：仅50个挑战，却保持难度多样性，显著降低实验成本，便于快速迭代。
- **多维度失败分析**：通过21个预定义原因自动分类，提供针对性改进方向。
- **代码与数据开源**：提供GitHub仓库，支持复现。

## 8. 不足与局限

- **代理架构单一**：仅评估D-CIPHER一种多代理框架，未对比单代理、强化学习代理等设计，结论可能无法推广。
- **超参数扫描不完整**：仅对Claude和GPT-4.1展示了所有超参数结果，对其他模型仅做了基线测试。
- **CCI权重固定**：六维度权重相等，未考虑任务类型差异；作者也指出未来需要自适应校准。
- **计算资源报告缺失**：未提供GPU型号、总实验时间等，不利于估算复现成本。
- **模型更新滞后**：论文发表于2026年，所用模型版本可能已被更新版本超越（如Claude 4 Sonnet为2025年5月版本）。
- **安全性风险提示**：虽强调仅用于教育研究，但所开发的代理能力可能被误用于真实攻击，需严格合规。

（完）
