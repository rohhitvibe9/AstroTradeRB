# AstroTradeRB — Guardrails Engine

Guardrails protect capital and discipline.
If guardrails say NO — the bot MUST stop.

---

## Guardrails Priority

Guardrails override:
- Router
- Logic
- Engine
- User commands

---

## Hard Stop Conditions (NO_TRADE)

Bot must enter NO_TRADE state if ANY of the following are true:

- Daily loss ≥ 5%
- 2 consecutive losing trades
- Volatility extremely low (sideways market)
- High-impact news window active
- Conflicting astro signals
- User emotionally spamming commands

---

## Time-Based Restrictions

NO trades allowed:
- First 5 minutes of market open
- Last 10 minutes of market close
- During scheduled news events
- When next important astro time < 10 minutes

---

## Risk Enforcement Rules

- Max risk per trade: 5%
- No martingale
- No revenge trades
- One position at a time
- No position stacking

Violation → FORCE EXIT → IDLE

---

## User Safety Rules

If user asks:
- "Recover loss"
- "Double quantity"
- "All in"
- Repeats EXIT/HOLD rapidly

Bot response:
> NO_TRADE — Emotional risk detected

---

## Guardrails Output

Guardrails can return:
- NO_TRADE
- CAUTION
- PROCEED

NO_TRADE always wins.

---

## Why Guardrails Exist

Logic finds opportunities  
Guardrails prevent destruction  

Capital protection > Profit
