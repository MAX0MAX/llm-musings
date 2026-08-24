# Scaling Laws 阅读清单

这不是完整 bibliography，而是一条为准备 20–30 分钟科普分享设计的阅读路线。每部分只有 1–2 个必读材料；论文不需要逐页精读，按下面标出的阅读重点即可。

## 如果只想先读 8 个

按这个顺序读，可以先形成完整叙事：

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

- [视频](https://www.youtube.com/watch?v=LPZh9BOjkQs) · [图文版](https://www.3blue1brown.com/lessons/mini-llm/)
- **时间：** 约 6 分钟
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
- **对分享的价值：** 为“loss 不是 intelligence”提供最直接的一手边界。

### 延伸阅读

- [Hestness et al., 2017](https://arxiv.org/abs/1712.00409)：Kaplan 之前的可预测 learning curves。
- [Rosenfeld et al., 2019](https://arxiv.org/abs/1909.12673)：模型规模与数据规模联合预测的前史。

---

## 3. 第二次改写：Kaplan 到 Chinchilla 为什么是转折

### 必读

#### 3.1 Hoffmann et al. — Training Compute-Optimal Large Language Models

- [论文](https://arxiv.org/abs/2203.15556)
- **建议只读：** Abstract、Introduction、Figure 1–3、Chinchilla 与 Gopher 对比、Conclusion。
- **重点问题：** 为什么相同训练 FLOPs 下，70B/1.4T-token 的 Chinchilla 能超过 280B Gopher？
- **阅读边界：** “20 tokens per parameter”是特定条件下的经验基线，不是自然常数。

#### 3.2 Porian et al. — Resolving Discrepancies in Compute-Optimal Scaling

- [论文](https://arxiv.org/abs/2406.19146)
- **建议只读：** Abstract、Introduction、Conclusion。
- **重点问题：** Kaplan 与 Chinchilla 的差异有多少来自参数计数、warmup、优化和拟合方法？
- **对分享的价值：** 防止把历史讲成“第一篇错了，第二篇对了”。

### 延伸阅读

- [LLaMA](https://arxiv.org/abs/2302.13971)：为什么部署推理成本会让团队把小模型训练得更久。
- [Beyond Chinchilla-Optimal](https://arxiv.org/abs/2401.00448)：把训练成本和未来推理需求放进同一个目标函数。

---

## 4. Scale data：更多数据不等于更多网页

### 必读

#### 4.1 GPT-3 supplementary material

- [补充材料](https://papers.neurips.cc/paper_files/paper/2020/file/1457c0d6bfcb4967418bfb8ac142f64a-Supplemental.pdf)
- **建议只读：** 数据集构建、Common Crawl filtering、deduplication 和 sampling 部分。
- **重点问题：** 为什么数据 scaling 同时包括数量、过滤、去重和重新加权？

#### 4.2 RefinedWeb

- [论文](https://arxiv.org/abs/2306.01116)
- **建议只读：** Abstract、数据处理流程和主要对比结果。
- **重点问题：** 大规模网页数据经过严格清洗后，能否超过人工混合的精选语料？

### 延伸阅读

- [Scaling Data-Constrained Language Models](https://arxiv.org/abs/2305.16264)：同一数据可以重复多少次，什么时候边际价值明显下降。
- [Bartz v. Anthropic 2025 court order](https://www.copyright.gov/fair-use/summaries/Bartz-v-Anthropic-PBC-787-F-Supp-3d-1007-ND-Cal-2025.pdf)：只看书籍采购、扫描和影子图书馆事实，不需要深入法律争论。
- 本地摘要：[data-scaling.md](data-scaling.md)

---

## 5. 第三次改写：资源开始进入训练后的阶段

### 必读

#### 5.1 InstructGPT

- [论文](https://arxiv.org/abs/2203.02155)
- **建议只读：** Abstract、方法总览图、主要 human-evaluation 结果。
- **重点问题：** 为什么较小模型经过 post-training 后，可以在人类偏好上超过更大的基础模型？

#### 5.2 Snell et al. — Test-time compute

- [论文](https://arxiv.org/abs/2408.03314)
- **建议只读：** Abstract、Figure 1、不同题目难度下的结果、Discussion。
- **重点问题：** 为什么“想得更久”只在特定难度、搜索策略和 verifier 条件下有效？

### 延伸阅读

- [Scaling Laws for Reward Model Overoptimization](https://arxiv.org/abs/2210.10760)：为什么更多 RL 优化可能让真实结果变差。
- [Kimi k1.5](https://arxiv.org/abs/2501.12599)：实验室如何把 RL 描述成新 scaling axis；按公司自报材料阅读。
- 本地证据综述：[lifecycle-scaling.md](lifecycle-scaling.md)

---

## 6. 参数之外：检索、Agent 与环境

### 必读

#### 6.1 RETRO

- [论文](https://arxiv.org/abs/2112.04426)
- **建议只读：** Abstract、Figure 1、主要 Pile 对比和局限。
- **重点问题：** 能力是否必须全部存进参数？扩大外部数据库能替代多少参数？

#### 6.2 AI Agents That Matter

- [论文](https://arxiv.org/abs/2407.01502)
- **建议只读：** Abstract、cost-controlled evaluation、Discussion。
- **重点问题：** 更复杂、更多调用的 agent 为什么可能被错误归因为“架构更智能”？

### 延伸阅读

- [ReAct](https://arxiv.org/abs/2210.03629)：reasoning、行动、检索和环境反馈如何组成闭环。
- [The Era of Experience](http://incompleteideas.net/papers/TheEraOfExperience.pdf)：把它当研究议程，而不是已经成立的 scaling law。

---

## 7. 行业争论：Scaling 到底有没有“结束”

### 必读

#### 7.1 Demis Hassabis — Dwarkesh interview

- [访谈全文](https://www.dwarkesh.com/p/demis-hassabis) · [视频](https://www.youtube.com/watch?v=qTogNUV3CAI)
- **建议重点：** scaling 与 invention 需要同时推进的部分。
- **阅读方式：** 把它当实验室负责人的战略判断，不当作科学证明。

#### 7.2 Dwarkesh Patel — Will scaling work?

- [文章](https://www.dwarkeshpatel.com/p/will-scaling-work)
- **重点问题：** 数据是否足够、next-token loss 是否对应 generality、经济回报是否跟得上？
- **对分享的价值：** 它能帮助你理解为什么“scaling 有效”和“scaling 通向 AGI”是两个命题。

### 延伸阅读

- [Yann LeCun 访谈](https://lexfridman.com/yann-lecun-3-transcript/)：world model、memory 和 planning 的架构反方。
- [HN: Will scaling work?](https://news.ycombinator.com/item?id=38781484)：看工程社区如何争论；不要把评论当事实证据。

---

## 8. 开场素材：GPU、HBM 与 AI 基建

### 必读

#### 8.1 NVIDIA FY2025 results

- [财报材料](https://investor.nvidia.com/news/press-release-details/2025/NVIDIA-Announces-Financial-Results-for-Fourth-Quarter-and-Fiscal-2025/)
- **重点看：** Data Center 收入及增长；不要从收入直接跳到 scaling law。

#### 8.2 Micron FY2025 Q2 prepared remarks

- [官方 PDF](https://investors.micron.com/static-files/52ce0c07-49dc-4eab-b1d2-a67bde373bca)
- **重点看：** HBM3E 相同 bit output 约需 3× DDR5 硅耗的公司表述。
- **对分享的价值：** 解释为什么 HBM 需求会影响普通 DRAM 资源。

### 延伸阅读

- [NVIDIA H200 specification](https://www.nvidia.com/en-us/data-center/h200/)：HBM 容量和带宽的具体例子。
- [SK hynix FY2024 results](https://news.skhynix.com/en/sk-hynix-announces-4q24-financial-results/)：HBM 对收入结构的影响。
- 本地证据综述：[ai-infrastructure-and-hbm.md](ai-infrastructure-and-hbm.md)

---

## 建议阅读节奏

### 第一轮：约 90 分钟

只读开头的 8 个材料；论文只读 Abstract、Introduction、关键图和 Conclusion。

### 第二轮：围绕你的讲稿补洞

- 不会解释直觉：回到第 1 部分。
- Kaplan/Chinchilla 说不清：读第 2–3 部分。
- 想加入 Anthropic/OpenAI 数据故事：读第 4 部分。
- 想讲新的 scaling axis：读第 5–6 部分。
- 想处理“scaling 已死”争论：读第 7 部分。
- 要制作股票/HBM 开场：读第 8 部分，并在发布前刷新行情和财报。

完整的 123 项去重来源仍保留在 [ALL_SOURCES.md](ALL_SOURCES.md)，需要追查某个具体 claim 时再查，不建议从头读到尾。
