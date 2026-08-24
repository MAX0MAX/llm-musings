# Scaling Laws, in a Nutshell — 第二轮证据整合审计

> 审计日期：2026-08-24
> 审计性质：只读交叉审计；不扩展资料库，不修改 `OUTLINE.md`、`reference/README.md` 或 `RESEARCH_RUNS.md`
> 审计输入：9 个文件——`OUTLINE.md`、`reference/README.md`、六份 Agent 研究文件、`RESEARCH_RUNS.md`

## 一、执行结论

现有三幕结构可以保留，但必须修正四个会改变叙事可信度的问题：

1. **开场不能说“四家公司股价一起疯涨”。** 2024 同窗口的现有交叉数据是 NVIDIA `+178%`（Reuters 2024-12-31 更新稿；12-23 初稿为 172%）、SK hynix `+23%`、Samsung Electronics `−32%`、Micron 约 `+0.6%`；后者还缺统一机构行情源复算。安全说法是“AI 硬件链被重新定价，但表现明显分化”，或直接改用经营事实卡。
2. **Anthropic/OpenAI 案例只能作为 data scaling 的工程与战略证据。** 它们证明公司在扩大数据覆盖、质量控制、授权、人工及合成数据渠道；不能单独证明更多数据导致多少能力提升。因果主证据仍应是 Chinchilla、GPT-3 数据工程、数据重复和 RefinedWeb 等受控实验。
3. **Kaplan → Chinchilla 仍适合承担第二幕。** 这是最清楚的固定预训练算力分配反转，但要把 Kaplan 从“起点/正确处方”改成“Transformer LM scaling 的系统化与训练规划节点”，补一句 Hestness/Rosenfeld 前史，并在 Chinchilla 后补上 inference-optimal 的目标函数变化。
4. **“Scale 整个生命周期”应作为产业框架。** 可把“预算和性能已扩展到预训练之外”作为事实弱版本，把“如何配置全生命周期资源”作为主框架，把 experience/RL 等作为战略下注；不能称为一条、或三条，与经典 loss scaling 同等成熟的新定律。

总体上，最可靠的正文证据链应收缩为：

> 可预测的条件性 loss scaling（Kaplan 等） → 固定训练算力的分配修正（Chinchilla） → 训练最优不等于部署最优（LLaMA/Llama 3） → 多个条件性的生命周期资源前沿（Gao、Snell、RETRO、Kapoor），而不是“旧 law 失效后出现三条新 law”。

## 二、证据等级

等级表示**适合支持哪类 claim**，不简单等于真假排序。

| 等级 | 来源类型 | 最适合支持 | 不宜单独支持 |
| --- | --- | --- | --- |
| **A** | 原始论文；法院命令/判决；监管机构文件；政府或国际组织官方报告 | 实验结果、论文身份、裁判内容、监管事实 | 跨实验条件的普适性；未裁判事项 |
| **B** | 原始访谈；公司博客/技术报告/系统卡；公司财报和 IR 材料 | 当事人观点、公司战略、自报实验、产品规格、经营事实 | 行业共识、独立 benchmark、技术因果、投资回报 |
| **C** | 权威媒体；专业研究机构；行业数据库/分析机构 | 背景、交叉核对、市场与供应链估计 | 原始实验替代品；无法公开核对的内部消息 |
| **D** | VC、卖方研究、产业观点 | 市场叙事、资本配置假说、战略语言 | 技术定律、内部架构事实、确定市场规模 |
| **E** | Hacker News 等社区反响 | 工程社区如何理解、质疑或误解 | 技术事实、人物身份、行业共识 |

补充规则：

- 公司技术报告虽可能包含原始实验，在本审计中仍记 **B**：它是该公司实验与战略的一手证据，但未必独立复现。
- 原始作者个人技术文章若不是论文，按用途记 **B/C**；例如 Lilian Weng 的文章适合解释拟合方法，不作为新定律证据。
- “原始采访”能证明说话者确实表达某观点，不能把观点升级成实证。

## 三、跨文件重复与冲突

### 3.1 高重复来源

以下来源已在多份研究中重复出现。`reference/README.md` 应只保留一张主卡，其他主题页用交叉引用，不再重复长引语和完整解释。

| 来源 | 重复位置 | 审计处理 |
| --- | --- | --- |
| Kaplan et al. 2020 | README、explainers、Kaplan/Chinchilla、data scaling | 保留为 slide 5、7、8 主证据；统一为“系统化/规划节点”，不称起点 |
| Hoffmann et al. 2022 / Chinchilla | README、data、explainers、Kaplan/Chinchilla | 保留为 slide 7–9 主证据；统一 70B、1.4T、280B、同训练 FLOPs |
| Ganguli et al. 2022 | README、Kaplan/Chinchilla、explainers 建议 | 保留为 slide 6 的 loss/behavior 边界 |
| Gao et al. 2022 | README、lifecycle | 保留为 slide 13 reward caveat |
| Snell et al. 2024 | README、lifecycle、explainers 的叙事映射 | 保留为 slide 12–13 test-time 条件证据 |
| RETRO | README、lifecycle、OUTLINE | 保留为 slide 10/11 的参数外资源轴 |
| Kapoor et al. 2024 | README、lifecycle、community | 保留为 slide 13 的成本与归因审计 |
| Shumailov et al. 2024 | data、lifecycle、community | 只保留一次“无甄别递归数据”的限定版本 |
| Villalobos et al. 2024 | data、explainers、community | 放附录；统一两个不同区间的含义 |
| Demis Hassabis 访谈 | README、explainers、lifecycle | 只保留一次原始访谈引语，标 B |
| Silver & Sutton / Era of Experience | README、lifecycle、community | 明确标“研究议程”，不进入已成立 law 清单 |
| Shunyu Yao / The Second Half | README、lifecycle | 明确标个人研究议程/观点，不作行业事实 |
| NVIDIA “three laws” | lifecycle、community、OUTLINE | 只作为卖方 taxonomy，标 B/D 用途边界 |

### 3.2 重复 claim

六份研究对以下结论高度重复，整合版应各讲一次：

- `loss 可预测 ≠ 具体能力可预测`：slide 5 提主张，slide 6 给边界。
- `20 tokens/parameter 不是自然常数`：只在 slide 9 脚注说明；不要在 README 多处重复。
- `test-time compute 依赖难度和 verifier`：slide 12 给正证据，slide 13 给条件。
- `synthetic data 不是无限免费 token`：放 slide 13 或附录，不要在 data、post-training、experience 三处分别展开。
- `NVIDIA 三条 laws 是 taxonomy`：只讲一次。
- `R1-Zero 才是纯 RL，正式 R1 是多阶段训练`：若正文不讲 DeepSeek，留在参考索引 context flag。
- `100,000× 来自扑克`：不进正文，只留人工复核/误引警告。

### 3.3 实质不一致与裁决

| 项目 | 文件间不一致 | 裁决 |
| --- | --- | --- |
| 四股表现 | OUTLINE 暗示同一浪潮；基础设施研究显示明显分化 | 删除任何“同时疯涨/一起上涨”措辞 |
| scaling 前史 | OUTLINE slide 4 容易暗示 Kaplan 前没有预测性工作；Kaplan 专题列出 Hestness 2017、Rosenfeld 2019 | 改成“在 frontier LM 训练规划成熟前”，并补前史 |
| Kaplan 的产业因果 | OUTLINE 称其强化行业信心；专题认为只有中等证据，不能证明各实验室内部决策 | 降为“与 GPT-3 及后续大参数训练范式相符” |
| data-wall 区间 | data 写“300T，90% 区间 100T–1000T；2026–2032”；community 写“2026–2032 为 80% 区间” | 两者都可成立：**存量估计**是 90% CI 100T–1000T；**耗尽年份**是 80% CI 2026–2032。必须分别标注 |
| METR 日期 | lifecycle 写论文 2025-03-18；explainers 写原研究 2025-03-19 | arXiv v1 为 03-18；METR 博客为 03-19。按载体分别写 |
| NVIDIA 日期 | lifecycle 只写 2025-02；community 写 2025-02-12 | 作者归档可核验 Kari Briski、2025-02-12；统一为该日期，同时标公司博客 |
| Anthropic 法律状态 | data 仅停留在 2025-06-23 简易判决阶段 | 截至本审计日已过时，见下一节 |
| 基础设施证据截止 | 文件称核心 cutoff 为 2025-04-24，却收录 2025-04-30 Samsung 结果及 2026 访问材料 | 改成“核心经营窗口至 2025-04-30；页面访问/核验日 2026-08-24”，或逐项给 cutoff |
| “生命周期”结构 | OUTLINE 是线性四阶段；lifecycle 研究指出 retrieval/memory 横跨多个阶段且 experience 回流 post-training | 改为闭环图，retrieval/memory 作侧轨 |
| “新 scaling laws”成熟度 | NVIDIA/VC 用 law；论文证据只支持条件性 axis | 正文统一用 axis/frontier/framework，不用复数 laws |

## 四、身份、日期、引语与法律状态核验

### 4.1 论文、人名和模型名

- **Kaplan**：应写 `Kaplan et al. (2020)`；Jared Kaplan 是作者之一，不应把论文写成人物个人回答。
- **Chinchilla**：是 70B 模型及 Hoffmann et al. 论文的通称；第一作者为 **Jordan Hoffmann**。推荐写 `Hoffmann et al. / Chinchilla (2022)`。
- **Gopher**：280B 模型；“Chinchilla 超过 Gopher”必须附“近似相同训练 FLOPs、论文评测范围内”。
- **RETRO**：论文标题用 Retrieval-Enhanced Transformer，正文可用 `RETRO`；“25× fewer parameters”只对应特定 Pile 比较。
- **DeepSeek-R1**：不能写“纯 RL 做出 R1”；纯 RL 指 **R1-Zero**，正式 R1 含 cold-start SFT、RL、rejection-sampling 数据和后续训练。
- **Noam Brown 100,000×**：来自扑克搜索实验，不是 o1/LLM 的训练—推理通用兑换率。
- **Meta `Compute Optimal Tokenization`**：arXiv `2605.01188`、标题、作者团队和 2026-05-04 Meta 页面均已核验可访问；不是可疑伪索引，但仍是 2026 新论文，缺少广泛独立复现。
- **Lilian Weng `Scaling Laws, Carefully`**：2026-06-24 页面已核验存在；它是技术综述/解释文章，不是“原始论文”，README 当前的“primary technical essay”容易与 A 级原始研究混淆。

### 4.2 引语归属

可保留、且已能追到原始载体的引语：

- Kaplan et al.：“The loss scales as a power-law …”——主语必须保留为 `loss`。
- Ganguli et al.：“predictable loss … unpredictable specific capabilities …”——来自 Anthropic 论文，不是媒体转述。
- Gao et al.：“Because the reward model is an imperfect proxy …”——只证明代理优化风险。
- Snell et al.：“critically varies depending on the difficulty …”——主要实验域是数学。
- Demis Hassabis：“push scaling … double down on innovation …”——原始访谈，属于战略判断。
- Kimi：“Scaling reinforcement learning … unlocks a new axis …”——团队自我解释，不是独立定律。

必须人工复听或避免逐字引用：

- 所有只依赖 YouTube 自动字幕的内容，特别是 Jared Kaplan 讲座、Computerphile、Noam Brown 视频。
- Noam Brown 的“首都 vs Sudoku”若用引号，需按原视频时间戳复听；当前可安全做释义。
- Yann LeCun 的时间戳引语虽有网页 transcript，正式逐字引用仍应与音频对照。
- Amazon 使用第三方 transcript host 的话语，需回到官方 webcast/IR transcript。

### 4.3 Bartz v. Anthropic 的法律状态

`data-scaling.md` 对 2025-06-23 简易判决命令本身的区分总体谨慎，但截至 2026-08-24，程序状态已经变化：

- 2025-06-23，Judge William Alsup 作出简易判决阶段的分拆裁定：特定训练复制和合法购买纸书的一对一数字化被认定为 fair use；盗版中央库的取得/保留未获 fair-use 保护，并留下责任/损害等问题。
- 2025 年双方达成 `Bartz` 集体和解。
- **2026-07-20**，Judge Araceli Martínez-Olguín 批准 **$1.5 billion** 集体和解并进入 final judgment；已核验最终批准命令及 Authors Guild/Authors Alliance 的同步说明。
- 和解处理的是界定范围内、截至约定日期的过去输入/盗版获取与复制 claims；不等于美国法院普遍判定“AI 训练合法”，也不处理所有输出侵权或未来行为。
- 截至 2026-08-24，是否存在仍会影响生效/分配的上诉，**本次未通过 PACER/第九巡回法院 docket 独立核验**；不得根据搜索摘要断言“已无上诉”或“款项已开始发放”。
- 地区法院简易判决不是最高法院或巡回法院的普遍约束规则；和解本身也不建立普遍先例。演讲若只为说明数据供应链，可避免讲法律结论，只说“法院记录和后续和解公开了采购、扫描及盗版库取得事实”。

因此，当前安全说法是：

> “Bartz 案的法院记录显示 Anthropic 曾从影子图书馆取得数百万书籍副本，后来又购买并破坏性扫描数百万纸书；2026 年法院最终批准了针对界定范围内过去盗版取得与复制 claims 的 15 亿美元集体和解。该案不能概括成‘所有 AI 训练合法’或‘所有下载书都用于每一代 Claude’。”

## 五、关键链接可访问性抽查

抽查日期：2026-08-24。这里的“失败”只表示本次环境访问结果，不等于链接永久失效。

| 链接类别 | 抽查结果 | 处理 |
| --- | --- | --- |
| Kaplan `arXiv:2001.08361` | 可访问 | A 级主证据 |
| Chinchilla `arXiv:2203.15556` | 可访问 | A 级主证据 |
| Ganguli `arXiv:2202.07785` | 可访问 | A 级主证据 |
| Gao `arXiv:2210.10760` | 可访问 | A 级主证据 |
| Snell `arXiv:2408.03314` | 可访问 | A 级主证据 |
| Kapoor `arXiv:2407.01502` | 可访问 | A 级主证据 |
| Villalobos / PMLR | 可访问；摘要明确 2026–2032 条件预测 | A 级论文；Epoch 页面属 C |
| Meta `arXiv:2605.01188` | arXiv、Meta 页面、项目页均可访问 | 可收录，但标 2026 新研究 |
| Lilian Weng 2026 文章 | 可访问 | C 级方法解释 |
| Anthropic Claude 4 model card | 可访问 | B 级公司披露 |
| Demis / Dwarkesh transcript | 可访问 | B 级原始访谈 |
| Shunyu Yao 原文 | 可访问 | B 级观点/议程 |
| NVIDIA “three laws” | 可访问；正文带明显 GPU 需求叙事 | B/D 用途，不作技术 law |
| OpenAI `Learning to reason with LLMs` | 2026-08-24 全量检查返回 200 | 页面可访问；曲线仍是公司自报，引用应回到原页 |
| Reuters Anthropic 链接 | 返回 401 | 付费/访问限制；法律数字回到法院命令 |
| Hacker News 样本页 | 自动请求返回 403/429；15 个 item ID 均经官方 Firebase API 确认存在 | E 级动态快照，不作事实证据 |

本节仍是语义抽查。后续全量检查已覆盖 topic 内 13 个 Markdown 文件的全部本地与外部目标；状态、方法和修复记录见 [LINK_CHECK.md](LINK_CHECK.md)。

## 六、14 页逐页证据裁决

### Slide 1 — 最近，卖“内存”的公司突然站到了 AI 舞台中央

**最强来源**

1. NVIDIA FY2025 results（B）
2. SK hynix FY2024 results（B）
3. Reuters 对 Samsung/SK hynix 2024 分化的年终核对（C）

**可安全讲的 claim**

> “AI 加速器和 HBM 已显著改变部分公司的收入结构与市场预期，但同一供应链公司的股价表现并不一致。”

经营事实可用 NVIDIA Data Center `+142% YoY`、SK hynix 2024 revenue `+102%`、SK hynix Q4 HBM 超过 DRAM revenue 的 40%；必须同时说明各指标窗口和业务范围不同。

**必须保留的 caveat**

- 股票反映未来现金流、估值、利率、仓位、执行与政策，不是 scaling law 证据。
- Samsung 2024 跌约 32%，Micron 全年接近持平且年末回撤，恰好反驳“全链一起涨”。
- 行情图必须由一个授权数据源、统一 adjusted close/total-return 口径重算。

**建议删改**

- 删除“四家公司股价一起疯涨”“共同暴涨”及任何等义标题。
- 把“市场正在重新定价 AI 硬件及其供应链”改为“市场对 AI 硬件链的不同位置进行了显著但分化的重新定价”。
- 若无法取得统一行情，改用四张经营事实卡，不做拼接股价图。

### Slide 2 — 因为 GPU 必须不断被数据“喂饱”

**最强来源**

1. NVIDIA H200 product specification（B）
2. Micron FY2025 Q2 prepared remarks（B）
3. TrendForce HBM manufacturing estimates（C）

**可安全讲的 claim**

> “HBM 为加速器提供高带宽、近芯片的数据访问；在给定产能下，HBM 的较高硅耗、工艺与封装要求会占用更多先进 DRAM 资源。”

**必须保留的 caveat**

- H200 的 141 GB/4.8 TB/s 是单一产品规格，不证明所有 workload 都 memory-bound。
- `3×` 指 Micron 所说“同 bit output 的硅耗”，不是成本、价格、封装数或每片晶圆严格替代比。
- 普通 DRAM 的供需还受库存、PC/手机周期、良率和产能纪律影响。

**建议删改**

- 把“HBM 占用更多先进产能，也会挤压普通 DRAM 的供给”精确化为“在给定已安装产能下，HBM 降低可用于非 HBM 产品的 bit output 与部分先进工艺资源”。
- 不用 Chinchilla 解释 HBM 数据流；这里的 “data” 是内存数据搬运，不是训练语料规模，二者同词但不是同一 claim。

### Slide 3 — 他们凭什么相信，更多算力会换来更好的模型？

**最强来源**

1. Microsoft FY2024 earnings call（B）
2. Amazon 2024 10-K AWS additions（A，监管托管文件）
3. Alphabet/Meta official earnings materials（B）

**可安全讲的 claim**

> “云厂商披露了数百亿美元级基础设施投入，并把相当部分与 AI/云容量、客户需求和自有产品联系起来；这建立了‘巨大下注’的事实。”

**必须保留的 caveat**

- 各公司 capex 定义、财年、租赁处理不同，不能相加成“AI capex 总额”。
- 披露没有证明 scaling law 导致投资，也没有证明投资必然获得回报。

**建议删改**

- 副标题中的“更多算力换来更好的模型”增加 `well-directed` 或中文“配置得当的额外算力”。
- 若展示数字，每个数字带会计定义；不画总和。

### Slide 4 — 在 scaling law 之前，放大训练更像一次豪赌

**最强来源**

1. Hestness et al. 2017（A）
2. Rosenfeld et al. 2019（A）
3. Kaplan et al. 2020（A）

**可安全讲的 claim**

> “在大规模 Transformer LM 训练规划成熟之前，昂贵运行更难通过统一的小规模 sweep 预测和配置；Kaplan 把已有 learning-curve 思想系统化到 LM 的参数、数据和训练算力。”

**必须保留的 caveat**

- Kaplan 之前已有 neural/LM scaling 与联合模型—数据预测工作。
- “豪赌”是成本和规划隐喻，不是说 2020 前团队完全没有工程预测方法。

**建议删改**

- 标题改为“在 scaling 成为训练规划工具之前，大训练更像一次难以复跑的下注”。
- 删除任何“Kaplan 发明了 scaling law”的暗示。

### Slide 5 — 小实验画出了一条可以向前延伸的曲线

**最强来源**

1. Kaplan et al. 2020（A）
2. GPT-4 Technical Report（B）
3. Lilian Weng 2026 方法综述（C）

**可安全讲的 claim**

> “在架构、数据、优化和测量口径相对稳定的 regime 内，小规模 runs 可以拟合 aggregate loss 趋势，并用于估计更大运行。”

GPT-4 报告可作为实验室公开采用小模型外推的 B 级案例。

**必须保留的 caveat**

- power law 是经验拟合，不是自然界保证。
- fit region、参数计数、tokenizer、数据 mix、optimizer 和学习率日程会移动外推。
- “平均结果”不是对单次运行失败概率的完整预测。

**建议删改**

- 坐标可保留“训练资源 / 平均预测误差”，但口述明确 measured outcome 通常是 loss。
- “改善会继续”改为“在已验证 regime 内趋势可延伸；跨 regime 需要重新校准”。

### Slide 6 — 但这条曲线预测的不是“智能”

**最强来源**

1. Ganguli et al. 2022（A）
2. Kaplan et al. 2020（A）
3. MIT Technology Review 机制边界长文（C）

**可安全讲的 claim**

> “aggregate training/distribution loss 可以平滑，而具体能力、输入、失败方式和商业价值仍不具有同等可预测性。”

**必须保留的 caveat**

- 不能反向说 loss 与能力毫无关系；较低 loss 常与许多下游改善相关。
- “能力突然出现”还受指标离散化、prompting 和评测阈值影响，不能在本页断言所有 emergence 都是本体突变。

**建议删改**

- `Loss 可以理解为猜下一个 token 时平均错得多远`保留为近似解释，但不要等同于所有训练目标。
- 把“不能告诉我们某项能力会在哪个规模突然出现”改为“单凭这条 aggregate loss 曲线，不能可靠给出某项能力出现的具体规模”。

### Slide 7 — 现在给你一袋固定的算力筹码

**最强来源**

1. Kaplan et al. 2020（A）
2. Hoffmann et al. 2022（A）
3. Sardana et al. 2024 / Beyond Chinchilla-Optimal（A）

**可安全讲的 claim**

> “先固定预训练 FLOPs；在相近架构、数据 regime 和目标下，参数量与训练 token 竞争同一预算。”

**必须保留的 caveat**

- 这里暂时不计推理请求、延迟、显存与数据取得成本。
- token 数不等于有效新信息；质量、重复和 tokenizer 都会改变价值。

**建议删改**

- 页面角落增加：`same training compute`、`same data regime`、`minimize pretraining loss`。
- 将“另一部分用于让模型读更多 token”改为视觉分配，不暗示 FLOPs 可机械拆成两袋独立成本。

### Slide 8 — 2020：Kaplan 的答案偏向更大的模型

**最强来源**

1. Kaplan et al. 2020（A）
2. GPT-3 paper（A）
3. Porian et al. 2024（A）

**可安全讲的 claim**

> “Kaplan 在其参数计数和实验范围内得到固定训练 compute 下快速扩大模型、较慢增加 token、提前停止的配方；GPT-3 随后把 loss 趋势扩展到更大计算尺度。”

**必须保留的 caveat**

- 公开资料不能证明 GPT-3 的 175B 是由 Kaplan 公式直接算出的唯一选择。
- 后续工作把配方差异部分归因于 FLOP/参数计数、warmup、优化调参和局部拟合。
- 其持久贡献是预测式方法，不是 `C^0.73/C^0.27` 处方。

**建议删改**

- 标题改为“2020：Kaplan 把 LM scaling 变成训练规划工具”。
- 把“这套结果强化了行业对大模型路线的信心”降为口述：“它与 GPT-3 及随后偏大参数、约 300B-token 的公开训练范式相符；各实验室内部因果不可核验。”

### Slide 9 — 2022：Chinchilla 用同样的筹码赢了

**最强来源**

1. Hoffmann et al. 2022（A）
2. Porian et al. 2024（A）
3. PaLM 2 Technical Report（B）

**可安全讲的 claim**

> “在近似相同训练 FLOPs 下，70B Chinchilla 训练约 1.4T token，在论文评测中超过 280B Gopher；核心修正是固定训练预算的参数/token 分配。”

**必须保留的 caveat**

- `20 tokens/parameter` 是 regime-specific heuristic。
- Chinchilla 的 Approach 3 公布系数和置信区间存在复拟合问题；方向性结论强于精确常数。
- 这不是推翻 smooth loss scaling，而是改写 compute-allocation prescription。

**建议删改**

- 标题可改为“2022：Chinchilla 证明，当时的大模型普遍读得太少”。
- 脚注写 `same training FLOPs; 70B/1.4T vs 280B; baseline, not constant`。
- “新配方让参数量和训练数据更均衡地共同增长”改为“在该固定训练算力问题中，两者随 compute 近似同比增长”。

### Slide 10 — 所以，Scaling 从来不等于“只加参数”

**最强来源**

1. LLaMA / Llama 3 reports（B）
2. RETRO paper（A）
3. Compute Optimal Tokenization 2026（A，新研究）

**可安全讲的 claim**

> “训练算力最优、全生命周期成本最优和系统架构最优是不同问题；部署请求多时，更小模型训练更久可能降低长期推理成本，检索也可把部分能力放在参数之外。”

**必须保留的 caveat**

- LLaMA/Llama 3 是公司报告与自报结果。
- RETRO 的可比表现限于特定数据集/loss。
- 2026 tokenization 论文尚缺广泛复现，不应成为正文唯一支柱。

**建议删改**

- 标题改为“最优配方取决于你在优化哪张账单”。
- 先讲 `training-optimal / inference-optimal / system-specific` 三张账单；原来的五项清单移到 slide 11 或附录。
- Anthropic 扫描纸书可作视觉旁例，但不替代 LLaMA/RETRO 的技术证据。

### Slide 11 — 当预训练越来越贵，筹码开始流向新的阶段

**最强来源**

1. InstructGPT（A）
2. RETRO（A）
3. Anthropic context engineering（B）

**可安全讲的 claim**

> “前沿系统在预训练之外继续消耗显著资源：后训练塑造行为，推理时搜索/采样/验证按题分配计算，检索和记忆提供参数外信息，环境 rollout 又可回流为训练数据。”

**必须保留的 caveat**

- “流向”不意味着预训练预算绝对下降；更准确是系统边界扩展。
- 四类资源的计量、成本和成熟度不同，不能画成可互换的同质筹码。

**建议删改**

- 把线性四阶段改成闭环：environment → post-training 有反馈箭头。
- `Retrieval / Context / Memory` 作为侧轨贯穿 post-training、test time 和 environment。
- 标题中的因果“因为预训练越来越贵”可改为“模型训练完成后，算力仍在继续消费”，避免未经量化的预算迁移 claim。

### Slide 12 — 第三次改写：不只是把模型做大，而是决定在哪里花算力

**最强来源**

1. Snell et al. 2024（A）
2. OpenAI o1 technical post（B）
3. Kimi k1.5 report（B）

**可安全讲的 claim**

> “post-training RL 和 test-time compute 已显示新的、条件性的资源—性能轴；它们把问题从单次预训练规模扩展为跨阶段预算分配。”

**必须保留的 caveat**

- OpenAI/Kimi 曲线是团队自报，细节和独立复现有限。
- test-time 增益依赖题目难度、基础命中率、搜索多样性和 verifier。
- NVIDIA 的三分法是产业 taxonomy，且把若干机制混在同一“law”下。

**建议删改**

- 正文删除或脚注化 NVIDIA 品牌。
- Kimi 用于证明“实验室这样下注”，不用于证明 universal law。
- 用“axis/frontier”替代“新 law”；保留“不是三条同等成熟数学定律”。

### Slide 13 — 更多计算，必须经过正确的反馈，才可能变成能力

**最强来源**

1. Gao et al. 2022（A）
2. Snell et al. 2024（A）
3. Kapoor et al. 2024（A）

**可安全讲的 claim**

> “额外计算只有在 reward、verifier、环境和评测仍与真实目标对齐时，才可能提高所关心的结果；否则会出现 Goodhart、无效搜索或 scaffold/成本误归因。”

**必须保留的 caveat**

- “正确反馈”在开放任务中通常不可直接观察。
- Gao 的 gold reward 是受控代理；Snell 主要是数学；Kapoor 主要审计代码 agent。
- benchmark gain、可靠性、成本和现实效用必须分开。

**建议删改**

- `better outcome` 旁增加 `quality/reliability` 与 `cost/latency`。
- 把 Experience 继续明确为研究议程。
- 可保留 model collapse 作附录反例，不要让它抢占 reward/verifier/environment 三道门的主线。

### Slide 14 — 下一次听到 “Scaling”，先问四个问题

**最强来源**

1. Kaplan + Hoffmann（A，说明 law/recipe 区分）
2. Demis Hassabis 原始访谈（B，说明 scaling + invention）
3. Silver & Sutton / Shunyu Yao 原文（B，研究议程）

**可安全讲的 claim**

> “Scaling 不是单一旋钮。判断一个 claim 时要问：扩什么、测什么、固定什么、它究竟是经验规律、工程策略还是战略下注。”

**必须保留的 caveat**

- “Scaling 没有结束”是综合判断，不是可由一条论文直接证明的事实。
- “整个系统资源配置”比“整个生命周期都能按 law scale”更安全。

**建议删改**

- 结尾改为：“经典 loss scaling 仍是条件性预测工具；行业正在寻找多个新的资源前沿，但它们成熟度不同。”
- `What is being scaled?` 下可口述补充 `unique high-quality data / verified synthetic experience`，不增加正文信息墙。

## 七、四项特别裁决

### 1. 开场能否使用“四家公司股价一起疯涨”

**不能。** 现有同窗口证据直接反驳“一起疯涨”。可以使用：

> “同一波 AI 硬件需求把四家公司带到同一叙事里，但市场回报明显分化。”

最稳妥的视觉是 2024 统一 rebased adjusted-price/total-return 图，主动显示 Samsung 下跌；拿不到统一数据就用经营事实卡。

### 2. Anthropic/OpenAI 案例能否支持“scale data”

**可以，但只能支持工程/战略层。**

- 支持：数据已成为需要采购、授权、过滤、去重、重加权、人工生产和合成验证的供应链。
- 不支持：采购规模与 Claude/GPT 能力增益的定量因果；任一合作内容确实进入某一基础模型；所有书都用于所有 Claude；版权争议来源是 scaling 的必要条件。
- 技术主证据应由 Chinchilla、GPT-3 数据工程、Muennighoff、RefinedWeb 等承担。

### 3. Kaplan → Chinchilla 是否仍适合承担第二幕

**适合，且仍是最佳主线，但必须从“英雄论文史”改成“方法演化史”。**

推荐一句话结构：

> “前史已有可预测 learning curves；Kaplan 把 Transformer LM scaling 系统化为训练规划；Chinchilla 用更好的固定算力实验改写分配；LLaMA 又说明训练最优不是部署最优。”

### 4. “Scale 整个生命周期”是什么

**首选：产业框架。**
**可讲的事实弱版本：** 预训练之外的后训练、推理时计算、检索/记忆和环境反馈已产生条件性增益并获得投入。
**战略下注：** RL、experience、长期 agent 环境可能形成更大资源前沿。
**不是：** 已经拟合出的统一新定律，或三条同等成熟的 laws。

## 八、需要人工复核的事项

### 必须在制作/发布前人工复核

1. **YouTube 自动字幕**：Jared Kaplan、Noam Brown、Computerphile、Yann LeCun 等任何逐字引用、术语、人名和时间戳。
2. **付费墙/访问限制**：Reuters 401；SemiAnalysis 付费正文；部分 IR/HN/社交页面可能触发机器人限制。不要从搜索摘要恢复长引语。
3. **实时股价**：四股统一数据商、交易所日历、复权方式、端点日期、币种和股息口径；当前 Micron `+0.6%` 仅为低等级交叉值。
4. **财报刷新**：当前开场经营窗口主要是 2024/early-2025；若演讲要说“最近”，必须重开最新 10-Q/10-K、DART/KRX 和 earnings transcript。
5. **Bartz docket**：2026-07-20 final approval 已核验；截至 2026-08-24 的任何上诉及 settlement effective/distribution 状态需 PACER/第九巡回 docket 人工复核。
6. **Amazon 引语**：当前需求逻辑使用第三方 transcript copy，逐字引用前回到 Amazon 官方 webcast/IR。

### 已核验但仍需显著标注新近性

7. **2026 索引**：`arXiv:2605.01188` 与 Lilian Weng 2026 文章均真实可访问；前者是新论文、后者是解释文章，不得因日期新就升格为共识。
8. **2026 可疑财务索引**：基础设施研究已正确排除无法与监管文件对账、出现内部不合理数字的搜索结果；不得重新纳入。
9. **公司自报 benchmark**：Kimi、OpenAI o1、DeepSeek-R1、Llama、Gemini 等均需标“team-reported”，除非另有独立复现。
10. **二手引语**：Noam Brown `100,000×`、任何“Kaplan 公式造出 GPT-3”、任何“Anthropic 700 万本全用于 Claude”的说法均不得使用。

## 九、对 `reference/README.md` 的精确修改清单

以下是编辑清单，不在本审计中直接修改：

1. 在文件开头加入本审计的 **A–E 证据等级表**，并给每个精选来源标级。
2. 将 “Eight primary sources” 改为 “Eight core sources”；其中公司技术报告不再泛称与论文同义的 primary technical evidence。
3. `Lilian Weng` 条目从 Foundations 移到 “Methodological explainers”，类型改为 C 级技术综述；保留 2026-06-24。
4. Foundations 增加一行前史：Hestness 2017、Rosenfeld 2019；说明 Kaplan 是系统化/普及节点而非首个 neural scaling law。
5. Kaplan 条目增加：旧 compute-allocation prescription 后来受 Chinchilla 与复现工作修正；持久贡献是条件性 loss 外推和训练规划。
6. Chinchilla 条目增加：70B/1.4T vs 280B、同训练 FLOPs；Approach 3 精确系数存在复拟合争议，20:1 仅 heuristic。
7. 新增 LLaMA/Llama 3 核心条目，专门解释 training-optimal 与 inference-optimal 不同。
8. 将 RETRO、Ganguli、Gao、Snell、Kapoor 等重复长引语各保留一次；主题文件改用链接，不重复整段。
9. 给 Kimi、OpenAI o1、NVIDIA、公司 model card 统一加 `team-reported / company-strategy` 标记。
10. NVIDIA 日期统一为 Kari Briski、2025-02-12；明确其证据等级 B/D、用途是 taxonomy。
11. METR 日期拆为 arXiv 2025-03-18、官方博客 2025-03-19。
12. data-wall 注释统一为：存量约 300T，90% CI 100T–1000T；耗尽年份 80% CI 2026–2032；二者不是同一个区间。
13. 新增 Bartz 法律状态更新：2026-07-20 final approval/final judgment；说明和解范围、地区法院裁定层级及上诉状态需 docket 复核。
14. Bartz 条目将 2025 order 与 2026 final settlement order 分成两个 A 级来源，不再让 Reuters 承担法律状态。
15. 把 “Team at publication” 等身份字段统一为论文作者/机构，不将第一作者、模型名和团队名混写。
16. 保留并加粗四个 context flags：`R1-Zero ≠ R1`、`100,000× = poker`、`three laws = taxonomy`、`loss ≠ capability`。
17. 新增“访问限制”小节：Reuters 401、动态公司页面、YouTube 自动字幕、SemiAnalysis paywall、HN 动态快照；后续全量结果见 `LINK_CHECK.md`。
18. 将 Era of Experience 和 The Second Half 明确放入 `Research agendas / viewpoints`，不要与 A 级实证论文并列成已成立 axis。
19. 删除来源卡中对同一 claim 的重复“最清楚/最权威/最关键”形容词，改为明确它支持哪一页、哪一句 claim。
20. README 末尾增加一条总边界：等级代表用途；A 级单篇论文也不自动建立跨任务通用 law。

## 十、对 `OUTLINE.md` 的精确修改清单

以下是编辑清单，不在本审计中直接修改：

1. 序幕“行情与业绩”改为“分化的行情与显著经营变化”，避免同涨暗示。
2. Slide 1 标题改为“AI 让内存公司进入同一舞台，但没有让它们同涨”或使用经营事实卡标题。
3. Slide 1 的“只说事实”后增加：Samsung/Micron 是负向或弱表现对照。
4. Slide 2 把“挤压普通 DRAM 供给”改成给定产能下的 bit output/资源约束精确表述。
5. Slide 2 口述区分 HBM 的数据搬运与训练数据规模，避免同一个 “data” 造成概念偷换。
6. Slide 3 的问题改成“为什么相信配置得当的额外算力会改善测得的模型结果？”
7. Slide 4 标题改为“在 scaling 成为训练规划工具之前，大训练更像一次难以复跑的下注”。
8. Slide 4 脚注加入 `Hestness 2017 → Rosenfeld 2019 → Kaplan 2020`。
9. Slide 5 将“改善会继续”改成“在已验证 regime 内呈平滑趋势，跨 regime 需重新拟合”。
10. Slide 6 将“不能告诉我们能力会在哪突然出现”改为“单凭 aggregate loss 曲线不能可靠给出具体能力出现规模”。
11. Slide 7 增加三个固定条件：same training FLOPs、same data regime、minimize pretraining loss。
12. Slide 8 标题改为“Kaplan 把 LM scaling 变成训练规划工具”。
13. Slide 8 删除或降级“强化行业信心”；禁止“Kaplan 公式直接决定 GPT-3”。
14. Slide 9 明写 `70B / 1.4T tokens / same training FLOPs / 280B Gopher`。
15. Slide 9 将 20:1 放脚注并写 `baseline, not constant`。
16. Slide 10 标题改为“最优配方取决于你在优化哪张账单”。
17. Slide 10 用 training-optimal、inference-optimal、system-specific 三框替代五项散列表；LLaMA/Llama 3 承担第二次反转。
18. Slide 10 的 RETRO 留作“参数外资源”例子；Anthropic 扫书只作 data-supply-chain 旁例。
19. Slide 11 删除“行业预算已从预训练转走”的强暗示，改成“训练后仍持续消费资源”。
20. Slide 11 将生命周期画成闭环，增加 environment → post-training 回流；retrieval/context/memory 画侧轨。
21. Slide 12 全部用 `axis/frontier/framework`，不把厂商口号写成 law。
22. Slide 12 将 NVIDIA 与 Kimi 移到脚注/口述，正文只保留实验性资源分配概念。
23. Slide 13 在 better outcome 后分出质量/可靠性与成本/延迟。
24. Slide 13 保留 Gao、Snell、Kapoor 三个互补证据；Era of Experience 只标研究议程。
25. Slide 14 结论改为：“经典 loss scaling 仍是条件性预测工具；新的资源前沿已出现，但成熟度不同。”
26. 全文统一术语：`Kaplan et al.`、`Hoffmann et al. / Chinchilla`、`R1-Zero ≠ R1`、`test-time compute`。
27. 全文凡出现“最近/当前”经营或市场数字，添加明确 cutoff；发布前一周做统一行情和财报刷新。
28. 时间分配不必变；若压缩，仍优先保留 slides 6、9、13 的证据边界。

## 十一、最终可用的一句话主旨

> Scaling laws 仍能在稳定条件下帮助预测 aggregate loss 和规划训练，但“下一步 scale 什么”已经变成跨数据、训练、推理、检索与环境的资源配置问题；这些新轴有真实结果，却还不是同一条可普遍外推的新定律。
