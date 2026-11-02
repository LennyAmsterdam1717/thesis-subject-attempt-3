# Literature landscape: machine learning × stock market / listed companies (2026 only)

*Scouting run, 2 November 2026. Only work first published or first posted in 2026. Older work appears only as `[BACKGROUND]` (dataset/library origin) or in the "excluded" notes.*

**Legend.** `[FT]` full text opened · `[ABS]` arXiv/publisher abstract page opened with the fetch tool · `[ABS-s]` abstract page content seen inside a search result (date and abstract visible, page not fetched separately) · `[UNVERIFIED]` named in a search result only, not relied on.
All numbers below are as reported in the abstract; check against the PDF before thesis use.
Date = arXiv v1 date unless stated. "PR" = peer-reviewed, "pre" = preprint.

<!-- CROWDING MAP (Phase 2) goes here -->

---

## A1. Graph & relational learning on stocks

**A1-1. Fanshawe, Masih & Cameron — *Forecasting Equity Correlations with Hybrid Transformer Graph Neural Network*.** <https://arxiv.org/abs/2601.04602> · 2026-01-08 · pre (q-fin.CP) · `[ABS]` (+ graph-building section seen in PDF via search)
- Summary: predicts 10-day-ahead pairwise correlations (Fisher-z residuals vs. a rolling baseline) for S&P 500 with a temporal-heterogeneous GNN; uses the forecasts to build trading baskets by graph clustering. The stock graph is explicitly **signed** (top/bottom correlations as edges, sign as edge feature).
- Task: edge-weight (correlation) forecasting → clustering/portfolio. Data: S&P 500 prices + sector + macro (public-obtainable). Code: none stated.
- Leaves open: correlation *edges* as the prediction target is rare — no sign-flip/regime analysis, no lead-lag (directed) edges, single market.

**A1-2. Niu, Lu, Jin & Dong — *GAPNet: Plug-in Jointly Learning Task-Specific Graph for Dynamic Stock Relation*.** <https://arxiv.org/abs/2602.00888> · 2026-01-31 · pre (cs.LG) · `[ABS]`
- Summary: plug-in that rewires graph/hypergraph backbones (RT-GCN, CI-STHPAN) by learning task-specific topology end-to-end; reports higher returns/Sharpe.
- Task: return forecasting/portfolio via learned graph. Data: two unnamed stock datasets. Code: none stated.
- Leaves open: whether the learned graph means anything economically; no comparison to real company relations.

**A1-3. Gregnanin, De Smedt, Gnecco & Parton — *The Statistical Significance of the Inclusion of Graph Neural Networks in the Financial Time Series Forecasting Problem*.** <https://arxiv.org/abs/2605.21192> · 2026-05-20 · pre (cs.CE) · `[ABS]`
- Summary: "Time-Geometric" model; tests whether adding GNN geometry improves univariate forecasts and claims statistically significant gains.
- Task: forecasting + significance testing. Data: not named in abstract. Code: none stated.
- Leaves open: contrasts with A1-5 (no gain at scale) — the literature disagrees on whether graphs help at all.

**A1-4. Huang, Fan, Hu & Ye — *Cross-Stock Predictability via LLM-Augmented Semantic Networks*.** <https://arxiv.org/abs/2604.19476> · 2026-04-21 (v2 04-26) · pre (q-fin.PM) · `[ABS]`
- Summary: candidate graph from 10-K embedding similarity; an LLM classifies each edge (competitor, supply chain, complementary, substitute, peer, unrelated) and prunes; typed graph aggregates pair mean-reversion signals into stock signals; better long-short Sharpe and drawdown.
- Task: graph construction (LLM edge typing) + cross-stock signal. Data: S&P 500, 2011–2019, SEC 10-K (public). Code: none stated.
- Leaves open: no edge-level ground truth for LLM edge labels; annual (slow) graph; no temporal link prediction; US only.

**A1-5. Guo — *Nyström Attention Matches Full Attention for Cross-Sectional Stock Prediction*.** <https://arxiv.org/abs/2609.08106> · 2026-09-08 · pre (cs.LG/q-fin.ST) · `[ABS]`
- Summary: dissects MASTER's inter-stock attention: nearly uniform; low-rank Nyström attention matches it. Graph-based alternatives degraded performance, and at ~3,500 stocks no cross-stock module beat a per-stock LSTM.
- Task: cross-sectional prediction (Rank IC) + mechanism analysis. Data: universes of ~300/800/3,500 stocks (unnamed). Code: none stated.
- Leaves open: **strong negative evidence for "graph helps prediction" at scale** → supports moving graph work away from return prediction.

**A1-6. Adhikari — *Signed network models for dimensionality reduction of portfolio optimization*.** <https://arxiv.org/abs/2602.21362> · 2026-02-24 · pre (math.CO) · `[ABS-s]`
- Summary: daily complete signed graphs from relative return behaviour; uses structural-balance properties to reduce portfolio optimisation; extension of a 2025 preprint.
- Task: portfolio construction with signed graphs (no learning). Data: asset returns. Code: none stated.
- Leaves open: no learning, no prediction of how signed structure evolves.

**A1-7 (method, not finance). Hou, Huang, Ran & Jia — *Inductive Dual-Polarity Modeling via Static–Dynamic Disentanglement for Dynamic Signed Networks* (IDP-DSN).** <https://arxiv.org/abs/2604.18213> · 2026-04-20 · PR (SIGIR 2026, per PDF header) · `[ABS-s]`
- Summary: dynamic signed edge prediction (none / positive / negative) with sign-selective memories; inductive cold-start setting. Code: <https://github.com/codewhisperer-rs/IDP-DSN>.
- Relevance: a ready-made 2026 method for **temporal signed link prediction**; evaluated on online-platform data only — not on market networks.

**A1-8 (method, not finance). Sung, Jee & Lee — *A Scalable Inter-edge Correlation Modeling in CopulaGNN for Link Sign Prediction*.** <https://arxiv.org/abs/2601.19175> · 2026-01-27 · PR (ICLR 2026, per comments) · `[ABS-s]`
- Summary: models correlation between edges for link-sign prediction at scale. Static graphs. Relevance: signed-link-prediction baseline family; not applied to finance.

Excluded (not 2026): MSGNN / FiLL lead-lag datasets (He et al., LoG 2022) → `[BACKGROUND]` dataset source for signed directed lead-lag networks, <https://arxiv.org/abs/2209.00546>. DeltaLag (arXiv 2511.00390, Nov 2025), Hermes (2509.23668), MaGNet (2511.00085), H3M-SSMoEs (2510.25091) are 2025. NIST-GNN (Quantitative Finance 26(1), 2026) has a 2025 DOI (online first 2025) → excluded `[UNVERIFIED]`.

## A2. Time-series foundation models & deep forecasting

**A2-1. Noguer i Alonso & Pereira Franklin — *Pretrained Time-Series Foundation Models for Financial Return Forecasting*.** <https://arxiv.org/abs/2606.27100> · 2026-06-25 · pre (q-fin.MF) · `[ABS]`
- Summary: pretrained TSFMs vs. from-scratch nets on 5 large US stocks with rolling-origin evaluation and Diebold–Mariano tests; TSFMs rank high but gains over random walk are small and rarely significant.
- Task: return forecasting (evaluation study). Data: AAPL, AMZN, GOOG, JPM, META (public prices). Code: none stated.
- Leaves open: only 5 stocks; no cross-section, no relational information.

**A2-2. Das, Goyal & Yadav — *Multivariate Financial Forecasting using the Chronos Time Series Foundation Models*.** <https://arxiv.org/abs/2605.21504> · 2026-05-08 · pre (q-fin.ST) · `[ABS]`
- Summary: Chronos-2 with multivariate vs. univariate context; multivariate context helps within equities or within rates, but mixing equities and rates hurts.
- Task: forecasting (prices/rates). Data: Magnificent-7, US Treasuries, 2000–2025 (public). Code: none stated.
- Leaves open: **which co-series to put in the context** is unsolved — i.e. a graph/selection problem (link to A1).

**A2-3. Bulut — *Conflicting History in Foundation Model Return Forecasts*.** <https://arxiv.org/abs/2610.25822> · 2026-10-19 · pre (q-fin.ST) · `[ABS]`
- Summary: with paired histories that differ only in older data, conflicting older history makes TSFM forecasts less likely to beat a zero forecast; simulation + exploratory 56-asset check.
- Task: forecasting robustness under regime change. Data: simulated + 56 assets. Code: none stated.
- Leaves open: regime-aware context selection for TSFMs.

**A2-4. Luo, Yi, Zhang & Sun — *STOCK-JEPA: Prior-Anchored Latent Revision Representation Learning in Equity Markets*.** <https://arxiv.org/abs/2610.07006> · 2026-10-04 · pre (cs.LG) · `[ABS]`
- Summary: JEPA-style self-supervised representations that learn revisions to a simple financial prior; evaluated by cross-sectional ranking and portfolios on China and US universes.
- Task: representation learning → return ranking. Code: none stated.
- Leaves open: still return prediction; representation interpretability.

`[BACKGROUND]` **Kronos** (Shi et al.), first posted 2025-08 (arXiv 2508.02739), published AAAI 2026 — open financial K-line foundation model, code <https://github.com/shiyu-coder/Kronos>. Named only as a library; not 2026-first-posted. Re(Visiting) TSFMs in Finance (arXiv 2511.18578, Nov 2025) excluded (2025).

## A3. LLMs for financial text → signals

**A3-1. Foley, Hartadi, Prakash, Takkallapalli & Vatsal — *Reading the News Without Hindsight: NoLBERT Topics and the Cross-Section of Stock Returns*.** <https://arxiv.org/abs/2610.22745> · 2026-10-15 · pre (q-fin.ST) · `[ABS]`
- Summary: compares four text readers (NoLBERT pretrained on pre-1996 text, LDA, MiniLM, FinBERT) × 8 forecasters on ~1.26M articles (2012–2024, top-1,000 US stocks); best combination's net Sharpe is not significant vs. a price-only benchmark after accounting for search.
- Task: cross-sectional return forecasting from news. Data: news corpus (availability not stated). Code: none stated.
- Leaves open: honest, look-ahead-free evaluation pipelines are rare; negative results.

**A3-2. Zheng — *More Mentions, Less Information? Diagnosing Identity and Alignment in Reddit Embeddings for Volatility Forecasting*.** <https://arxiv.org/abs/2610.25468> · 2026-10-18 · PR (ICAIF '26, per comments) · `[ABS]`
- Summary: WSB-post embeddings for realized-variance forecasting; most apparent gain is firm identity / firm-year information; text adds ~1.2% MSE reduction over HAR and nothing in 2020–2022.
- Task: volatility forecasting + diagnostic. Data: 202k stock-days 2015–2022 (Reddit; access not stated).
- Leaves open: identity-leakage diagnostics for any text→market model (method transfers to graph features too).

**A3-3. Yan, Tang, Gao, Jiang & Lu — *DatedGPT: Preventing Lookahead Bias in Large Language Models with Time-Aware Pretraining*.** <https://arxiv.org/abs/2603.11838> · 2026-03-12 (v2 07-23) · pre (cs.CL) · `[ABS]`
- Summary: twelve 1.3B LMs, each pretrained with a strict annual cutoff (2013–2024), plus instruction data; shows a measurable lookahead premium when training data cover the outcome period.
- Task: LLM pretraining for bias-free return prediction from headlines. Data: ~100B tokens per model; 61k firm-day headlines. Demo: www.datedgpt.com.
- Leaves open: **time-stamped models enable leak-free text→graph construction** (A12) — not yet used for that.

**A3-4. Iacovides, Hannibal, Zhou & Mandic — *FinLLM-KG: Knowledge Graph-Enhanced LLMs for Financial Sentiment Analysis in Algorithmic Trading*.** <https://arxiv.org/abs/2610.36083> · 2026-10-26 · pre (cs.CL) · `[ABS]`
- Summary: injects a 10-K-derived company knowledge graph into any causal LM at inference for company-aware sentiment; portfolio simulations improve over baseline.
- Task: sentiment + trading. Data: SEC 10-K (public); news set not specified.
- Leaves open: KG quality, temporal validity of the KG.

**A3-5. Yılkı — *Supply Chain Propagation of Textual Signals: LLM Embeddings and Cross-Sectional Return Predictability*.** <https://arxiv.org/abs/2606.29290> · 2026-06-28 · pre (q-fin.PR) · `[ABS]`
- Summary: FinBERT embeddings of 10-K MD&A for 255 S&P 500 firms (2011–2025), propagated over a supply-chain KG; network signal gives long-short Sharpe 0.86 and FF5 alpha.
- Task: cross-sectional prediction with text + graph. Data: 10-K public; supply-chain source not stated in abstract.
- Leaves open: source and timing of supply-chain edges; whether propagation is causal.

**A3-6. Kirtac — *Learning to Aggregate Zero-Shot LLM Agents for Corporate Disclosure Classification*.** <https://arxiv.org/abs/2603.20965> · 2026-03-21 (v2 04-30) · pre (q-fin.TR) · `[ABS]`
- Summary: several perspective-prompted zero-shot LLMs; logistic meta-classifier over labels, confidences and rationales beats single LLMs, voting, LLM-judge and FinBERT for next-day direction. Uses a post-LLM-release sample (Jan 2025–Mar 2026) to limit contamination.
- Task: disclosure classification → direction. Data: 9,860 US disclosures.
- Leaves open: very short test window; plain direction classification (crowded).

**A3-7. Lehner & Lopez-Lira — *ChatGPT as a Time Capsule: The Limits of Price Discovery*.** <https://arxiv.org/abs/2604.21433> · 2026-04-23 · pre (q-fin.GN) · `[ABS]`
- Summary: treats 12 frozen OpenAI checkpoints (2021–2025) as time-stamped summaries of public text; a sector-neutral LLM outlook score predicts analyst revisions and one-month returns (~7,000 US firms).
- Task: asset pricing with LLM checkpoints. Code: none stated.
- Leaves open: using checkpoint-dated LLMs to *build relation graphs* as of a date.

Excluded: Gao, Jiang & Yan, *A Test of Lookahead Bias in LLM Forecasts* (arXiv 2512.23847, first posted 2025-12-29) → 2025; relevant to A11 but outside the rule.

## A4. LLM agents & multi-agent trading

**A4-1. Kohli — *Decorrelating the Advice Layer: A Calibrated Fragility Metric and Tested Mitigations for Synchronized Liquidation in Agentic Wealth Management*.** <https://arxiv.org/abs/2610.37705> · 2026-10-26 · pre (q-fin.RM) · `[ABS]`
- Summary: agent-based model of AI advisory agents; model concentration drives security-level crowding, synchronised automation drives index tail losses; proposes a fragility index (hold-out R² 0.56) and mitigations (dispersed overlay parameters, staged execution).
- Task: simulation of systemic risk from correlated AI agents. Data: calibrated to 33 years of equity returns. Code: none stated.
- Leaves open: **empirical** detection of AI-agent herding in real market co-movement networks (link to A1/A9).

**A4-2. Chen, Xu, Chen, Lu & Jin — *Agent Policy-Value Audit: Separating Transition Composition from Event Selection in Financial LLM Agents*.** <https://arxiv.org/abs/2610.04040> · 2026-10-02 · pre (cs.AI) · `[ABS]`
- Summary: permutation-style audit that separates an LLM agent's returns into passive composition and true event-selection skill; applied to 723 earnings events at 44 US firms.
- Task: agent evaluation methodology. Code: none stated.
- Leaves open: audit tools for agents beyond earnings events; relational (cross-stock) selection skill.

**A4-3. Wang, Wang & He — *MintEval: Do LLMs Implement the Trading Strategy You Asked For?*** <https://arxiv.org/abs/2610.03080> · 2026-10-02 · pre (cs.SE) · `[ABS]`
- Summary: behavioural-equivalence benchmark (800 tasks) for natural-language→strategy code; scores bar-by-bar action match. Crypto data (BTCUSDT 15-min), method transfers. Code: <https://github.com/spearmintai/minteval>.
- Leaves open: equity version; multi-asset strategies.

**A4-4. Feng, Dai, Pan, Lau, Xu & Liu — *Governed Self-Evolution for Autonomous Investing: A Multi-Agent LLM System with an Invariant Core* (Steward).** <https://arxiv.org/abs/2610.30557> · 2026-10-22 · pre (cs.AI) · `[ABS]`
- Summary: nine-role multi-agent system with a protected core (order logic, risk rules) that self-edits prompts via nightly grading; 5-month live deployment + replay + 2015–2026 backtest. Code: <https://github.com/yebof/quant-agent>.
- Leaves open: short live window; governance evaluation is anecdotal.

**A4-5. Xue — *Representation Signatures and Risk-Feedback Alignment in LLM Trading Agents* (TradeArena).** <https://arxiv.org/abs/2605.28850> · 2026-05 (v2 2026-05-30) · pre (cs.LG) · `[ABS-s]`
- Summary: auditable trading-agent testbed with risk reports, execution simulation and replayable trajectories; finds a "correlation blind spot" — LLM rationales justify exposure to coupled assets that the risk layer has to clip.
- Leaves open: **agents do not reason about cross-asset dependence** → a graph-aware agent/risk layer is a gap.

Crowding note: live LLM-trading benchmarks proliferated in late 2025 (Agent Market Arena 2510.11695, LiveTradeBench 2511.03628, AI-Trader 2512.10971, StockBench) — all 2025, excluded. 2026 titles seen only in search snippets, `[UNVERIFIED]`: TradeTrap (reliability/faithfulness of trading agents, ~2026-02), AlphaForgeBench (~2026-02).

## A5. Reinforcement learning for trading / portfolios

**A5-1. Tavakoli et al. — *Certifying Reward Alignment in Portfolio Reinforcement Learning*.** <https://arxiv.org/abs/2610.34153> · 2026-10-25 · PR (workshop IAFM @ ICAIF 2026) · `[ABS]`
- Summary: audit certifying whether an RL policy implements its intended mean-variance objective; reward calibration preserves targets but does not improve backtests. Data: synthetic + 10/30/49 US industry portfolios (Kenneth French library, likely public).
- Leaves open: certification for richer objectives; relational state.

**A5-2. Song & Xiang — *When News Gets Old: Portfolio Allocation with Reinforcement Learning and Large Language Models*.** <https://arxiv.org/abs/2610.30564> · 2026-10-22 · pre (cs.LG) · `[ABS]`
- Summary: LLM signals from SEC filings; dropping stale news helps the LLM allocator; RL policies gain nothing consistent from news-age information. Net of costs, 2023–2025.
- Leaves open: RL adds little over simpler allocators — another negative result.

**A5-3. Koulouris & Campajola — *Beyond Supra-Competitive Outcomes: Collusive Behaviour in Deep Reinforcement Learning for Optimal Execution Games*.** <https://arxiv.org/abs/2610.00619> · 2026-09-30 · pre (q-fin.TR) · `[ABS]`
- Summary: independent PPO agents in a 2-player Almgren–Chriss liquidation game learn supra-competitive outcomes with punishment after deviation. Simulated only.
- Leaves open: detection of algorithmic collusion in real data.

**A5-4. Gelissen & Yuan — *Data-Driven Dynamic Portfolio Selection with Vine Copula Simulation and Reinforcement Learning*.** <https://arxiv.org/abs/2610.20037> · 2026-10-14 · pre (q-fin.PM) · `[ABS]`
- Summary: vine-copula scenario generator + recurrent RL with CVaR penalty; 7-asset panel, 22 monthly periods. Small evaluation.

**A5-5. Kashif & Ślepaczuk — *Deep Reinforcement Learning Framework for Diversified Portfolio Management Across Global Equity Markets*.** <https://arxiv.org/abs/2605.17307> · 2026-05-17 · pre (q-fin.PM) · `[ABS-s]`
- Summary: SAC with transaction costs, turnover penalty and walk-forward retraining; 16 out-of-sample folds 2003–2026 on Nasdaq-100, Nikkei 225, Euro Stoxx 50. Notable for honest walk-forward design and a European index.

**A5-6. Ozechi, Francis, Yakanu & Byers — *Comparative Evaluation of Modern Deep Learning Methodologies for Portfolio Optimization*.** <https://arxiv.org/abs/2604.24486> · 2026-04-27 · pre (cs.CE) · `[ABS-s]`
- Summary: compares GNN, DRL, Transformer and autoencoder approaches with classical models on equities/ETFs/bonds 2015–2023.

## A6. ML asset pricing & alpha/factor mining

**A6-1. Wang & Ventre — *FactorBench: A Portfolio-Aware Benchmark for Automated Factor Mining*.** <https://arxiv.org/abs/2610.06947> · 2026-10-03 · pre (q-fin.PM) · `[ABS]`
- Summary: ~5,000 factors from nine mining methods across five equity markets, judged on validity, generalisation, distinctness and after-cost portfolio value; no paradigm consistently wins.
- Leaves open: field has more methods than evaluation; benchmark itself now exists → **evaluation niche partly closed**.

**A6-2. Huang et al. — *AlphaRLM: Aligning Language Models for Literature-Grounded Symbolic Factor Discovery*.** <https://arxiv.org/abs/2610.14959> · 2026-10-10 (v3 10-15) · pre (cs.AI) · `[ABS]`
- Summary: RL-aligned LLM that writes executable factors from financial literature; CSI 300/1000, S&P 500.

**A6-3. Qu, Chen & Wang — *Propose, Don't Judge: An Anytime-Valid Referee for LLM Agents That Mine Investment Factors*.** <https://arxiv.org/abs/2609.27051> · 2026-09-22 · pre (cs.AI) · `[ABS]`
- Summary: agent proposes, a fixed betting-based (e-value) referee admits factors using only post-submission data, giving false-discovery control; certification takes ~500 trading days. CSI 500 walk-forward.
- Leaves open: anytime-valid testing for other ML-in-finance claims (e.g. graph edges, agent skill).

**A6-4. Pan, Ding & Giesecke — *Agentic Empirical Asset Pricing: Methodological Foundations*.** <https://arxiv.org/abs/2609.00731> · 2026-09-01 · pre (cs.AI) · `[ABS]`
- Summary: reference architecture + evaluation standard for LLM agents doing factor research (SEADS vs five baselines; reliability across re-runs); reports negative findings.

**A6-5. Shi, Yan, Cai & Lv — *Hubble: An LLM-Driven Agentic Framework for Safe, Diverse, and Reproducible Alpha Factor Discovery*.** <https://arxiv.org/abs/2604.09601> · 2026-03-09 (v2 04-14) · pre (cs.AI) · `[ABS-s]`

**A6-6. Wang et al. — *FactorMiner: A Self-Evolving Agent with Skills and Experience Memory for Financial Alpha Discovery*.** <https://arxiv.org/abs/2602.14670> · 2026-02 · pre · `[ABS-s]`

Also seen in listings, not opened (`[UNVERIFIED]`): AlphaPADI (2610.04959, diffusion for formulaic alphas), EverMine (2609.33524, long-horizon alpha research agents), Residual Learning in Empirical Asset Pricing (2610.09613). Background-era AAAI 2026 papers first posted 2025 (Alpha Jungle MCTS, 2505.11122) excluded.
Crowding: **LLM alpha mining is one of the most crowded 2026 niches** (≥9 papers found in one sweep, heavy Chinese-market/Qlib focus).

## A7. Generative models & market simulation

**A7-1. Marti — *CorrFlow: Exact and Permutation-Equivariant Flow Matching on the Correlation Elliptope*.** <https://arxiv.org/abs/2610.13606> · 2026-10-09 · pre (stat.ML/q-fin.RM) · `[ABS]`
- Summary: generalised Fisher transform maps correlation matrices to unconstrained space; permutation-equivariant graph flow matching learns their distribution; always-valid outputs. Data: 80×80 Taiwan equity correlation matrices.
- Leaves open: *conditional/temporal* generation of correlation networks (e.g. next-month network given today's) — generation of signed market graphs as a forecasting tool. Authors say no clear win over tuned image models.

**A7-2. Nigmatulin, Mohl, Frey, Li, Marti-Shahandeh, Cucuringu, Calinescu, Foerster & Zohren — *LOB-Impact Benchmark: Emergent Market Impact in Generative Limit Order Book Models*.** <https://arxiv.org/abs/2610.27100> · 2026-10-19 · PR (ICAIF '26) · `[ABS]`
- Summary: tests whether autoregressive message-level LOB generators reproduce market impact when metaorders are injected; five NASDAQ stocks, five models. Code: <https://github.com/george-nigmatulin/lob-impact>.
- Leaves open: needs LOB message data (LOBSTER — paid/academic) → outside Frank's public-data constraint.

**A7-3. Masi, Coletta & Bartolini — *High-Quality Synthetic Financial Time-Series using a GAN-Diffusion Framework* (CoMeTS-GAN).** <https://arxiv.org/abs/2605.27113> · 2026-05-26 · pre (cs.LG) · `[ABS]`
- Summary: conditional GAN generating mid-price and volume for correlated stocks; critic guides a diffusion model to preserve cross-asset correlation; supports counterfactual shocks that propagate to correlated assets.
- Leaves open: counterfactual propagation is only correlation-based, not causal.

**A7-4. Fukunishi, Qiu & Takahashi — *Generating Synthetic Stock Return Distributions with Diffusion Models*.** CARF Working Paper F-627 / CIRJE F-1273, Univ. of Tokyo, 2026-05. <https://ideas.repec.org/p/cfi/fseres/cf627.html> · working paper · `[ABS-s]` (RePEc record)
- Summary: diffusion model tailored to return distributions, extended to regime-conditional generation.

Not opened (rate-limited, `[UNVERIFIED]`): 2610.24544 *Rachev-Ratio Portfolio Optimization with TimeGAN Scenarios*; 2610.16732 GROMM (options). Pre-2026: Diffusion Factor Models (2504.06566), CorrGAN (Marti 2020) → background only.

## A8. Causal ML, lead-lag & spillover networks

**A8-1. Deng & Zhang — *Lead-Lag Relationships in Financial Markets: A Comparison of Multiple Clustering Algorithms*.** <https://arxiv.org/abs/2608.24703> · 2026-08-25 · pre (q-fin.ST) · `[ABS]`
- Summary: compares MiniRocket-KMeans, KShape and an ensemble against DTW-KMedoids for clustering stocks by lead-lag; evaluates via lead-lag trading strategy (best max drawdown −63.9%).
- Leaves open: lead-lag *networks* are still built by unsupervised statistics; no learned/forecast lead-lag edges, no sign dynamics.

**A8-2. Duong, Moneta, Lillo, Giannetti & Nguyen — *Contemporaneous Transmission Networks and Systemic Risk in European Banking*.** <https://arxiv.org/abs/2610.37487> · 2026-10-27 · pre (q-fin.ST) · `[ABS]`
- Summary: recursive non-Gaussian (LiNGAM-type) network of daily equity-return shocks among 51 listed European banks; systemic-impact and vulnerability scores. Receiving roles more reproducible than transmitting roles.
- Leaves open: European listed firms beyond banks; temporal stability of causal edges; link to ML.

**A8-3. Thumm & Chen — *Market Impact Estimation via Causal Foundation Models*.** <https://arxiv.org/abs/2610.12537> · 2026-10-08 · pre (cs.LG) · `[ABS]`
- Summary: causal prior-data fitted network trained on synthetic markets with hidden confounders; transfers zero-shot to LOB simulations and real flow bursts (crypto perps, ~3,800 Nasdaq equity bursts). Proof of concept.
- Leaves open: **causal foundation models (PFNs) for other financial causal questions**, e.g. spillover estimation between firms.

**A8-4 (method, not finance-specific). Redden, Wang & Li — *Causal-INSIGHT: Probing Temporal Models to Extract Causal Structure*.** <https://arxiv.org/abs/2603.25473> · 2026-03-26 · PR (IJCNN 2026, per page) · `[ABS-s]`
- Summary: model-agnostic probing (input clamping) of a trained temporal predictor to recover the directed Granger-style dependency graph it relies on.
- Relevance: tool to ask "what graph does a stock forecaster actually use?" — links A8 and A10.

Seen, not relied on: *Surpassing stock market's noise-nonstationarity tradeoff by causal-based domain discovery* (Xu et al., Quantitative Finance 26(4), 2026; online date unknown) `[UNVERIFIED]`; 2610.19428 *Common Signals, Spurious Cross-Excitation, and Identification in Multivariate Hawkes Processes* (listing only) `[UNVERIFIED]`. A Princeton senior thesis (2026-04) compares linear vs neural Granger networks on 20 US assets — not peer-reviewed, noted as a signal that the question is student-sized.
Pre-2026 background: DeltaLag (2511.00390), CausalStock (2411.06391), Cucuringu lead-lag clustering line.

## A9. Anomaly, regime & risk (incl. credit/default contagion)

**A9-1. Chen & Hybinette — *Velocity- and Regime-Aware Detection of Intraday Options Market Manipulation, with Explainable Attribution*.** <https://arxiv.org/abs/2608.05373> · 2026-08-05 · pre (q-fin.TR) · `[ABS]`
- Summary: minute-level detector based on the velocity of market state; HMM regime conditioning hurts; a pump-reversal *shape* score transfers to US small caps. **Labels from public enforcement records** (Indian regulator order; SEC v. Patel complaint). Exact SHAP attribution per alert.
- Leaves open: tiny label sets (10 days); single-asset detection — no cross-stock / network view of coordinated manipulation in equities. Authors themselves suggest graph-based detection as future work.

**A9-2. Kriuk & Kriuk — *ORCA — Online Regime Correlation Analyzer*.** <https://arxiv.org/abs/2604.17251> · 2026-04-19 · pre (cs.CE) · `[ABS]`
- Summary: 127 spectral/topological features of rolling correlation networks (24 ETFs) + price features → Random Forest for 10-day rally/crash probability; walk-forward with anti-leakage gaps; topology features add ~10pp AUC for crashes.
- Leaves open: no learned graph model; 24 instruments only; no sign structure.

**A9-3. *Fraud Detection in Cryptocurrency Markets with Spatio-Temporal Graph Neural Networks*.** <https://arxiv.org/abs/2604.24590> · 2026-04-27 · pre · `[ABS-s]` (via aggregator; authors not verified)
- Summary: three ways to build hourly market graphs; ST-GNN detects pump-and-dump better than per-asset baselines. Crypto-only → **method transfers** to equity micro-caps.

**A9-4. Brogaard & Chen — *The Network Foundations of Credit Counterparty Risk: Theory and Evidence*.** Working paper (SMU conference, 2026-06). `[UNVERIFIED]` (PDF seen in search only; first-public date unclear; uses CDS = paid data)
- Summary: production-network model; GNN shows supply-chain topology improves CDS-spread prediction.

Credit → equity search outcome: **no 2026 ML paper found** that learns how defaults/bankruptcies propagate to linked firms' *equity*. Finance evidence on bankruptcy/downgrade spillovers along supply chains is older event-study work (e.g. Kolay, Lemmon & Tashjian, JFQA 2016 `[BACKGROUND]`). SME credit-GNN work (2510.09407) is 2025 and uses private bank data. Systemic Risk Radar (2512.17185) is Dec 2025 → excluded.
Low-quality 2026 items seen and ignored: 2607.04184 (QPAIN 2026 manipulation), JEFAS 2026 "AI-driven" manipulation blueprint (no experiments).
