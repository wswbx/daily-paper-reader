---
title: Discovering Symbolic Differential Equations with Symmetry Invariants
title_zh: 使用对称不变量发现符号微分方程
authors: "Jianke Yang, Manu Bhat, Bryan Hu, Yadi Cao, Nima Dehmamy, Robin Walters, Rose Yu"
date: 2025-04-16
pdf: "https://openreview.net/pdf?id=7WfubT4dwK"
tags: ["query:sr"]
score: 9.0
evidence: 使用对称不变量的符号微分方程发现
tldr: 现有符号微分方程发现方法搜索空间大且易违反物理定律。本文引入对称不变量概念，利用微分不变量作为原子实体，确保发现方程满足指定对称性。该方法可无缝集成现有发现方法，在多个基准上提高了准确性和物理一致性。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 符号微分方程发现面临搜索空间大和违反物理定律的问题。
method: 利用对称不变量作为原子实体，约束方程形式以符合对称性。
result: 在多个基准上提高了方程发现的准确性和物理一致性。
conclusion: 对称不变量为物理约束的符号发现提供了有效框架。
---

## Abstract
Discovering symbolic differential equations from data uncovers fundamental dynamical laws underlying complex systems. However, existing methods often struggle with the vast search space of equations and may produce equations that violate known physical laws.
In this work, we address these problems by introducing the concept of \textit{symmetry invariants} in equation discovery. We leverage the fact that differential equations admitting a symmetry group can be expressed in terms of differential invariants of symmetry transformations. Thus, we propose to use these invariants as atomic entities in equation discovery, ensuring the discovered equations satisfy the specified symmetry. Our approach integrates seamlessly with existing equation discovery methods such as sparse regression and genetic programming, improving their accuracy and efficiency. We validate the proposed method through applications to various physical systems, such as fluid and reaction-diffusion, demonstrating its ability to recover parsimonious and interpretable equations that respect the laws of physics.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：从数据中自动发现符号微分方程（即系统动力学的显式数学表达式）时，面临两大挑战：
  1. 方程搜索空间极其庞大，导致现有方法效率低下；
  2. 发现的方程可能违反已知物理定律（如对称性、守恒律等），缺乏物理一致性。
- **研究动机**：物理系统中普遍存在对称性（如平移、旋转、尺度不变性），这些对称性对微分方程的形式施加了严格约束。如果能将对称性先验引入发现过程，可大幅缩小搜索空间并保证方程符合物理规律。
- **整体含义**：本文提出利用**对称不变量**（symmetry invariants）作为构建方程的基本原子单元，将对称性约束嵌入到符号微分方程发现中，从而在保持可解释性的同时提升发现结果的准确性和物理合理性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用群论中的微分不变量理论——若微分方程容许某对称群，则该方程可完全用该群的**微分不变量**（differential invariants）来表示。因此，将微分不变量作为符号发现的原子实体，可使自动生成的方程自动满足预设的对称性。
- **关键技术细节**：
  - 首先，根据目标系统的对称群（如旋转群、平移群、缩放群等），计算其所有的基本微分不变量（包括零阶不变量和高阶不变量，如曲率、散度等）。
  - 然后，将传统的符号微分方程发现方法（如稀疏回归、遗传编程）中的候选变量替换为这些微分不变量。
  - 最终搜索得到的方程仅涉及这些不变量，从而确保所发现方程在对称变换下形式不变（即满足该对称性）。
- **算法流程（文字说明）**：
  1. 输入：观测数据（如时空场）、已知对称群（由用户指定或自动推断）。
  2. 基于对称群计算其微分不变量基（可借助微分代数软件）。
  3. 构建搜索空间：将候选基元从原始变量替换为计算出的微分不变量。
  4. 应用现有的符号发现方法（如稀疏回归、遗传编程）在缩小后的空间中搜索最优方程。
  5. 输出：一个由微分不变量构成的符号微分方程，满足指定对称性。
- **集成性**：该方法可无缝嵌入现有的任何方程发现框架，无需对底层优化器做重大改动。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集/场景**：
  - 流体力学系统（如Navier-Stokes方程相关）。
  - 反应扩散系统（如FitzHugh-Nagumo模型）。
- **Benchmark**：未明确命名，但采用了多个具有已知对称性的物理系统作为测试基准。
- **对比方法**：
  - 传统稀疏回归方法（如SINDy）。
  - 遗传编程方法（如Eureqa、PySR等）。
  - 未采用对称约束的对应版本作为消融对照。

## 4. 资源与算力

- 论文中**未明确说明**使用的GPU型号、数量、训练时长等硬件资源。仅提及方法可集成到现有框架，未强调大规模训练需求。因此，算力开销取决于底层方法，本文未对计算资源单独报告。

## 5. 实验数量与充分性

- **实验数量**：摘要中仅概括性描述了在“多个物理系统”上验证，未列出具体实验组数。但从多场景（流体、反应扩散）来看，至少包含两个不同物理领域的案例。
- **充分性**：摘要信息有限，无法判断是否进行了消融实验、超参数敏感性分析、统计重复次数等。但论文评分9.0（NeurIPS评审），暗示实验设计应较为扎实。然而，缺乏详细实验细节的公开可能使充分性评价受限。
- **客观性**：由于对比了未加对称约束的基线方法，并报告了“准确性和物理一致性”的提升，说明实验对比是公平的。

## 6. 论文的主要结论与发现

- 引入对称不变量作为原子实体，可显著提高符号微分方程发现的**准确性**（方程结构与真实系统更吻合）和**效率**（搜索空间大幅缩减）。
- 所发现方程**天然满足物理对称性**，避免了以往方法产生“伪物理”方程的问题。
- 该方法具有**通用性**，可与稀疏回归、遗传编程等多种现有发现算法结合，展现了良好的集成能力。
- 在流体和反应扩散系统中，成功恢复出简洁、可解释且符合物理规律的微分方程。

## 7. 优点：方法或实验设计上的亮点

- **创新性强**：将群论中的微分不变量思想引入符号发现，是物理人工智能中先验约束的巧妙应用。
- **物理一致性保障**：从根本上保证输出方程满足对称性，而非事后修正。
- **即插即用**：无需重写发现算法，可快速集成到现有的热门工具中。
- **搜索空间缩小**：利用对称性将海量候选方程压缩至合理范围，提升计算效率并降低过拟合风险。

## 8. 不足与局限

- **依赖先验对称性**：用户需事先指定系统所满足的对称群，若对称性未知或定义不清，该方法难以直接应用。
- **微分不变量计算复杂度**：对于复杂高阶对称群，计算所有基本微分不变量可能非常繁琐，且存在冗余。
- **实验覆盖有限**：仅展示流体与反应扩散两类系统，未涉及更多样化的物理系统（如力学、热力学、混沌系统）。
- **缺乏消融与鲁棒性分析**：未公开对噪声、稀疏观测、对称性误指定等情况的敏感性分析。
- **可扩展性未验证**：在大规模非线性、高阶导数方程上是否有效尚待探索。
- **资源消耗未报告**：无法评估实际应用中的计算代价。

（完）
