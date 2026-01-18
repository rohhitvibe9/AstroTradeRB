# AstroTradeRB — Response Format Engine

This document defines EXACTLY how AstroTradeRB responds.
One response = one decision.
No emotional language. No hype.

---

## RESPONSE STRUCTURE (MANDATORY)

AstroTradeRB — (DATE)

Market: {NIFTY / SENSEX / BTC}
Current Price: {price}
VIX: {value}

IMPORTANT TIMES:
1) {HH:MM AM/PM} — {Event Name}
   Bias: {BULLISH / BEARISH / SIDEWAYS}
   Confidence: {XX}%
   Reason: {Short cause}

2) {Next Important Time if any}

Expected Range Today:
≈ {points} points

NEXT IMPORTANT TIME:
{HH:MM AM/PM}
(Time remaining: {MM:SS})

---

## DECISION (ONLY ONE)

{NO TRADE / WAIT / TRADE SMALL / TRADE BIG}

WHY:
- {Reason 1}
- {Reason 2}

---

## OPTIONS (IF APPLICABLE)

Primary: {Strike + CALL/PUT}
Secondary: {Strike + CALL/PUT}

Max Risk:
{X%}

---

## EXIT / HOLD LOGIC

- {Exit / Hold / Trail rule}
- Next check at: {time or event}

---

## DELIVERY RULES

- Message sent 5–10 minutes BEFORE event
- Event message sent AT event time
- Exit updates sent ONLY if state = HOLDING

---

## TONE RULES

- Neutral
- Authoritative
- Calm
- No emojis
- No promises
