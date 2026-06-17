---
title: "Orion: Towards Lab Automation with Computer-Using Agents"
title_zh: 猎户座：迈向利用计算机智能体的实验室自动化
authors: "Ma, C., Trinh, L., Bucci, M., Regev, A., Wang, H."
date: 2026-06-16
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.13.732095v1.full.pdf"
tags: ["query:cli-agent"]
score: 8.0
evidence: 结合大语言模型与终端执行实现实验室自动化
tldr: "实验室发现依赖计算工作流，但受限于专用软件的人工操作。Orion是计算机使用AI代理，结合大语言模型与终端/GUI控制，实现自动化生物医学图像分析与解释。在基准测试中检索准确率超90%，自主学习CellProfiler等工具，100小时自主探索生成52份报告，22个机制假设获科学家认可。该方法扩展了实验室自动化范围，提供可扩展可审计的从数据到分析再到假设的路线。"
source: biorxiv
selection_source: fresh_fetch
motivation: 现有实验室计算工作流依赖人工操作专用软件，效率低下，需自动化。
method: Orion结合大语言模型、终端执行和GUI控制，实现自适应多步推理和计算机操作。
result: "检索任务准确率超90%，自主学会CellProfiler和QuPath，100小时生成52份报告，22个合理假设。"
conclusion: 计算机使用AI代理可显著扩展实验室自动化，提供可审计的从数据到假设的途径。
---

## 摘要
实验室发现越来越依赖于将实验数据连接到分析、解释和后续假设的计算工作流程。然而，这些工作流程仍然受限于劳动密集型的专业软件使用、通过图形用户界面的视觉检查以及跨多个来源的知识整合。在这里，我们介绍猎户座，一个用于生物医学图像分析和解释的计算机使用型AI智能体，它通过自动化实验室工作的计算层来迈向实验室自动化。猎户座将大语言模型与终端执行、GUI控制和自适应多步推理结合在一个共享的计算环境中。它可以检查视觉数据，操作标准科学软件，挖掘网络资源，并进行端到端的分析和解释工作流程，而无需定制软件集成。在基准测试中，猎户座在生物医学数据库和文献检索任务上实现了超过90%的准确率，学会了分别使用流行工具CellProfiler和QuPath进行细胞和组织图像的定量分析，并促进了实验成像数据中的自主发现。在100小时的大规模扰动成像数据集自主探索中，猎户座生成了52份研究报告，其中人类科学家审阅后优先选出了22个合理的机制假设。这些结果表明，使用计算机的AI智能体可以显著扩展实验室自动化的范围，为从实验成像数据到定量分析、报告和基于生物学的假设提供可扩展且可审计的路径。

## Abstract
Laboratory discovery increasingly depends on computational workflows that connect experimental data to analysis, interpretation and follow-up hypotheses. Yet these workflows remain constrained by labor-intensive use of specialized software, visual inspection through graphical user interfaces, and integration of knowledge across multiple sources. Here, we present Orion, a computer-using AI agent for biomedical image analysis and interpretation that moves towards lab automation by automating this computational layer of laboratory work. Orion combines large language models with terminal execution, GUI control and adaptive multi-step reasoning in a shared computing environment. It can inspect visual data, operate standard scientific software, mine web resources and conduct end-to-end analysis and interpretation workflows without requiring bespoke software integrations. Across benchmarks, Orion achieved over 90% accuracy on biomedical database and literature retrieval tasks, learned to use the popular tools CellProfiler and QuPath for quantitative analysis of cellular and tissue images, respectively, and facilitated autonomous discovery in experimental imaging data. In 100 hours of autonomous exploration of a large-scale perturbation imaging dataset, Orion generated 52 research reports, of which human scientist review prioritized 22 plausible mechanistic hypotheses. These results show that computer-using AI agents can substantially expand the reach of laboratory automation, providing a scalable and auditable route from experimental imaging data to quantitative analysis, reports and biologically grounded hypotheses.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：实验室发现越来越依赖连接实验数据、分析、解释和后续假设的计算工作流。然而，当前这些工作流受限于劳动密集型的专业软件操作（如通过 GUI 视觉检查）、多源知识的手动整合，缺乏有效自动化手段。
- **整体含义**：现有实验室自动化多集中在实验操作（如移液、样品处理）层面，而计算层（数据分析、软件使用、文献检索等）自动化程度低。Orion 旨在通过“计算机使用型 AI 智能体”（computer-using agent）弥合这一差距，将大语言模型（LLM）与终端执行、GUI 控制结合，实现端到端的计算层自动化，从而扩展实验室自动化的范围。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：将大语言模型作为“大脑”，赋予其操作计算机（终端 + GUI）的能力，使其能像人类科学家一样使用现有科学软件、浏览网页、执行分析脚本，而无需针对每个软件进行定制集成。
- **关键技术细节**：
  - **架构组件**：LLM + 终端执行 + GUI 控制 + 自适应多步推理。LLM 负责任务分解、指令生成和中间结果理解；终端执行用于运行命令行工具（如 CellProfiler、QuPath）；GUI 控制（可能通过截图分析、鼠标/键盘模拟）用于操作图形界面软件。
  - **共享计算环境**：所有组件运行在同一环境中，LLM 可以观察输出、截图、文件系统，并据此规划下一步操作。
  - **自适应多步推理**：Agent 能根据当前观察结果自动调整推理步骤，执行多步操作（如从图像分析到数据库检索再到报告生成）。
- **关键技术细节（续）**：无公式或特定算法流程描述，但整体流程可概括为：用户输入任务 → LLM 分解子任务 → 调用终端/GUI 执行 → 观察结果 → 循环迭代直到完成 → 生成最终报告或假设。

## 3. 实验设计：数据集/场景、benchmark、对比方法
- **数据集/场景**：
  1. **生物医学数据库和文献检索任务**：基准测试，评估检索准确率。
  2. **定量分析工具学习**：使用 CellProfiler（细胞图像）和 QuPath（组织图像）进行定量分析，测试能自主学会操作这些流行软件。
  3. **大规模扰动成像数据集自主探索**：100 小时连续运行，对一个大规模扰动成像数据集（未具体说明数据集名称，可能来自实验室内部或公开数据集）进行完全自主的探索、分析和假设生成。
- **Benchmark**：检索任务上准确率 >90% 作为衡量标准。无明确公开基准数据集名称，但属于生物医学数据库与文献检索。
- **对比方法**：文中未提及与现有其他 AI agent 或自动化系统的直接对比。主要展示 Orion 自身的能力表现，属于概念验证性工作。

## 4. 资源与算力
- **未明确说明**：论文在摘要和元数据中未提及具体的 GPU 型号、数量、训练时长、推理成本等算力信息。仅提到“100 小时自主探索”，但未说明硬件配置。可能因本文是 bioRxiv 预印本，侧重方法概念，未详细披露计算资源。需要指出这一点。

## 5. 实验数量与充分性
- **实验组数**：
  - 检索任务基准测试（1 组，准确率>90%）。
  - 工具学习实验（2 个工具：CellProfiler 和 QuPath）。
  - 大规模自主探索：100 小时连续运行，生成 52 份研究报告，其中 22 个合理假设获科学家认可。
- **充分性与公平性**：
  - **优点**：66生成 52 份报告并经过人类专家评审，体现了实际应用价值；自主探索时间长，覆盖较多场景。
  - **不足**：缺乏与现有自动化系统（如基于工作流引擎的）的直接定量对比；未进行消融实验（如去掉 GUI 控制或知识检索的效果）；检索任务基准的具体构成（数据集大小、难度）未说明，是否具有代表性存疑；仅在一个成像数据集上进行了大规模探索，泛化性未验证。因此实验设计偏展示性，充分性和公平性有待加强。

## 6. 论文的主要结论与发现
- Orion 能通过结合 LLM 和计算机操作能力，在无需定制集成的情况下，自主学会使用标准科学软件（CellProfiler、QuPath）进行定量分析。
- 在生物医学数据库和文献检索任务上，准确率超过 90%，表明其信息检索能力可靠。
- 在 100 小时自主探索中，生成了 52 份研究报告，其中 22 个机制假设被人类科学家优先选中，证明其能够从原始成像数据产生生物学上有意义的假设。
- 结论：计算机使用型 AI 智能体可以显著扩展实验室自动化的覆盖范围，为从实验成像数据到定量分析、报告和假设生成提供可扩展且可审计的路径。

## 7. 优点：方法或实验设计上的亮点
- **通用性**：无需对每种科学软件进行定制接口，通过终端和 GUI 控制即可操作，大幅降低部署成本。
- **端到端自动化**：从原始数据到报告和假设的全流程自动化，减少人工干预。
- **自适应推理**：核心是 LLM 的多步推理能力，能应对开放式的科学探索任务。
- **规模化验证**：100 小时连续运行生成 52 份报告，并由人类科学家评审，展示了实际可用性。
- **可审计性**：所有操作可记录，便于追溯和验证。

## 8. 不足与局限
- **实验覆盖有限**：仅在一个成像数据集上进行了大规模探索，未在其他领域（如基因组学、质谱分析）测试，泛化性未知。
- **缺乏基准对比**：未与现有自动化系统或人工操作进行定量效率/准确性对比，说服力不足。
- **未披露算力需求**：无法评估资源消耗和实际部署可行性。
- **假设可靠性不确定**：22 个合理假设仅经人类科学家优先选，但未经过 wet-lab 验证，可能包含假阳性。
- **依赖 LLM 能力**：当前 LLM 存在幻觉、长任务稳定性等问题，可能影响长时自主探索的质量。论文未讨论错误率和恢复机制。
- **安全与治理**：给 AI 代理直接操作计算机的权限可能带来安全风险（如误删除文件、访问敏感数据），论文未讨论安全措施。

（完）
