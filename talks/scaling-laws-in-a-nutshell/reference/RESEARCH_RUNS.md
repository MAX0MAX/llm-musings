# Scaling Laws Research Runs

用于记录并行研究 Agent 的任务、产物和执行状态，便于中断恢复与后续复盘。

## Run: 2026-08-24

**目标：** 为 `OUTLINE.md` 的三幕叙事补充可核验的互联网证据，并收集优质科普叙事样本。

**统一要求：**

- 优先使用原始论文、法院文件、公司技术报告、官方访谈和财报。
- 媒体报道用于补充背景；VC/PE 文章用于分析产业叙事，不代替技术证据。
- Hacker News 用于观察社区反响，不作为事实依据。
- 每条来源必须包含标题、作者或机构、发布日期、链接、收录原因和证据边界。
- 区分事实、作者观点、公司战略表述、诉讼指控和法院认定。
- 不为现有大纲寻找预设结论；发现证据不支持时必须明确报告。

### Agent 01 — 大模型的数据需求

- **状态：** completed
- **Agent ID：** `dcca5fdc-c6c9-41b5-acdb-c6bc09897058`
- **范围：** Anthropic、OpenAI 获取和扩展训练数据的案例；书籍、网页、授权数据、合成数据与数据稀缺。
- **法律深度：** 版权诉讼只介绍必要背景，不做法律专题研究。
- **输出：** `data-scaling.md`
- **结果：** 整理 18 条来源卡片；覆盖两家公司扩展公开、授权、人工和合成数据的路径，并区分法院事实、诉讼指控、公司披露与媒体概括。
- **核验备注：** 文件已生成并抽查；部分 Reuters/OpenAI 页面存在访问限制，最新模型的完整数据配方和来源比例未公开。

### Agent 02 — 科普内容与叙事模板

- **状态：** completed
- **Agent ID：** `8303001d-8901-4bc8-b9a3-90f6216ca4fe`
- **范围：** YouTube、Latent Space、研究机构、VC/PE、survey、重量级报道和可引用观点。
- **重点：** 不只搜集链接，还要分析开场、节奏、类比、反转和结尾。
- **输出：** `explainers-and-storytelling.md`
- **结果：** 16 个候选、精选 10 个；已覆盖来源元数据、叙事拆解、误导风险、推荐顺序和大纲修改建议。
- **核验备注：** 文件已生成并抽查；YouTube 自动字幕仍需在最终引用前人工复听。

### Agent 03 — Kaplan / Chinchilla 影响验证

- **状态：** completed
- **Agent ID：** `877ad6e5-0df7-47c2-bc94-7f76f2f1db58`
- **范围：** 开放式验证两项工作对 scaling-law 研究和训练实践的真实影响。
- **禁止预设：** 允许结论为保留、降权、补充前史或替换当前叙事。
- **输出：** `kaplan-and-chinchilla.md`
- **结果：** 审查 23 个来源，其中 22 个为一手或官方来源；裁决为保留转折主线，但降权 Kaplan 的原创性和具体配方，补入前史、复现修正与 inference-optimal 后史。
- **核验备注：** 文件已生成并抽查；闭源 frontier lab 未充分披露参数/token 配方，不能据此断言其当前具体做法。

### Agent 04 — 生命周期 Scaling 的一手证据

- **状态：** completed
- **Agent ID：** `6ac31199-2cd1-48f4-aaab-8094ea234871`
- **范围：** Post-training、test-time compute、retrieval、environment 和 experience；AI Lab 负责人访谈及官方研究。
- **输出：** `lifecycle-scaling.md`
- **结果：** 整理 28 条一手与关键反方来源；分别评估 post-training、test-time compute、retrieval/context/memory 与 environments/experience，并映射至 slides 11–13。
- **核验备注：** 文件已生成并抽查；“scale 整个生命周期”适合作为产业框架与战略下注，不应表述为已经成立的新定律。

### Agent 05 — 社区与产业观点

- **状态：** completed
- **Agent ID：** `ad6efdb5-2e11-4844-88e7-ccd31bd8bb5f`
- **范围：** Hacker News 高分讨论、工程师评论、VC/产业分析，以及支持和质疑 lifecycle scaling 的代表观点。
- **输出：** `community-and-industry.md`
- **结果：** 精选 13 条来源，包括 8 个 Hacker News 讨论和 5 个产业分析；逐条记录支持/质疑、利益相关、热度快照、适用页面和证据边界。
- **核验备注：** 文件已生成并抽查；HN 身份与评论不作为事实依据，部分产业分析存在付费访问限制。

### Agent 06 — GPU、HBM 与开场证据

- **状态：** completed
- **Agent ID：** `69a6241f-1629-4763-9b63-e52c2f57bdb6`
- **范围：** NVIDIA、SK 海力士、三星、美光；AI capex、HBM 需求、供给约束和存储周期。
- **输出：** `ai-infrastructure-and-hbm.md`
- **结果：** 整理 21 条来源；覆盖四家公司经营事实、HBM 技术与供给、hyperscaler capex、开场因果边界和 slides 1–3 素材建议。
- **核验备注：** 文件已生成并抽查；不一致的 2026 索引材料已排除，最终行情图和部分财报引语需在发布前从统一授权数据源刷新。

### Agent 07 — 跨主题证据审计

- **状态：** completed
- **Agent ID：** `217ac871-32a8-48b9-86fe-14a23542ede7`
- **范围：** 对 Agent 01–06 的结果做交叉核验、重复项识别、证据分级和 14 页映射。
- **输出：** `EVIDENCE_AUDIT.md`
- **结果：** 审计 9 个输入文件；完成重复/冲突识别、A–E 证据分级、14 页逐页裁决及 README/OUTLINE 精确修改清单。
- **核验备注：** 四股并未同涨；Bartz v. Anthropic 法律状态已更新至 2026-07-20 最终和解批准。

### Agent 08 — 全量来源链接索引

- **状态：** completed
- **Agent ID：** `735a3962-1c46-4ae4-ade9-11a7cc1a1105`
- **范围：** 汇总并去重全部研究材料，为每项附日期、直接链接、证据等级和专题位置；明确标记缺失或需人工复核的链接。
- **输出：** `ALL_SOURCES.md`
- **结果：** 去重收录 123 项；123/123 至少有一个直接链接；19 项因付费墙、自动字幕、动态数据、二手托管或访问限制标为需人工复核。
- **核验备注：** 文件已生成并抽查；完全缺链项目为 0。

### Agent 09 — 实际链接可用性检查

- **状态：** cancelled — 用户转向阅读清单任务，检查未完成
- **Agent ID：** 待分配
- **范围：** 对本 topic 全部 Markdown 中的外部链接执行实际 HTTP 检查，区分真失效、站点阻挡、限流、重定向和临时错误；修复确认错误的链接。
- **输出：** `LINK_CHECK.md`

## 集成阶段

- **状态：** completed
- **任务：**
  1. 交叉核验日期、原始链接、引语和法律表述。
  2. 删除重复、低质量和纯营销材料。
  3. 将证据映射到 `OUTLINE.md` 的 14 页。
  4. 更新 `reference/README.md` 为精选索引。
  5. 记录哪些原有叙事获得支持、需要降权或应被修改。
- **已应用：**
  - `OUTLINE.md` 已根据逐页审计修正开场、Kaplan/Chinchilla 定位、部署目标和 lifecycle scaling 口径。
  - `reference/README.md` 已增加 A–E 证据分级、研究索引、scaling 前史、LLaMA/Llama 3、Bartz 法律状态和访问限制。
  - `data-scaling.md` 已更新 Bartz v. Anthropic 至 2026-07-20 最终和解批准，并保留上诉/docket 核验边界。
- **发布前人工检查：** YouTube 逐字引语、统一行情数据、最新财报、付费墙材料、Bartz 后续 docket。
