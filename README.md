# DataNexus 🇮🇳📈

> **Financial Market Intelligence & Forecasting System**  
> An end-to-end open source data science project — Indian equities & mutual funds, ML-powered, agent-accessible.

![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=flat&logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)
![Status](https://img.shields.io/badge/Status-In%20Development-orange?style=flat)
![Cost](https://img.shields.io/badge/Cost-₹0-brightgreen?style=flat)

---

## What is DataNexus?

DataNexus takes any NSE-listed stock or Indian mutual fund, analyses years of market data, runs machine learning models to forecast price direction, backtests the strategy historically, and — in its final form — does all of this autonomously when you ask it a question in plain English.

```
You ask  →  "Should I hold RELIANCE or buy more HDFCBANK right now?"
DataNexus →  Fetches data → Runs models → Backtests → Explains answer
```

Built as a personal finance tool for retail investors. No Bloomberg terminal. No paid APIs. No cloud bills. Just Python, open source libraries, and free data.

---

## The Problem It Solves

| Problem | What DataNexus Does |
|---|---|
| Market data is scattered and raw | Automated ETL pipeline — fetches, cleans, and versions NSE + AMFI data daily |
| Analysis is not reproducible | Every model run is logged in MLflow with full parameters and metrics |
| Financial insight requires technical expertise | Natural language agent interface — ask questions, get answers, no Python needed |

---

## Capabilities

### 1. Data Ingestion
- Pulls historical OHLCV data for NSE-listed stocks via `yfinance` (ticker format: `RELIANCE.NS`)
- Pulls daily NAV history for all AMFI-registered mutual funds via `mftool`
- Handles splits, dividends, missing trading days automatically
- Stores clean data as Parquet files, versioned with DVC

### 2. Exploratory Analysis
- Rolling returns, volatility, Sharpe ratio, maximum drawdown
- Sector correlation matrices and heatmaps
- Interactive Plotly candlestick charts with Bollinger bands and moving averages
- SIP return simulation and XIRR calculation for mutual funds
- Fund vs benchmark comparison (Nifty 50, Nifty Midcap 150)

### 3. Machine Learning Pipeline
- Predicts next-day price direction (up/down) for any NSE stock
- Features: RSI, MACD, Bollinger bands, lag returns, rolling volatility, sector context
- Walk-forward cross-validation — no data leakage
- Models: Logistic Regression → XGBoost → LightGBM → Stacked Ensemble
- Hyperparameter optimisation with Optuna
- SHAP values for explainability — know *why* the model predicted what it did
- All experiments tracked in MLflow

### 4. Backtesting Engine
- Walk-forward backtest simulating real trading on model signals
- Strategy returns vs Nifty 50 buy-and-hold benchmark
- Sharpe ratio, Sortino ratio, max drawdown, win rate, average trade duration
- Transaction cost modelling (brokerage + STT)

### 5. Agentic AI Interface *(Phase 8)*
- LangGraph-powered agent with tool-calling
- Plain English queries → multi-step reasoning → synthesised answer
- Tools: `fetch_data`, `run_model`, `backtest`, `generate_chart`, `write_report`, `query_knowledge_base`
- RAG over earnings transcripts and fund factsheets
- Chainlit chat UI — accessible to anyone with the link

---

## Tech Stack

| Layer | Technology | Why |
|---|---|---|
| Language | Python 3.12 | Industry standard for data science |
| Package management | uv | Faster than pip, better than conda |
| Data — Equities | yfinance | Free NSE/BSE data, no API key |
| Data — Mutual Funds | mftool | Free AMFI NAV data for all Indian MFs |
| Data versioning | DVC | Reproducible datasets, tracked like code |
| Wrangling | pandas, numpy | The DS standard |
| Visualisation | plotly, seaborn | Interactive charts for financial dashboards |
| Statistics | scipy, statsmodels | Hypothesis testing, ARIMA, return analysis |
| ML | scikit-learn, XGBoost, LightGBM | Production-grade tabular ML |
| Hyperparameter tuning | Optuna | Bayesian optimisation |
| Explainability | SHAP | Why did the model predict this? |
| Experiment tracking | MLflow | Every model run logged and versioned |
| API | FastAPI + Pydantic | Production REST endpoints |
| Agent | LangGraph + LangChain | Stateful multi-step reasoning |
| LLM | Ollama (local, free) | Zero API cost |
| Chat UI | Chainlit | Accessible chat interface |
| Testing | pytest | Automated test suite |
| CI/CD | GitHub Actions | Tests run on every push |
| Containerisation | Docker + Compose | Runs identically everywhere |
| Deployment | Render.com free tier | Live on the internet, zero cost |
| Version control | Git + GitHub | Full project history |

---

## Project Structure

```
datanexus/
├── src/
│   └── datanexus/
│       ├── data/          # ETL pipeline — fetch, clean, store
│       ├── features/      # Feature engineering
│       ├── models/        # ML training and evaluation
│       ├── backtest/      # Backtesting engine
│       ├── api/           # FastAPI service
│       └── agent/         # LangGraph agent
├── notebooks/             # EDA and exploration (never production logic)
├── data/
│   └── raw/               # Tracked with DVC, not committed to Git
├── models/                # Serialised models, tracked with MLflow
├── tests/                 # pytest test suite
├── notes/                 # Learning journal
├── docs/                  # Project brief and detailed documentation
├── docker/                # Dockerfile and Compose configs
├── .github/
│   └── workflows/         # GitHub Actions CI/CD
├── pyproject.toml         # Project config and dependencies
├── Makefile               # One-command pipeline runner
└── .gitignore
```

---

## Build Roadmap

| Phase | Data Science | Engineering | Status |
|---|---|---|---|
| Foundation | Project scaffold | Git, uv, pyproject.toml | ✅ Done |
| 01 | Python OOP, dataclasses | Conventional commits, pre-commit | 🔄 In progress |
| 02 | Pandas ETL, yfinance + mftool | DVC, Makefile | ⏳ |
| 03 | EDA, Plotly dashboard | Notebooks → scripts, pytest | ⏳ |
| 04 | Stats inference, ARIMA | Docker container | ⏳ |
| 05 | scikit-learn pipeline, CV | Model serialisation, GitHub Actions | ⏳ |
| 06 | XGBoost, LightGBM, Optuna, MLflow | Docker Compose stack | ⏳ |
| 07 | FastAPI REST service | Cloud deployment, Render | ⏳ |
| 08 | LangGraph agent, RAG, Chainlit | Auth, monitoring, CI/CD | ⏳ |

---

## Cost

**Total: ₹0**

| Component | Free Option |
|---|---|
| Data (equities) | yfinance — Yahoo Finance, no key needed |
| Data (mutual funds) | mftool — AMFI India, completely free |
| All Python libraries | Open source — MIT / Apache 2.0 |
| Hosting | Render.com free tier |
| Database | Supabase free tier |
| CI/CD | GitHub Actions (free for public repos) |
| LLM for agent | Ollama — runs locally, no API cost |
| MLflow tracking | Self-hosted |

The only optional cost is an LLM API (Anthropic/OpenAI) instead of local Ollama — approximately ₹100–200/month at personal usage scale.

---

## Who Is This For?

Built for **retail investors** — anyone who invests their own money in Indian stocks or mutual funds and wants data-driven insight without a Bloomberg terminal or a finance degree.

- You do SIPs into mutual funds and want to know if your fund is actually beating the index
- You track a few NSE stocks and want a signal beyond "the news said buy"
- You want to understand your portfolio's risk — not just returns
- You want to ask a question in plain English and get an honest, model-backed answer

---

## Getting Started

```bash
# Clone the repo
git clone git@github.com:VSKoffl/datanexus.git
cd datanexus

# Install dependencies
uv sync

# Pull data (DVC)
dvc pull

# Run the pipeline
make data
make features
make train

# Start the API
make api

# Start the agent chat UI
make agent
```

---

## Learning Context

This project is being built as part of an R → Python transition — learning the full Python data science and engineering stack by building one real, useful system from scratch rather than following disconnected tutorials.

Every phase is documented in `notes/`. Every decision has a reason.

---

## License

MIT — use it, fork it, share it. No restrictions.

---

*Built with Python. Powered by open source. Cost: ₹0.*
