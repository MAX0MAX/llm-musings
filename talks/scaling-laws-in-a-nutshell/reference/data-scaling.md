# Data Scaling：Anthropic 与 OpenAI 为什么需要海量、高质量训练数据

> 研究日期：2026-08-24
> 研究范围：数据需求、获取与扩展方式；版权诉讼仅用于厘清数据来源事实，不展开法律专题。
> 来源口径：优先法院文件、公司材料和论文；媒体只用于交叉核验或补充语境。下文将“诉讼指控”“公司披露或程序性承认”“法院在裁定中确认的事实”“媒体概括”分开表述。

## 一、结论摘要

### 1. 为什么前沿模型需要“海量”数据

数据不是算力之外的附属品，而是训练计算得以产生有效更新的另一项投入。

- **Compute-optimal scaling 要求数据量随模型规模一起增长。** Chinchilla 的核心结果是：在其研究范围和训练设置中，模型参数和训练 token 应大致同步扩展。70B 参数的 Chinchilla 用与 280B 参数 Gopher 相同的训练算力、但多约 4 倍的数据，整体表现更好。这直接否定了“只加参数即可有效 scale”的简单版本。
- **更大的模型会更快耗尽可重复利用的新信息。** 重复同一批数据前几轮仍有价值，但边际收益最终衰减。Muennighoff 等人的实验显示，约 4 个 epoch 内重复数据与新数据的 loss 差距很小；继续重复时，每个 token 的有效价值下降，增加计算最终接近无收益。
- **数据决定模型能学到什么分布。** 网页提供覆盖面，书籍提供长篇、编辑过的表达与连贯结构，代码和数学提供可验证的逻辑模式，人工反馈和合成样本则用于塑造特定行为。单纯统计 token 数无法表示这些差异。

### 2. 为什么还必须是“高质量”数据

原始互联网数据规模大，但包含重复、垃圾文本、模板页、错误、低信息密度内容和评测集污染。训练预算有限时，把算力花在低价值或重复 token 上，会降低每单位计算获得的学习信号。

- GPT-3 团队不是把 Common Crawl 原样送入模型，而是用高质量参考语料对网页进行质量筛选、做文档级模糊去重，再把 WebText、书籍语料和 Wikipedia 加入并提高采样权重。
- RefinedWeb 表明，“高质量”不必等于昂贵的人工精选合集：严格过滤和去重后的 Common Crawl 仍可得到数万亿 token，并在其实验中超过若干混合型精选语料训练的模型。
- Anthropic 的法院记录给出一个罕见的内部判断：公司逐渐认为书籍是构建世界级 LLM 最具成本效益的数据，并偏好“编辑会认可”的好写作、经过整理的事实与连贯叙事。这里能证明 Anthropic 如何评价书籍，不能证明每一本书对 Claude 的独立增益。

### 3. 两家公司实际怎样 scale data

共同模式不是“再爬一次网页”，而是同时扩展五个维度：

1. **覆盖面：** 公共网页、代码、数学、书籍、多模态内容。
2. **质量：** 分类、过滤、去重、重新加权、人工标注。
3. **稀缺领域：** 购买或授权非公开档案、专业知识和长篇内容。
4. **行为数据：** 人工训练者、红队、用户选择加入的数据、反馈数据。
5. **生成数据：** 用模型生成提示、答案、多语言样本或针对性安全样本，再筛选或验证。

Anthropic 的极端案例是购买数百万册纸质书、拆除装订、裁页扫描并丢弃纸本；OpenAI 的公开路径更容易观察到网页抓取、Books1/Books2、授权数据及一系列媒体和平台合作。两家公司都披露了去重/分类和内部生成数据，但都没有公开足以复现最新模型数据配方的完整清单或采样权重。

---

## 二、Anthropic：从影子图书馆到“买纸书再扫描”

### 2.1 法院已经确认到什么程度

2025 年 6 月 23 日，美国加州北区联邦地区法院在 **Bartz v. Anthropic** 的 fair-use 简易判决命令中写明：

- 2021 年初，Anthropic 联合创始人 Ben Mann 下载了 **Books3**，含 196,640 本书；命令称他知道这些是未经授权汇编的副本。
- 2021 年 6 月，Mann 下载了至少 **500 万**份来自 **Library Genesis（LibGen）** 的书籍副本。
- 2022 年 7 月，Anthropic 下载了至少 **200 万**份来自 **Pirate Library Mirror（PiLiMi）** 的书籍副本。
- 法院命令概括为 Anthropic 取得了 **超过 700 万**份盗版书籍副本。
- Anthropic 后续从这些库中选择不同的集合、子集或部分，加入不同 LLM 的训练 data mixes；不是所有下载的书都被证明进入了每一个模型。
- 2024 年，Anthropic 转向批量购买纸质书。法院称其花费“many millions of dollars”购买“millions of print books”，多为二手书；服务商拆除装订、裁切页面、扫描为带可机读文本的 PDF，然后丢弃纸本。

这些不是单纯的起诉书指控。该命令说明，Anthropic 为寻求简易判决，需要依赖无争议事实，或采用有利于对方的事实推断；法院据此写入上述事实并裁定：

- 为训练 LLM 而复制涉案作品，在该案记录和主张范围内属于 fair use；
- 把合法购买的纸本一对一替换成内部数字副本属于 fair use；
- 下载并永久保留盗版副本、建立通用中央图书馆不属于 fair use；
- 对中央图书馆后续额外复制等问题仍存在事实争议。

**证据边界：** 这是 2025 年简易判决阶段对不同用途的分拆裁定，不应改写成“法院确认所有 700 万本都用于 Claude 训练”或“美国法院普遍认定所有 AI 训练合法”。命令确认不同子集被用于不同模型，也明确有些副本后来没有使用或不再使用但仍被保留。

### 2.2 截至 2026-08-24 的案件状态

2025 年双方就界定范围内的过去盗版取得与复制 claims 达成集体和解。2026 年 7 月 20 日，Judge Araceli Martínez-Olguín [批准 15 亿美元和解并进入 final judgment](https://s3.documentcloud.org/documents/28503369/anthropic-settlement-final-approval.pdf)。

- 和解处理特定 class 范围内的过去行为，不等于 Anthropic 承认所有指控，也不建立“AI 训练是否属于 fair use”的普遍先例。
- 2025 年 fair-use order 和 2026 年 final settlement order 回答不同问题，不能合并成一句“法院判 Anthropic 违法/合法”。
- 本研究未通过 PACER 或第九巡回法院 docket 独立核验此后的上诉、effective date 或款项分配状态，因此不对此作断言。
- 对本分享最安全的用途仍是：法院记录与和解材料公开了 Anthropic 如何取得、购买、扫描和管理大规模书籍数据。

### 2.3 Books3、LibGen：四种证据状态必须分开

| 证据状态 | 可以安全地说 | 不应说 |
| --- | --- | --- |
| **诉讼指控** | 原告主张 Anthropic 未经授权复制其作品，并从影子图书馆取得书籍用于中央库和训练。 | 不能仅凭起诉书说所有主张都已获法院认可。 |
| **公司披露/程序性立场** | Anthropic 在诉讼中没有把争点限定为“从未复制”，而是主动以 fair use 申请简易判决；法院还记载 Anthropic 承认训练过程复制次数多到难以估算。 | 这不等于 Anthropic 在官网公开了一份包含 Books3、LibGen 的训练集清单，也不等于承认每个下载副本都用于训练。 |
| **法院裁定中的事实与认定** | 命令具体列出 Books3、LibGen、PiLiMi 的时间、至少数量、知情状态，并认定来自这些集合的不同子集进入不同 LLM 的 data mixes；永久保留盗版中央库不属于 fair use。 | 不能把“不同子集”扩大成“700 多万本全部训练了 Claude”；也不能忽略该命令的程序阶段与尚存事实争议。 |
| **媒体概括** | Reuters/AP 可简要概括为：训练用途获 fair-use 裁定，但盗版中央库问题没有获得保护。 | 媒体常把程序与责任压缩成“合法/侵权”二分；涉及数量、用途和终局责任时应回到法院命令。 |

### 2.4 为什么购买、拆解、扫描纸质书是 data scaling 的重要案例

这项行动同时揭示了数量和质量两个约束。

- **数量约束：** “millions of print books”不是为了少量微调，而是为了建立可搜索、可长期复用的通用研究库。
- **质量约束：** 法院记录称 Anthropic 看重书籍中的整理过的事实、结构化分析、叙事与“good writing”。长篇书籍补充了网页碎片难以稳定提供的连续结构和编辑质量。
- **来源约束：** 当免费数字来源带来法律和来源风险时，公司愿意支付数百万美元、建立实物采购和工业扫描链路。数据获取因此成为与芯片采购类似的运营工程。
- **混合优化：** 工程师检查语言、主题和作者等元数据，反复选择训练子集，并测试更多、较少或不同书籍的效果。数据 mix 本身是实验变量。

但这项案例**不能**证明：纸书一定优于所有过滤后的网页；扫描书的数量与模型能力存在线性关系；或者 Claude 的进步可以单独归因于书籍。法院记录没有公开对照实验、各版本使用的精确书目、token 占比或边际收益。

### 2.5 Anthropic 当前公开的数据框架

Claude Opus 4 / Sonnet 4 System Card 披露的类别包括：

- 截至 2025 年 3 月的公开互联网信息；
- 第三方非公开数据；
- 数据标注服务和付费承包商提供的数据；
- 明确选择加入训练的 Claude 用户数据；
- Anthropic 内部生成的数据；
- 训练过程中的去重和分类；
- 通过通用爬虫获取公共网页，并声明遵守 robots.txt、不访问需登录、密码或 CAPTCHA 的页面。

这份披露证明 Anthropic 的数据扩展已经覆盖公开抓取、采购/合作、人工数据和合成数据，也证明质量控制是明确流程。它没有披露各来源比例、具体许可方、训练 token 数，也没有说明早期 Claude 版本与诉讼中书籍库之间的逐版本映射。

---

## 三、OpenAI：网页、书籍、授权内容、平台合作与合成数据

### 3.1 公开网页与书籍：GPT-3 是最透明的历史样本

GPT-3 论文披露了相对具体的数据混合：

- 过滤后的 Common Crawl：410B token，训练混合权重 60%；
- WebText2：19B token，权重 22%；
- Books1：12B token，权重 8%；
- Books2：55B token，权重 8%；
- 英文 Wikipedia：3B token，权重 3%。

OpenAI 用 WebText、Wikipedia 和网页书籍语料作为高质量正样本训练分类器，给 Common Crawl 文档打分并重采样；随后做文档级模糊去重。论文补充材料称去重平均减少约 10% 的数据。高质量集合在训练中被更高频采样，说明“数据量”在工程上是**经质量权重调整后的有效 token**，不是原始抓取字节数。

**边界：** 论文没有公开 Books1、Books2 的完整来源清单和授权状态，不能据此断言它们等于某个后来诉讼中出现的特定图书库。

### 3.2 较新模型：披露转向高层类别

GPT-4 Technical Report 只确认使用了公开数据（如互联网数据）和第三方授权数据，并明确不披露数据集构建细节。GPT-4o System Card 则列出：

- 机器学习数据集和网页抓取取得的精选公开数据；
- 数据合作取得的非公开内容，如付费墙内容、档案和元数据；
- 网页、代码与数学、多模态数据；
- 安全分类和个人信息过滤；
- 红队数据及针对性合成数据。

因此可以确认 OpenAI 在扩展数据类型和获取渠道，但不能从公开材料计算 GPT-4/GPT-4o 中网页、书籍、授权新闻、代码或合成数据的比例，也不能把某项后来签署的合作自动视为某个更早模型的训练来源。

### 3.3 媒体和平台合作：买到的不只是“更多文本”

OpenAI 的合作公告显示，数据合作主要提供三类增量：

- **历史、非公开或付费内容：** Financial Times、Axel Springer、News Corp 等的当前与历史内容，补足公共爬虫无法稳定获取的高质量新闻档案。
- **结构化、实时社区知识：** Reddit Data API 提供实时、结构化内容；Stack Overflow 的 OverflowAPI 提供经过社区验证的技术问答和反馈。
- **产品内检索与归因：** 很多合作同时允许 ChatGPT 展示带链接和归因的实时内容。这属于检索/产品数据流，不应全部算作预训练 token。

合作公告的具体边界：

- **FT（2024-04-29）：** 明确为授权协议，允许在 ChatGPT 中展示带归因内容，并“incorporating FT journalism”以提高模型 usefulness。
- **News Corp（2024-05-22）：** 明确提供当前及历史内容，用于展示和增强产品；公告没有公布训练 token 数、价格或模型版本。
- **Stack Overflow（2024-05-06）：** 明确称 OpenAI 将使用 OverflowAPI 改进模型面向开发者的表现；不能推断所有 Stack Overflow 历史内容都进入基础预训练。
- **Reddit（2024-05-16）：** 公告明确实时 API 接入和产品展示，但 OpenAI 原始公告对“用于基础模型训练”的措辞不如媒体标题明确；应把可确认 claim 限定为访问、理解和展示 Reddit 内容。
- **Data Partnerships（2023-11-09）：** OpenAI 主动征集不易公开获得、体现人类意图的大规模多模态数据，特别提到长篇写作或对话；这证明其数据战略，不证明任何潜在合作数据已经进入模型。

这些合作支持“高质量、稀缺、结构化、及时的数据正在变成付费投入”，但不支持“每一家媒体单独显著提升模型”。OpenAI 自己在回应 NYT 诉讼时也称，任何单一来源对现有或未来模型都不足以产生实质影响；这是一项公司立场，不是独立测量。

### 3.4 合成数据：扩大稀缺区域，而不是无限复制老师

OpenAI 的官方说明称，其越来越多地在部分训练流程使用合成数据，例如生成 synthetic prompts、多语言样本或其他训练材料，用于补充稀疏或失衡区域，并可能支持隐私增强。GPT-4o System Card 还确认，红队发现会驱动有针对性的合成数据生成。

机会主要来自：

- 可以按目标能力定向生成长尾样本，而不是等待网页自然出现；
- 数学、代码等可验证领域可以用答案、执行结果或单元测试做 rejection sampling；
- 强模型可为较小模型生成大批 instruction / reasoning 数据；
- 可以调整语言、难度和安全类别的分布。

OpenMathInstruct-2 提供了一个公开的机会证据：14M 数学问答对可显著提高 8B 模型在 MATH 上的成绩，而且控制样本量后，强老师、问题多样性和答案格式都影响结果。这不是 OpenAI 自己的训练报告，但说明合成数据价值来自**生成、验证、筛选和多样性设计**，不是“免费无限 token”。

风险同样明确：

- Nature 论文显示，**不加区分地递归使用模型生成数据**会让尾部分布先消失并累积误差，形成 model collapse。
- 该论文的实验条件包括小模型和递归微调，不能直接推出“任何合成数据都会毁掉 GPT-5/Claude”。保留真实数据、使用更强教师、验证正确性和筛选多样性会改变结果。
- 合成数据可能放大教师模型的错误、偏见和表达习惯；如果生成器与学生共享盲点，token 数增长但新信息量可能很低。
- 网页中 AI 生成内容日益增多，使来源追踪和人类原始数据保留更重要。

---

## 四、Data wall：真实瓶颈，但时间点高度不确定

Epoch AI / ICML 2024 的估计是：经质量和多 epoch 调整后，可用公共人类文本的有效存量约为 **300T token**，90% 区间为 **100T–1000T**；若当时趋势延续，前沿训练集规模可能在 **2026–2032** 年触及这一存量。

这项结果应表述为条件预测，而不是“2028 年互联网数据必然用完”：

- 它估的是**有效公共人类文本**，不是所有文字、私人数据、多模态数据或未来合成数据；
- “高质量”过滤、可重复训练 epoch 数和未来训练策略都会显著改变结果；
- 更强的数据效率、跨模态迁移、检索、合成数据或新的合法数据合作可推迟瓶颈；
- 若公司为了降低推理成本而用更多 token “overtrain”较小模型，数据消耗可能反而更快；
- 前沿实验室不公开最新数据集规模，使预测输入存在系统性不确定。

Muennighoff 等人进一步说明，重复数据可暂时缓冲数据墙，但不是无限方案：约 4 个 epoch 以内损失变化很小，更多重复后收益持续衰减。因此，“数据墙”更准确的含义是：**高价值的新信息增长速度可能赶不上可用训练计算，而不是硬盘中没有更多字符。**

---

## 五、这些案例支持什么，不支持什么

### 支持：“scale data”是 scaling 的关键维度

1. **因果层面的技术证据：** Chinchilla 在固定算力下改变参数/数据分配并获得更好结果，直接说明数据量是 compute-optimal scaling 的变量，而非背景常数。
2. **边际收益证据：** 重复数据的价值最终衰减，说明新颖、高质量 token 不能由更多 GPU 无限替代。
3. **工程行为证据：** Anthropic 花费数百万美元购买并工业化扫描数百万册书；OpenAI 建立数据合作计划并签下媒体、社区和多模态平台。企业行为与“数据是稀缺投入”一致。
4. **质量工程证据：** OpenAI 和 Anthropic 都明确使用去重、分类或过滤；GPT-3 和 RefinedWeb 的公开实验说明筛选与采样权重会改变有效数据质量。
5. **战略迁移证据：** 当公开网页不足或风险上升，公司转向授权档案、结构化 API、人工数据、用户选择加入的数据和合成数据，说明 data scaling 已从爬虫问题变成供应链和数据生产问题。

### 不支持：需要在演讲中明确降调

- 不能由采购规模推断 Claude 或 GPT 的具体性能增益；没有公开消融实验。
- 不能说“书越多模型必然越聪明”，也不能说书籍永远比过滤网页更优。
- 不能把 Chinchilla 的约 20 tokens/parameter 当作所有架构、训练目标和部署经济下的自然常数。
- 不能说 2026–2032 必然撞墙；这是条件预测，且区间很宽。
- 不能说合成数据已经解决数据稀缺；其可靠成功目前更集中于数学、代码和可验证任务。
- 不能把授权合作、产品内实时检索、预训练数据和后训练数据混成一类。
- 不能把法院对特定复制用途的 fair-use 判断扩展成所有 AI 训练数据获取方式都合法，也不能把争议来源的使用说成 scaling 必需条件。
- 不能仅凭 Anthropic 与 OpenAI 的行为证明全行业普遍规律；企业采购同时受法律风险、竞争保密、产品需求和部署经济影响。

---

## 六、逐条来源卡片（18 条）

### 1. Bartz v. Anthropic PBC — Order on Fair Use

- **机构/作者：** U.S. District Court, Northern District of California；Judge William Alsup
- **发布日期：** 2025-06-23
- **直接链接：** https://www.copyright.gov/fair-use/summaries/Bartz-v-Anthropic-PBC-787-F-Supp-3d-1007-ND-Cal-2025.pdf
- **来源类型：** 法院命令（一手）
- **收录原因：** Anthropic 购买、拆解、扫描纸书以及 Books3、LibGen、PiLiMi 的最强公开证据。
- **可支持的 claim：** 超过 700 万份盗版书副本的来源与时间；花费数百万美元购买、破坏性扫描数百万纸书；不同书籍子集进入不同训练 data mixes；书籍质量与成本效益的内部判断；各用途的 fair-use 裁定。
- **证据边界：** 简易判决阶段；不是完整终局审判，不证明全部下载书都进入 Claude，也未公开逐模型书目和 token 比例。

### 2. Anthropic wins key US ruling on AI training in authors' copyright lawsuit

- **机构/作者：** Reuters；Blake Brittain
- **发布日期：** 2025-06-24
- **直接链接：** https://www.reuters.com/legal/litigation/anthropic-wins-key-ruling-ai-authors-copyright-lawsuit-2025-06-24/
- **来源类型：** 权威媒体报道
- **收录原因：** 对法院命令的及时独立概括，可用于非法律听众的背景说明。
- **可支持的 claim：** 法院区分训练用途与盗版中央库；诉讼当时的程序状态。
- **证据边界：** Reuters 页面在本次环境返回 401，正文通过搜索工具可见片段交叉核对；数量、具体来源和裁定措辞应以法院命令为准。

### 3. System Card: Claude Opus 4 & Claude Sonnet 4

- **机构/作者：** Anthropic
- **发布日期：** 2025-05（与模型发布 2025-05-22 同期；文档后有修订）
- **直接链接：** https://www.anthropic.com/claude-4-model-card
- **来源类型：** 公司系统卡（一手）
- **收录原因：** Anthropic 对当前训练数据类别、爬虫与质量流程的官方披露。
- **可支持的 claim：** 公开互联网、第三方非公开数据、承包商/标注数据、用户 opt-in 数据、内部生成数据；去重和分类；通用爬虫政策。
- **证据边界：** 不披露来源比例、具体合作方、token 数和早期模型逐版本配方；公司自行陈述未获独立审计。

### 4. Training Compute-Optimal Large Language Models

- **机构/作者：** Jordan Hoffmann et al., Google DeepMind
- **发布日期：** 2022-03-29
- **直接链接：** https://arxiv.org/abs/2203.15556
- **来源类型：** 主要技术论文
- **收录原因：** “数据本身是 scaling 维度”的最直接实验依据。
- **可支持的 claim：** 固定算力下参数和 token 的分配影响结果；Chinchilla 以 70B 参数、1.4T token、与 Gopher 相同算力超过更大的模型；进一步 scaling 需要更大高质量数据集。
- **证据边界：** 结论依赖其模型、优化器、数据和 loss 范围；约 20 token/parameter 不是普适常数。

### 5. Language Models are Few-Shot Learners

- **机构/作者：** Tom B. Brown et al., OpenAI
- **发布日期：** 2020-05-28
- **直接链接：** https://proceedings.neurips.cc/paper_files/paper/2020/file/1457c0d6bfcb4967418bfb8ac142f64a-Paper.pdf
- **来源类型：** 主要技术论文
- **收录原因：** OpenAI 最具体的公开网页、书籍与数据混合披露。
- **可支持的 claim：** GPT-3 使用过滤 Common Crawl、WebText2、Books1、Books2、Wikipedia；做质量筛选、模糊去重和差异化采样。
- **证据边界：** Books1/Books2 的具体来源和权利状态未完整公开；不能外推为 GPT-4 以后模型的配方。

### 6. GPT-3 Supplementary Material — Details of Common Crawl Filtering

- **机构/作者：** OpenAI / Brown et al.
- **发布日期：** 2020
- **直接链接：** https://papers.neurips.cc/paper_files/paper/2020/file/1457c0d6bfcb4967418bfb8ac142f64a-Supplemental.pdf
- **来源类型：** 论文补充材料（一手）
- **收录原因：** 核对“质量优先”和去重不是口号，而是具体数据工程。
- **可支持的 claim：** 用 WebText、Wikipedia、网页书籍作为正样本给 Common Crawl 评分重采样；MinHashLSH 模糊去重平均减少约 10% 数据。
- **证据边界：** 质量分类器本身会带入参考语料偏好；实验属于 GPT-3 时期。

### 7. GPT-4 Technical Report

- **机构/作者：** OpenAI
- **发布日期：** 2023-03-15
- **直接链接：** https://cdn.openai.com/papers/gpt-4.pdf
- **来源类型：** 公司技术报告（一手）
- **收录原因：** 确认 GPT-4 的公开数据和授权数据两大类别，同时记录透明度边界。
- **可支持的 claim：** GPT-4 以公开互联网数据和第三方授权数据预训练，之后使用 RLHF。
- **证据边界：** OpenAI 明确不披露数据集构建、规模、比例和其他训练细节，不能据此识别具体网站或书库。

### 8. GPT-4o System Card

- **机构/作者：** OpenAI
- **发布日期：** 2024-08-08
- **直接链接：** https://openai.com/index/gpt-4o-system-card/
- **来源类型：** 公司系统卡（一手）
- **收录原因：** 展示 OpenAI 如何把网页、代码、数学、多模态、合作数据和合成安全数据纳入同一数据体系。
- **可支持的 claim：** 精选网页抓取、非公开合作数据、代码/数学/多模态数据、数据过滤、针对性合成数据。
- **证据边界：** 不给出各类 token 数、权重或消融；Shutterstock 例子主要涉及图像，不应当作文本预训练证据。

### 9. How ChatGPT and our foundation models are developed

- **机构/作者：** OpenAI Help Center
- **发布日期：** 持续更新页面；本次核验日 2026-08-24，页面未稳定显示首次发布日期
- **直接链接：** https://help.openai.com/en/articles/7842364-how-chatgpt-and-our-foundation-models-are-developed
- **来源类型：** 公司官方说明（一手）
- **收录原因：** OpenAI 对公共互联网、第三方合作、人类提供/生成信息和合成数据的最清楚通俗说明。
- **可支持的 claim：** 三大信息来源；过滤垃圾和不需要内容；越来越多地用合成提示、多语言样本等补足稀疏或失衡数据。
- **证据边界：** 页面会更新且无模型级数字；本次直接抓取超时，文字由搜索结果中的原文段落核对，不宜引用为固定历史版本。

### 10. OpenAI Data Partnerships

- **机构/作者：** OpenAI
- **发布日期：** 2023-11-09
- **直接链接：** https://openai.com/index/data-partnerships/
- **来源类型：** 公司战略公告（一手）
- **收录原因：** 直接说明 OpenAI 想获取哪些公共互联网之外的数据。
- **可支持的 claim：** 征集大规模、多模态、体现人类意图且不易公开获取的数据；特别重视长篇写作和对话；同时建设开放与私有数据集。
- **证据边界：** 是征集与战略声明，不证明任何提议数据已经用于某个模型；直接抓取超时，内容由工具返回的完整页面片段核对。

### 11. We’re bringing the Financial Times’ world-class journalism to ChatGPT

- **机构/作者：** Financial Times / OpenAI 联合公告
- **发布日期：** 2024-04-29
- **直接链接：** https://openai.com/index/content-partnership-with-financial-times/
- **来源类型：** 官方合作公告
- **收录原因：** 授权高质量新闻用于产品展示和模型改进的明确案例。
- **可支持的 claim：** ChatGPT 可展示带归因的 FT 摘要、引语和链接；FT 新闻将被纳入以提高模型 usefulness。
- **证据边界：** 不披露价格、语料范围、token 数、训练阶段和对应模型；公告由合作双方自行表述。

### 12. A landmark multi-year global partnership with News Corp

- **机构/作者：** News Corp / OpenAI
- **发布日期：** 2024-05-22
- **直接链接：** https://openai.com/index/news-corp-and-openai-sign-landmark-multi-year-global-partnership/
- **来源类型：** 官方合作公告
- **收录原因：** 展示大规模当前与历史专业内容授权。
- **可支持的 claim：** OpenAI 获得 News Corp 多个媒体品牌当前和历史内容的访问权，用于展示和增强产品。
- **证据边界：** “enhance products”不等于全部内容进入基础预训练；无公开模型映射、价格或效果消融。

### 13. API Partnership with Stack Overflow

- **机构/作者：** Stack Overflow / OpenAI
- **发布日期：** 2024-05-06
- **直接链接：** https://openai.com/index/api-partnership-with-stack-overflow/
- **来源类型：** 官方合作公告
- **收录原因：** 结构化、经社区验证的技术知识数据案例。
- **可支持的 claim：** OpenAI 使用 OverflowAPI 改进开发者相关模型表现，并在 ChatGPT 中展示带归因的技术知识。
- **证据边界：** API 使用可同时服务检索、产品和模型改进；公告不证明整个历史库进入预训练。直接抓取遇到 JavaScript 验证，正文由搜索返回原文核对。

### 14. OpenAI and Reddit Partnership

- **机构/作者：** Reddit / OpenAI
- **发布日期：** 2024-05-16
- **直接链接：** https://openai.com/index/openai-and-reddit-partnership/
- **来源类型：** 官方合作公告
- **收录原因：** 实时、结构化社区内容的数据通道案例。
- **可支持的 claim：** OpenAI 访问 Reddit Data API，使工具更好理解和展示 Reddit 内容。
- **证据边界：** 原公告重点是实时访问和产品展示；不能只凭媒体标题断言所有内容用于某个基础模型的预训练，也没有公开财务条款。

### 15. Position: Will we run out of data? Limits of LLM scaling based on human-generated data

- **机构/作者：** Pablo Villalobos, Anson Ho, Jaime Sevilla, Tamay Besiroglu, Lennart Heim, Marius Hobbhahn；Epoch AI / ICML
- **发布日期：** 2024（ICML 2024；更新版）
- **直接链接：** https://proceedings.mlr.press/v235/villalobos24a.html
- **来源类型：** 同行评审会议论文 / 预测分析
- **收录原因：** 对 public human text “data wall”的最系统定量估计之一。
- **可支持的 claim：** 有效存量中心估计约 300T token、90% 区间 100T–1000T；按当时趋势，训练集可能在 2026–2032 触及存量；合成数据、跨模态迁移和数据效率是可能出路。
- **证据边界：** 模型依赖不透明的前沿数据规模、质量阈值、重复 epoch 和增长趋势；不是已发生事实，也不覆盖全部私人或多模态数据。

### 16. Scaling Data-Constrained Language Models

- **机构/作者：** Niklas Muennighoff et al.
- **发布日期：** 2023-05-25（arXiv v1；NeurIPS 2023）
- **直接链接：** https://arxiv.org/abs/2305.16264
- **来源类型：** 主要技术论文
- **收录原因：** 定量回答数据不足时能否靠重复 token 继续 scale。
- **可支持的 claim：** 固定计算下最多约 4 个 epoch 的重复数据与新数据 loss 差异很小；更多重复后价值衰减，最终额外计算收益趋近于零。
- **证据边界：** 实验最大约 9B 参数、900B 训练 token；不能直接断言前沿闭源模型的精确重复阈值。

### 17. The RefinedWeb Dataset for Falcon LLM: Outperforming Curated Corpora with Web Data, and Web Data Only

- **机构/作者：** Guilherme Penedo et al., TII
- **发布日期：** 2023-06-01
- **直接链接：** https://arxiv.org/abs/2306.01116
- **来源类型：** 数据集与技术论文
- **收录原因：** 证明网页数据经过严格过滤、去重后可成为高质量、大规模训练源。
- **可支持的 claim：** 从 Common Crawl 构建约 5T token 的英文 RefinedWeb；严格过滤和多层去重后的网页数据在其实验中可超过若干精选混合语料。
- **证据边界：** 结果针对其数据管线和 1.3B/7.5B 级模型；不能证明书籍无价值，也不能自动外推到所有语言和前沿规模。

### 18. AI models collapse when trained on recursively generated data

- **机构/作者：** Ilia Shumailov, Zakhar Shumaylov, Yiren Zhao et al.; Nature
- **发布日期：** 2024-07-24
- **直接链接：** https://www.nature.com/articles/s41586-024-07566-y
- **来源类型：** 同行评审研究论文
- **收录原因：** 合成数据风险最有代表性的原始实验和理论证据。
- **可支持的 claim：** 不加区分地递归训练模型生成数据会丢失低概率尾部并累积误差；保留真实原始分布和追踪数据来源很重要。
- **证据边界：** 论文研究特定递归替换/混合设置，LLM 实验使用较小模型和微调；不支持“任何合成数据都会导致 collapse”。

---

## 七、建议映射到哪些 slide

- **Slide 2「GPU 必须被数据喂饱」：** 用 Chinchilla 的固定算力对比说明“喂饱”不是比喻：更多 GPU 若没有足够有效 token，不能保持 compute-optimal。
- **Slide 7「固定算力筹码」：** 将筹码明确分成参数与训练 token；补一句 token 还要乘以质量、新颖性和采样权重。
- **Slide 9「Chinchilla 用同样筹码赢了」：** 核心证据用 70B / 1.4T token 对 280B Gopher，保持“特定实验条件”边界。
- **Slide 10「Scaling 不等于只加参数」：** Anthropic 数百万纸书扫描可作为最具视觉冲击力的 data-supply-chain 案例；旁边放 OpenAI 的网页→过滤/去重→书籍/授权→合成数据流程。
- **Slide 11「筹码流向新的阶段」：** 用 OpenAI 的人工/红队/合成数据说明数据生产也从 pretraining 延伸到 post-training。
- **Slide 13「正确反馈才变成能力」：** 用 model collapse 说明合成 token 不是天然新信息；数学/代码需要 verifier，通用领域需要人类数据锚点。
- **Slide 14「先问四个问题」：** 在 “What is being scaled?” 下增加：raw tokens、unique high-quality tokens、licensed/private data，还是 verified synthetic experience？

适合做一页附录而非正文的材料：Books3/LibGen 四种证据状态、OpenAI 各合作公告的“训练 vs 检索/展示”边界、data-wall 预测区间。

## 八、最值得保留的 5 条来源

1. **Bartz v. Anthropic — Order on Fair Use**：唯一能直接核验 Anthropic 采购、扫描和影子图书馆事实的法院材料。
2. **Hoffmann et al., Training Compute-Optimal Large Language Models**：data scaling 对模型结果的核心技术证据。
3. **Brown et al., Language Models are Few-Shot Learners + supplement**：OpenAI 数据 mix、过滤、去重和重采样最透明的一手材料。
4. **Villalobos et al., Will we run out of data?**：data wall 的定量框架和条件边界。
5. **Shumailov et al., AI models collapse when trained on recursively generated data**：合成数据不能被当成无限、无风险替代品的关键证据。

## 九、仍未解决的问题

- Anthropic 每一代 Claude 实际用了哪些 Books3、LibGen、PiLiMi 或纸书子集？各占多少 token？公开记录不足。
- Anthropic 纸书扫描项目的最终精确数量、总成本、去重后唯一书目数和模型边际收益是多少？法院材料只给出“millions / many millions”。
- OpenAI 的 Books1、Books2 完整组成和权利状态是什么？GPT-3 论文没有披露。
- OpenAI 各媒体/平台合作中，哪些内容进入预训练、mid-training、post-training、检索索引或仅用于产品展示？公告常把这些用途并列但不量化。
- 最新 OpenAI 与 Anthropic 模型的真实训练 token 数、重复 epoch、合成数据比例和质量权重是多少？公司未公开。
- 公共网页中 AI 生成内容的比例如何被可靠识别？现有来源追踪不足，会影响 data-wall 存量和 model-collapse 风险估计。
- 在不可自动验证的通用写作、社会科学和现实决策领域，什么机制能让合成数据持续增加新信息而不只是模仿教师？
- 数据获取成本何时会与算力成本同量级，并真正改变前沿实验室的 scaling 配方？现有公开财务信息不足。
