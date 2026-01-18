# AstroTradeRB — State Architecture

This document defines how AstroTradeRB remembers context.
Without STATE, the bot is reactive.
With STATE, the bot becomes situationally aware.

State persists across messages during a trading session.

---

## 1️⃣ CORE STATE PRINCIPLE

- One user = one active state
- State resets daily or on command
- State controls WHAT the bot is allowed to do

State is read BEFORE logic execution.

---

## 2️⃣ MARKET STATE

Tracks which market the bot is currently operating in.

Fields:
- active_market → NIFTY | SENSEX | BTC
- mode → LIVE | PAPER | OBSERVE
- session → PREOPEN | OPEN | MID | CLOSE | CLOSED

Default:
- active_market = NIFTY
- mode = LIVE
- session = AUTO

---

## 3️⃣ TIME STATE

Tracks time-based awareness.

Fields:
- last_important_time
- next_important_time
- astro_bias_window (start → end)
- time_confidence %

Used to:
- Prevent overtrading
- Avoid late entries
- Decide HOLD / EXIT validity

---

## 4️⃣ TRADE STATE

Tracks current trade lifecycle.

Fields:
- trade_active → true / false
- direction → CALL / PUT
- instrument → INDEX / OPTION
- strike
- entry_time
- entry_reason
- confidence %
- expected_move
- status → RUNNING | EXITED | STOPPED

Only ONE trade can be active at a time.

---

## 5️⃣ RISK STATE (LOCK SYSTEM)

Controls safety.

Fields:
- max_risk_per_trade (default 5%)
- risk_used_today %
- loss_lock → true / false
- no_trade_flag → true / false

Rules:
- If loss_lock = true → bot refuses trades
- Bot can command NO TRADE DAY

---

## 6️⃣ COMMAND STATE

Tracks last user interaction.

Fields:
- last_command
- last_response_type
- repeat_count

Used to:
- Detect spam / overconfidence
- Prevent repeated risky commands

---

## 7️⃣ STATE RESET RULES

State resets when:
- New trading day starts
- User sends RESET
- Market session ends
- Loss lock is triggered

---

## 8️⃣ STATE → LOGIC FLOW

Order of execution:

1. Read STATE
2. Validate command permission
3. Apply LOGIC
4. Generate RESPONSE
5. Update STATE
6. Send MESSAGE

No logic runs without state validation.

---

⚠️ Important:
STATE is authority.
Logic cannot override state.
