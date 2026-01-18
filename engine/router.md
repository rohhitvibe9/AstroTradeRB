# AstroTradeRB — Command Router

The router is the gatekeeper between user input and the engine.
NO command reaches logic without passing the router.

---

## Router Responsibilities

1. Identify command intent
2. Check current STATE
3. Allow or block execution
4. Route to correct engine module
5. Enforce guardrails

---

## Supported Commands Mapping

| Command     | Allowed States              | Routes To              |
|------------|-----------------------------|------------------------|
| NIFTY      | IDLE                        | Market Context Engine  |
| SENSEX     | IDLE                        | Market Context Engine  |
| BTC        | IDLE                        | Market Context Engine  |
| GAP?       | IDLE, ANALYZING             | Gap Logic Engine       |
| OTM?       | SIGNAL                      | Options Engine         |
| NEXT TIME? | IDLE, ANALYZING, HOLDING    | Time Engine            |
| WHY?       | SIGNAL, HOLDING             | Reasoning Engine       |
| HOLD?      | HOLDING                     | State Validator        |
| EXIT?      | HOLDING                     | Exit Engine            |
| RISK?      | ANY                         | Risk Engine            |
| BACKTEST?  | IDLE                        | Analytics Engine       |

---

## Invalid Command Handling

If command is:
- Not recognized → respond with HELP
- Not allowed in current STATE → respond with WHY BLOCKED
- Allowed but low confidence → respond with CAUTION

---

## Router Rules

- Router does NOT calculate logic
- Router does NOT generate signals
- Router ONLY decides routing

---

## Why Router Exists

This prevents:
- Logic overlap
- State violations
- Accidental trades
- Emotional command spam

Router = Traffic Police  
Engine = Judge  
Logic = Analyst 
