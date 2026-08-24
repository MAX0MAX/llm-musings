# Scaling Laws Topic — Full Link and Citation Audit

> Audit date: 2026-08-24
>
> Scope: the 13 existing Markdown files under `talks/scaling-laws-in-a-nutshell` before this report was added

## Result

The 13-file source corpus contained **172 unique external URLs** and **12 unique local targets**. After adding and linking this report, the 2026-08-24 14-file snapshot contained the same 172 external URLs and **13 unique local targets**. Every external target was requested with redirects enabled, every local file and Markdown heading target was resolved, and the important links were also checked for semantic fit rather than relying on status codes alone. The table below records that snapshot; the later reading-list follow-up is recorded immediately after it.

| Final classification | Count | Meaning |
| --- | ---: | --- |
| Direct success | 151 | Final HTTP response was successful and the target was not an unexpected redirect. |
| Expected, valid redirect | 2 | The canonical Alphabet earnings page redirects to the official event page; Anthropic's Claude 4 model-card page redirects to its official PDF. |
| Access-limited but independently validated | 19 | 15 Hacker News items, 3 Reuters pages, and 1 WallStreetCN mirror were blocked or transiently unavailable to the automated client. |
| Confirmed broken (`404`/`410`) | 0 | None. |
| Local file or heading-anchor problem | 0 | None after this report was created. |

The final automated pass returned `403` for all 15 Hacker News items; earlier passes also produced transient `429` and `503` responses. All 15 item IDs exist in the official Hacker News Firebase API, and their story/comment roles and cited context were checked. The three Reuters URLs return `401` to this client but still identify the stated articles. The WallStreetCN page returns `403`; it is retained only as a dated mirror now that the accessible 36Kr/Waves publication is the primary interview link.

### 2026-08-25 reading-list follow-up

The revised [READING_LIST.md](READING_LIST.md) adds eight unique external targets, bringing the current 14-file corpus to **180 unique external URLs** while retaining **13 unique local targets**. All eight returned HTTP `200` with redirects enabled and were checked for semantic fit: the Schaeffer paper; the official 3Blue1Brown Bilibili upload; Hugging Face's Chinese RLHF explainer, FineWeb interactive article, and test-time-compute visualization; plus the optional Chinese CS336, Datawhale, and test-time-scaling notes. No local target or heading-anchor problem was introduced.

## Citation-target fixes

| Problem | Resolution |
| --- | --- |
| A two-page U.S. Copyright Office Fair Use Index summary was labeled as the 32-page Bartz court order. | Replaced the primary links in [README.md](README.md), [READING_LIST.md](READING_LIST.md), [data-scaling.md](data-scaling.md), and [ALL_SOURCES.md](ALL_SOURCES.md) with the actual Dkt. 231 court PDF. The government summary remains only where it is explicitly labeled as a summary. |
| The Bartz final-approval links used DocumentCloud without an explicit docket identity. | Replaced them with the Dkt. 680 court PDF and labeled the docket number. |
| A deleted WeChat page still returned HTTP 200, hiding the semantic failure. | Replaced it with the accessible 36Kr/Waves interview, corrected the main publication date to 2024-07-22, and retained the 2024-07-18 WallStreetCN copy only as a dated mirror. |
| The Micron FY2025 Q2 prepared-remarks URL redirected to the IR overview page. | Replaced it with the working Micron official-CDN PDF already used by the infrastructure dossier. |
| The old Dwarkesh domain redirected to the current domain. | Replaced it with the canonical current URL. |
| Four README paper links pinned older arXiv versions although newer revisions exist. | Changed RETRO, Ganguli et al., Porian et al., and Kimi k1.5 to unversioned arXiv links so readers receive the latest revision. |

## Source-access and provenance improvements

- Recovered Micron's official FY2025 Q1 prepared-remarks PDF and current quarterly-results archive; the secondary transcript is no longer the primary route.
- Replaced Samsung's regional Q2 2024 mirror with the global Newsroom page.
- Replaced the bot-blocked SEC table fragment with Amazon's official 2024 Annual Report PDF and identified the printed page containing the table.
- Added Amazon's official Q4 2024 earnings-call page beside the secondary transcript.
- Replaced the old Alphabet IR path with its canonical earnings-call URL; its redirect is expected and stays within Alphabet.
- Replaced the HTTP-only Era of Experience route with the HTTPS DeepMind-hosted PDF.
- Corrected the Reuters version boundary for NVIDIA's 2024 return: the 2024-12-23 snapshot reported 172%, while the 2024-12-31 update reported 178%.
- Updated stale notes that described three currently accessible OpenAI pages as timeouts; the 2026-08-24 check returned 200 for all three.

## What remains a human publication check

The remaining items are evidence-quality or freshness tasks, not unresolved broken links:

- Recompute all market-return numbers from one licensed source with one calendar, adjustment, currency, and endpoint convention.
- Recheck the Bartz docket for appeals, settlement effectiveness, and distribution status before presenting current legal status.
- Re-listen to any quotation taken only from YouTube auto-captions or transcript mirrors.
- Do not reconstruct paywalled claims from snippets.
- Record access dates or archive snapshots for continuously updated company/help pages.

An HTTP success does not prove that a page still contains the cited evidence; the deleted WeChat page is the concrete counterexample from this audit. Conversely, a `401`, `403`, `429`, or transient `5xx` response from an automated client does not by itself prove that a citation is dead.
