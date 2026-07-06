---
title: Noise-Resilient Symbolic Regression with Dynamic Gating Reinforcement Learning
title_zh: 基于动态门控强化学习的噪声鲁棒符号回归
authors: "Chenglu Sun, Shuo Shen, Wenzhi Tao, Deyi Xue, Zixia Zhou"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/34280/36435"
tags: ["query:sr"]
score: 10.0
evidence: 使用动态门控强化学习的噪声鲁棒符号回归
tldr: 针对现有符号回归方法在高噪声数据下性能下降的问题，提出噪声鲁棒符号回归方法NRSR，结合强化学习与噪声鲁棒门控模块动态过滤噪声，学习符号选择策略。实验表明，NRSR在多种噪声水平下均能准确恢复符号表达式，优于现有方法，推动了符号回归在噪声环境下的应用。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
motivation: 现有符号回归方法在高噪声数据上表现不佳。
method: 提出强化学习框架配合噪声鲁棒门控模块动态过滤噪声。
result: 在高噪声数据上成功恢复符号表达式，优于基线。
conclusion: NRSR提升了符号回归在噪声环境下的鲁棒性。
---

## Abstract
Symbolic regression (SR) has emerged as a pivotal technique for uncovering the intrinsic information within data and enhancing the interpretability of AI models. However, current state-of-the-art (sota) SR methods struggle to perform correct recovery of symbolic expressions from high-noise data. To address this issue, we introduce a novel noise-resilient SR (NRSR) method capable of recovering expressions from high-noise data. Our method leverages a novel reinforcement learning (RL) approach in conjunction with a designed noise-resilient gating module (NGM) to learn symbolic selection policies. The gating module can dynamically filter the meaningless information from high-noise data, thereby demonstrating a high noise-resilient capability for the SR process. And we also design a mixed path entropy (MPE) bonus term in the RL process to increase the exploration capabilities of the policy. Experimental results demonstrate that our method significantly outperforms several popular baselines on benchmarks with high-noise data. Furthermore, our method also can achieve sota performance on benchmarks with clean data, showcasing its robustness and efficacy in SR tasks.

---

## 论文详细总结（自动生成）

# 中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有符号回归（Symbolic Regression, SR）方法在含有高噪声（即无关输入变量）的数据上表现严重下降，无法准确恢复真实的符号表达式。现实世界的数据往往包含大量噪声变量，而大部分SR基准测试使用干净数据，导致算法在真实场景中应用困难。
- **整体含义**：论文旨在提出一种噪声鲁棒的符号回归方法，使其能在高噪声数据中有效筛选出有意义的变量，恢复正确的数学表达式，同时保持干净数据上的竞争力，从而提升SR在工业与科学发现中的实用性和鲁棒性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：结合强化学习（RL）与一个噪声鲁棒门控模块（Noise-Resilient Gating Module, NGM），以及一种混合路径熵正则化（Mixed Path Entropy, MPE）来提升策略探索能力，实现从高噪声数据中动态筛选有效输入变量并生成符号表达式。
- **关键技术细节**：
  1. **噪声鲁棒门控模块（NGM）**：
     - 使用一个二进制门控层 \( G \in \{0,1\}^{m \times n} \) 对输入变量进行逐元素乘操作（Hadamard积），得到筛选后的输入 \( X' = X \odot G \)。
     - 训练目标是最小化均方误差（MSE）加上 \( L_0 \) 正则化项（控制非零门数量），即 \( J(W,G) = \min_{W,G} \frac{1}{m}\sum (y_i - W X'_i)^2 + \lambda \|G\|_0 \)。
     - 由于 \( L_0 \) 不可微，使用 Louizos 等人的近似方法实现梯度优化。
  2. **门控与动作掩码（Action Mask）集成**：
     - 将训练好的门控层 \( G \) 与原有动作掩码（防止无效符号序列）通过逐元素乘结合为新掩码 \( A_{\text{new}} = A_{\text{original}} \odot G \)，从而在RL采样阶段只允许被选择的变量出现，缩小搜索空间。
  3. **表达式生成与策略优化**：
     - 使用RNN作为策略网络 \( \pi_\theta \)，通过预序遍历生成表达式树，每一步从符号库中采样token。
     - 奖励函数定义为 \( R(\tau) = 1 / (1 + \text{NRMSE}) \)，其中NRMSE为归一化均方根误差。
     - 采用近端策略优化（PPO）进行策略训练，并使用经验 \( (1-\eta) \) 分位数作为基线，仅用top样本更新。
  4. **混合路径熵（MPE）正则化**：
     - 单步熵 \( H(\pi_\theta) \)：对每个时间步的熵进行指数衰减加权，鼓励早期动作多样性。
     - 路径熵 \( H_\tau(\pi_\theta) \)：对整个序列的联合概率熵，促进探索完全不同的表达式路径。
     - 最终目标函数：\( L(\theta) = L_p(\theta) + \alpha H_\tau(\pi_\theta) + \beta H(\pi_\theta) \)。

- **算法流程**（文字说明）：
  1. 使用训练集训练NGM，获得门控层 \( G \)。
  2. 将 \( G \) 集成到动作掩码中。
  3. 初始化RL策略（RNN），循环迭代：
     - 策略依次采样token生成表达式轨迹。
     - 计算每条轨迹的奖励 \( R(\tau) \)。
     - 使用PPO更新策略参数，同时加入MPE正则化。
     - 每轮评估最优表达式，直到找到完美表达式或达到最大表达式生成数量。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：
  - 使用 **Nguyen SR基准套件**（12个代表性表达式），每个基准包含真实表达式、算子库（+、-、×、÷、sin、cos、log、exp、x_i）和输入变量范围。
  - 生成数据划分为三部分：20000个样本用于NGM训练，20个样本用于计算RL奖励，20个样本用于评估。
  - 噪声设置：向原始输入变量中分别添加 **5个**、**10个**、**20个** 无关噪声变量（即无关输入），构造高噪声数据场景。
  - 此外也使用干净数据（无噪声）进行实验。

- **对比方法**（5个baseline）：
  1. **DSR**（Petersen et al. 2021）：基于RNN+风险寻求策略梯度的RL方法。
  2. **HESL**（Landajuela et al. 2021b）：在DSR基础上加入层次熵正则化和软长度先验。
  3. **GP-Meld**（Landajuela et al. 2022）：结合遗传编程和DSR的混合方法。
  4. **DGSR**（Holt et al. 2023）：基于预训练深度生成模型的符号回归。
  5. **Eureqa**（White 2012）：商业GP软件。

- **评价指标**：
  - **Recovery Rate (RR)**：在所有重复实验中成功恢复完美表达式（NRMSE=0）的比例。
  - **Explored Expression Number (EEN)**：平均每个任务生成的表达式数量（越低效率越高）。
  - **Normalized Mean-Square Error (NMSE)**：最佳表达式与真实表达式之间的拟合误差。
  - 另外，消融实验中引入 **Effective Exploration Ratio (EER)** = 唯一表达式数量/总表达式数量，衡量探索效率。

## 4. 资源与算力

- **文中未明确说明使用的GPU型号、数量或具体训练时长**。仅提及所有实验在统一的SR框架（Landajuela et al. 2022）中实现，Eureqa通过DataRobot API运行。因此无法判断算力需求细节。

## 5. 实验数量与充分性

- **实验数量**：
  - 高噪声数据对比：分别在5噪声和10噪声下测试所有方法，每种噪声水平下对12个基准进行100次重复实验（不同随机种子），共2×12×100=2400次实验。
  - 干净数据对比：12个基准，100次重复，共1200次实验。
  - 消融实验：使用10噪声数据在12个基准上重复100次，评估NGM、MPE、PPO的贡献；在干净数据上也进行类似消融。
  - NGM分析：使用93个表达式（补充文件），测试不同噪声数量（3、5、10、20）及不同门控训练参数（Otsu阈值、L0损失系数）下的过滤准确率。
  - MPE分析：在Nguyen-5上计算EER；在Nguyen-7上调整β参数看RR/EEN变化；在Nguyen-12上展示训练过程中的总熵曲线（10次独立实验）。

- **充分性与公平性**：
  - 实验覆盖了不同噪声水平、不同基准、不同基线方法，消融实验考察了核心模块的重要性。
  - 所有方法在同一框架下实现（除Eureqa使用API），避免了实现差异。
  - 重复100次取平均，结果具有统计学意义。
  - 不足：未在真实世界噪声数据集上验证（仅合成噪声），也未与其他专门处理噪声的SR方法（如鲁棒GP）对比，可能影响泛化性论证。

## 6. 论文的主要结论与发现

- **高噪声数据**：NRSR在5噪声和10噪声场景下，平均RR分别达到89.1%和89.1%，远超其他基线（次优DGSR为72.5%和68.5%），EEN最低（425K和423K），NMSE最低（7.73e-3和8.52e-3）。说明NRSR具有显著的噪声鲁棒性。
- **干净数据**：NRSR平均RR为89.7%，EEN为408K，优于所有基线（次优HESL：RR 88.3%，EEN 441K），证明其在干净数据上同样达到SOTA。
- **消融实验**：NGM对于高噪声场景至关重要（移除后RR从89.1%降至32.9%）；MPE和PPO能进一步提升性能（移除后RR下降）。
- **门控模块可靠性**：在不超过10个噪声变量时，门控层过滤准确率高达98.92%；即使20个噪声仍达96.77%。使用平均门控层（跨所有epoch）配合Otsu阈值效果优于仅使用最终epoch的门控。
- **MPE效果**：在Nguyen-5上NRSR的EER（0.713）最高，表明探索更高效；β过大可能导致探索成本上升。

## 7. 优点：方法或实验设计上的亮点

- **方法创新性**：
  - 首次将 \( L_0 \) 正则化的门控与RL动作掩码结合，动态过滤噪声输入，显著缩小搜索空间。
  - 提出混合路径熵（MPE），在单步熵基础上增加整个序列的路径熵，避免策略过早收敛到局部最优，促进探索完全不同的表达式。
  - 门控模块和MPE可作为即插即用组件，适用于其他SR框架，扩展性强。
- **实验设计**：
  - 使用统一框架比较，控制变量公平。
  - 消融系统全面，不仅分析整体模块贡献，还深入研究了NGM的参数敏感性（Otsu阈值、λ）和MPE的β影响。
  - 在SR领域首次系统地评估高噪声（多达20个噪声变量）下的方法性能，具有重要现实意义。

## 8. 不足与局限

- **噪声类型单一**：论文定义的“噪声”仅为无关输入变量（即特征噪声），未考虑输出标签中的观测噪声（如高斯噪声、异方差噪声）。实际数据通常包含多种噪声类型，方法对标签噪声的鲁棒性未知。
- **数据规模限制**：训练NGM使用了20000个样本，而在RL阶段仅用20个样本计算奖励，可能对小样本场景的泛化性不足。
- **基准范围较小**：仅使用了12个Nguyen基准表达式，且这些表达式相对简单（通常为低阶多项式、三角函数等组合）。对于高维、复杂函数（如分形、分段函数）的表现未测试。
- **计算资源未披露**：缺少对训练时间、GPU型号/数量的详细描述，其他研究者难以复现或对比效率。
- **未与近期其他噪声鲁棒SR方法对比**：例如基于贝叶斯推断或dropout的GP方法，仅对比了通用SR基线。
- **门控训练依赖数据量**：\( L_0 \) 正则化训练需要足够数据才能准确识别噪声变量，在极端小样本或高度相关变量场景下可能失效。
- **MPE的超参数敏感性**：实验表明β存在最优区间（0.02~0.04），过大过小均导致性能下降，实际应用中需调参，增加使用门槛。

（完）
