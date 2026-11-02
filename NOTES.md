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

## Access tests

(see below, filled in during Phase 1)

## Search queries log

(per area, filled in during Phase 1)
