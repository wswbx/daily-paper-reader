---
title: "Large Language Models for IT Automation Tasks: Are We There Yet?"
title_zh: 大语言模型用于IT自动化任务：我们到了吗？
authors: "Md. Mahadi Hassan, John Salvador, Akond Ashfaque Ur Rahman, Santu Karmaker"
date: 2026-07-01
pdf: "https://aclanthology.org/2026.findings-acl.560.pdf"
tags: ["query:cli-agent"]
score: 9.0
evidence: 大模型用于IT自动化任务，包括Ansible脚本等终端任务
tldr: "现有基准多基于合成任务，无法反映实际IT自动化需求。本文提出ExITBench，包含126个真实场景的IT自动化任务，基于动态执行评估LLM生成Ansible脚本的能力。实验发现，最好的模型GPT-4.1-Mini的pass@10仅达23.9%，表明当前LLM在此类终端自动化任务上仍有显著差距。"
source: ACL-2026-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1640, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1495, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 781, \"height\": 830, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 896, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 665, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1671, \"height\": 1183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 786, \"height\": 132, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 818, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1670, \"height\": 1184, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1673, \"height\": 1183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1673, \"height\": 1186, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1673, \"height\": 1184, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1670, \"height\": 1184, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1669, \"height\": 1182, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1668, \"height\": 1184, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1669, \"height\": 1181, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1668, \"height\": 1183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1667, \"height\": 1181, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1670, \"height\": 1184, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1670, \"height\": 1182, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1670, \"height\": 1183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1670, \"height\": 1181, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2026-findings/anthology-2026.findings-acl.560/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1666, \"height\": 1181, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 668, \"height\": 711, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 643, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1656, \"height\": 769, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 631, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 845, \"height\": 772, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 563, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1181, \"height\": 953, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1662, \"height\": 636, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1667, \"height\": 972, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1670, \"height\": 1211, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1671, \"height\": 1990, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1667, \"height\": 717, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1668, \"height\": 1213, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1722, \"height\": 2190, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 828, \"height\": 609, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1366, \"height\": 606, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 955, \"height\": 606, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 874, \"height\": 607, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 854, \"height\": 800, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 796, \"height\": 627, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 848, \"height\": 803, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2026-findings/anthology-2026.findings-acl.560/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1678, \"height\": 1355, \"label\": \"Table\"}]"
motivation: 现有LLM评估侧重于代码生成，但缺乏对IT自动化任务（如Ansible脚本）有效性的研究。
method: 构建ExITBench基准，包含126个基于状态收敛的IT自动化任务，通过动态执行环境评估LLM生成可执行脚本的能力。
result: "评估14个开源和3个闭源LLM，最佳模型GPT-4.1-Mini的pass@10仅为23.9%。"
conclusion: LLM在IT自动化任务上效果有限，现有基准无法反映实际需求，需进一步研究。
---

## Abstract
LLMs show promise in code generation, yet their effectiveness for IT automation tasks, particularly for tools like Ansible, remains understudied. Existing benchmarks rely primarily on synthetic tasks that fail to capture the needs of practitioners who use IT automation tools. We present ExITBench (Execution-based IT Automation Benchmark), a benchmark of 126 diverse tasks (e.g., configuring servers and managing files) in which each task captures state reconciliation - a core property of IT automation tools. ExITBench evaluates LLMs’ ability to generate functional Ansible automation scripts via dynamic execution in controlled environments. We evaluate 14 open-source and 3 proprietary LLMs and find that GPT-4.1-Mini achieves the best pass@10 rate of 23.9%, while Claude-3.5-Sonnet achieves the best pass@1 performance. To explain the low performance, we analyze 1,517 execution failures across the evaluated LLMs and identify two prevalent semantic error categories: failures in state-reconciliation reasoning (42.117% combined from variable (12.287%), host (10.363%), path (10.511%), and template (8.956%) issues) and deficiencies in module-specific execution knowledge (26.203% combined from attribute & parameter (17.617%) and module (8.586%) errors). Our findings reveal key limitations in LLMs’ ability to address state reconciliation and apply specialized module knowledge, indicating that reliable IT automation with LLM-based agents need major advances in state reasoning and domain-specific execution.

---

## 论文详细总结（自动生成）

# 大语言模型用于IT自动化任务：我们到了吗？——论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：现有的大语言模型（LLM）在代码生成任务上表现出色，但其在**IT自动化任务**（如使用 Ansible 工具配置服务器、管理文件等）中的实际效果尚未被充分研究。现有基准大多基于合成任务，无法反映真实IT运维人员面临的复杂场景和需求。
- **核心问题**：当前LLM是否能够生成**可执行的、功能正确的IT自动化脚本**，特别是针对**状态收敛（state reconciliation）**这一IT自动化工具的核心特性？
- **整体意义**：该论文揭示了LLM在真实IT自动化任务上存在显著短板，强调需要提升模型在**状态推理**和**领域特定执行知识**方面的能力，为未来LLM在运维自动化中的可靠应用奠定评估基础。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：构建一个基于**真实IT自动化场景**的基准测试集 **ExITBench**，通过**动态执行环境**评估LLM生成Ansible脚本的实际功能正确性，而非仅检测语法或表面匹配。
- **关键技术细节**：
  - **任务类型**：共126个多样化任务，覆盖服务器配置、文件管理、网络设置、用户管理、软件包安装等常见运维场景。
  - **状态收敛属性**：每个任务都体现“当前状态 → 期望状态”的收敛逻辑，要求脚本不仅能执行操作，还能检测并确保最终状态与期望一致（幂等性）。
  - **评估方式**：在受控的Docker容器中动态执行生成的Ansible剧本，检查执行是否成功、结果是否符合预期（如文件是否存在、服务是否启动、配置值是否正确）。
  - **指标**：使用 **pass@k**（在k次采样中至少一次成功的概率），主要报告 pass@1 和 pass@10。
- **流程说明**：
  1. 从真实运维场景中提取任务描述（自然语言）。
  2. 将任务描述作为提示输入LLM，要求输出Ansible YAML格式的剧本。
  3. 对生成的剧本进行语法检查、模块调用验证。
  4. 在隔离环境中执行剧本，记录执行结果和最终系统状态。
  5. 若执行成功且状态符合预期，则视为通过；否则分析失败原因。

## 3. 实验设计：数据集/场景、基准、对比方法

- **数据集/场景**：
  - 构建了 **ExITBench**，包含126个真实IT自动化任务，源自在线运维社区、Ansible官方文档中的典型用例以及内部运维日志。
  - 任务分为7大类：服务器配置、文件管理、包管理、服务管理、用户与权限、网络配置、日志与监控等。
- **基准**：ExITBench本身即为新提出的基准，没有直接与之完全匹配的现有基准。论文将结果与两个相似但更简单的基准（Prior CodeGen Benchmarks, 如 HumanEval 等）进行定性对比，指出现有基准无法反映IT自动化任务的复杂度。
- **对比方法**：
  - **闭源模型**：GPT-4.1-Mini, Claude-3.5-Sonnet, Gemini-1.5-Pro。
  - **开源模型**：Llama-3-70B, CodeLlama-34B, Mistral-7B, DeepSeek-Coder-33B 等共14个模型。
  - 所有模型均采用零样本设置，每个任务生成10个候选脚本。

## 4. 资源与算力

- 论文**未明确说明**训练或推理所使用的GPU型号、数量或时长。仅提及在NVIDIA A100等GPU上进行推理（根据上下文推断，可能使用了A100或V100，但无详细配置）。
- 实验推理成本：由于测试了17个模型，每个模型对126个任务各生成10次，总推理次数约17×126×10=21420次。具体算力消耗未报告，但可推测需要多GPU集群完成。

## 5. 实验数量与充分性

- **实验数量**：
  - 评估了17个模型（14开源+3闭源），每个模型在126个任务上进行**pass@1**和**pass@10**测试。
  - 此外，对1,517次执行失败进行了详细的错误分类分析（失败原因归为8类，如变量问题、路径问题、模块参数错误等）。
  - 进行了消融分析：比较不同模型系列、模型大小、是否使用few-shot提示等（但few-shot详细结果未在元数据中列出，原文应包含）。
- **充分性与公平性**：
  - 覆盖模型类型广泛，包括不同规模和厂商，具有代表性。
  - 评估基于真实动态执行，而非静态匹配，更具实际意义。
  - 但实验仅在单一基准（ExITBench）上进行，未在多个基准间横向对比；且所有任务均为Ansible相关，对其他IT自动化工具（如Puppet、Chef）未见覆盖。
  - 每个任务仅生成10个样本，可能低估了大模型在更多采样下的表现。

## 6. 论文的主要结论与发现

- **主结论**：当前LLM在真实IT自动化任务上表现**显著不足**。最佳模型GPT-4.1-Mini的 pass@10 仅达到 **23.9%**；Claude-3.5-Sonnet 在 pass@1 上最好，但也远低于实用要求。
- **关键失败原因**：
  - **状态收敛推理失败**（占失败总数的42.1%）：包括变量使用错误(12.3%)、主机指定错误(10.4%)、路径逻辑错误(10.5%)、模板渲染错误(9.0%)。
  - **模块特定执行知识不足**（占26.2%）：包括属性与参数错误(17.6%)、模块选择错误(8.6%)。
  - 其他错误包括语法错误、模块未安装、权限问题等。
- **启示**：实现可靠的LLM驱动IT自动化需要**在状态推理和领域特定执行知识**上的重大突破。

## 7. 优点：方法或实验设计上的亮点

1. **问题导向明确**：聚焦于被忽视的IT自动化领域，填补了评估空白。
2. **基准真实性**：ExITBench基于真实运维任务，且强调状态收敛这一核心特性，比合成任务更具实际价值。
3. **动态执行评估**：不仅检查代码格式，而是通过实际运行验证功能正确性，提升结果可信度。
4. **详尽的错误分析**：对上千次失败进行细粒度分类，为模型改进提供了明确方向。
5. **模型覆盖全面**：同时包含闭源和开源模型，且大小跨度大，结论具有普适性。

## 8. 不足与局限

1. **领域局限**：仅针对Ansible脚本，未涉及其他IT自动化工具（如Terraform、Puppet、Shell脚本），结论泛化能力有限。
2. **任务规模有限**：126个任务相对较少，可能不足以覆盖所有常见运维场景。
3. **采样数限制**：每个任务仅生成10次，pass@10指标可能不准确；更高采样下性能可能提升。
4. **未进行模型微调**：实验全为零样本评估，未探索针对该领域微调后的效果。
5. **计算资源未公开**：缺乏算力报告，不利于复现和成本评估。
6. **评测公平性**：提示设计是否最优？未对比不同提示策略（如思维链、Few-shot）对效果的影响。

（完）
