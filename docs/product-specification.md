# MONY — Master Product & Engineering Specification

## 1. Role

Act as a world-class fintech product architect, senior full-stack engineer, quantitative researcher, financial data engineer, UX designer and product strategist.

Build MONY from the ground up. Think independently, challenge weak assumptions, design original solutions and implement in carefully tested phases.

Do not create a clone of an existing trading application. Design MONY's own information architecture, user experience, analytical framework and learning system.

Do not rush into coding before understanding the complete product vision.

---

## 2. Product Vision

- **Name:** MONY
- **Category:** Financial technology, equity-market intelligence and trading education
- **Market:** Indian listed cash-equity stocks
- **Use case:** Intraday equity-market research and understanding
- **Initial audience:** The founder, then a small private testing group
- **Platform:** Web application
- **Budget:** Minimal — prefer open-source, local development, affordable infrastructure

MONY is a new way for ordinary equity traders to understand the stock market. It brings together financial news, global developments, Indian equity-market data, technical analysis, historical behaviour, risk concepts and educational explanations in one unified experience.

The long-term goal: a reliable, continuously improving market-knowledge platform — not another application that merely displays prices and indicators.

---

## 3. The Most Important Rule

**MONY MUST NEVER TELL USERS WHICH STOCK TO BUY OR SELL.**

Never use:
- "Buy this stock now."
- "Sell this stock now."
- "This stock will definitely rise."
- "Guaranteed profit."
- "Certain market prediction."

Always provide:
- Verified market facts
- Historical observations
- Technical indicator values and explanations
- Relevant news and source links
- Possible interpretations — clearly labelled
- Supporting and contradicting evidence
- Risk calculations and limitations
- Historical examples and counterexamples
- Educational explanations

This rule must influence design, API contracts, UI copy, AI prompts, analytics and testing.

---

## 4. Scope

### In scope
- Indian listed cash-equity shares
- Intraday market research
- Equity market scanning and exploration
- Global financial context relevant to Indian equities
- Financial news and company announcements
- Technical analysis
- Historical market analysis
- Trading education
- Risk and position-size calculations
- Historical strategy testing
- Simulated paper trading
- Personal research notes and trading journals
- Performance analysis and learning

### Explicitly excluded
- Futures and options / derivatives trading
- Long-term investing and portfolio management
- Brokerage services
- Real-money order execution
- Unauthorised broker integrations
- Unvalidated automated trading
- Guaranteed-return claims
- Unverified market rumours presented as facts
- Artificial trading signals

---

## 5. Core Experience

### A. Global Market Intelligence
Major global indices, Asian/European/US sessions, currencies, commodities, central bank decisions, inflation/employment releases, geopolitical events, cross-market relationships.

Explain why a development might matter and which Indian sectors may be exposed. Distinguish confirmed events, correlations, hypotheses and uncertain implications.

### B. Indian Equity Market Intelligence
Price changes, volume, liquidity, breadth, sector performance, relative strength, volatility, gaps, corporate events, historical comparisons.

### C. Stock Explorer
OHLCV data, intraday charts, volume, gaps, trend context, indicators, support/resistance, volatility, news, sector context, data freshness.

### D. Technical Analysis Engine
Candlestick analysis, trend and market structure, support/resistance, breakouts, volume analysis, moving averages, RSI, MACD, VWAP, ATR, momentum, relative strength, gaps, multi-timeframe, pattern studies.

Do not display every indicator. Explain what each measures, its limitations and when it may mislead.

### E. Financial News Intelligence
Licensed providers, exchange announcements, company disclosures, economic releases, central bank communications.

Record: source, URL, publication time, event time, affected companies/sectors, verification status. Detect duplicates. Distinguish new from recirculated information.

### F. Market Explanation Engine
Answer: Why did this stock move? What changed in this sector? What happened overnight?

Structure: Facts → Context → Supporting evidence → Contradicting evidence → Interpretations → Unknowns → Historical comparisons → Sources → Educational explanation.

### G. Continuous Learning Environment
Lessons, chart explanations, indicator tutorials, historical case studies, risk education, common mistake explanations, knowledge library. Make learning contextual.

### H. Historical Market Research
Historical OHLCV analysis, comparable event exploration, pattern studies, backtesting, out-of-sample evaluation, sensitivity analysis, post-cost performance.

Prevent look-ahead bias, survivorship bias, data leakage and overfitting. Keep results reproducible.

### I. ORB Research Hypothesis
Opening Range Breakout as a hypothesis — not a proven profitable strategy. Define opening range, eligible universe, entry conditions, liquidity filters, stop methodology, exit rules, execution assumptions explicitly. Test long side initially.

Present historical observations and limitations as research. Evaluate after realistic brokerage, taxes, slippage.

### J. Risk Intelligence
Position sizing, entry-to-stop distance, capital exposure, risk budgets, reward-to-risk arithmetic, transaction costs, slippage, liquidity, gap risk. Explain that stops cannot guarantee exact exit price.

### K. Paper Trading and Journal
Simulation only. Simulated orders, fill assumptions, open/closed positions, intraday session-end closure, gross/net P&L, transaction costs, trade notes, strategy attribution.

Track: win rate, average win/loss, net expectancy, profit factor, maximum drawdown, losing streaks, costs proportion, performance by strategy/stock/regime.

---

## 6. Intelligence Principles

1. Evidence before explanation
2. Explanation before interpretation
3. Uncertainty must be visible
4. Every market claim traceable to a source or calculation
5. Historical relationships are not proof of causation
6. Technical indicators are measurements, not guarantees
7. Market coverage and data freshness must be explicit
8. Must be willing to say evidence is insufficient
9. No fabricated signals or manufactured certainty
10. User education takes priority over trading frequency
11. Every financial calculation must be deterministic, validated and tested
12. Strategy performance must be evaluated after costs
13. Important results must be reproducible
14. Original design must not come at the expense of financial accuracy

---

## 7. Technical Architecture

Start with a modular monolith. No unnecessary distributed infrastructure.

**Frontend:** React + TypeScript + Vite + responsive design + charting library
**Backend:** Python + FastAPI + Pydantic + SQLAlchemy + Alembic
**Database:** PostgreSQL + time-series candle storage + explicit versioning
**Testing:** pytest + HTTPX + unit + integration + deterministic fixtures

Use Redis, streaming or microservices only when a demonstrated requirement justifies it.

Keep indicators, strategy logic, risk calculations and backtesting separate from frontend code. Create replaceable adapters for data providers and AI services.

---

## 8. Data Reliability

Use authorised historical equity-market data only. Build a provider-independent data interface.

Record: provider, dataset version, instrument ID, exchange timestamp, receipt timestamp, source timeframe, quality status, missing bars, import history, access restrictions.

Detect duplicates, missing bars, invalid OHLC, stale data, session-calendar mismatches.

---

## 9. Data Models

Entities to design and version:
- Instruments
- Market data imports
- Historical candles
- Data source metadata
- News articles and sources
- Corporate events
- Economic events
- Technical indicator results
- Strategy definitions and versions
- Research observations
- Backtest runs
- Signals and evidence
- Paper trading sessions
- Simulated orders and fills
- Completed simulated trades
- Journal entries
- Performance metrics
- Audit events

Use Decimal-compatible arithmetic for financial values. Store timestamps consistently. Display in Asia/Kolkata.

---

## 10. Build Phases

| Phase | Deliverable |
|-------|-------------|
| 0 | Project skeleton, frontend shell, API health, DB setup, migrations, smoke tests |
| 1 | Historical data import, validation, session handling, instrument metadata |
| 2 | Stock explorer + core technical indicators |
| 3 | News ingestion, source tracking, event timelines |
| 4 | Market explanation engine — evidence, citations, uncertainty labels |
| 5 | ORB research hypothesis, scanner, risk calculator |
| 6 | Backtesting, simulated execution, transaction cost modelling |
| 7 | Paper trading, journal, learning analytics |
| 8 | Security, performance, data licensing, regulatory review |

---

## 11. Definition of Success

MONY succeeds when users:
- Understand market concepts more accurately
- Investigate price movements using evidence
- Distinguish facts from speculation
- Recognise uncertainty and limitations
- Understand risk and transaction costs
- Learn from historical examples
- Evaluate strategies reproducibly
- Maintain useful research records
- Make more informed independent decisions

Not defined by: number of signals, trades placed or notifications opened.
