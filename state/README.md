# AstroTradeRB — Bot State System

The bot always operates in ONE state at a time.
State defines *what the bot is allowed to do right now*.

## States

- IDLE  
  Waiting, observing, no active intent

- ANALYZING  
  Processing logic, time windows, astro + market data

- SIGNAL  
  Tradeable insight generated (but not yet executed)

- HOLDING  
  Position is active and being managed

- EXITED  
  Trade closed, context preserved

- NO_TRADE  
  Guardrails blocked action (risk, volatility, rules)

## Rules

- Bot cannot skip states
- Only ONE state can exist at a time
- EXITED always resets system back to IDLE
- NO_TRADE overrides all signals
- State must be checked before every response

## Purpose

State prevents:
- Duplicate signals
- Overtrading
- Conflicting instructions
- Emotional or reactive behavior
