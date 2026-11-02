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
