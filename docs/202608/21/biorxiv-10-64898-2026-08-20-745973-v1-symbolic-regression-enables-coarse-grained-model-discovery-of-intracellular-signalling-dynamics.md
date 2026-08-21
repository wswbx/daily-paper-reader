---
title: Symbolic regression enables coarse-grained model discovery of intracellular signalling dynamics
title_zh: 符号回归助力细胞内信号传导动力学的粗粒度模型发现
authors: "de Pomereu, T., Fröhlich, F."
date: 2026-08-21
pdf: "https://www.biorxiv.org/content/10.64898/2026.08.20.745973v1.full.pdf"
tags: ["query:sr"]
score: 9.0
evidence: 该论文将符号回归应用于细胞信号转导的粗粒度建模，属于符号回归的应用场景。
tldr: 细胞信号网络在癌症中常失调，其动力学建模受限于实验数据与计算资源，传统粗粒度方法依赖强假设。本文提出用符号回归数据驱动地检验信号系统能否在测量变量上粗粒度化，并自动发现紧凑且机制可解释的模型。在合成酶系统中恢复米氏动力学，在ERK磷酸化数据中识别出癌症相关基因过表达下的紧凑速率定律。这为判断降阶模型是否合理提供了新工具，也为设计新测量提供依据。
source: biorxiv
selection_source: fresh_fetch
motivation: 经典粗粒度建模依赖强假设，难以判断何时部分实验观测能支持系统动力学的降阶描述。
method: 利用符号回归从时间序列数据中自动发现测量变量间的紧凑动力学方程，并检验粗粒度化的可行性。
result: 在合成酶系统中恢复米氏动力学，在ERK磷酸化数据中识别出癌症相关基因过表达下的紧凑速率定律。
conclusion: 符号回归为判断粗粒度模型是否合理提供数据驱动准则，失败时提示更复杂动力学，指导新测量。
---

## 摘要
细胞通过蛋白质网络响应其环境，这些网络在癌症中常常失调，因此动力学建模至关重要。实验数据和计算资源的限制促使人们采用粗粒化方法来构建低维描述。然而，经典的粗粒化建模方法依赖强假设，使得部分实验观察何时支持系统动力学的简化描述尚不明确。在此，我们展示符号回归（SR）提供了一种数据驱动的方式，用以测试信号传导系统动力学是否以及以何种紧凑程度在所测变量上进行粗粒化，并在可行时推断出具有机理解释性的模型。在合成酶系统中，SR恢复了双步机制和三步扩展下的米氏动力学。随着数据质量降低，SR简化为有效的动力学定律，同时保持正确的理论极限。将SR应用于已发表的时间分辨ERK磷酸化数据，SR在选定的癌症相关基因过表达背景下识别出紧凑的磷酸化ERK速率定律，产生可解释的动力学效应。一个稀疏神经ODE基线在SR成功的场景中只需少量输入，但在SR失败时平均需要更多输入，表明在简化模型根本可学习的场景中，SR失败与更复杂的动力学相关，而简单数学模型无法描述这些动力学。综上所述，这些发现确立了符号回归作为一种测试何时需要紧凑粗粒度描述的方法，在存在这种描述时生成假设，并在不存在时激发潜在的新测量。

## Abstract
Cells respond to their environment through protein networks often dysregulated in cancer, making dynamical modelling crucial. Limitations in experimental data and computational resources motivate coarse-graining methods to build low-dimensional descriptions. Yet classical approaches to coarse-grained modelling rely on strong assumptions, leaving it unclear when partial experimental observations support reduced descriptions of system dynamics. Here we show that symbolic regression (SR) provides a data-driven way to test whether, and how compactly, the dynamics of a signalling system coarse-grain over the measured variables, and, when they do, infers mechanistically interpretable models. In synthetic enzyme systems, SR recovers Michaelis-Menten kinetics for the two-step mechanism and under three-step extensions. As data quality is degraded, SR simplifies toward effective kinetic laws while preserving correct theoretical limits. Applied to published time-resolved ERK phosphorylation data, SR identifies compact phospho-ERK rate laws in selected cancer-relevant gene overexpression contexts, yielding interpretable kinetic effects. A sparse neural ODE baseline requires few inputs where SR succeeds, but on average more where it fails, indicating that, where a reduced model is learnable at all, SR failure is associated with more complex dynamics that a simple mathematical model cannot describe. Together, these findings establish symbolic regression as a way to test when a compact coarse-grained description is warranted, generating hypotheses where one holds and motivating potential new measurements where it does not.

---

## 论文详细总结（自动生成）

# 符号回归助力细胞内信号传导动力学的粗粒度模型发现——论文总结

## 1. 论文的核心问题与整体含义

- **研究背景**：细胞通过蛋白质信号网络响应环境，这些网络在癌症中常发生失调，因此对其动力学进行建模至关重要。然而，实验数据有限和计算资源受限促使研究者采用粗粒度（coarse-graining）方法，构建系统的低维动力学描述。
- **核心问题**：经典的粗粒度建模方法依赖强假设（如时间尺度分离、拟稳态近似等），导致一个根本性问题悬而未决——**当仅有部分实验观测（即部分变量的时间序列）时，我们何时能够确信这些观测足以支持系统动力学的降阶描述？** 换言之，粗粒度模型的适用边界在哪里？
- **整体含义**：本文提出将符号回归（Symbolic Regression, SR）作为一种数据驱动的手段，用于**测试信号传导系统的动力学是否能在所测变量上粗粒度化，以及以何种紧凑程度实现粗粒度化**；在可行时，SR 还能自动推断出具有机理解释性的紧凑模型。这项工作为判断何时需要（以及何时不需要）紧凑粗粒度描述提供了新准则，也为设计新的实验测量提供了依据。

## 2. 论文提出的方法论

- **核心思想**：不再依赖先验的强假设来推导降阶模型，而是直接从时间序列数据中，通过符号回归自动搜索测量变量之间的紧凑动力学方程（速率定律）。如果存在一个简洁的数学表达式能够描述系统在所测变量上的动力学，则说明粗粒度化是可行的；如果找不到，则提示系统的简化描述不存在或需要更复杂的数学形式。
- **关键技术细节**：
  - **符号回归**：在函数空间中进行搜索，自动组合基本运算符和变量，以发现能够拟合时间序列数据的简洁解析表达式。其优势在于生成的模型是显式的、可解释的数学公式，而非黑箱。
  - **测试粗粒度化可行性**：SR 的成功与否直接作为粗粒度化是否合理的判据——若 SR 能找到低维紧凑方程，则该系统在测量变量上可以粗粒度化；若失败，则暗示其动力学在给定观测下本质上更复杂。
  - **与神经 ODE 基线的对比**：引入稀疏神经 ODE（sparse neural ODE）作为基线，通过对比其所需的输入数量来辅助解释 SR 失败的含义——若 SR 失败但稀疏神经 ODE 只需少量输入即可学习，说明存在可学习的降阶模型但 SR 搜索受限；若神经 ODE 也需要大量输入，则说明系统动力学本身确实复杂，简单数学模型本质上是不可学的。
- **算法流程（文字说明）**：给定时间序列观测数据 → 使用符号回归搜索测量变量及其导数之间的紧凑函数关系 → 评估所得表达式的拟合精度与简洁性 → 判断粗粒度化可行性 → 在可行时解读动力学机制；同时运行稀疏神经 ODE 基线以交叉验证与对照解释。

## 3. 实验设计

- **数据集/场景一：合成酶系统（synthetic enzyme systems）**
  - 测试了双步酶催化机制（经典米氏动力学推导的设定）。
  - 进一步扩展到三步机制（引入额外中间态）。
  - 考察了不同数据质量（噪声水平、时间分辨率等退化条件）下的 SR 表现。
- **数据集/场景二：已发表的 ERK 磷酸化时间序列数据**
  - 使用时间分辨的 ERK 磷酸化数据，在选定的癌症相关基因过表达背景下，利用 SR 识别紧凑的磷酸化 ERK 速率定律。
- **对比方法**：稀疏神经 ODE 基线模型（作为 SR 的对照），比较两者在相同任务下所需的输入数量（即模型所需的变量或隐藏状态维度），用于辅助判断 SR 失败时的原因归属。
- **Benchmark 性质**：该工作没有与广泛的既有粗粒度化方法库（如近似模型降阶、主方程约化等）做系统化横向对比，而是以神经 ODE 作为单一对照，重点验证 SR 作为粗粒度化可行性判据的效用。

## 4. 资源与算力

- 论文原文**未明确说明**所用的具体算力资源，包括 GPU 型号、数量、训练时长、超算环境等信息。
- 从方法性质推断，符号回归和稀疏神经 ODE 的训练通常不需要大规模分布式计算资源，属于中等计算规模的任务；但原文缺少可复现的算力明细。

## 5. 实验数量与充分性

- **实验组数**：
  - 合成酶系统：双步机制与三步扩展两个主要设定，辅以数据质量退化测试（噪声水平等）。
  - 真实数据：ERK 磷酸化数据中的一个或多个癌症相关基因过表达背景。
  - 对比实验：SR 与稀疏神经 ODE 在不同场景下的系统性对照。
- **充分性评估**：
  - **优点**：合成实验与真实数据相结合，验证了方法在已知真值（合成系统）与未知真实系统（ERK 数据）上的表现，逻辑链条较为完整；数据质量退化分析增加了对方法鲁棒性的认识。
  - **不足**：合成实验仅局限于酶动力学这一类系统，缺少对更广泛信号网络拓扑（如反馈环、多通路交汇、空间异质性等）的覆盖；真实数据验证局限于 ERK 通路和特定的基因过表达背景，外部推广性有待更多场景验证；与神经 ODE 的对比虽能辅助解释 SR 失败的原因，但没有与更丰富的降阶建模基线（如 PCA-based 动力学、流形学习 + ODE 拟合等）对比，公平性评价空间有限。

## 6. 论文的主要结论与发现

- 在合成酶系统中，SR **成功恢复了经典的米氏动力学方程**，包括在双步机制下以及在引入三步扩展后的相应速率定律——即使扩展机制下，SR 也能找到对应正确理论极限的紧凑表达式。
- 当数据质量下降（如噪声增大、观测减少）时，SR 倾向收敛到更简化的**有效动力学定律**（effective kinetic laws），但依然保持正确的理论极限，说明 SR 在数据有限时能合理退化为更粗粒度的描述。
- 在 ERK 磷酸化真实数据中，SR 在特定癌症相关基因过表达背景下识别出了**紧凑的磷酸化 ERK 速率定律**，并产生了可解释的动力学效应（揭示了不同基因过表达如何影响 ERK 磷酸化的速率行为）。
- 稀疏神经 ODE 基线在 SR 成功的场景中只需少量输入，而在 SR 失败时平均需要更多输入。这表明：**SR 失败与更复杂的系统动力学相关联**——在降阶模型根本可学习的场景中，SR 失败提示动力学复杂度超出了一般简单数学模型的表达能力。
- 总体结论：符号回归确立了作为一种**测试粗粒度描述何时成立**的方法——存在这种描述时生成可检验的假设，不存在时则激励新的实验测量。

## 7. 优点

- **方法新颖性**：将符号回归引入粗粒度建模的可行性判据层面，而非仅仅作为拟合工具——这是一个方法论上的关键跃迁。
- **可解释性**：SR 输出的显式解析表达式天然具有机理解释性，避免了黑箱模型的不可读性，有助于生物学机制假设的生成。
- **理论-数据结合**：合成系统中对照已知理论（米氏动力学）验证方法正确性，真实数据中展示应用价值，形成了"验证→应用"的完整逻辑。
- **失败模式分析**：通过神经 ODE 基线对 SR 失败进行归因分析，区分了"搜索能力不足"与"系统本身不可降阶"两种情况，体现了分析深度。
- **实用导向**：明确了何时需要粗粒度模型、何时不需要，直接指导实验设计（如增加哪些测量维度）——有较强的转化价值。

## 8. 不足与局限

- **算力信息缺失**：未报告计算资源细节（GPU 型号/数量/时长等），影响可复现性和成本评估。
- **实验覆盖有限**：
  - 合成系统仅覆盖酶动力学机制，未涉及反馈回路、多稳态、振荡等复杂信号动力学行为。
  - 真实数据仅限 ERK 通路及少数基因过表达背景，泛化性证据不足。
- **基线对比不够全面**：仅与稀疏神经 ODE 对照，缺少与经典降阶方法（如 QSSA、反应网络约化、本征正交分解等）的系统对比。
- **符号回归的固有挑战未充分讨论**：搜索的计算复杂度、对噪声的敏感性、多解性（多个等价表达式）问题，以及在高维系统上的扩展性，均未深入分析。
- **数据质量退化的测试维度有限**：主要考察了噪声影响，未系统考察时间采样稀疏性、变量缺失（不可观测变量）等更贴近实际的实验限制。
- **神经 ODE 用作"复杂度探针"的合理性值得商榷**：神经 ODE 的输入数量与系统动力学复杂度之间的关系并非严格单调对应，作为归因工具可能存在偏差风险。

（完）
