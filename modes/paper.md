# AstroTradeRB — Paper Trading Mode

Paper Mode simulates live trading without real execution.
All decisions are generated exactly like LIVE mode,
but marked as PAPER for validation.

---

## Paper Mode Rules

- No real trades executed
- Signals are informational
- Guardrails still apply
- State transitions are enforced
- Loss lock is simulated

---

## What Paper Mode Tests

- Important Time detection
- Bias & confidence accuracy
- OTM strike logic
- Exit / Hold behavior
- Message format clarity

---

## Paper Mode Output

Every message must include:

Mode: PAPER

This ensures no confusion with LIVE signals.

---

## Transition Rules

Default mode = PAPER

Only user command can switch to LIVE:
> MODE LIVE

If guardrails block → stays in PAPER.

---

## Purpose

Paper Mode builds confidence before capital exposure.
