---
title: Learning Randomized Reductions
title_zh: 学习随机归约
authors: "Ferhat Erata, Orr Paradise, Thanos Typaldos, Timos Antonopoulos, ThanhVu Nguyen, Shafi Goldwasser, Ruzica Piskac"
date: 2026-04-30
pdf: "https://openreview.net/pdf/347cf5cad260da0034ae2a9c92c2465df2f41fa4.pdf"
tags: ["query:sr"]
score: 6.0
evidence: 将符号回归作为后端之一
tldr: 本文提出Bitween算法，用于自动学习随机自归约。其Vanilla Bitween集成了线性回归、遗传编程、符号回归和混合整数规划等多个后端，其中线性回归后端表现最佳，在RSR-Bench基准上成功发现了80个函数中43个的归约，包括已知的首次归约。符号回归作为其中一个后端，展示了其在自动发现归约中的辅助作用。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 随机自归约的发现长期依赖人工推导，限制了实际应用。
method: 提出Bitween算法，形式化学习框架并集成多种后端（包括符号回归）。
result: 线性回归后端在RSR-Bench上发现43/80个函数的归约。
conclusion: 自动学习RSR是可行的，符号回归作为后端之一有潜力。
---

## Abstract
Randomized self-reductions (RSRs) express $f(x)$ using $f$ evaluated at random correlated points, enabling self-correcting programs, instance-hiding protocols, and applications in complexity theory and cryptography. Yet discovering RSRs has required manual expert derivation for over 40 years, limiting their practical use.
We present Bitween for automated RSR learning. First, we formalize RSR learning with sample complexity analysis under correlated sampling. Second, we develop Vanilla Bitween, which integrates multiple backends (linear regression, genetic programming, symbolic regression, and mixed-integer programming). The linear regression backend outperforms the others, discovering RSRs for 43 of 80 functions (54%) in RSR-Bench, our benchmark suite, including the first known reduction for sigmoid. Third, we introduce Agentic Bitween, a neuro-symbolic approach where LLM agents propose novel query functions beyond the fixed set ($x+r$, $x-r$, $x \cdot r$, $x$, $r$) in prior work. Agentic Bitween discovers RSRs for 64 of 80 functions (80%), outperforming pure neural baselines in both RSR discovery and verification accuracy.

---

## 论文详细总结（自动生成）

好的，根据您提供的论文元数据和摘要信息，以下是对《Learning Randomized Reductions》一文的详细中文总结。

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：随机自归约（Randomized Self-Reductions, RSRs）是表达函数 $f(x)$ 时利用 $f$ 在随机相关点上的求值结果的一种技术，广泛应用于自矫正程序、实例隐藏协议以及复杂性和密码学领域。然而，40多年来发现新的RSR一直依赖人工专家推导，这严重限制了其实际应用和规模化。
- **研究动机**：自动化RSR的发现过程，降低门槛，使其能应用于更多函数。
- **整体含义**：本文证明了RSR的自动学习是可行的，并提出了一套有效的算法框架，能够自动发现包括sigmoid函数在内的多种函数的新归约。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将RSR发现形式化为一个学习问题，并设计一个名为**Bitween**的算法框架来自动学习RSR。
- **关键技术细节**：
    - **形式化学习框架**：首先对RSR学习问题进行形式化定义，并给出了在相关采样（correlated sampling）下的样本复杂度分析。
    - **Vanilla Bitween**：基础版本，集成了多个后端，包括：
        - 线性回归（Linear Regression）
        - 遗传编程（Genetic Programming）
        - 符号回归（Symbolic Regression）
        - 混合整数规划（Mixed-Integer Programming）
    - **其中线性回归后端表现最佳**，在基准测试中成功发现了80个函数中43个（54%）的归约，包括首次发现sigmoid函数的归约。
    - **Agentic Bitween**：神经符号（neuro-symbolic）进阶版本，引入大语言模型（LLM）智能体，能够提出超越固定查询函数集合（如 $x+r$, $x-r$, $x \cdot r$, $x$, $r$）的新查询函数，从而扩展搜索空间。
- **算法流程（文字说明）**：
    1. 给定目标函数 $f$ 和输入 $x$，定义一组可能的查询变体（如 $x+r$, $x-r$ 等）。
    2. 使用选定的后端（如线性回归）尝试学习一个表达式（通常是线性组合或非线性组合），使得 $f(x)$ 可以用 $f$ 在这些查询变体上的值来表示。
    3. 学习到的表达式需经过验证，确保其是有效的RSR。
    4. 在Agentic Bitween中，LLM会动态生成新的、非预定义的查询函数，进一步探索更多可能的归约形式。

## 3. 实验设计：使用了哪些数据集/场景，它的benchmark是什么，对比了哪些方法

- **Benchmark**：构建了名为**RSR-Bench**的基准测试套件，包含80个不同的函数。
- **数据集/场景**：涵盖多种函数（具体函数类别未在摘要中详述，但包括sigmoid等经典函数），旨在测试算法自动发现RSR的能力。
- **对比方法**：
    - **内部后端对比**：在Vanilla Bitween中，对比了线性回归、遗传编程、符号回归和混合整数规划四个后端的性能。
    - **纯神经基线**：在Agentic Bitween中，将其与纯神经网络基线进行了对比，对比维度包括RSR发现率（discovery）和验证准确率（verification accuracy）。

## 4. 资源与算力

- **文中未明确说明**：摘要和元数据中未提及使用了多少GPU型号、数量以及训练时长等具体算力信息。仅提到Agentic Bitween使用了LLM智能体（具体模型型号未指明），但未给出硬件资源细节。

## 5. 实验数量与充分性

- **实验数量**：主要依据两个主要实验：
    1. **Vanilla Bitween** 在RSR-Bench（80个函数）上运行，报告发现43/80个归约（54%）。
    2. **Agentic Bitween** 在同样的80个函数上运行，报告发现64/80个归约（80%）。
- **充分性评估**：
    - 实验覆盖了多个后端和完整的基准套件，对比了不同方法，具有较好的客观性。
    - 但未提及进行额外的消融实验（如去掉LLM、改变样本复杂度等）、未在不同规模或领域的函数集上测试泛化性，也未提到多次运行取统计结果。因此实验充分性中等，基本验证了假设，但深度和广度可以进一步加强。

## 6. 论文的主要结论与发现

- **主要结论**：自动学习随机自归约（RSR）是可行的。
- **关键发现**：
    - Vanilla Bitween的线性回归后端显著优于其他后端（遗传编程、符号回归、混合整数规划），成功发现54%函数的归约。
    - 首次自动发现了sigmoid函数的RSR。
    - Agentic Bitween通过引入LLM智能体提出新查询函数，将发现率提升至80%，并在发现准确率和验证准确率上均优于纯神经基线方法。

## 7. 优点：方法或实验设计上有哪些亮点

- **方法亮点**：
    - **问题形式化**：首次将RSR发现问题系统化为学习问题，并提供了理论样本复杂度分析。
    - **多后端集成**：Vanilla Bitween集成了多种回归和搜索方法，便于比较不同技术路线的效果。
    - **神经符号融合**：Agentic Bitween创新性地融合了大语言模型的生成能力和传统优化方法（符号回归/线性回归），既保留了搜索的严谨性，又引入了灵活的新查询生成能力。
- **实验亮点**：
    - 构建了公开的基准套件RSR-Bench，为后续研究提供了标准评估平台。
    - 实验明确比较了不同后端和神经基线，设计清晰。

## 8. 不足与局限

- **实验覆盖**：基准函数只有80个，且来源单一，可能未能覆盖所有类型的函数或复杂场景（如高维输入、非平滑函数）。未在更大的函数库上验证。
- **偏差风险**：Agentic Bitween依赖LLM智能体，LLM的固有偏见（如偏向常见函数形式）可能影响新查询生成的多样性和公平性。纯神经基线的具体结构未描述，对比可能不够彻底。
- **应用限制**：自动发现的RSR可能仅在特定采样分布下有效，其实际部署到自矫正程序或密码学协议中的效率和安全性尚未讨论。
- **可重复性**：算力资源未报告，难以复现；后端的超参数设置也未在摘要中说明。
- **符号回归角色**：虽然符号回归是后端之一，但性能不如线性回归，论文未深入分析其原因，也没有指出符号回归在哪些特定函数上可能优于其他方法。

（完）
