# MONY — Architecture Notes

## Modular Monolith (Phase 0)

```
mony/
├── frontend/          # React + TypeScript + Vite
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   └── utils/
│   └── package.json
│
├── backend/           # Python + FastAPI
│   ├── app/
│   │   ├── api/       # Route handlers
│   │   ├── core/      # Config, security
│   │   ├── db/        # Models, migrations
│   │   ├── services/  # Business logic
│   │   │   ├── market_data/
│   │   │   ├── technical/
│   │   │   ├── news/
│   │   │   ├── explanation/
│   │   │   ├── backtest/
│   │   │   └── risk/
│   │   └── adapters/  # Data provider interfaces
│   └── tests/
│
└── docs/              # Product spec, architecture, decisions
```

## Key Design Decisions

- **Replaceable data adapters** — swap providers without changing business logic
- **Deterministic financial calculations** — all indicator and risk logic in backend, not frontend
- **Explicit uncertainty** — every explanation carries confidence level and source
- **No fabricated data** — dev fixtures clearly marked, never displayed as real market data
- **Decimal arithmetic** — never float for money or prices

## Database Strategy

- PostgreSQL for all persistent data
- Separate tables for candles, signals, trades, journal, audit
- Dataset versioning — know exactly which data backed which backtest
- Strategy versioning — rule changes don't silently invalidate old results
