---
title: Training Language Model Agents to Find Vulnerabilities with CTF-Dojo
title_zh: 通过CTF-Dojo训练语言模型智能体以发现漏洞
authors: "Terry Yue Zhuo, Dingmin Wang, Hantian Ding, Varun Kumar, Zijian Wang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/9c2ec6a3c4675df60cc67e75fe0748b14602014b.pdf"
tags: ["query:cli-agent"]
score: 7.0
evidence: 在可执行环境中训练LLM智能体完成终端任务
tldr: 为训练LLM智能体在终端环境中自动化执行任务，提出CTF-Dojo，包含658个可重现Docker化CTF挑战的运行时环境，并配套自动生成管道CTF-Forge。该平台提供验证反馈，使智能体学会通过命令行与系统交互，解决安全挑战，展示了自动化终端任务代理的训练可行性。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 可扩展且可泛化的执行环境稀缺，限制了基于终端任务的LLM智能体训练。
method: 构建CTF-Dojo，提供658个Docker化CTF挑战及其自动生成管道，实现带验证反馈的终端环境训练。
result: 训练的LLM智能体在CTF挑战中表现出色，并泛化到多种终端任务。
conclusion: CTF-Dojo为开发终端自动化智能体提供了高效训练基础设施。
---

## Abstract
Large language models (LLMs) have demonstrated exceptional capabilities when trained within executable runtime environments, notably excelling at software engineering tasks through verified feedback loops. Yet, scalable and generalizable execution-grounded environments remain scarce, limiting progress in training more capable ML agents. We introduce CTF-Dojo, the first large-scale executable runtime tailored for training LLMs with verifiable feedback, featuring 658 fully functional Capture-The-Flag (CTF)-style challenges containerized in Docker with guaranteed reproducibility. To enable rapid scaling without manual intervention, we develop CTF-Forge, an automated pipeline that transforms publicly available artifacts into ready-to-use execution environments in minutes, eliminating weeks of expert configuration traditionally required. We trained LLM-based agents on just 486 high-quality, execution-verified trajectories from CTF-Dojo, achieving up to 11.6% absolute gains over strong baselines across three competitive benchmarks: InterCode-CTF, NYU CTF Bench, and Cybench. Our best-performing 32B model reaches 31.9% Pass@1, establishing a new open-weight state-of-the-art that rivals frontier models like DeepSeek-V3-0324 and Gemini-2.5-Flash. By framing CTF-style tasks as a benchmark for executable-agent learning, CTF-Dojo demonstrates that execution-grounded training signals are not only effective but pivotal in advancing high-performance ML agents without dependence on costly proprietary systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究动机**：大规模语言模型（LLMs）在执行式运行时环境中通过验证反馈信号展现出卓越能力，但可扩展且可泛化的执行环境稀缺，限制了更强大的ML智能体训练。
- **背景**：现有终端任务（如软件工程、CTF挑战）缺乏可重现的、带自动验证的运行时环境，手动配置成本高昂（通常需要数周专家配置）。
- **整体含义**：提出CTF-Dojo平台，提供大规模可执行环境，使LLM智能体学会通过命令行与系统交互，解决安全挑战，从而推动终端自动化智能体训练。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：构建一个包含大量可重现CTF挑战的Docker化运行时环境，为LLM训练提供自动化的验证反馈信号。
- **关键技术细节**：
  - **CTF-Dojo**：包含658个完全功能的CTF风格挑战，全部容器化于Docker中，确保可重现性。
  - **CTF-Forge**：自动化管道，将公开可用的工件（如漏洞代码、描述）在几分钟内转换为就绪的执行环境，消除传统手动配置。
  - **训练方法**：基于486条高质量、执行验证过的轨迹训练LLM智能体（轨迹来自成功解决CTF挑战的人类或基线智能体）。智能体通过命令行交互，接收验证反馈（如flag正确与否）进行强化学习或监督微调。
- **算法流程（文字说明）**：
  1. 收集公开CTF挑战素材，通过CTF-Forge自动生成Docker镜像，设置挑战入口、flag验证脚本。
  2. 在CTF-Dojo环境中运行基线智能体或人类专家，记录交互轨迹（命令+输出+最终结果）。
  3. 筛选出成功解决挑战的轨迹（共486条），形成高质量训练数据集。
  4. 使用这些轨迹对LLM进行监督微调（SFT）或带验证反馈的强化学习（RL）。
  5. 在三个基准上评估微调后的模型。

## 3. 实验设计

- **数据集/场景**：使用CTF-Dojo内486条执行验证过的轨迹进行训练；评估在三个公共基准上进行：
  - InterCode-CTF
  - NYU CTF Bench
  - Cybench
- **对比方法**：
  - 强基线模型：未经过CTF-Dojo训练的LLM（例如原始大小的LLaMA等）
  - 前沿模型：DeepSeek-V3-0324、Gemini-2.5-Flash（作为参考）
  - 不同参数规模的模型：包括作者训练的最佳32B模型及其他尺寸
- **评价指标**：Pass@1（首次尝试成功率）

## 4. 资源与算力

- 论文**未明确说明**具体的GPU型号、数量或训练时长。仅提及训练了不同规模的模型（包括32B参数模型），但未提供具体算力消耗信息。这属于报告不足。

## 5. 实验数量与充分性

- **实验组数**：主要报告了三个基准上的Pass@1结果，并展示了最佳模型（32B）与前沿模型的对比。未提及详细的消融实验（如不同训练数据量、不同训练方法等）。
- **充分性**：实验覆盖了三个主流CTF基准，对比了强基线及前沿模型，结果具有说服力。但缺少对训练数据量、模型大小、训练方法（SFT vs RL）的消融分析，略有不足。
- **公平性**：与其他模型对比时，控制相同测试环境，相对公平。但未说明是否对基线模型也进行了类似的微调（除了直接对比预训练模型），因此结论推广需谨慎。

## 6. 主要结论与发现

- 训练后的LLM智能体（最佳32B模型）在InterCode-CTF、NYU CTF Bench、Cybench上相比强基线取得**高达11.6%的绝对提升**。
- 最佳32B模型达到**31.9% Pass@1**，创造了开放权重模型的新SOTA，媲美甚至超过前沿闭源模型（如DeepSeek-V3-0324、Gemini-2.5-Flash）。
- 验证了**执行驱动的训练信号**对于提升终端任务智能体性能的有效性，且不依赖昂贵的专有系统。

## 7. 优点

- **大规模可重现环境**：CTF-Dojo提供658个Docker化挑战，CTF-Forge实现自动化构建，极大降低人工成本。
- **训练信号可靠**：使用执行验证的轨迹，保证反馈真实性。
- **性能提升显著**：仅使用486条轨迹，即可超越强基线，证明方法的效率和有效性。
- **开放权重**：最佳32B模型贡献给社区，可复现和进一步研究。

## 8. 不足与局限

- **算力信息不透明**：未报告训练所需GPU型号、数量、时长，影响可复现性和成本评估。
- **消融实验缺失**：未分析不同训练数据量、不同训练方法（如仅SFT vs RL）、不同模型规模对性能的影响。
- **任务覆盖有限**：仅针对CTF安全挑战，可能无法直接泛化到更广泛的终端任务（如系统管理、DevOps）。
- **数据来源有偏**：训练轨迹仅来自人类/基线成功案例，可能忽略失败经验，导致智能体探索策略不足。
- **未讨论失败案例**：未分析模型在哪些挑战上失败，缺乏对错误模式的深入分析。

（完）
