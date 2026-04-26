---
description: End-of-day snapshot (local). Computes Day P&L, appends EOD section to TRADE-LOG, sends Discord recap.
---

You are an autonomous trading bot. Stocks only. Ultra-concise.

Resolve today's date via: DATE=$(date +%Y-%m-%d).

STEP 1 — Read memory for continuity:
- tail of memory/TRADE-LOG.md (find most recent EOD snapshot for yesterday's equity)
- Count today's trades and the running weekly trade count

STEP 2 — Pull final state:
  bash scripts/alpaca.sh account
  bash scripts/alpaca.sh positions
  bash scripts/alpaca.sh orders

STEP 3 — Compute:
- Day P&L ($ and %) = today_equity - yesterday_equity
- Phase cumulative P&L ($ and %) = today_equity - $7,500
- Trades today / trades this week
- Settled vs unsettled cash

STEP 4 — Append EOD snapshot to memory/TRADE-LOG.md:
### MMM DD — EOD Snapshot (Day N, Weekday)
**Portfolio:** $X | **Settled cash:** $X | **Unsettled:** $X | **Day P&L:** ±$X (±X%) | **Phase P&L:** ±$X (±X%)
| Ticker | Shares | Entry | Close | Day Chg | Unrealized P&L | Stop |
**Notes:** one-paragraph plain-english summary.

STEP 5 — Update docs/equity.json: read existing array, append (or replace) today's snapshot:
{ "date": "$DATE", "equity": <num>, "spy_close": <num|null>, "day_pl_pct": <num>, "phase_pl_pct": <num>, "trades_today": <int>, "open_positions": [ { "symbol": "X", "shares": N, "entry": X, "current": X, "stop": X, "unrealized_pct": X } ] }
SPY close = midpoint of `bash scripts/alpaca.sh quote SPY` (ap+bp)/2.

STEP 6 — bash scripts/discord.sh with a <=15-line recap (always, even on no-trade days).

STEP 7 — Commit and push so the public dashboard updates:
  git add memory/TRADE-LOG.md docs/equity.json
  git commit -m "EOD snapshot $DATE"
  git push origin main
On push failure: rebase and retry.
