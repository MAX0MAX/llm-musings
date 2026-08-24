# Scaling Laws 阅读清单

这不是完整 bibliography，而是一条为准备 20–30 分钟科普分享设计的阅读路线。主线拆成两轮：先用视频、图解和访谈建立直觉，再回到论文的关键图和适用边界；最后只按讲稿补洞。论文不需要逐页精读，按下面标出的阅读重点即可。

辅助材料负责降低理解门槛，不能替代定量证据。讲稿中的数字、比较和因果判断，仍应引用论文、官方材料或本地证据综述。

## 第一轮：先建立直觉（约 1.5–2 小时）

按分享的叙事顺序浏览；除第 1 项外，每项限时 10–15 分钟。视频只看片段，图文只看示意图和结论，不必全部读完。

1. **LLM 是什么：** [3Blue1Brown 视频](https://www.youtube.com/watch?v=LPZh9BOjkQs)（约 8 分钟）· [官方双语版](https://www.bilibili.com/video/BV1xmA2eMEFF/) · [图文版](https://www.3blue1brown.com/lessons/mini-llm/)
2. **训练预算怎么分：** [DeepLearning.AI — Scaling laws and compute-optimal models](https://learn.deeplearning.ai/courses/generative-ai-with-llms/lesson/v5xa6/scaling-laws-and-compute-optimal-models)
3. **Scaling law 怎么被发现：** [Jared Kaplan — Scaling Laws and Their Implications for Coding AI](https://www.youtube.com/watch?v=Suhp3OLASSo)，只看开头 0:00–15:00 的 scaling-law 回顾，重点理解“小实验如何辅助规划大训练”，不用看后半的代码/RL 内容。
4. **为什么 Chinchilla 改写配方：** [DeepMind 图解](https://deepmind.google/blog/an-empirical-analysis-of-compute-optimal-large-language-model-training/)；再看 [Latent Space 的 Llama 3 访谈](https://www.latent.space/p/llama-3) 09:56–12:15，理解训练成本与推理成本为何会导向不同选择。
5. **数据 scaling 不只是抓网页：** [FineWeb 交互图文](https://huggingface.co/spaces/HuggingFaceFW/blogpost-fineweb-v1)，先看 filtering、deduplication 和 benchmark 对比。
6. **Post-training 与 test-time compute：** [OpenAI 的 InstructGPT 图解](https://openai.com/index/instruction-following/) · [Hugging Face 中文 RLHF 导读](https://huggingface.co/blog/zh/rlhf) · [test-time compute 可视化](https://huggingface.co/spaces/HuggingFaceH4/blogpost-scaling-test-time-compute)。
7. **参数之外的外部资源：** [DeepMind RETRO 图解](https://deepmind.google/blog/improving-language-models-by-retrieving-from-trillions-of-tokens/) · [Google ReAct 图解](https://research.google/blog/react-synergizing-reasoning-and-acting-in-language-models/) · [Anthropic — Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents)。
8. **争论与物理约束：** [Computerphile — Has Generative AI Already Peaked?](https://www.youtube.com/watch?v=dDUC-LqVrPU) 全片约 13 分钟；[Epoch AI — Can AI Scaling Continue Through 2030?](https://epoch.ai/publications/can-ai-scaling-continue-through-2030) 只看四类约束的总览图。前者用于理解反方直觉，后者用于拆分电力、芯片、数据和延迟约束；两者都不代替原始证据。

## 第二轮：8 项讲稿骨架

按这个顺序读，可以先形成主要叙事骨架；它不是完整证据清单。3Blue1Brown 是表达模板，Demis 访谈是行业判断，其余材料才承担相应技术论点的主要证据角色。

1. [3Blue1Brown — Large Language Models explained briefly](https://www.youtube.com/watch?v=LPZh9BOjkQs)
2. [Kaplan et al. — Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361)
3. [Hoffmann et al. — Training Compute-Optimal Large Language Models](https://arxiv.org/abs/2203.15556)
4. [Ganguli et al. — Predictability and Surprise in Large Generative Models](https://arxiv.org/abs/2202.07785)
5. [GPT-3 supplementary material](https://papers.neurips.cc/paper_files/paper/2020/file/1457c0d6bfcb4967418bfb8ac142f64a-Supplemental.pdf)
6. [Snell et al. — Scaling LLM Test-Time Compute Optimally](https://arxiv.org/abs/2408.03314)
7. [RETRO](https://arxiv.org/abs/2112.04426)
8. [Demis Hassabis — Dwarkesh interview](https://www.dwarkesh.com/p/demis-hassabis)

---

## 1. 先学怎么把复杂概念讲得不无聊

### 必读

#### 1.1 3Blue1Brown — Large Language Models explained briefly

- [视频](https://www.youtube.com/watch?v=LPZh9BOjkQs) · [官方双语版](https://www.bilibili.com/video/BV1xmA2eMEFF/) · [图文版](https://www.3blue1brown.com/lessons/mini-llm/)
- **时间：** 约 8 分钟
- **重点看：** 如何先展示熟悉现象，再逐步引入 token、参数和训练；画面如何复用同一个对象，而不是不断换图。
- **对分享的价值：** 这是视觉和叙事风格模板，不是 scaling-law 技术证据。

#### 1.2 DeepLearning.AI — Scaling laws and compute-optimal models

- [课程与逐字稿](https://learn.deeplearning.ai/courses/generative-ai-with-llms/lesson/v5xa6/scaling-laws-and-compute-optimal-models)
- **时间：** 约 10 分钟
- **重点看：** 如何用固定预算解释模型大小、数据量和 compute 的取舍。
- **对分享的价值：** 可以直接帮助设计“算力筹码”页面。

### 延伸阅读

- [Lilian Weng — Scaling Laws, Carefully](https://lilianweng.github.io/posts/2026-06-24-scaling-laws/)：想理解拟合范围、tokenizer、参数计数和数据 mix 如何改变结论时再读。
- [Stanford CS336 — Scaling Laws lectures](https://cs336.stanford.edu/spring2024/)：需要更完整技术背景时看 Lectures 9–10。

---

## 2. 第一次改写：训练如何从豪赌变成可预测工程

### 先看辅助材料

- [Jared Kaplan — Scaling Laws and Their Implications for Coding AI](https://www.youtube.com/watch?v=Suhp3OLASSo)：先看 0:00–15:00，听研究者如何从实验曲线过渡到训练规划；后半代码/RL 内容可跳过。自动字幕中的数字和公式应回论文核对。

### 必读

#### 2.1 Kaplan et al. — Scaling Laws for Neural Language Models

- [论文](https://arxiv.org/abs/2001.08361)
- **建议只读：** Abstract、Introduction、Figure 1、compute-efficient training 部分、Conclusion。
- **重点问题：** 它预测的究竟是什么？哪些条件保持不变？为什么小实验可以用于规划更大的训练？
- **阅读边界：** Kaplan 不是 neural scaling law 的起点；具体资源配方后来被修正。

#### 2.2 Ganguli et al. — Predictability and Surprise in Large Generative Models

- [论文](https://arxiv.org/abs/2202.07785)
- **建议只读：** Abstract、Introduction、Discussion。
- **重点问题：** 为什么 aggregate loss 可以平滑可预测，而具体能力、输入和失败仍然不可预测？
- **对分享的价值：** 为“aggregate loss 可预测，不代表具体能力、行为和失败模式同样可预测”提供一手边界。

### 延伸阅读

- [Hestness et al., 2017](https://arxiv.org/abs/1712.00409)：Kaplan 之前的可预测 learning curves。
- [Rosenfeld et al., 2019](https://arxiv.org/abs/1909.12673)：模型规模与数据规模联合预测的前史。
- [Schaeffer et al., 2023](https://arxiv.org/abs/2304.15004)：在固定模型输出上，非线性或不连续指标可能制造“涌现”外观，是理解不连续能力曲线的重要反证。

---

## 3. 第二次改写：Kaplan 到 Chinchilla 为什么是转折

### 先看辅助材料

- [DeepMind — An empirical analysis of compute-optimal training](https://deepmind.google/blog/an-empirical-analysis-of-compute-optimal-large-language-model-training/)：用图理解“同样 compute，模型更小、token 更多”的核心结果。
- [Latent Space — Llama 3 访谈](https://www.latent.space/p/llama-3)：看 09:56–12:15，理解所谓“Chinchilla trap”以及推理需求如何影响训练决策。访谈中的公司选择仍应与论文区分。

### 必读

#### 3.1 Hoffmann et al. — Training Compute-Optimal Large Language Models

- [论文](https://arxiv.org/abs/2203.15556)
- **建议只读：** Abstract、Introduction、Figure 1–3、Chinchilla 与 Gopher 对比、Conclusion。
- **重点问题：** 为什么相同训练 FLOPs 下，70B/1.4T-token 的 Chinchilla 能超过 280B Gopher？
- **阅读边界：** “20 tokens per parameter”是特定条件下的经验基线，不是自然常数。

#### 3.2 Porian et al. — Resolving Discrepancies in Compute-Optimal Scaling

- [论文](https://arxiv.org/abs/2406.19146)
- **建议只读：** Abstract、Introduction、Conclusion。
- **重点问题：** Kaplan 与 Chinchilla 的差异有多少来自最后一层的 FLOP 计费方式、warmup 长度，以及是否随模型规模重新调 optimizer 超参数？
- **对分享的价值：** 防止把历史讲成“第一篇错了，第二篇对了”。

### 延伸阅读

- [LLaMA](https://arxiv.org/abs/2302.13971)：为什么部署推理成本会让团队把小模型训练得更久。
- [The Llama 3 Herd of Models](https://arxiv.org/abs/2407.21783)：把“训练远超 compute-optimal token 数”放回具体模型家族和部署目标中看。
- [Beyond Chinchilla-Optimal](https://arxiv.org/abs/2401.00448)：把训练成本和未来推理需求放进同一个目标函数。

---

## 4. Scale data：更多数据不等于更多网页

### 先看辅助材料

- [FineWeb 交互图文](https://huggingface.co/spaces/HuggingFaceFW/blogpost-fineweb-v1)：顺着流程看网页提取、语言过滤、质量过滤、去重与 benchmark；它是具体数据工程案例，不是“唯一正确配方”。

### 必读

#### 4.1 GPT-3 supplementary material

- [补充材料](https://papers.neurips.cc/paper_files/paper/2020/file/1457c0d6bfcb4967418bfb8ac142f64a-Supplemental.pdf)
- **建议只读：** 数据集构建、Common Crawl filtering、deduplication 和 sampling 部分。
- **重点问题：** 为什么数据 scaling 同时包括数量、过滤、去重和重新加权？

#### 4.2 RefinedWeb

- [论文](https://arxiv.org/abs/2306.01116)
- **建议只读：** Abstract、数据处理流程和主要对比结果。
- **重点问题：** 在该论文训练的模型、benchmark 和 Pile-trained baselines 对比中，严格清洗的大规模网页语料表现如何？不要外推成“网页数据普遍优于精选语料”。

### 延伸阅读

- [Scaling Data-Constrained Language Models](https://arxiv.org/abs/2305.16264)：在论文的固定 compute 与数据分布条件下，最多重复约 4 epochs 时，相比拥有同量 unique data，loss 变化可以忽略；再增加 compute 的价值才逐渐衰减到零。不要把 4 epochs 讲成普适阈值。
- [Villalobos et al., 2024](https://proceedings.mlr.press/v235/villalobos24a.html)：高质量公开文本供给何时可能成为约束；预测依赖数据定义、增长趋势和训练配方。
- [Bartz v. Anthropic 2025 court order — Dkt. 231 PDF](https://cases.justia.com/federal/district-courts/california/candce/3%3A2024cv05417/434709/231/0.pdf)：只看书籍采购、扫描和影子图书馆事实，不需要深入法律争论。
- 本地摘要：[data-scaling.md](data-scaling.md)

---

## 5. 第三次改写：资源开始进入训练后的阶段

### 先看辅助材料

- **先分清流程：** [OpenAI — InstructGPT 图解](https://openai.com/index/instruction-following/) · [Hugging Face 中文 RLHF 导读](https://huggingface.co/blog/zh/rlhf)。前者对应具体论文，后者负责解释概念。
- **再理解推理预算：** [Hugging Face — Scaling test-time compute](https://huggingface.co/spaces/HuggingFaceH4/blogpost-scaling-test-time-compute) · [Noam Brown 访谈](https://sequoiacap.com/podcast/training-data-noam-brown/)。先用 “Bhutan 首都 vs. Sudoku” 建立直觉，再回论文看任务和 verifier 条件。

### 必读

#### 5.1 InstructGPT

- [论文](https://arxiv.org/abs/2203.02155)
- **建议只读：** Abstract、方法总览图、主要 human-evaluation 结果。
- **重点问题：** 为什么在论文使用的 OpenAI API prompt 分布和标注者偏好评测中，1.3B InstructGPT 可以胜过 175B GPT-3？这不是“较小模型整体能力更强”的证明。

#### 5.2 Snell et al. — Test-time compute

- [论文](https://arxiv.org/abs/2408.03314)
- **建议只读：** Abstract、Figure 1、不同题目难度下的结果、Discussion。
- **重点问题：** 在以数学等可验证任务为主的实验中，为什么 verifier-guided search 或自适应调整 response distribution 只在特定题目难度和策略下有效？test-time compute 不只是让模型“想得更久”。

### 延伸阅读

- [Scaling Laws for Reward Model Overoptimization](https://arxiv.org/abs/2210.10760)：在 synthetic gold-reward 实验中，持续优化不完美 proxy reward 为什么会降低 gold model score；它提示真实系统风险，但不直接测量“真实世界结果”。
- [Kimi k1.5](https://arxiv.org/abs/2501.12599)：实验室如何把 RL 描述成新 scaling axis；按公司自报材料阅读。
- 本地证据综述：[lifecycle-scaling.md](lifecycle-scaling.md)

---

## 6. 参数之外：检索、Agent 与环境

### 先看辅助材料

- [DeepMind — RETRO 图解](https://deepmind.google/blog/improving-language-models-by-retrieving-from-trillions-of-tokens/)：先看参数记忆与外部数据库的结构分工。
- [Google Research — ReAct 图解](https://research.google/blog/react-synergizing-reasoning-and-acting-in-language-models/) · [Anthropic — Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents)：前者解释 reasoning、action 与 observation 如何交错，后者帮助区分 workflow 和 agent；都不构成环境学习 scaling law 的证明。

### 必读

#### 6.1 RETRO

- [论文](https://arxiv.org/abs/2112.04426)
- **建议只读：** Abstract、Figure 1、主要 Pile 对比和局限。
- **重点问题：** 在论文使用的 Pile 对比和 2T-token retrieval database 下，RETRO 如何以约 25× 更少参数取得可比表现？不要把 25× 当成任意任务上的固定“参数兑换率”。

#### 6.2 AI Agents That Matter

- [论文](https://arxiv.org/abs/2407.01502)
- **建议只读：** Abstract、cost-controlled evaluation、Discussion。
- **重点问题：** 更复杂、更多调用的 agent 为什么可能被错误归因为“架构更智能”？

### 延伸阅读

- [ReAct](https://arxiv.org/abs/2210.03629)：reasoning traces、task-specific actions 与外部 observations 如何交错；它展示推理—行动结构，不等于证明模型从环境中持续学习。
- [Welcome to the Era of Experience — stable PDF](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf)：把它当研究议程，而不是已经成立的 scaling law。

---

## 7. 行业争论：Scaling 到底有没有“结束”

### 必读

#### 7.1 Demis Hassabis — Dwarkesh interview

- [访谈全文](https://www.dwarkesh.com/p/demis-hassabis) · [视频](https://www.youtube.com/watch?v=qTogNUV3CAI)
- **建议重点：** 先看视频 16:31–20:00 的 scaling/alignment 章节，或用页面章节和全文搜索定位 scaling 与 invention 需要同时推进的部分；不必看完约一小时的完整访谈。
- **阅读方式：** 把它当实验室负责人的战略判断，不当作科学证明。

#### 7.2 Dwarkesh Patel — Will scaling work?

- [文章](https://www.dwarkesh.com/p/will-scaling-work)
- **重点问题：** 数据是否足够、next-token loss 是否对应 generality、成本与可承受投入是否跟得上？
- **对分享的价值：** 它能帮助你理解为什么“scaling 有效”和“scaling 通向 AGI”是两个命题。

### 延伸阅读

- [Yann LeCun 访谈](https://lexfridman.com/yann-lecun-3-transcript/)：world model、memory 和 planning 的架构反方。
- [HN: Will scaling work?](https://news.ycombinator.com/item?id=38781484)：看工程社区如何争论；不要把评论当事实证据。

---

## 8. 开场素材：GPU、HBM 与 AI 基建

> 本节材料主要是 2024 年和 2025 年初的历史基线。可以用于解释机制，所有“当前收入、供给和价格”数字都应在发布前刷新。

### 先看辅助材料

- [Epoch AI — Can AI Scaling Continue Through 2030?](https://epoch.ai/publications/can-ai-scaling-continue-through-2030)：用其分类框架理解电力、芯片制造、数据和延迟约束；具体预测是情景分析，不是确定结果。
- [NVIDIA H200 产品页](https://www.nvidia.com/en-us/data-center/h200/)：只用来建立 HBM 容量、带宽和 GPU 封装的量级直觉。

### 必读

#### 8.1 NVIDIA FY2025 results

- [财报材料](https://investor.nvidia.com/news/press-release-details/2025/NVIDIA-Announces-Financial-Results-for-Fourth-Quarter-and-Fiscal-2025/)
- **重点看：** Data Center 收入及增长；不要从收入直接跳到 scaling law。

#### 8.2 Micron FY2025 Q2 prepared remarks

- [官方 PDF](https://s25.q4cdn.com/621799436/files/doc_financials/2025/q2/Micron_FY25_Q2_Prepared_Remarks_2-1.pdf)
- **重点看：** Micron 估计，在相同 bit output 下，HBM3E 所需 silicon 约为 DDR5 的 3×。
- **阅读边界：** 这是公司披露的 trade ratio，不是固定的成本、晶圆、封装投入或 DRAM 替代比例。
- **对分享的价值：** 解释为什么 HBM 需求可能挤占普通 DRAM 的硅资源。

### 延伸阅读

- [NVIDIA H200 specification](https://www.nvidia.com/en-us/data-center/h200/)：HBM 容量和带宽的具体例子。
- [SK hynix FY2024 results](https://news.skhynix.com/en/sk-hynix-announces-4q24-financial-results/)：HBM 对收入结构的影响。
- [Amazon 2024 Annual Report](https://s2.q4cdn.com/299287126/files/doc_financials/2025/ar/Amazon-2024-Annual-Report.pdf) · [Q4 2024 earnings call](https://ir.aboutamazon.com/events/event-details/2025/Q4-2024-Amazoncom-Inc-Earnings-Conference-Call/default.aspx)：用 capex、基础设施和需求表述补充云厂商视角，不能把全部资本开支都归为训练。
- [Samsung Q1 2025 results](https://news.samsung.com/global/samsung-electronics-announces-first-quarter-2025-results)：补充供应商对 HBM 产品节奏和市场需求的同期表述。
- 本地证据综述：[ai-infrastructure-and-hbm.md](ai-infrastructure-and-hbm.md)

---

## 中文技术补课（可选，不计入主路线）

- [Stanford CS336 2026 Lecture 9 中文讲义](https://yulong-ge.github.io/open-course-notes/courses/stanford-cs336-2026/lecture09-scaling-laws/)：适合系统补 Kaplan、Chinchilla、IsoFLOP 和外推边界。它是基于官方课程材料、使用 AI 辅助整理的非官方讲义，并非 Stanford 官方译本；关键数字仍回官方课件或论文。
- [Datawhale Diy-LLM 第 9 章 — Scaling Laws](https://datawhalechina.github.io/diy-llm/chapter9/chapter9_Scaling_Laws.html)：适合从公式过渡到实际拟合实验；把 `20 tokens/parameter` 当教学基线，不当通用常数。
- [Hands-on Modern RL — Test-Time Scaling](https://walkinglabs.github.io/hands-on-modern-rl/chapter19_reasoning/test-time-scaling)：用并行采样、反复修订和树搜索解释“推理预算花在哪里”。它是二手开源教材，定量结论仍回 Snell 等原论文。

---

## 建议阅读节奏

### 第一轮：约 1.5–2 小时，只建立直觉

走开头的辅助路线。视频只看片段，交互图文只看流程和图；记下仍不理解的概念，不在这一轮追公式。

### 第二轮：约 2–3 小时，分两次回看证据

先读“8 项讲稿骨架”，只看 Abstract、Introduction、关键图、实验条件和 Conclusion；各节其他“必读”不再整批通读，只按讲稿实际涉及的章节补 1–2 项。每看到一个适合放进幻灯片的数字，同时记下它的任务、模型、数据和比较对象。

### 第三轮：围绕你的讲稿补洞

- 不会解释直觉：回到第 1 部分。
- Kaplan/Chinchilla 说不清：读第 2–3 部分。
- 想加入 Anthropic/OpenAI 数据故事：读第 4 部分。
- 想讲新的 scaling axis：读第 5–6 部分。
- 想处理“scaling 已死”争论：读第 7 部分。
- 要制作股票/HBM 开场：读第 8 部分，并在发布前刷新行情和财报。

完整的 124 项去重证据来源仍保留在 [ALL_SOURCES.md](ALL_SOURCES.md)，需要追查某个具体 claim 时再查，不建议从头读到尾。124 项按作品去重，同一作品的论文、官方博客、视频或镜像会合并计数；部分纯教学新增链接未单列为证据项。
