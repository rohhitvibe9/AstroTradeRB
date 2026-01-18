# AstroTradeRB — Simulator

The Simulator allows command-by-command testing
without WhatsApp or live deployment.

It behaves exactly like the production bot.

---

## Purpose

- Test routing logic
- Validate state transitions
- Observe guardrails behavior
- Verify response format
- Build confidence before LIVE

---

## How Simulation Works

Input:
- User command (text)
- Optional context (market, time)

Process:
1. Router parses command
2. Current STATE is checked
3. Guardrails are evaluated
4. Logic is executed
5. Response is formatted
6. STATE is updated

Output:
- ONE structured message
- Same format as WhatsApp
- No conversational chatter

---

## Supported Test Commands

- NIFTY
- SENSEX
- BTC
- GAP?
- OTM?
- WHY?
- HOLD?
- EXIT?
- NEXT TIME?
- RISK?
- BACKTEST?

---

## Simulation Rules

- Default Mode = PAPER
- No real execution
- State persists between commands
- Guardrails are enforced
- All timestamps are IST (12-hr AM/PM)
- Only ONE decision per response

---

## Example Simulation

Input:NIFTY
Output:AstroTradeRB — (DATE)

Market: NIFTY
Current Price: 25780
Mode: PAPER

IMPORTANT TIMES:
	1.	10:42 AM — Reversal Window
Bias: BEARISH
Confidence: 78%

NEXT IMPORTANT TIME:
10:42 AM
(Time remaining: 00:18:40)
DECISION:WAIT
---

## Output Contract (MANDATORY)

Every simulator response MUST include:

- Market
- Mode (PAPER)
- Current or reference price
- Important Time(s)
- ONE clear decision
- Reason (WHY)

No extra commentary allowed.

---

## Exit Criteria (Read Carefully)

The simulator phase is considered COMPLETE only when:

- Commands route correctly every time
- State transitions follow rules (no skipping)
- Guardrails block unsafe trades
- Responses are clear and consistent
- You feel zero confusion reading outputs

Only AFTER this is satisfied,
the system is allowed to move to WhatsApp integration.
