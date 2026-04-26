---
description: Manual trade helper with strategy-rule validation. Usage — /trade SYMBOL SHARES buy|sell
---

Execute a manual trade with full rule validation. Refuse if any rule fails.

Args: SYMBOL SHARES SIDE (buy or sell). If missing, ask.

1. Pull state: account, positions, quote SYMBOL (capture ask price P).
2. For BUY, validate:
   - Total positions after fill <= 6
   - Trades this week + 1 <= 3
   - SHARES * P <= 20% of equity ($1,500 cap at $7,500 starting equity)
   - SHARES * P <= available SETTLED cash (read `cash`, NOT `buying_power`;
     T+1 settlement on IRA cash accounts can leave unsettled proceeds in
     buying_power that aren't actually usable)
   - Catalyst documented (ask for thesis if not in today's RESEARCH-LOG)
   - Instrument is a stock
   If any fail, STOP and print the failed checks.
3. For SELL, confirm position exists with right qty. No other checks.
4. Print order JSON + validation results, ask "execute? (y/n)".
5. On confirm:
   bash scripts/alpaca.sh order '{"symbol":"SYM","qty":"N","side":"buy|sell","type":"market","time_in_force":"day"}'
6. For BUYs, immediately place 10% trailing stop GTC (same flow as market-open).
7. Log to memory/TRADE-LOG.md with full thesis, entry, stop, target, R:R.
8. bash scripts/clickup.sh with trade details.
