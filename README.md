# Algorithmic Sports Betting

Quantitative betting on sports exchanges and bookmakers — outcome modelling, cross-book
arbitrage detection, and staking strategy.

**Why this is separate from prediction markets:** the pricing surface is different. Betting
exchanges and bookmakers quote decimal odds with an overround and per-book limits;
prediction markets quote a probability in a CLOB with an order book. Arbitrage, staking and
model calibration all work differently. Related work lives in
[Prediction Market Systems](https://github.com/pranay123-stack/prediction-market-systems).

---

## Published

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

The substantial work in this domain is built but not public:

- **UK horse racing quant platform** — a full pipeline on The Racing API: data ingestion,
  feature engineering, model training and a live prediction product (CLI, dashboard and
  API). By far the largest project in this category.
- **NBA betting strategy** — a separate modelling codebase from the Polymarket signal work above.

Together roughly 173 source files and 41 test files. Neither is a git repository yet.
Publishing the horse racing platform would make this the best-evidenced category on my
profile rather than the thinnest.

*Modelling vocabulary across this work: Elo ratings, expected goals (xG), Kelly staking,
overround removal, and cross-book arbitrage.*
