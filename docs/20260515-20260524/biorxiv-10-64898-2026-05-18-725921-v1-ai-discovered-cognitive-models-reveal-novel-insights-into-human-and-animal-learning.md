---
title: AI-Discovered Cognitive Models Reveal Novel Insights into Human and Animal Learning
title_zh: AI发现的认知模型揭示人类与动物学习的新见解
authors: "Kasenberg, D., Castro, P. S., Eckstein, M. K., Elteto, N., Dabney, W., Wang, C. L., Engelcke, M., Mohanta, R., Dev, A., Botvinick, M. M., Tomasev, N., Turner, G. C., Costa, V. D., Daw, N. D., Stachenfeld, K. L., Miller, K. J."
date: 2026-05-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.18.725921v1.full.pdf"
tags: ["query:ai-scientific-discovery"]
score: 9.0
evidence: AI发现认知模型揭示学习新见解
tldr: 本文提出DataDIVER，一种自动从数据中发现计算模型的方法。传统手工模型难以捕捉行为全貌，数据驱动方法需大量人力。DataDIVER生成简短计算机程序形式的模型，兼顾数据拟合与简洁性，与理论框架连接，可理解并能做出新预测，部分预测在现有数据重分析中得到验证，有望加速科学发现。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统手工认知模型难以捕捉行为的全部丰富性，而现有数据驱动方法需要大量人力才能从数据中提取见解。
method: 提出DataDIVER，一种自动发现计算模型的通用方法，模型以简短计算机程序形式，优化目标为既拟合数据又好理解。
result: 发现的模型与现有理论框架明确连接，可被科学家理解，并能做出新颖预测，部分预测在现有数据重分析中得到验证。
conclusion: 通用工具从数据中自动发现新见解，结合日益丰富的大数据集，有望显著加速科学发现。
---

## 摘要
科学模型在自然科学中广泛用作科学理论与经验数据之间的接口。例如，在人类和动物学习研究中，这些模型扮演着关键角色，它们表达算法假设并将其与心理学和神经科学数据联系起来。这些模型传统上由专家研究人员根据现有理论或新见解手工构建。然而，已知这种手工构建的模型即使在狭窄领域内也无法捕捉行为的全部丰富性。另一种数据驱动的方法已经出现，旨在通过拟合和解释灵活模型来发现新见解。然而，这些工具需要大量人力从数据中提取见解，并且尚不清楚如何高效地从数据中发现新思想。在这里，我们提出了DataDIVER，一种从数据中自动发现计算模型的通用方法，并证明这些模型揭示了人类和动物学习的新机制见解。我们的方法生成的模型采用短计算机程序的形式，这些程序既优化为很好地拟合数据，又力求简单。这些程序与现有的理论框架明确连接，并且易于人类科学家理解。它们还可以用于做出新颖的预测，其中一些预测我们证明在对现有数据的重新分析中得到证实。从数据中发现新思想的通用工具，尤其是与许多领域日益可用的大型数据集相结合，将极大地加速科学发现。

## Abstract
Scientific models are widely used across the natural sciences as an interface between scientific theories and empirical data. Such models play a key role, for example, in the study of human and animal learning, where they express algorithmic hypotheses and relate them to psychology and neuroscience data. These models are traditionally handcrafted by expert researchers based on existing theory or new insights. Such handcrafted models, however, are now known to fall short of capturing the full richness of behavior, even in their narrow domains. An alternative data-driven approach has emerged, seeking to discover new insights by fitting and interpreting flexible models. However, these tools require substantial human effort to derive insight from data, and it has been unclear how to discover new ideas from data efficiently. Here, we present DataDIVER, a general approach for automatically discovering computational models from data, and demonstrate that these models surface novel mechanistic insights into human and animal learning. Our approach delivers models that take the form of short computer programs, which are optimized both to fit data well and to be simple. These programs explicitly connect with existing theoretical frameworks and are readily understandable by human scientists. They can also be used to make novel predictions, some of which we show are borne out in re-analysis of existing data. General-purpose tools for surfacing new ideas from data, especially in combination with the large datasets that are increasingly available in many fields, stand to dramatically accelerate scientific discovery.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将对这篇题为《AI发现的认知模型揭示人类与动物学习的新见解》的论文进行结构化、深入、客观的总结。

---

### 论文详细总结

#### 1. 论文的核心问题与整体含义

*   **研究动机**：在认知科学（特别是奖励学习领域），传统上依赖专家手工构建计算模型来解释行为数据。然而，这些手工模型已被证明无法充分捕捉行为的复杂性，尤其是在大规模数据集面前表现不佳。另一方面，新兴的数据驱动方法（如深度神经网络）虽然拟合能力强，但通常难以解释，作为“黑箱”模型无法直接提供关于认知机制的洞见。
*   **核心问题**：如何自动化地从行为数据中发现既能精确拟合数据，又具备高可解释性、能揭示新机制见解的符号化计算模型？
*   **整体含义**：本文提出的方法旨在解决AI科学发现中的一个核心难题——不仅是预测，更是解释。它尝试用AI生成可读的代码作为科学模型，桥接预测能力与可解释性之间的鸿沟，有望加速对大脑学习算法的科学理解。

#### 2. 论文提出的方法论

*   **核心思想**：提出一个名为 **DataDIVER (Data-driven Discovery of Interpretable models Via Evolutionary Refinement)** 的通用框架。该框架利用大型语言模型（LLM）和进化算法，自动生成并优化以短计算机程序形式呈现的认知模型。这些程序被优化以同时满足两个目标：高数据拟合度和低程序复杂度。
*   **关键技术细节**：
    1.  **模型表示**：模型以 **JAX** 编写的可微分Python程序呈现，程序定义了内部状态（如价值、痕迹）和基于这些状态的更新及选择概率函数。
    2.  **两阶段优化**：
        *   **阶段一：最大化拟合度 (Maximize Quality-of-Fit)**。使用 **AlphaEvolve**（一个基于LLM的进化算法）优化程序，主要目标是最大化模型对观测数据的拟合度（归一化似然）。此阶段产生的程序非常复杂但拟合度极高。
        *   **阶段二：简化 (Simplify)**。在给定不同拟合度下限的前提下，使用第二个AlphaEvolve运行来最小化程序复杂度（通过 **Halstead effort** 度量）。这会产生一系列在不同拟合度与复杂度之间权衡的简化程序。
    3.  **可读性优化**：在获得简化程序后，使用另一个LLM（Gemini 2.5 Pro）对程序进行重构，以改善代码结构和添加注释，使其更易被人类科学家理解。
*   **算法流程**：
    1.  **输入**：行为数据（人类/动物的选择与奖励历史）。
    2.  **第一阶段**：运行AlphaEvolve，生成并评估大量程序，目标是最大化拟合度，输出一个“最佳拟合”程序。
    3.  **第二阶段**：从第一阶段帕累托前沿的程序出发，在三个不同的拟合度下限条件下，运行AlphaEvolve来最小化复杂度。输出三个不同复杂度级别的“简化”程序。
    4.  **后处理**：使用LLM对简化程序进行代码重构以提升可读性。
    5.  **人工合成**：作为可选步骤，研究人员根据多个发现程序中的共同机制，手动构建一个“合成”程序，以整合最佳洞见。
    6.  **输出**：可读的、可解释的计算机程序，作为候选的认知模型。

#### 3. 实验设计

*   **数据集与场景**：使用了来自五个不同物种和实验场景的公开学习行为数据集：
    *   **人类多臂老虎机 (Human Bandit)**：人类在四个选项中选择，获得点数奖励。
    *   **大鼠老虎机 (Rat Bandit)**：大鼠在两个选择口中选择，获得液体奖励。
    *   **果蝇老虎机 (Fly Bandit)**：果蝇在两个气味中选择，获得糖水奖励。
    *   **猴子老虎机 (Monkey Bandit)**：猴子在三个图像中选择，获得奖励，并能接触新图像（新奇性）。
    *   **大鼠两步任务 (Rat Two-step)**：大鼠的选择会随机导向不同状态，用于区分模型基础与无模型学习。
*   **Benchmark**：每个数据集都有一个来自文献的“手工基线模型”，作为基准对比。
*   **对比方法**：
    *   **手工基线模型**：每个数据集当前最好的认知模型。
    *   **递归神经网络 (RNN)**：一种“黑箱”深度学习模型，作为非符号化模型的性能上限参考。
    *   **DataDIVER发现的模型**：
        *   “仅拟合”程序：来自第一阶段，高复杂度。
        *   三种简化程序：低、中、高拟合度下限，对应不同的复杂度-性能权衡。
        *   “合成”程序：人工整合发现洞见的程序。

#### 4. 资源与算力

*   论文**未明确说明**具体的计算资源（如GPU型号、数量、训练总时长等）。
*   文中提到使用了 **Gemini 2.5 Flash** 作为AlphaEvolve的底层LLM，并使用 **Gemini 2.5 Pro** 进行代码可读性重构。所有AlphaEvolve运行在10万步后停止。程序使用 **JAX** 编写，以便利用GPU进行高效的梯度优化。

#### 5. 实验数量与充分性

*   **实验数量**：实验量非常充分。涵盖了5个迥异的跨物种数据集，每个数据集有3次独立的DataDIVER运行，每次运行产生1个“仅拟合”程序和最多3个简化程序，总计产生了数十个候选模型。此外，还对RNN基线进行了超参数搜索，并进行了广泛的自动化和选择性消融实验。
*   **充分性**：实验设计较为充分、客观和公平。
    *   **交叉验证**：使用两折交叉验证（按session划分）来拟合个体参数，并在**完全未见过的个体上**评估最终模型，确保了泛化能力。
    *   **多维度评估**：不仅评估了拟合度，还通过生成人工数据并分析其“滞后回归”统计量，评估了模型的正确性。这能检验模型是否捕捉了真实数据的行为模式。
    *   **消融实验**：通过自动删除代码行、替换操作符等，验证了程序中每个部分对性能的贡献，确定了哪些是关键机制。
    *   **对比公平性**：所有发现的程序与手工基线、RNN都采用了相同的评估协议。
    *   尽管实验规模庞大且设计严谨，但模型的“新颖见解”部分（如“工作记忆”和“重置”机制）的验证，尚局限于对现有数据的统计分析，而非全新的、独立的实验。

#### 6. 论文的主要结论与发现

1.  **DataDIVER发现了高度竞争的程序**：第一阶段产生的“仅拟合”程序在拟合度上显著超越了手工基线模型，并基本弥合了其与“黑箱”RNN之间的差距。这表明符号化模型可以达到与深度学习模型媲美的预测能力。
2.  **简化程序在解释性与性能之间实现了有效平衡**：简化后的程序（尤其是低门槛的程序）比手工基线更简单，同时仍能显著优于基线。这些程序更易读，科学家能够理解其背后的机制。
3.  **揭示了新颖的认知机制**：
    *   **人类**：揭示了“工作记忆”式（直接覆盖）的价值更新机制，而不是经典的增量学习。
    *   **人类**：发现了“非线性重置”的持续性机制，预测在长时间的重复选择后，一次切换会消除习惯性重复倾向。
    *   **猴子**：将新奇性偏好与价值学习分离为两个独立的认知变量，这与传统理论中两者合并为统一货币的假设相悖。
    *   **果蝇**：发现了随时间变化的动态学习率，以及“资格迹”（eligibility trace）机制。
    *   **大鼠**：发现了多系统交互、不对称的遗忘等新模式，并强调了以行动对（action-pair）而非单一偏好值来表征价值的重要性。
4.  **模型生成的数据能匹配真实数据**：由发现程序和合成程序生成的人工数据的行为统计特征（滞后回归曲线）与真实数据高度吻合，甚至优于手工基线。

#### 7. 优点

1.  **方法论的突破性**：成功地将AI（LLM + 进化算法）用于自动化发现可解释的符号化科学模型，这是 AI for Science 领域的一个重要进展。
2.  **优秀的可解释性**：输出的模型不是“黑箱”，而是带有注释的短代码，具备与现有理论对话的潜力，科学家可以理解和检验。
3.  **自动化的模型选择**：通过两步优化，自动地在“拟合度”和“复杂性”之间做出权衡，生成了覆盖不同科学需求的模型谱系。
4.  **新颖发现的可验证性**：不仅发现了新机制，还通过重分析现有数据验证了这些机制的预测（例如，人类重复运行后的切换行为），增加了其可信度。
5.  **通用性与跨学科性**：该方法框架不局限于奖励学习，可推广到其他需要从数据中推断潜在过程的科学领域。

#### 8. 不足与局限

1.  **计算资源的模糊性**：论文未能详细说明实现这些结果所需的具体计算资源，这可能会影响其他实验室复现其结果的可行性。
2.  **可解释性的上限**：即便经过简化，高门槛程序依然复杂难懂。发现模型的“可理解性”仍停留在能解释其操作层面，但模型是否揭示了大脑真实的神经实现仍然存疑。
3.  **新颖性的来源与偏差**：模型输出的“新颖”机制可能仅仅是挖掘了数据中未被发现的模式，而非真正的认知过程；LLM的固有知识也可能带来先验偏差，限制了发现真正超越人类理解的机制的可能性。
4.  **验证的局限性**：对新颖预测的验证仅限于对已有数据的统计检验，这是最具说服力的方式是执行全新的、旨在直接测试这些预测的实验。目前这项工作尚未完成。
5.  **“合成”过程的主观性**：手动构建“合成”程序的过程引入了研究者的主观判断，且作者指出“没有加入基于文献背景知识之外的新机制”，这种方法虽然在整合洞见上有帮助，但潜在的存在主观性。

（完）
