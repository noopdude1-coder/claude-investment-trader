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

### May 01 — Market-Open Trade (Day 6, Friday)

**BUY XLE 340 @ $58.5084** | Cost: $19,892.86 (19.89% of $100k equity) | Stop: trailing 10% GTC, initial $52.623 (HWM $58.47)
- Thesis: ISM April 54.0 (vs 53.1 fcst, 52.7 prior) = strongest expansion since May 2022. CVX Q1 EPS $1.41 vs $0.95 (biggest beat since Oct 2020); XOM $1.16 vs $1.00 — both clean prints, "little changed" premarket. WTI ~$106 (Strait of Hormuz blocked since Feb). XLE YTD leader +32.89% as of 4/29. All four documented re-entry gates passed: SPX > 7,100, VIX < 22, AAPL no crater, ISM ≥ 50.
- Target: +15-20% (~$67.30-$70.20). R:R ≥ 1.5-2:1.
- Order IDs: BUY caf68907..., TRAIL f7f3739a...
- Trades this week: 1/3. Positions: 1/6.

### Apr 30 — EOD Snapshot (Day 5, Thursday)
**Portfolio:** $100,000.00 | **Settled cash:** $100,000.00 | **Unsettled:** $0.00 | **Day P&L:** $0.00 (0.00%) | **Phase P&L:** $0.00 (0.00%)

No open positions.

**Notes:** Fourth consecutive no-trade trading day; first full week ends with zero deployments. Buy gate did not pass at market-open again — full $100k still parked in settled cash. SPY post-close quote again one-sided (ap=0 stale ask, bid $693.23) — using bid as proxy close. vs yesterday's $689.60 bid proxy, ~+0.53% on the day; bot flat means SPY beat us by ~53 bps today. Cumulative through Day 5 from Apr 26 baseline: bot flat (0 bps); SPY (today's bid proxy) ~-2.91% from $714.005 — bot still ahead by ~291 bps purely on cash drag avoiding the Apr 29 leg down. 0 trades today, 0 trades this week (cap 3/wk fully unused). Five sessions in, capital 100% idle — gate is doing its job in a falling tape but we're now leaving alpha on the table on bounce days. Tomorrow (Fri May 1): weekly-review (Sharpe vs SPY, max DD, vs RSP, process metrics) plus pre-market scan; if any sector leader with relative strength clears the gate, deploy first ≤20% ($20k) position with mandatory 10% GTC trailing stop. Worth a re-examination of the buy-gate thresholds given five straight skips.

### May 01 — EOD Snapshot (Day 6, Friday)
**Portfolio:** $100,109.34 | **Settled cash:** $80,107.14 | **Unsettled:** $0.00 | **Day P&L:** +$109.34 (+0.11%) | **Phase P&L:** +$109.34 (+0.11%)

| Ticker | Shares | Entry | Close | Day Chg | Unrealized P&L | Stop |
|--------|--------|-------|-------|---------|----------------|------|
| XLE    | 340    | $58.5084 | $58.83 | -1.38% | +$109.34 (+0.55%) | $53.1945 (trail 10%, HWM $59.105) |

**Notes:** First trade of the phase fired today — XLE 340 @ $58.5084 ($19,892.86, 19.89% of equity) on the energy thesis (ISM 54.0, CVX/XOM clean Q1 beats, WTI ~$106 Hormuz, XLE YTD +32.89%). All four documented re-entry gates passed pre-open. Trailing 10% GTC stop live at $53.1945 with HWM $59.105 (XLE printed higher intraday before fading). XLE closed -1.38% on the day (lastday $59.65 → $58.83) but we entered below the lastday so we're still +0.55% on cost. SPY mid at EOD = $720.555 vs yesterday's bid proxy $693.23 → SPY ripped ~+3.94% on the day; with one position at 20% weight up only +0.55%, bot's day return ~+0.11% lagged SPY by ~383 bps. Cumulative from Apr 26 baseline: bot +0.11%, SPY +0.92% ($714.005 → $720.555) — SPY now ahead by ~81 bps as the cash-drag alpha got eaten on the bounce. 1 trade today, 1 trade this week (cap 3/wk; 2 left). Settled cash $80,107.14 fully available Monday (no sales pending T+1). Positions 1/6, capital 19.99% deployed (well below the 75-85% target — gate was conservative on a day SPY ripped +3.94%). Monday (May 4): pre-market scan; energy still leader, look for a second sector to diversify (financials/tech relative-strength check) — deploy second ≤20% position if gate passes. Watch XLE — if it gives back toward the $53.19 stop that's a -10% from HWM and a clean exit; if it closes >$58.50 entry consistently, hold.
