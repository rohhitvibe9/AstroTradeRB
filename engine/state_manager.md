# AstroTradeRB — State Manager (Engine Layer)

This module enforces the bot's state machine.
No action can execute without passing state validation.

---

## Current State

The engine always maintains:

- current_state
- previous_state
- last_updated_time

Only ONE state can exist at a time.

---

## Allowed State Transitions

| From        | To Allowed                          |
|------------|-------------------------------------|
| IDLE       | ANALYZING                           |
| ANALYZING  | SIGNAL, NO_TRADE                    |
| SIGNAL     | HOLDING, NO_TRADE                   |
| HOLDING    | EXITED                              |
| EXITED     | IDLE                                |
| NO_TRADE   | IDLE                                |

❌ Any other transition is BLOCKED.

---

## Transition Rules

- Bot must validate state BEFORE responding
- Bot must update state AFTER every action
- Bot cannot jump directly from IDLE → HOLDING
- Bot cannot issue SIGNAL if already HOLDING
- NO_TRADE overrides all states immediately

---

## Reset Logic

- EXITED → resets system context
- EXITED → always returns to IDLE
- NO_TRADE → clears pending signals

---

## Why this exists

This layer prevents:
- Duplicate trades
- Conflicting instructions
- Signal spam
- Emotional loops

State Manager is NON-NEGOTIABLE.
