# AI Scaling Laws：科普材料与叙事方法研究

> 研究日期：2026-08-24
> 用途：20–30 分钟、无公式、静态幻灯片、视觉直觉优先的公司内部分享。
> 口径：候选 16 个，精选 10 个。这里评估的是“能否帮助讲清楚”，不是按技术权威性给来源排总榜。

## 先给结论

最适合本分享的主线不是“参数越多越聪明”，而是三次改写：

1. **从豪赌到可预测：** 先展示一组便宜的小实验如何预测一次昂贵的大训练，再补上“预测的是平均 loss，不是智能”的边界。
2. **从加码到换筹码：** 固定总算力，把同一袋筹码在“模型容量”和“读过的数据”之间重分；Kaplan 是第一种配方，Chinchilla 是在总预算不变时的反转。
3. **从一条曲线到一张生命周期地图：** 预训练不是消失，而是筹码继续流向 post-training、推理时搜索/验证和环境反馈；这些方向成熟度不同，不能都叫已经成立的 law。

对本题最有价值的材料分三类：Jared Kaplan、DeepLearning.AI 和 Stanford/MIT 课程负责概念骨架；Latent Space 和 Sequoia 访谈负责把 Chinchilla 接到部署及 test-time；3Blue1Brown、Computerphile 和 MIT Technology Review 负责视觉语法、节奏和认知边界。

## 评选标准与标签

- **精选**：建议完整观看/阅读，直接影响正文结构或画面。
- **候补**：有一项明显价值，但过于技术、过长、偏题或叙事立场较强。
- 优先条件：一手讲者、完整逐字稿/字幕、明确发布日期、能追到原始论文。
- `VC 视角` 表示文章同时在塑造投资叙事；它可用于展示产业如何讲故事，不单独作为技术结论证据。
- 下列“可能误导点”是对用于本次演讲时的风险判断，不等于来源本身有事实错误。

## 候选详析

### 1. 精选｜Large Language Models explained briefly

- **作者/频道：** Grant Sanderson / 3Blue1Brown
- **发布日期：** 2024-11-20
- **链接：** [YouTube](https://www.youtube.com/watch?v=LPZh9BOjkQs) · [图文课页](https://www.3blue1brown.com/lessons/mini-llm/)
- **类型：** 视觉科普短片；有字幕与图文版
- **一句话收录理由：** 它不专讲 scaling law，却是本项目最应模仿的“无公式建立正确直觉”样板。
- **开场钩子：** 从人人见过的聊天输出倒推“它其实只是在重复预测下一个词”，把熟悉界面变成陌生问题。
- **解释顺序：** 可见行为 → next-token prediction → 海量文本 → 参数旋钮 → 训练反馈 → Transformer 内部；每一步只引入一个新对象。
- **类比：** 参数是大机器上的大量可调旋钮；训练是根据一次次猜错微调旋钮。
- **视觉手法：** 同一对象在画面中持续变形；数字先被转成可感知尺度（读完 GPT-3 数据需约 2,600 年），再给术语。
- **信息节奏：** 约 8 分钟只完成一条因果链，细节留给后续章节；旁白总比画面晚半拍命名。
- **认知反转：** 看似会说话的系统，核心训练信号极其朴素。
- **结尾方式：** 收束成一个可继续展开的内部结构，而非列总结清单。
- **可借鉴点：** 用“筹码”替代抽象 FLOPs；先让观众看见移动，再说“固定算力预算”；相邻静态页模拟视频中的连续变形。
- **可能误导点：** “旋钮”很直观，但容易让人以为单个参数有稳定可解释含义；本分享应说明这是资源计数隐喻，不是机理解释。

### 2. 精选｜Scaling Laws and Their Implications for Coding AI

- **作者/频道：** Jared Kaplan；Harvard CMSA New Technologies in Mathematics Seminar
- **发布日期：** 讲座 2022-03-02；视频 2022-03-04
- **链接：** [YouTube（完整自动字幕）](https://www.youtube.com/watch?v=Suhp3OLASSo) · [Kaplan et al. 原论文，2020-01-23](https://arxiv.org/abs/2001.08361)
- **类型：** 原作者学术讲座；一手来源
- **一句话收录理由：** 最适合确认 scaling law 最初解决什么工程问题，以及作者当时如何从语言扩展到代码、数据限制和 RL。
- **开场钩子：** 把 scaling laws 说成理解 AI 进展的“organizing principle”，不是一条孤立公式。
- **解释顺序：** 多领域共同曲线 → 语言模型 → 固定预算分配 → 下游代码能力 → 数据与 RL 的未来限制。
- **类比：** 原论文把宏观 scaling relation 类比成气体的宏观定律：忽略大量微观细节仍能描述整体。
- **视觉手法：** 多条曲线在统一坐标中形成平滑趋势，再外推到未训练的大模型；适合改造成“实验点—趋势—昂贵目标点”三页。
- **信息节奏：** 技术密度高，先给反复出现的总体图景，再进入代码案例。
- **认知反转：** 价值不在“越大越好”这句常识，而在跨多个数量级仍可外推，以及由此决定预算分配。
- **结尾方式：** 从已测规律转向数据是否够用、RL 是否成为新轴的开放问题。
- **可借鉴点：** Slide 4–6 应把 scaling 讲成“预测工具”；可引用论文原文关于 loss 跨七个数量级呈幂律，但正文不展示公式。
- **可能误导点：** 讲座发生在 Chinchilla 发表前后，沿用 Kaplan 的旧 compute-optimal 配方；不能把它当今天的最佳训练处方。

### 3. 精选｜Scaling laws and compute-optimal models

- **作者/机构：** Antje Barth、Chris Fregly、Shelbee Eigenbrode、Mike Chambers；DeepLearning.AI × AWS
- **发布日期：** 2023-06（课程上线月份；当前课程页未给精确日）
- **链接：** [8 分钟课程与逐字稿](https://learn.deeplearning.ai/courses/generative-ai-with-llms/lesson/v5xa6/scaling-laws-and-compute-optimal-models) · [课程页](https://www.deeplearning.ai/courses/generative-ai-with-llms)
- **类型：** 教学视频；逐字稿可读
- **一句话收录理由：** 最短且完整地串起 compute、model size、data、loss 与 Chinchilla，适合校准 14 页分享的信息密度。
- **开场钩子：** 先把 petaflop/s-day 换成具体 GPU 和时间，再展示 BERT、T5、GPT-3 的训练量级差。
- **解释顺序：** 可感知的计算成本 → 三个 scaling 选择 → loss 曲线 → 固定预算 → Chinchilla 的更优平衡。
- **类比：** 没有花哨比喻，核心是“预算约束下的三选项”；可直接转成筹码。
- **视觉手法：** 模型家族的量级柱状对比、同一图上的训练轨迹和最优包络线。
- **信息节奏：** 8 分钟完成一个闭环，每个图只回答一个问题。
- **认知反转：** 最大参数模型不一定是固定算力下最好的模型。
- **结尾方式：** 从经验规律落到可执行的 right-sizing 决策。
- **可借鉴点：** Slide 7 先规定筹码总数，Slide 8–9 再换分配；不要先教三个变量的定义。
- **可能误导点：** 教学简化容易让“约 20 tokens/parameter”听起来像普适常数；它是特定训练、数据和目标下的估计，部署最优还要计入推理成本。

### 4. 精选｜Llama 2, 3 & 4: Synthetic Data, RLHF, Agents on the Path to Open Source AGI

- **作者/频道：** swyx、Alessio Fanelli / Latent Space；嘉宾 Thomas Scialom（Meta/FAIR，Llama 2 lead、Llama 3 post-training lead）
- **发布日期：** 2024-07-23
- **链接：** [文章与完整逐字稿](https://www.latent.space/p/llama-3) · [YouTube](https://www.youtube.com/watch?v=uLR8nSrhk_w)
- **类型：** 技术播客/访谈；完整逐字稿
- **一句话收录理由：** 少见地把 Kaplan→Chinchilla→“Chinchilla trap”→过度训练小模型→synthetic data/RLHF/agents 串成一条工程叙事。
- **开场钩子：** 借 Llama 3.1 发布和 405B 模型的热点，直接问“为什么今天的开源模型配方不同了”。
- **解释顺序：** Llama 历代变化 → 预训练数据和 Chinchilla → 部署经济性 → synthetic data → RLHF → agents。
- **类比：** “Chinchilla trap”：论文中的训练算力最优，不等于高调用量产品的总成本最优。
- **视觉手法：** 播客本身视觉弱，但逐字稿章节化很好；最适合转成“训练账单 + 每次推理账单”的两张收据。
- **信息节奏：** 通过主持人不断把研究术语拉回实际模型和成本；每 10 分钟换一个生命周期阶段。
- **认知反转：** 超过 Chinchilla 的训练量并不一定浪费；更小、训练更久的模型可能更便宜地服务。
- **结尾方式：** 从单模型扩展到能规划、回退、用工具的 agent 系统。
- **可借鉴点：** Slide 9 后补一句“Chinchilla 优化的是哪张账单？”；Slide 10 用部署成本说明为何“law、recipe、product optimum”不同。
- **可能误导点：** “Chinchilla trap”是嘉宾的解释性标签，不是对论文错误的证明；对 Llama 未来和 agents 的描述带团队愿景，不能当独立验证。

### 5. 精选｜Can AI scaling continue through 2030?

- **作者/机构：** Jaime Sevilla、Tamay Besiroglu、Ben Cottier、Josh You、Edu Roldán 等 / Epoch AI
- **发布日期：** 2024-08-20
- **链接：** [完整研究报告](https://epoch.ai/publications/can-ai-scaling-continue-through-2030)
- **类型：** 非营利研究机构的产业/技术研究；图表丰富
- **一句话收录理由：** 把“还能不能继续 scale”拆成电力、芯片、数据、延迟四个可视瓶颈，是第三幕最好的现实约束地图。
- **开场钩子：** 一个明确但可检验的问题：历史上约 4×/年的训练算力增长能否持续到 2030？
- **解释顺序：** 先给 2e29 FLOP 的总判断 → 逐一检查电力、芯片、数据、latency wall → 合并最先触顶的约束。
- **类比：** 多个串联瓶颈；系统上限由最先卡住的那个决定。
- **视觉手法：** 每种约束一条可行区间，最后叠合；把抽象数量级换成数据中心、电厂、GPU 和 token 库存。
- **信息节奏：** 结论先行，逐层增加不确定性；非常适合静态页“每次多打开一道闸门”。
- **认知反转：** “技术上可行”并不等于“经济上会发生”，也不等于能力按同样速度增长。
- **结尾方式：** 给中央估计，同时列出跨过下一瓶颈所需的基础设施变化。
- **可借鉴点：** Slide 11 可把筹码放上生命周期之前，先让它们通过电力、芯片、数据三道供给门；或作为附录回答“钱真的能换成算力吗”。
- **可能误导点：** Epoch 的使命偏重趋势测量和预测，场景假设较积极；2e29 FLOP 是可行性上界分析，不是预测，也不是 scaling law 本身。

### 6. 精选｜Generative AI’s Act o1

- **作者/机构：** Sonya Huang、Pat Grady 与 o1 / Sequoia Capital
- **发布日期：** 2024-10-09
- **链接：** [原文](https://sequoiacap.com/article/generative-ais-act-o1/)
- **类型：** VC 产业论述；`VC 视角`
- **一句话收录理由：** 它是“pretraining → reasoning layer → inference cloud”叙事最凝练的产业版本，也正因过度凝练而适合做批判性样本。
- **开场钩子：** 把 o1 称为 2024 最重要的模型更新和生成式 AI 的新一幕。
- **解释顺序：** foundation model 层趋稳 → o1“停下来想” → 新的 inference-time scaling plane → agent 与服务市场。
- **类比：** “stop and think”；从一次作答扩展为在草稿纸上搜索和回退。
- **视觉手法：** 戏剧“Act”结构和二维坐标面，把新轴画成从原曲线旁边展开的新平面。
- **信息节奏：** 宣言式短段落，技术证据与市场机会交替，转折极快。
- **认知反转：** 未来最大的算力池可能不是一次性训练集群，而是按问题难度动态分配的 inference cloud。
- **结尾方式：** 从技术趋势落到应用层和“service as software”的投资机会。
- **可借鉴点：** Slide 11 用“作答前直接说 vs 拿到草稿纸和检查器”解释 test-time compute；Slide 12 用新平面，而不是三条并列“定律”。
- **可能误导点：** 文中直接称“new scaling law”，证据主要来自 OpenAI 自报曲线和早期 benchmark；Sequoia 投资于应用与基础设施，叙事有明显扩大市场空间的激励。

### 7. 精选｜Noam Brown, Ilge Akkaya & Hunter Lightman on Teaching LLMs to Reason Better

- **作者/频道：** Sonya Huang、Pat Grady / Sequoia Training Data；嘉宾为 OpenAI o1 研究团队
- **发布日期：** 2024-10-02
- **链接：** [原始节目与逐字稿](https://sequoiacap.com/podcast/training-data-noam-brown/) · [YouTube](https://www.youtube.com/watch?v=jPluSXJpdrA)
- **类型：** 一手团队访谈，由 VC 制作；完整逐字稿；`VC 视角`
- **一句话收录理由：** 用 Sudoku 把“多想一会儿何时有用”讲得非常具体，也公开承认并非所有问题都受益。
- **开场钩子：** 问“想两年能让你知道澳大利亚首都吗？”随后用 Sudoku 对照，立即建立任务条件。
- **解释顺序：** 有/无思考收益的任务 → chain of thought 中的回退 → RL 如何教会这种行为 → train-time 与 test-time 两条轴。
- **类比：** Sudoku：答案容易验证、路径需要搜索；“思考更久”是探索更多候选，不是凭空增加知识。
- **视觉手法：** 可画两条路径：事实回忆是一扇锁死的门，Sudoku 是带检查器的迷宫。
- **信息节奏：** 先给反例，再讲成功例，天然抑制“越想越好”的误读。
- **认知反转：** test-time compute 的价值来自问题结构和验证信号，不是 token 越多越智能。
- **结尾方式：** 把 o1 的当前表现定位为新方向的早期样本，而非完成态。
- **可借鉴点：** Slide 13 直接采用“首都 vs Sudoku”双画面；让 verifier 成为决定筹码能否转成能力的门。
- **可能误导点：** 嘉宾是产品团队，无法披露训练细节；节目和宿主对 o1 的定位偏积极，benchmark 不是独立复现。

### 8. 精选｜Demis Hassabis — Scaling, superhuman AIs, AlphaZero atop LLMs, AlphaFold

- **作者/频道：** Dwarkesh Patel；嘉宾 Demis Hassabis（Google DeepMind CEO）
- **发布日期：** 2024-02-28
- **链接：** [原始访谈与全文逐字稿](https://www.dwarkesh.com/p/demis-hassabis) · [YouTube](https://www.youtube.com/watch?v=qTogNUV3CAI)
- **类型：** 重量级人物长访谈；一手逐字稿
- **一句话收录理由：** 给出最适合本分享结尾的中间立场：继续推 scaling，同时加倍发明新架构与算法。
- **开场钩子：** 从“scaling 强假说遗漏了什么”切入，不要求听众先接受赞成或反对立场。
- **解释顺序：** LLM 已得到什么 → scaling 的实际工程限制 → loss 与能力差异 → search/planning/RL 叠加。
- **类比：** scaling 是“art form”：每跨一个数量级都要重新校正配方，不能按复印机式流程放大。
- **视觉手法：** 访谈视觉一般，但语言适合做一条“直线外推—中途校准—继续前行”的图。
- **信息节奏：** 主持人持续追问反事实和瓶颈，使嘉宾在乐观判断旁边给出条件。
- **认知反转：** “scaling works”与“只要 scaling 就够了”不是同一个命题。
- **结尾方式：** 以组合下注收束：规模与发明同时推进。
- **可借鉴点：** Slide 14 的 `law / strategy / bet` 之前，加入“继续曲线”和“发明新路”不是二选一。
- **可能误导点：** 这是实验室负责人的战略判断；“半数 scaling、半数 invention”是组织叙事，不是行业资源统计。

**可直接引用的一手原话（2024-02-28）：**

> “I think we’ve got to push scaling as hard as we can… In the meantime, we should also double down on innovation and invention… my betting right now… is that you need both.”

引用时保留省略号并链接全文，不改写为“Demis 说 scaling 已到尽头”。

### 9. 精选｜Large language models can do jaw-dropping things. But nobody knows exactly why.

- **作者/媒体：** Will Douglas Heaven / MIT Technology Review
- **发布日期：** 2024-03-04
- **链接：** [原文](https://www.technologyreview.com/2024/03/04/1089403/large-language-models-amazing-but-nobody-knows-why/)
- **类型：** 权威媒体长文；有 16 分钟官方朗读版
- **一句话收录理由：** 它提供一条必要的反叙事：经验曲线可预测，不代表我们拥有完整的机制理论。
- **开场钩子：** 从一个模型先死记算术、很久后突然“grok”出规则的具体实验开场。
- **解释顺序：** 离奇案例 → 经典统计学预期 → double descent/grokking → 多位研究者解释 → 未解问题。
- **类比：** 经典“U 形过拟合曲线”被实际的 double descent 穿过；旧地图无法完整描述新地形。
- **视觉手法：** 一条本应向上恶化却再次下降的曲线，本身就是视觉反转。
- **信息节奏：** 每提出一个神秘现象，就用研究者原话降低断言强度；长文有呼吸感。
- **认知反转：** 工程上能稳定预测某些宏观量，与科学上知道“为什么产生智能行为”可以同时一真一假。
- **结尾方式：** 不假装解谜，转向“理解机制是控制更强系统的前提”。
- **可借鉴点：** Slide 6 左边保留平滑 loss 曲线，右边让具体能力卡片不规则出现；旁白明确“可预测”有边界。
- **可能误导点：** 标题“nobody knows”是媒体化概括；研究者并非完全无知，而是缺少完整统一理论。不要用它否定 scaling 的经验可靠性。

### 10. 精选｜AI’s Version of Moore’s Law?

- **作者/频道：** Computerphile；讲者 Sydney von Arx（METR）；拍摄/剪辑 Sean Riley
- **发布日期：** 2025-04-29
- **链接：** [YouTube（字幕）](https://www.youtube.com/watch?v=evSFeqTZdqs) · [对应 METR 原研究，2025-03-19](https://metr.org/blog/2025-03-19-measuring-ai-ability-to-complete-long-tasks/)
- **类型：** 13 分钟研究科普视频；一手研究者讲解
- **一句话收录理由：** 展示如何用一个直观指标、一个指数趋势和连续的怀疑检查，讲清“趋势不等于定律”。
- **开场钩子：** 不是问 benchmark 又涨了多少，而是问“模型能独立完成多长的人类任务？”
- **解释顺序：** benchmark 的不足 → 构造真实任务集 → 人类耗时作为横轴 → 7 个月翻倍趋势 → 稳健性与外推限制。
- **类比：** Moore’s law 提供熟悉脚手架，但全片不断检查这个类比是否过强。
- **视觉手法：** 任务时长从分钟向小时延伸；散点、趋势线、阈值敏感性都能用逐页揭示复刻。
- **信息节奏：** 每展示一个令人兴奋的趋势，马上安排一个“如果换成功率阈值呢？”的质疑。
- **认知反转：** 能力趋势可以很稳健，但单次具体任务仍然噪声很大。
- **结尾方式：** 以“我看过任务和轨迹后相信趋势真实”收束，而非把外推包装成确定预测。
- **可借鉴点：** 全场采用“主张—边界”成对节奏：Slide 5 曲线后立刻是 Slide 6；Slide 12 新轴后立刻是 Slide 13 条件。
- **可能误导点：** 时间跨度指标不是训练 loss scaling law；模型、scaffold 和评测共同变化，不能把 7 个月翻倍归因于单一 scaling 变量。

### 11. 候补｜The Mathematics of Training LLMs

- **作者/频道：** swyx、Alessio Fanelli / Latent Space；嘉宾 Quentin Anthony（EleutherAI）
- **发布日期：** 2023-08-16
- **链接：** [文章、播客与完整逐字稿](https://www.latent.space/p/transformers-math)
- **类型：** 技术播客/工程 masterclass
- **一句话收录理由：** 解释“纸面 FLOPs 相同，现实成本不相同”，可防止把筹码隐喻讲得过度理想化。
- **开场钩子：** “停止 handwaving，让 GPU 真正跑起来”；从训练预算如何变成时间和钱切入。
- **解释顺序：** 参数/数据 → Chinchilla → 吞吐量 → GPU 时间 → 显存 → 并行和通信。
- **类比：** 1,000 张 GPU 跑 1 小时并不总等于 1 张跑 1,000 小时，因为通信和并行效率不同。
- **视觉手法：** 适合把筹码分成“有效计算”和“通信损耗”两色。
- **信息节奏：** 50 分钟、术语密集，依赖主持人复述和估算例子。
- **认知反转：** 理论 compute-optimal 不自动等于 wall-clock 或 dollar-optimal。
- **结尾方式：** 扩展到分布式训练和硬件约束。
- **可借鉴点：** 口述加一句“筹码是假设可互换的抽象预算，现实 GPU 还有通信损耗”。
- **可能误导点：** 对无公式 26 分钟分享过深；其中的经验数值会随硬件栈变化，不宜进正文。

### 12. 候补｜Training compute of frontier AI models grows by 4–5× per year

- **作者/机构：** Jaime Sevilla、Edu Roldán / Epoch AI
- **发布日期：** 2024-05-28
- **链接：** [原文与数据方法](https://epoch.ai/publications/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year)
- **类型：** 数据驱动产业研究
- **一句话收录理由：** 为“行业实际在 scale 什么、速度多快”提供比轶闻更可靠的历史基线。
- **开场钩子：** 直接回答近年来 frontier training compute 的增长速度，而不是用某一个模型代表全行业。
- **解释顺序：** notable models → frontier top-10 → 近期 LLM → 各实验室子样本 → 不确定区间。
- **类比：** 像从不同相机角度测同一辆加速中的车，检查结论是否依赖样本定义。
- **视觉手法：** 同一时间轴叠加不同筛选口径；置信区间始终可见。
- **信息节奏：** 主结论反复经不同切片检验，节奏偏研究报告。
- **认知反转：** “LLM 总体 9.5×/年”和“近期 frontier LLM 约 5×/年”可同时成立，取决于样本和时期。
- **结尾方式：** 给暂定结论并保留“可能加速/曾经减速”的不确定性。
- **可借鉴点：** 开场若使用硬件热潮，只说投入规模的历史事实，不把股价当 scaling 成立的证据。
- **可能误导点：** 训练 compute 增长是投入趋势，不是性能回报率；`4–5×` 不能直接投射成能力增长。

### 13. 候补｜A jargon-free explanation of how AI large language models work

- **作者/媒体：** Timothy B. Lee、Sean Trott / Ars Technica（原载 Understanding AI）
- **发布日期：** 原版 2023-07-28；Ars 版 2023-07-31
- **链接：** [Ars Technica](https://arstechnica.com/science/2023/07/a-jargon-free-explanation-of-how-ai-large-language-models-work/) · [作者副本](https://seantrott.substack.com/p/large-language-models-explained)
- **类型：** 长篇无公式科普；多幅定制图
- **一句话收录理由：** 是“最少数学但不止一句 next-token prediction”的优秀书面范例。
- **开场钩子：** 承认公众对 LLM 的解释常停在“预测下一个词”，承诺再深入一层但不用线代。
- **解释顺序：** token → 向量 → 层 → attention/MLP → 训练 → scaling 与涌现行为。
- **类比：** 用词义空间和逐层加工解释内部表征；用人类儿童接触约一亿词对比 GPT-3 的约五千亿词。
- **视觉手法：** 定制示意图与短段落交替，图不是装饰，而是承担下一步推理。
- **信息节奏：** 每一节只回答一个普通读者自然会追问的问题。
- **认知反转：** “只预测下一个词”并不意味着内部只存局部词频。
- **结尾方式：** 从已知机制回到仍难解释的整体行为。
- **可借鉴点：** 每页标题写成观众问题的答案；数字必须附人类尺度参照物。
- **可能误导点：** 人类阅读量比较很抓人，但训练 token 与儿童经验质量、感官和交互不可直接等价。

### 14. 候补｜Stanford CS336: Scaling Laws（Lectures 9–10）

- **作者/机构：** Tatsunori Hashimoto / Stanford CS336: Language Modeling from Scratch
- **发布日期：** 2024-04-29、2024-05-01
- **链接：** [课程日程与讲义入口](https://cs336.stanford.edu/spring2024/) · [课程仓库](https://github.com/stanford-cs336/spring2024-lectures)
- **类型：** 大学课程/讲义；技术 survey
- **一句话收录理由：** 最系统地核对 Kaplan、Chinchilla、拟合流程和外推陷阱，适合讲者备课而非观众观看。
- **开场钩子：** 从实际任务“用便宜训练 API 拟合曲线，预测更大模型”开始。
- **解释顺序：** 资源核算 → 经验 power law → 拟合 → compute-optimal → Kaplan/Chinchilla 差异 → 实践陷阱。
- **类比：** proxy model 像先做风洞实验，再决定是否造整架飞机。
- **视觉手法：** 真实实验点、包络线、不同拟合区间的外推对照。
- **信息节奏：** 两堂课，技术细节完整但远超本分享容量。
- **认知反转：** scaling law 不是从一条漂亮直线读答案；数据选择、训练日程和拟合区间会改变外推。
- **结尾方式：** 落到学生亲自拟合和检查误差。
- **可借鉴点：** Slide 5 必须先出现散点，再出现曲线；曲线不应从画面外神谕式降临。
- **可能误导点：** 课堂为懂 ML 的学生设计；若照搬坐标和术语，会破坏“无公式、一页一动作”的目标。

### 15. 候补｜Lecture 20: Scaling Laws

- **作者/机构：** MIT 6.7960 Deep Learning（Fall 2024）
- **发布日期：** 2024（课程讲义未在 PDF 首页标精确日）
- **链接：** [MIT OpenCourseWare PDF](https://ocw.mit.edu/courses/6-7960-deep-learning-fall-2024/mit6_7960_f24_lec20.pdf)
- **类型：** 技术 survey/课件
- **一句话收录理由：** 以紧凑图表并置 Kaplan 与 Chinchilla 三种分析方法，是事实核查和附录素材库。
- **开场钩子：** “能否从小实验外推大实验？在固定预算下该要多少数据和参数？”
- **解释顺序：** 问题定义 → power law → Kaplan → Chinchilla 的三种估计方法 → 新旧分配差异 → 注意事项。
- **类比：** 最优配置是一条低维“山脊/流形”，不是参数和数据各自独立越多越好。
- **视觉手法：** 用同一预算的等算力切片比较模型；三种方法最终汇合到近似结果。
- **信息节奏：** 课件式高密度，结论短促。
- **认知反转：** Chinchilla 不是一个单模型轶事，而是三种分析都指向“旧模型普遍欠训练”。
- **结尾方式：** 回到 scaling laws 用于资源分配的工程价值。
- **可借鉴点：** Slide 9 的反转口述应强调“同样筹码，三种测法都提示重新分配”，不只讲 70B 打败 280B。
- **可能误导点：** 单独截取 20:1 图会丢掉方法和适用范围；课件包含公式，不适合直接投屏。

### 16. 候补｜Has Generative AI Already Peaked?

- **作者/频道：** Computerphile；讲者 Rob Miles
- **发布日期：** 2024（YouTube 页面可访问字幕，但检索接口未稳定返回精确发布日期）
- **链接：** [YouTube](https://www.youtube.com/watch?v=dDUC-LqVrPU) · [可检索逐字稿镜像](https://rosetta.to/u/computerphile/has-generative-ai-already-peaked-computerphile)
- **类型：** 质疑型科普视频
- **一句话收录理由：** 提供“曲线会变平、收益越来越贵”的反方视觉语法，避免全场只有乐观外推。
- **开场钩子：** 直接问生成式 AI 是否已接近平台期。
- **解释顺序：** 展示多组下游曲线 → 观察收益递减 → 讨论数据需求 → 追问是否值得 → 承认未来可证伪。
- **类比：** 不断加数据像在越来越平的坡上推车，成本增大但高度变化变小。
- **视觉手法：** 多条不同任务曲线重复同一种变平形状，形成模式识别。
- **信息节奏：** 强主张后主动自嘲和限定“只是一篇论文”，保持可亲近感。
- **认知反转：** power law 可以持续改善，同时经济回报已不划算；“未硬停”与“实际平台期”并不冲突。
- **结尾方式：** 给出两种未来并承诺几年后回看，而非宣布争论结束。
- **可借鉴点：** Slide 5 口述“曲线没断，但每一点越来越贵”；Slide 14 加上 measured outcome 和 economics 的区别。
- **可能误导点：** 视频讨论的任务/论文不等同于 LLM 预训练 loss；“peaked”标题强于证据。精确日期需在正式引用前到 YouTube 原页人工复核。

## 三条叙事链的交叉比较

### A. 无公式解释 scaling law

最有效的顺序是：

1. **先有代价：** 一次大训练贵到不能反复试错。
2. **再有小实验：** 许多小点不是为了炫图，而是“便宜地探路”。
3. **再连趋势：** 曲线是经验总结，不是自然界写好的命令。
4. **最后说用途：** 它让团队预测平均 loss、比较资源配置。
5. **立即画边界：** 不直接预测某项能力、可靠性、AGI 或商业价值。

对应最佳样本：3Blue1Brown 的“先看对象再命名”、Kaplan 的“小到大外推”、Computerphile 的“结论后立刻做稳健性检查”。

### B. Kaplan → Chinchilla

不要按论文摘要顺序讲，而要把它讲成一个固定预算游戏：

- 给观众一袋总数不变的筹码。
- Kaplan：更多筹码放进更大模型，数据增长较慢、较早停止。
- 保持构图和筹码总数完全不变。
- Chinchilla：把一部分筹码移到“让较小模型多读”，70B Chinchilla 用相同训练 compute 超过 280B Gopher。
- 再反转一次：产品若要服务海量请求，训练最优不等于全生命周期成本最优，Llama 会选择更小模型、训练更久。

这比“2020 一条公式、2022 另一条公式”更准确也更有戏剧性。最佳样本是 DeepLearning.AI 的预算框架、MIT 的三种分析汇合、Latent Space 的部署账单。

### C. Pretraining → post-training / test-time

避免“旧 scaling 失效，所以发明三条新 law”的断裂叙事。更稳妥的视觉是同一袋筹码沿生命周期移动：

- **Pretraining：** 在回答任何具体问题前，把能力压进权重。
- **Post-training：** 用偏好、可验证任务、合成数据和环境反馈改变行为。
- **Test-time：** 遇到具体问题后，购买草稿、搜索、候选采样和验证。
- **Environment/experience：** 让系统从长期交互产生新反馈；这是研究议程，不是已稳定拟合的统一 law。

Sequoia 的“新平面”是好画法，Noam Brown 的“首都 vs Sudoku”提供适用条件，Demis 的“scaling + invention”防止伪二选一。

## 最值得借鉴的 5 个具体叙事技巧

### 1. 同一预算、只移动筹码

不要在 Kaplan 和 Chinchilla 两页换图。保留完全相同的筹码总数、两个容器和画面比例，只移动筹码。观众一眼看到：规律没有被推翻，**配方被改写**。

### 2. 每个主张后面紧跟一页边界

采用 Computerphile 的节奏：

- “loss 可预测” → “但能力不直接可预测”
- “Chinchilla 赢了” → “但 20:1 不是自然常数”
- “test-time 有新轴” → “但首都问题想再久也没用”

这让严谨本身成为节奏，而不是演讲末尾的免责条款。

### 3. 用反例先定义 test-time compute

先画两道题：

- “澳大利亚首都？”——没有知识，想两年也不会增加答案质量。
- Sudoku——可以搜索，且答案易验证，更多计算可能有用。

然后才命名 `test-time compute`。这比先列 search、sampling、verification 更容易记，也自然引出 verifier。

### 4. 把一条曲线拆成三次逐步揭示

静态幻灯片也能获得动画式连续性：

1. 只有多个小实验点；
2. 同构图增加拟合曲线；
3. 同构图延伸到昂贵大实验；
4. 下一页把右侧拆成 loss 与四个不规则能力结果。

这是 3Blue1Brown 的“对象连续变形”在静态幻灯片中的等价物。

### 5. 区分三张账单

每次说“optimal”都让观众看到是哪张账单：

- 一次训练的算力最优；
- 训练 + 海量服务的总成本最优；
- 给一道具体题的推理预算最优。

Kaplan、Chinchilla、Llama overtraining 和 test-time compute 的表面矛盾，会在这三张账单下自动化解。

## 可引用原话：只保留可追到一手来源的版本

### Richard Sutton，2019-03-13

> “The biggest lesson that can be read from 70 years of AI research is that general methods that leverage computation are ultimately the most effective, and by a large margin.”

原始来源：[The Bitter Lesson](http://incompleteideas.net/IncIdeas/BitterLesson.html)。这是 scaling 的思想前史，不是 LLM scaling law。

### Kaplan et al.，2020-01-23

> “The loss scales as a power-law with model size, dataset size, and the amount of compute used for training, with some trends spanning more than seven orders of magnitude.”

原始来源：[Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361)。引用时必须保留主语是 `loss`。

### Hoffmann et al.，2022-03-29

> “For compute-optimal training, the model size and the number of training tokens should be scaled equally.”

原始来源：[Training Compute-Optimal Large Language Models](https://arxiv.org/abs/2203.15556)。这是论文实验区间内的 compute-optimal 结论，不应改写为固定 20:1 的自然定律。

### Demis Hassabis，2024-02-28

> “I think we’ve got to push scaling as hard as we can… In the meantime, we should also double down on innovation and invention… my betting right now… is that you need both.”

原始来源：[Dwarkesh 完整视频与逐字稿](https://www.dwarkesh.com/p/demis-hassabis)，约 16:31 起。它表达战略判断，不是实验结果。

### Noam Brown，2024-10-02

> “There’s some problems where there’s clearly a benefit from being able to think for longer. So one classic example that I point to is a Sudoku puzzle.”

原始来源：[Sequoia Training Data 完整逐字稿](https://sequoiacap.com/podcast/training-data-noam-brown/)。与节目中“首都问题想再久也无益”的反例一起使用，不能截成“所有题都应想更久”。

## 推荐观看/阅读顺序

### 90 分钟核心路径

1. **3Blue1Brown — Large Language Models explained briefly（约 8 分钟）**：先校准视觉语法和无公式密度。
2. **DeepLearning.AI — Scaling laws and compute-optimal models（8 分钟）**：得到参数、数据、compute 与 Chinchilla 的最短骨架。
3. **Jared Kaplan 讲座选段（约 20 分钟）**：看开头的 organizing principle、loss 曲线和 fixed-compute 部分，不必看完整代码段。
4. **Latent Space / Thomas Scialom（读 09:56 起的 Chinchilla 段和部署段，约 15 分钟）**：理解“训练最优”和“服务最优”的差别。
5. **Sequoia / Noam Brown（看开头到 Sudoku、再看 test-time scaling 段，约 20 分钟）**：获得第三幕的具体反例与条件。
6. **Dwarkesh / Demis（读 scaling and alignment 段，约 10 分钟）**：确定结尾立场。
7. **Computerphile — AI’s Version of Moore’s Law?（13 分钟）**：学习主张与边界交替的节奏。

### 深入核验路径

1. Stanford CS336 2024 scaling lectures；
2. MIT 6.7960 Lecture 20；
3. Epoch AI 的 2030 四瓶颈报告；
4. MIT Technology Review 的理论边界长文；
5. Latent Space / Quentin Anthony 的现实硬件成本；
6. 回到 Kaplan 与 Chinchilla 原论文核验所有数字和引语。

## 如何改进当前 14 页大纲

整体三幕结构已经成立，最需要的不是加页，而是强化“同构图 + 主张/边界成对”。

### Slides 1–3：缩短供应链解释，尽快把热点变成下注

- Slide 1 保留公司与同一时间窗，不让行情图承担因果。
- Slide 2 只画一条 `HBM → GPU → 集群` 数据流；口述控制在 45–60 秒。
- Slide 3 的筹码山旁增加一张极简“多年资本承诺”收据，让问题从“芯片为何热”变成“凭什么长期下注”。
- 热点数据临近制作时另行核验；本研究不提供 2026-08-24 的实时股价或财报数字。

### Slides 4–6：把“预测”做成一次现场视觉发现

- Slide 4 不先说 power law，只呈现很多小实验和一个昂贵、尚未运行的大实验。
- Slide 5 拆成三次逐步揭示（点 → 曲线 → 外推点），坐标写“训练资源 / 平均猜错程度”。
- Slide 6 复用同一曲线；从预测点伸出四张不规则卡片：推理、可靠性、幻觉、商业价值。标题可改为：**“曲线很稳，模型的具体行为却不一定。”**
- 用 Kaplan 2020 和 Anthropic 2022 的一手原话分别支撑左右两边。

### Slides 7–10：增加第三张账单，完成双重反转

- Slides 7–9 构图必须像翻页动画：筹码总数、容器位置和颜色都不变。
- Slide 8 标题避免“Kaplan 的答案错了”，改为“2020：按当时实验，筹码更偏向模型”。
- Slide 9 让较小 Chinchilla 的结果卡越过 Gopher，但脚注说明同训练 compute、70B vs 280B、4× 数据。
- Slide 10 不要一开始列五个维度；先加“训练账单”和“每次推理账单”，用 Llama overtraining 完成第二次反转，再把 retrieval/MoE 等作为系统地图逐个展开。
- 口述明确：Kaplan 是历史配方，Chinchilla 是修订配方，Llama 是把部署经济性纳入目标；三者优化的问题不同。

### Slides 11–13：用“首都 vs Sudoku”替代术语列表

- Slide 11 先呈现模型生命周期和筹码流，不列缩写。
- Slide 12 左半画“首都问题：锁死的门”，右半画“Sudoku：带检查器的迷宫”；然后揭示 search、sampling、verification。
- 原 Slide 12 的 Kimi、NVIDIA 分类移入口述或脚注，避免品牌拼贴。
- Slide 13 保留三道门，但把每道门的问题写成动词：
  - reward 是否奖励了真正想要的结果？
  - verifier 能否识别更好的候选？
  - environment 是否提供真实且可扩展的反馈？
- 页尾只留一句：**“更多计算不是能力；更多计算 × 可用反馈，才可能变成能力。”**

### Slide 14：从四个问题收束成一次复用筹码的回看

- 四个问题保留，但每出现一个问题，就让筹码图中对应部分高亮。
- `Is it a law, a strategy, or a bet?` 应是最后一个，也是全场真正的认知工具。
- 结尾先引用 Demis 的“you need both”，再落到自己的结论：**Scaling 没有结束；我们只是从扩大一个模型，转向配置整个系统的资源。**
- 不新增 Thank You 页；在同一页停留，方便听众拍照。

## 访问限制与核验说明

- YouTube 页面可通过检索结果读取标题、频道、时长和自动字幕，但无法在本环境中稳定调用 YouTube 官方字幕下载 API；自动字幕可能有人名和术语误识别。正式做逐字引用时应在原视频时间戳人工复听。
- `Has Generative AI Already Peaked?` 的精确发布日期未从当前检索接口稳定取得，因此只标年份，不把它用于任何需精确日期的引语。
- DeepLearning.AI 课程当前页面提供逐字稿和教师信息，但未显示最初上线的精确日期；这里只记录可核验到的上线月份。
- 部分课程 PDF（MIT、Stanford）有完整图表但不是面向大众的逐字稿；它们用于事实核验，不建议直接复用截图，且正式使用需检查版权/署名要求。
- Sequoia 与 Latent Space 的逐字稿可访问；前者有明确投资叙事，后者是主持人与嘉宾观点，均不能替代原论文或独立评测。
- Epoch AI 报告可完整访问；其数值是模型化估计并带假设，不应改写成确定预测。
- 本文件未使用二手文章作为名人直接引语来源；所有列出的直接引语均链接到原始文章、论文、视频或完整访谈，并标注日期与语境。
