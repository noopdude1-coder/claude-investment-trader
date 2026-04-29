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

### Apr 28 — EOD Snapshot (Day 3, Tuesday)
**Portfolio:** $100,000.00 | **Settled cash:** $100,000.00 | **Unsettled:** $0.00 | **Day P&L:** $0.00 (0.00%) | **Phase P&L:** $0.00 (0.00%)

No open positions.

**Notes:** Second straight no-trade day. Buy gate did not pass at market-open; full $100k still parked in settled cash. SPY mid at EOD = $711.555 (-$3.34 vs yesterday's $714.895, ~-0.47%) — we're flat so we beat SPY by ~47 bps on the day. 0 trades today, 0 trades this week (cap 3/wk untouched). Cumulative through Day 3 from Apr 26 baseline: bot flat (0 bps), SPY -34 bps ($714.005 → $711.555) — bot ahead by ~34 bps purely on cash drag avoiding the dip. Patience > activity holding, but capital is still 100% idle three sessions in. Tomorrow (Wed Apr 29): pre-market scan should look harder at sector momentum; if any name passes buy gate, deploy first position sized ≤20% ($20k) with mandatory 10% trailing stop as GTC.

### Apr 29 — EOD Snapshot (Day 4, Wednesday)
**Portfolio:** $100,000.00 | **Settled cash:** $100,000.00 | **Unsettled:** $0.00 | **Day P&L:** $0.00 (0.00%) | **Phase P&L:** $0.00 (0.00%)

No open positions.

**Notes:** Third consecutive no-trade day. Buy gate did not pass at market-open; full $100k still parked in settled cash. SPY post-close quote returned ap=0 (stale ask), bid $689.60 — using bid as proxy close. If the bid is representative, SPY fell ~3.1% today vs yesterday's $711.555 mid; bot flat means we beat SPY by ~310 bps on the day, but treat the SPY number with caution given the one-sided quote. 0 trades today, 0 trades this week (cap 3/wk untouched). Cumulative through Day 4 from Apr 26 baseline: bot flat (0 bps); SPY (using today's bid proxy) ~-3.4% from $714.005 — bot ahead by ~340 bps on cash drag during a possible market drop. Capital still 100% idle four sessions in — patience is paying right now, but the buy gate needs to fire eventually to actually generate alpha rather than just avoid drawdown. Tomorrow (Thu Apr 30): pre-market scan; if SPY drop is real, look for sector leaders that held up (relative strength) for first deployment ≤20% ($20k) with mandatory 10% trailing stop as GTC.
