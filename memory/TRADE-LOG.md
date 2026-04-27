# Trade Log

## Day 0 — EOD Snapshot (pre-launch baseline)
**Portfolio:** $7,500.00 | **Cash:** $7,500.00 (100%) | **Day P&L:** $0 | **Phase P&L:** $0

No positions yet. Bot launches tomorrow.

### Apr 26 — EOD Snapshot (Day 1, Sunday)
**Portfolio:** $100,000.00 | **Settled cash:** $100,000.00 | **Unsettled:** $0.00 | **Day P&L:** $0.00 (0.00%) | **Phase P&L:** $0.00 (0.00%)

No open positions.

**Notes:** Sunday — US equity markets closed, no trading activity. Alpaca paper account active and funded at $100,000.00 (note: TRADING-STRATEGY.md / PROJECT-CONTEXT.md reference a $7,500 IRA baseline — actual paper account is $100k; using $100k as the Phase baseline going forward to keep dashboard math sane. User should reconcile the strategy doc.) `last_equity` from Fri Apr 24 = $100,000 → Day P&L = $0. SPY mid = $714.005. Zero trades today, zero this week. Tomorrow (Mon Apr 27): pre-market scan → market-open workflow if buy gate passes.

### Apr 27 — EOD Snapshot (Day 2, Monday)
**Portfolio:** $100,000.00 | **Settled cash:** $100,000.00 | **Unsettled:** $0.00 | **Day P&L:** $0.00 (0.00%) | **Phase P&L:** $0.00 (0.00%)

No open positions.

**Notes:** First live trading day of the week — zero trades executed. Pre-market and market-open workflows apparently did not pass the buy gate (no orders, no fills, full $100k still in settled cash). SPY mid at EOD = $714.895 (+$0.89 vs yesterday's $714.005, ~+0.12%); we're flat so we underperformed SPY on the day by ~12 bps. 0 trades today, 0 trades this week (cap 3/wk untouched). Buying power $200k is the 2x margin echo — IRA cash account uses settled cash only ($100k). T+1: nothing to settle. Tomorrow (Tue Apr 28): pre-market scan → market-open; if buy gate passes, deploy first 1-2 positions sized at ≤20% ($20k each) with mandatory 10% trailing stops as GTC orders.
