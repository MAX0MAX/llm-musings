# Kaplan 与 Chinchilla 是否真是 scaling-law 历史转折？

> 研究日期：2026-08-24
> 范围：neural/language-model scaling 的科学史、训练资源分配与公开可核验的产业实践
> 人名说明：Kaplan 指 Jared Kaplan 等人的论文；Chinchilla 是 Hoffmann et al. 训练的模型及其论文的通称，论文第一作者是 Jordan Hoffmann。

## 裁决

**组合裁决：保留为关键转折，但必须降权 Kaplan 的“原创起点”和具体配方，并补充前史、复现修正与 inference-optimal 后史；不建议完全替换 Kaplan → Chinchilla 主线。**

更准确的四段式历史是：

1. **Hestness / Rosenfeld 等建立前史：** 深度学习的误差随数据和模型规模呈可预测幂律、可以从小实验外推，并非 Kaplan 首创。
2. **Kaplan 将方法集中到 Transformer LM 并工程化：** 系统测量参数、数据、训练算力、batch/steps 与 loss 的关系，给出固定训练算力下的资源分配；GPT-3 随后把可预测 loss 的范围再延伸两个数量级。
3. **Hoffmann et al. 用 Chinchilla 改写训练算力分配：** 同等训练 FLOPs 下，70B/1.4T-token Chinchilla 超过 280B Gopher，说明当时多数旗舰模型参数过多、训练 token 过少。
4. **后 Chinchilla 时代把“最优”改成目标相关：** PaLM 2 独立支持参数与数据近似同比增长；LLaMA、Llama 3 则为降低长期推理成本而主动把小模型训练得远超 Chinchilla 的训练-compute 最优点。数据质量、重复、tokenizer、MoE 和部署请求量都会改变配方。

因此，两篇论文的地位不同：

- **Kaplan 的历史重要性主要来自“聚焦、定量化、可操作化与传播”，而不是发现了第一个 neural scaling law。** 其 loss scaling 与小规模预测思想影响持久；其 `N ∝ C^0.73`、`D ∝ C^0.27` 资源分配已不应作为正确配方教授。
- **Chinchilla 是更扎实的训练策略转折。** 它不仅拟合曲线，还以同训练算力的完整大模型对照验证了“更小模型 + 更多 token”；PaLM 2、两项 2024 独立研究及后续训练报告提供了外部支持。但“20 tokens per parameter”只应称为特定 tokenizer、数据、架构与目标下的经验基线。

## 证据强弱总览

| 判断 | 证据强度 | 理由与边界 |
| --- | --- | --- |
| Kaplan 之前已有 neural/LM scaling 工作 | **强** | Hestness 2017 直接覆盖语言模型等四个领域；Rosenfeld 2019 给出模型规模与数据规模的联合误差面。 |
| Kaplan 使 Transformer LM loss scaling 更系统、可用于训练规划 | **强** | 原论文直接测量 `N/D/C`、过拟合、batch、steps 和固定 compute 分配；GPT-3 原论文将预测曲线外推两个数量级。 |
| Kaplan 的配方直接决定 GPT-3 的 175B/300B 设计 | **中等，不能写成已证明因果** | 两篇论文作者高度重叠，GPT-3 明确验证 Kaplan 曲线；Chinchilla 也把 GPT-3 训练设置称为后续模型遵循的范式。但 GPT-3 报告没有说“175B 是由 Kaplan 公式计算得出”，可靠公开访谈证据也有限。 |
| Kaplan 强化了 GPT-3 时代“优先增参数”的实践 | **中强** | Chinchilla 对 GPT-3、Gopher、MT-NLG 等公开设置的汇总显示多数约训练 300B token，并明确写作“following Kaplan … and GPT-3”；这支持实践相关性，但不能证明每个实验室的内部决策链。 |
| Chinchilla 修正了参数/token 分配 | **强** | 400+ 训练观测、三种估计方法和 70B 对 280B 的同 FLOPs 大模型验证。 |
| Chinchilla 降低推理成本并改变部署取舍 | **强** | 原论文直接比较内存与 inference FLOPs；LLaMA 与 Llama 3 明确把推理预算纳入模型大小选择。 |
| 约 1:1 的参数/数据增长趋势可复现 | **中强** | PaLM 2 在不同数据混合和更大 compute 上独立得到相近结论；Porian et al. 与 Pearce & Song 从不同角度解释 Kaplan/Chinchilla 差异并支持 Chinchilla。仍受实验设置和参数定义影响。 |
| `20 tokens/parameter` 是今天通用最优值 | **弱/否定** | Chinchilla 自身 Approach 3 的公布系数有拟合问题；复拟合约为 20–26，但部署、数据质量、重复和 tokenizer 会移动最优点。现代小模型常主动远超 20。 |
| 现代 frontier labs 仍使用 scaling laws | **强，但公开范围不完整** | GPT-4、PaLM 2、DeepSeek LLM、Llama 3 均公开小模型外推或自拟合；闭源实验室未披露具体配方不能被解释为“未使用”。 |

## 1. Kaplan 之前：不是一片空白

### 1.1 Hestness et al. 2017 已有跨领域幂律与 LM 结果

[Deep Learning Scaling is Predictable, Empirically](https://arxiv.org/abs/1712.00409) 在机器翻译、语言建模、图像分类和语音识别中研究了训练集规模与泛化误差、最优模型规模的关系。论文明确报告：

- 测试领域中的泛化误差随训练样本量呈经验幂律；
- word/character LM 的 learning curves 尤其稳定、可预测；
- 达到给定数据规模下最佳误差的模型大小也随数据增长；
- 指数需经验估计，已有简单理论不能解释真实任务中较小的指数。

这已经包含“从小规模实验预测更大规模结果”的核心思想。2019 年的 [Beyond Human-Level Accuracy](https://arxiv.org/abs/1909.01736) 还把这些曲线用于估计达到预定能力目标所需的数据、模型和硬件资源。故 slide 若暗示“Kaplan 前只能豪赌、没有可预测曲线”，历史上过强。

### 1.2 Rosenfeld et al. 2019 已有联合模型/数据误差面

[A Constructive Prediction of the Generalization Error Across Scales](https://arxiv.org/abs/1909.12673) 明确提出同时依赖模型规模和数据规模的联合函数，并在 vision 与 language、不同架构上测试从小到大的外推。它的重要性在于：Kaplan 不是第一个把 `loss/error = f(model size, data size)` 当成联合经验面来处理的工作。

不过 Rosenfeld 的范围更广、更抽象，未像 Kaplan 那样围绕 autoregressive Transformer LM、训练 FLOPs、batch/steps 和 GPT 级规划形成一套完整操作框架。

### 1.3 OpenAI 自身也有训练系统化前史

[An Empirical Model of Large-Batch Training](https://arxiv.org/abs/1812.06162)（Sam McCandlish、Jared Kaplan、Dario Amodei 等）用 gradient noise scale 预测最大有效 batch，并建立 compute efficiency 与 wall-clock efficiency 的权衡。[AI and Compute](https://openai.com/index/ai-and-compute/) 则记录了 2012–2018 大型训练运行算力的快速增长。

二者都不是 LM loss scaling law，但说明 Kaplan 2020 是同一研究计划的延续：把昂贵训练从“调参艺术”变成可测量的工程系统，而非突然出现的单篇发现。

### 1.4 Kaplan 真正新增了什么

[Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361) 的独特组合贡献是：

1. **对象聚焦：** autoregressive Transformer LM，loss 跨参数 `N`、数据 `D`、训练 compute `C` 多个数量级呈平滑幂律。
2. **联合工程问题：** 同时讨论过拟合、样本效率、batch、optimization steps 与训练 compute，而不只是一条 data-learning curve。
3. **可执行配方：** 在其定义与实验条件下，固定训练 compute 时主张参数增长快于 token：约 `N ∝ C^0.73`、`D ∝ C^0.27`，超大模型应在收敛前较早停止。
4. **可外推性示范：** 论文声称架构 depth/width 在较宽范围内影响弱于 scale；这为昂贵单次大训练提供了前期预测框架。
5. **研究传播：** 同团队随后把方法扩展到图像、视频、多模态和数学的 [Scaling Laws for Autoregressive Generative Modeling](https://arxiv.org/abs/2010.14701)，使“scaling laws”成为跨生成建模的共同研究语言。

科学史上应将 Kaplan 描述为 **LM scaling 的系统化与普及节点**，而不是起点。

## 2. Kaplan 与 GPT-3：真实联系在哪里，证据缺口又在哪里

### 2.1 可以直接确认的联系

[GPT-3 论文](https://arxiv.org/abs/2005.14165) 的 Figure 3.1 明确说，训练 compute 与 cross-entropy loss 的幂律趋势在 Kaplan 的基础上又延伸了两个数量级，只有很小偏差。它还显示较低 loss 通常伴随广泛任务表现提升，但没有把每一项能力都说成可预测。

两篇论文的团队高度重叠：Tom Brown、Jared Kaplan、Sam McCandlish、Alec Radford、Dario Amodei 等同时参与。时间、作者和 GPT-3 对 Kaplan 曲线的直接检验，使“Kaplan 与 GPT-3 项目紧密相连”成为强判断。

Hoffmann et al. 2022 进一步写道，**“Following Kaplan et al. and the training setup of GPT-3”**，当时多数大型 dense LM 约训练 300B tokens，并把这视为主要增加参数的路径。这是同业原论文对实践模式的直接历史归纳。

### 2.2 不能从公开材料确认的更强说法

公开的一手材料不足以证明：

- 175B 参数是由 Kaplan 的 `C^0.73` 公式直接算出的唯一选择；
- 没有 Kaplan 论文，GPT-3 就不会被训练；
- 整个产业的大规模资本开支由这一篇论文触发。

GPT-3 报告没有给出这样的内部决策记录。媒体与后来的口述史常把“论文发布五个月后 GPT-3 出现”写成直接因果，但时间先后、团队重叠与曲线验证只能支持“密切相关”，不能独立证明“公式决定设计”。

### 2.3 对训练实践的影响应拆成两层

- **持久层：预测式工程。** GPT-4 报告称，团队从 compute 少 1,000–10,000 倍的模型预测最终 loss，并从少 1,000 倍 compute 的实验预测 HumanEval 子集表现。这与 Kaplan 的核心方法连续，是很强的实际影响证据。
- **被推翻层：具体资源分配。** 参数比数据增长快、较早停止的具体公式在 Chinchilla 后失去主导地位；2024 两项独立研究也将差异归因于参数/算力计数、规模区间、warmup 与 optimizer tuning。

所以 slide 8 可以说 Kaplan 让 scaling 成为训练规划工具，但不应把已过时配方与持久方法混为一谈。

## 3. Chinchilla 到底修正了什么

### 3.1 修正的不是“scale 是否有效”，而是固定训练 FLOPs 怎么分

[Training Compute-Optimal Large Language Models](https://arxiv.org/abs/2203.15556) 研究固定训练 compute 下的 `N` 与 `D` 分配。其主要结果：

- 训练 400+ 个模型/训练配置，模型约 70M–16B，训练 5B–500B tokens；
- 三种估计方法都指向参数量与训练 token 随 compute 近似等比例增长；
- 以 Gopher 训练 FLOPs 为预算，预测约 40–70B 参数而不是 280B，并应使用约四倍数据；
- 实际训练 70B Chinchilla、约 1.4T tokens，与 280B Gopher 使用近似相同训练 FLOPs；
- Chinchilla 在论文评测的大量任务上超过 Gopher，也超过若干更大的同期模型；
- 参数小四倍直接减少模型内存、fine-tuning 与每 token 推理成本。

最强证据不是一条拟合线，而是 **同训练算力的大模型对照**。这使 Chinchilla 比单纯公式修订更有历史说服力。

### 3.2 “约 20 tokens/parameter”的准确含义

70B × 20 ≈ 1.4T，因此 Chinchilla 的实际训练点形成著名的 20:1 heuristic。它回答的是：

> 在该数据分布、dense Transformer、tokenizer、训练目标、优化流程和 FLOP 记账方式下，仅以固定预训练算力最小化语言建模 loss 时，什么 `N/D` 分配接近最优？

它**不**直接回答：

- 生命周期总成本（训练 + 数十亿次推理）最低；
- 固定延迟、显存、模型下载大小或设备条件下最优；
- 数据重复、质量差异、合成数据和多语言混合下最优；
- MoE 的 total parameters、active parameters 应如何计数；
- downstream benchmark、对齐后模型或商业效用最优。

### 3.3 对训练和部署的实际影响

影响不是“所有模型改成 20:1”，而是两个更持久的决策变化：

1. **训练规划不能只看参数。** Google 的 [PaLM 2 报告](https://arxiv.org/abs/2305.10403) 在不同数据混合和更大 compute 上复做 IsoFLOPs，明确验证 `N` 与 `D` 约 1:1 增长，并指出 PaLM 2 最大模型比 PaLM 最大模型小、但使用更多训练 compute。
2. **训练最优与部署最优分离。** [LLaMA](https://arxiv.org/abs/2302.13971) 明确说，虽然 Chinchilla 建议 10B/200B tokens，7B 在 1T tokens 后仍改善；为了给定 inference budget 的最佳表现，应训练更小模型更久。[Llama 3](https://arxiv.org/abs/2407.21783) 更明确：405B 旗舰接近团队自拟合的 compute-optimal 点，而 8B/70B 刻意训练远超 compute-optimal，因为同推理预算下更好。

Chinchilla 因此既纠正了“大参数优先”，也暴露了新问题：训练一次的最优点不是服务数亿请求的最优点。

## 4. 后续复现、修正与质疑

### 4.1 Chinchilla 自身拟合并非无瑕

[Besiroglu et al. 2024](https://arxiv.org/abs/2404.10102) 从图中重建 Chinchilla Approach 3 数据并复拟合，发现：

- 论文正文公布的 Approach 3 参数有舍入与 optimizer early-stopping 问题；
- 原文极窄置信区间不可信；按其估算，达到相近宽度需要远多于实际 400+ 的观测；
- 公布的 Approach 3 参数实际上导出约 70 tokens/parameter，与论文 Approaches 1/2 及实际 Chinchilla 20:1 不一致；
- 修正拟合后约为 25.6 tokens/parameter，仍与“约 20”同一数量级。

这不是推翻 Chinchilla 的方向性结论，而是把精确常数和不确定性显著降级。

### 4.2 两项独立工作更直接地解释 Kaplan–Chinchilla 差异

- [Porian et al. 2024](https://arxiv.org/abs/2406.19146) 在 OpenWebText2 与 RefinedWeb 上重现 Kaplan 式结果，逐项修正 decoding layer FLOPs、固定 warmup 对小模型的不利影响、scale-dependent optimizer tuning 后，与 Chinchilla 很接近；它还发现精确匹配 cosine decay 并不是关键。
- [Pearce & Song 2024](https://arxiv.org/abs/2406.12907) 从另一方向说明，Kaplan 只计 non-embedding parameters 且研究尺度较小，会产生局部约 0.74–0.78 的指数；改用 total parameters 后接近 Chinchilla 的 0.50。

两者共同说明：Kaplan 的错误配方主要是实验设计、计数和局部拟合造成，不是“2020 的模型有不同自然定律”。

### 4.3 数据约束、重复和质量

[Scaling Data-Constrained Language Models](https://arxiv.org/abs/2305.16264) 用 400+ runs 研究重复数据：在其设置下，最多约四个 epoch 的重复与同量 unique data 的 loss 差异可很小，但更多重复的边际价值最终衰减。原始 token 数因此不能始终当作等价的新信息。

[DeepSeek LLM](https://arxiv.org/abs/2401.02954) 则发现不同数据集导出的 scaling law 有明显差异；数据质量更高时，最优预算可更多分给模型而非 token 数。它还用 non-embedding FLOPs/token 取代简单参数量，以处理 attention 等未被 `6ND` 精确覆盖的成本。

这些结果反对把所有 token 等价地塞进 20:1。

### 4.4 推理需求改变“最优”

[Beyond Chinchilla-Optimal](https://arxiv.org/abs/2401.00448) 把推理请求量加入成本函数，并训练 47 个模型验证。其结论是：当预期推理量很高时，训练更小模型、使用远多于 Chinchilla 的 token 可以降低全生命周期 FLOPs/成本；实验观察到 tokens/parameter 达 10,000 时仍有改善，但作者也警告外推到极端比例的拟合可靠性。

这不是说“越过 20 永远免费”，而是说最优目标从 `min pretraining loss | training FLOPs` 改成 `min train + serve cost | target quality and demand` 后，数学问题已经不同。

### 4.5 tokenizer 使“token”本身不稳定

Meta 的 2026 [Compute Optimal Tokenization](https://arxiv.org/abs/2605.01188) 在可控压缩率的 tokenizer 上训练 988 个模型，主张跨 tokenizer 更稳定的量是 bytes/parameter，而不是 tokens/parameter；对其英语数据，约为 60 bytes/parameter。该结果仍需更多独立复现，但它直接说明 20:1 隐含固定 tokenizer 压缩率，不能当自然常数。

## 5. 现代 frontier labs：采用、引用还是偏离

### OpenAI

- [GPT-4 Technical Report](https://arxiv.org/abs/2303.08774) 是最强的公开采用证据：从小 1,000–10,000 倍 compute 的模型预测最终 loss，并预测 HumanEval 子集表现。
- 报告没有公开 `N/D`、token 数与具体 compute-optimal 配方，因此不能判断 GPT-4 是否按 20:1 训练。
- 结论：**明确采用预测式 scaling；资源分配不透明。**

### Google / DeepMind

- Chinchilla 是内部对 Gopher 的直接修正。
- PaLM 2 在不同数据混合、更大 compute 下重新做 IsoFLOPs，得到约 1:1 参数/数据增长。
- 结论：**公开证据最强的 Chinchilla 方向独立验证与实际模型改变。**

### Meta

- LLaMA 直接引用 Chinchilla，但明确为 inference budget 训练小模型更久。
- Llama 3 自建 scaling-law sweep：40M–16B 小模型、多个 compute 档位，外推 405B/约 16T；预测约 402B/16.55T，最终选 405B/15.6T。与此同时把 8B/70B 训练远超 compute-optimal。
- 结论：**旗舰模型使用团队特定 compute-optimal 规划，小模型有意偏离 20:1 以优化推理。** 这比“行业抛弃 Chinchilla”更准确。

### DeepSeek

- DeepSeek LLM 明确不直接照抄 Kaplan/Chinchilla 常数，而是为自身数据、架构、batch 与 learning rate 拟合 scaling laws。
- 结论：**采用方法论，偏离通用参数计数和固定常数。**

### Anthropic

- [Predictability and Surprise in Large Generative Models](https://arxiv.org/abs/2202.07785) 明确承认 broad-distribution loss 可预测、具体能力和输出难预测。
- Claude frontier 训练数据、参数和资源分配未充分公开，不能从其一般研究立场反推实际训练配方。
- 结论：**研究语言上采用；无法从公开资料核验 Claude 的实际配方。**

总的说，现代实验室没有把 Kaplan 或 Chinchilla 当固定 cookbook。它们保留的是流程：

> 在自家 architecture × optimizer × tokenizer × data mix × hardware × deployment objective 上做较小规模 sweep，拟合局部规律，再外推并留出安全裕量。

## 6. 历史重要性究竟来自哪里

### Kaplan

- **科学贡献：中强。** Transformer LM 上的大范围系统测量、联合工程变量与可操作 compute 分配是真贡献；但幂律、learning curve、联合模型/数据误差面已有前史。
- **产业改变：中等。** 与 GPT-3 团队和训练实践关系密切，GPT-3 直接延伸其曲线；但公开证据不足以把 GPT-3 或数千亿美元投入归因给单篇论文。
- **传播与叙事：强。** “一条平滑曲线让大训练可预测”非常易传播，也容易遮蔽 Hestness、Rosenfeld 与 OpenAI 2018 的连续研究计划。
- **今天仍有效的部分：强。** 小模型外推 loss、用 scaling sweep 规划昂贵训练。
- **今天已失效的部分：强否定。** `C^0.73/C^0.27` 作为通用 compute-optimal 配方。

### Chinchilla

- **科学贡献：强。** 更适当的实验 sweep、三种方法、完整 70B 模型与同 FLOPs 对照。
- **产业改变：强。** PaLM 2、LLaMA、Llama 3 的一手报告均明确回应其问题设定；后续模型普遍更重视 token、数据质量与推理成本。
- **传播与叙事：也很强。** 20:1 是方便口号，但传播时经常丢掉目标函数和 tokenizer 条件。
- **今天仍有效的部分：中强。** 在固定预训练 FLOPs、相近 dense LM 设置下，参数与新数据大体同比扩展是可靠基线。
- **今天不应保留的部分：强否定。** 20:1 是跨 tokenizer、数据质量、架构和部署目标的常数。

## 7. 是否有更合适的替代主线

### 不建议完全替换

Kaplan → Chinchilla 仍是 20–30 分钟演讲中最清楚的资源分配反转：相同筹码从“参数”移到“数据”，而且有 Chinchilla/Gopher 同 FLOPs 对照。没有另一对论文同时具备如此清晰的公式冲突、实验验证和公开产业后续。

### 建议替换“英雄论文史”为“方法演化史”

推荐叙事：

> **Hestness/Rosenfeld：可预测曲线已有前史 → Kaplan/GPT-3：把 LM scaling 变成大训练规划工具 → Chinchilla：配方可被更好的实验推翻 → LLaMA/Llama 3：目标函数加入推理成本后又主动偏离训练最优。**

如果必须只增加一个事件，优先增加 **LLaMA 2023**，而不是另一篇纯 scaling 论文。它第一次把“为什么要超过 Chinchilla-optimal”说得极清楚：训练多花一次，换取每次推理都更便宜。这也自然引向当前 slides 10–13 的“scale 整个生命周期”。

## 对 slides 7–10 的具体修改建议

### Slide 7：固定算力筹码

保留视觉，但把口述问题改为：

> “先固定**预训练 FLOPs**。在相同架构、数据质量和 tokenizer 下，参数与 token 怎么分？注意：这还没有计算未来的推理账单。”

页面角落加三个小条件：`same training compute`、`same data regime`、`minimize pretraining loss`。这样 slide 9 的 Chinchilla 和 slide 10 的部署偏离不会互相矛盾。

### Slide 8：Kaplan 不应写成 scaling 的起点

建议标题从：

> **2020：Kaplan 的答案偏向更大的模型**

改为：

> **2020：Kaplan 把 LM scaling 变成了训练规划工具**

正文改为：

- 前史已有 Hestness 的 learning curves 与 Rosenfeld 的联合模型/数据预测；
- Kaplan 在 Transformer LM 上系统连接参数、数据、训练 compute 与 loss；
- 其固定 compute 配方强烈偏向增大参数、较早停止；
- GPT-3 将预测曲线再延伸两个数量级，但公开资料不能证明 175B 是公式直接算出的。

视觉上可在页面顶部加很小的前史线：`2017 Hestness → 2019 Rosenfeld → 2020 Kaplan/GPT-3`，避免“单篇论文发明领域”。

删除或降级“这套结果强化了行业对大模型路线的信心”。若保留，口述应改成：

> “它与 GPT-3 及随后约 300B-token 的大参数训练范式相符；但我们没有每家实验室内部决策的公开记录。”

### Slide 9：保留 Chinchilla 为强反转，但补一句方法原因

建议标题：

> **2022：Chinchilla 证明，当时的大模型普遍读得太少**

正文保留 70B/1.4T 对 280B Gopher、同训练 FLOPs，并增加：

- 不是只重画曲线：团队真的训练了 Chinchilla 验证；
- 参数与 token 随 compute 近似同比增长得到 PaLM 2 与 2024 独立研究支持；
- “约 20 tokens/parameter”只放脚注：`baseline, not constant`。

不要说 Chinchilla “推翻 Kaplan scaling law”；应说它推翻 Kaplan 的 **compute-allocation prescription**，而非平滑 loss scaling 或小规模外推方法。

### Slide 10：从“参数不是全部”升级为“三种最优”

建议标题：

> **最优配方取决于你在优化哪张账单**

用三个并列筹码框替代宽泛系统清单：

1. **Training-optimal：** 固定预训练 FLOPs，Chinchilla 是基线；
2. **Inference-optimal：** 请求很多时，LLaMA/Llama 3 选择更小模型、更多 token；
3. **Data/architecture-specific：** 数据质量、重复、tokenizer、MoE/active parameters 会移动最优点。

保留 retrieval、context、post-training 等内容可移到 slide 11。Slide 10 的任务应是完成 Kaplan → Chinchilla → 现代偏离的闭环，而不是一次展开所有系统组件。

## 最重要的 8 条来源

1. [Hestness et al., **Deep Learning Scaling is Predictable, Empirically** (2017)](https://arxiv.org/abs/1712.00409) — Kaplan 前史的最关键原论文；直接含 language modeling。
2. [Kaplan et al., **Scaling Laws for Neural Language Models** (2020)](https://arxiv.org/abs/2001.08361) — LM loss scaling、sample efficiency 与原始 compute-allocation 配方。
3. [Brown et al., **Language Models are Few-Shot Learners** (GPT-3, 2020)](https://arxiv.org/abs/2005.14165) — Kaplan 曲线在更大 compute 上延伸的直接证据。
4. [Hoffmann et al., **Training Compute-Optimal Large Language Models** (2022)](https://arxiv.org/abs/2203.15556) — Chinchilla 原论文与 Gopher 同 FLOPs 对照。
5. [Anil et al., **PaLM 2 Technical Report** (2023)](https://arxiv.org/abs/2305.10403) — 不同数据混合、更大 compute 下对近 1:1 增长的实验室独立验证。
6. [Touvron et al., **LLaMA: Open and Efficient Foundation Language Models** (2023)](https://arxiv.org/abs/2302.13971) — 为推理预算主动超过 Chinchilla training-optimal 的关键一手证据。
7. [Porian et al., **Resolving Discrepancies in Compute-Optimal Scaling of Language Models** (2024)](https://arxiv.org/abs/2406.19146) — 独立重现并分解 Kaplan/Chinchilla 差异。
8. [Dubey et al., **The Llama 3 Herd of Models** (2024)](https://arxiv.org/abs/2407.21783) — 现代实验室自拟合 scaling、旗舰 compute-optimal 与小模型 inference-optimal 并存的最佳公开案例。

## 完整来源清单与核验限制

本研究实际采用 **23 个独立来源**：22 个原论文、模型技术报告或实验室官方材料，外加 1 个历史综述用于交叉检查；最重要的 8 个见上。除上述来源外，还使用：

9. [Rosenfeld et al., A Constructive Prediction of the Generalization Error Across Scales (2019)](https://arxiv.org/abs/1909.12673)
10. [McCandlish et al., An Empirical Model of Large-Batch Training (2018)](https://arxiv.org/abs/1812.06162)
11. [Hestness et al., Beyond Human-Level Accuracy (2019)](https://arxiv.org/abs/1909.01736)
12. [Henighan et al., Scaling Laws for Autoregressive Generative Modeling (2020)](https://arxiv.org/abs/2010.14701)
13. [OpenAI, GPT-4 Technical Report (2023)](https://arxiv.org/abs/2303.08774)
14. [Ganguli et al., Predictability and Surprise in Large Generative Models (2022)](https://arxiv.org/abs/2202.07785)
15. [Muennighoff et al., Scaling Data-Constrained Language Models (2023)](https://arxiv.org/abs/2305.16264)
16. [Sardana et al., Beyond Chinchilla-Optimal (2024)](https://arxiv.org/abs/2401.00448)
17. [Besiroglu et al., Chinchilla Scaling: A Replication Attempt (2024)](https://arxiv.org/abs/2404.10102)
18. [Pearce & Song, Reconciling Kaplan and Chinchilla Scaling Laws (2024)](https://arxiv.org/abs/2406.12907)
19. [DeepSeek-AI, DeepSeek LLM (2024)](https://arxiv.org/abs/2401.02954)
20. [Meta AI, Compute Optimal Tokenization (2026)](https://arxiv.org/abs/2605.01188)
21. [Epoch AI, Scaling Laws Literature Review](https://epoch.ai/publications/scaling-laws-literature-review) — 历史定位辅助，不替代原论文。
22. [Google DeepMind, An Empirical Analysis of Compute-Optimal Large Language Model Training](https://deepmind.google/blog/an-empirical-analysis-of-compute-optimal-large-language-model-training/) — 官方发布说明，用于核对团队对推理成本与结果的表述。
23. [OpenAI, AI and Compute (2018)](https://openai.com/index/ai-and-compute/) — 训练算力快速增长的历史背景；不是 loss scaling law。

所有网页链接于 **2026-08-24** 核验。没有使用媒体重复报道作为产业影响证据，也没有使用引用量作判断：本次未对 OpenAlex、Google Scholar、Semantic Scholar 等数据库做统一、可复现的同日引用量查询；不同数据库覆盖和合并规则差异大，而且引用量至多是传播的弱指标。

主要限制：

- OpenAI、Anthropic、Google 等未公开最新 frontier 模型的完整参数量、token 数、数据质量和训练 FLOPs，不能验证其是否贴近 20:1。
- 公司报告是其训练策略的一手证据，但自报 benchmark 不能单独证明跨实验室普适性。
- 多数 scaling 研究仍在远小于 frontier 的模型上拟合再外推；架构、optimizer、tokenizer 与数据分布改变会引入 regime shift。
- 对 GPT-3 的内部立项和具体尺寸决策，公开材料能确认 Kaplan 曲线被验证和团队高度重叠，但缺少可审计的内部决策记录；因此本文拒绝“Kaplan 公式直接造出 GPT-3”的强因果说法。
