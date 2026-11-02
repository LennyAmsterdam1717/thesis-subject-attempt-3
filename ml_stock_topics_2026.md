# Thesis topics: ML × stock market / listed companies (2026 scouting)

<!-- PHASE 4 SUMMARY GOES HERE -->

---

## 1. Raw ideas and kill tests (Phase 3)

Each idea came from a gap in the crowding map (`lit_review_ml_stock_2026.md`, G1–G11). Each was searched for directly ("kill test"). Verdicts: **survived** (no close prior work found) · **weakened** (related work exists; a differentiated angle remains) · **killed** (done already, or infeasible under the constraints). Queries are logged in `NOTES.md`. Kill-test hits that are not 2026 are listed as evidence only (they can kill an idea but do not count as 2026 literature).

| # | Raw idea | Gap | Kill-test hits (closest) | Verdict |
|---|---|---|---|---|
| I1 | **Temporal signed lead-lag link prediction**: forecast which directed, signed influence edges between stocks switch on/off or flip sign next period | G1 | A1-1 Fanshawe 2026 (undirected correlation forecasting, no sign events); Padova MSc thesis (lead-lag as temporal link prediction, unsigned, date unknown) `[UNVERIFIED]`; 2602.12663 (dynamic signed weighted link prediction, social data); IDP-DSN (SIGIR 2026, platform data); MSGNN/FiLL (2022, static per year) | **Survived (weakened slightly)** |
| I2 | Forecast structural events in correlation networks (cluster splits, sign flips) | G1/G11 | A1-1; U-GNN graph-signal diffusion on S&P 500 (2607.06833, `[ABS-s]`) | Merged into I1 |
| I3 | **Faithfulness audit of explanations from temporal stock-graph models** | G2 | Azzolin et al. ICLR 2026 (general, molecules/synthetic); no financial application found | **Survived** |
| I4 | **Point-in-time LLM-built company graphs**: measure and remove look-ahead when LLMs extract firm relations; then predict typed edges over time | G3 | finnlp 2025 zero-shot LLM relation graphs from model memory (leak-prone, not tested for it); Köse et al. 2605.15842 (LLM + web archives, temporal semiconductor network, no look-ahead test); A1-4, A12-1; DatedGPT (A3-3) gives the tool | **Survived** |
| I5 | **Credit-event contagion to linked firms' equity** with graph learning on public filings | G4 | Das et al. CorpNet (credit ratings from SEC-filing graph; older, predicts ratings not equity); Brogaard & Chen 2026 (CDS, paid data) `[UNVERIFIED]`; Alldredge et al. 2022, Kolay et al. 2016 (event studies, no ML) | **Survived** |
| I6 | **Cross-stock (network) manipulation detection** using SEC litigation releases as labels | G5 | A9-1 Chen & Hybinette 2026 (single-asset, SEC v. Patel labels); A9-3 crypto ST-GNN; SEC litigation releases name target tickers (verified on sec.gov examples) | **Survived** (data risk) |
| I7 | **Is the learned graph meaningful?** Compare graphs learned by stock models (attention/structure learning) with real relations | G6 | 2606.08468 (graphical-model selection vs competitor/customer relations, `[ABS-s]`); Pu et al. 2023 L2G; A1-5 (attention ≈ uniform) | **Weakened** |
| I8 | Empirical footprint of AI-agent herding in co-movement networks | G7 | GeomHerd 2605.11645 (simulated LLM agents); Fed lab study 2026 (AI herds less); no way to label AI-driven trades in public data | **Killed** (identification infeasible) |
| I9 | Graph-guided context selection for TSFMs (which co-series Chronos-2 sees) | G8 | A2-2 (shows mixing hurts, no selection method); none found | Survived, but **fails gate** (objective is still return forecasting) → runner-up |
| I10 | Cross-market transfer (AEX/Euronext vs US) of temporal graph models | G9 | Few 2026 EU studies (A5-5, A8-2) | Survived as an **add-on** to I1/I3, not standalone |
| I11 | Anytime-valid (e-value) inference on lead-lag edges | G10 | A6-3 (factors); e-value multiple-testing literature (2024–25); Toyoda & Uematsu 2024 (FDR network exploration) | **Weakened**; too statistics-heavy for fit → absorbed as evaluation tool in I1 |
| I12 | Conditional generation of next-period correlation networks | G11 | CorrFlow (A7-1, unconditional); A1-1; 2607.06833 | **Weakened** → absorbed into I1 baselines |
| I13 | Temporal link prediction of supply-chain edges between listed firms | G1 | GDES 2508.12044 (2025, 88k Chinese firms, AUC 94%); Leskovec et al. TPG (AAAI 2025); Köse et al. 2026 | **Weakened** → merged into I4 |
| I14 | 13F common-ownership link prediction | G1 | **2607.12067 Izadifar & Rahmati (Jul 2026): TGB benchmark on 13F holdings, persistence baseline almost unbeatable** | **Killed** |
| I15 | Tariff/geopolitical shock propagation through firm networks to returns | G4/G9 | Andreou et al. 2025 (ML on 10-K tariff risk, Liberation Day); Han et al. Economics Letters 2026 (tariff exposure index); RIETI Arata 2026 (GNN shock propagation, Japanese transaction data) | **Weakened** → runner-up |
| I16 | Structural-balance early-warning from signed stock networks | G1/A9 | 2608.12023 Dahake & Chakraborty (Aug 2026, sectoral balance loss); 2512.10606, 2407.14272; ORCA (A9-2) | **Killed** as standalone (feature inside I1) |
| I17 | Graph-aware risk layer for LLM trading agents (agents ignore cross-asset dependence) | A4-5 | TradeArena (A4-5) documents the blind spot; no fix found | Survived, weak supervisor fit → runner-up |
| I18 | Leak-free re-evaluation of 2025–26 stock-graph SOTA | A11 | A11-5 leakage-controlled benchmark incl. inter-stock graphs (Zenodo 2026); A1-5; A11-4 | **Killed** as standalone (now done in part) |

Survivors used for cards: I1, I4, I3, I5, I7, I6. Runners-up: I9, I15, I17, I10.

---

## 2. Full proposal cards

Scoring (briefing §9): Novelty ×3, Supervisor fit ×2, Data ×2, Feasibility ×2, Evaluation clarity ×1, AI relevance ×1, Artefact ×1, Industry/Accenture ×1, Frank's interests ×1. Max = 70.

### Card 1 — SignFlip: forecasting when signed lead-lag influence edges between stocks switch on, off or flip *(I1)*

**1. Pitch.** Treat the market as a temporal, directed, *signed* graph of lead-lag influence (A moves → B follows, same or opposite direction) and make the *edges themselves* the prediction target: which influence edges will be active, absent, or flip sign next month — evaluated like a temporal-graph benchmark, then checked for economic value.

**2. Research question.** Can temporal signed-graph learning forecast the activation, deactivation and sign flips of lead-lag influence edges among listed stocks better than persistence and statistical baselines, without look-ahead?
- SQ1: How persistent are signed lead-lag edges, and which edge/node features (sector, size, liquidity, past sign history, structural balance of triads) predict flips?
- SQ2: Do 2026 dynamic signed-network methods (e.g. IDP-DSN) beat strong persistence / exponential-smoothing baselines on market graphs, as they do on social graphs?
- SQ3: Does a portfolio that only trades on *forecast* active edges beat one using last period's lead-lag graph, after transaction costs?

**3. Supervisor directions hit.** Temporal ✔ · **signed, time-activated influence edges + time series** ✔ (her capitalised point) · **link prediction** ✔ · anomaly (sign-flip bursts as regime signals) ◐ · heterogeneous (sector/industry node types optional) ◐.

**4. Closest 2026 work and the difference.**
- A1-1 Fanshawe et al. (2601.04602) `[ABS]`: forecasts undirected 10-day correlations; signed only as an edge feature; no directed lead-lag, no sign-flip events, no link-prediction protocol.
- A1-7 IDP-DSN (2604.18213, SIGIR 2026) `[ABS-s]` and 2602.12663 `[ABS-s]`: dynamic signed edge prediction — on online platforms, never on markets. This thesis *transfers and stress-tests* them on market networks.
- A8-1 Deng & Zhang (2608.24703) `[ABS]`: clusters lead-lag structure statistically; no forecasting of edges.
- A1-5 Guo (2609.08106) `[ABS]`: shows cross-stock modules do not help *return* prediction at scale → motivates predicting the *graph* instead of returns.
- Background only: MSGNN/FiLL datasets (He et al. 2022) — yearly static signed lead-lag graphs.

**5. Kill test.** Queries in NOTES.md (I1). Closest hits: a Padova MSc thesis framing lead/lag detection as temporal link prediction (unsigned, not peer-reviewed, date unverified) and a 2026 BSIC student blog comparing lead-lag graphs inside GNNs. No peer-reviewed or arXiv 2026 work forecasts *signed, directed* lead-lag edge dynamics on equities. → **Survived; must cite and differentiate from the Padova thesis** (signed + flips + leak-free protocol + economic test).

**6. Data.** Daily adjusted prices of S&P 500 constituents (point-in-time membership needed against survivorship — Wikipedia change log or a public constituents history on GitHub; to verify) and optionally AEX/Euronext (G9). Sources: Stooq / `yfinance` (terms to check) — downloads must happen outside the cloud sandbox (allowlist). Sector: SEC SIC codes (EDGAR, free). Access risk: **low**; survivorship handling is the main care point.

**7. Method sketch.** (i) Rolling windows (e.g. 60 trading days, monthly step) → lead-lag matrix per window via lagged regression / cross-correlation (as in FiLL) on market-residual returns; significance filter (FDR) → signed directed snapshot graphs. (ii) Task per pair: {none, +, −} next window (3-class, like IDP-DSN). (iii) Models: persistence; EWMA of past signs; logistic/GBM on pair features; static signed GNN (MSGNN via PyTorch Geometric Signed Directed — library exists); temporal models (TGN / DyRep via TGB tooling; IDP-DSN official code). Existing code: PyG Signed Directed `[BACKGROUND]`, TGB, IDP-DSN GitHub.

**8. Baselines & evaluation.** Chronological train/val/test by window; no pair feature computed with data past the window end; embargo between windows. Metrics: macro-F1 and AUC per class, MRR with TGB-style negative sampling, sign-flip recall. Economic test: lead-lag long-short using forecast vs last-period graph, net of 10–20 bps costs. Statistical test: Diebold–Mariano style or block bootstrap.

**9. Artefact.** "Influence radar" dashboard: for a chosen stock, the forecast leaders/laggers next month with sign and confidence; edges flagged as likely to flip (Streamlit / Plotly).

**10. Feasibility (30 weeks).** Weeks 1–8 lit review + data pipeline; 9–14 graph construction + baselines; 15–22 temporal/signed models; 23–26 economic test + dashboard; 27–30 writing. Risks: (a) lead-lag edges are mostly noise → low predictability; (b) TGB-style models expect event streams, need snapshot adaptation. Fallback: restrict to sector-level or ETF-level graphs (fewer, stronger edges), or predict only *sign flips of persistent edges*.

**11. Ethics.** Company-level nodes only; public prices; no personal data. Disclose GenAI coding assistance.

**12. Scores.** Novelty 4 (×3=12) · Fit 5 (×2=10) · Data 5 (×2=10) · Feasibility 4 (×2=8) · Evaluation 5 · AI relevance 5 · Artefact 4 · Industry 3 · Frank's interests 4 → **61 / 70**.

**13. Questions for the supervisor.** Is a 3-class signed link-prediction framing acceptable, or does she prefer a continuous edge-weight target? Daily or intraday lead-lag? Does UU have WRDS/CRSP access for survivorship-free prices? Would she accept the Padova thesis as "prior art" to beat?

### Card 2 — Time-honest company graphs: measuring and removing look-ahead in LLM-built firm-relation graphs, then forecasting new edges *(I4 + I13)*

**1. Pitch.** In 2026 LLMs started building company graphs (competitor, supplier, partner) from 10-Ks and the web — but a modern LLM already "knows" which relations formed later. This thesis measures that leakage, builds a point-in-time typed company graph from EDGAR, and uses it for temporal link prediction of new relations.

**2. Research question.** How much future information leaks into company-relation graphs extracted by LLMs, and does a point-in-time (date-restricted) extraction change downstream conclusions about predicting new inter-firm relations and their market relevance?
- SQ1: Does a frontier LLM, asked only for "relations of firm X as of year t" (no document), recall relations first disclosed after t? (date-only recall probe, adapted from the lookahead-test idea)
- SQ2: How do graphs from (a) model memory, (b) document-grounded extraction from 10-Ks filed ≤ t, (c) date-cutoff LMs differ in edge precision against 10-K disclosed customers/competitors?
- SQ3: Can temporal heterogeneous link prediction forecast next-year typed edges, and do leaked graphs inflate its scores?

**3. Supervisor directions hit.** Link prediction ✔ · heterogeneous (typed edges: supplier, customer, competitor, partner) ✔ · temporal ✔ · text analysis & knowledge networks ✔ (her expertise) · time series ◐ (market relevance test).

**4. Closest 2026 work and the difference.**
- A1-4 Huang et al. (2604.19476) `[ABS]`: LLM types edges of a 10-K similarity graph — no leakage check, annual static graph, no edge prediction.
- A12-1 Fukada & Mizuno (2605.27845) `[ABS-s]`: LLM supply-chain KG from search snippets (China) — snapshot, no time honesty.
- Köse et al. (2605.15842) `[ABS-s]` — temporal multi-relational semiconductor network from web archives with LLM extraction; validates precision, but does not test LLM memory leakage and does not do link prediction.
- A3-3 DatedGPT (2603.11838) `[ABS]` and A3-7 time-capsule checkpoints `[ABS]`: tools and evidence that LLM knowledge cutoffs matter for *returns* — not yet applied to *graph construction*.
- Evidence outside 2026: FinNLP 2025 zero-shot LLM relation graphs built purely from model memory (exactly the leak-prone design).

**5. Kill test.** Queries in NOTES.md (I4, I13). No work found that quantifies look-ahead in LLM-extracted firm graphs. Supply-chain link prediction itself is done in 2025 (GDES 2508.12044; Leskovec TPG, AAAI 2025) on proprietary/Chinese data → the novelty is the **time-honesty angle + public EDGAR data**, not link prediction alone. → **Survived.**

**6. Data.** SEC EDGAR 10-K Item 1 / Item 1A text, and 10-K customer disclosures (major-customer mentions) — free, bulk; EDGAR full-text search for validation. Wikidata (owned-by, industry) as weak ground truth. Date-cutoff models: DatedGPT checkpoints (availability of weights **unverified**; demo at datedgpt.com) or older open models with known cutoffs (e.g. FinBERT-era). Access risk: **low–medium** (LLM API costs for extraction; few-thousand-firm scale is cheap).

**7. Method sketch.** (i) Universe ≈ 500–1,500 US firms, 2012–2025. (ii) Three graph builders: memory-only prompting; RAG over 10-Ks filed ≤ t (point-in-time); date-cutoff LM. (iii) Leakage score per edge = was it recalled before its first disclosure date? (iv) Temporal heterogeneous link prediction (R-GCN / HGT with time snapshots in PyG; TGB-style evaluation) trained on each graph version. (v) Market relevance: does a newly predicted supplier/customer edge forecast increased return co-movement? (cross-check with Card 1 machinery).

**8. Baselines & evaluation.** Edge precision/recall against 10-K-disclosed relations (hand-checked sample of 200 edges for gold). Link prediction: MRR/Hits@k on year t+1 edges, chronological split, filtered negatives; baselines: common neighbours, Adamic-Adar, persistence. Key comparison: inflated score with leaked graph vs point-in-time graph.

**9. Artefact.** "Time-honest company graph explorer": pick a date, see the graph as knowable at that date, with each edge's source sentence and first-disclosure date; flagged edges where the LLM "knew too early".

**10. Feasibility.** Medium. Weeks 1–8 lit + EDGAR pipeline (edgartools / sec-edgar libraries); 9–16 extraction + leakage probes; 17–23 link prediction; 24–30 artefact + writing. Risks: entity resolution of firm names; LLM cost; noisy ground truth. Fallback: restrict to one sector (e.g. semiconductors, where Köse et al. offer a comparison) and to the leakage study (SQ1–2) only.

**11. Ethics.** Firms only; no executives. LLM use disclosed; no proprietary data. Note LLM provider terms for research use.

**12. Scores.** Novelty 4 (12) · Fit 5 (10) · Data 4 (8) · Feasibility 3 (6) · Evaluation 4 · AI relevance 5 · Artefact 4 · Industry 5 (Accenture GenAI/knowledge-graph work) · Interests 4 → **58 / 70**.

**13. Questions for the supervisor.** Is the leakage measurement a strong enough contribution even if link prediction is modest? Does her group have entity-resolution tooling from the ING/SPIN work? Preference for RAG over raw filings vs prompting?

### Card 3 — Do stock-graph explanations explain? A faithfulness audit of temporal graph models for markets *(I3)*

**1. Pitch.** Stock-graph papers routinely show attention maps and "important neighbours" as explanations. 2026 graph-XAI research shows such explanations can be degenerate yet pass standard faithfulness metrics. This thesis builds a controlled audit for temporal stock-graph models: synthetic markets with planted influence edges plus real data, testing whether explanations recover the edges the model actually uses.

**2. Research question.** Are edge-level explanations of temporal stock-graph models (attention weights, GNNExplainer-type masks, probing) faithful to the model and to the true influence structure?
- SQ1: In synthetic markets with planted signed lead-lag edges, which explanation methods recover the planted edges, and which faithfulness metrics detect when they do not?
- SQ2: On real data (S&P 500, optionally AEX), do explanations agree across seeds, methods and adjacent time windows?
- SQ3: Can a cheap "explanation sanity check" be proposed for analysts (an AI-Act-style transparency test)?

**3. Supervisor directions hit.** Temporal ✔ · graph + time series ✔ · signed influence (planted edges) ✔ · anomaly ◐ (explanation instability as a warning) · link prediction ✘. Fit with Frank's XAI/AI-Act background ✔✔.

**4. Closest 2026 work and the difference.**
- A10-4 Azzolin et al. (ICLR 2026, arXiv 2601.20815) `[ABS-s]`: unfaithful-but-undetected explanations in self-explainable GNNs; new metric — general benchmarks, not temporal, not finance.
- A10-1 Liang, Zohren & Cucuringu (2610.15144) `[ABS]`: feature attribution for ML portfolios — features, not edges; no faithfulness test.
- A10-3 RegimeRank (2610.26456, ICAIF 2026) `[ABS]` and A12-2 TRACE (2603.12500) `[ABS]`: present attention/evidence chains as explanations, unvalidated.
- A8-4 Causal-INSIGHT (2603.25473, IJCNN 2026) `[ABS-s]`: probing a trained temporal predictor for the graph it uses — a candidate method to audit.
- A1-5 Guo (2609.08106) `[ABS]`: MASTER inter-stock attention is nearly uniform → a concrete case where attention-as-explanation is doubtful.

**5. Kill test.** Queries in NOTES.md (I3). No finance-specific faithfulness study of graph explanations found (2026 or earlier in results). → **Survived.**

**6. Data.** Synthetic: simulated returns with planted signed lead-lag graph (Card 1 generator; or VAR with sparse signed coefficients). Real: S&P 500 daily prices (Stooq/yfinance) + sector codes. Access risk: **low**.

**7. Method sketch.** Models: GAT-based temporal model, MASTER-style inter-stock attention (official code exists for MASTER `[BACKGROUND]`, to check), a simple temporal GCN. Explainers: attention, GNNExplainer/PGExplainer (PyG `torch_geometric.explain`), integrated gradients on edge masks, Causal-INSIGHT-style clamping. Metrics: fidelity+/−, Azzolin et al.'s metric, planted-edge recall, stability (Jaccard across seeds/windows).

**8. Evaluation.** Ground truth exists in synthetic data → precision/recall of explanations; on real data, agreement/stability metrics + sanity checks (randomised-model test, label-shuffle test). Chronological splits for real-data models.

**9. Artefact.** "Explanation reliability panel" for an analyst view: for each prediction, the explanation + a reliability badge (passes/fails sanity checks).

**10. Feasibility.** Good — mostly existing libraries. Weeks 1–8 lit; 9–14 simulator + models; 15–22 explainers + metrics; 23–30 real data, artefact, writing. Risk: result could be "all explainers fail" — still publishable as an audit. Fallback: synthetic-only plus one real dataset.

**11. Ethics.** No personal data. Strong link to AI Act transparency for high-risk/financial uses — discuss carefully (stock prediction itself is not an AI-Act high-risk category; frame as good practice).

**12. Scores.** Novelty 4 (12) · Fit 3 (6) · Data 5 (10) · Feasibility 4 (8) · Evaluation 4 · AI relevance 5 · Artefact 4 · Industry 4 · Interests 5 → **58 / 70**.

**13. Questions for the supervisor.** Is an XAI-audit thesis "network analysis" enough for her? Would she co-supervise with an XAI person (e.g. UU's explainability group)? Synthetic-heavy design acceptable?
