# References

Reference notes for **Scaling Laws, in a Nutshell**. The goal is a defensible presentation narrative, not an exhaustive catalog of public comments.

Dates below are the original publication date or arXiv v1 date. Technical claims favor primary papers and reports; interviews and essays are kept only when they express a distinctive research position.

## Evidence levels

Levels describe what a source is suitable for; they are not a simple truth ranking.

- **A — Primary evidence:** Papers, court orders, regulatory filings, and government reports. Best for experimental or legal claims; one paper still does not establish a universal law.
- **B — First-party evidence:** Original interviews, company technical reports, model cards, blogs, earnings materials, and product specifications. Best for team-reported results, company strategy, and operating facts.
- **C — Independent synthesis:** Reputable reporting, methodological explainers, and professional research. Best for context and cross-checking.
- **D — Industry thesis:** VC, sell-side, and investment analysis. Best for showing market narratives and capital-allocation beliefs.
- **E — Community reaction:** Hacker News and similar discussion. Best for showing how engineers interpret or dispute a claim, never for establishing the claim itself.

## Research dossiers

- [Curated reading list](READING_LIST.md)
- [All sources: 123-item deduplicated link index](ALL_SOURCES.md)
- [Data scaling: Anthropic and OpenAI](data-scaling.md)
- [Explainers and storytelling patterns](explainers-and-storytelling.md)
- [Kaplan and Chinchilla impact review](kaplan-and-chinchilla.md)
- [Lifecycle scaling](lifecycle-scaling.md)
- [Community and industry viewpoints](community-and-industry.md)
- [AI infrastructure and HBM](ai-infrastructure-and-hbm.md)
- [Cross-topic evidence audit](EVIDENCE_AUDIT.md)
- [Full link and citation-target audit](LINK_CHECK.md)
- [Agent execution record](RESEARCH_RUNS.md)

## Presentation thesis

> Scaling laws remain conditional tools for forecasting aggregate loss and planning training. The frontier is now testing additional resource axes—data, post-training RL, test-time compute, retrieval, environments, and experience—but their maturity, economics, and relevance to general intelligence differ.

This is more accurate than either “bigger models solve everything” or “scaling is over.”

## Consensus map

This is a qualitative synthesis of representative evidence, not a field-wide survey.

| Classification | Presentation-safe wording | Evidence boundary |
| --- | --- | --- |
| **Broad empirical agreement** | Conditional loss/compute scaling is useful within a stable training regime. | It does not make downstream capabilities, out-of-distribution behavior, or economic value equally predictable. |
| **Broad agreement** | Parameter count alone is an inadequate definition of scale. | Data, activated compute, architecture, optimization, retrieval, and training duration can change the result. |
| **Strong strategic momentum—not consensus** | Major programs are investing in post-training RL, test-time compute, agents, and generated experience. | Investment and benchmark gains do not establish universal scaling laws for these methods. |
| **Open technical disagreement** | It is unknown whether the newer axes scale reliably, economically, and safely. | Reward-model validity, task difficulty, verifier quality, environment design, and inference cost all matter. |
| **Open architectural disagreement** | Autoregressive Transformers may remain central, but retrieval, world models, and hybrid systems are active alternatives. | There is no consensus that the current architecture is either sufficient for AGI or near exhaustion. |
| **Broad evaluation concern** | A benchmark score alone does not establish general intelligence or real-world utility. | The field still disagrees about valid replacements and external validity. |

## Foundations

### 2017–2019 — Predictable learning curves before Kaplan [A]

- [Hestness et al., Deep Learning Scaling is Predictable, Empirically](https://arxiv.org/abs/1712.00409)
- [Rosenfeld et al., A Constructive Prediction of the Generalization Error Across Scales](https://arxiv.org/abs/1909.12673)
- These establish that Kaplan was not the origin of neural scaling laws. Kaplan's importance is the systematic treatment of Transformer language-model parameters, data, compute, and training planning.

### 2020-01-23 — Kaplan et al.: LM scaling as a planning tool [A]

- [Scaling Laws for Neural Language Models — primary paper](https://arxiv.org/abs/2001.08361)
- Established smooth relationships among language-model loss, model size, data, and training compute.
- Durable contribution: conditional loss extrapolation and a practical training-planning framework.
- Historical caveat: its specific compute-allocation prescription was revised by Chinchilla and later replication work.

### 2022-03-29 — Hoffmann et al. / Chinchilla: allocation correction [A]

- [Training Compute-Optimal Large Language Models — primary paper](https://arxiv.org/abs/2203.15556)
- Under approximately equal training FLOPs, the 70B-parameter Chinchilla trained on about 1.4T tokens and outperformed the 280B Gopher within the paper's evaluations.
- The directional result—that parameters and training tokens should grow together in this fixed-training-compute problem—is stronger than any exact coefficient.
- The familiar “20 tokens per parameter” is a regime-specific heuristic, not a universal constant or deployment optimum.

### 2023–2024 — Training-optimal is not deployment-optimal [B]

- [LLaMA: Open and Efficient Foundation Language Models](https://arxiv.org/abs/2302.13971)
- [The Llama 3 Herd of Models](https://arxiv.org/abs/2407.21783)
- Models serving many requests may be deliberately trained beyond a training-compute optimum to reduce long-run inference cost. The objective function changes with deployment economics.

## Methodological explainers

### 2026-06-24 — Lilian Weng: fitting laws carefully [C]

- [Scaling Laws, Carefully — technical explainer](https://lilianweng.github.io/posts/2026-06-24-scaling-laws/)
- Explains why parameter counting, fit region, tokenizer, data mix, optimizer, and learning-rate schedule can materially change an extrapolation.
- Useful methodological synthesis; it is not primary evidence for a new scaling law.

## Eight core sources selected from the research audit

These eight sources were selected from 20 candidates because they cover different claims rather than repeating the same pro- or anti-scaling position.

### 2021-12-08 — RETRO: retrieval as an alternative scaling axis [A]

> “With a 2 trillion token database, our Retrieval-Enhanced Transformer (Retro) obtains comparable performance to GPT-3 and Jurassic-1 on the Pile, despite using 25× fewer parameters.”

- **Team at publication:** Sebastian Borgeaud et al., Google DeepMind.
- **Axes:** data, parameters, retrieval architecture, test-time compute.
- **Use in the talk:** Evidence that capability need not be stored only in model parameters.
- [Improving language models by retrieving from trillions of tokens — primary paper](https://arxiv.org/abs/2112.04426)

### 2022-02-15 — Anthropic: predictable loss, unpredictable behavior [A]

> “These generative models have a paradoxical combination of predictable loss on a broad training distribution (as embodied in their ‘scaling laws’), and unpredictable specific capabilities, inputs, and outputs.”

- **Team at publication:** Deep Ganguli et al., Anthropic research and infrastructure.
- **Axes:** parameters, data, pretraining compute, evaluation.
- **Use in the talk:** The cleanest primary-source boundary between forecasting aggregate loss and forecasting specific behavior.
- [Predictability and Surprise in Large Generative Models — primary paper](https://arxiv.org/abs/2202.07785)

### 2022-10-19 — OpenAI: scaling a proxy reward can backfire [A]

> “Because the reward model is an imperfect proxy, optimizing its value too much can hinder ground truth performance, in accordance with Goodhart’s law.”

- **Team at publication:** Leo Gao, John Schulman, and Jacob Hilton, OpenAI.
- **Axes:** post-training/RL, evaluation.
- **Use in the talk:** A direct technical reason not to call RL scaling a settled law.
- [Scaling Laws for Reward Model Overoptimization — primary paper](https://arxiv.org/abs/2210.10760v1)

### 2024-01-05 — DeepSeek: company evidence on classical scaling [B]

> “The scaling laws described in previous literature present varying conclusions … We delve into the study of scaling laws and present our distinctive findings.”

- **Team at publication:** DeepSeek-AI research team.
- **Axes:** parameters, data, pretraining compute.
- **Use in the talk:** Shows that scaling laws are calibrated to a team's architecture, data, and compute conditions rather than copied as universal constants.
- [DeepSeek LLM: Scaling Open-Source Language Models with Longtermism — primary technical report](https://arxiv.org/abs/2401.02954v1)

### 2024-06-27 — Independent Chinchilla replication [A]

> “With these factors corrected, we obtain excellent agreement with the Hoffmann et al. (i.e., ‘Chinchilla’) scaling law.”

- **Team at publication:** Tomer Porian et al., Tel Aviv University, University of Washington, Jülich, and LAION.
- **Axes:** parameters, data, pretraining compute.
- **Use in the talk:** Independent evidence for the limited but real consensus around compute-optimal pretraining.
- [Resolving Discrepancies in Compute-Optimal Scaling of Language Models — primary paper](https://arxiv.org/abs/2406.19146)

### 2024-07-01 — Princeton: agent gains can be misattributed [A]

> “SOTA agents are needlessly complex and costly, and the community has reached mistaken conclusions about the sources of accuracy gains.”

- **Team at publication:** Sayash Kapoor et al., Princeton researchers.
- **Axes:** test-time compute, agent scaffolding, evaluation.
- **Use in the talk:** More inference and orchestration can improve a score without proving that the underlying model became more generally capable.
- [AI Agents That Matter — primary paper](https://arxiv.org/abs/2407.01502v1)

### 2024-08-06 — Test-time compute works in specific regimes [A]

> “The effectiveness of different approaches to scaling test-time compute critically varies depending on the difficulty of the prompt.”

- **Team at publication:** Charlie Snell et al., UC Berkeley and Google DeepMind.
- **Axes:** test-time compute, model size, evaluation.
- **Use in the talk:** Test-time compute can outperform a much larger model, but only with suitable problem difficulty, allocation strategy, and verifier quality.
- [Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters — primary paper](https://arxiv.org/abs/2408.03314v1)

### 2025-01-22 — Kimi: RL as a strategic scaling bet [B]

> “Scaling reinforcement learning (RL) unlocks a new axis for the continued improvement of artificial intelligence … Long context scaling and improved policy optimization methods are key ingredients of our approach.”

- **Team at publication:** Moonshot AI/Kimi research team.
- **Axes:** post-training/RL, long context, test-time compute, environments.
- **Use in the talk:** Strong Chinese primary evidence for strategic momentum toward RL scaling—not proof of a universal law.
- **Caveat:** Comparisons with OpenAI o1 are the authors' benchmark claims, not independent evaluation.
- [Kimi k1.5: Scaling Reinforcement Learning with LLMs — primary technical report](https://arxiv.org/abs/2501.12599)

## Data scaling and legal context

Company behavior shows that data has become a supply chain—covering acquisition, licensing, filtering, deduplication, weighting, human production, and synthetic generation. It does not by itself quantify how much capability any additional dataset creates.

### 2025-06-23 — Bartz v. Anthropic fair-use order [A]

- [Order on Fair Use — Dkt. 231 court PDF](https://cases.justia.com/federal/district-courts/california/candce/3%3A2024cv05417/434709/231/0.pdf)
- [U.S. Copyright Office Fair Use Index case summary](https://www.copyright.gov/fair-use/summaries/Bartz-v-Anthropic-PBC-787-F-Supp-3d-1007-ND-Cal-2025.pdf) — a two-page government summary, not the court order.
- Court records document Anthropic's acquisition of Books3/LibGen/PiLiMi copies and its later purchase and destructive scanning of millions of paper books.
- The order separated uses: particular training copies and one-to-one digitization of lawfully purchased books were treated differently from acquiring and retaining a central library of pirated copies.
- This supports the factual data-supply-chain story, not a general claim that all AI training is lawful or that every acquired book entered every Claude model.

### 2026-07-20 — Bartz settlement final approval [A]

- [Final approval order and judgment — Dkt. 680 court PDF](https://cases.justia.com/federal/district-courts/california/candce/4%3A2024cv05417/434709/680/0.pdf)
- The court approved a $1.5 billion class settlement for defined past acquisition and copying claims.
- A settlement does not establish a universal copyright precedent; any appeal, effective-date, or distribution status after the order requires docket verification.

For OpenAI's public-web pipeline, licensed archives, platform/API partnerships, human feedback, synthetic data, and source-specific caveats, see [data-scaling.md](data-scaling.md).

## Six dated viewpoints and research agendas worth quoting

| Date | Speaker and position | Concise interpretation | Primary source |
| --- | --- | --- | --- |
| 2019-03-13 | **Richard Sutton [B]:** general methods that leverage computation ultimately win. | Intellectual precursor to scaling, not an LLM power law. | [The Bitter Lesson](http://incompleteideas.net/IncIdeas/BitterLesson.html) |
| 2024-02-28 | **Demis Hassabis [B]:** push scaling while doubling down on invention. | Strategic judgment: pursue scale and new algorithms together. | [Dwarkesh interview](https://www.dwarkesh.com/p/demis-hassabis) |
| 2024-03-07 | **Yann LeCun [B]:** autoregressive LLMs lack essential components for human-level intelligence. | Architecture-and-objective critique, not a claim that benchmark improvement stops. | [Lex Fridman transcript](https://lexfridman.com/yann-lecun-3-transcript/) |
| 2024-07-22 | **Liang Wenfeng (梁文锋) [B]:** “我们偏乐观，整个行业看起来都符合预期。” | Scaling remains useful, while architecture, data efficiency, and original research determine progress per unit compute. | [36Kr / Waves interview](https://www.36kr.com/p/2872793466982535) · [2024-07-18 mirror](https://wallstreetcn.com/articles/3719982) |
| 2025-04-10 | **Shunyu Yao (姚顺雨) [B]:** “evaluation becomes more important than training.” | A personal research agenda: task definition, environments, and real utility become bottlenecks. | [The Second Half](https://ysymyth.github.io/The-Second-Half/) |
| 2025-04-11 | **David Silver and Richard Sutton [B]:** experience may dwarf human training data. | A research agenda for agent experience, not an established empirical law. | [Welcome to the Era of Experience — stable PDF](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf) |

## Context flags for presentation slides

- **Loss is not capability:** predictable in-distribution loss does not make a particular skill, failure, or economic payoff equally predictable.
- **“Three scaling laws”:** NVIDIA's pretraining/post-training/test-time framing (Kari Briski, 2025-02-12) is a company taxonomy, not proof of three shared mathematical laws.
- **Noam Brown's “100,000×”:** the comparison came from a poker experiment; it is not a general exchange rate between pretraining and reasoning tokens.
- **“Pure RL created DeepSeek-R1”:** pure RL describes **R1-Zero**. DeepSeek-R1 also uses cold-start data and multi-stage training.
- **Test-time compute:** gains depend on task difficulty, verifier quality, and compute allocation; more thinking does not always help.
- **Company technical reports:** they are primary evidence for a company's strategy and measurements, but self-reported benchmark comparisons do not establish field consensus.

## Access and verification limits

- Recheck YouTube auto-transcripts against audio before using quotation marks or timestamps.
- Reuters links may return 401; use court orders, filings, and company materials for the underlying fact where possible.
- SemiAnalysis and similar paywalled sources should not be reconstructed from snippets.
- Hacker News points and comments are dynamic snapshots, and commenter identities are generally unverifiable.
- Refresh market prices and the latest earnings from one authorized source immediately before publication.
- Labels describe evidentiary use. Even an A-level paper does not automatically establish a cross-task, cross-model universal scaling law.
- For the complete 2026-08-24 URL results and the distinction between broken links and bot-blocked links, see [LINK_CHECK.md](LINK_CHECK.md).
