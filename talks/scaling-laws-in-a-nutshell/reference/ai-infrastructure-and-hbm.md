# AI infrastructure and HBM: evidence for slides 1–3

Research date: **2026-08-24**
Evidence cutoff used in the talk: **2025-04-24**, except for later material that can be re-opened and checked against an original filing or company page.
Purpose: build a defensible opening chain from observable business results to GPU/HBM demand and hyperscaler infrastructure spending. This is **not investment research** and does not treat share prices as evidence for scaling laws.

## Bottom line

The evidence safely supports this chain:

1. In 2024 and early 2025, NVIDIA's Data Center revenue and the AI-memory businesses of SK hynix, Samsung, and Micron rose sharply or became strategically more important.
2. AI accelerators pair very high compute throughput with HBM. HBM supplies the capacity and bandwidth needed to keep accelerator compute fed; for example, NVIDIA specifies 141 GB of HBM3e and 4.8 TB/s for H200.
3. HBM is unusually silicon- and process-intensive. Micron says HBM3E consumes about **3×** the silicon of DDR5 for the same bit output; TrendForce separately describes larger dies, lower yields, longer cycles, and substantial advanced-node wafer allocation.
4. Microsoft, Alphabet, Meta, and Amazon disclosed very large infrastructure investment, and their own materials connect much of it to cloud and AI capacity. The figures are not perfectly comparable and are not “pure AI capex.”
5. The companies say they invest against customer demand, contracted backlog, capacity constraints, and expected use of training and inference in products and cloud services. Scaling-law research may inform model-building strategy, but these filings do **not** establish that scaling laws caused the spending or any stock-price movement.

**Safe sentence for the talk**

> “The visible chain is demand and capacity, not a stock-market proof of scaling laws: cloud providers report spending tens of billions on AI-capable infrastructure; accelerator sales rose; each accelerator needs high-bandwidth memory; and HBM consumes disproportionate leading-edge DRAM resources. Scaling laws enter only at the next question—why model builders expect additional well-directed compute to improve measured model outcomes.”

**Forbidden over-causal sentence**

> “Scaling laws made NVIDIA and memory stocks rise, proving that buying more GPUs always creates better AI and higher shareholder returns.”

That sentence collapses technical evidence, company demand, memory supply, pricing, macro conditions, and valuation into one unsupported cause.

## 1. Four-company opening facts

### Comparable market window, with a warning

For a one-page market chart, use **total shareholder-price return from the last trading day of 2023 to the last trading day of 2024**, rebased to 100 and adjusted for NVIDIA's 2024 stock split. The following published year-end facts are usable as a **cross-check**, not as the final chart data:

- NVIDIA: Reuters reported **+178% in 2024**.
- SK hynix: Reuters reported **+23% in 2024**.
- Samsung Electronics: Reuters reported **−32% in 2024**.
- Micron: the cleanest full-year quote found was StatMuse's **+0.6% in 2024**; Reuters reported that it was still about +22% immediately before its December 18 guidance and then fell sharply. Because StatMuse is below the requested source hierarchy, **refresh Micron and all four price series from one institutional market-data vendor before publication**.

The divergence is the point. It prevents the slide from implying “AI hardware all went up together.” Samsung and Micron show that qualification progress, consumer-memory exposure, guidance, competitive position, macro expectations, and valuation can dominate a simple AI-demand narrative.

### Better evidence than price alone: operating facts

| Company | Reporting window | Verifiable fact | What it supports | What it does not support |
| --- | --- | --- | --- | --- |
| NVIDIA | FY2025, ended 2025-01-26 | Total revenue **$130.5bn, +114% YoY**; Data Center revenue **$115.2bn, +142% YoY** | Accelerator/data-center demand became the dominant revenue engine | The release attributes demand to accelerated computing and AI, but does not isolate scaling laws |
| SK hynix | CY2024 | Revenue **KRW 66.193tn, +102%**; operating profit **KRW 23.467tn** versus a KRW 7.730tn loss; Q4 HBM exceeded **40% of DRAM revenue** | AI memory/HBM materially changed the company's mix and earnings | Recovery also includes price, inventory, eSSD, supply discipline, and the broader memory cycle |
| Samsung Electronics | CY2024 | Revenue **KRW 300.9tn**; operating profit **KRW 32.7tn**; Memory achieved record Q4 revenue as HBM/server DDR5 raised blended DRAM ASP | HBM and server memory helped revenue and pricing | Samsung is diversified; consolidated results include phones, displays, appliances, foundry, and other memory |
| Micron | FY2024, ended 2024-08-29 | Revenue **$25.111bn**, versus **$15.540bn**; Q4 revenue **+93% YoY**; company said robust AI demand drove data-center DRAM and HBM ramp | AI products contributed to a strong memory recovery | Fiscal year is not calendar 2024; NAND, conventional DRAM pricing, and cycle recovery also mattered |

Do not put these four revenue growth rates into one bar chart as if they cover the same dates or business scope. They are opening facts, not a standardized comparison.

## 2. From GPU demand to HBM demand

### Why HBM matters to an AI accelerator

An accelerator can only use its arithmetic units when model weights, activations, attention state, and intermediate results move through memory quickly enough. HBM puts stacked DRAM close to the processor on a very wide interface. This provides:

- **Bandwidth:** many bytes per second to feed parallel compute;
- **Capacity near the accelerator:** enough memory for larger model partitions, batches, and inference state;
- **Energy efficiency per transferred bit:** data movement is a major system cost.

NVIDIA's H200 page is useful because it states a product fact rather than a generic marketing abstraction: **141 GB HBM3e at 4.8 TB/s**, almost twice H100's capacity and 1.4× its bandwidth. It says the larger/faster memory accelerates generative AI and LLM workloads. This proves that HBM is an integral accelerator subsystem; it does not prove that every workload is memory-bound or that more HBM always improves end-to-end performance.

### Why HBM can tighten ordinary DRAM supply

There are three linked constraints:

1. **More silicon per delivered bit.** Micron states that HBM3E consumes about **3× the silicon** of DDR5 for the same bit output; it expects the ratio to rise for HBM4 and exceed 4:1 for HBM4E.
2. **More difficult manufacturing.** TrendForce estimated HBM dies were 35–45% larger than DDR5 at comparable process/capacity, yields including TSV packaging 20–30% lower, and production cycles 1.5–2 months longer.
3. **Shared leading-edge resources.** HBM uses DRAM wafers plus TSV/stacking and advanced packaging. TrendForce expected HBM to take 35% of advanced-process wafer input by end-2024. Samsung explicitly said concentrating capacity on HBM, AI server DRAM, and server SSDs could constrain conventional leading-edge PC/mobile bit supply.

The correct wording is **“reduces the bit output and resources available to non-HBM products at a given installed capacity”**, not “every HBM wafer literally replaces one consumer-memory wafer.” Front-end nodes, back-end tools, yields, qualifications, and product mixes are not fully interchangeable.

## 3. Supplier evidence: revenue, orders, capacity, and supply

### SK hynix

- Q3 2024 HBM sales grew **more than 70% QoQ and more than 330% YoY**; HBM was 30% of DRAM revenue and the company forecast 40% in Q4.
- FY2024 results later said HBM exceeded **40% of Q4 DRAM revenue**.
- In Q1 2025, SK hynix explained that HBM supply volume is generally agreed about a year ahead and maintained its company forecast that 2025 HBM demand would approximately double.

Boundary: “approximately double” is management's forecast as of 2025-04-24. It is not an audited market total. The company did not disclose a full HBM order book, customer-by-customer volume, or a separate annual HBM revenue number.

### Samsung Electronics

- Q1 2024 capex focused memory spending on HBM, DDR5, and related packaging; Samsung began HBM3E 8H mass production and planned HBM3E 12H.
- Q2 2024 said cloud-provider AI investment was driving HBM, conventional DRAM, and server SSD demand, and that concentrating capacity on AI products would constrain conventional leading-edge bit supply.
- FY2024 results said increased HBM and high-density server DDR5 lifted blended DRAM ASP and helped Memory reach record Q4 revenue.
- Q1 2025 is important negative evidence: HBM sales fell because of AI-chip export controls and demand deferred for an enhanced HBM3E product.

Boundary: Samsung did not disclose a clean 2024 HBM revenue, order book, or “sold out” figure in the reviewed primary materials. Its results demonstrate both AI demand and company-specific execution/qualification risk.

### Micron

- FY2024 revenue rose to **$25.111bn**; Micron said robust AI demand drove its data-center DRAM and HBM ramp.
- Its December 2024 prepared remarks said HBM revenue more than doubled sequentially and calendar-2025 HBM output was **sold out with pricing already determined**; it forecast multiple billions of HBM revenue in FY2025.
- Later prepared remarks explain the supply mechanism: HBM3E's 3:1 silicon trade ratio contributes to tight leading-edge supply and constrains non-HBM DRAM.

Boundary: “sold out,” TAM forecasts, and future revenue are company statements at a point in time, not independently audited demand. Customer concentration, qualification, yield, and schedule execution remain relevant.

## 4. Hyperscaler capex: official numbers and comparability

| Company | Period and official figure | Link to AI infrastructure | Comparability boundary |
| --- | --- | --- | --- |
| Microsoft | FY2024 capex including finance leases **$55.7bn** (sum of disclosed quarters); Q4 **$19.0bn** | Microsoft said cloud and AI represented nearly all capex; roughly half was long-lived data centers and the rest primarily CPU/GPU servers. It also said AI capacity was constrained. | Includes finance leases; not pure AI; fiscal year ended 2024-06-30 |
| Alphabet | CY2024 capex approximately **$52.5bn** from filings; Q3 **$13.1bn** | Q3 call: most technical-infrastructure spend; about 60% servers (TPUs and GPUs), 40% data centers/networking; supports Gemini, Cloud, and Services. | Includes non-AI technical infrastructure and some other assets |
| Meta | CY2024 capex including finance-lease principal **$39.23bn** | Meta said it accelerated infrastructure for its AI roadmap; 2025 growth would support generative AI and core business. | Meta explicitly says most 2025 capex still supports the core business; no pure-AI breakout |
| Amazon | CY2024 property-and-equipment additions **$85.752bn**, of which AWS **$53.267bn** | SEC segment table gives the AWS amount. On the Q4 call, management said most 2025 technology infrastructure would support AWS, including AI services, and that procurement follows demand signals. | “Additions” differs from cash capex and from competitors' finance-lease definitions; AWS includes non-AI cloud |

**Do not add these four numbers into a “Big Tech AI capex” total.** Their accounting definitions and fiscal periods differ. A safe slide either:

- shows four separately labeled bars with definitions in footnotes; or
- uses only companies with a harmonized cash-purchases-of-PP&E measure from 10-K statements.

## 5. Why the industry keeps buying compute

The primary sources support four motives:

1. **Cloud customer demand and backlog.** Microsoft tied server procurement to customer demand signals and said it was AI-capacity constrained. Amazon said it procures infrastructure after seeing significant demand signals.
2. **First-party product use.** Alphabet says infrastructure supports Google Services, Google Cloud, and DeepMind; Meta connects capex to its recommendation systems, core business, and generative-AI roadmap.
3. **Training and inference both consume capacity.** Product materials and calls consistently describe AI infrastructure as serving both. Inference can make continuing demand depend on user traffic and product economics, not only one-off frontier training runs.
4. **Long-lived platform strategy.** Data centers, power, networking, and servers can support multiple cloud and AI workloads. Microsoft specifically calls its long-lived infrastructure fungible across its cloud.

These are management explanations plus observed expenditure—not proof that all investment earns an adequate return. They coexist with:

- uncertain model and product monetization;
- rapid hardware depreciation and obsolescence;
- energy, permitting, networking, and packaging bottlenecks;
- customer concentration and custom accelerators;
- export controls;
- the possibility that efficiency gains reduce compute per task while lower costs increase total usage.

## 6. Keep the causal factors separate

### AI demand

Evidence: NVIDIA Data Center growth; hyperscaler calls; HBM sales mix and data-center DRAM growth.
Boundary: “AI” includes training, inference, recommendation, cloud rentals, internal services, and conventional workloads reported together.

### Supply constraints

Evidence: HBM silicon trade ratio, lower yield/longer cycle, advanced packaging and leading-node allocation, capacity-constrained cloud commentary.
Boundary: a constraint can ease through yields, node transitions, new fabs, packaging expansion, or lower demand.

### Memory cycle

Evidence: SK hynix swung from a 2023 loss to a 2024 profit; Samsung and Micron discuss inventory, conventional PC/mobile demand, and recovering ASPs.
Boundary: HBM is not the whole DRAM/NAND market. Inventory correction and supplier production discipline independently affect revenue and margins.

### Pricing and mix

Evidence: Samsung attributes higher blended DRAM ASP to HBM and high-density DDR5; Micron says HBM gross margins were accretive and 2025 pricing had been set.
Boundary: revenue can rise because of price/mix even if unit growth is lower; company ASP is not the same as spot price.

### Macro, policy, and execution

Evidence: Samsung cited export controls and deferred HBM demand; Reuters documented tariff concern and different customer exposures. Qualification, yield, power, data-center construction, and interest rates can change outcomes.
Boundary: these effects are difficult to isolate from one quarter of reported results.

### Valuation expectations

Evidence: SK hynix shares fell 8.4% on a day it reported its highest profit since 2018; Micron fell after guidance despite strong AI-related sales.
Boundary: a stock price reflects discounted future cash flow, risk, positioning, rates, and expectations—not just current demand.

## 7. What is suitable for a standardized slide

### Recommended slide 1 chart

**Four rebased total-return lines, 2024-01-02 = 100, through 2024-12-31**

- Use one vendor, same close convention, same timezone rule, and adjusted prices.
- Include NVIDIA split adjustment and reinvested dividends if “total return” is claimed; otherwise label “adjusted price return.”
- Tickers/exchanges: NVDA (Nasdaq), 000660 (KRX), 005930 (KRX), MU (Nasdaq).
- Show local-currency returns; rebasing makes currencies irrelevant to percentage movement.
- Put a thin KOSPI and Nasdaq-100 benchmark in gray only if the visual remains readable.
- Footnote source, retrieval date, and exact endpoint dates.

**Avoid**

- mixing ADRs and Korean ordinary shares;
- using current intraday prices for one company and closing prices for others;
- selecting each company's local low as the starting point;
- putting causal labels such as “scaling laws” on price inflections;
- omitting Samsung's decline or Micron's late-year reversal.

### Recommended slide 1 fallback

If a licensed, reproducible four-stock series is unavailable, use four **fact cards** instead of a line chart:

- NVIDIA: FY2025 Data Center revenue +142%;
- SK hynix: 2024 revenue +102%, Q4 HBM >40% of DRAM revenue;
- Samsung: record Q4 Memory revenue, but 2024 shares −32%;
- Micron: FY2024 revenue +62%, while consumer weakness later hurt guidance.

Label each period; do not imply the fiscal windows match.

### Recommended slide 2 visual

One H200 block:

`HBM3e (141 GB, 4.8 TB/s) → GPU compute`

Then zoom out to multiple accelerator blocks and add one restrained annotation:

`HBM3E ≈ 3× DDR5 silicon per delivered bit (Micron company statement)`

Keep “3×” attached to **same bit output**, not per package, per wafer, cost, or revenue.

### Recommended slide 3 visual

Use a capex “wall” with four separate figures and accounting labels, then a question mark:

`Microsoft $55.7bn | Alphabet ~$52.5bn | Meta $39.23bn | Amazon AWS additions $53.27bn`

Subtitle: “Large infrastructure commitments; not a harmonized AI-only total.”
Transition: “What evidence makes model builders believe additional, well-directed compute can improve model outcomes?”

## 8. Source cards

The list below contains **21 distinct sources**. Company forecasts are labeled as such.

### S1 — NVIDIA FY2025 results

- **Title:** NVIDIA Announces Financial Results for Fourth Quarter and Fiscal 2025
- **Institution / date:** NVIDIA Investor Relations, 2025-02-26
- **Link:** https://investor.nvidia.com/news/press-release-details/2025/NVIDIA-Announces-Financial-Results-for-Fourth-Quarter-and-Fiscal-2025/
- **Key facts:** FY revenue $130.5bn, +114%; Data Center $115.2bn, +142%; Q4 Data Center $35.6bn, +93%.
- **Why included:** strongest audited-adjacent company evidence that accelerator/data-center sales expanded.
- **Evidence boundary:** segment includes networking and other data-center products; company attribution to AI is not a scaling-law test.

### S2 — NVIDIA H200 product specification

- **Title:** H200 GPU
- **Institution / date:** NVIDIA, product page accessed 2026-08-24; H200 announced 2023-11
- **Link:** https://www.nvidia.com/en-us/data-center/h200/
- **Key facts:** 141 GB HBM3e, 4.8 TB/s; nearly 2× H100 capacity and 1.4× bandwidth.
- **Why included:** primary product evidence connecting HBM to an AI accelerator.
- **Evidence boundary:** vendor specification and workload claim; not independent performance testing.

### S3 — SK hynix FY2024 results

- **Title:** SK hynix Announces 4Q24 Financial Results
- **Institution / date:** SK hynix Newsroom / IR, 2025-01-23
- **Link:** https://news.skhynix.com/en/sk-hynix-announces-4q24-financial-results/
- **Key facts:** 2024 revenue KRW 66.193tn (+102%); operating profit KRW 23.467tn versus loss; HBM >40% of Q4 DRAM revenue.
- **Why included:** best annual operating evidence for SK hynix.
- **Evidence boundary:** preliminary K-IFRS release; does not separately disclose annual HBM revenue.

### S4 — SK hynix Q3 2024 HBM mix

- **Title:** SK hynix Announces 3Q24 Financial Results
- **Institution / date:** SK hynix Newsroom / IR, 2024-10-24
- **Link:** https://news.skhynix.com/en/sk-hynix-announces-3q24-financial-results/
- **Key facts:** HBM sales >70% QoQ and >330% YoY; 30% of DRAM revenue; company forecast 40% in Q4.
- **Why included:** quantifies HBM growth and mix.
- **Evidence boundary:** Q4 40% was a forecast at publication; later annual release only says “over 40%.”

### S5 — SK hynix Q1 2025 supply contracting

- **Title:** SK hynix Announces 1Q25 Financial Results
- **Institution / date:** SK hynix Newsroom / IR, 2025-04-24
- **Link:** https://news.skhynix.com/en/sk-hynix-announces-1q25-financial-results/
- **Key quote/fact:** HBM supply volume is mutually agreed about a year ahead; company maintained forecast that HBM demand would approximately double YoY.
- **Why included:** primary explanation of order timing and visibility.
- **Evidence boundary:** demand doubling is management's projection, not realized audited volume.

### S6 — Samsung FY2024 results

- **Title:** Samsung Electronics Announces Fourth Quarter and FY 2024 Results
- **Institution / date:** Samsung Global Newsroom / IR, 2025-01-31
- **Link:** https://news.samsung.com/global/samsung-electronics-announces-fourth-quarter-and-fy-2024-results
- **Key facts:** FY revenue KRW 300.9tn; operating profit KRW 32.7tn; record Q4 Memory revenue, with HBM and server DDR5 lifting blended DRAM ASP.
- **Why included:** primary annual evidence for Samsung's HBM/pricing contribution.
- **Evidence boundary:** consolidated company and Memory results are not HBM-only.

### S7 — Samsung Q1 2024 capacity action

- **Title:** Samsung Electronics Announces First Quarter 2024 Results
- **Institution / date:** Samsung Global Newsroom / IR, 2024-04-30
- **Link:** https://news.samsung.com/global/samsung-electronics-announces-first-quarter-2024-results
- **Key facts:** Q1 capex KRW 11.3tn, including KRW 9.7tn for DS; memory spending focused on HBM, DDR5, and packaging; HBM3E 8H mass production began.
- **Why included:** connects demand to concrete production investment.
- **Evidence boundary:** DS capex includes more than HBM; production plans are company statements.

### S8 — Samsung Q2 2024 supply interaction

- **Title:** Samsung Electronics Announces Results for Second Quarter of 2024
- **Institution / date:** Samsung Newsroom, 2024-07-31
- **Link:** https://news.samsung.com/nl/samsung-electronics-announces-results-for-second-quarter-of-2024
- **Key quote/fact:** concentrating capacity on HBM, AI server DRAM, and SSDs was expected to constrain conventional leading-edge PC/mobile bit supply.
- **Why included:** direct company statement of the HBM-to-conventional-memory transmission.
- **Evidence boundary:** forward-looking statement; regional Newsroom mirror of company release.

### S9 — Samsung Q1 2025 negative evidence

- **Title:** Samsung Electronics Announces First Quarter 2025 Results
- **Institution / date:** Samsung Global Newsroom / IR, 2025-04-30
- **Link:** https://news.samsung.com/global/samsung-electronics-announces-first-quarter-2025-results
- **Key fact:** HBM sales fell due to AI-chip export controls and deferred demand pending enhanced HBM3E.
- **Why included:** prevents a one-directional “AI demand explains everything” account.
- **Evidence boundary:** company explanation; does not quantify each factor.

### S10 — Micron FY2024 results

- **Title:** Micron Technology, Inc. Reports Results for the Fourth Quarter and Full Year of Fiscal 2024
- **Institution / date:** Micron Investor Relations, 2024-09-25
- **Link:** https://investors.micron.com/news/press-release/2024/Micron-Technology-Inc--Reports-Results-for-the-Fourth-Quarter-and-Full-Year-of-Fiscal-2024-09-25-2024/default.aspx
- **Key facts:** FY revenue $25.111bn versus $15.540bn; Q4 $7.75bn, +93% YoY; company linked ramp to AI data-center DRAM and HBM.
- **Why included:** primary annual financial evidence for Micron.
- **Evidence boundary:** fiscal year ended August 29; recovery includes NAND, pricing, and conventional memory.

### S11 — Micron 2025 HBM allocation

- **Title:** Fiscal Q1 2025 prepared remarks / earnings materials
- **Institution / date:** Micron Investor Relations, 2024-12-18
- **Link:** [Micron quarterly results archive](https://investors.micron.com/financials/quarterly-results/default.aspx); [transcript mirror](https://www.fool.com/earnings/call-transcripts/2024/12/18/micron-technology-mu-q1-2025-earnings-call-transcr/) (the former direct PDF now redirects to the IR homepage)
- **Key quote/fact:** calendar-2025 HBM output “sold out,” pricing determined; HBM revenue more than doubled sequentially; company forecast multiple billions in FY2025 HBM revenue.
- **Why included:** strongest primary supply/order statement from Micron.
- **Evidence boundary:** “sold out,” TAM, and future revenue are management statements, not audited future outcomes.

### S12 — Micron HBM silicon trade ratio

- **Title:** Fiscal Q2 2025 prepared remarks
- **Institution / date:** Micron Investor Relations, 2025-03-20
- **Link:** https://s25.q4cdn.com/621799436/files/doc_financials/2025/q2/Micron_FY25_Q2_Prepared_Remarks_2-1.pdf
- **Key quote/fact:** HBM3E consumes 3× the silicon of DDR5 for the same bits; HBM4 higher; HBM4E expected above 4:1; this constrains non-HBM leading-edge supply.
- **Why included:** primary explanation for ordinary-DRAM supply pressure.
- **Evidence boundary:** company estimate and forward view; “silicon” is not identical to total finished-product capacity.

### S13 — Microsoft FY2024 capex

- **Title:** Microsoft Fiscal Year 2024 Fourth Quarter Earnings Conference Call
- **Institution / date:** Microsoft Investor Relations, 2024-07-30
- **Link:** https://www.microsoft.com/en-us/investor/events/fy-2024/earnings-fy-2024-q4
- **Key facts:** Q4 capex including finance leases $19bn; quarterly disclosures sum to $55.7bn FY2024; cloud/AI nearly all capex; AI capacity constrained.
- **Why included:** strongest official capex-to-demand link among hyperscalers.
- **Evidence boundary:** includes cloud non-AI and finance leases; summed annual figure should be labeled as derived from four official quarters.

### S14 — Alphabet infrastructure composition

- **Title:** 2024 Q3 Earnings Call
- **Institution / date:** Alphabet Investor Relations, 2024-10-29
- **Link:** https://abc.xyz/investor/events/event-details/2024/2024-Q3-Earnings-Call/
- **Key facts:** Q3 capex $13bn; technical infrastructure approximately 60% servers (TPUs/GPUs), 40% data centers/networking.
- **Why included:** official breakdown of what capex buys and whom it serves.
- **Evidence boundary:** not AI-only; the approximately $52.5bn CY2024 total should be refreshed from the 10-K before publication.

### S15 — Meta FY2024 capex

- **Title:** Meta Reports Fourth Quarter and Full Year 2024 Results
- **Institution / date:** Meta Investor Relations, 2025-01-29
- **Link:** https://investor.atmeta.com/investor-news/press-release-details/2025/Meta-Reports-Fourth-Quarter-and-Full-Year-2024-Results/
- **Key facts:** 2024 capex including finance-lease principal $39.23bn; 2025 capex then forecast at $60–65bn, supporting gen-AI and core business.
- **Why included:** official realized annual capex and explicit allocation boundary.
- **Evidence boundary:** no pure-AI breakout; 2025 range was a forecast and is stale.

### S16 — Amazon 2024 10-K segment additions

- **Title:** Amazon 2024 Form 10-K, Segment Information—Property and Equipment Additions
- **Institution / date:** Amazon / U.S. SEC, filed 2025-02-07
- **Link:** https://www.sec.gov/Archives/edgar/data/1018724/000101872425000004/R90.htm
- **Key facts:** total 2024 additions $85.752bn; AWS $53.267bn versus $24.843bn in 2023.
- **Why included:** regulator-hosted, segment-specific infrastructure measure.
- **Evidence boundary:** additions are not cash capex; AWS includes ordinary cloud capacity and leases.

### S17 — Amazon demand logic

- **Title:** Amazon Q4 2024 earnings call transcript
- **Institution / date:** Amazon call, 2025-02-06; accessible transcript copy by The Transcript
- **Link:** https://thetranscript.net/transcript/7502/amazon.com-q4-2024-earnings-report
- **Key quote/fact:** Q4 capital investment $26.3bn; management said most technology infrastructure supported AWS, including AI services, and procurement follows significant demand signals.
- **Why included:** explains why capacity is purchased.
- **Evidence boundary:** transcript host is secondary; verify against Amazon webcast/official transcript before quoting verbatim. Forward capex comments are company expectations.

### S18 — TrendForce HBM manufacturing intensity

- **Title:** 2024 HBM Supply Bit Growth Estimated to Reach 260%, Making Up 14% of DRAM Industry
- **Institution / date:** TrendForce, 2024-03-18
- **Link:** https://www.trendforce.com/presscenter/news/20240318-12081.html
- **Key estimates:** 250K wafers/month or 14% of capacity for HBM TSV by end-2024; die 35–45% larger; yield 20–30% lower; cycle 1.5–2 months longer than DDR5.
- **Why included:** independent industry triangulation of the Micron mechanism.
- **Evidence boundary:** estimates and forecast, not supplier-audited capacity; “14%” refers to the article's capacity framing, not HBM bit share.

### S19 — TrendForce advanced-node allocation

- **Title:** HBM3e Production Surge Expected to Make Up 35% of Advanced Process Wafer Input by End of 2024
- **Institution / date:** TrendForce, 2024-05-20
- **Link:** https://www.trendforce.com/presscenter/news/20240520-12143.html
- **Key estimate:** HBM expected to take 35% of advanced-process wafer input; constrained yield and larger wafer area increase input needs.
- **Why included:** quantifies leading-edge resource competition.
- **Evidence boundary:** forecast; “35%” is advanced-process wafer input, not total DRAM production.

### S20 — Reuters year-end NVIDIA market fact

- **Title:** Markets in 2024: Wall Street's high-octane rally keeps investors captive to the US
- **Institution / date:** Reuters, 2024-12-23
- **Link:** https://www.reuters.com/markets/global-markets-year-end-graphic-2024-12-23/
- **Key fact:** NVIDIA shares rose 178% in 2024.
- **Why included:** authoritative market cross-check for the opening chart.
- **Evidence boundary:** market return does not identify cause; exact endpoint/method should be reproduced from one data vendor.

### S21 — Reuters Samsung/SK hynix divergence and expectations

- **Title:** Samsung's preliminary Q4 profit falls far short of estimates as chip issues drag
- **Institution / date:** Reuters, 2025-01-08
- **Link:** https://www.reuters.com/business/media-telecom/samsung-fourth-quarter-operating-profit-outlook-misses-estimates-by-large-margin-2025-01-07/
- **Key facts:** Samsung shares fell 32% in 2024; SK hynix rose 23%; Samsung missed profit expectations while working to qualify high-end HBM.
- **Why included:** clean same-market-window counterexample and evidence that execution/expectations matter.
- **Evidence boundary:** Reuters' causal discussion synthesizes analysts and market context; it is not a controlled attribution.

## 9. 2026 material excluded or downgraded

Search surfaced pages indexed as 2026 company releases, but several contained internally implausible values—for example, net income above revenue or abrupt multi-fold quarterly revenue changes without a regulator filing checked in parallel. A URL on an IR domain is not enough if the content cannot be reconciled to an SEC/KRX filing.

Therefore:

- no 2026 NVIDIA, SK hynix, Samsung, Micron, or hyperscaler number is used as a core slide fact here;
- no search-result summary is treated as evidence;
- no claim that 2026/2027 HBM is sold out is included without an original filing/call transcript that can be independently reopened;
- 2026 claims should be added only after reconciling the company release, regulator filing, accounting units, and a second authoritative report.

## 10. Slides 1–3 material recommendation

### Slide 1 — “Memory moved onto the AI stage”

- Prefer the four rebased 2024 price lines after a licensed-data refresh.
- Put two callouts only: NVIDIA +178%; Samsung −32% / SK hynix +23%.
- Say: “Markets repriced different positions in the AI hardware chain—but not uniformly.”
- Speaker note: Micron's late-year reversal and Samsung's decline show why AI demand is not a complete stock explanation.

### Slide 2 — “A GPU must be fed”

- Use H200's 141 GB / 4.8 TB/s as the concrete anchor.
- Show HBM beside—not underneath—the GPU, then repeat the unit into a cluster.
- Add the 3× silicon trade ratio in a footnote.
- Say: “HBM increases the rate at which the accelerator can reach nearby data; producing the same number of memory bits consumes more scarce silicon and process resources.”

### Slide 3 — “Why keep building?”

- Show separately labeled 2024 infrastructure figures for Microsoft, Alphabet, Meta, and Amazon AWS.
- Do not total them.
- Say: “The companies cite customer demand, backlog, capacity constraints, and first-party AI products. That establishes a large bet, not that the bet must pay off.”
- End on the question: “What technical evidence made model builders expect well-directed additional compute to improve outcomes?”

## 11. Refresh before publication

1. Pull all four daily adjusted-close series from one licensed vendor; save CSV, query timestamp, exchange calendars, corporate-action settings, and exact endpoints.
2. Replace the 2024 chart with a newer common window only if all four series are reproducible; otherwise keep 2024.
3. Re-open NVIDIA's latest 10-Q/10-K and update Data Center revenue.
4. Re-open SK hynix and Samsung KRX/DART filings and Micron's SEC filing; reconcile any latest HBM/order claims to earnings-call transcripts.
5. Update hyperscaler capex using one accounting definition. Keep “AI-only” separate from total technical infrastructure.
6. Check whether company forecasts (“sold out,” demand doubling, planned capacity) became realized results.
7. Refresh export-control, HBM qualification, and advanced-packaging context.
8. Verify every quote against the live page or archived PDF; do not quote a transcript aggregator if the official transcript is available.
9. Put the data cutoff and source directly on each slide.

## 12. Most important sources

1. NVIDIA FY2025 results — Data Center revenue: S1.
2. SK hynix FY2024 results — HBM mix and earnings: S3.
3. Samsung FY2024 results — HBM/server DDR5 and ASP: S6.
4. Micron FY2025 Q1 prepared remarks — sold-out statement and pricing: S11.
5. Micron FY2025 Q2 prepared remarks — 3× silicon trade ratio: S12.
6. Microsoft FY2024 Q4 call — capex composition and AI capacity constraint: S13.
7. Amazon 2024 10-K segment table — AWS additions: S16.
8. TrendForce manufacturing comparison — die, yield, cycle, and wafer allocation: S18.
