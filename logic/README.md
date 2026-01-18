# AstroTradeRB — Core Trading Logic

This document defines the decision-making engine of AstroTradeRB.
The bot DOES NOT predict randomly. It reacts to TIME + BEHAVIOR + VOLATILITY.

---

## 1️⃣ DEFAULT MARKET PRIORITY
- Weekdays (Mon–Fri): **NIFTY 50 (Primary)**, **SENSEX (Secondary)**
- Weekends (Sat–Sun): **BTC / Crypto (Paper / Observation Mode)**

If no command is given, bot assumes:
> MARKET = NIFTY 50

---

## 2️⃣ IMPORTANT TIME LOGIC (ASTRO + MARKET)

Each Important Time is generated using:
- Planetary transitions (Moon, Mercury, Mars)
- Nakshatra change OR planetary aspect
- Market session overlap (India / US)

### Every Important Time MUST include:
- Reason (WHY time matters)
- Expected behavior (Reversal / Expansion / Trap / Spike)
- Confidence % (not direction accuracy, but conviction strength)

Example:
> Mercury crosses Moon → Fast move + false breakout risk

---

## 3️⃣ BIAS CONFIDENCE (%)

Bias % is calculated from combined confirmations:

| Factor | Weight |
|------|-------|
| Astro strength | 40% |
| Market structure | 30% |
| Volatility (VIX / ATR) | 20% |
| Session timing | 10% |

### Interpretation:
- **90%+** → Aggressive opportunity
- **70–89%** → Tradeable
- **50–69%** → Cautious / scalp only
- **Below 50%** → Avoid or paper trade

---

## 4️⃣ GAP UP / GAP DOWN LOGIC (Carry Forward)

Checked at **3:00 PM IST**

### Conditions analyzed:
- Day close vs day range
- Last hour volume expansion
- Astro bias for next session
- US market opening proximity

### Output:
- GAP UP / GAP DOWN / NO GAP
- Probable gap size (points)
- Hold / Hedge / Exit recommendation

---

## 5️⃣ OTM OPTIONS SELECTION LOGIC

OTM strikes are selected using:
- Expected move (points)
- Time-to-event
- Volatility expansion probability

### Rules:
- High confidence → Slight OTM
- Medium confidence → Safer OTM
- Low confidence → Avoid or hedge

Bot always gives:
- Primary Strike
- Secondary Strike (backup)

---

## 6️⃣ EXIT / HOLD / TRAIL LOGIC (DYNAMIC)

Exit is NOT fixed-time.

Bot evaluates:
- Speed of move
- Reaction at levels
- Next important time proximity

Possible commands:
- EXIT NOW
- HOLD till next event
- TRAIL aggressively
- TRAIL conservatively

Holding can range from **5 minutes to 1+ hour**.

---

## 7️⃣ LEVEL GENERATION

Levels are generated as:
> Current Price ± Expected Points

Example:
- Current Price: 25600
- Expected Move: 64 points
- Level: 25664 / 25536

Levels are **reaction zones**, not targets.

---

## 8️⃣ MESSAGE DELIVERY RULE

- Messages are sent **5–10 minutes BEFORE** important time
- Includes:
  - Current price
  - VIX
  - Time remaining
  - Reason (WHY)
  - Risk instruction

---

## 9️⃣ RISK MANAGEMENT (MANDATORY)

- Max risk per trade: **5%**
- No revenge trades
- No trades in low-volatility sideways phases
- Bot can command **NO TRADE DAY**

---

## 🔟 COMMAND FLOW (USER → BOT)

Supported commands:
- NIFTY
- SENSEX
- BTC
- GAP?
- OTM?
- HOLD?
- EXIT?
- NEXT TIME?
- WHY?
- RISK?
- BACKTEST?

Bot always responds in structured format.

---

⚠️ Disclaimer:
AstroTradeRB is a decision-support system.
Final execution responsibility lies with the trader.
