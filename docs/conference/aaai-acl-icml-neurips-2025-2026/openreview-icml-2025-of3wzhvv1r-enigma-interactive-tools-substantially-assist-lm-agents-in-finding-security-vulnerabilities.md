---
title: "EnIGMA: Interactive Tools Substantially Assist LM Agents in Finding Security Vulnerabilities"
title_zh: EnIGMA：交互工具显著帮助LM智能体发现安全漏洞
authors: "Talor Abramovich, Meet Udeshi, Minghao Shao, Kilian Lieret, Haoran Xi, Kimberly Milner, Sofija Jancheska, John Yang, Carlos E Jimenez, Farshad Khorrami, Prashanth Krishnamurthy, Brendan Dolan-Gavitt, Muhammad Shafique, Karthik R Narasimhan, Ramesh Karri, Ofir Press"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Of3wZhVv1R"
tags: ["query:cli-agent"]
score: 9.0
evidence: 使用交互终端工具的LM智能体用于安全任务
tldr: 针对LM智能体在网络安全任务中表现有限的问题，EnIGMA引入交互式终端工具（如调试器、服务器连接工具），使智能体能首次运行交互式终端程序。在390个CTF挑战中，工具显著提升了漏洞发现和利用成功率，验证了将终端工具集成到LM智能体的有效性，直接对应智能终端智能体需求。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: LM智能体在网络安全领域表现有限，缺乏终端交互能力。
method: 设计交互式终端工具集，使智能体可运行调试器等交互程序。
result: 在390个CTF挑战中，工具大幅提升漏洞发现和利用成功率。
conclusion: 交互式终端工具是增强LM智能体安全能力的关键。
---

## Abstract
Although language model (LM) agents have demonstrated increased performance in multiple domains, including coding and web-browsing, their success in cybersecurity has been limited. We present *EnIGMA*, an LM agent for autonomously solving  Capture The Flag (CTF) challenges. We introduce new tools and interfaces to improve the agent's ability to find and exploit security vulnerabilities, focusing on interactive terminal programs.  These novel *Interactive Agent Tools* enable LM agents, for the first time,  to run interactive utilities, such as a debugger and a server connection tool, which are essential for solving these challenges.
Empirical analysis on 390 CTF challenges across four benchmarks demonstrate that these new tools and interfaces substantially improve our agent's performance, achieving state-of-the-art results on NYU CTF, Intercode-CTF, and CyBench. Finally, we analyze data leakage, developing new methods to quantify it and identifying a new phenomenon we term *soliloquizing*, where the model self-generates hallucinated observations without interacting with the environment.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：尽管语言模型（LM）智能体在编码、网页浏览等领域表现出色，但在网络安全任务（如解决 Capture The Flag 挑战）中进展有限。现有 LM 智能体缺乏与交互式终端程序（如调试器、服务器连接工具）直接交互的能力，而这些工具对于漏洞发现和利用至关重要。
- **整体含义**：本研究旨在通过为 LM 智能体设计全新的交互式终端工具集，弥补其在安全场景中的能力短板，验证“赋予终端交互能力”对提升安全任务性能的关键作用。

## 2. 方法论

- **核心思想**：构建一个名为 **EnIGMA** 的 LM 智能体，为其配备一套 **Interactive Agent Tools（交互式智能体工具）**，使其能够**首次运行交互式终端程序**（如调试器、服务器连接工具），从而增强漏洞发现与利用能力。
- **关键技术细节**：
  - 工具集包括：调试器（如 GDB）、服务器连接工具（如 netcat）等，模拟人类安全分析师在终端中交互操作。
  - 智能体通过自然语言指令调用这些工具，并根据工具返回结果动态调整下一步操作，形成闭环。
  - 未提及具体模型架构或公式，强调工程化集成与接口设计。

## 3. 实验设计

- **数据集与场景**：使用 **390 个 CTF 挑战**，覆盖 **四个基准**：
  - NYU CTF
  - Intercode-CTF
  - CyBench
  - （第四个基准未在摘要中明确命名，可能为内部或社区基准）
- **对比方法**：摘要未列出具体对比基线，仅说明 EnIGMA 达到 **state-of-the-art (SOTA)** 结果。
- **额外分析**：研究了数据泄露问题，并提出新的量化方法；发现一种新现象 **soliloquizing**（模型自我生成幻觉观察而不与环境交互）。

## 4. 资源与算力

- 论文摘要**未明确说明**使用的 GPU 型号、数量、训练时长或推理开销。算力需求未知。

## 5. 实验数量与充分性

- **实验数量**：涵盖 **390 个挑战 × 4 个基准**，实验规模较大。
- **充分性**：多基准覆盖不同难度和类型的 CTF 挑战，并包含对数据泄露和幻觉现象的专项分析，设计较为全面。但缺少与现有其他 LM 智能体的直接对比（如 SWE-agent、ReAct 等），可能影响公平性。

## 6. 主要结论与发现

- **核心结论**：交互式终端工具**显著提升**了 LM 智能体在网络安全任务中的漏洞发现与利用成功率，验证了终端交互能力的关键作用。
- **发现**：
  - 新工具集使智能体能够完成之前无法处理的交互式挑战。
  - 存在 **soliloquizing** 现象：模型在没有环境反馈时自行生成看似合理但虚幻的观察，可能误导决策。

## 7. 优点

- **方法上的亮点**：首次为 LM 智能体设计可原生运行终端交互程序（如调试器）的工具集，弥补了安全领域的关键能力缺口。
- **实验设计**：采用多基准、大数据量测试，并引入对数据泄露和幻觉现象的定量分析，研究深度较强。
- **实用价值**：直接可应用于自动化漏洞挖掘、渗透测试等实际安全任务。

## 8. 不足与局限

- **实验覆盖**：仅聚焦于 CTF 挑战场景，未在真实世界漏洞库（如 CVE）或企业环境验证，泛化性未知。
- **偏差风险**：未披露对比基线，难以判断 SOTA 提升的具体幅度；未讨论模型过拟合或训练数据泄露对 CTF 任务的影响。
- **资源需求**：未提供算力统计，无法评估部署成本。
- **应用限制**：当前工具集可能仅适用于特定类型的交互式程序，对图形界面或协议复杂的工具有效性待验证。

（完）
