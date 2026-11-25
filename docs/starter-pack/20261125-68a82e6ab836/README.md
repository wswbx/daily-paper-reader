<div class="dpr-topic-result-actions"><button type="button" data-topic-copy="docs/starter-pack/20261125-68a82e6ab836/papers.md">复制论文清单</button> <a href="docs/starter-pack/20261125-68a82e6ab836/papers.md" download data-no-router>下载 Markdown</a> <a href="docs/starter-pack/20261125-68a82e6ab836/papers.json" download data-no-router>下载 JSON</a> <button type="button" data-topic-continue="20261125-68a82e6ab836">继续生成阅读内容</button></div>

# user-sim · 入门导读

> 本导读基于所列论文的标题、摘要和已有速览，不代表已阅读全部全文。近期窗口不是完整领域史；检索不保证覆盖全部相关论文。模型导读需结合原文核验。

检索窗口：arXiv &#91;2025-11-25, 2026-11-25&#41;；会议 &#91;2024-11-25, 2026-11-25&#41;（UTC，结束日不含）

## 方向概览

本导读聚焦近期检索窗口内关于用户模拟器（user simulator）的研究，核心问题是：如何构建和评估能够替代真实用户、用于训练与测试交互式对话系统及智能体的模拟用户。覆盖的子方向包括：模拟器的构建方法（提示工程、监督微调、强化学习、对抗训练、人格/状态建模）、模拟器质量与保真度评估（与真实用户行为分布和判断的一致性、下游效用）、以及将模拟器应用于对话系统、推荐系统、搜索和智能体基准的评测实践。现有证据显示，模拟器普遍存在过度合作、行为同质、目标偏离等“Sim2Real”差距，且评估指标本身可能无法可靠检测这些失败；同时，基于真实数据微调和显式状态建模的方法在保真度和下游效用上表现更好。本导读仅依据输入论文的标题与摘要，不补写外部文献或实验数字；部分方向（如语音模拟、多模态模拟）证据较少，已明确说明。

依据：[A Survey on LLM-based Conversational User Simulation](/20251125-20261124/2604.24977v1)；[On Evaluating User Simulators for Interactive Agents](/20251125-20261124/2611.24892v1)；[SimulatorArena: Are User Simulators Reliable Proxies for Multi-Turn Evaluation of AI Assistants?](/conference/emnlp-2025/anthology-2025emnlp-main1786-simulatorarena-are-user-simulators-reliable-proxies-for-multi-turn-evaluation-of-ai-assistants)；[Quantifying the Utility of User Simulators for Building Collaborative LLM Assistants](/20251125-20261124/2605.09808v1)；[Mind the Sim2Real Gap in User Simulation for Agentic Tasks](/20251125-20261124/2603.11245v2)；[Measuring and Mitigating the Distributional Gap Between Real and Simulated User Behaviors](/20251125-20261124/2605.07847v1)

## 子方向一：用户模拟器的构建方法与架构

该子方向关注如何生成模拟用户行为，方法谱系包括：基于提示的角色扮演、在真实人机对话上监督微调、多轮强化学习（含多奖励、分层奖励、GRPO 等）、对抗式训练（生成器-判别器、意图保持的对抗规划）、以及显式建模用户内部状态（认知/情感状态、BDI/E、知识状态图、人格向量）。代表性工作如 MIMESIS 强调用真实对话和显式推理监督训练专用模拟器；TRACER 和 UserLM-2.0 通过多轮强化学习对齐行为轨迹与任务意图；UserIDA 将每轮交互意图与语言表达解耦；CUE 和 RealUserSim 用真实会话导出人格/行为表示来条件化模拟器；HumanLM 和 Mind2Dialogue 引入潜在心理状态作为监督信号。另有工作探索多智能体分解（状态跟踪、消息属性生成）和自动提示/工作流优化。总体趋势是从表面模仿转向状态对齐和行为可控，但各方法的训练数据、奖励设计和适用场景差异较大，摘要中未提供统一的架构分类标准。

依据：[MIMESIS: Learning User Simulators as Training Environments for Interactive Agents](/20251125-20261124/2610.09484v2)；[Beyond Surface Style: Aligning Multi-Turn User Simulators with Behavioral Consistency](/20251125-20261124/2609.28690v1)；[Towards User Simulators That Stay On Task And Still Sound Natural](/20251125-20261124/2610.31512v1)；[Intent Speaks Louder: Controllable User Simulation Beyond Response Imitation](/20251125-20261124/2608.09420v1)；[CUEing User Simulators: Calibrated User Embeddings for Multi-Turn Benchmarking](/20251125-20261124/2610.02460v1)；[RealUserSim: Bridging the Reality Gap in Agent Benchmarking via Grounded User Simulation](/20251125-20261124/2605.20204v1)；[HumanLM: Simulating Users with State Alignment Beats Response Imitation](/20251125-20261124/2603.03303v1)；[Mind2Dialogue: Training Human-Aware Language Models by Simulating User Mental States](/20251125-20261124/2609.15972v1)；[Training User Simulators with Latent Intrinsic Feedback](/20251125-20261124/2610.13617v1)；[AgentPersonaBench: Benchmarking Persona-Driven User Simulation](/20251125-20261124/2610.04379v1)；[Agentic Persona Control and Task State Tracking for Realistic User Simulation in Interactive Scenarios](/20251125-20261124/2601.15290v1)；[Beyond Cooperative Simulators: Generating Realistic User Personas for Robust Evaluation of LLM Agents](/20251125-20261124/2605.12894v1)；[UserLM-R1: Modeling Human Reasoning in User Language Models with Multi-Reward Reinforcement Learning](/20251125-20261124/2601.09215v1)；[A Survey on LLM-based Conversational User Simulation](/20251125-20261124/2604.24977v1)

## 子方向二：模拟器质量与保真度评估

该子方向研究如何判断模拟器是否可信。评估维度包括：与真实用户消息的相似度、人格/行为一致性、群体层面行为分布对齐、轨迹级目标保持、以及模拟器作为评估工具的下游效用（即用其训练或评测的智能体在真实用户上的表现）。多项工作指出现有模拟器存在系统性偏差：过度合作、缺乏挫败感与歧义、风格同质化，导致智能体成功率被高估（“easy mode”）。On Evaluating User Simulators 通过扰动注入发现已有评估指标只能检测部分失败；SimulatorArena 和 RealUserSim 等提出以真实会话为基准的保真度评测；Measuring and Mitigating the Distributional Gap 系统比较了 24 个模拟器的行为分布差异。也有工作从模型激活层面分析“助手偏差”，或提出无外部参照的人格一致性诊断。需注意：这些评估框架的覆盖范围、指标定义和人类研究规模各不相同，摘要中未给出统一的基准结论。

依据：[On Evaluating User Simulators for Interactive Agents](/20251125-20261124/2611.24892v1)；[SimulatorArena: Are User Simulators Reliable Proxies for Multi-Turn Evaluation of AI Assistants?](/conference/emnlp-2025/anthology-2025emnlp-main1786-simulatorarena-are-user-simulators-reliable-proxies-for-multi-turn-evaluation-of-ai-assistants)；[Quantifying the Utility of User Simulators for Building Collaborative LLM Assistants](/20251125-20261124/2605.09808v1)；[Mind the Sim2Real Gap in User Simulation for Agentic Tasks](/20251125-20261124/2603.11245v2)；[Measuring and Mitigating the Distributional Gap Between Real and Simulated User Behaviors](/20251125-20261124/2605.07847v1)；[Synthetic Users, Real Differences: an Evaluation Framework for User Simulation in Multi-Turn Conversations](/20251125-20261124/2605.02624v1)；[UserProxyBench: Evaluating LLM User Simulators for Agent Benchmarks and Training](/20251125-20261124/2609.38043v1)；[MirrorBench: A Benchmark to Evaluate Conversational User-Proxy Agents for Human-Likeness](/20251125-20261124/2601.08118v3)；[Investigating Assistant Bias in LLM User Simulators Using a Role Vector](/20251125-20261124/2609.00608v1)；[Evaluating Persona Consistency in LLM User Simulators Without External Reference Annotations](/20251125-20261124/2611.30280v1)；[Is He Extroverted? Identifying Missing Relevant Personas for Faithful User Simulation](/20251125-20261124/2602.15832v2)；[A Survey on LLM-based Conversational User Simulation](/20251125-20261124/2604.24977v1)

## 子方向三：面向对话系统与智能体基准的模拟器应用

该子方向将用户模拟器作为可扩展的评测环境，应用于任务型对话、对话推荐、对话搜索、编码智能体、语音智能体和主动式助手等场景。典型模式是：模拟器按人格或任务目标与待测系统多轮交互，再通过规则校验、LLM 评判或数据库状态比对给出评分。τ-bench 系列工作将模拟用户与工具调用智能体结合；UserSimCRS v2 和 ConvApparel 面向对话推荐提供模拟与验证工具；AutoSim 面向对话搜索，强调用真实用户信号微调模拟器权重以匹配 NIST 排序；SpokenUS 和 τ-Voice 将模拟扩展到语音交互；SWE-WhatIf 和 SWE-Together 用记录的真实编码会话驱动可适应新智能体轨迹的模拟用户。应用研究普遍报告：模拟器越接近真实用户，评测结论越可能改变部署决策；但不同基准的任务域、评分协议和模拟器配置差异很大，跨基准可比性有限。

依据：[&#123;&#36;&#92;tau&#36;&#125;-bench: A Benchmark for &#92;underline&#123;T&#125;ool-&#92;underline&#123;A&#125;gent-&#92;underline&#123;U&#125;ser Interaction in Real-World Domains](/conference/iclr-2025/openreview-iclr-2025-ronsxzpudn-tau-bench-a-benchmark-for-underlinetool-underlineagent-underlineuser-interaction-in-real-world-domains)；[UserSimCRS v2: Simulation-Based Evaluation for Conversational Recommender Systems](/20251125-20261124/2512.04588v3)；[ConvApparel: A Benchmark Dataset and Validation Framework for User Simulators in Conversational Recommenders](/20251125-20261124/2602.16938v1)；[AutoSim: A Self-Improving User Simulator for Conversational Search Evaluation](/20251125-20261124/2610.28054v1)；[SpokenUS: A Spoken User Simulator for Task-Oriented Dialogue](/20251125-20261124/2603.16783v2)；[&#36;τ&#36;-Voice: Benchmarking Full-Duplex Voice Agents on Real-World Domains](/20251125-20261124/2603.13686v1)；[SWE-WhatIf: Simulating Real Users of Coding Agents from Recorded Session](/20251125-20261124/2611.21095v1)；[SWE-Together: Evaluating Coding Agents in Interactive User Sessions](/20251125-20261124/2606.29957v1)；[Enjoy Your Talk: A Human-Centered Benchmark for Multi-Turn Dialogue with Decoupled User Simulation, Target Modeling, and Judging](/20251125-20261124/2607.10428v2)；[PersonaForge: Realistic Multi-Turn User Simulation for Agentic Systems](/20251125-20261124/2608.28378v1)；[Proactive Agent Research Environment: Simulating Active Users to Evaluate Proactive Assistants](/20251125-20261124/2604.00842v1)；[TurnFlow: Benchmarking User-State Reasoning in Multi-Turn LLM Agents via Scene-Guided User Simulation](/20251125-20261124/2611.10412v1)；[CRAB-Bench: Evaluating LLM Agents under Complex Task Dependencies and Human-aligned User Simulation](/20251125-20261124/2606.01815v1)；[Efficient Agent Evaluation via Diversity-Guided User Simulation](/20251125-20261124/2604.21480v1)；[User-Oriented Multi-Turn Dialogue Generation with Tool Use at scale](/20251125-20261124/2601.08225v1)

## 子方向四：面向推荐与搜索的模拟用户行为建模

该子方向关注推荐系统和搜索场景中的用户模拟，强调用户偏好、决策过程和上下文对行为的影响。方法包括：用 LLM 显式分析物品特征与用户情感（LLM-Powered User Simulator for Recommender System）；将用户决策分解为效用选择与选择过载下的承诺决策（Hesitator）；用世界模型从真实交互中学习用户策略（AlignUSER）；以及将日常生活情境（时间、地点、需求）纳入模拟（ContextSim）。对话推荐方向还关注“目标泄漏”和“猜测游戏”问题，PEPPER 提出无目标用户模拟器以评估偏好启发能力。搜索方向有 Agent4DL 和 UXSim 等，分别面向数字图书馆和混合式搜索模拟。该子方向的证据多来自离线实验和与真实日志的相关性分析，摘要中未提供统一的在线 A/B 验证结论。

依据：[LLM-Powered User Simulator for Recommender System](/conference/aaai-2025/aaai-2025-33456-llm-powered-user-simulator-for-recommender-system)；[Decision-aware User Simulation Agent for Evaluating Conversational Recommender Systems](/20251125-20261124/2605.05250v1)；[AlignUSER: Human-Aligned LLM Agents via World Models for Recommender System Evaluation](/20251125-20261124/2601.00930v1)；[Beyond Offline A/B Testing: Context-Aware Agent Simulation for Recommender System Evaluation](/20251125-20261124/2604.09549v2)；[Stop Playing the Guessing Game&#33; Evaluating Conversational Recommender Systems via Target-free User Simulation](/conference/emnlp-2025/anthology-2025findings-emnlp1067-stop-playing-the-guessing-game-evaluating-conversational-recommender-systems-via-target-free-user-simulation)；[Generative Agents Navigating Digital Libraries](/20251125-20261124/2602.22529v1)；[UXSim: Towards a Hybrid User Search Simulation](/20251125-20261124/2602.24241v1)；[Through Their Eyes: Fixation-aligned Tuning for Personalized User Emulation](/20251125-20261124/2604.09368v1)；[Towards Faithful Simulation of Human Shopping Behavior](/20251125-20261124/2608.20707v1)

## 子方向五：人格、心理状态与行为一致性建模

该子方向聚焦模拟用户“像不像一个人”：人格一致性、心理状态演化、情绪与认知动态。相关工作包括：用多轮强化学习减少人格漂移（Consistently Simulating Human Personas）；用 BDI 模型生成生活轨迹（LifeSim）；用认知状态转移驱动主动对话策略（Cog-Sim）；用心理网络模型和图表征奖励模拟心理机制（SimAI）；以及用知识状态图评估信息校准（KnowSim）。人格控制方面，AgentPersonaBench 在多种交互界面上检验人格特质是否真正驱动行为，PersonaEval 和 PersonaForge 提供基于人格的模拟框架。该方向的一个共同发现是：仅靠提示注入人格往往导致行为夸张或漂移，需要训练或结构化状态维护；但各工作对“一致性”的操作化定义不同，摘要中未给出统一度量。

依据：[Consistently Simulating Human Personas with Multi-Turn Reinforcement Learning](/conference/neurips-2025/openreview-neurips-2025-a0t3pihiis-consistently-simulating-human-personas-with-multi-turn-reinforcement-learning)；[LifeSim: Long-Horizon User Life Simulator for Personalized Assistant Evaluation](/20251125-20261124/2603.12152v1)；[Proactive Dialogue Policy Optimization via Cognitive-State Transition](/20251125-20261124/2609.34948v1)；[SimAI: Mechanistic User Simulation through Psychological Network Models](/20251125-20261124/2611.21808v1)；[KnowSim: Evaluating Information Calibration in LLM Assistants with User Simulators that Learn](/20251125-20261124/2608.17150v1)；[AgentPersonaBench: Benchmarking Persona-Driven User Simulation](/20251125-20261124/2610.04379v1)；[PersonaEval: Persona-Based User Simulation for Evaluating Interactive Applications](/20251125-20261124/2608.15838v1)；[PersonaForge: Realistic Multi-Turn User Simulation for Agentic Systems](/20251125-20261124/2608.28378v1)；[SPASM: Stable Persona-driven Agent Simulation for Multi-turn Dialogue Generation](/20251125-20261124/2604.09212v1)；[Cognitive World Model for Progressive BDI/E Trajectory Evaluation of Conversational Agents](/20251125-20261124/2606.29495v2)；[Beyond Borrowed Histories: Person-Aligned User Simulation for Interactive Role-Playing Evaluation](/20251125-20261124/2607.27816v2)；[After Talking with 1,000 Personas: Learning Preference-Aligned Proactive Assistants From Large-Scale Persona Interactions](/20251125-20261124/2602.04000v3)

## 子方向六：可控性、对抗性与压力测试

该子方向研究如何让模拟器按需产生特定行为，以及如何用对抗性用户暴露智能体的鲁棒性缺陷。可控性方面，Controllable User Simulation 将可控模拟形式化为因果推断问题，指出在事后轨迹标签上监督微调会产生前视偏差，并证明策略偏移下评估方差会急剧放大；Intent Speaks Louder 将每轮交互意图作为显式指令；CUE 和三层人格向量工作通过连续表示或结构化维度控制模拟用户。对抗性方面，StressSim 在保持用户目标不变的前提下优化对抗计划以降低智能体成功率；MASP 将主动对话建模为与理性抵抗用户的博弈；PPol 通过进化搜索生成多样且保持任务目标的人格策略。该方向的价值在于揭示合作型模拟器掩盖的失败模式，但对抗强度与行为真实性之间的权衡在摘要中尚未得到系统量化。

依据：[Controllable User Simulation](/20251125-20261124/2605.11519v1)；[Intent Speaks Louder: Controllable User Simulation Beyond Response Imitation](/20251125-20261124/2608.09420v1)；[CUEing User Simulators: Calibrated User Embeddings for Multi-Turn Benchmarking](/20251125-20261124/2610.02460v1)；[A Three-Tier Persona Vector for Controllable User Simulation in Agentic Evaluation](/20251125-20261124/2609.08592v1)；[Intent-Preserving Adversarial User Simulation for Multi-Turn Agent Evaluation](/20251125-20261124/2610.35426v1)；[Stop Training Against Soft Users: Mentalized Adversarial Self-Play for Proactive Dialogue](/20251125-20261124/2610.21156v1)；[Beyond Cooperative Simulators: Generating Realistic User Personas for Robust Evaluation of LLM Agents](/20251125-20261124/2605.12894v1)；[Disclosure-Gated User Simulation for Companion-Agent Evaluation](/20251125-20261124/2609.00982v1)；[Efficient Agent Evaluation via Diversity-Guided User Simulation](/20251125-20261124/2604.21480v1)；[MADS: Multi-Agent Dialog Simulation for Robust Conversational Agents](/20251125-20261124/2610.12757v1)；[ToolRACER: A Robust Agentic Conversation Emulation Resource for Agent Training and Evaluation](/20251125-20261124/2610.09163v1)

## 子方向七：模拟器作为训练环境与反馈来源

该子方向把用户模拟器从评测工具扩展为训练环境：智能体与模拟用户交互，通过强化学习或蒸馏获得多轮能力。MIMESIS 冻结模拟器并用多轮强化学习训练智能体，同时提出教练式在策略自蒸馏；Training User Simulators with Latent Intrinsic Feedback 让模拟器输出潜在评价状态作为奖励信号；Quantifying the Utility of User Simulators 通过用户研究比较不同模拟器训练出的助手在真实用户上的表现；SMTPO 和 ECPO 将模拟器反馈用于对话推荐的偏好优化。该方向的关键问题是模拟器反馈的偏差会累积到智能体策略中，因此模拟器保真度直接决定训练效果。摘要中报告了不同模拟器训练效果的差异，但训练规模、奖励设计和真实用户验证方式各异，难以直接横向比较。

依据：[MIMESIS: Learning User Simulators as Training Environments for Interactive Agents](/20251125-20261124/2610.09484v2)；[Training User Simulators with Latent Intrinsic Feedback](/20251125-20261124/2610.13617v1)；[Quantifying the Utility of User Simulators for Building Collaborative LLM Assistants](/20251125-20261124/2605.09808v1)；[User Simulator-Guided Multi-Turn Preference Optimization for Reasoning LLM-based Conversational Recommendation](/20251125-20261124/2604.03671v1)；[Expectation Confirmation Preference Optimization for Multi-Turn Conversational Recommendation Agent](/conference/acl-2025/anthology-2025findings-acl307-expectation-confirmation-preference-optimization-for-multi-turn-conversational-recommendation-agent)；[Mind2Dialogue: Training Human-Aware Language Models by Simulating User Mental States](/20251125-20261124/2609.15972v1)；[SimRPD: Optimizing Recruitment Proactive Dialogue Agents through Simulator-Based Data Evaluation and Selection](/20251125-20261124/2601.02871v3)；[After Talking with 1,000 Personas: Learning Preference-Aligned Proactive Assistants From Large-Scale Persona Interactions](/20251125-20261124/2602.04000v3)

## 评测实践与局限：证据不足与开放问题

综合输入论文，当前用户模拟器研究的主要局限包括：（1）模拟器与真实用户之间存在系统性行为差距，表现为过度合作、风格同质、缺乏挫败与歧义，可能高估智能体能力；（2）现有评估指标对模拟器失败的检测能力有限，部分指标甚至偏好异常行为；（3）模拟器的可控性、保真度与下游效用之间关系复杂，提示工程、人格条件化和模型规模扩展的收益并不一致；（4）跨领域、跨语言和语音/多模态场景的模拟证据仍然较少，部分工作仅覆盖单一领域或单一语言；（5）人类验证研究规模有限，且不同研究的任务和评分协议差异大，难以形成统一结论。本导读未补写任何外部经典文献、代码仓库或领域事实；凡摘要未明确给出的信息，均视为证据不足。

依据：[On Evaluating User Simulators for Interactive Agents](/20251125-20261124/2611.24892v1)；[SimulatorArena: Are User Simulators Reliable Proxies for Multi-Turn Evaluation of AI Assistants?](/conference/emnlp-2025/anthology-2025emnlp-main1786-simulatorarena-are-user-simulators-reliable-proxies-for-multi-turn-evaluation-of-ai-assistants)；[Mind the Sim2Real Gap in User Simulation for Agentic Tasks](/20251125-20261124/2603.11245v2)；[Measuring and Mitigating the Distributional Gap Between Real and Simulated User Behaviors](/20251125-20261124/2605.07847v1)；[Synthetic Users, Real Differences: an Evaluation Framework for User Simulation in Multi-Turn Conversations](/20251125-20261124/2605.02624v1)；[Controllable User Simulation](/20251125-20261124/2605.11519v1)；[A Survey on LLM-based Conversational User Simulation](/20251125-20261124/2604.24977v1)

## 建议阅读顺序

以下为建议学习顺序，不是公布时间排序。

1. [A Survey on LLM-based Conversational User Simulation](/20251125-20261124/2604.24977v1) · 入门
   - 阅读理由：综述性论文，提供用户模拟器的分类框架、核心技术与评估方法，适合作为入门总览。
   - 公布时间：2026-04-27（日精度）
   - arxiv · 2026-04-27（日精度）：[原文](https://arxiv.org/pdf/2604.24977v1) / [PDF](https://arxiv.org/pdf/2604.24977v1)

2. [&#123;&#36;&#92;tau&#36;&#125;-bench: A Benchmark for &#92;underline&#123;T&#125;ool-&#92;underline&#123;A&#125;gent-&#92;underline&#123;U&#125;ser Interaction in Real-World Domains](/conference/iclr-2025/openreview-iclr-2025-ronsxzpudn-tau-bench-a-benchmark-for-underlinetool-underlineagent-underlineuser-interaction-in-real-world-domains) · 入门
   - 阅读理由：τ-bench 是模拟用户与工具智能体交互的代表性基准，理解其任务设置和评估协议有助于把握应用场景。
   - 公布时间：2025（年精度）
   - ICLR-2025-Accepted · 2025（年精度）：[官方论文集](https://proceedings.iclr.cc/paper_files/paper/2025/hash/1b126cc38b8638e07bef37e7b2bb72bf-Abstract-Conference.html) / [原文](https://openreview.net/forum?id=roNSXZpUDN)

3. [On Evaluating User Simulators for Interactive Agents](/20251125-20261124/2611.24892v1) · 入门
   - 阅读理由：系统元评估现有模拟器评估指标，揭示指标检测失败的能力边界，是理解“如何评估模拟器”的关键入口。
   - 公布时间：2026-11-18（日精度）
   - arxiv · 2026-11-18（日精度）：[原文](https://arxiv.org/pdf/2611.24892v1)

4. [SimulatorArena: Are User Simulators Reliable Proxies for Multi-Turn Evaluation of AI Assistants?](/conference/emnlp-2025/anthology-2025emnlp-main1786-simulatorarena-are-user-simulators-reliable-proxies-for-multi-turn-evaluation-of-ai-assistants) · 入门
   - 阅读理由：SimulatorArena 提供模拟器与真实用户判断一致性的基准，展示人格条件化模拟器的表现与局限。
   - 公布时间：2025（年精度）
   - EMNLP-2025-Main · 2025（年精度）：[原文](https://aclanthology.org/2025.emnlp-main.1786/) / [PDF](https://aclanthology.org/2025.emnlp-main.1786.pdf)

5. [Quantifying the Utility of User Simulators for Building Collaborative LLM Assistants](/20251125-20261124/2605.09808v1) · 进阶
   - 阅读理由：从下游效用角度量化模拟器质量，连接模拟器训练与真实用户表现，适合理解评估的实践意义。
   - 公布时间：2026-05-10（日精度）
   - arxiv · 2026-05-10（日精度）：[原文](https://arxiv.org/pdf/2605.09808v1) / [PDF](https://arxiv.org/pdf/2605.09808v1)

6. [Mind the Sim2Real Gap in User Simulation for Agentic Tasks](/20251125-20261124/2603.11245v2) · 进阶
   - 阅读理由：形式化 Sim2Real 差距并用真实人类实验基准测试多种模拟器，揭示过度合作等系统性问题。
   - 公布时间：2026-03-11（日精度）
   - arxiv · 2026-03-11（日精度）：[原文](https://arxiv.org/pdf/2603.11245v2) / [PDF](https://arxiv.org/pdf/2603.11245v2)

7. [Measuring and Mitigating the Distributional Gap Between Real and Simulated User Behaviors](/20251125-20261124/2605.07847v1) · 进阶
   - 阅读理由：系统比较 24 个模拟器的行为分布差距，提供分布级评估视角和可解释的行为模式分析。
   - 公布时间：2026-05-08（日精度）
   - arxiv · 2026-05-08（日精度）：[原文](https://arxiv.org/pdf/2605.07847v1) / [PDF](https://arxiv.org/pdf/2605.07847v1)

8. [MIMESIS: Learning User Simulators as Training Environments for Interactive Agents](/20251125-20261124/2610.09484v2) · 进阶
   - 阅读理由：MIMESIS 展示专用模拟器的训练方法及其作为智能体训练环境的效果，连接模拟器构建与训练应用。
   - 公布时间：2026-10-07（日精度）
   - arxiv · 2026-10-07（日精度）：[原文](https://arxiv.org/pdf/2610.09484v1)
   - arxiv · 2026-10-07（日精度）：[原文](https://arxiv.org/pdf/2610.09484v2)

9. [Beyond Surface Style: Aligning Multi-Turn User Simulators with Behavioral Consistency](/20251125-20261124/2609.28690v1) · 进阶
   - 阅读理由：TRACER 通过多轮强化学习对齐行为轨迹，体现从单轮模仿到轨迹级一致性的方法演进。
   - 公布时间：2026-09-23（日精度）
   - arxiv · 2026-09-23（日精度）：[原文](https://arxiv.org/pdf/2609.28690v1)
   - arxiv · 2026-09-23（日精度）：[原文](https://arxiv.org/pdf/2609.28690v2)

10. [Intent Speaks Louder: Controllable User Simulation Beyond Response Imitation](/20251125-20261124/2608.09420v1) · 进阶
   - 阅读理由：将每轮交互意图与语言表达解耦，提供可控模拟的一个清晰技术路线。
   - 公布时间：2026-08-10（日精度）
   - arxiv · 2026-08-10（日精度）：[原文](https://arxiv.org/pdf/2608.09420v1)

11. [Controllable User Simulation](/20251125-20261124/2605.11519v1) · 专题
   - 阅读理由：从因果推断角度分析可控模拟的偏差来源，理论性较强，适合深入理解可控性问题。
   - 公布时间：2026-05-12（日精度）
   - arxiv · 2026-05-12（日精度）：[原文](https://arxiv.org/pdf/2605.11519v1) / [PDF](https://arxiv.org/pdf/2605.11519v1)

12. [Intent-Preserving Adversarial User Simulation for Multi-Turn Agent Evaluation](/20251125-20261124/2610.35426v1) · 专题
   - 阅读理由：意图保持的对抗用户模拟，展示压力测试智能体鲁棒性的方法设计。
   - 公布时间：2026-10-26（日精度）
   - arxiv · 2026-10-26（日精度）：[原文](https://arxiv.org/pdf/2610.35426v1)

13. [RealUserSim: Bridging the Reality Gap in Agent Benchmarking via Grounded User Simulation](/20251125-20261124/2605.20204v1) · 专题
   - 阅读理由：RealUserSim 用真实行为数据 grounding 模拟器，并分析现有基准中的指令放大问题，适合研究保真度提升。
   - 公布时间：2026-04-07（日精度）
   - arxiv · 2026-04-07（日精度）：[原文](https://arxiv.org/pdf/2605.20204v1) / [PDF](https://arxiv.org/pdf/2605.20204v1)

14. [CUEing User Simulators: Calibrated User Embeddings for Multi-Turn Benchmarking](/20251125-20261124/2610.02460v1) · 专题
   - 阅读理由：CUE 用校准的用户嵌入进行基准测试，关注结果校准和失败模式对齐，适合研究评测有效性。
   - 公布时间：2026-10-01（日精度）
   - arxiv · 2026-10-01（日精度）：[原文](https://arxiv.org/pdf/2610.02460v1)

15. [UserProxyBench: Evaluating LLM User Simulators for Agent Benchmarks and Training](/20251125-20261124/2609.38043v1) · 专题
   - 阅读理由：UserProxyBench 直接测量模拟用户是否执行其被分配的角色，补充了仅评分智能体的基准盲点。
   - 公布时间：2026-09-29（日精度）
   - arxiv · 2026-09-29（日精度）：[原文](https://arxiv.org/pdf/2609.38043v1)

16. [HumanLM: Simulating Users with State Alignment Beats Response Imitation](/20251125-20261124/2603.03303v1) · 专题
   - 阅读理由：HumanLM 强调状态对齐优于响应模仿，并构建大规模基准，适合研究心理状态建模。
   - 公布时间：2026-02-07（日精度）
   - arxiv · 2026-02-07（日精度）：[原文](https://arxiv.org/pdf/2603.03303v1) / [PDF](https://arxiv.org/pdf/2603.03303v1)
   - ICML-2026-Accepted · 2026（年精度）：[原文](https://openreview.net/forum?id=xyFVjBi9wC) / [PDF](https://openreview.net/pdf/bbaf316cff8b2804691a848da2ead815aebca2ec.pdf)

17. [Training User Simulators with Latent Intrinsic Feedback](/20251125-20261124/2610.13617v1) · 专题
   - 阅读理由：让模拟器输出潜在内在反馈作为奖励，探索模拟器作为训练信号源的新角色。
   - 公布时间：2026-10-09（日精度）
   - arxiv · 2026-10-09（日精度）：[原文](https://arxiv.org/pdf/2610.13617v1)

18. [UserLM-R1: Modeling Human Reasoning in User Language Models with Multi-Reward Reinforcement Learning](/20251125-20261124/2601.09215v1) · 专题
   - 阅读理由：UserLM-R1 将人类推理引入用户语言模型，面向跨域泛化和对抗性交互。
   - 公布时间：2026-01-14（日精度）
   - arxiv · 2026-01-14（日精度）：[原文](https://arxiv.org/pdf/2601.09215v1) / [PDF](https://arxiv.org/pdf/2601.09215v1)

19. [SpokenUS: A Spoken User Simulator for Task-Oriented Dialogue](/20251125-20261124/2603.16783v2) · 专题
   - 阅读理由：SpokenUS 将用户模拟扩展到语音任务型对话，覆盖语音行为多样性，适合研究多模态模拟。
   - 公布时间：2026-03-17（日精度）
   - arxiv · 2026-03-17（日精度）：[原文](https://arxiv.org/pdf/2603.16783v2) / [PDF](https://arxiv.org/pdf/2603.16783v2)

20. [ConvApparel: A Benchmark Dataset and Validation Framework for User Simulators in Conversational Recommenders](/20251125-20261124/2602.16938v1) · 专题
   - 阅读理由：ConvApparel 提供对话推荐模拟器的验证框架和反事实验证，适合研究领域特定的模拟器评估。
   - 公布时间：2026-02-18（日精度）
   - arxiv · 2026-02-18（日精度）：[原文](https://arxiv.org/pdf/2602.16938v1) / [PDF](https://arxiv.org/pdf/2602.16938v1)

任务：研究方向大礼包

固定窗口：arXiv &#91;2025-11-25, 2026-11-25&#41;；会议 &#91;2024-11-25, 2026-11-25&#41;（UTC，结束日不含）

本次候选评审上限 300，最终名单上限 100；本轮内容预算 10。

覆盖限制：仅检索配置范围内已有库存与预算内候选；向量/会议Top-k召回并非全库遍历，不保证找全相关论文。未核实录用、日期边界和缺失库存不能当作已覆盖。

缺失库存：eccv 2025、emnlp 2026。

研究需求：请帮我查找用户模拟器相关的论文

# user-sim

以下为本次固定最终名单，按相关性评分降序；不代表全部相关论文。

1. [On Evaluating User Simulators for Interactive Agents](https://arxiv.org/abs/2611.24892v1) · 分数 10
2. [SimulatorArena: Are User Simulators Reliable Proxies for Multi-Turn Evaluation of AI Assistants?](https://aclanthology.org/2025.emnlp-main.1786/) · 分数 10
3. [LLM-Powered User Simulator for Recommender System](https://ojs.aaai.org/index.php/AAAI/article/view/33456) · 分数 10
4. [Consistently Simulating Human Personas with Multi-Turn Reinforcement Learning](https://papers.neurips.cc/paper_files/paper/2025/hash/4c91443877f8388d8190c938ac5a4d4d-Abstract-Conference.html) · 分数 10
5. [AutoSim: A Self-Improving User Simulator for Conversational Search Evaluation](https://arxiv.org/abs/2610.28054v1) · 分数 9
6. [DIAL: Direct Iterative Adversarial Learning for Realistic Multi-Turn Dialogue Simulation](https://arxiv.org/abs/2512.20773v4) · 分数 9
7. [Intent Speaks Louder: Controllable User Simulation Beyond Response Imitation](https://arxiv.org/abs/2608.09420v1) · 分数 9
8. [MIMESIS: Learning User Simulators as Training Environments for Interactive Agents](https://arxiv.org/abs/2610.09484v2) · 分数 9
9. [Beyond Surface Style: Aligning Multi-Turn User Simulators with Behavioral Consistency](https://arxiv.org/abs/2609.28690v1) · 分数 9
10. [Training User Simulators with Latent Intrinsic Feedback](https://arxiv.org/abs/2610.13617v1) · 分数 9
11. [Quantifying the Utility of User Simulators for Building Collaborative LLM Assistants](https://arxiv.org/abs/2605.09808v1) · 分数 9
12. [MUSE: Multi-Domain Chinese User Simulation via Self-Evolving Profiles and Rubric-Guided Alignment](https://arxiv.org/abs/2604.13828v1) · 分数 9
13. [CUEing User Simulators: Calibrated User Embeddings for Multi-Turn Benchmarking](https://arxiv.org/abs/2610.02460v1) · 分数 9
14. [Controllable User Simulation](https://arxiv.org/abs/2605.11519v1) · 分数 9
15. [Towards User Simulators That Stay On Task And Still Sound Natural](https://arxiv.org/abs/2610.31512v1) · 分数 9
16. [UserProxyBench: Evaluating LLM User Simulators for Agent Benchmarks and Training](https://arxiv.org/abs/2609.38043v1) · 分数 9
17. [HumanLM: Simulating Users with State Alignment Beats Response Imitation](https://arxiv.org/abs/2603.03303v1) · 分数 9
18. [Measuring and Mitigating the Distributional Gap Between Real and Simulated User Behaviors](https://arxiv.org/abs/2605.07847v1) · 分数 9
19. [Proactive Dialogue Policy Optimization via Cognitive-State Transition](https://arxiv.org/abs/2609.34948v1) · 分数 9
20. [UserSimCRS v2: Simulation-Based Evaluation for Conversational Recommender Systems](https://arxiv.org/abs/2512.04588v3) · 分数 9
21. [ConvApparel: A Benchmark Dataset and Validation Framework for User Simulators in Conversational Recommenders](https://arxiv.org/abs/2602.16938v1) · 分数 9
22. [Synthetic Users, Real Differences: an Evaluation Framework for User Simulation in Multi-Turn Conversations](https://arxiv.org/abs/2605.02624v1) · 分数 9
23. [RealUserSim: Bridging the Reality Gap in Agent Benchmarking via Grounded User Simulation](https://arxiv.org/abs/2605.20204v1) · 分数 9
24. [Enjoy Your Talk: A Human-Centered Benchmark for Multi-Turn Dialogue with Decoupled User Simulation, Target Modeling, and Judging](https://arxiv.org/abs/2607.10428v2) · 分数 9
25. [Analyzing Repetition and Interference Effects in Memory-Constrained User Simulators](https://arxiv.org/abs/2610.24232v1) · 分数 9
26. [MirrorBench: A Benchmark to Evaluate Conversational User-Proxy Agents for Human-Likeness](https://arxiv.org/abs/2601.08118v3) · 分数 9
27. [Mind the Sim2Real Gap in User Simulation for Agentic Tasks](https://arxiv.org/abs/2603.11245v2) · 分数 9
28. [SimAI: Mechanistic User Simulation through Psychological Network Models](https://arxiv.org/abs/2611.21808v1) · 分数 9
29. [OmniSimulator: Aligning Small Language Models for Authentic Heterogeneous Behavior Modeling](https://arxiv.org/abs/2610.29472v1) · 分数 9
30. [SpokenUS: A Spoken User Simulator for Task-Oriented Dialogue](https://arxiv.org/abs/2603.16783v2) · 分数 9
31. [Learning User Representations to Improve Simulation Fidelity](https://arxiv.org/abs/2610.22518v1) · 分数 9
32. [Investigating Assistant Bias in LLM User Simulators Using a Role Vector](https://arxiv.org/abs/2609.00608v1) · 分数 9
33. [KnowSim: Evaluating Information Calibration in LLM Assistants with User Simulators that Learn](https://arxiv.org/abs/2608.17150v1) · 分数 9
34. [Decision-aware User Simulation Agent for Evaluating Conversational Recommender Systems](https://arxiv.org/abs/2605.05250v1) · 分数 9
35. [LifeSim: Long-Horizon User Life Simulator for Personalized Assistant Evaluation](https://arxiv.org/abs/2603.12152v1) · 分数 9
36. [Towards Fast Domain Adaptation and Fine-Grained User Simulation for Evaluating Conversational Recommender Systems](https://arxiv.org/abs/2606.22803v2) · 分数 9
37. [Generating Diverse Personas for User Simulators to Test Interview Dialogue Systems](https://arxiv.org/abs/2608.19549v1) · 分数 9
38. [PersonaEval: Persona-Based User Simulation for Evaluating Interactive Applications](https://arxiv.org/abs/2608.15838v1) · 分数 9
39. [A Survey on LLM-based Conversational User Simulation](https://arxiv.org/abs/2604.24977v1) · 分数 9
40. [PersonaForge: Realistic Multi-Turn User Simulation for Agentic Systems](https://arxiv.org/abs/2608.28378v1) · 分数 9
41. [Beyond Action Imitation: Learning a Decision-Aware User Simulator for Online Advertising](https://arxiv.org/abs/2607.26893v1) · 分数 9
42. [CustomerSim: Benchmarking and Aligning Multimodal Language Models as Retail User Simulators](https://arxiv.org/abs/2605.08334v2) · 分数 9
43. [AgentPersonaBench: Benchmarking Persona-Driven User Simulation](https://arxiv.org/abs/2610.04379v1) · 分数 9
44. [Profile-Driven User Simulation via Reinforcement Learning with Hierarchical Rewards for Task-Oriented Dialogues](https://arxiv.org/abs/2610.32435v1) · 分数 9
45. [Agentic Persona Control and Task State Tracking for Realistic User Simulation in Interactive Scenarios](https://arxiv.org/abs/2601.15290v1) · 分数 9
46. [Intent-Preserving Adversarial User Simulation for Multi-Turn Agent Evaluation](https://arxiv.org/abs/2610.35426v1) · 分数 9
47. [UXSim: Towards a Hybrid User Search Simulation](https://arxiv.org/abs/2602.24241v1) · 分数 9
48. [Beyond Cooperative Simulators: Generating Realistic User Personas for Robust Evaluation of LLM Agents](https://arxiv.org/abs/2605.12894v1) · 分数 9
49. [Stop Playing the Guessing Game&#33; Evaluating Conversational Recommender Systems via Target-free User Simulation](https://aclanthology.org/2025.findings-emnlp.1067/) · 分数 9
50. [UserLM-R1: Modeling Human Reasoning in User Language Models with Multi-Reward Reinforcement Learning](https://arxiv.org/abs/2601.09215v1) · 分数 9
51. [UXBench Pro: Benchmarking Personalized User Experience in Multi-Turn Dialogue Interactions](https://arxiv.org/abs/2610.11638v1) · 分数 9
52. [Prompt Optimization for User Simulation in Conversational Recommender Systems: A Multi-Objective Framework](https://arxiv.org/abs/2607.00010v1) · 分数 9
53. [SWE-WhatIf: Simulating Real Users of Coding Agents from Recorded Session](https://arxiv.org/abs/2611.21095v1) · 分数 9
54. [SimRPD: Optimizing Recruitment Proactive Dialogue Agents through Simulator-Based Data Evaluation and Selection](https://arxiv.org/abs/2601.02871v3) · 分数 9
55. [Stop Training Against Soft Users: Mentalized Adversarial Self-Play for Proactive Dialogue](https://arxiv.org/abs/2610.21156v1) · 分数 9
56. [Disclosure-Gated User Simulation for Companion-Agent Evaluation](https://arxiv.org/abs/2609.00982v1) · 分数 9
57. [Evaluating Persona Consistency in LLM User Simulators Without External Reference Annotations](https://arxiv.org/abs/2611.30280v1) · 分数 9
58. [A Three-Tier Persona Vector for Controllable User Simulation in Agentic Evaluation](https://arxiv.org/abs/2609.08592v1) · 分数 9
59. [Verifiable User Simulation for Search and Recommendation Systems](https://arxiv.org/abs/2606.14474v1) · 分数 9
60. [Through Their Eyes: Fixation-aligned Tuning for Personalized User Emulation](https://arxiv.org/abs/2604.09368v1) · 分数 9
61. [CRAB-Bench: Evaluating LLM Agents under Complex Task Dependencies and Human-aligned User Simulation](https://arxiv.org/abs/2606.01815v1) · 分数 9
62. [Unlocking Proactivity in Task-Oriented Dialogue](https://arxiv.org/abs/2605.22240v2) · 分数 9
63. [Is He Extroverted? Identifying Missing Relevant Personas for Faithful User Simulation](https://arxiv.org/abs/2602.15832v2) · 分数 9
64. [&#36;τ&#36;-Voice: Benchmarking Full-Duplex Voice Agents on Real-World Domains](https://arxiv.org/abs/2603.13686v1) · 分数 9
65. [Breakdowns in Conversational AI: Interactional Failures in Emotionally and Ethically Sensitive Contexts](https://arxiv.org/abs/2604.02713v1) · 分数 9
66. [Generative Agents Navigating Digital Libraries](https://arxiv.org/abs/2602.22529v1) · 分数 9
67. [MH-RAG-DIVE: Dynamic and Cost-Efficient Multi-Hop RAG Evaluation via Tree-Cached Dialogue Simulation](https://arxiv.org/abs/2611.30335v1) · 分数 9
68. [AlignUSER: Human-Aligned LLM Agents via World Models for Recommender System Evaluation](https://arxiv.org/abs/2601.00930v1) · 分数 9
69. [SDialog: A Python Toolkit for End-to-End Agent Building, User Simulation, Dialog Generation, and Evaluation](https://arxiv.org/abs/2512.09142v2) · 分数 8
70. [ToolTurns: Benchmarking LLM Agents in Multi-Turn Dialogue](https://arxiv.org/abs/2611.14925v1) · 分数 8
71. [Dialogue SWE-Bench: A Benchmark for Dialogue-Driven Coding Agents](https://arxiv.org/abs/2606.13995v1) · 分数 8
72. [Joint Workflow and Prompt Optimization for User Behavior Simulation](https://arxiv.org/abs/2610.07663v1) · 分数 8
73. [User Simulator-Guided Multi-Turn Preference Optimization for Reasoning LLM-based Conversational Recommendation](https://arxiv.org/abs/2604.03671v1) · 分数 8
74. [Mind2Dialogue: Training Human-Aware Language Models by Simulating User Mental States](https://arxiv.org/abs/2609.15972v1) · 分数 8
75. [Beyond Borrowed Histories: Person-Aligned User Simulation for Interactive Role-Playing Evaluation](https://arxiv.org/abs/2607.27816v2) · 分数 8
76. [Proactive Agent Research Environment: Simulating Active Users to Evaluate Proactive Assistants](https://arxiv.org/abs/2604.00842v1) · 分数 8
77. [TurnFlow: Benchmarking User-State Reasoning in Multi-Turn LLM Agents via Scene-Guided User Simulation](https://arxiv.org/abs/2611.10412v1) · 分数 8
78. [CoReflect: A Reflective Co-Evolution Framework for Improving Conversational Evaluation](https://arxiv.org/abs/2601.12208v2) · 分数 8
79. [Efficient Agent Evaluation via Diversity-Guided User Simulation](https://arxiv.org/abs/2604.21480v1) · 分数 8
80. [MADS: Multi-Agent Dialog Simulation for Robust Conversational Agents](https://arxiv.org/abs/2610.12757v1) · 分数 8
81. [Joi-Bench-Task: Benchmarking Task Coordination in Full-duplex Voice Agents through Interactive Simulation](https://arxiv.org/abs/2611.12118v1) · 分数 8
82. [Learning to Simulate Human Dialogue](https://arxiv.org/abs/2601.04436v1) · 分数 8
83. [ToolRACER: A Robust Agentic Conversation Emulation Resource for Agent Training and Evaluation](https://arxiv.org/abs/2610.09163v1) · 分数 8
84. [User-Oriented Multi-Turn Dialogue Generation with Tool Use at scale](https://arxiv.org/abs/2601.08225v1) · 分数 8
85. [Towards Faithful Simulation of Human Shopping Behavior](https://arxiv.org/abs/2608.20707v1) · 分数 8
86. [&#123;&#36;&#92;tau&#36;&#125;-bench: A Benchmark for &#92;underline&#123;T&#125;ool-&#92;underline&#123;A&#125;gent-&#92;underline&#123;U&#125;ser Interaction in Real-World Domains](https://proceedings.iclr.cc/paper_files/paper/2025/hash/1b126cc38b8638e07bef37e7b2bb72bf-Abstract-Conference.html) · 分数 8
87. [Towards Personalized Conversational Sales Agents: Contextual User Profiling for Strategic Action](https://aclanthology.org/2025.findings-emnlp.275/) · 分数 8
88. [Interactive Task Alignment as a POMDP](https://arxiv.org/abs/2607.16412v1) · 分数 8
89. [PersonaChatBench: Evaluating Chat Assistants with Diverse Simulated Users](https://arxiv.org/abs/2610.42060v1) · 分数 8
90. [Interactive Visual Gym: Evaluating Visual Interaction Models with Simulated Users in Interactive Worlds](https://arxiv.org/abs/2611.08286v2) · 分数 8
91. [SWE-Together: Evaluating Coding Agents in Interactive User Sessions](https://arxiv.org/abs/2606.29957v1) · 分数 8
92. [SPASM: Stable Persona-driven Agent Simulation for Multi-turn Dialogue Generation](https://arxiv.org/abs/2604.09212v1) · 分数 8
93. [Personality-Aware Reinforcement Learning for Persuasive Dialogue with LLM-Driven Simulation](https://arxiv.org/abs/2601.06877v1) · 分数 8
94. [Automatic multimodal UX improvement recommendations from LLM agent user simulations](https://arxiv.org/abs/2609.22971v1) · 分数 8
95. [Expectation Confirmation Preference Optimization for Multi-Turn Conversational Recommendation Agent](https://aclanthology.org/2025.findings-acl.307/) · 分数 8
96. [Cognitive World Model for Progressive BDI/E Trajectory Evaluation of Conversational Agents](https://arxiv.org/abs/2606.29495v2) · 分数 8
97. [KnowU-Bench: Towards Interactive, Proactive, and Personalized Mobile Agent Evaluation](https://arxiv.org/abs/2604.08455v1) · 分数 8
98. [From Transcripts to AI Agents: Knowledge Extraction, RAG Integration, and Robust Evaluation of Conversational AI Assistants](https://arxiv.org/abs/2602.15859v1) · 分数 8
99. [Beyond Offline A/B Testing: Context-Aware Agent Simulation for Recommender System Evaluation](https://arxiv.org/abs/2604.09549v2) · 分数 8
100. [After Talking with 1,000 Personas: Learning Preference-Aligned Proactive Assistants From Large-Scale Persona Interactions](https://arxiv.org/abs/2602.04000v3) · 分数 8

[按公布时间查看](#/starter-pack/20261125-68a82e6ab836/dates)

阅读内容：已完成 1，待补充 99。

部分阅读内容生成失败；固定名单及导出保留，可继续生成缺失内容。
