# Algorithmic Sports Betting

Quantitative betting on sports exchanges and bookmakers — outcome modelling, cross-book
arbitrage detection, and staking strategy.

**Why this is separate from prediction markets:** the pricing surface is different. Betting
exchanges and bookmakers quote decimal odds with an overround and per-book limits;
prediction markets quote a probability in a CLOB with an order book. Arbitrage, staking and
model calibration all work differently. Related work lives in
[Prediction Market Algorithmic Trading](https://github.com/pranay123-stack/prediction-market-algorithmic-trading).

---

## Published

### UK Horse Racing Quant Platform
A full quantitative pipeline on The Racing API: ingestion, point-in-time feature
engineering, a calibrated probability engine, an expected-value strategy layer with
walk-forward backtesting, and a live daily prediction product served over FastAPI.

**What's in it**
- 89 point-in-time features attached by a single `as_of_join` helper, so look-ahead bias
  is structurally impossible rather than merely avoided — the test for it caught a real
  leak in the codebase
- LR / XGBoost / LightGBM with Platt and isotonic calibration, race-level normalisation,
  and a versioned, promotable model registry
- An analysis protocol frozen and content-hashed *before* the data existed: one
  pre-registered hypothesis, eight pre-flight gates, Bonferroni-corrected segments, and a
  mechanical verdict function that no prose in the report can move
- A live product: daily BET/NO_BET signals with reasons, settled performance reported with
  its t-statistic, and a replay check proving the live path and the backtest run identical
  code

**Honest status.** 162 modules, ~23,400 lines of application code, 1,081 tests passing.
But **the edge is unproven**: The Racing API subscription on these credentials is inactive,
so every published number comes from synthetic data and says nothing about real racing
markets. The apparatus is complete and tested; the verdict is blocked on billing, and the
repository says so on its front page rather than in a footnote.

**Tech:** Python 3.12, FastAPI, SQLAlchemy 2.0, PostgreSQL 16, pandas, scikit-learn,
XGBoost, LightGBM, Docker, GitHub Actions

[View repository →](https://github.com/pranay123-stack/horse-quant-platform)

---

### Smarkets Sports Quant Trading
Quantitative strategies against the Smarkets betting exchange.

**What's in it**
- `Arbitrage_detector_strategy` — cross-book price discrepancy detection
- `Football_outcome_predictor_bets_strategy` — match outcome modelling
- `backtester` — a full harness: data loader, execution manager, bet manager,
  position and portfolio management, plus a Streamlit dashboard
- The only trained models in my public work: a scikit-learn RandomForest with a committed
  `model.pkl`, a Keras LSTM, and a hand-rolled PPO actor-critic

**Honest status — read before judging the strategies.** This repository **does not
currently run**. A module it imports is missing, a base class is never imported, it carries
a hardcoded absolute path, and 17 files are zero bytes — including all four test files. The
modelling work is real; the packaging around it is broken. It is listed rather than hidden
because the models and the backtester structure are worth reading, but nothing here has
been validated end to end.

**Tech:** Python, pandas, scikit-learn, TensorFlow/Keras, Streamlit

[View repository →](https://github.com/pranay123-stack/Smarkets_Sports_Quant_Trading)

---

## Sports markets, traded as event contracts

These are sports projects that trade on prediction markets rather than betting exchanges,
so they are cross-listed rather than duplicated.

| Project | What it is |
|---|---|
| [nba-prediction-edge](https://github.com/pranay123-stack/nba-prediction-edge) | NBA playoffs signal generation — injury-driven alpha with cross-market momentum-lag detection, priced against Polymarket. **Has never traded**; runs dry-run by default. |
| [matchcall](https://github.com/pranay123-stack/matchcall) | World Cup outcome market on Solana — pari-mutuel escrow settled trustlessly through an onchain CPI. Program verified executable on devnet. |

---

## Not yet published

One codebase in this domain is built but not public:

- **NBA betting strategy** — a separate modelling codebase from the Polymarket signal
  work above: data collection, model training, a daily pipeline and a prediction script,
  plus an MLB RBI model alongside it. Roughly 1,400 lines across four modules, with no
  tests and no git history yet — a working script set rather than a platform, which is
  why it is listed here and not above.

*Modelling vocabulary across this work: Elo ratings, expected goals (xG), Kelly staking,
overround removal, and cross-book arbitrage.*
