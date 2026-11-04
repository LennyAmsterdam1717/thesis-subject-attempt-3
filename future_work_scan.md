# Future-work scan of the 2026 lit review (4 Nov 2026)

Purpose: check what the authors of the most relevant papers in `lit_review_ml_stock_2026.md` say about **future work, open problems and limitations**, and map that onto the six topic cards (`ml_stock_topics_2026.md`).

Method: read the conclusion / discussion / limitations sections of the arXiv HTML full text (verification `[FT-c]` = full text opened, conclusion and limitations sections read; rest of the paper only skimmed by the fetch tool). 18 papers covered. Not reached: 2610.15144 (Liang, Zohren & Cucuringu; the HTML is ~850k characters and the conclusion was not within the first 300k).

Everything below is paraphrased from the authors. "→" lines are my reading of what it means for Frank.

## Card 1 — SignFlip (signed lead-lag link prediction)

| Paper | What the authors say is open | → Relevance |
|---|---|---|
| **IDP-DSN** (Hou et al., SIGIR 2026, 2604.18213) | Let positive and negative channels interact earlier, to capture **sign reversals**; richer edge-weight features; adaptive time decay; **apply to larger real-world data**; extend to **heterogeneous** signed interactions. Tested only on Bitcoin-OTC/Alpha trust, Wiki-RfA, Epinions. | Strongest support. Applying this method to signed lead-lag stock graphs is exactly their own "larger real-world data" + "sign reversal" agenda; heterogeneous extension = sector/industry node types. |
| **Fanshawe et al.** (2601.04602) | Compare against LSTM/CNN/other GNNs; test on global equities and crypto; replace classifier filter with deep models; combine attention with attribution methods. Admit: no slippage, one hyperparameter setting, replication gap. | Their missing baselines and single market are easy, defensible improvements in Card 1. |
| **Guo** (2609.08106) | Main direction: **cross-stock mechanisms that sharpen differences between stocks instead of averaging them**; whether the near-uniform attention is general beyond MASTER and Chinese A-shares; why cross-stock benefits vanish at large universes. Admit frictionless Sharpe, single model and market. | Reinforces predicting *relations* (sparse, signed, directed) rather than adding attention to return models. |
| **CorrFlow** (Marti, 2610.13606) | Explicitly does **not forecast the next correlation matrix**; calls for temporal benchmarks with observation-disjoint splits; separate true dependence from estimator noise of overlapping windows; transfer to S&P 500 not established. | Your graph-construction step needs the same care (overlapping windows inflate apparent persistence). Forecasting next-period networks is confirmed open. |
| **Deng & Zhang** (2608.24703) | Tailor the lead-lag matrix to each clustering method; try HDBSCAN on MiniRocket features; soft voting weighted by silhouette scores. Data: CRSP. | Minor; shows lead-lag work is still unsupervised clustering, not prediction. |
| **ORCA** (Kriuk & Kriuk, 2604.17251) | Extend to international markets and other asset classes; online/adaptive models; intraday correlation; live paper trading. Authors **deliberately avoided graph neural networks** in favour of tree ensembles. | Learned temporal-graph models on correlation-network regimes are left open by them. |

## Card 2 — Time-honest LLM company graphs

| Paper | What the authors say is open | → Relevance |
|---|---|---|
| **Huang et al.** (2604.19476) | **Dynamic, higher-frequency graphs** instead of one static graph per year; multi-source edge classification (news, supply-chain data); better text extraction; **feed the LLM-refined graph into a GNN** end to end. They anonymise firms to reduce LLM memorisation but do not measure it. | Their future work *is* Card 2's design (dynamic typed graph + learnable model); the leakage measurement is still yours. |
| **Yılkı** (2606.29290) | KG is manually built, covers part of S&P 500 and is **static**; wants **time-varying network**; suggests **chronologically consistent LLMs (ChronoBERT/ChronoGPT)** against look-ahead; accounting controls. KG built from public filings/disclosures but not released. | Direct support: time-varying + look-ahead-free LLMs named as the next step. |
| **Fukada & Mizuno** (2605.27845) | Validate economic importance of edges (does the link actually propagate shocks?); absent edge ≠ no relation; **entity resolution is the bottleneck** (proposes vector retrieval + small LM); product taxonomies; other countries. **Do not** mention temporal updating, market use or link prediction. | Entity resolution is the main practical risk of Card 2 — plan for it. Market relevance + temporal link prediction remain unclaimed. |
| **TRACE** (Ding et al., 2603.12500) | Only admitted limitation: dependence on **KG coverage and drift**; future: multi-horizon, confidence calibration, other markets. KG sources/vendors not named, not released. | "KG drift" is the time-honesty problem in other words. |
| **DatedGPT** (Yan et al., 2603.11838) | No conclusion section in the HTML. **Release: twelve year-cutoff checkpoints on Hugging Face (hf.co/datedGPT)** plus DatedInstruct; pretraining data filtered from FineWeb-Edu. | Resolves an open data question: date-cutoff models for Card 2 are available. |

## Card 3 — Faithfulness of graph explanations

| Paper | What the authors say is open | → Relevance |
|---|---|---|
| **RegimeRank** (Koa et al., ICAIF 2026, 2610.26456) | Turn rankings into portfolios after costs; add sentiment; **use LLMs to turn SHAP/attention attributions into plain-language rationales**. No limitation or future work on whether the attributions are faithful. | Clear gap: the field is moving to *communicating* explanations (LLM narratives) before *validating* them. Good motivating example for Card 3. |
| **Fanshawe et al.** (2601.04602) | Combine attention with Integrated Gradients, DeepLIFT, SHAP, Gradient×Input. | Acknowledges attention ≠ explanation, does not test which method is faithful. |
| **Guo** (2609.08106) | Interpretation of the attention pattern labelled "preliminary". | Same gap. |

## Card 4 — Credit-event contagion

| Paper | What the authors say is open | → Relevance |
|---|---|---|
| **Duong et al.** (2610.37487, European banks) | Independent shock measurements and richer exposure data to strengthen identification; higher-frequency data; robustness to other causal-discovery algorithms. Sample = currently listed banks only (survivorship). | Nothing on credit events; confirms equity-network causal work is still mostly about banks and contemporaneous shocks. |
| **Thumm & Chen** (2610.12537) | Many open items on causal foundation models for market impact; **no mention of spillovers between firms**. | Causal PFN idea for firm-to-firm spillovers is unclaimed but far from Card 4's scope. |

No paper in the review discusses credit-event propagation to equity as future work — consistent with the crowding map (gap G4).

## Card 6 — Coordinated manipulation detection

| Paper | What the authors say is open | → Relevance |
|---|---|---|
| **Chen & Hybinette** (2608.05373) | **Graph-based detection of spot–option decoupling as a cross-market edge anomaly** (named, not developed); contrastive representation learning to separate legitimate volatility from manipulation; streaming detection; triage of false positives. Admit precision ≈25%, incomplete positive-only labels, only two SEC-complaint tickers. | Authors themselves name the graph/edge-anomaly direction → supports Card 6, and their label problems show what to design for (positive-unlabelled evaluation). |
| **Losavio et al.** (crypto ST-GNN, 2604.24590) | No limitations or future-work section. | Nothing to add. |

## Runner-up R1 — graph-guided context for time-series foundation models

| Paper | What the authors say is open | → Relevance |
|---|---|---|
| **Das, Goyal & Yadav** (2605.21504) | Bigger "world" panel (macro, commodities, international); conformal calibration; hybrid econometric + foundation-model embeddings. **No method for choosing which related series to include**, although noisy co-series hurt. | Selection-of-context gap stays open. |

## Recurring limitations across the 18 papers
- Single market (mostly US or China) and single model family: Fanshawe, Guo, ORCA, Das, RegimeRank, Chen & Hybinette.
- Transaction costs / slippage ignored or simplified: GAPNet, Guo, Fanshawe, ORCA, TRACE.
- Static graphs where relations change: Huang, Yılkı, Fukada & Mizuno, TRACE ("KG drift").
- Attention or SHAP presented as explanation without validation: Fanshawe, Guo, RegimeRank.
