# NOTES — decision log (ML × stock market, 2026 scouting run)

Run started 2026-11-02 (Europe/Amsterdam). Branch: `scouting-ml-stock-2026` (the prompt's `<BRANCH>` placeholder was not filled in, so a new branch was created off `main` instead of writing to `main`).

Repo state at start: only a one-line `README.md`. No earlier NOTES.md or lit review existed, so nothing to build on.

## Scope and rules for this run

- Literature rule: **only papers first published or first posted in 2026**. Exception: the original paper behind a named dataset or library, labelled `[BACKGROUND]`.
- Verification legend: **[FT]** full text opened · **[ABS]** abstract/record page opened · **[UNVERIFIED]** seen in a search result only, not relied on.
- Public data only. No data downloads, no code in this run.

## Phase 0 — Taxonomy of ML-in-stock-market subject areas (12 areas)

| ID | Area | What falls in it | Supervisor-signal links |
|---|---|---|---|
| A1 | **Graph & relational learning** | Stock/company graphs: GNNs, temporal, signed, heterogeneous, hypergraphs, dynamic graph structure learning, link prediction | temporal, signed, link prediction, heterogeneous |
| A2 | **Time-series foundation models & deep forecasting** | TSFMs (Chronos, TimesFM, Moirai, Kronos…) applied to or pretrained on financial series; transformer forecasting; zero-shot vs fine-tuned | time series + graph |
| A3 | **LLMs for financial text → signals** | News/earnings-call/filings sentiment, LLM embeddings as features, event extraction, return prediction from text | (supervisor: text analysis) |
| A4 | **LLM agents & multi-agent trading** | Agentic trading systems, multi-agent debate, LLM portfolio managers, agent benchmarks/arenas | — |
| A5 | **Reinforcement learning for trading/portfolio** | Portfolio RL, execution, market making, offline RL, RL + LLM | — |
| A6 | **ML asset pricing & alpha/factor mining** | Cross-sectional return models, deep factor models, LLM-/GP-based formulaic alpha mining, characteristic-based ML | — |
| A7 | **Generative models & market simulation** | Diffusion/GAN/flow synthetic market data, agent-based simulators, scenario generation, stress testing | — |
| A8 | **Causal ML, lead-lag & spillovers** | Causal discovery on returns, Granger/transfer entropy, lead-lag detection, connectedness networks | signed, temporal, causation |
| A9 | **Anomaly, regime & risk (incl. credit/default contagion)** | Regime/structural-break detection, crash early warning, manipulation detection, volatility/tail risk, default propagation into equity | anomaly, credit default |
| A10 | **Explainability & interpretability** | XAI for financial models, faithfulness of explanations, interpretable factor/graph models, LLM-rationale faithfulness | (Frank: XAI) |
| A11 | **Evaluation methodology & leakage** | Look-ahead bias (incl. LLM training-data contamination), backtest overfitting, benchmark design, transaction costs | — |
| A12 | **Company knowledge graphs & relation extraction** | Building firm graphs from filings/news with LLMs (supply chain, competitors, ownership), KG completion, graph quality | link prediction, heterogeneous, text |

Notes on the taxonomy:
- Credit-default contagion is folded into A9 (risk) but searched separately so it gets its own count.
- A1 and A12 overlap deliberately: A1 = learning *on* graphs, A12 = *building* the graph.
- Crypto-only papers are out of scope unless the method transfers.

## Access tests (2026-11-02)

| Route | Result |
|---|---|
| Google Scholar via web fetch | **Blocked** (robots_disallowed). Not retried. Scholar "cited by" checks left for Frank. |
| arXiv search page (`/search/`) via web fetch | **Blocked** (robots_disallowed). Not retried. |
| arXiv monthly listing pages (`/list/q-fin.XX/2026-10`) via web fetch | **Works** (summariser may truncate long lists). Used for q-fin.ST, .PM, .CP, .RM, .TR (Oct 2026) and q-fin.ST (Sep 2026). |
| arXiv abstract pages (`/abs/…`) via web fetch | **Works** — main verification route (`[ABS]`). |
| Web search | Works; often returns the arXiv abs/HTML page text directly (`[ABS-s]`). |

## Search queries log

### A1 Graph & relational
- `arxiv 2026 graph neural network stock prediction`
- `arxiv 2026 signed graph stock lead-lag network learning`
- `arxiv 2026 hypergraph stock temporal graph link prediction company`
- `2026 arxiv dynamic signed network stock correlation edge sign prediction OR "signed graph" equity`
- Listings: q-fin.ST 2026-09, 2026-10; q-fin.PM/CP/RM/TR 2026-10.

### A2 TSFMs
- `2026 arxiv time series foundation model stock returns zero-shot evaluation financial`
- `2026 financial foundation model pretrained market data Kronos OR "foundation model" equities benchmark arxiv`

### A3 LLM text → signals
- `2026 arxiv LLM news earnings call stock return prediction look-ahead bias embeddings`
- `arxiv 2026 large language model 10-K filings OR earnings calls cross-section stock returns signal`

## Phase 1 decisions
- Papers first posted on arXiv in 2025 but published in a 2026 venue (e.g. Kronos, AAAI 2026) are **excluded** under the strict 2026 rule, or kept only as `[BACKGROUND]` when they are a named library/dataset.
- Journal papers in 2026 issues with 2025 DOIs (online-first 2025) are excluded.

### A4 Agents
- listing scan q-fin.PM/TR/RM 2026-10
- `2026 arxiv LLM trading agents benchmark live market evaluation multi-agent stock`

### A5 RL
- listing scan q-fin.PM/TR 2026-10
- `2026 arxiv deep reinforcement learning portfolio optimization graph OR transaction costs stocks`

### A6 Alpha / asset pricing
- listing scan q-fin.PM/CP 2026-10, q-fin.ST 2026-09
- `2026 arxiv LLM formulaic alpha factor mining agent`

### A7 Generative
- listing scan q-fin.RM/TR 2026-10
- `2026 arxiv diffusion model synthetic stock returns generation multivariate equity scenario`
- Rate-limit hit on arXiv when fetching 3+ abs pages in parallel → now fetching ≤2 at a time. 2610.24544 not opened (rate-limited twice; skipped).

### A8 Causal / lead-lag
- `2026 arxiv causal discovery stock returns network Granger transfer entropy neural`
- `2026 arxiv lead-lag detection equities deep learning cross-asset predictability`

### A9 Anomaly / regime / credit
- `2026 graph neural network credit default contagion supply chain bankruptcy prediction listed firms`
- `2026 arxiv market manipulation detection pump and dump stocks machine learning OR graph anomaly detection equities`
- `2026 arxiv regime change detection correlation network stock market early warning crash machine learning`
- `arxiv 2026 corporate bankruptcy announcement spillover stock returns customers suppliers network learning`
- Finding: no 2026 ML paper on default → equity contagion over firm networks (gap signal, see crowding map).

### A10 XAI
- listing scan q-fin.PM/TR/CP 2026-10
- `2026 explainable graph neural network stock explanation faithfulness financial forecasting arxiv`

### A11 Evaluation
- listing scan q-fin.ST 2026-09/10
- `2026 reproducibility study stock movement prediction deep learning benchmarks leakage survivorship bias re-evaluation`

### A12 Company KGs
- `2026 LLM extraction company relationships supply chain knowledge graph SEC filings temporal knowledge graph finance arxiv`
- `2026 temporal knowledge graph link prediction companies financial events OR "company relation" prediction graph neural network arxiv`

Phase 1 complete: 12/12 areas covered (≈70 2026 items, of which ~50 `[ABS]`, rest `[ABS-s]`/`[UNVERIFIED]`). No full texts opened in this run (`[FT]` = 0) — breadth-first by design.

## Phase 3 — kill-test queries
- I1: `temporal link prediction lead-lag network stocks signed directed edges forecasting 2026`
- I3: `faithfulness explanations graph neural network stock prediction attention weights not explanation finance 2026`
- I4: `LLM look-ahead bias knowledge graph construction company relationships point-in-time supply chain extraction 2026`
- I5: `8-K bankruptcy filing contagion graph neural network stock returns linked firms prediction`; `credit rating downgrade spillover peer firms stock returns graph neural network prediction rating actions network 2026`
- I6: `SEC litigation releases labels pump and dump detection microcap stocks graph co-movement coordinated manipulation`
- I7: `learned stock graph adjacency compared with true industry supply chain relations does the learned graph reflect economic links`
- I9: `Chronos-2 covariates selection related series graph context time series foundation model stocks peer selection`
- I14: `13F common ownership network link prediction institutional holdings future co-holding comovement machine learning` → **killed by arXiv 2607.12067**
- I13: `predicting future supply chain links between listed firms temporal link prediction 10-K customer disclosures graph neural network`
- I15: `2026 tariff shock propagation firm network stock returns graph neural network exposure 10-K geopolitical`
- I16: `structural balance signed stock correlation network early warning crash 2026` → killed by 2608.12023 etc.
- I12: `forecasting correlation matrix next period generative model graph neural network stocks 2026 conditional`
- I8: `detecting AI or algorithmic herding in stock comovement networks LLM-driven trading correlation increase empirical 2026`
- I11: `e-values anytime valid testing lead-lag relationships stocks multiple testing network edges false discovery`

Rejected ideas and why: I8 (cannot identify AI trades in public data), I14 (2607.12067 did it, persistence baseline ~unbeatable), I16 (2026 balance-loss papers), I18 (A11-5 benchmark), I2/I12/I11/I13 merged into stronger cards.

## Phase 4 decisions
- Recommendation: **Card 1 (SignFlip)** as main topic, with a small explanation-reliability chapter borrowed from Card 3; Card 2 as alternative (text/KG side, Accenture relevance); Card 4 if the supervisor wants credit default specifically.
- Bib policy: arXiv IDs mentioned only as *excluded* (pre-2026) or as `[UNVERIFIED]` listing titles are deliberately **not** in `references.bib` (29 such IDs). 2025 items used as kill-test evidence or as likely baselines are in the bib as `[BACKGROUND]`.

## Open questions for the supervisor
See `ml_stock_topics_2026.md` → "Questions for the supervisor" (8 questions) and each card's item 13.

## Unverified leads (to check)
- Padova MSc thesis: lead/lag detection as temporal link prediction (thesis.unipd.it handle 20.500.12608/81805) — date and content unverified; closest prior art for Card 1.
- DatedGPT model weights availability (only a web demo confirmed).
- SEC Rule 17g-7(b) XBRL rating histories — format/access.
- S&P 500 point-in-time membership source; Stooq/yfinance coverage of OTC tickers.
- 2610.24544 (TimeGAN Rachev portfolio) — rate-limited, not opened.

## Status / where I stopped (2026-11-02)
- **Done:** Phase 0 (taxonomy, 12 areas) → Phase 1 (sweep of all 12 areas; ≈60 2026 items logged, ~50 `[ABS]`) → Phase 2 (crowding map + 11 gaps) → Phase 3 (18 raw ideas with kill tests; 6 full cards; 4 runners-up) → Phase 4 (morning summary, recommendation, supervisor questions). All committed and pushed to branch `scouting-ml-stock-2026`.
- **Not done / limits:** no full texts opened (`[FT]` = 0) — breadth first by design; Google Scholar and arXiv search blocked (logged once, not retried); per-area counts are a sample, not a census; most `[ABS-s]` items should be upgraded to `[ABS]`/`[FT]` before citing in the proposal.
- **Next session:** (1) after the supervisor picks a direction, open full texts of the 4–6 closest papers for the chosen card; (2) phase-1 literature review for that card, including 2025 baselines if the supervisor allows; (3) data-availability checks (list above); (4) prototype code.

## 2026-11-04 — Future-work scan
- Read conclusion/limitations sections (arXiv HTML full text) of 18 papers → `future_work_scan.md`. Verification for these upgrades to `[FT-c]` (full text opened, conclusion/limitations read). 2610.15144 not reached (HTML ~850k chars).
- Resolved lead: DatedGPT checkpoints are on Hugging Face (hf.co/datedGPT), per the paper's abstract.
- Takeaways: IDP-DSN authors name sign reversals + larger real-world data + heterogeneous signed interactions as future work (supports Card 1); Huang et al. and Yılkı name dynamic graphs and chronologically consistent LLMs (supports Card 2); RegimeRank wants LLM narratives of attributions without validating them (supports Card 3); Chen & Hybinette name graph-based edge-anomaly detection (supports Card 6). No paper names credit-event→equity contagion (Card 4 gap unchanged).
