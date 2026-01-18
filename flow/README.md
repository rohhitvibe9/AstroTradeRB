# AstroTradeRB — Message Flow Architecture

This document defines how messages flow between the user, WhatsApp, logic engine, and response layer.

AstroTradeRB is NOT chatty.
It is event-driven, command-based, and time-sensitive.

---

## 1️⃣ ENTRY POINT (WHATSAPP)

All interaction starts on WhatsApp.

User sends:
- A command
- OR receives an auto-triggered message (Important Time alert)

Examples:
- NIFTY
- GAP?
- OTM?
- WHY?
- NEXT TIME?

No free-text conversation is allowed.

---

## 2️⃣ COMMAND PARSER

Incoming message is first classified as:

- MARKET command (NIFTY / SENSEX / BTC)
- QUESTION command (WHY? / RISK? / GAP?)
- CONTROL command (HOLD? / EXIT?)
- SYSTEM command (BACKTEST?)

If command is invalid:
→ Bot replies: `INVALID COMMAND`

---

## 3️⃣ CONTEXT RESOLUTION

Bot resolves current context using:
- Selected market (default: NIFTY)
- Current time (IST)
- Last important time
- Active position (if any)
- Volatility state

If context is missing:
→ Bot requests minimal clarification.

---

## 4️⃣ LOGIC ENGINE CALL

Bot calls Core Logic with:
- Market
- Time
- Price
- Volatility
- User command

Logic returns:
- Bias %
- Expected behavior
- Risk instruction
- Reason (WHY)

No execution happens here.

---

## 5️⃣ RESPONSE FORMATTER

Raw logic output is converted into:
- Clean WhatsApp-readable message
- Fixed structure
- Emojis used sparingly (⚠️ ⏱️ 🔍)

No charts.
No slang.
No motivation.

---

## 6️⃣ MESSAGE DELIVERY RULES

- Important Time alerts: auto-sent
- Command replies: instant
- Duplicate spam commands: ignored for 30 seconds
- High-risk periods: warning first, then response

---

## 7️⃣ FAIL-SAFE FLOW

If:
- Volatility is abnormal
- Bias < 50%
- Logic confidence is low

→ Bot responds:
`NO TRADE — CONDITIONS NOT FAVORABLE`

---

## 8️⃣ LOGGING (INTERNAL)

Every interaction logs:
- Time
- Command
- Logic output
- Response sent

Used for:
- Backtesting
- Audits
- Strategy refinement

---

## 9️⃣ USER EXPERIENCE RULE

User should always know:
- WHY a message was sent
- WHAT is expected
- WHAT NOT to do

No confusion.
No emotional language.

---

## ⚠️ IMPORTANT

AstroTradeRB never:
- Forces a trade
- Predicts outcomes
- Encourages overtrading

It supports decisions — nothing more.
