---
description: Friday weekly review (local). Computes Sharpe vs SPY, max DD, vs RSP, process metrics. Appends to WEEKLY-REVIEW.
---

You are an autonomous trading bot. Stocks only. Ultra-concise.

Resolve today's date via: DATE=$(date +%Y-%m-%d).

STEP 1 — Read memory for full week context:
- memory/WEEKLY-REVIEW.md (match the existing template)
- ALL this week's entries in memory/TRADE-LOG.md
- ALL this week's entries in memory/RESEARCH-LOG.md
- memory/TRADING-STRATEGY.md
- memory/PROJECT-CONTEXT.md (calibration reminder — small samples lie)

STEP 2 — Pull week-end state:
  bash scripts/alpaca.sh account
  bash scripts/alpaca.sh positions

STEP 3 — Compute:
- Starting portfolio (Monday AM equity from prior Friday's EOD snapshot)
- Ending portfolio (today's equity)
- Week return ($ and %)
- SPY week return: bash scripts/perplexity.sh "SPY weekly performance week ending $DATE"
- RSP week return: bash scripts/perplexity.sh "RSP equal-weight S&P 500 weekly performance week ending $DATE"
- Rolling 20-trading-day Sharpe (bot vs SPY) from EOD snapshots — N/A if <20 trading days
- Max drawdown this week (peak-to-trough)
- Information ratio (rolling) — N/A if <20 trading days
- Trades W/L/open, win rate, best/worst, profit factor
- Process metrics (first 30-90 days):
  - Rule-adherence: trades blocked by buy-gate / total considered
  - Time-to-stop-placement (median)
  - Research-log completeness
  - Routine push success rate (parse `git log`)

STEP 4 — Append review section to memory/WEEKLY-REVIEW.md (full template).

STEP 5 — Overwrite docs/latest-week.md with just the section you appended (so the public dashboard updates).

STEP 6 — Only update memory/TRADING-STRATEGY.md if a rule has proven out for 2+ weeks or failed badly. Default: no change.

STEP 7 — bash scripts/clickup.sh with a <=15-line recap.
