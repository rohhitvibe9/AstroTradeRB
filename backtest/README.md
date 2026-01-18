# AstroTradeRB — Backtest Engine

The backtest engine validates AstroTradeRB logic
against historical data before live usage.

---

## Scope

- Market: NIFTY / SENSEX / BTC (phase-wise)
- Period: Last 5 years (rolling)
- Timeframe: Event-based (not candle-based)

---

## What Is Tested

For each historical Important Time:

- Astro event type
- Event time (IST)
- Market behavior:
  - Direction
  - Points moved
  - Time to peak
  - Reversal or continuation

---

## Metrics Captured

- Sample count
- Avg rise (points)
- Avg fall (points)
- Avg absolute move
- Max expansion
- Sideways frequency
- Win / loss ratio
- Volatility regime

---

## Outcome Classification

Each event is tagged as:
- STRONG
- MODERATE
- WEAK
- NO EDGE

These tags feed directly into:
- Bias %
- Trade size (small / big)
- OTM distance

---

## Guardrails Integration

Backtest respects:
- No-trade windows
- Volatility filters
- Risk limits

Blocked trades are recorded, not ignored.

---

## Confidence Scoring

Confidence % is derived from:
- Sample size
- Consistency
- Drawdown
- Volatility alignment

Minimum samples required:
- 20 events (otherwise LOW CONFIDENCE)

---

## Output Usage

Backtest data is used by:
- Logic engine
- Response format
- Decision engine

No backtest = no live confidence.
