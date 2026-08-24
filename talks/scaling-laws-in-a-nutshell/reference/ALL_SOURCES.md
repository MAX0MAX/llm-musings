# Scaling Laws, in a Nutshell — 全部来源总索引

> 整理日期：2026-08-25
> 范围：`README.md`、`READING_LIST.md`、`data-scaling.md`、`explainers-and-storytelling.md`、`kaplan-and-chinchilla.md`、`lifecycle-scaling.md`、`community-and-industry.md`、`ai-infrastructure-and-hbm.md`、`EVIDENCE_AUDIT.md`。
> 去重口径：同一作品的论文页/PDF、官方发布页、视频/逐字稿、代码/数据仓库合并为一条；HN 讨论与被讨论的原文分别计数。`v1`、`pdf`、`html` 等 arXiv 变体不重复计数。

## 统计

- **去重后材料总数：124**
- **按等级：A 38；B 50；C 24；D 4；E 8**
- **按材料类型：论文/技术报告 43；法院/监管文件 3；公司财报/产品/官方工程与战略材料 30；访谈/视频/课程/个人文章 21；独立研究/媒体/行业分析 15；VC/卖方研究 4；HN 讨论 8**
- **链接覆盖：124/124 至少有一个直接链接。**
- **需人工复核：19 条材料、归并为 15 类问题**（见文末；均已有可打开或可恢复的链接，但存在付费墙、JS/超时、自动字幕、动态数据、二手托管或日期/版本问题）。

等级沿用本目录口径：A 原始论文/法院/监管；B 原始访谈、公司技术与经营材料；C 独立综合、教学与专业研究；D VC/卖方产业论述；E 社区讨论。

专题简称：`总览`=`README.md`；`阅读`=`READING_LIST.md`；`数据`=`data-scaling.md`；`叙事`=`explainers-and-storytelling.md`；`KC`=`kaplan-and-chinchilla.md`；`生命周期`=`lifecycle-scaling.md`；`社区`=`community-and-industry.md`；`基建`=`ai-infrastructure-and-hbm.md`；`审计`=`EVIDENCE_AUDIT.md`。

## A — 原始论文、法院与监管材料（38）

- **A01｜2017-12-01｜Deep Learning Scaling is Predictable, Empirically｜Joel Hestness et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/1712.00409)｜支持 Kaplan 之前已有跨领域可预测 learning curves。｜专题：总览、KC、审计**
- **A02｜2019-09-27｜A Constructive Prediction of the Generalization Error Across Scales｜Jonathan S. Rosenfeld et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/1909.12673)｜支持模型规模与数据规模的联合误差面前史。｜专题：总览、KC、审计**
- **A03｜2020-01-23｜Scaling Laws for Neural Language Models｜Jared Kaplan et al., OpenAI/Johns Hopkins｜论文｜[直接：arXiv](https://arxiv.org/abs/2001.08361)｜LM loss scaling、固定算力分配与小模型外推的核心原始证据。｜专题：总览、叙事、KC、审计**
- **A04｜2022-03-29｜Training Compute-Optimal Large Language Models｜Jordan Hoffmann et al., DeepMind｜论文｜[直接：arXiv](https://arxiv.org/abs/2203.15556)｜Chinchilla 70B/1.4T 与 Gopher 280B 同训练 FLOPs 对照。｜专题：总览、数据、叙事、KC、审计**
- **A05｜2021-12-08｜Improving language models by retrieving from trillions of tokens (RETRO)｜Sebastian Borgeaud et al., DeepMind｜论文｜[直接：arXiv](https://arxiv.org/abs/2112.04426)；[补充：官方博客](https://deepmind.google/blog/improving-language-models-by-retrieving-from-trillions-of-tokens/)｜支持检索库作为参数外资源轴。｜专题：总览、生命周期、审计**
- **A06｜2022-02-15｜Predictability and Surprise in Large Generative Models｜Deep Ganguli et al., Anthropic｜论文｜[直接：arXiv](https://arxiv.org/abs/2202.07785)｜支持“aggregate loss 可预测，不等于具体行为可预测”。｜专题：总览、KC、审计**
- **A07｜2022-10-19｜Scaling Laws for Reward Model Overoptimization｜Leo Gao, John Schulman, Jacob Hilton｜论文｜[直接：arXiv](https://arxiv.org/abs/2210.10760)｜支持代理 reward 过度优化与 Goodhart 风险。｜专题：总览、生命周期、审计**
- **A08｜2024-06-27｜Resolving Discrepancies in Compute-Optimal Scaling of Language Models｜Tomer Porian et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/2406.19146)｜独立复现并解释 Kaplan/Chinchilla 差异。｜专题：总览、KC、审计**
- **A09｜2024-07-01｜AI Agents That Matter｜Sayash Kapoor et al., Princeton｜论文｜[直接：arXiv](https://arxiv.org/abs/2407.01502)｜支持 agent 成本控制、复现与 scaffold 归因边界。｜专题：总览、生命周期、社区、审计**
- **A10｜2024-08-06｜Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters｜Charlie Snell et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/2408.03314)｜支持 test-time compute 的难度、verifier 与预算依赖。｜专题：总览、生命周期、叙事、审计**
- **A11｜2020-05-28｜Language Models are Few-Shot Learners｜Tom B. Brown et al., OpenAI｜论文｜[直接：arXiv](https://arxiv.org/abs/2005.14165)；[正式论文 PDF](https://proceedings.neurips.cc/paper_files/paper/2020/file/1457c0d6bfcb4967418bfb8ac142f64a-Paper.pdf)；[补充材料](https://papers.neurips.cc/paper_files/paper/2020/file/1457c0d6bfcb4967418bfb8ac142f64a-Supplemental.pdf)｜GPT-3 数据混合、过滤、去重及 Kaplan 曲线扩展。｜专题：数据、KC、审计**
- **A12｜2024-05-28（ICML 2024 更新版）｜Will we run out of data? Limits of LLM scaling based on human-generated data｜Pablo Villalobos et al., Epoch AI｜论文｜[直接：PMLR](https://proceedings.mlr.press/v235/villalobos24a.html)；[补充：Epoch 分析](https://epoch.ai/publications/will-we-run-out-of-data-limits-of-llm-scaling-based-on-human-generated-data)｜公共人类文本存量与 2026–2032 条件预测。｜专题：数据、社区、审计**
- **A13｜2023-05-25｜Scaling Data-Constrained Language Models｜Niklas Muennighoff et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/2305.16264)｜固定 compute 下，重复最多约四个 epoch 相比同量 unique data 的 loss 变化可忽略；之后追加 compute 的价值逐渐衰减。｜专题：数据、KC、审计**
- **A14｜2023-06-01｜The RefinedWeb Dataset for Falcon LLM｜Guilherme Penedo et al., TII｜论文/数据集｜[直接：arXiv](https://arxiv.org/abs/2306.01116)｜支持过滤和去重后的网页数据可形成大规模高质量语料。｜专题：数据、审计**
- **A15｜2024-07-24｜AI models collapse when trained on recursively generated data｜Ilia Shumailov et al.｜论文｜[直接：Nature](https://www.nature.com/articles/s41586-024-07566-y)｜支持无甄别递归合成数据的尾部丢失风险。｜专题：数据、生命周期、社区、审计**
- **A16｜2019-09-04｜Beyond Human-Level Accuracy: Computational Challenges in Deep Learning｜Joel Hestness et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/1909.01736)｜将 learning curves 用于能力目标所需资源估计。｜专题：KC**
- **A17｜2018-12-14｜An Empirical Model of Large-Batch Training｜Sam McCandlish et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/1812.06162)｜Kaplan 研究计划中的 batch/compute 工程前史。｜专题：KC**
- **A18｜2020-10-28｜Scaling Laws for Autoregressive Generative Modeling｜Tom Henighan et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/2010.14701)｜将 scaling-law 方法扩展到图像、视频、多模态与数学。｜专题：KC**
- **A19｜2024-04-15｜Chinchilla Scaling: A Replication Attempt｜Tamay Besiroglu et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/2404.10102)｜复核 Chinchilla Approach 3 系数与置信区间。｜专题：KC、审计**
- **A20｜2024-06-18｜Reconciling Kaplan and Chinchilla Scaling Laws｜Tim Pearce, Jinyeop Song｜论文｜[直接：arXiv](https://arxiv.org/abs/2406.12907)｜支持参数计数与局部尺度解释指数差异。｜专题：KC**
- **A21｜2024-01-01｜Beyond Chinchilla-Optimal: Accounting for Inference in Language Model Scaling Laws｜Nikhil Sardana et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/2401.00448)｜把推理需求加入训练—服务总成本函数。｜专题：KC、审计**
- **A22｜2026-05（arXiv v1 月份）｜Compute Optimal Tokenization｜Meta AI researchers｜论文｜[直接：arXiv](https://arxiv.org/abs/2605.01188)｜支持跨 tokenizer 用 bytes/parameter 重新审视 20:1；新近结果。｜专题：KC、审计**
- **A23｜2022-03-04｜Training language models to follow instructions with human feedback｜Long Ouyang et al., OpenAI｜论文｜[直接：arXiv](https://arxiv.org/abs/2203.02155)；[补充：官方说明](https://openai.com/index/instruction-following/)｜InstructGPT 的 SFT、reward model 与 RLHF 实验。｜专题：生命周期、审计**
- **A24｜2022-12-15｜Constitutional AI: Harmlessness from AI Feedback｜Yuntao Bai et al., Anthropic｜论文/研究报告｜[直接：官方研究页](https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback)｜支持 RLAIF 与原则驱动的可扩展监督。｜专题：生命周期**
- **A25｜2023-05-31｜Let’s Verify Step by Step / Improving mathematical reasoning with process supervision｜Hunter Lightman et al., OpenAI｜论文/研究报告｜[直接：官方研究页](https://openai.com/index/improving-mathematical-reasoning-with-process-supervision/)｜支持过程监督和 verifier 质量。｜专题：生命周期**
- **A26｜2024-08-05｜Self-Taught Evaluators｜Tianlu Wang et al., Meta FAIR｜论文｜[直接：arXiv](https://arxiv.org/abs/2408.02666)；[补充：代码/数据](https://github.com/facebookresearch/RAM/tree/main/projects/self_taught_evaluator)｜支持无人工偏好标签的合成 evaluator 训练。｜专题：生命周期**
- **A27｜2023-10-03｜Large Language Models Cannot Self-Correct Reasoning Yet｜Jie Huang et al., Google DeepMind｜论文｜[直接：DeepMind 论文页](https://deepmind.google/research/publications/48252/)｜支持无外部反馈的自我纠错可能退化。｜专题：生命周期**
- **A28｜2025（Nature 版；精确日未在索引材料中给出）｜Olympiad-level formal mathematical reasoning with reinforcement learning｜Google DeepMind AlphaProof team｜论文｜[直接：Nature](https://www.nature.com/articles/s41586-025-09833-y)；[补充：2024-07-25 官方博客](https://deepmind.google/blog/ai-solves-imo-problems-at-silver-medal-level/)｜支持 Lean verifier、test-time RL 与自生成经验。｜专题：生命周期**
- **A29｜2023-07-07｜Lost in the Middle: How Language Models Use Long Contexts｜Nelson F. Liu et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/2307.03172)｜区分上下文容量与实际利用率。｜专题：生命周期**
- **A30｜2022-10-06｜ReAct: Synergizing Reasoning and Acting in Language Models｜Shunyu Yao et al.｜论文｜[直接：arXiv](https://arxiv.org/abs/2210.03629)；[补充：Google Research](https://research.google/blog/react-synergizing-reasoning-and-acting-in-language-models/)｜把 reasoning、检索、行动与环境反馈连接起来。｜专题：生命周期**
- **A31｜2025-06（论文月）｜AlphaEvolve: A Gemini-powered coding agent for designing advanced algorithms｜Google DeepMind｜论文｜[直接：arXiv PDF](https://arxiv.org/pdf/2506.13131)；[补充：2025-05-14 官方博客](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/)｜支持可执行 evaluator 驱动的生成—评分—进化闭环。｜专题：生命周期**
- **A32｜2025-03-18｜Measuring AI Ability to Complete Long Software Tasks｜METR｜论文｜[直接：arXiv](https://arxiv.org/abs/2503.14499)；[补充：分析代码](https://github.com/METR/eval-analysis-public)；[补充：2025-03-19 研究博客](https://metr.org/blog/2025-03-19-measuring-ai-ability-to-complete-long-tasks/)｜支持 agent 任务时长趋势及可靠性边界。｜专题：生命周期、叙事、审计**
- **A33｜2024-10-09｜SWE-Bench+: Enhanced Coding Benchmark for LLMs｜作者见论文｜论文｜[直接：arXiv](https://arxiv.org/abs/2410.06992)｜补充 agent benchmark 的泄漏、弱测试与评分问题。｜专题：生命周期**
- **A34｜2024-10-02｜OpenMathInstruct-2: Accelerating AI for Math with Massive Open-Source Instruction Data｜Shubham Toshniwal et al., NVIDIA｜论文/数据集｜[直接：arXiv](https://arxiv.org/abs/2410.01560)；[补充：数据集](https://huggingface.co/datasets/nvidia/OpenMathInstruct-2)｜支持强教师、问题多样性、格式与 14M 合成数学样本的消融结论。｜专题：数据**
- **A35｜2025-06-23｜Bartz v. Anthropic PBC — Order on Fair Use｜U.S. District Court, N.D. California；Judge William Alsup｜法院命令｜[Dkt. 231 法院 PDF：Justia 托管](https://cases.justia.com/federal/district-courts/california/candce/3%3A2024cv05417/434709/231/0.pdf)；[补充：U.S. Copyright Office 两页摘要](https://www.copyright.gov/fair-use/summaries/Bartz-v-Anthropic-PBC-787-F-Supp-3d-1007-ND-Cal-2025.pdf)｜Anthropic 的 Books3/LibGen/PiLiMi、纸书采购与扫描事实；版权局材料仅作摘要，不能替代法院命令。｜专题：总览、数据、审计**
- **A36｜2026-07-20｜Bartz v. Anthropic — Order Granting Final Approval and Judgment｜U.S. District Court, N.D. California；Judge Araceli Martínez-Olguín｜法院命令｜[Dkt. 680 法院 PDF：Justia 托管](https://cases.justia.com/federal/district-courts/california/candce/4%3A2024cv05417/434709/680/0.pdf)｜15 亿美元集体和解 final approval/final judgment。**需人工复核后续上诉与生效/分配状态。**｜专题：总览、数据、审计**
- **A37｜2025-02-07｜Amazon 2024 Form 10-K — Property and Equipment Additions｜Amazon / U.S. SEC filing｜10-K 监管文件（Amazon 托管副本）｜[直接：Amazon 2024 Annual Report PDF](https://s2.q4cdn.com/299287126/files/doc_financials/2025/ar/Amazon-2024-Annual-Report.pdf)｜印刷页 68 的 AWS 与公司 2024 property-and-equipment additions。｜专题：基建、审计**
- **A38｜2023-04-28｜Are Emergent Abilities of Large Language Models a Mirage?｜Rylan Schaeffer, Brando Miranda, Sanmi Koyejo｜论文｜[直接：arXiv](https://arxiv.org/abs/2304.15004)｜支持在固定模型输出上，非线性或不连续评价指标可能产生表观“涌现”，为能力曲线边界提供反证。｜专题：阅读**

## B — 一手公司材料、原始访谈与观点（50）

- **B01｜2023-02-27｜LLaMA: Open and Efficient Foundation Language Models｜Hugo Touvron et al., Meta｜公司技术报告｜[直接：arXiv](https://arxiv.org/abs/2302.13971)｜支持为推理预算训练更小模型更久。｜专题：总览、KC、审计**
- **B02｜2024-07-23｜The Llama 3 Herd of Models｜Abhimanyu Dubey et al., Meta｜公司技术报告｜[直接：arXiv](https://arxiv.org/abs/2407.21783)｜支持团队自拟合 scaling 与小模型 inference-optimal 偏离。｜专题：总览、KC、审计**
- **B03｜2024-01-05｜DeepSeek LLM: Scaling Open-Source Language Models with Longtermism｜DeepSeek-AI｜公司技术报告｜[直接：arXiv](https://arxiv.org/abs/2401.02954)｜支持 scaling law 需按团队数据/架构重拟合。｜专题：总览、KC、审计**
- **B04｜2025-01-22｜Kimi k1.5: Scaling Reinforcement Learning with LLMs｜Kimi Team / Moonshot AI｜公司技术报告｜[直接：arXiv](https://arxiv.org/abs/2501.12599)；[补充：官方仓库](https://github.com/MoonshotAI/kimi-k1.5)｜RL/长上下文作为新战略轴的团队自报结果。｜专题：总览、生命周期、审计**
- **B05｜2023-03-15｜GPT-4 Technical Report｜OpenAI｜公司技术报告｜[直接：arXiv](https://arxiv.org/abs/2303.08774)；[官方 PDF](https://cdn.openai.com/papers/gpt-4.pdf)｜支持小模型外推与公开/授权数据类别，同时显示透明度边界。｜专题：数据、KC、审计**
- **B06｜2023-05-17｜PaLM 2 Technical Report｜Rohan Anil et al., Google｜公司技术报告｜[直接：arXiv](https://arxiv.org/abs/2305.10403)｜支持参数和数据近同比扩展的实验室复核。｜专题：KC、审计**
- **B07｜2025-01-22｜DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning｜DeepSeek-AI｜公司技术报告｜[直接：arXiv](https://arxiv.org/abs/2501.12948)｜区分 R1-Zero 纯 RL 与正式 R1 多阶段训练。｜专题：生命周期、审计**
- **B08｜2024-03-08｜Gemini 1.5: Unlocking multimodal understanding across millions of tokens of context｜Gemini Team / Google｜公司技术报告｜[直接：arXiv PDF](https://arxiv.org/pdf/2403.05530)｜长上下文单 needle 强结果与 multi-needle 退化。｜专题：生命周期**
- **B09｜2025-05｜System Card: Claude Opus 4 & Claude Sonnet 4｜Anthropic｜公司系统卡｜[直接：Anthropic](https://www.anthropic.com/claude-4-model-card)｜训练数据类别、爬虫、去重与分类披露。｜专题：数据、审计**
- **B10｜2024-08-08｜GPT-4o System Card｜OpenAI｜公司系统卡｜[直接：OpenAI](https://openai.com/index/gpt-4o-system-card/)｜网页、代码、数学、多模态、合作和合成安全数据类别。｜专题：数据**
- **B11｜首次发布日期未知；持续更新｜How ChatGPT and our foundation models are developed｜OpenAI Help Center｜公司说明｜[直接：OpenAI Help](https://help.openai.com/en/articles/7842364-how-chatgpt-and-our-foundation-models-are-developed)｜OpenAI 对公开、合作、人类提供及合成数据的概括。**2026-08-24 链接检查返回 200；动态页面仍需记录访问日或存档版本。**｜专题：数据、审计**
- **B12｜2023-11-09｜OpenAI Data Partnerships｜OpenAI｜公司战略公告｜[直接：OpenAI](https://openai.com/index/data-partnerships/)｜证明其征集非公开、长篇、多模态数据的战略。**2026-08-24 链接检查返回 200；征集意图不证明数据已进入具体模型。**｜专题：数据**
- **B13｜2024-04-29｜We’re bringing the Financial Times’ world-class journalism to ChatGPT｜Financial Times / OpenAI｜官方合作公告｜[直接：OpenAI](https://openai.com/index/content-partnership-with-financial-times/)｜授权新闻、产品归因与模型改进边界。｜专题：数据**
- **B14｜2024-05-22｜A landmark multi-year global partnership with News Corp｜News Corp / OpenAI｜官方合作公告｜[直接：OpenAI](https://openai.com/index/news-corp-and-openai-sign-landmark-multi-year-global-partnership/)｜当前和历史专业内容授权案例。｜专题：数据**
- **B15｜2024-05-06｜API Partnership with Stack Overflow｜Stack Overflow / OpenAI｜官方合作公告｜[直接：OpenAI](https://openai.com/index/api-partnership-with-stack-overflow/)｜OverflowAPI、开发者模型改进与归因。**JS 验证，需人工重开。**｜专题：数据**
- **B16｜2024-05-16｜OpenAI and Reddit Partnership｜Reddit / OpenAI｜官方合作公告｜[直接：OpenAI](https://openai.com/index/openai-and-reddit-partnership/)｜实时结构化社区数据访问；不等于全量预训练。｜专题：数据**
- **B17｜2024-09-12｜Learning to reason with LLMs｜OpenAI｜官方技术说明｜[直接：OpenAI](https://openai.com/index/learning-to-reason-with-llms/)｜团队自报 train-time RL 与 test-time compute 曲线。**2026-08-24 链接检查返回 200；曲线仍属团队自报。**｜专题：生命周期、审计**
- **B18｜2025-09-29｜Effective context engineering for AI agents｜Anthropic｜官方工程文章｜[直接：Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)｜compaction、结构化笔记、检索和持久记忆的工程经验。｜专题：生命周期、审计**
- **B19｜2019-03-13｜The Bitter Lesson｜Richard Sutton｜个人原始文章｜[直接：作者站](http://incompleteideas.net/IncIdeas/BitterLesson.html)｜利用计算的通用方法、search 与 learning 的思想前史。｜专题：总览、叙事、生命周期**
- **B20｜2024-02-28｜Demis Hassabis — Scaling, superhuman AIs, AlphaZero atop LLMs, AlphaFold｜Dwarkesh Patel / Demis Hassabis｜原始访谈｜[直接：全文/节目](https://www.dwarkesh.com/p/demis-hassabis)；[补充：YouTube](https://www.youtube.com/watch?v=qTogNUV3CAI)｜支持“继续 scaling + 发明”战略判断。｜专题：总览、叙事、生命周期、审计**
- **B21｜2024-03-07｜Lex Fridman Podcast #416 — Yann LeCun｜Lex Fridman / Yann LeCun｜原始访谈｜[直接：带时间戳全文](https://lexfridman.com/yann-lecun-3-transcript/)｜world model、memory、planning 的架构反方。**逐字引用仍需对照音频。**｜专题：总览、生命周期、审计**
- **B22｜2024-07-22｜揭秘 DeepSeek：一个更极致的中国技术理想主义故事｜梁文锋 / 于丽丽 / 暗涌 Waves｜原始访谈｜[直接：36Kr / 暗涌](https://www.36kr.com/p/2872793466982535)；[补充：2024-07-18 镜像](https://wallstreetcn.com/articles/3719982)｜中国实验室对 scaling、效率与原创研究的判断；原微信 URL 已成为删除页。｜专题：总览**
- **B23｜2025-04-10｜The Second Half｜Shunyu Yao｜个人研究议程｜[直接：作者站](https://ysymyth.github.io/The-Second-Half/)｜支持 evaluation、环境、长期记忆可能成为瓶颈。｜专题：总览、生命周期、审计**
- **B24｜2025-04-11｜Welcome to the Era of Experience｜David Silver, Richard Sutton｜研究议程｜[直接：DeepMind 托管 PDF](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf)｜experience scaling 的原始研究议程，不是已成立定律。｜专题：总览、生命周期、社区、审计**
- **B25｜2025-02-12｜How Scaling Laws Drive Smarter, More Powerful AI｜Kari Briski / NVIDIA｜公司博客/产业 taxonomy｜[直接：NVIDIA](https://blogs.nvidia.com/blog/ai-scaling-laws/)｜pretraining/post-training/test-time 三分法；仅作公司框架。｜专题：生命周期、社区、审计**
- **B26｜2024-12-19｜Building Effective “Agents”｜Erik Schluntz, Barry Zhang / Anthropic｜官方工程文章｜[直接：Anthropic](https://www.anthropic.com/engineering/building-effective-agents)｜workflows、tools、ground truth、stopping 与 evals。｜专题：社区**
- **B27｜2025-02-26｜NVIDIA Announces Financial Results for Fourth Quarter and Fiscal 2025｜NVIDIA IR｜公司财报材料｜[直接：NVIDIA IR](https://investor.nvidia.com/news/press-release-details/2025/NVIDIA-Announces-Financial-Results-for-Fourth-Quarter-and-Fiscal-2025/)｜Data Center 与全年收入经营事实。｜专题：基建、审计**
- **B28｜2023-11（产品宣布月）｜H200 GPU｜NVIDIA｜产品规格｜[直接：NVIDIA](https://www.nvidia.com/en-us/data-center/h200/)｜141 GB HBM3e、4.8 TB/s。｜专题：基建、审计**
- **B29｜2025-01-23｜SK hynix Announces 4Q24 Financial Results｜SK hynix IR｜公司财报材料｜[直接：SK hynix](https://news.skhynix.com/en/sk-hynix-announces-4q24-financial-results/)｜FY2024 收入、利润及 Q4 HBM 占 DRAM 收入比例。｜专题：基建、审计**
- **B30｜2024-10-24｜SK hynix Announces 3Q24 Financial Results｜SK hynix IR｜公司财报材料｜[直接：SK hynix](https://news.skhynix.com/en/sk-hynix-announces-3q24-financial-results/)｜HBM 同比/环比增长与 mix。｜专题：基建**
- **B31｜2025-04-24｜SK hynix Announces 1Q25 Financial Results｜SK hynix IR｜公司财报材料｜[直接：SK hynix](https://news.skhynix.com/en/sk-hynix-announces-1q25-financial-results/)｜HBM 供货约提前一年协商及需求预测。｜专题：基建**
- **B32｜2025-01-31｜Samsung Electronics Announces Fourth Quarter and FY 2024 Results｜Samsung IR｜公司财报材料｜[直接：Samsung](https://news.samsung.com/global/samsung-electronics-announces-fourth-quarter-and-fy-2024-results)｜全年经营结果与 HBM/server DDR5 对 Memory 的贡献。｜专题：基建**
- **B33｜2024-04-30｜Samsung Electronics Announces First Quarter 2024 Results｜Samsung IR｜公司财报材料｜[直接：Samsung](https://news.samsung.com/global/samsung-electronics-announces-first-quarter-2024-results)｜HBM、DDR5、封装投资与 HBM3E 量产。｜专题：基建**
- **B34｜2024-07-31｜Samsung Electronics Announces Results for Second Quarter of 2024｜Samsung｜公司财报材料｜[直接：Samsung Global Newsroom](https://news.samsung.com/global/samsung-electronics-announces-results-for-second-quarter-of-2024)｜AI 产品产能配置与普通先进 DRAM bit supply。｜专题：基建**
- **B35｜2025-04-30｜Samsung Electronics Announces First Quarter 2025 Results｜Samsung IR｜公司财报材料｜[直接：Samsung](https://news.samsung.com/global/samsung-electronics-announces-first-quarter-2025-results)｜HBM 销售下降的出口管制与产品延迟负向证据。｜专题：基建**
- **B36｜2024-09-25｜Micron Reports Fourth Quarter and Full Year Fiscal 2024 Results｜Micron IR｜公司财报材料｜[直接：Micron IR](https://investors.micron.com/news/press-release/2024/Micron-Technology-Inc--Reports-Results-for-the-Fourth-Quarter-and-Full-Year-of-Fiscal-2024-09-25-2024/default.aspx)｜FY2024 收入与 AI data-center/HBM ramp。｜专题：基建**
- **B37｜2024-12-18｜Micron Fiscal Q1 2025 Prepared Remarks｜Micron IR｜公司财报材料｜[直接：Micron 官方 PDF](https://micron.gcs-web.com/static-files/21b50828-dd30-429f-9502-b1ebc452c6e3)；[官方季度材料归档](https://micron.gcs-web.com/quarterly-results)｜“sold out”、定价及 HBM 收入预测均为当时管理层表述。｜专题：基建**
- **B38｜2025-03-20｜Micron Fiscal Q2 2025 Prepared Remarks｜Micron IR｜公司财报材料｜[直接：Micron 官方 CDN PDF](https://s25.q4cdn.com/621799436/files/doc_financials/2025/q2/Micron_FY25_Q2_Prepared_Remarks_2-1.pdf)｜HBM3E 同 bit output 约 3× DDR5 硅耗。｜专题：基建、审计**
- **B39｜2024-07-30｜Microsoft FY2024 Q4 Earnings Conference Call｜Microsoft IR｜公司财报/电话会｜[直接：Microsoft IR](https://www.microsoft.com/en-us/investor/events/fy-2024/earnings-fy-2024-q4)｜capex、云/AI 配置与容量约束。｜专题：基建、审计**
- **B40｜2024-10-29｜Alphabet 2024 Q3 Earnings Call｜Alphabet IR｜公司财报/电话会｜[直接：Alphabet earnings-call page](https://abc.xyz/2024-q3-earnings-call/)｜技术基础设施中服务器与数据中心/网络构成。｜专题：基建、审计**
- **B41｜2025-01-29｜Meta Reports Fourth Quarter and Full Year 2024 Results｜Meta IR｜公司财报材料｜[直接：Meta IR](https://investor.atmeta.com/investor-news/press-release-details/2025/Meta-Reports-Fourth-Quarter-and-Full-Year-2024-Results/)｜2024 capex 与 2025 AI/core business 投资口径。｜专题：基建、审计**
- **B42｜2025-02-06｜Amazon Q4 2024 Earnings Conference Call｜Amazon IR｜公司电话会｜[直接：Amazon IR](https://ir.aboutamazon.com/events/event-details/2025/Q4-2024-Amazoncom-Inc-Earnings-Conference-Call/default.aspx)；[补充：现有逐字稿副本](https://thetranscript.net/transcript/7502/amazon.com-q4-2024-earnings-report)｜AWS/AI 基础设施采购与需求信号。**官方页为 webcast/材料，逐字引用需人工对照音频。**｜专题：基建、审计**
- **B43｜2018-05-16｜AI and Compute｜OpenAI｜公司研究博客｜[直接：OpenAI](https://openai.com/index/ai-and-compute/)｜2012–2018 大型训练运行算力增长的历史背景。｜专题：KC**
- **B44｜2022-04-12｜An empirical analysis of compute-optimal large language model training｜Google DeepMind｜官方研究博客｜[直接：DeepMind](https://deepmind.google/blog/an-empirical-analysis-of-compute-optimal-large-language-model-training/)｜交叉核对 Chinchilla 团队对结果和推理成本的表述。｜专题：KC**
- **B45｜2022-03-02（视频 2022-03-04）｜Scaling Laws and Their Implications for Coding AI｜Jared Kaplan / Harvard CMSA｜原作者学术讲座｜[直接：YouTube](https://www.youtube.com/watch?v=Suhp3OLASSo)｜原作者解释 scaling 作为规划工具及代码/RL 外延。**自动字幕需人工复听。**｜专题：叙事、审计**
- **B46｜2024-07-23｜Llama 2, 3 & 4: Synthetic Data, RLHF, Agents on the Path to Open Source AGI｜Latent Space / Thomas Scialom｜原始访谈/播客｜[直接：全文逐字稿](https://www.latent.space/p/llama-3)；[补充：YouTube](https://www.youtube.com/watch?v=uLR8nSrhk_w)｜“Chinchilla trap”、部署经济与后训练工程叙事。｜专题：叙事**
- **B47｜2024-10-02｜Teaching LLMs to Reason Better by Thinking Longer｜Sequoia Training Data / Noam Brown, Ilge Akkaya, Hunter Lightman｜原始团队访谈｜[直接：全文逐字稿](https://sequoiacap.com/podcast/training-data-noam-brown/)；[补充：YouTube](https://www.youtube.com/watch?v=jPluSXJpdrA)｜“首都 vs Sudoku”、任务边界与 test-time search。**逐字引用需复听。**｜专题：叙事、生命周期、审计**
- **B48｜2023（精确日未在索引材料中核验）｜The bot Cicero can collaborate, scheme and build trust with humans｜No Priors / Noam Brown｜原始访谈｜[直接：可检索逐字稿](https://podscripts.co/podcasts/no-priors-artificial-intelligence-technology-startups/the-bot-cicero-can-collaborate-scheme-and-build-trust-with-humans-what-does-this-mean-for-the-next-frontier-of-ai-with-noam-brown-research-scientist-at-meta)｜核对“100,000×”来自扑克实时搜索语境。**当前仅稳定找到第三方逐字稿，需人工找回节目官方页/音频。**｜专题：生命周期、审计**
- **B49｜2021｜The Scaling Hypothesis｜Gwern Branwen｜个人长文｜[直接：作者站](https://gwern.net/scaling-hypothesis)｜区分 loss scaling 与通向 AGI 的 scaling hypothesis。｜专题：社区**
- **B50｜2024-11-10｜Confirmed: LLMs have indeed reached a point of diminishing returns｜Gary Marcus｜个人评论文章｜[直接：Substack](https://garymarcus.substack.com/p/confirmed-llms-have-indeed-reached)｜代表 pretraining 放缓/递减叙事；标题强于可公开核验证据。｜专题：社区**

## C — 独立综合、教学、媒体与行业研究（24）

- **C01｜2026-06-24｜Scaling Laws, Carefully｜Lilian Weng｜技术综述｜[直接：作者站](https://lilianweng.github.io/posts/2026-06-24-scaling-laws/)｜拟合区间、参数计数、tokenizer、数据 mix 与优化器 caveat。｜专题：总览、KC、审计**
- **C02｜2024-11-20｜Large Language Models explained briefly｜Grant Sanderson / 3Blue1Brown｜科普视频/图文课｜[直接：YouTube](https://www.youtube.com/watch?v=LPZh9BOjkQs)；[补充：Bilibili 官方双语版](https://www.bilibili.com/video/BV1xmA2eMEFF/)；[补充：图文课](https://www.3blue1brown.com/lessons/mini-llm/)｜约 7:58 的无公式视觉解释与叙事节奏样板。｜专题：叙事**
- **C03｜2023-06｜Scaling laws and compute-optimal models｜DeepLearning.AI × AWS；Antje Barth et al.｜教学视频/课程｜[直接：课程逐字稿](https://learn.deeplearning.ai/courses/generative-ai-with-llms/lesson/v5xa6/scaling-laws-and-compute-optimal-models)；[课程页](https://www.deeplearning.ai/courses/generative-ai-with-llms)｜短篇预算框架与 Chinchilla 教学。｜专题：叙事**
- **C04｜2024-08-20｜Can AI scaling continue through 2030?｜Jaime Sevilla et al., Epoch AI｜独立研究报告｜[直接：Epoch AI](https://epoch.ai/publications/can-ai-scaling-continue-through-2030)｜电力、芯片、数据和延迟四瓶颈地图。｜专题：叙事**
- **C05｜2024-03-04｜Large language models can do jaw-dropping things. But nobody knows exactly why.｜Will Douglas Heaven / MIT Technology Review｜媒体长文｜[直接：MIT Technology Review](https://www.technologyreview.com/2024/03/04/1089403/large-language-models-amazing-but-nobody-knows-why/)｜经验可预测性与机制理解之间的边界。｜专题：叙事、审计**
- **C06｜2025-04-29｜AI’s Version of Moore’s Law?｜Computerphile / Sydney von Arx (METR)｜研究科普视频｜[直接：YouTube](https://www.youtube.com/watch?v=evSFeqTZdqs)；[补充：METR 原研究](https://metr.org/blog/2025-03-19-measuring-ai-ability-to-complete-long-tasks/)｜展示趋势、稳健性检查与外推边界。**字幕需人工复听。**｜专题：叙事**
- **C07｜2023-08-16｜The Mathematics of Training LLMs｜Latent Space / Quentin Anthony｜技术播客/逐字稿｜[直接：Latent Space](https://www.latent.space/p/transformers-math)｜FLOPs、吞吐、GPU 时间、显存和通信成本。｜专题：叙事**
- **C08｜2024-05-28｜Training compute of frontier AI models grows by 4–5× per year｜Jaime Sevilla, Edu Roldán / Epoch AI｜数据研究｜[直接：Epoch AI](https://epoch.ai/publications/training-compute-of-frontier-ai-models-grows-by-4-5x-per-year)｜frontier training compute 历史增长基线。｜专题：叙事**
- **C09｜2023-07-28（Ars 版 07-31）｜A jargon-free explanation of how AI large language models work｜Timothy B. Lee, Sean Trott｜科普文章｜[直接：作者副本](https://seantrott.substack.com/p/large-language-models-explained)；[补充：Ars Technica](https://arstechnica.com/science/2023/07/a-jargon-free-explanation-of-how-ai-large-language-models-work/)｜无公式解释 token、表征、训练与 scaling。｜专题：叙事**
- **C10｜2024-04-29/05-01｜Stanford CS336: Scaling Laws (Lectures 9–10)｜Tatsunori Hashimoto / Stanford｜大学课程｜[直接：课程页](https://cs336.stanford.edu/spring2024/)；[讲义仓库](https://github.com/stanford-cs336/spring2024-lectures)｜拟合流程、Kaplan/Chinchilla 与外推陷阱。｜专题：叙事**
- **C11｜2024（精确日未知）｜MIT 6.7960 Lecture 20: Scaling Laws｜MIT OpenCourseWare｜大学课件｜[直接：MIT OCW PDF](https://ocw.mit.edu/courses/6-7960-deep-learning-fall-2024/mit6_7960_f24_lec20.pdf)｜Kaplan、Chinchilla 三种分析与固定预算比较。｜专题：叙事**
- **C12｜2024-05-09｜Has Generative AI Already Peaked?｜Computerphile / Rob Miles｜科普视频｜[直接：YouTube](https://www.youtube.com/watch?v=dDUC-LqVrPU)；[补充：逐字稿镜像](https://rosetta.to/u/computerphile/has-generative-ai-already-peaked-computerphile)｜递减收益和经济平台期的反方视觉叙事。**自动字幕/镜像需人工复听。**｜专题：叙事**
- **C13｜首次日期未知｜Scaling Laws Literature Review｜Epoch AI｜研究综述｜[直接：Epoch AI](https://epoch.ai/publications/scaling-laws-literature-review)｜仅作历史定位辅助，不替代原论文。｜专题：KC**
- **C14｜2022（原文年份）｜Will we run out of ML data? Evidence from projecting dataset size trends｜Epoch AI｜研究文章｜[直接：Epoch](https://epoch.ai/publications/will-we-run-out-of-ml-data-evidence-from-projecting-dataset)｜早期 data-wall 预测及与 2024 版本的方法变化。｜专题：社区**
- **C15｜2025-06-24｜Anthropic wins key US ruling on AI training in authors’ copyright lawsuit｜Blake Brittain / Reuters｜媒体报道｜[直接：Reuters](https://www.reuters.com/legal/litigation/anthropic-wins-key-ruling-ai-authors-copyright-lawsuit-2025-06-24/)｜独立概括 Bartz 简易判决程序状态。**Reuters 可能返回 401。**｜专题：数据、审计**
- **C16｜2024-03-18｜2024 HBM Supply Bit Growth Estimated to Reach 260%, Making Up 14% of DRAM Industry｜TrendForce｜行业研究｜[直接：TrendForce](https://www.trendforce.com/presscenter/news/20240318-12081.html)｜HBM die、yield、周期与产能估计。｜专题：基建、审计**
- **C17｜2024-05-20｜HBM3e Production Surge Expected to Make Up 35% of Advanced Process Wafer Input｜TrendForce｜行业研究｜[直接：TrendForce](https://www.trendforce.com/presscenter/news/20240520-12143.html)｜先进制程 wafer input 竞争估计。｜专题：基建**
- **C18｜2024-12-23；12-31 更新｜Markets in 2024: Wall Street’s high-octane rally keeps investors captive to the US｜Reuters｜媒体/市场报道｜[直接：Reuters](https://www.reuters.com/markets/global-markets-year-end-graphic-2024-12-23/)｜12-31 更新稿支持 NVIDIA 2024 `+178%`；12-23 初稿为 172%。**Reuters canonical 可能返回 401；行情仍需统一数据商重算。**｜专题：基建**
- **C19｜2025-01-08｜Samsung’s preliminary Q4 profit falls far short of estimates as chip issues drag｜Reuters｜媒体/市场报道｜[直接：Reuters](https://www.reuters.com/business/media-telecom/samsung-fourth-quarter-operating-profit-outlook-misses-estimates-by-large-margin-2025-01-07/)｜Samsung/SK hynix 2024 股价分化与执行背景。**Reuters canonical 可能返回 401。**｜专题：基建、审计**
- **C20｜动态查询；2024 数据｜MU stock returns 2024｜StatMuse Money｜市场数据查询页｜[直接：StatMuse](https://www.statmuse.com/money/ask/mu-stock-returns-2024)｜Micron 2024 约 +0.6% 的低等级交叉值。**动态行情口径，发布前必须用授权统一数据源替换。**｜专题：基建、审计**
- **C21｜2026-07-21｜Court Grants Final Approval of $1.5 Billion Anthropic Copyright Settlement｜Authors Guild｜利益相关组织说明｜[直接：Authors Guild](https://authorsguild.org/news/court-grants-final-approval-anthropic-copyright-settlement/)｜交叉核对 final approval 与分配说明；法律结论以法院命令为准。｜专题：审计**
- **C22｜2026-07-21｜Bartz v. Anthropic Settlement Receives Final Approval｜Authors Alliance｜法律/政策说明｜[直接：Authors Alliance](https://www.authorsalliance.org/2026/07/21/bartz-v-anthropic-settlement-receives-final-approval/)｜交叉核对 final approval、费用和生效条件；法律结论以法院命令为准。｜专题：审计**
- **C23｜2023-12-27｜Will scaling work?｜Dwarkesh Patel｜观点综合文章｜[直接：原文](https://www.dwarkesh.com/p/will-scaling-work)｜综合讨论数据、loss、generality 与经济回报。｜专题：社区**
- **C24｜2024-07-03｜New paper: AI Agents That Matter｜AI Snake Oil / Sayash Kapoor et al.｜研究解读文章｜[直接：Normal Technology](https://www.normaltech.ai/p/new-paper-ai-agents-that-matter)｜论文的成本、可复现性与 agent benchmark 解读。｜专题：社区**

## D — VC、卖方与投资论述（4）

- **D01｜2024-10-09｜Generative AI’s Act o1｜Sonya Huang, Pat Grady / Sequoia Capital｜VC 产业论述｜[直接：Sequoia](https://sequoiacap.com/article/generative-ais-act-o1/)｜“reasoning layer / inference cloud”产业叙事；不作技术定律。｜专题：叙事**
- **D02｜2024-12-11｜Scaling Laws — O1 Pro Architecture, Reasoning Training Infrastructure, Orion and Claude 3.5 Opus “Failures”｜Dylan Patel et al. / SemiAnalysis｜付费产业分析｜[直接：SemiAnalysis](https://newsletter.semianalysis.com/p/scaling-laws-o1-pro-architecture-reasoning-training-infrastructure-orion-and-claude-3-5-opus-failures)｜pretraining、RL、synthetic data 与 inference infrastructure 产业叙事。**付费墙；不可从摘要恢复内部架构断言。**｜专题：社区、审计**
- **D03｜2024-06-20｜AI’s $600B Question｜David Cahn / Sequoia Capital｜VC 分析｜[直接：Sequoia](https://sequoiacap.com/article/ais-600b-question)｜把技术 scaling 转成 capex 回报与终端收入问题。｜专题：社区**
- **D04｜2025-08-12｜The State of AI 2025｜Kent Bennett, Talia Goldberg, Janelle Teng et al. / Bessemer Venture Partners｜VC 年度报告｜[直接：Bessemer](https://www.bvp.com/atlas/the-state-of-ai-2025)；[报告 PDF](https://www.bvp.com/assets/uploads/2025/08/Final_PDF_State_of_AI_2025_slides_Bessemer_Venture_Partners.pdf)｜agents、adaptive reasoning、memory 与 compound systems 投资 thesis。｜专题：社区**

## E — Hacker News 讨论（8）

HN points/comments 都是 2026-08-24 查询快照；评论者身份通常不可核验。每条以 HN permalink 为直接链接，原文仅作关联。

- **E01｜2022-05-30（原文 2021）｜HN: The Scaling Hypothesis｜Hacker News 社区｜HN 讨论｜[直接：HN 31564033](https://news.ycombinator.com/item?id=31564033)；[代表评论 31564974](https://news.ycombinator.com/item?id=31564974)；[关联原文](https://gwern.net/scaling-hypothesis)｜展示社区混用 scaling law 与 AGI hypothesis。｜专题：社区**
- **E02｜2023-12-27｜HN: Will scaling work?｜Hacker News 社区｜HN 讨论｜[直接：HN 38781484](https://news.ycombinator.com/item?id=38781484)；[代表评论 38782337](https://news.ycombinator.com/item?id=38782337)；[关联原文](https://www.dwarkesh.com/p/will-scaling-work)｜展示数据、能力与经济影响的公开辩论。｜专题：社区**
- **E03｜2024-11-10｜HN: LLMs have reached a point of diminishing returns｜Hacker News 社区｜HN 讨论｜[直接：HN 42097774](https://news.ycombinator.com/item?id=42097774)；[评论 42097898](https://news.ycombinator.com/item?id=42097898)；[评论 42097975](https://news.ycombinator.com/item?id=42097975)；[关联原文](https://garymarcus.substack.com/p/confirmed-llms-have-indeed-reached)｜区分递减收益、能力放缓与 loss 撞墙。｜专题：社区**
- **E04｜2023-04-23（原文 2022）｜HN: Will we run out of ML data?｜Hacker News 社区｜HN 讨论｜[直接：HN 35667764](https://news.ycombinator.com/item?id=35667764)；[评论 35672198](https://news.ycombinator.com/item?id=35672198)；[评论 35676073](https://news.ycombinator.com/item?id=35676073)；[关联原文](https://epoch.ai/publications/will-we-run-out-of-ml-data-evidence-from-projecting-dataset)｜展示质量、版权、模态与生成污染变量。｜专题：社区**
- **E05｜2024-07-24｜HN: AI models collapse when trained on recursively generated data｜Hacker News 社区｜HN 讨论｜[直接：HN 41058194](https://news.ycombinator.com/item?id=41058194)；[代表评论 41059652](https://news.ycombinator.com/item?id=41059652)；[关联论文](https://www.nature.com/articles/s41586-024-07566-y)｜区分递归模仿与有 verifier 的合成数据。｜专题：社区**
- **E06｜2024-12-20｜HN: Building Effective “Agents”｜Hacker News 社区｜HN 讨论｜[直接：HN 42470541](https://news.ycombinator.com/item?id=42470541)；[评论 42475700](https://news.ycombinator.com/item?id=42475700)；[评论 42478651](https://news.ycombinator.com/item?id=42478651)；[关联原文](https://www.anthropic.com/engineering/building-effective-agents)｜展示 workflow/agent 工程接受与质疑。｜专题：社区**
- **E07｜2024-07-03｜HN: AI Agents That Matter｜Hacker News 社区｜HN 讨论｜[直接：HN 40868448](https://news.ycombinator.com/item?id=40868448)；[评论 40868893](https://news.ycombinator.com/item?id=40868893)；[评论 40869099](https://news.ycombinator.com/item?id=40869099)；[关联解读](https://www.normaltech.ai/p/new-paper-ai-agents-that-matter)｜展示成本、归因及工程前史争论。｜专题：社区**
- **E08｜2025-04-20｜HN: Welcome to the Era of Experience｜Hacker News 社区｜HN 讨论｜[直接：HN 43740858](https://news.ycombinator.com/item?id=43740858)；[评论 43745354](https://news.ycombinator.com/item?id=43745354)；[评论 43746456](https://news.ycombinator.com/item?id=43746456)；[关联 PDF](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf)｜展示 experience 议程与持续学习质疑。｜专题：社区**

## 无稳定链接 / 需人工复核

以下 **19 条材料（15 类问题）**都已有至少一个直接链接；问题是访问、版本、动态性或逐字引用可靠性，不是完全缺链。

1. **A36 Bartz final approval**：Justia 托管的 Dkt. 680 法院 PDF 可访问；仍需通过 PACER/第九巡回 docket 核验 2026-08-24 时点的上诉、生效与分配状态。
2. **B11 OpenAI foundation-model data 说明**：持续更新且无稳定首发日期；引用时记录访问日或使用网页存档。
3. **B12 OpenAI Data Partnerships**：2026-08-24 链接检查返回 200；正式引用仍应把征集意图与已采用数据分开。
4. **B15 Stack Overflow partnership**：原页可能触发 JavaScript 验证。
5. **B17 OpenAI o1 技术说明**：2026-08-24 链接检查返回 200；曲线属于团队自报，不要用搜索摘要替代原页。
6. **B21 Yann LeCun 访谈**：网页 transcript 可用，逐字引语仍需对照音频。
7. **B22 梁文锋访谈**：原微信链接已成为删除页；现以 36Kr/暗涌 2024-07-22 页面为主，并保留 2024-07-18 镜像说明日期差异。
8. **B42 Amazon Q4 2024 call**：已把直接链接修复为 Amazon 官方 IR event；逐字稿仍是二手托管，引用需对照官方 webcast。
9. **B45 Jared Kaplan 讲座**：YouTube 自动字幕需人工复听。
10. **B47 Noam Brown / Sequoia 视频**：逐字稿可读，但“首都 vs Sudoku”逐字引用需复听。
11. **B48 No Priors / Noam Brown**：目前稳定直接链接是第三方逐字稿；需找回官方节目页/音频，并核验原始发布日期。
12. **C06、C12 Computerphile 视频**：自动字幕/逐字稿镜像可能误识别人名和术语。
13. **C15、C18、C19 Reuters**：页面可能返回 401；法律事实回法院命令，市场事实需另用授权数据源重算。
14. **C20 StatMuse / 所有实时行情**：动态查询且回报口径不统一；只能作交叉值，不能作为最终图表数据。
15. **D02 SemiAnalysis**：付费墙；只保留公开可核验的作者、日期和高层产业 thesis，不恢复付费正文细节。

完全无链接的收录材料：**0**。
