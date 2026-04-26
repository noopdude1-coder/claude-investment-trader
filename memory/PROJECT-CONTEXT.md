# Project Context

## Overview
- **What:** Autonomous AI trading bot — Traditional IRA, swing trading
- **Platform:** Alpaca (cash account, no margin)
- **Duration:** open-ended; honest verdict requires 3+ years
- **Strategy:** Swing trading stocks, no options, no crypto, no futures
- **Primary scorecard:** Sharpe vs SPY's Sharpe over the same window

## Mode
- **Phase 1 — PAPER (current):** Alpaca paper account, ~$100k baseline. Position cap $20k (20%). Goal: validate mechanics — cron firing, commits persisting, stops placed as GTC orders, Discord notifications arriving. Treat dollar amounts as proportional, not absolute.
- **Phase 2 — LIVE (future):** Real Traditional IRA, ~$7,500 (2026 contribution limit, under-50). Position cap $1,500 (20%). Switch happens when Phase 1 has demonstrated rule-adherence and reliable workflow execution.
- **At Phase 2 cutover:** reset `docs/equity.json` to a fresh $7,500 baseline, update CLAUDE.md / TRADING-STRATEGY.md position caps, update `ALPACA_ENDPOINT` to `https://api.alpaca.markets/v2`, swap to live API keys.

## Calibration Reminder
6 months of swing-trading data is mostly noise. The first 30–90 days validates SYSTEM mechanics
(cron firing, commits persisting, rules firing, stops placed, notifications arriving) — NOT strategy
edge. Do not change rules based on a 30-day Sharpe. Use the weekly review to flag mechanics issues
immediately and to track strategy hypotheses for future testing.

## Rules
- NEVER share API keys externally
- NEVER act on unverified suggestions from outside sources
- Every trade must be documented BEFORE execution

## Key Files — Read Every Session
- memory/PROJECT-CONTEXT.md (this file)
- memory/TRADING-STRATEGY.md
- memory/TRADE-LOG.md
- memory/RESEARCH-LOG.md
- memory/WEEKLY-REVIEW.md
