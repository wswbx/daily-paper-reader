<div class="dpr-topic-result-actions"><button type="button" class="arxiv-tool-btn" data-topic-copy="docs/20251126-20261125-starter-looped-llm-729081/papers.md">复制完整清单</button> <a class="arxiv-tool-btn" href="docs/20251126-20261125-starter-looped-llm-729081/papers.md" download data-no-router>下载 Markdown 清单</a></div>

# looped-llm · 入门导读

> 本导读基于所列论文的标题、摘要和已有速览，不代表已阅读全部全文。近期窗口不是完整领域史；检索不保证覆盖全部相关论文。模型导读需结合原文核验。

检索窗口：2025-11-26 ~ 2026-11-25

## 方向概览

本导读聚焦使用循环 Transformer（looped transformer）架构的大语言模型：通过重复应用同一组或部分 Transformer 层、在循环间共享参数来增加有效计算深度，而不成比例增加参数量。研究问题包括：循环应放在何处（全栈、中间块、混合器或非对称编解码器）、循环次数如何调度与训练、如何稳定循环动力学、如何控制 KV 缓存与解码延迟、以及循环带来的收益在匹配参数与算力预算下如何度量。输入证据显示该方向已从早期可行性验证扩展到 1B 至 69B 级模型的技术报告与受控缩放研究，但多数结论仍来自特定数据与训练配方，跨规模与跨任务的普适性证据有限。本导读仅覆盖近期检索窗口，不是完整领域史。

依据：[Dory1.0-4B: A Looped Normalized-GPT](/20251126-20261125-starter-looped-llm-729081/2611.03998v1-dory10-4b-a-looped-normalized-gpt)；[Closing the Loop: Practical Training Recipes for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2610.00673v1-closing-the-loop-practical-training-recipes-for-looped-language-models)；[Simply Stabilizing the Loop via Fully Looped Transformer](/20251126-20261125-starter-looped-llm-729081/2605.18797v2-simply-stabilizing-the-loop-via-fully-looped-transformer)；[CART: Context-Anchored Recurrent Transformer -- A Parameter-Efficient Architecture with Learned Stability](/20251126-20261125-starter-looped-llm-729081/2606.01495v2-cart-context-anchored-recurrent-transformer----a-parameter-efficient-architecture-with-learned-stability)；[Loopback Transformer: Towards a Unified View of Residual Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2611.07226v1-loopback-transformer-towards-a-unified-view-of-residual-looped-transformers)；[ARLoop: Fully-Open Pre-trained Looped Transformers with Attention Residuals](/20251126-20261125-starter-looped-llm-729081/2611.05234v1-arloop-fully-open-pre-trained-looped-transformers-with-attention-residuals)；[How to Loop Your Transformer: Loop Scaling, Specialization, and Parallel Inference](/20251126-20261125-starter-looped-llm-729081/2610.40325v1-how-to-loop-your-transformer-loop-scaling-specialization-and-parallel-inference)；[Parcae: Scaling Laws For Stable Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.12946v1-parcae-scaling-laws-for-stable-looped-language-models)

## 循环架构与循环位置设计

该子方向研究循环应作用于哪些层以及如何组织前奏、循环块与尾声。Dory1.0-4B 采用归一化 Transformer 主干，组织为输入块、共享循环块与输出块，支持推理时可变循环次数。CART 用多层前奏一次性计算 KV，循环核心通过交叉注意力复用冻结张量。双路径架构在同一层中并行设置重复 K 次的共享深层子层与只执行一次的宽子层。Loopback Transformer 将共享栈输入置于独立路径，以几何衰减控制更新权重。ARLoop 用跨深度注意力残差选择性聚合循环中间表示。AsymLoop 分离单遍上下文编码与循环状态精炼。Hyperloop 以 begin/middle/end 三块组织，仅中间块循环并加入超连接。Parcae 将循环视为残差流上的动力系统并约束注入参数谱范数。上述工作共同表明循环位置与循环间信息传递方式显著影响收益，但各设计多在自建设置下评估，横向可比性有限。

依据：[Dory1.0-4B: A Looped Normalized-GPT](/20251126-20261125-starter-looped-llm-729081/2611.03998v1-dory10-4b-a-looped-normalized-gpt)；[CART: Context-Anchored Recurrent Transformer -- A Parameter-Efficient Architecture with Learned Stability](/20251126-20261125-starter-looped-llm-729081/2606.01495v2-cart-context-anchored-recurrent-transformer----a-parameter-efficient-architecture-with-learned-stability)；[A Dual-Path Architecture for Scaling Compute and Capacity in LLMs](/20251126-20261125-starter-looped-llm-729081/2605.30202v1-a-dual-path-architecture-for-scaling-compute-and-capacity-in-llms)；[Loopback Transformer: Towards a Unified View of Residual Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2611.07226v1-loopback-transformer-towards-a-unified-view-of-residual-looped-transformers)；[ARLoop: Fully-Open Pre-trained Looped Transformers with Attention Residuals](/20251126-20261125-starter-looped-llm-729081/2611.05234v1-arloop-fully-open-pre-trained-looped-transformers-with-attention-residuals)；[Asymmetric Looped Transformers: Fixed Global Representations for an Iterative Decoder](/20251126-20261125-starter-looped-llm-729081/2610.28489v1-asymmetric-looped-transformers-fixed-global-representations-for-an-iterative-decoder)；[Hyperloop Transformers](/20251126-20261125-starter-looped-llm-729081/2604.21254v3-hyperloop-transformers)；[Parcae: Scaling Laws For Stable Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.12946v1-parcae-scaling-laws-for-stable-looped-language-models)

## 训练配方、稳定性与循环调度

该子方向关注如何稳定训练循环模型以及如何调度循环次数。Parcae 指出残差爆炸与损失尖峰源于注入参数谱范数过大，并提出约束方案。全循环 Transformer 分析梯度振荡与残差爆炸，引入两项无参数修改以支持更深循环。训练配方工作将从头训练预算从 7.7T token 降至 310B token，并给出把稠密模型转为循环模型的最小配方。残差缩放研究指出权重共享使迭代更新相关，需要 1/N 而非 1/√L 缩放，并给出 λ/&#40;N√L&#41; 分解。DeepLoop 进一步分析绑定深度效应与访问对齐系数。循环次数调度研究比较固定与采样调度，发现采样区间下界决定额外循环是充当完整层还是小幅修正。截断反向传播研究在近 600 次训练上拟合缩放律，倾向完整 BPTT。反向窗口研究则表明预算增长时窗口偏好会变化。这些结论多来自受控小中规模实验，向更大规模迁移仍需验证。

依据：[Parcae: Scaling Laws For Stable Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.12946v1-parcae-scaling-laws-for-stable-looped-language-models)；[Simply Stabilizing the Loop via Fully Looped Transformer](/20251126-20261125-starter-looped-llm-729081/2605.18797v2-simply-stabilizing-the-loop-via-fully-looped-transformer)；[Closing the Loop: Practical Training Recipes for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2610.00673v1-closing-the-loop-practical-training-recipes-for-looped-language-models)；[On the Residual Scaling of Looped Transformers: Stability and Transferability](/20251126-20261125-starter-looped-llm-729081/2606.18524v1-on-the-residual-scaling-of-looped-transformers-stability-and-transferability)；[DeepLoop: Depth Scaling for Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2607.13491v2-deeploop-depth-scaling-for-looped-transformers)；[Loop-Count Schedules in Looped Transformers: An Empirical Study](/20251126-20261125-starter-looped-llm-729081/2611.29704v1-loop-count-schedules-in-looped-transformers-an-empirical-study)；[Truncate or Not? A Scaling Study of Looped Transformers with Truncated Backpropagation](/20251126-20261125-starter-looped-llm-729081/2610.26030v2-truncate-or-not-a-scaling-study-of-looped-transformers-with-truncated-backpropagation)；[Deeper Backpropagation or More Updates? Training Looped Language Models Across Budgets](/20251126-20261125-starter-looped-llm-729081/2610.38422v1-deeper-backpropagation-or-more-updates-training-looped-language-models-across-budgets)

## 循环间状态、记忆与 KV 缓存

该子方向研究如何在循环之间传递与复用信息以控制显存与稳定性。StateLoop 为每个 token 维护额外持久状态并用门控更新。共享记忆工作让仅首次循环写 KV 缓存，后续循环读取，报告质量不降反升。LSTM 风格循环 Transformer 在循环核心共享单一 KV 缓存，并用一致性损失对齐训练与续写。KV 重放研究让部分循环写入、后续循环复用 KV 状态。循环因果编码器-解码器将循环放在编码器以精炼全局 KV，实现零轮次 KV 增长。Dory1.0-4B 仅缓存最后一次循环的 KV。非对称循环 Transformer 用固定全局 KV 加局部 KV 联合注意力。这些机制在各自设置下报告了显存或质量收益，但缓存共享对长上下文与批量服务的影响仍缺乏统一评测。

依据：[StateLoop: Persistent State for Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2610.35544v1-stateloop-persistent-state-for-looped-transformers)；[The Surprising Effectiveness of Shared Memory in Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2610.02383v1-the-surprising-effectiveness-of-shared-memory-in-looped-transformers)；[LSTM-Style Looped Transformers with Shared KV Caches](/20251126-20261125-starter-looped-llm-729081/2610.33360v1-lstm-style-looped-transformers-with-shared-kv-caches)；[Architectures and KV Replay for Depth-Recurrent Language Models](/20251126-20261125-starter-looped-llm-729081/2611.19446v1-architectures-and-kv-replay-for-depth-recurrent-language-models)；[Looping Deeper Without Growing the KV Cache: Recurrent Depth for Causal Encoder-Decoders](/20251126-20261125-starter-looped-llm-729081/2611.13378v1-looping-deeper-without-growing-the-kv-cache-recurrent-depth-for-causal-encoder-decoders)；[Dory1.0-4B: A Looped Normalized-GPT](/20251126-20261125-starter-looped-llm-729081/2611.03998v1-dory10-4b-a-looped-normalized-gpt)；[Asymmetric Looped Transformers: Fixed Global Representations for an Iterative Decoder](/20251126-20261125-starter-looped-llm-729081/2610.28489v1-asymmetric-looped-transformers-fixed-global-representations-for-an-iterative-decoder)

## 稀疏化与 MoE 循环模型

该子方向将循环与稀疏专家或稀疏层结合以改善扩展性。稀疏层研究对比稠密与 MoE 循环模型，发现循环 MoE 扩展性优于标准基线，而稠密循环模型不然，原因是不同循环轮次激活不同专家。LoopMoE 用迭代索引与隐藏状态调制的 IterAdaLN 破解权重共享对称性，并在匹配参数与 FLOPs 下与普通 MoE 对比。SMELT 在匹配每 token FLOPs、非嵌入参数与 KV 缓存的条件下让中间一半层循环两次，并拟合 Chinchilla 式缩放律。循环 MoE 预算匹配研究给出核心深度占展开深度 25% 至 35% 并重分配参数的配置。混合循环 Transformer 用 KV 作为跨深度跨循环的选择性记忆。这些结果支持稀疏性是循环模型扩展的重要方向，但多数实验规模与数据配方各异，直接比较需谨慎。

依据：[Sparse Layers are Critical to Scaling Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2605.09165v2-sparse-layers-are-critical-to-scaling-looped-language-models)；[LoopMoE: Unifying Iterative Computation with Mixture-of-Experts for Language Modeling](/20251126-20261125-starter-looped-llm-729081/2606.04438v2-loopmoe-unifying-iterative-computation-with-mixture-of-experts-for-language-modeling)；[SMELT: Scaling Laws for Compute-Matched MoE Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2609.01343v2-smelt-scaling-laws-for-compute-matched-moe-looped-transformers)；[Scaling Looped MoE Language Models under Matched Budgets: Information Flow and Parameter Allocation](/20251126-20261125-starter-looped-llm-729081/2611.34276v1-scaling-looped-moe-language-models-under-matched-budgets-information-flow-and-parameter-allocation)；[Mixture-of-Loops Transformer](/20251126-20261125-starter-looped-llm-729081/2611.34923v1-mixture-of-loops-transformer)

## 推理、潜在思维与测试时计算

该子方向把循环深度视为测试时计算轴并研究其推理收益。潜在思维工作证明 k 层循环 L 次可接近 kL 层非循环模型，并论证循环模型可隐式模拟思维链步骤。LOTUS 用循环填充 Transformer 并行处理潜在块，报告在 3B 规模弥合潜在与显式思维链差距并降低延迟。LoopMTP 用多 token 预测对齐各循环隐状态以缓解潜在过度思考。循环深度 Transformer 研究系统性泛化与深度外推，并指出过度循环会退化。弹性深度工作让每个 token 动态决定循环次数或按预算条件化推理。LoopFold 折叠多个循环深度为并行批次以降低解码延迟。另有研究报告循环增加可缩小内部知识与输出差距，但部分源于表征知识退化，且表征感知只在最后一轮出现。这些发现揭示循环推理的能力与边界并存。

依据：[Reasoning with Latent Thoughts: On the Power of Looped Transformers](/conference/iclr-2025/openreview-iclr-2025-din0lgfzfd-reasoning-with-latent-thoughts-on-the-power-of-looped-transformers)；[Bridging the Gap Between Latent and Explicit Reasoning with Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2606.31779v2-bridging-the-gap-between-latent-and-explicit-reasoning-with-looped-transformers)；[LoopMTP: A looped transformer guided by latent multi-token prediction](/20251126-20261125-starter-looped-llm-729081/2608.03624v1-loopmtp-a-looped-transformer-guided-by-latent-multi-token-prediction)；[Loop, Think, &amp; Generalize: Implicit Reasoning in Recurrent-Depth Transformers](/20251126-20261125-starter-looped-llm-729081/2604.07822v2-loop-think--generalize-implicit-reasoning-in-recurrent-depth-transformers)；[T-LoopFormer: Token-Level Elastic-Depth Looped Transformers for Latent Reasoning With Dynamic Routing](/20251126-20261125-starter-looped-llm-729081/2609.15160v1-t-loopformer-token-level-elastic-depth-looped-transformers-for-latent-reasoning-with-dynamic-routing)；[LoopFormer: Elastic-Depth Looped Transformers for Latent Reasoning via Shortcut Modulation](/20251126-20261125-starter-looped-llm-729081/2602.11451v1-loopformer-elastic-depth-looped-transformers-for-latent-reasoning-via-shortcut-modulation)；[LoopFold: Parallelizing Recurrent Depth in Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2610.35556v1-loopfold-parallelizing-recurrent-depth-in-looped-transformers)；[Loop as a Bridge: Can Looped Transformers Truly Link Representation Space and Natural Language Outputs?](/20251126-20261125-starter-looped-llm-729081/2601.10242v1-loop-as-a-bridge-can-looped-transformers-truly-link-representation-space-and-natural-language-outputs)

## 匹配预算下的收益度量与缩放律

该子方向试图在匹配参数、FLOPs 或显存条件下分离循环本身的贡献。等深度缩放律研究拟合循环等价指数约 0.46，表明用共享循环替换独立块有收益但小于等量独立层，并指出截断反向传播会降低该指数而超连接会提高它。循环次数调度研究估计循环约恢复真实深度收益的三分之一。SMELT 在严格预算匹配下报告节省 6.8% 至 18.0% 训练 FLOPs。UpLoop 通过上循环在最终参数量、训练 token 与训练 FLOPs 与稠密基线完全对齐下训练循环模型。双路径工作报告在等 FLOP 下优于匹配基线。也有研究报告在参数对齐测试中循环模型未超过稠密基线，并给出负面的可变循环推理结果。总体而言，收益度量高度依赖预算定义与基线选择，尚无统一结论。

依据：[How Much Is One Recurrence Worth? Iso-Depth Scaling Laws for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.21106v3-how-much-is-one-recurrence-worth-iso-depth-scaling-laws-for-looped-language-models)；[Loop-Count Schedules in Looped Transformers: An Empirical Study](/20251126-20261125-starter-looped-llm-729081/2611.29704v1-loop-count-schedules-in-looped-transformers-an-empirical-study)；[SMELT: Scaling Laws for Compute-Matched MoE Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2609.01343v2-smelt-scaling-laws-for-compute-matched-moe-looped-transformers)；[UpLoop: Training Looped Transformers via Upcycling at No Extra Pretraining Compute](/20251126-20261125-starter-looped-llm-729081/2610.41720v1-uploop-training-looped-transformers-via-upcycling-at-no-extra-pretraining-compute)；[A Dual-Path Architecture for Scaling Compute and Capacity in LLMs](/20251126-20261125-starter-looped-llm-729081/2605.30202v1-a-dual-path-architecture-for-scaling-compute-and-capacity-in-llms)；[CART: Context-Anchored Recurrent Transformer -- A Parameter-Efficient Architecture with Learned Stability](/20251126-20261125-starter-looped-llm-729081/2606.01495v2-cart-context-anchored-recurrent-transformer----a-parameter-efficient-architecture-with-learned-stability)

## 评测、进展与局限

现有评测覆盖语言建模困惑度、零样本与少样本下游任务、数学与代码推理、长上下文、智能体任务以及训练与推理效率。进展方面：循环模型已扩展到数十亿至数百亿参数并发布开源检查点；训练稳定性与缩放律取得进展；KV 共享与并行解码缓解了显存与延迟；循环 MoE 显示出更好的扩展趋势；潜在推理在特定规模上缩小了与显式思维链的差距。局限方面：多数收益在自建数据与配方下测得，跨研究可比性不足；部分工作报告参数对齐下未超过稠密基线或可变深度推理退化；循环次数增加会出现收益饱和、反转或不稳定；循环模型容量在固定 FLOPs 下可能低于基线；表征感知与内省能力有限；过深循环导致过度思考。证据不足处：输入未提供统一的基准套件、标准化的预算匹配协议或跨家族的大规模复现，因此不能断言循环架构普遍优于稠密架构。

依据：[Dory1.0-4B: A Looped Normalized-GPT](/20251126-20261125-starter-looped-llm-729081/2611.03998v1-dory10-4b-a-looped-normalized-gpt)；[Closing the Loop: Practical Training Recipes for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2610.00673v1-closing-the-loop-practical-training-recipes-for-looped-language-models)；[Simply Stabilizing the Loop via Fully Looped Transformer](/20251126-20261125-starter-looped-llm-729081/2605.18797v2-simply-stabilizing-the-loop-via-fully-looped-transformer)；[CART: Context-Anchored Recurrent Transformer -- A Parameter-Efficient Architecture with Learned Stability](/20251126-20261125-starter-looped-llm-729081/2606.01495v2-cart-context-anchored-recurrent-transformer----a-parameter-efficient-architecture-with-learned-stability)；[How Much Is One Recurrence Worth? Iso-Depth Scaling Laws for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.21106v3-how-much-is-one-recurrence-worth-iso-depth-scaling-laws-for-looped-language-models)；[Sparse Layers are Critical to Scaling Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2605.09165v2-sparse-layers-are-critical-to-scaling-looped-language-models)；[Bridging the Gap Between Latent and Explicit Reasoning with Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2606.31779v2-bridging-the-gap-between-latent-and-explicit-reasoning-with-looped-transformers)；[Loop as a Bridge: Can Looped Transformers Truly Link Representation Space and Natural Language Outputs?](/20251126-20261125-starter-looped-llm-729081/2601.10242v1-loop-as-a-bridge-can-looped-transformers-truly-link-representation-space-and-natural-language-outputs)；[Loop, Think, &amp; Generalize: Implicit Reasoning in Recurrent-Depth Transformers](/20251126-20261125-starter-looped-llm-729081/2604.07822v2-loop-think--generalize-implicit-reasoning-in-recurrent-depth-transformers)；[How to Loop Your Transformer: Loop Scaling, Specialization, and Parallel Inference](/20251126-20261125-starter-looped-llm-729081/2610.40325v1-how-to-loop-your-transformer-loop-scaling-specialization-and-parallel-inference)

## 建议阅读顺序

以下为建议学习顺序，不是公布时间排序。

1. [Reasoning with Latent Thoughts: On the Power of Looped Transformers](/conference/iclr-2025/openreview-iclr-2025-din0lgfzfd-reasoning-with-latent-thoughts-on-the-power-of-looped-transformers) · 入门
   - 阅读理由：从推理视角建立循环 Transformer 的核心动机：深度而非参数是关键，循环可模拟潜在思维链。
   - 公布时间：2025（年精度）
   - ICLR-2025-Accepted · 2025（年精度）：[官方论文集](https://proceedings.iclr.cc/paper_files/paper/2025/hash/2676109d49d1eb26d6bc584a8f556305-Abstract-Conference.html) / [原文](https://openreview.net/forum?id=din0lGfZFd)

2. [Dory1.0-4B: A Looped Normalized-GPT](/20251126-20261125-starter-looped-llm-729081/2611.03998v1-dory10-4b-a-looped-normalized-gpt) · 入门
   - 阅读理由：代表性技术报告，展示 4B 级循环语言模型的完整架构、训练与弹性推理流程。
   - 公布时间：2026-11-02（日精度）
   - arxiv · 2026-11-02（日精度）：[原文](https://arxiv.org/pdf/2611.03998v1)

3. [Parcae: Scaling Laws For Stable Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.12946v1-parcae-scaling-laws-for-stable-looped-language-models) · 入门
   - 阅读理由：系统处理循环训练稳定性与缩放律，是理解后续稳定性工作的基础。
   - 公布时间：2026-04-14（日精度）
   - arxiv · 2026-04-14（日精度）：[原文](https://arxiv.org/pdf/2604.12946v1) / [PDF](https://arxiv.org/pdf/2604.12946v1)

4. [Closing the Loop: Practical Training Recipes for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2610.00673v1-closing-the-loop-practical-training-recipes-for-looped-language-models) · 入门
   - 阅读理由：给出实用训练配方与稠密转循环的最小方案，适合建立训练流程认识。
   - 公布时间：2026-09-30（日精度）
   - arxiv · 2026-09-30（日精度）：[原文](https://arxiv.org/pdf/2610.00673v1)

5. [Simply Stabilizing the Loop via Fully Looped Transformer](/20251126-20261125-starter-looped-llm-729081/2605.18797v2-simply-stabilizing-the-loop-via-fully-looped-transformer) · 进阶
   - 阅读理由：分析循环失稳来源并提出无参数修改，补充稳定性设计视角。
   - 公布时间：2026-05-11（日精度）
   - arxiv · 2026-05-11（日精度）：[原文](https://arxiv.org/pdf/2605.18797v2) / [PDF](https://arxiv.org/pdf/2605.18797v2)

6. [On the Residual Scaling of Looped Transformers: Stability and Transferability](/20251126-20261125-starter-looped-llm-729081/2606.18524v1-on-the-residual-scaling-of-looped-transformers-stability-and-transferability) · 进阶
   - 阅读理由：从残差缩放理论解释权重共享下的训练动力学，衔接稳定性与理论分析。
   - 公布时间：2026-06-16（日精度）
   - arxiv · 2026-06-16（日精度）：[原文](https://arxiv.org/pdf/2606.18524v1) / [PDF](https://arxiv.org/pdf/2606.18524v1)

7. [How Much Is One Recurrence Worth? Iso-Depth Scaling Laws for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.21106v3-how-much-is-one-recurrence-worth-iso-depth-scaling-laws-for-looped-language-models) · 进阶
   - 阅读理由：提供循环等价指数的定量缩放律，是理解循环收益度量的关键。
   - 公布时间：2026-04-22（日精度）
   - NeurIPS-2026-Accepted · 2026（年精度）：[原文](https://openreview.net/forum?id=iBvm5lCnAJ)
   - arxiv · 2026-04-22（日精度）：[原文](https://arxiv.org/pdf/2604.21106v3) / [PDF](https://arxiv.org/pdf/2604.21106v3)

8. [Loop-Count Schedules in Looped Transformers: An Empirical Study](/20251126-20261125-starter-looped-llm-729081/2611.29704v1-loop-count-schedules-in-looped-transformers-an-empirical-study) · 进阶
   - 阅读理由：通过循环次数调度实验揭示额外循环何时充当完整层或小幅修正。
   - 公布时间：2026-11-22（日精度）
   - arxiv · 2026-11-22（日精度）：[原文](https://arxiv.org/pdf/2611.29704v1)

9. [Truncate or Not? A Scaling Study of Looped Transformers with Truncated Backpropagation](/20251126-20261125-starter-looped-llm-729081/2610.26030v2-truncate-or-not-a-scaling-study-of-looped-transformers-with-truncated-backpropagation) · 进阶
   - 阅读理由：大规模截断反向传播缩放研究，补充训练预算与循环步数的权衡。
   - 公布时间：2026-10-19（日精度）
   - arxiv · 2026-10-19（日精度）：[原文](https://arxiv.org/pdf/2610.26030v1)
   - arxiv · 2026-10-19（日精度）：[原文](https://arxiv.org/pdf/2610.26030v2)

10. [Loopback Transformer: Towards a Unified View of Residual Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2611.07226v1-loopback-transformer-towards-a-unified-view-of-residual-looped-transformers) · 进阶
   - 阅读理由：从深度记忆视角统一分析循环间信息复用，连接架构设计与残差控制。
   - 公布时间：2026-11-04（日精度）
   - arxiv · 2026-11-04（日精度）：[原文](https://arxiv.org/pdf/2611.07226v1)

11. [ARLoop: Fully-Open Pre-trained Looped Transformers with Attention Residuals](/20251126-20261125-starter-looped-llm-729081/2611.05234v1-arloop-fully-open-pre-trained-looped-transformers-with-attention-residuals) · 进阶
   - 阅读理由：注意力残差循环架构并发布开源预训练模型，适合作为可复现基线。
   - 公布时间：2026-11-03（日精度）
   - arxiv · 2026-11-03（日精度）：[原文](https://arxiv.org/pdf/2611.05234v1)

12. [Asymmetric Looped Transformers: Fixed Global Representations for an Iterative Decoder](/20251126-20261125-starter-looped-llm-729081/2610.28489v1-asymmetric-looped-transformers-fixed-global-representations-for-an-iterative-decoder) · 进阶
   - 阅读理由：非对称循环设计分离上下文编码与状态精炼，展示循环位置的重要变体。
   - 公布时间：2026-10-20（日精度）
   - arxiv · 2026-10-20（日精度）：[原文](https://arxiv.org/pdf/2610.28489v1)

13. [A Dual-Path Architecture for Scaling Compute and Capacity in LLMs](/20251126-20261125-starter-looped-llm-729081/2605.30202v1-a-dual-path-architecture-for-scaling-compute-and-capacity-in-llms) · 进阶
   - 阅读理由：双路径块同时扩展计算与容量，回应循环模型容量受限问题。
   - 公布时间：2026-05-28（日精度）
   - arxiv · 2026-05-28（日精度）：[原文](https://arxiv.org/pdf/2605.30202v1) / [PDF](https://arxiv.org/pdf/2605.30202v1)

14. [Sparse Layers are Critical to Scaling Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2605.09165v2-sparse-layers-are-critical-to-scaling-looped-language-models) · 进阶
   - 阅读理由：稀疏层与循环 MoE 的扩展性分析，是稀疏化方向的入口。
   - 公布时间：2026-05-09（日精度）
   - arxiv · 2026-05-09（日精度）：[原文](https://arxiv.org/pdf/2605.09165v2) / [PDF](https://arxiv.org/pdf/2605.09165v2)
   - NeurIPS-2026-Accepted · 2026（年精度）：[原文](https://openreview.net/forum?id=zt77AglOvq)

15. [LoopMoE: Unifying Iterative Computation with Mixture-of-Experts for Language Modeling](/20251126-20261125-starter-looped-llm-729081/2606.04438v2-loopmoe-unifying-iterative-computation-with-mixture-of-experts-for-language-modeling) · 进阶
   - 阅读理由：LoopMoE 在匹配预算下隔离迭代计算效应，衔接稀疏化与受控评测。
   - 公布时间：2026-06-03（日精度）
   - arxiv · 2026-06-03（日精度）：[原文](https://arxiv.org/pdf/2606.04438v2) / [PDF](https://arxiv.org/pdf/2606.04438v2)

16. [SMELT: Scaling Laws for Compute-Matched MoE Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2609.01343v2-smelt-scaling-laws-for-compute-matched-moe-looped-transformers) · 专题
   - 阅读理由：SMELT 在严格预算匹配下拟合缩放律，是循环 MoE 扩展的代表性证据。
   - 公布时间：2026-09-01（日精度）
   - arxiv · 2026-09-01（日精度）：[原文](https://arxiv.org/pdf/2609.01343v1)
   - arxiv · 2026-09-01（日精度）：[原文](https://arxiv.org/pdf/2609.01343v2)

17. [The Surprising Effectiveness of Shared Memory in Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2610.02383v1-the-surprising-effectiveness-of-shared-memory-in-looped-transformers) · 专题
   - 阅读理由：共享记忆机制改变循环 KV 缓存策略并报告质量提升，属缓存方向关键工作。
   - 公布时间：2026-10-01（日精度）
   - arxiv · 2026-10-01（日精度）：[原文](https://arxiv.org/pdf/2610.02383v1)

18. [Looping Deeper Without Growing the KV Cache: Recurrent Depth for Causal Encoder-Decoders](/20251126-20261125-starter-looped-llm-729081/2611.13378v1-looping-deeper-without-growing-the-kv-cache-recurrent-depth-for-causal-encoder-decoders) · 专题
   - 阅读理由：循环因果编码器-解码器实现零轮次 KV 增长，面向生产级服务。
   - 公布时间：2026-11-09（日精度）
   - arxiv · 2026-11-09（日精度）：[原文](https://arxiv.org/pdf/2611.13378v1)

19. [Bridging the Gap Between Latent and Explicit Reasoning with Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2606.31779v2-bridging-the-gap-between-latent-and-explicit-reasoning-with-looped-transformers) · 专题
   - 阅读理由：LOTUS 在 3B 规模桥接潜在与显式思维链，是潜在推理方向的代表。
   - 公布时间：2026-06-30（日精度）
   - arxiv · 2026-06-30（日精度）：[原文](https://arxiv.org/pdf/2606.31779v2) / [PDF](https://arxiv.org/pdf/2606.31779v2)

20. [CART: Context-Anchored Recurrent Transformer -- A Parameter-Efficient Architecture with Learned Stability](/20251126-20261125-starter-looped-llm-729081/2606.01495v2-cart-context-anchored-recurrent-transformer----a-parameter-efficient-architecture-with-learned-stability) · 专题
   - 阅读理由：CART 报告参数对齐下未超过稠密基线的负面结果，对评估循环收益的边界很重要。
   - 公布时间：2026-05-31（日精度）
   - arxiv · 2026-05-31（日精度）：[原文](https://arxiv.org/pdf/2606.01495v2) / [PDF](https://arxiv.org/pdf/2606.01495v2)

## 检索覆盖与论文目录

- 检索窗口：2025-11-26 ~ 2026-11-25（截止 2026-11-26，不含当天）
- 最终入选：50 篇（精读区 50 篇 · 速读区 0 篇）
- 研究需求：查找使用了循环 Transformer（looped transformer）架构的大语言模型相关论文。 原始语义意图（必须保留已有的全部限定，仅在原需求内收窄）： large language models built with looped transformer architectures language models that reuse transformer layers in loops Papers that study looped transformer architectures for large language models Papers that train large language models with looped transformer layers and shared parameters across recurrent steps. 本次研究限定（方法或技术）：先ccf-a论文、技术报告 请生成符合原始语义意图及本次限定的英文检索词和语义查询，关键词最多4个，应体现正向限定条件，不要仅重复原来的宽泛方向，也不得丢掉原有范围限定。排除要求保留为评审语义，不宣称执行关键词NOT过滤。
- 本次细化：先ccf-a论文、技术报告
- 缺失会议库存：eccv 2025、emnlp 2026

# 日报 · looped-llm · 大礼包 (2025-11-26 ~ 2026-11-25)

- 最近生成时间：2026-11-26T15:23:13.410356+00:00
- 今日累计更新：1 次
- 今日累计推荐总数：50
- 精读区：50
- 速读区：0

## 精读区
1. [Simply Stabilizing the Loop via Fully Looped Transformer](/20251126-20261125-starter-looped-llm-729081/2605.18797v2-simply-stabilizing-the-loop-via-fully-looped-transformer) （10.0/10）
2. [A Dual-Path Architecture for Scaling Compute and Capacity in LLMs](/20251126-20261125-starter-looped-llm-729081/2605.30202v1-a-dual-path-architecture-for-scaling-compute-and-capacity-in-llms) （10.0/10）
3. [CART: Context-Anchored Recurrent Transformer -- A Parameter-Efficient Architecture with Learned Stability](/20251126-20261125-starter-looped-llm-729081/2606.01495v2-cart-context-anchored-recurrent-transformer----a-parameter-efficient-architecture-with-learned-stability) （10.0/10）
4. [Shared Weights, Selected Computations: How Looped Transformers Route What Each Loop Does](/20251126-20261125-starter-looped-llm-729081/2609.39892v1-shared-weights-selected-computations-how-looped-transformers-route-what-each-loop-does) （10.0/10）
5. [Closing the Loop: Practical Training Recipes for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2610.00673v1-closing-the-loop-practical-training-recipes-for-looped-language-models) （10.0/10）
6. [Deeper Backpropagation or More Updates? Training Looped Language Models Across Budgets](/20251126-20261125-starter-looped-llm-729081/2610.38422v1-deeper-backpropagation-or-more-updates-training-looped-language-models-across-budgets) （10.0/10）
7. [Dory1.0-4B: A Looped Normalized-GPT](/20251126-20261125-starter-looped-llm-729081/2611.03998v1-dory10-4b-a-looped-normalized-gpt) （10.0/10）
8. [Reasoning with Latent Thoughts: On the Power of Looped Transformers](/conference/iclr-2025/openreview-iclr-2025-din0lgfzfd-reasoning-with-latent-thoughts-on-the-power-of-looped-transformers) （10.0/10）
9. [Loop as a Bridge: Can Looped Transformers Truly Link Representation Space and Natural Language Outputs?](/20251126-20261125-starter-looped-llm-729081/2601.10242v1-loop-as-a-bridge-can-looped-transformers-truly-link-representation-space-and-natural-language-outputs) （9.0/10）
10. [LoopFormer: Elastic-Depth Looped Transformers for Latent Reasoning via Shortcut Modulation](/20251126-20261125-starter-looped-llm-729081/2602.11451v1-loopformer-elastic-depth-looped-transformers-for-latent-reasoning-via-shortcut-modulation) （9.0/10）
11. [Adaptive Loops and Memory in Transformers: Think Harder or Know More?](/20251126-20261125-starter-looped-llm-729081/2603.08391v3-adaptive-loops-and-memory-in-transformers-think-harder-or-know-more) （9.0/10）
12. [Loop, Think, & Generalize: Implicit Reasoning in Recurrent-Depth Transformers](/20251126-20261125-starter-looped-llm-729081/2604.07822v2-loop-think--generalize-implicit-reasoning-in-recurrent-depth-transformers) （9.0/10）
13. [Parcae: Scaling Laws For Stable Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.12946v1-parcae-scaling-laws-for-stable-looped-language-models) （9.0/10）
14. [How Much Is One Recurrence Worth? Iso-Depth Scaling Laws for Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2604.21106v3-how-much-is-one-recurrence-worth-iso-depth-scaling-laws-for-looped-language-models) （9.0/10）
15. [Hyperloop Transformers](/20251126-20261125-starter-looped-llm-729081/2604.21254v3-hyperloop-transformers) （9.0/10）
16. [Sparse Layers are Critical to Scaling Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2605.09165v2-sparse-layers-are-critical-to-scaling-looped-language-models) （9.0/10）
17. [LT2: Linear-Time Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2605.20670v2-lt2-linear-time-looped-transformers) （9.0/10）
18. [LoopMoE: Unifying Iterative Computation with Mixture-of-Experts for Language Modeling](/20251126-20261125-starter-looped-llm-729081/2606.04438v2-loopmoe-unifying-iterative-computation-with-mixture-of-experts-for-language-modeling) （9.0/10）
19. [On the Residual Scaling of Looped Transformers: Stability and Transferability](/20251126-20261125-starter-looped-llm-729081/2606.18524v1-on-the-residual-scaling-of-looped-transformers-stability-and-transferability) （9.0/10）
20. [Dense Supervision Is Not Enough: The Readout Blind Spot in Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2606.24898v1-dense-supervision-is-not-enough-the-readout-blind-spot-in-looped-language-models) （9.0/10）
21. [Bridging the Gap Between Latent and Explicit Reasoning with Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2606.31779v2-bridging-the-gap-between-latent-and-explicit-reasoning-with-looped-transformers) （9.0/10）
22. [DeepLoop: Depth Scaling for Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2607.13491v2-deeploop-depth-scaling-for-looped-transformers) （9.0/10）
23. [Looped Transformers with Source-Centered State Evolution](/20251126-20261125-starter-looped-llm-729081/2607.27656v1-looped-transformers-with-source-centered-state-evolution) （9.0/10）
24. [LoopMTP: A looped transformer guided by latent multi-token prediction](/20251126-20261125-starter-looped-llm-729081/2608.03624v1-loopmtp-a-looped-transformer-guided-by-latent-multi-token-prediction) （9.0/10）
25. [Retrofitting Recurrent Depth into a Pretrained Language Model: Installation, Extrapolation, Transfer, and Retention at Two Parameter Budgets](/20251126-20261125-starter-looped-llm-729081/2608.11233v1-retrofitting-recurrent-depth-into-a-pretrained-language-model-installation-extrapolation-transfer-and-retention-at-two-parameter-budgets) （9.0/10）
26. [Allocating Recurrent Compute in Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2608.18230v1-allocating-recurrent-compute-in-looped-language-models) （9.0/10）
27. [SMELT: Scaling Laws for Compute-Matched MoE Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2609.01343v2-smelt-scaling-laws-for-compute-matched-moe-looped-transformers) （9.0/10）
28. [T-LoopFormer: Token-Level Elastic-Depth Looped Transformers for Latent Reasoning With Dynamic Routing](/20251126-20261125-starter-looped-llm-729081/2609.15160v1-t-loopformer-token-level-elastic-depth-looped-transformers-for-latent-reasoning-with-dynamic-routing) （9.0/10）
29. [The Surprising Effectiveness of Shared Memory in Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2610.02383v1-the-surprising-effectiveness-of-shared-memory-in-looped-transformers) （9.0/10）
30. [Towards Looped Models Done Right, Part I: Topology, Input Injection, Recurrent-State Design](/20251126-20261125-starter-looped-llm-729081/2610.23036v1-towards-looped-models-done-right-part-i-topology-input-injection-recurrent-state-design) （9.0/10）
31. [Truncate or Not? A Scaling Study of Looped Transformers with Truncated Backpropagation](/20251126-20261125-starter-looped-llm-729081/2610.26030v2-truncate-or-not-a-scaling-study-of-looped-transformers-with-truncated-backpropagation) （9.0/10）
32. [Asymmetric Looped Transformers: Fixed Global Representations for an Iterative Decoder](/20251126-20261125-starter-looped-llm-729081/2610.28489v1-asymmetric-looped-transformers-fixed-global-representations-for-an-iterative-decoder) （9.0/10）
33. [LSTM-Style Looped Transformers with Shared KV Caches](/20251126-20261125-starter-looped-llm-729081/2610.33360v1-lstm-style-looped-transformers-with-shared-kv-caches) （9.0/10）
34. [One Model, Two Paths: Balancing Single-Pass and Looped Performance in Language Models](/20251126-20261125-starter-looped-llm-729081/2610.33517v1-one-model-two-paths-balancing-single-pass-and-looped-performance-in-language-models) （9.0/10）
35. [StateLoop: Persistent State for Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2610.35544v1-stateloop-persistent-state-for-looped-transformers) （9.0/10）
36. [LoopFold: Parallelizing Recurrent Depth in Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2610.35556v1-loopfold-parallelizing-recurrent-depth-in-looped-transformers) （9.0/10）
37. [How to Loop Your Transformer: Loop Scaling, Specialization, and Parallel Inference](/20251126-20261125-starter-looped-llm-729081/2610.40325v1-how-to-loop-your-transformer-loop-scaling-specialization-and-parallel-inference) （9.0/10）
38. [UpLoop: Training Looped Transformers via Upcycling at No Extra Pretraining Compute](/20251126-20261125-starter-looped-llm-729081/2610.41720v1-uploop-training-looped-transformers-via-upcycling-at-no-extra-pretraining-compute) （9.0/10）
39. [ARLoop: Fully-Open Pre-trained Looped Transformers with Attention Residuals](/20251126-20261125-starter-looped-llm-729081/2611.05234v1-arloop-fully-open-pre-trained-looped-transformers-with-attention-residuals) （9.0/10）
40. [Loopback Transformer: Towards a Unified View of Residual Looped Transformers](/20251126-20261125-starter-looped-llm-729081/2611.07226v1-loopback-transformer-towards-a-unified-view-of-residual-looped-transformers) （9.0/10）
41. [Looping Deeper Without Growing the KV Cache: Recurrent Depth for Causal Encoder-Decoders](/20251126-20261125-starter-looped-llm-729081/2611.13378v1-looping-deeper-without-growing-the-kv-cache-recurrent-depth-for-causal-encoder-decoders) （9.0/10）
42. [Rectified Looped Transformer](/20251126-20261125-starter-looped-llm-729081/2611.16265v2-rectified-looped-transformer) （9.0/10）
43. [Architectures and KV Replay for Depth-Recurrent Language Models](/20251126-20261125-starter-looped-llm-729081/2611.19446v1-architectures-and-kv-replay-for-depth-recurrent-language-models) （9.0/10）
44. [Loop-Count Schedules in Looped Transformers: An Empirical Study](/20251126-20261125-starter-looped-llm-729081/2611.29704v1-loop-count-schedules-in-looped-transformers-an-empirical-study) （9.0/10）
45. [Unlocking the Power of Loops in Pretrained LLMs with Loop Residuals](/20251126-20261125-starter-looped-llm-729081/2611.31094v2-unlocking-the-power-of-loops-in-pretrained-llms-with-loop-residuals) （9.0/10）
46. [Learning from Recurrence: Internalizing Depth-Induced Preferences in Looped Language Models](/20251126-20261125-starter-looped-llm-729081/2611.33468v1-learning-from-recurrence-internalizing-depth-induced-preferences-in-looped-language-models) （9.0/10）
47. [Scaling Looped MoE Language Models under Matched Budgets: Information Flow and Parameter Allocation](/20251126-20261125-starter-looped-llm-729081/2611.34276v1-scaling-looped-moe-language-models-under-matched-budgets-information-flow-and-parameter-allocation) （9.0/10）
48. [Mixture-of-Loops Transformer](/20251126-20261125-starter-looped-llm-729081/2611.34923v1-mixture-of-loops-transformer) （9.0/10）
49. [Relaxed Recursive Transformers: Effective Parameter Sharing with Layer-wise LoRA](/conference/iclr-2025/openreview-iclr-2025-wwpysokkct-relaxed-recursive-transformers-effective-parameter-sharing-with-layer-wise-lora) （9.0/10）
50. [Mixture-of-Recursions: Learning Dynamic Recursive Depths for Adaptive Token-Level Computation](/conference/neurips-2025/openreview-neurips-2025-quqseivwig-mixture-of-recursions-learning-dynamic-recursive-depths-for-adaptive-token-level-computation) （9.0/10）

## 速读区
- 本次无速读推荐。

---
使用键盘方向键可在日报/论文之间快速切换。
