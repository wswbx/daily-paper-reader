---
title: "MDBench: Benchmarking Data-Driven Methods for Model Discovery"
title_zh: MDBench：模型发现数据驱动方法的基准测试
authors: "Amirmohammad Ziaei Bideh, Aleksandra Georgievska, Jonathan Gryak"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39056/43018"
tags: ["query:sr"]
score: 8.0
evidence: 模型发现基准，包含符号回归方法比较
tldr: MDBench针对模型发现领域缺乏综合基准的问题，构建了开源框架评估12种算法在14个PDE和63个ODE上的表现，包含不同噪声水平。评价指标涵盖导数预测精度和模型复杂度等。该基准直接服务于符号回归方法比较与状态评估需求。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 模型发现领域缺乏全面、标准化的基准，特别是针对动力学系统。
method: 构建开源基准框架，包含多个PDE/ODE和噪声水平，评估12种算法。
result: 揭示了不同算法在噪声下的性能权衡，提供了标准化评测。
conclusion: MDBench促进了模型发现方法的系统比较与进步。
---

## Abstract
Model discovery aims to uncover governing differential equations of dynamical systems directly from experimental data. Benchmarking such methods is essential for tracking progress and understanding trade-offs in the field. While prior efforts have focused mostly on identifying single equations, typically framed as symbolic regression, there remains a lack of comprehensive benchmarks for discovering dynamical models. To address this, we introduce MDBench, an open-source benchmarking framework for evaluating model discovery methods on dynamical systems. MDBench assesses 12 algorithms on 14 partial differential equations (PDEs) and 63 ordinary differential equations (ODEs) under varying levels of noise. Evaluation metrics include derivative prediction accuracy, model complexity, and equation fidelity. We also introduce seven challenging PDE systems from fluid dynamics and thermodynamics, revealing key limitations in current methods. Our findings illustrate that linear methods and genetic programming methods achieve the lowest prediction error for PDEs and ODEs, respectively. Moreover, linear models are in general more robust against noise. MDBench accelerates the advancement of model discovery methods by offering a rigorous, extensible benchmarking framework and a rich, diverse collection of dynamical system datasets, enabling systematic evaluation, comparison, and improvement of equation accuracy and robustness.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的中文总结。

## 论文详细中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：数据驱动的模型发现方法（从实验数据中自动发现动力学系统的控制方程）领域缺乏一个全面、标准化、可扩展的基准测试平台。现有基准要么专注于单一方程的符号回归（如SRBench），要么仅评估黑盒预测模型（如PDEBench），未能充分覆盖动力学系统（尤其是偏微分方程系统）的发现任务。
- **研究动机**：随着高维大规模实验数据时代的到来，仅靠专家知识推导方程越来越不现实。自动化的模型发现方法变得至关重要，但不同方法（如遗传规划、线性模型、深度学习、大规模预训练）在准确性、鲁棒性、复杂度等方面存在显著差异，需要一个统一框架进行公平比较和追踪进展。
- **整体含义**：本文推出的MDBench填补了这一空白，为推动可解释、鲁棒的动力学系统模型发现研究提供了重要的基础设施。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：构建一个开源、可扩展的基准测试框架MDBench，统一评估多种模型发现方法在常微分方程（ODE）和偏微分方程（PDE）系统上的表现。
- **关键技术细节与流程**：
    - **数据预处理**：
        - 对ODE系统：输入为状态变量u，目标为其时间导数du/dt（通过有限差分计算）。
        - 对PDE系统：利用有限差分法（二阶精度，通过findiff包）计算状态变量及其一至四阶空间导数，构建符号特征库；目标同样为时间导数。
    - **噪声设置**：在干净数据上添加乘法高斯噪声，信噪比（SNR）分别为40 dB、30 dB、20 dB、10 dB。噪声同时影响了状态变量和通过有限差分估计的导数。
    - **评价指标**：
        1. **NMSE（归一化均方误差）**：衡量预测时间导数与真实导数之间的精度。NMSE越低越好。
        2. **复杂度（Complexity）**：表达式树中节点、常数项和操作的总数，通过SymPy计算。鼓励简洁的方程。
    - **超参数调优**：为每个方法-数据集对预定义超参数网格，使用复合适应度函数（平衡NMSE与复杂度）选择最佳配置。适应度函数为 `s = 1/(1+NMSE) + φ * exp(-l/L)`，其中φ=1，L=200。
    - **训练与推理**：时间维度上按60%训练、20%验证、20%测试拆分。验证集用于调参，之后在训练+验证集上重新训练模型，最后在测试集上评估。
- **算法分类与所选方法**：论文将模型发现方法分为四类：
    - **线性模型（LM）**：PDEFIND, SINDy, WSINDy, E(W)SINDy, Bayesian, DeepMoD
    - **遗传规划（GP）**：PySR, Operon
    - **深度学习（DL）**：EQL, uDSR
    - **大规模预训练（LSPT）**：ODEFormer, End2end

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法
- **数据集**：
    - **ODE系统**：63个系统（来自ODEBench，涵盖Strogatz教材和Wikipedia），状态变量1到4个，模拟真实世界现象。
    - **PDE系统**：14个PDE系统。包括文献中常用的Advection, Burgers, KdV, KS, NLS, Reaction-Diffusion, Advection-Diffusion等，以及作者新贡献的7个更具挑战性的物理系统：Heat (Laser), Heat (Solar), Navier-Stokes (Channel), Navier-Stokes (Cylinder), Reaction-Diffusion (Cylinder)等。
- **场景**：在无噪声及四种不同信噪比（40, 30, 20, 10 dB）的噪声条件下进行评估。
- **对比方法**：共12种方法，覆盖四大类别：
    - **LM**: PDEFIND, SINDy, WSINDy, E(W)SINDy, Bayesian, DeepMoD
    - **GP**: PySR, Operon
    - **DL**: EQL, uDSR
    - **LSPT**: ODEFormer, End2end

### 4. 资源与算力
- **计算资源**：
    - CPU：Ubuntu 22.04.3服务器，24核Intel Core Ultra 9 285K @ 1.44 GHz，96 GB RAM。
    - GPU：单张NVIDIA RTX 4000 Ada Generation GPU，20 GB显存（用于需要GPU加速的方法：EQL, uDSR, ODEFormer, End2end, DeepMoD）。
- **时间限制**：每个实验（含训练和超参数调优）设置了12小时的时间上限。
- **运行时间统计**：文中给出了所有方法在所有PDE数据集上（干净数据）的平均运行时间，例如PDEFIND平均26±53分钟，PySR平均8±13分钟，uDSR平均9±11分钟。具体运行时间方差较大。

### 5. 实验数量与充分性
- **实验数量**：
    - 在63个ODE系统和14个PDE系统上进行评估，共计77个动力学系统。
    - 每个系统测试了无噪声和4个噪声水平共5种情况。
    - 对比了12种不同算法。如果每种算法在每个数据集、每个噪声水平下运行一次，总实验数约为77×5×12=4620次（实际由于部分方法在某些数据集上失败或超时，数量会减少）。
- **充分性分析**：
    - **充分性较高**：覆盖了广泛的系统类型（线性/非线性、低维/高维、ODEs/PDEs）、多种噪声水平、多种算法类别，并采用了统一的超参数调优流程和标准化的评价指标。
    - **公平性较好**：对所有方法采用相同的训练/验证/测试划分；超参数通过验证集上的复合适应度函数自动选择；对GP方法使用作者推荐的默认设置；对所有方法施加12小时时间限制。
    - **客观性**：使用公开数据集和方法代码，结果可复现。

### 6. 论文的主要结论与发现
- **总体性能**：没有一种方法在所有场景下都表现最优。
- **ODE系统**：
    - 遗传规划方法（如PySR）通常预测误差最低。
    - 线性模型（如SINDy、ESINDy）在噪声下表现更鲁棒，生成的方程更简洁。
    - 预训练方法（如ODEFormer）在低噪声下表现良好，但对噪声敏感，易过拟合。
    - 端到端方法（End2end）预测误差最大，因其预训练数据不包含动力学系统。
- **PDE系统**：
    - 线性方法（如WSINDy）在低噪声下预测误差最低，对噪声的鲁棒性优于GP方法。
    - PDE系统的噪声敏感性远高于ODE系统，因为空间导数的计算会放大噪声。
    - 高维系统（如3D Heat）对所有方法都是巨大挑战，线性方法因函数库膨胀而效率下降，GP方法搜索空间爆炸。
    - 带有非均匀强制项的真实系统（如Heat (Laser)、Reaction-Diffusion (Cylinder)）对当前所有方法都极具挑战性，大多数方法无法正确恢复方程。
- **关键发现**：线性模型在PDE上更优，GP在ODE上更优；线性模型对噪声更鲁棒；当前方法在面向真实世界的复杂PDE系统（高维、异质性、复杂强制函数）上存在严重不足。

### 7. 优点
- **综合性**：首个同时覆盖大量ODE和PDE系统、多种方法类别（12种算法）的模型发现基准。
- **标准化**：提供了统一的数据格式、噪声模型、预处理流程、超参数调优协议和评价指标，确保了公平比较。
- **可扩展性**：开源框架，易于加入新的方法和数据集。
- **挑战性**：引入了7个来自流体力学的复杂PDE系统，这些系统带有空间依赖或分段强制函数，揭示了现有方法的局限性，有助于推动算法改进。
- **实用性**：评估了噪声鲁棒性，以及预测精度与模型复杂度之间的权衡，对实际应用有指导意义。

### 8. 不足与局限
- **实验覆盖偏差**：
    - ODE数据全部来自ODEBench（Strogatz教材和Wikipedia），可能不能代表所有类型的ODE系统。
    - PDE数据虽包含流体动力学等复杂系统，但空间网格均为均匀网格，未考虑不规则或自适应网格场景。
    - 噪声模型仅为高斯乘法噪声，未涵盖其他实际噪声类型（如泊松噪声、有色噪声）。
- **评估指标局限**：
    - NMSE和复杂度并不能完全反映方程的结构正确性。例如，某些方法可能得到低NMSE但结构完全不同的方程。
    - 作者也指出了缺乏“方程保真度”的可靠度量，建议未来的工作引入像Sobolev半范数这样的指标。
- **方法实现问题**：
    - 部分方法（如DeepMoD, uDSR, End2end）因内存或运行时间限制，无法处理大数据集，只能使用子采样数据（最多10，000点），这可能影响其性能。
    - 一些方法在特定数据集上因代码实现不支持高维或多变量系统而失败。
- **局限性总结**：
    - 1. 假设空间均匀的物理参数，不适用于异质性系统。
    - 2. 高维系统时性能急剧下降（函数库爆炸或搜索空间过大）。
    - 3. 对噪声敏感，尤其是通过导数放大的PDE系统。
    - 4. 缺乏衡量方程真实保真度的良好指标。
    - 5. 多种方法因实现限制无法直接应用于某些数据集。

（完）
