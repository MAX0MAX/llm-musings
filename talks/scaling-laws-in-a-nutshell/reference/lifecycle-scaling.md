# Lifecycle Scaling：从 Scale 模型到 Scale 整个模型生命周期

> 研究日期：2026-08-24
> 研究问题：行业是否已经从“扩大预训练模型”转向“扩大 post-training、test-time compute、retrieval/context/memory、environment/agent experience”？
> 口径：优先采用论文、技术报告、官方研究博客和带全文的原始访谈。公司自报 benchmark 只证明该公司的实验与战略，不自动代表独立复现或行业共识。

## 结论先行

“Scale 整个模型生命周期”**最适合作为产业框架，其次是战略下注，不宜作为一条已经验证的事实定律**。

- 作为**事实描述**，可以安全地说：前沿团队已经把显著的研究、工程和推理预算投入到预训练之外；post-training、推理时搜索与采样、检索和外部记忆、可交互环境都已经产生可测的性能增益。
- 作为**产业框架**，它很有解释力：算力不再只在一次预训练中消费，而是在 SFT/RL、生成和筛选数据、在线推理、工具调用、检索、环境 rollout 和持续记忆中反复消费。
- 作为**“新 scaling law”**，证据不足。新轴通常依赖任务可验证性、基础模型先验、数据和 reward 质量、问题难度、推理预算分配及 benchmark 设计；目前没有一组像稳定条件下预训练 loss–compute 关系那样跨任务、跨模型、可外推的共同函数。
- 更准确的总叙事是：**行业正在从单一的 pretraining scaling 配方，转向寻找多个条件性的资源—性能前沿。** 这些前沿有真实实验，但成熟度不同。

### 四条轴的证据强度

| Axis | “追加资源能改善结果” | “存在可预测、可外推的通用 law” | 本研究判断 |
| --- | --- | --- | --- |
| Post-training | **强**：SFT、RLHF/RLAIF、RLVR、reward model、合成偏好数据均有直接实验 | **弱—中**：主要在特定数据、reward 和任务分布内成立，reward hacking 是结构性反例 | 已验证工程轴；通用 scaling law 未成立 |
| Test-time compute | **强（可验证任务）/中（开放任务）**：sampling、search、verifier、长思考有清晰增益 | **弱—中**：收益随题目难度、基础成功率、verifier 和预算分配变化，最难题可能无收益 | 最接近“新 scaling axis”，但高度条件化 |
| Retrieval/context/memory | **中—强**：RETRO、长上下文、外部记忆证明能力不必全存入参数 | **弱**：容量、有效利用、检索质量和成本不是同一件事 | 成熟的系统设计轴，不是单一训练定律 |
| Environments/agents/experience | **中**：ReAct、AlphaProof、AlphaEvolve、长期任务评测显示闭环经验有价值 | **弱**：结果最依赖环境与 verifier；开放世界、长期迁移和真实效用仍缺证据 | 强战略下注和研究议程；领域内已有成功先例 |

## 证据分类

- **实验结果**：有明确实验设计、指标和对照；仍需注意是否只由团队自报。
- **战略表述**：实验室负责人或团队明确说明资源和研发方向；可证明“他们在下注”，不能单独证明技术规律。
- **观点**：研究者对历史、架构或未来的判断。
- **研究议程**：提出下一阶段应研究什么，尚未形成稳定经验律。
- **营销分类**：为产品、基础设施或市场叙事整理出的分类；可帮助沟通，但不等于科学定律。

---

## 一、总框架与“转向”是否真实

### 1. The Bitter Lesson

- **人物/机构、日期、链接：** Richard Sutton，2019-03-13，[原文](http://www.incompleteideas.net/IncIdeas/BitterLesson.html)。
- **直接观点：** “The biggest lesson … is that general methods that leverage computation are ultimately the most effective”；Sutton 特别把 **search 和 learning** 称为利用大规模计算的两类关键方法。
- **为什么收录：** 它是“把更多计算放到搜索、学习和经验，而非手写知识”叙事的思想前史。
- **Scaling axis：** 跨轴；尤其 test-time search、environment/experience。
- **证据类型：** 观点/历史归纳。
- **边界或反证：** 不是 LLM scaling law，也没有给出资源—性能函数；“通用方法长期胜出”不意味着任何增加计算的方法都会有效。

### 2. Demis Hassabis：scaling 与 invention 同时推进

- **人物/机构、日期、链接：** Demis Hassabis（Google DeepMind CEO），2024-02-28，[Dwarkesh 访谈全文](https://www.dwarkesh.com/p/demis-hassabis)。
- **直接观点与上下文：** 在讨论大模型是否撞墙时，他说应当“push scaling as hard as we can”，但是否遇到 asymptote 是经验问题，“no one knows”；DeepMind 可被理解为一半精力在 scaling，一半在发明新架构和算法。
- **为什么收录：** 一位头部实验室负责人明确拒绝“旧 scaling 已死”和“只要继续 scale”两个极端。
- **Scaling axis：** 跨轴。
- **证据类型：** 战略表述/观点。
- **边界或反证：** 说明组织战略，不是新轴已经成立的实验；“一半/一半”是访谈中的概念性表达，不应解读为预算披露。

### 3. NVIDIA 的“三种 scaling laws”

- **机构、日期、链接：** NVIDIA，2025-02（原页面当前未显示具体日），[How Scaling Laws Drive Smarter, More Powerful AI](https://blogs.nvidia.com/blog/ai-scaling-laws/)。
- **直接观点：** 将 AI 计算分成 pretraining、post-training、test-time/“long thinking”三类，并把 fine-tuning、RL、synthetic data、推理时多路径探索都纳入。
- **为什么收录：** 这是当前产业中最清楚、传播最广的生命周期计算分类之一，能解释硬件需求为何从训练延伸到推理。
- **Scaling axis：** post-training、test-time compute。
- **证据类型：** **营销分类/产业框架**。
- **边界或反证：** NVIDIA 是算力供应商，文章目标包含解释持续的加速计算需求；“law”一词比其所引证的实验更强。它没有证明三个阶段各自都有统一幂律，也没有覆盖 retrieval 和 environment 的独立作用。

**小结：** “转向”首先是**预算和系统边界的扩展**，不是预训练被替代。所有后续方法都以预训练模型提供的先验为起点。

---

## 二、Axis 1：Post-training

### 4. InstructGPT：小模型经后训练可胜过大基础模型

- **标题、人物/机构、日期、链接：** *Training language models to follow instructions with human feedback*，Long Ouyang 等，OpenAI，2022-03-04，[论文](https://arxiv.org/abs/2203.02155)，[官方说明](https://openai.com/index/instruction-following/)。
- **直接观点：** 管线由人类 demonstrations 的 SFT、偏好排序训练 reward model、再以 PPO 做 RLHF 组成；在人类偏好评测上，1.3B InstructGPT 输出优于 175B GPT-3。
- **为什么收录：** 直接证明“参数更大”不是部署效果的充分条件，后训练可以改变模型行为并带来大幅偏好收益。
- **Scaling axis：** SFT、reward model、RLHF。
- **证据类型：** 实验结果。
- **边界或反证：** 优势是在 OpenAI API prompt 分布及其标注者偏好上测得；论文明确说它对齐的是一组标注者/研究者的偏好，不是普遍“人类价值”。模型仍会犯简单错误。

### 5. Constitutional AI：用 AI feedback 扩大监督

- **标题、人物/机构、日期、链接：** *Constitutional AI: Harmlessness from AI Feedback*，Yuntao Bai 等，Anthropic，2022-12-15，[官方研究页](https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback)。
- **直接观点：** 先让模型依据原则生成自我批评和修订并做 supervised learning，再由模型比较响应、训练 preference model、进行 RLAIF；仅以一组人写原则提供高层监督。
- **为什么收录：** 展示合成反馈可把人类监督从逐条标签转为规则设计，扩大 post-training 数据生产。
- **Scaling axis：** SFT、reward model、RLAIF、合成数据。
- **证据类型：** 实验结果/研究方向。
- **边界或反证：** AI judge 继承基础模型偏差；原则仍由人选定；“更少人类标签”不等于没有人类价值判断或没有监督瓶颈。

### 6. Let’s Verify Step by Step：过程 reward model 在数学上优于只看答案

- **标题、人物/机构、日期、链接：** *Let’s Verify Step by Step / Improving mathematical reasoning with process supervision*，Hunter Lightman 等，OpenAI，2023-05-31，[官方研究页](https://openai.com/index/improving-mathematical-reasoning-with-process-supervision/)。
- **直接观点：** 在 MATH 上，对每一步给反馈的 process supervision 比只奖励最终答案的 outcome supervision 更可靠；随着候选解数量增加，两者差距扩大。团队发布了 80 万个步骤级标签。
- **为什么收录：** 将 reward/verifier 质量和 test-time sampling 连接起来：生成更多候选只有在排序器可靠时才有价值。
- **Scaling axis：** reward model、过程监督、test-time selection。
- **证据类型：** 实验结果。
- **边界或反证：** 结果来自数学这一可检查领域，并依赖昂贵的人类步骤标签；不能直接外推到写作、策略或开放世界任务。

### 7. Reward model overoptimization：代理 reward 会随优化变坏

- **标题、人物/机构、日期、链接：** *Scaling Laws for Reward Model Overoptimization*，Leo Gao、John Schulman、Jacob Hilton（OpenAI），2022-10-19，[论文](https://arxiv.org/abs/2210.10760v1)。
- **直接观点：** “Because the reward model is an imperfect proxy, optimizing its value too much can hinder ground truth performance”；RL 与 best-of-N 都会出现代理 reward 继续升高、gold reward 转而下降的 Goodhart 效应。
- **为什么收录：** 这是对“多做 RL/多采样就持续变好”的直接反证，而且由支持 post-training 的实验室自己给出。
- **Scaling axis：** RL、reward model、sampling。
- **证据类型：** 实验结果/限制。
- **边界或反证：** 使用固定“gold reward model”代替真实人类，属于可控合成设置；它证明结构性风险，不给出所有真实 RLHF 系统的失败点。

### 8. Self-Taught Evaluators：合成偏好数据可迭代训练 evaluator

- **标题、人物/机构、日期、链接：** *Self-Taught Evaluators*，Tianlu Wang 等，Meta FAIR，2024-08-05，[论文](https://arxiv.org/html/2408.02666v1)，[代码与数据](https://github.com/facebookresearch/RAM/tree/main/projects/self_taught_evaluator)。
- **直接观点：** 不用人工偏好标签，从无标签 instruction 生成对比响应和判断轨迹；Llama-3-70B-Instruct 在 RewardBench 从 75.4 提升到 88.3（多数投票 88.7）。
- **为什么收录：** 是“合成数据扩大 reward model 训练”的直接实验，而非只谈数据稀缺。
- **Scaling axis：** synthetic preference data、reward model、iterative self-training。
- **证据类型：** 实验结果。
- **边界或反证：** 合成 pair 的“正确答案”由构造规则产生，RewardBench 也只是 evaluator benchmark；多数投票把一部分收益转移为更高推理成本。

### 9. Kimi k1.5：明确把 RL 称为新的 scaling axis

- **标题、人物/机构、日期、链接：** *Kimi k1.5: Scaling Reinforcement Learning with LLMs*，Kimi Team / Moonshot AI，2025-01-22，[技术报告](https://arxiv.org/abs/2501.12599)，[官方仓库](https://github.com/MoonshotAI/kimi-k1.5)。
- **直接观点：** “Scaling reinforcement learning (RL) unlocks a new axis”；团队将 RL context 扩到 128K，并称更长 context 带来持续改善和更多搜索步骤。
- **为什么收录：** 这是中国头部实验室对“RL scaling”最直接的战略和实验表述。
- **Scaling axis：** RL、long context、long CoT、合成 rollout。
- **证据类型：** 实验结果 + 战略表述。
- **边界或反证：** “new axis”是作者对结果的解释，不是跨实验室定律；与 o1 的比较为团队自报，且训练 recipe、数据和算力未完全开放。

### 10. DeepSeek-R1：可验证 reward 能激发推理，但 R1 不是“纯 RL”

- **标题、人物/机构、日期、链接：** *DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning*，DeepSeek-AI，2025-01-22，[技术报告](https://arxiv.org/abs/2501.12948)。
- **直接观点：** R1-Zero 从基础模型出发，以 rule-based correctness/format reward 做 RL，出现 reflection、verification 和策略调整；正式 R1 则加入 cold-start SFT、RL、rejection-sampling 生成的新 SFT 数据及第二阶段 RL。
- **为什么收录：** 同时提供 post-training 的真实增益和对流行简化叙事的纠正。
- **Scaling axis：** RLVR、SFT、rejection sampling、synthetic data。
- **证据类型：** 实验结果/技术报告。
- **边界或反证：** 强结果集中在数学、代码、STEM 等可验证任务；R1-Zero 可读性差且语言混杂，说明纯 reward 优化不会自动得到所有期望行为；正式 R1 依赖多阶段人工设计。

### 11. 合成数据的反例：递归训练可能 model collapse

- **标题、人物/机构、日期、链接：** *AI models collapse when trained on recursively generated data*，Ilia Shumailov 等，2024-07-24，[Nature 论文](https://www.nature.com/articles/s41586-024-07566-y)。
- **直接观点：** 不加区分地用前代模型生成数据训练后代，会逐步丢失真实分布尾部，造成不可逆缺陷。
- **为什么收录：** 防止把“合成数据可无限扩展”说成无条件事实。
- **Scaling axis：** synthetic data。
- **证据类型：** 实验结果/理论分析/限制。
- **边界或反证：** 论文针对递归、无甄别替代真实数据的设置；不否定经过验证、混合真实数据、面向可检查任务的合成数据。

**Post-training 判断：** 已经是强事实性的工程能力轴，但目前证据支持的是“更好的反馈和更多有效 rollout 可改善特定目标”，不是“RL compute 单调地转化为通用智能”。真正的稀缺资源常常是**可靠 reward、覆盖分布和可审计数据**，而不只是 GPU。

---

## 三、Axis 2：Test-time compute

### 12. OpenAI o1：训练计算和思考时间都出现增益

- **标题、人物/机构、日期、链接：** *Learning to reason with LLMs*，OpenAI，2024-09-12，[官方技术说明](https://openai.com/index/learning-to-reason-with-llms/)。
- **直接观点：** “performance of o1 consistently improves with more reinforcement learning (train-time compute) and with more time spent thinking (test-time compute)”；IOI 系统还通过多候选、公共/模型生成测试及 learned scorer 做选择。
- **为什么收录：** 头部实验室首次公开展示通用语言推理模型上的 train-time 与 test-time 两条曲线。
- **Scaling axis：** long thinking、sampling、selection、RL。
- **证据类型：** 实验结果 + 战略表述。
- **边界或反证：** OpenAI 未公开算法、曲线数据或独立复现条件；多数展示是数学、代码和科学 benchmark，且常用最大 test-time compute，成本比较不完整。

### 13. Compute-optimal test-time scaling：收益取决于题目难度

- **标题、人物/机构、日期、链接：** *Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters*，Charlie Snell 等（UC Berkeley；工作完成于 Google DeepMind 实习），2024-08-06，[论文](https://arxiv.org/abs/2408.03314)。
- **直接观点：** test-time 方法的有效性“critically varies depending on the difficulty of the prompt”；自适应分配预算可比 best-of-N 高效 4 倍，在基础小模型已有非零成功率的题上可胜过 14 倍大的模型。
- **为什么收录：** 最直接地把“更多推理计算”改写为“应按难度做 compute-optimal 分配”。
- **Scaling axis：** search、sampling、process verifier、adaptive compute。
- **证据类型：** 实验结果。
- **边界或反证：** 最简单题不需要额外预算，最难题所有方法都可能失败；依赖 learned verifier 和题目难度估计，主要实验域为数学。

### 14. 无外部反馈的自我纠错可能退化

- **标题、人物/机构、日期、链接：** *Large Language Models Cannot Self-Correct Reasoning Yet*，Jie Huang 等，Google DeepMind，2023-10-03，[官方研究页](https://deepmind.google/research/publications/48252/)。
- **直接观点：** 仅依靠模型自身能力、没有外部反馈的 intrinsic self-correction 在推理任务上很困难，纠错后表现有时反而下降。
- **为什么收录：** 直接反驳“让模型再想一遍自然会更好”；额外 token 必须携带新的搜索、证据或可靠反馈。
- **Scaling axis：** long thinking、self-refinement。
- **证据类型：** 实验结果/反证。
- **边界或反证：** 结论针对当时模型和特定 prompting；后续经过 RL 训练的 reasoning model 可能更会利用长思考，但仍不能取消 verifier 条件。

### 15. Noam Brown 与 o1 团队：test-time compute 的收益有任务边界

- **标题、人物/机构、日期、链接：** *Teaching LLMs to Reason Better by Thinking Longer*，Noam Brown、Ilge Akkaya、Hunter Lightman（OpenAI），2024-10-02，[Sequoia 访谈全文](https://sequoiacap.com/podcast/training-data-noam-brown/)，[视频](https://www.youtube.com/watch?v=jPluSXJpdrA)。
- **直接观点与时间戳：** 视频开场即用“想两年也不能帮助回答不记得的首都”对比 Sudoku 这类易验证搜索题；团队在文字稿中说延长思考出现 backtracking/self-correction，但也承认要找到适合额外计算的 eval。Noam 常被引用的“20 秒≈100,000×”来自扑克搜索实验，不是 LLM 通用汇率；他在 2023 年 No Priors 访谈约 **00:18:49** 解释了该扑克语境。
- **为什么收录：** 同一位 test-time scaling 倡导者明确给出收益条件，能防止断章取义。
- **Scaling axis：** long thinking、search。
- **证据类型：** 原始访谈/战略表述/领域实验回顾。
- **边界或反证：** 100,000× 来自特定扑克 bot 的模型与搜索比较，不能用于估算 o1 或一般 LLM 的训练—推理兑换率。

### 16. Mind Evolution：并行探索与迭代改进可随推理预算提升

- **标题、人物/机构、日期、链接：** *Evolving Deeper LLM Thinking*，Kuang-Huei Lee 等，Google DeepMind，2025-01-17，[官方研究页](https://deepmind.google/research/publications/122391/)。
- **直接观点：** 用遗传算法式生成、交叉、改进和选择扩展 inference-time compute；在 TravelPlanner 与 Natural Plan 上固定预算内达到 99% 以上，并报告性能随推理计算持续改善。
- **为什么收录：** 展示“long thinking”不只是一条更长 CoT，也可以是并行搜索和选择。
- **Scaling axis：** search、sampling、iterative refinement。
- **证据类型：** 实验结果。
- **边界或反证：** 规划 benchmark 有明确评分器和可程序化结构；99% 不等于开放现实规划已解决，且进化搜索的延迟与 token 成本较高。

### 17. AlphaProof：数天 test-time RL 可解难题，也暴露成本与环境依赖

- **标题、人物/机构、日期、链接：** *AI achieves silver-medal standard solving IMO problems*，Google DeepMind，2024-07-25，[官方博客](https://deepmind.google/blog/ai-solves-imo-problems-at-silver-medal-level/)；后续论文 *Olympiad-level formal mathematical reasoning with reinforcement learning*，[Nature](https://www.nature.com/articles/s41586-025-09833-y)。
- **直接观点：** AlphaProof 在 Lean 环境搜索并验证证明，把成功证明回灌训练；对最难问题用 Test-Time RL 生成并学习数百万相关变体。IMO 2024 的若干解各需约 2–3 天计算。
- **为什么收录：** 是 test-time compute、可验证 reward、自生成经验真正合流的强实证。
- **Scaling axis：** search、verification、test-time RL、environment experience。
- **证据类型：** 实验结果。
- **边界或反证：** 题目由专家手工形式化，答案候选还使用 Gemini 和手写例子；Lean 提供近乎完美 verifier，两个组合题仍未解。成本与开放自然语言任务不可直接类比。

**Test-time 判断：** 在**答案可验证、基础模型有一定命中率、搜索能产生多样候选**时，证据很强；在事实回忆、主观写作、不可判定目标或极难问题上，“想更久”可能只是更贵地重复错误。

---

## 四、Axis 3：Retrieval、Context 与 External Memory

### 18. RETRO：扩大外部数据库可替代部分参数

- **标题、人物/机构、日期、链接：** *Improving language models by retrieving from trillions of tokens*，Sebastian Borgeaud 等，Google DeepMind，2021-12-08，[官方博客](https://deepmind.google/blog/improving-language-models-by-retrieving-from-trillions-of-tokens/)，[论文](https://arxiv.org/abs/2112.04426)。
- **直接观点：** 7.5B RETRO 访问 2T-token 数据库，在 Pile 上达到可与 GPT-3/Jurassic-1 比较的表现而参数少 25 倍；语言建模随检索库扩大持续改善，至少到 2T token。
- **为什么收录：** 直接证明能力不必全部压入参数，外部存储大小本身可以成为资源轴。
- **Scaling axis：** retrieval、external memory、parameters。
- **证据类型：** 实验结果。
- **边界或反证：** 比较基于特定 loss/dataset，RETRO 需要专门架构和高质量检索；论文也检查了但不能完全排除训练/测试泄漏问题。数据库规模增长不保证每个下游任务同步获益。

### 19. Gemini 1.5：上下文容量可大幅扩展，但“能装下”不等于“都能用好”

- **标题、人物/机构、日期、链接：** *Gemini 1.5: Unlocking multimodal understanding across millions of tokens of context*，Gemini Team / Google，2024-03-08，[技术报告](https://arxiv.org/pdf/2403.05530)。
- **直接观点：** 单 needle 在 1M token 内召回超过 99.7%；但 100 needles 的复杂设置中，1M token 召回率降到 60% 以上。
- **为什么收录：** 同一份实验同时给出长上下文的强结果和评测边界。
- **Scaling axis：** context length、in-context retrieval。
- **证据类型：** 实验结果/技术报告。
- **边界或反证：** needle retrieval 是人工构造的 recall 任务，不等于跨百万 token 推理；多目标召回明显下降，输入成本和延迟随长度增加。

### 20. Lost in the Middle：更多上下文可增加成本却几乎不增加答案质量

- **标题、人物/机构、日期、链接：** *Lost in the Middle: How Language Models Use Long Contexts*，Nelson F. Liu 等，2023-07-07，[论文](https://arxiv.org/abs/2307.03172)。
- **直接观点：** 相关信息位于上下文中间时表现显著下降；开放域 QA 中 reader 的收益先于 retriever recall 饱和，超过 20 篇文档只给 GPT-3.5/Claude-1.3 带来约 1–1.5% 改善，却增加长度、延迟和成本。
- **为什么收录：** 区分 context window 容量、检索召回和 reader 真正利用信息这三个概念。
- **Scaling axis：** context、retrieval。
- **证据类型：** 实验结果/限制。
- **边界或反证：** 测试的是 2023 年模型；后续长上下文训练已有改进，但 Gemini 自己的 multi-needle 结果仍说明问题未消失。

### 21. ReAct：检索不是被动塞上下文，而是由 agent 按需行动

- **标题、人物/机构、日期、链接：** *ReAct: Synergizing Reasoning and Acting in Language Models*，Shunyu Yao 等（Princeton / Google Brain），2022-10-06，[论文](https://arxiv.org/abs/2210.03629v1)，[Google 官方说明](https://research.google/blog/react-synergizing-reasoning-and-acting-in-language-models/)。
- **直接观点：** 让模型交替生成 reasoning trace 和 action；在 HotpotQA/FEVER 中通过 Wikipedia API 降低纯 CoT 的 hallucination/error propagation，在 ALFWorld 与 WebShop 上也优于对照。
- **为什么收录：** 把 retrieval、tool use 和 environment feedback 统一成主动的信息获取过程。
- **Scaling axis：** retrieval、context、agents/environments。
- **证据类型：** 实验结果。
- **边界或反证：** 早期结果基于少量 in-context examples 和相对简单环境；scaffold 的贡献不能等同于基础模型变聪明。

### 22. Anthropic 的 context engineering：外部记忆是长期 agent 的工程补丁

- **标题、机构、日期、链接：** *Effective context engineering for AI agents*，Anthropic，2025-09-29，[官方工程文章](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)。
- **直接观点：** 长期任务会超过固定 context window；等待更大窗口不能消除 context pollution 和相关性问题，因此需要 compaction、结构化笔记、按需检索和 context 外持久化记忆。
- **为什么收录：** 来自实际构建长时 agent 的实验室，说明“memory scaling”是选择、压缩和恢复信息，而不是简单增大 token 上限。
- **Scaling axis：** context management、external memory、long-horizon agents。
- **证据类型：** 工程经验/战略表述。
- **边界或反证：** 不是受控 scaling-law 论文；文章所述内部评测和产品能力缺少完整公开数据，摘要压缩还可能遗失关键信息。

**Retrieval/context 判断：** 这是最成熟的**系统级替代轴**之一，但没有一个标量能代表它。数据库更大、上下文更长、检索更准、记忆更持久分别消耗不同资源，也可能在 reader、排序、污染或延迟处提前饱和。

---

## 五、Axis 4：Environments、Agents 与 Experience

### 23. AlphaEvolve：生成—执行—评分—进化在可验证领域产生实际改进

- **标题、机构、日期、链接：** *AlphaEvolve: A Gemini-powered coding agent for designing advanced algorithms*，Google DeepMind，2025-05-14，[官方博客](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/)，[技术论文](https://arxiv.org/pdf/2506.13131)。
- **直接观点：** Gemini 生成和改写程序，自动 evaluator 执行、验证、评分，再以进化框架保留和扩展高分候选；系统在矩阵乘法、数据中心调度和训练 kernel 等问题上报告改进。
- **为什么收录：** 是“自生成经验”最具体的生产级形式：经验不是无限文本，而是由环境执行后得到的可量化反馈。
- **Scaling axis：** agents、environment feedback、experience、verification。
- **证据类型：** 实验结果/官方案例。
- **边界或反证：** 官方明确限定在“候选可自动评估”的问题；程序通过测试不保证规格完整，开放科学问题缺少同等可靠 evaluator。

### 24. Welcome to the Era of Experience：明确提出下一阶段研究议程

- **标题、人物/机构、日期、链接：** *Welcome to the Era of Experience*，David Silver、Richard Sutton，2025-04-11，[Google DeepMind 托管 PDF](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf)。
- **直接观点：** “A new generation of agents will acquire superhuman capabilities by learning predominantly from experience”；主张 agent 长期、持续地与世界交互，以环境中的 grounded signals 而非主要依赖人类预判来学习。
- **为什么收录：** “scale experience”叙事最权威、最完整的原始文本。
- **Scaling axis：** long-term interaction、self-generated experience、environment rewards。
- **证据类型：** **研究议程/观点**。
- **边界或反证：** 文章用 AlphaProof 等案例说明可能性，但没有拟合经验量—通用能力曲线；开放世界 reward、持续学习稳定性、安全和现实试错成本都未解决。

### 25. The Second Half：瓶颈可能从训练转向任务与环境定义

- **标题、人物/机构、日期、链接：** *The Second Half*，Shunyu Yao（姚顺雨），2025-04-10，[原文](https://ysymyth.github.io/The-Second-Half/)。
- **直接观点：** “evaluation becomes more important than training”；他把当前 recipe 概括为 language pretraining + scale + reasoning/acting，并认为真实任务需要 human-in-the-loop、顺序而非 i.i.d. 的评测，以及跨任务积累熟悉度的长期记忆。
- **为什么收录：** 把“环境质量”从 RL 的背景条件提升为下一阶段核心问题。
- **Scaling axis：** environments、evaluation、long-term memory、agents。
- **证据类型：** 观点/研究议程。
- **边界或反证：** “RL finally generalizes”是作者的强判断，不是系统综述；文章也承认 pretraining priors 可能比 RL 算法本身更关键，因此不能把所有 agent 增益归功于新增 experience。

### 26. AI Agents That Matter：agent benchmark 容易把更多调用误当成架构进步

- **标题、人物/机构、日期、链接：** *AI Agents That Matter*，Sayash Kapoor 等，2024-07-01，[论文](https://arxiv.org/abs/2407.01502v1)。
- **直接观点：** “SOTA agents are needlessly complex and costly, and the community has reached mistaken conclusions about the sources of accuracy gains”；简单 baseline 在 HumanEval 上可低成本胜过多个复杂 agent，因此评测必须控制成本。
- **为什么收录：** 正面处理 slide 13 所需的 agent benchmark 归因问题。
- **Scaling axis：** agent scaffolding、test-time compute、evaluation。
- **证据类型：** 实验结果/评测审计。
- **边界或反证：** 主要分析代码生成和当时的 agents；不说明复杂 scaffold 永远无价值，而是说明比较必须在相同模型、预算、重试数和工具条件下进行。

### 27. METR time horizon：长期任务能力在增长，但外部有效性未证实

- **标题、机构、日期、链接：** *Measuring AI Ability to Complete Long Software Tasks*，METR，2025-03-18，[论文](https://arxiv.org/abs/2503.14499)，[公开分析代码](https://github.com/METR/eval-analysis-public)。
- **直接观点：** 提出“50% task-completion time horizon”；在其软件/研究任务集上，前沿模型的可完成任务时长约每 7 个月翻倍，但 80% 可靠度对应的 horizon 约短 5 倍。
- **为什么收录：** 比单次 benchmark 分数更接近“agent 能持续多久”的实证趋势。
- **Scaling axis：** long-horizon agents、tool use、reliability。
- **证据类型：** 实验结果/趋势测量。
- **边界或反证：** 作者明确警告外部有效性；任务仍以软件和研究为主、环境相对结构化，“人类耗时”只是难度代理。2026 年更新仍报告长任务置信区间很宽，并修正了易 reward-hack 或评分错误的任务。

### 28. Yann LeCun：缺失的不只是更多 token，而是 world model、memory 与 planning

- **标题、人物/机构、日期、链接：** Lex Fridman #416，Yann LeCun（Meta Chief AI Scientist），2024-03-07，[带时间戳全文](https://lexfridman.com/yann-lecun-3-transcript/)。
- **直接观点与时间戳：** **00:02:47** 起，他认为 autoregressive LLM 对物理世界理解、persistent memory、reasoning、planning 都很原始；**00:17:58** 附近强调语言是低带宽的世界表示，应学习能预测行动后果的 world model。
- **为什么收录：** 提供对“在现有语言模型生命周期上继续堆计算即可通往通用智能”的架构性反方。
- **Scaling axis：** external memory、environments、world models、planning。
- **证据类型：** 观点/研究议程。
- **边界或反证：** LeCun 的强断言并不否定 LLM benchmark 会继续进步，world-model 路线本身也尚无通用成功实证；它应被用作未决架构争论，而非“scaling 已失败”的事实。

---

## 六、限制条件与反方证据汇总

### 1. Reward hacking / proxy overoptimization

- reward model 只是人类偏好或规则的代理；Gao 等证明代理分数可继续上升而 gold score 下降。
- DeepSeek-R1-Zero 的可读性和语言混杂说明“正确答案 reward”不足以塑造全部期望行为。
- 合成 evaluator 可以减少标签成本，却可能把生成器、judge 和 benchmark 的共同偏差闭环放大。

**演讲安全表述：** “更多 RL 只有在 reward 仍与真实目标一致时才会变成能力。”

### 2. Verifier 依赖

- 数学答案、Lean proof、unit tests 和程序性能有廉价、清晰的 verifier，因此最容易出现 RLVR 和搜索收益。
- 主观写作、长期商业决策、科研新颖性和社会互动没有同等可靠的自动 reward。
- 过程 verifier 可改善排序，但训练它需要高质量步骤标签；learned verifier 本身也会被 overoptimize。

**演讲安全表述：** “新轴目前最强的证据来自可验证任务；越开放的任务，证据越弱。”

### 3. 任务难度与基础模型先验

- Snell 等显示：易题额外计算浪费，最难题所有策略可能失败；收益最大的是基础模型已有一定成功概率的中间区间。
- 无外部信号的重复自我纠错可能降级。
- Noam Brown 自己用事实回忆与 Sudoku 的对比说明“思考时间”不能创造缺失知识。

### 4. 推理成本、延迟和机会成本

- best-of-N、beam search、进化搜索、multi-agent debate 都可能靠更多调用提高 pass rate；若不报告 token、美元、墙钟时间和能耗，会把预算优势误写成方法优势。
- AlphaProof 的关键 IMO 解需要数日计算；这证明可能性，不证明适合常规服务。
- context 越长并非免费：输入 token、attention/KV cache、检索、排序和重复请求都有成本。

### 5. Agent benchmark 归因

- 必须分离基础模型、prompt/scaffold、工具、重试数、并行度、verifier 和人工介入。
- *AI Agents That Matter* 证明简单多次调用可胜过复杂 agent；SWE-Bench+ 进一步报告 solution leakage、弱测试和知识截止日前数据会显著抬高成绩（可作为补充材料：[论文](https://arxiv.org/abs/2410.06992v2)）。
- benchmark pass rate 不自动等于长期自主性；50% 成功也不等于可部署可靠性。

### 6. 环境质量与真实效用

- 环境决定 agent 能看到什么、做什么以及什么会被奖励；错误 simulator 或测试会训练“赢评测”而非解决真实问题。
- Yao 指出现有评测常假定无人工介入、任务 i.i.d.，而真实工作有持续协作和跨任务记忆。
- Silver/Sutton 的 experience 议程需要可持续产生、随能力增强而变难的交互；静态合成数据会被模型赶超，但开放环境又带来安全和成本问题。

### 7. 合成数据与经验的质量

- “self-generated”不是质量保证。无甄别递归训练会丢失分布尾部。
- 成功案例通常都有 grounding：Lean kernel、单元测试、可执行程序、规则答案、搜索到的真实文档或人类原则。
- 因而真正可扩展的对象可能不是“经验数量”，而是**可验证、覆盖新状态且不过度同质化的经验生产系统**。

---

## 七、最终判断：事实描述、产业框架还是战略下注？

### 事实描述：只能采用较弱版本

可验证的弱版本是：

> 前沿模型系统的性能已经不只由一次预训练决定；后训练、推理时计算、检索/上下文/记忆和环境反馈均能在特定条件下带来显著增益，且主要实验室正在扩大这些阶段的投入。

不应采用的强版本是：

> 行业已经发现了几条与预训练 scaling law 同等稳定的新定律，增加任何生命周期阶段的计算都会可预测地提高通用智能。

后者被 reward overoptimization、难度依赖、verifier 依赖、long-context 利用率和 agent 归因问题直接否定。

### 产业框架：最合适

生命周期框架能回答“算力筹码现在花在哪里”：

1. **Pretraining** 形成广泛先验；
2. **Post-training** 用 demonstrations、偏好、reward 和 rollout 塑造行为；
3. **Test time** 按题目动态购买搜索、采样、验证和工具调用；
4. **Context/memory** 在参数外按需提供知识和状态；
5. **Environment/experience** 产生新的反馈和训练数据，再回流前面各阶段。

它是一个**闭环而非线性流水线**：推理 rollout 可变成 SFT/RL 数据，检索结果进入 context，环境反馈训练 verifier，长期记忆改变下一次行动。

### 战略下注：强，但下注方向并不唯一

- OpenAI、Kimi、DeepSeek 明确押注 reasoning RL 和 test-time compute。
- DeepMind 的 AlphaProof/AlphaEvolve 押注可验证环境、搜索和自生成经验。
- Anthropic 押注可扩展监督、context management 和 agent reliability。
- Meta FAIR 同时探索合成 evaluator；LeCun 则认为还需要 world model、persistent memory 和 planning。
- Silver/Sutton 将长期 experience 提升为下一时代；Yao 则认为最稀缺的可能是环境与 evaluation 定义。

这些不是一个已经收敛的共识路线，而是一组共享“预训练之外还有资源前沿”的不同下注。

---

## 八、对 Slides 11–13 的证据映射

### Slide 11：当预训练越来越贵，筹码开始流向新的阶段

**可支持内容**

- Post-training：InstructGPT、Constitutional AI、Kimi k1.5、DeepSeek-R1。
- Test time：OpenAI o1、Snell 等、Mind Evolution。
- Environment/experience：ReAct、AlphaProof、AlphaEvolve、Era of Experience。
- Retrieval/context/memory：RETRO、Gemini 1.5、Anthropic context engineering。

**建议改图**

- 不要只画四段线性流程。把 `Retrieval / Context / Memory` 画成贯穿 post-training、test-time 和 environment 的侧边轨道。
- 从 environment 画一条回到 post-training 的反馈箭头，表示 rollout、成功轨迹和合成数据回流。

**推荐口述**

> “变化不是预训练停止，而是模型训练完以后仍然持续花算力：用反馈塑造行为，用搜索和验证换取更好的单次答案，用检索和记忆扩展参数外知识，再从环境里制造下一轮经验。”

### Slide 12：第三次改写——决定在哪里花算力

**最强证据**

- Kimi：“Scaling reinforcement learning unlocks a new axis”。
- OpenAI o1：训练时 RL 与测试时思考时间都带来持续改善。
- RETRO：2T-token 外部数据库让更少参数达到可比结果。
- AlphaProof：数百万题目变体 + Lean verifier + test-time RL 解出此前未解的 IMO 题。

**必须降权**

- NVIDIA “three laws”只作为产业分类，页面脚注写明“taxonomy, not three equally established mathematical laws”。
- “Noam Brown 100,000×”不放正文；若放附录，必须标注为扑克搜索实验，不能当 LLM 通用兑换率。
- “DeepSeek 用纯 RL 做出 R1”改为“R1-Zero 展示纯 RL；正式 R1 使用 cold-start SFT 和多阶段训练”。

**推荐口述**

> “这些方向证明了新的改善轴存在，但还没有证明它们是同一条、跨任务可外推的定律。现在更像一组新的资源分配问题。”

### Slide 13：更多计算必须经过正确反馈

**三道门的证据**

1. **Reward 门：** Gao 等 reward overoptimization；DeepSeek-R1-Zero 的行为质量问题。
2. **Verifier 门：** Snell 的难度依赖；OpenAI process supervision；AlphaProof/AlphaEvolve 的强结果集中于可验证环境。
3. **Environment 门：** AI Agents That Matter 的成本和归因；Yao 对非 i.i.d./human-in-loop 环境的批评；METR 的外部有效性与可靠度差距。

**建议把“better outcome”旁边再加两个小标签**

- `quality / reliability`
- `cost / latency`

这能避免把 benchmark 增益与部署价值合并。

**推荐口述**

> “计算本身不会自动变成能力。它必须通过一个仍然对准真实目标的 reward、一个足够可靠的 verifier，以及一个没有把错误目标写进规则的环境。”

---

## 九、推荐直接引语

1. **Richard Sutton，2019-03-13，历史框架**
   > “The biggest lesson that can be read from 70 years of AI research is that general methods that leverage computation are ultimately the most effective.”

2. **Demis Hassabis，2024-02-28，战略不确定性**
   > “It’s an empirical question, whether that will hit an asymptote or a brick wall … I think no one knows.”

3. **OpenAI o1，2024-09-12，双重扩展**
   > “The performance of o1 consistently improves with more reinforcement learning (train-time compute) and with more time spent thinking (test-time compute).”

4. **Kimi Team，2025-01-22，RL 战略**
   > “Scaling reinforcement learning (RL) unlocks a new axis for the continued improvement of artificial intelligence.”

5. **Gao、Schulman、Hilton，2022-10-19，reward 边界**
   > “Because the reward model is an imperfect proxy, optimizing its value too much can hinder ground truth performance.”

6. **Snell 等，2024-08-06，难度依赖**
   > “The effectiveness of different approaches to scaling test-time compute critically varies depending on the difficulty of the prompt.”

7. **RETRO，2021-12-08，参数外扩展**
   > “With a 2 trillion token database … [RETRO] obtains comparable performance to GPT-3 and Jurassic-1 … despite using 25× fewer parameters.”

8. **AI Agents That Matter，2024-07-01，归因边界**
   > “SOTA agents are needlessly complex and costly, and the community has reached mistaken conclusions about the sources of accuracy gains.”

9. **David Silver、Richard Sutton，2025-04-11，研究议程**
   > “A new generation of agents will acquire superhuman capabilities by learning predominantly from experience.”

10. **Shunyu Yao，2025-04-10，环境与评测**
    > “In this new era, evaluation becomes more important than training.”

---

## 十、最重要的 10 条来源

按对 slides 11–13 的信息增量和证据互补性排序：

1. [OpenAI — Learning to reason with LLMs (2024-09-12)](https://openai.com/index/learning-to-reason-with-llms/)：train-time RL 与 test-time compute 的核心一手表述。
2. [Snell et al. — Scaling LLM Test-Time Compute Optimally (2024-08-06)](https://arxiv.org/abs/2408.03314)：难度、verifier、预算分配的最关键条件证据。
3. [Gao et al. — Scaling Laws for Reward Model Overoptimization (2022-10-19)](https://arxiv.org/abs/2210.10760v1)：reward scaling 的结构性反证。
4. [Kimi Team — Kimi k1.5 (2025-01-22)](https://arxiv.org/abs/2501.12599)：RL 作为新 axis 的直接战略与实验。
5. [DeepSeek-AI — DeepSeek-R1 (2025-01-22)](https://arxiv.org/abs/2501.12948)：RLVR 的强结果及“R1-Zero ≠ R1”边界。
6. [Google DeepMind — RETRO (2021-12-08)](https://arxiv.org/abs/2112.04426)：检索库作为参数之外资源轴。
7. [Google DeepMind — AlphaProof / Olympiad-level formal reasoning](https://www.nature.com/articles/s41586-025-09833-y)：可验证环境、test-time RL、自生成经验的合流。
8. [Kapoor et al. — AI Agents That Matter (2024-07-01)](https://arxiv.org/abs/2407.01502v1)：agent 成本控制与增益归因。
9. [Silver & Sutton — Welcome to the Era of Experience (2025-04-11)](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf)：experience scaling 的权威研究议程。
10. [Shunyu Yao — The Second Half (2025-04-10)](https://ysymyth.github.io/The-Second-Half/)：为何环境、长期记忆和 evaluation 可能成为下一瓶颈。

## 核验说明

- 本文共整理 **28 条独立来源卡片**，其中以实验论文/技术报告为主，另保留少量负责人访谈、研究议程和一个明确标注的营销分类。
- 日期采用原始发布日或 arXiv v1 日；后续期刊版只在需要补充更完整实验时并列。
- 视频仅在可定位到公开 transcript 或页面时间戳时引用；Noam Brown 的 100,000× 特别保留了扑克实验语境。
- 公司 benchmark 均按“团队自报实验”处理；未找到公开材料时不推断训练计算、私有数据或商业系统的隐藏细节。
- 截至 2026-08-24，post-training 和 test-time compute 的公开证据明显多于长期开放环境中的持续学习证据；后者仍最容易被 benchmark 设计、reward 质量和成本混淆。
