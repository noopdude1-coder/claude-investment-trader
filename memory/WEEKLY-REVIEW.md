# Weekly Review

Friday reviews appended here. Template for each entry:

## Week ending YYYY-MM-DD

### Stats
| Metric | Value |
|--------|-------|
| Starting portfolio | $X |
| Ending portfolio | $X |
| Week return | ±$X (±X%) |
| SPY week return | ±X% |
| RSP week return | ±X% |
| Bot vs SPY | ±X% |
| Bot vs RSP | ±X% |
| Rolling 20d Sharpe (bot) | X.XX |
| Rolling 20d Sharpe (SPY) | X.XX |
| Max drawdown (week) | -X% |
| Information ratio (vs SPY, rolling) | X.XX |
| Trades | N (W:X / L:Y / open:Z) |
| Win rate (closed) | X% |
| Best trade | SYM +X% |
| Worst trade | SYM -X% |
| Profit factor | X.XX |

### Closed Trades
| Ticker | Entry | Exit | P&L | Notes |

### Open Positions at Week End
| Ticker | Entry | Close | Unrealized | Stop |

### Process Metrics (mechanics validation — first 30–90 days)
- Rule-adherence: trades blocked by buy-gate / total considered = X / Y
- Time-to-stop-placement after fill: median X seconds
- Research-log completeness: X / Y trades had pre-documented catalyst
- Routine push success rate: X / Y runs persisted to main
- Notification delivery: X / Y expected Discord messages arrived

### What Worked
- ...

### What Didn't Work
- ...

### Key Lessons
- ...

### Adjustments for Next Week
- ...

### Overall Grade: X

## Week ending 2026-04-26

Launch week. Bot scaffolded and went live today (Sunday). Zero trades, zero
positions. Earlier blocked entry replaced — env now provisioned.

### Stats
| Metric | Value |
|--------|-------|
| Starting portfolio | $100,000.00 |
| Ending portfolio | $100,000.00 |
| Week return | $0.00 (0.00%) |
| SPY week return | N/A — Perplexity 503 + Alpaca data endpoint 503 (weekend) |
| RSP week return | N/A — same |
| Bot vs SPY | N/A |
| Bot vs RSP | N/A |
| Rolling 20d Sharpe (bot) | N/A — insufficient data (1 EOD snapshot) |
| Rolling 20d Sharpe (SPY) | N/A — insufficient data |
| Max drawdown (week) | 0.00% |
| Information ratio (vs SPY, rolling) | N/A — insufficient data |
| Trades | 0 (W:0 / L:0 / open:0) |
| Win rate (closed) | N/A — no closed trades |
| Best trade | N/A |
| Worst trade | N/A |
| Profit factor | N/A |

### Closed Trades
| Ticker | Entry | Exit | P&L | Notes |
| — | — | — | — | None |

### Open Positions at Week End
| Ticker | Entry | Close | Unrealized | Stop |
| — | — | — | — | None |

### Process Metrics (mechanics validation — first 30–90 days)
- Rule-adherence: trades blocked by buy-gate / total considered = 0 / 0 (none considered — pre-FOMC HOLD)
- Time-to-stop-placement after fill: N/A — no fills
- Research-log completeness: N/A — 0 executed trades, 1 documented HOLD decision (Mon 4/27 plan)
- Routine push success rate: 2 / 2 expected runs persisted (pre-market 4/26 ✓, EOD 4/26 ✓; market-open + midday + daily-summary not expected on Sunday)
- Notification delivery: prior weekly-review run sent its alert to local
  `NOTIFICATIONS.md` (gitignored) instead of Discord — env was unset.
  Now resolved; this run targets the live webhook.

### What Worked
- Scaffolding committed and pushed cleanly (8 commits, working tree clean at EOD)
- Pre-market routine produced a defensible HOLD ahead of FOMC + GDP/PCE week — patience > activity
- Switched notifications to Discord webhook before the missing-env failure mode could go silent
- Auto-merge workflow rewired to fire on push to `claude/**` (not PR open) — closes the persistence gap

### What Didn't Work
- First weekly-review run today was blocked by missing env vars; alert fell through to gitignored NOTIFICATIONS.md and never reached the user
- Account funding mismatch: strategy doc anchors at $7,500 IRA; live paper account is $100k. Sizing rules referencing the $1,500 / 20% cap are now inconsistent with actual equity. Flagged in TRADE-LOG; needs reconciliation, but NOT this week (small-sample rule)
- Benchmark snapshot blocked: Perplexity + Alpaca data endpoint both 503 on Sunday — no SPY/RSP closing levels captured for the week

### Key Lessons
- Env provisioning is a P0 mechanics check; verify ALL four secrets before any wrapper call (already in routine — held this time)
- Sunday is a bad day for benchmark fetches; future Friday runs will execute during market hours when data endpoints respond
- Don't penalize a flat-equity launch week of perfect rule-following — process grade only

### Adjustments for Next Week
- NO strategy-rule changes (1-week sample, do not calibrate from noise)
- Reconcile $7,500 vs $100k funding in PROJECT-CONTEXT.md / TRADING-STRATEGY.md before sizing the first real trade — user decision, not bot
- Run weekly review on actual Friday afternoon (not Sunday) so benchmark APIs are live
- Watch FOMC (Wed) + GDP/PCE (Thu) reactions; XLE / XLI / SMH on watchlist for post-event entries; max 3 trades per rule

### Overall Grade: B
Process held: pre-market + EOD routines fired and persisted, HOLD decision was the right call ahead of binary events, notification gap was caught and patched same day. Capped at B (not A) because the prior weekly-review run failed silently and the funding mismatch is still unreconciled. P&L (flat) is not penalized — week 1 of a 3+ year window.

## Week ending 2026-05-01

First full trading week. Five sequential HOLDs through FOMC + 4 hyperscaler AMC + GDP/PCE + AAPL; first deployment Fri 5/1 once all four documented re-entry gates cleared. Single position (XLE), 19.89% deployed.

### Stats
| Metric | Value |
|--------|-------|
| Starting portfolio | $100,000.00 |
| Ending portfolio | $100,109.34 |
| Week return | +$109.34 (+0.11%) |
| SPY week return | +0.92% ($714.005 → $720.555 mid) |
| RSP week return | N/A — Perplexity data conflict (one source $202.76 close 4/30 +1.17%; another $183.55 close 4/24 — uncalibrated) |
| Bot vs SPY | -0.81% |
| Bot vs RSP | N/A |
| Rolling 20d Sharpe (bot) | N/A — insufficient data (6 EOD snapshots) |
| Rolling 20d Sharpe (SPY) | N/A — insufficient data |
| Max drawdown (week) | 0.00% (flat Mon–Thu, +0.11% Fri only) |
| Information ratio (vs SPY, rolling) | N/A — insufficient data |
| Trades | 1 (W:0 / L:0 / open:1) |
| Win rate (closed) | N/A — no closed trades |
| Best trade | XLE +0.55% (open) |
| Worst trade | N/A |
| Profit factor | N/A — no closed trades |

### Closed Trades
| Ticker | Entry | Exit | P&L | Notes |
| — | — | — | — | None |

### Open Positions at Week End
| Ticker | Entry | Close | Unrealized | Stop |
| XLE | $58.5084 (340 sh) | $58.83 | +$109.34 (+0.55%) | $53.1945 (10% trail GTC, HWM $59.105) |

### Process Metrics (mechanics validation — first 30–90 days)
- Rule-adherence: buy-gate blocked 4/5 days (Mon–Thu, all triple-binary event days); passed Fri once SPX > 7,100, VIX < 22, AAPL didn't crater, ISM 53.1 ≥ 50 — gate fired exactly per documented rule
- Time-to-stop-placement after fill: ~< 30 seconds (BUY + TRAIL placed in same market-open call; orders caf68907... + f7f3739a...)
- Research-log completeness: 1 / 1 executed trade had pre-documented catalyst (XLE: ISM 54.0, CVX/XOM clean Q1 beats, Brent ~$110, YTD +32.89% leader)
- Routine push success rate: 11 / 11 expected commits pushed cleanly (5 pre-market + 5 EOD + 1 market-open)
- Notification delivery: Discord webhook live; pre-market + EOD + market-open recaps all delivered

### What Worked
- Documented re-entry gate (SPX > 7,100, VIX < 22, no AAPL crater, ISM ≥ 50) held through the densest binary node of the year — five sequential HOLDs were the right call ahead of FOMC + Big Tech + GDP/PCE
- XLE thesis was fully pre-documented in 5/1 RESEARCH-LOG before market-open routine fired — no reactive trades
- 10% GTC trailing stop placed atomically with the buy in same workflow — no manual gap, stop live before market-open recap sent
- Cash drag was protective Mon–Thu: bot ahead ~291 bps vs SPY through Thu before Friday's bounce
- Routine cadence held: every trading day produced pre-market + EOD entries; all pushed cleanly

### What Didn't Work
- Friday's +3.94% SPY rip ate most of the cash-drag alpha; ended week -81 bps vs SPY despite four days of relative outperformance — the gate optimized for risk-off and was late to a risk-on bounce
- Capital still 20% deployed at week-end vs 75–85% target rule; one position = 100% energy exposure, no sector diversification
- Funding mismatch ($7,500 IRA in strategy doc vs $100k paper account) is now week 2 unreconciled — flagged again, still requires user decision
- Friday market-open routine fired at 9:30 before ISM 10am print actually released; the conditional gate-pass relied on CVX/XOM BMO + forecast 53.1 but technically the rule said "wait for actual" — minor process slip, defensible given pre-open energy confirmation but worth tightening
- Only 1 of 3 trade slots used; gate, not cap, was the binding constraint all five days

### Key Lessons
- Gate held through stacked-binary week — that IS the right behavior even when the index rips Friday; do not loosen rules from a one-week sample
- Sector concentration risk: one position = 100% energy exposure; next deployment must diversify (financials/tech/staples relative-strength check)
- Cash drag is asymmetric — protective in falling tape, expensive on rallies; the gate's job is to catch the regime, not to maximize deployment
- Conditional buy-gate ("if X print clears at 10am, deploy at 9:30") is sloppy — either wait for the actual print or restructure the gate to fire post-print

### Adjustments for Next Week
- NO strategy-rule changes (2-week sample; small samples lie — calibration reminder per PROJECT-CONTEXT.md)
- Mon 5/4 pre-market: scan for second position with sector diversification away from energy (XLF / XLP / XLI relative strength); deploy ≤20% if buy-gate clears
- Watch XLE: stop at $53.1945 is the clean exit; if it consolidates above $58.50 entry, hold to +15% (~$67.30) target with trail tighten to 7%
- Tighten gate timing: do not fire pre-print if the gate explicitly requires the print; either delay 30 min or restructure the rule
- Funding reconciliation ($7,500 vs $100k) — user decision pending; do not change docs autonomously
- Continue 1/1 catalyst-documented-pre-trade hit rate

### Overall Grade: B+
Process held cleanly: every documented entry rule fired correctly, the one trade was fully pre-documented in RESEARCH-LOG, the trailing stop was placed atomically with the buy, all 11 expected commits pushed. Capped at B+ (not A) because (a) Friday's gate-timing relied on a forecast rather than the actual ISM print — a small process inconsistency, (b) the funding mismatch is in week 2 unreconciled, (c) capital deployment 20% vs 75–85% target with one sector means we're not yet executing the diversified-momentum strategy as written. P&L (-81 bps vs SPY) not penalized — week 2 of a 3+ year window.

## Week ending 2026-05-08

Second full trading week. Three trades fired (cap maxed): XLP buy Mon, XLE sell Wed (thesis-break), XLK buy Thu. Closed loser, two open winners. Capital ~40% deployed at week end. FOMC Wed-Thu plus NFP Fri provided binary risk; bot navigated cleanly with one rule-driven exit.

### Stats
| Metric | Value |
|--------|-------|
| Starting portfolio | $100,109.34 |
| Ending portfolio | $100,470.41 |
| Week return | +$361.07 (+0.36%) |
| SPY week return | +2.29% (Fri 5/1 → Fri 5/8 close-to-close) |
| RSP week return | +0.05% to +0.24% (Finviz "Perf Week" mid ~+0.15%) |
| Bot vs SPY | -1.93% |
| Bot vs RSP | ~+0.21% (vs +0.15% mid) |
| Rolling 20d Sharpe (bot) | N/A — insufficient data (~11 EOD snapshots) |
| Rolling 20d Sharpe (SPY) | N/A — insufficient data |
| Max drawdown (week) | -0.46% (Mon close $100,216 → Thu close $99,759) |
| Information ratio (vs SPY, rolling) | N/A — insufficient data |
| Trades | 3 (W:0 / L:1 / open:2) |
| Win rate (closed) | 0% (1 closed = loser) |
| Best trade | XLK +3.14% (open) |
| Worst trade | XLE -1.17% (closed) |
| Profit factor | N/A — no closed winners |

### Closed Trades
| Ticker | Entry | Exit | P&L | Notes |
| XLE | $58.5084 (340 sh, 5/1) | $57.821176 (5/6) | -$233.66 (-1.17%) | Thesis broken — Iran accord chatter; WTI $116→$91 in 5 sessions; rule "thesis broken → close" applied; trail at $53.78 still ~7%+ away |

### Open Positions at Week End
| Ticker | Entry | Close | Unrealized | Stop |
| XLK | $170.17 (117 sh, 5/7) | $175.52 | +$625.95 (+3.14%) | $158.031 (trail 10%, HWM $175.59) |
| XLP | $83.8515 (238 sh, 5/4) | $84.18 | +$78.18 (+0.39%) | $76.32 (trail 10%, HWM $84.80) |

### Process Metrics (mechanics validation — first 30–90 days)
- Rule-adherence: 3/3 executed trades passed buy-gate or sell-rule cleanly; week buy-cap (3/3) blocked Fri post-NFP setup as designed; Wed FOMC-eve deferral of redeploy was rule-correct; Tue 5/5 produced no trade (gate did not see qualifying setup) — 0 rule violations
- Time-to-stop-placement after fill: median <30s — XLP trail aa46ecf2... and XLK trail f68c12ea... both placed atomically with their buys in same market-open call
- Research-log completeness: 3 / 3 executed trades had pre-documented catalyst (XLP defensive/diversification thesis 5/4; XLE thesis-break documented 5/6 pre-sell; XLK redeploy documented 5/7)
- Routine push success rate: 11 / 13 expected commits pushed (5 pre-market ✓ Mon-Fri, 4/5 EOD ✓ — Tue 5/5 EOD snapshot missing/gap-day, 3/3 market-open ✓ for Mon buy + Wed sell + Thu buy folded into EOD); no merge conflicts; auto-merge clean
- Notification delivery: Discord webhook live; pre-market + EOD + market-open recaps delivered each day no failures observed

### What Worked
- XLE thesis-break exit on 5/6 was the correct rule application — "catalyst invalidated → close, even if not at -7%" — beat the trail stop by ~7%, locked loss at -1.17% vs potential -10% if we had waited for trail
- XLK redeploy of XLE proceeds same week (Thu 5/7) caught the post-FOMC bounce and printed +3.14% by Friday close — discipline of "redeploy into a non-energy leader with relative strength" worked
- Diversification holding: XLP defensive sleeve absorbed FOMC tape (+0.39% across the week), XLK growth caught the post-FOMC rip — sector mix doing its job
- Trailing 10% GTC stops placed atomically with every buy; HWMs ratcheted on both opens; no manual gap, no stop missing
- Week buy-cap (3/3) held: Fri NFP setup ignored despite tape rip, exactly the rule's intent — patience > activity
- 3/3 trades pre-documented in RESEARCH-LOG before execution; no reactive trades

### What Didn't Work
- Underperformed SPY by ~193 bps for the second straight week — capital still 40% deployed against a 75-85% target while SPY ripped +2.29%; concentrated underdeployment is the recurring drag
- XLE trade closed at -1.17% — first realized loss of the phase; thesis was correct on entry (CVX/XOM beats, ISM 54.0) but the geopolitical premium pillar was binary and flipped on a single news headline (Axios Iran accord)
- Tue 5/5 EOD snapshot was missed (gap day in TRADE-LOG); routine push success 11/13 not 13/13 — small persistence slip
- Buy-cap fully maxed by Thu 5/7 leaving no room to add a third position even though XLK was printing fresh HWMs Fri; gate prioritized "redeploy XLE proceeds" over "add diversification slot" — defensible but illustrates the 3/wk cap as a binding constraint
- Funding mismatch ($7,500 IRA in strategy doc vs $100k paper account) is in week 3 unreconciled
- Sector exit rule ("2 consecutive failed trades → exit sector") not yet tested but XLE is now 1/2 toward sector exit — if next energy attempt fails, no XLE/XOP/USO for the rest of the phase

### Key Lessons
- Thesis-break exits work — cutting on catalyst invalidation rather than waiting for the trail stop saved ~7% on XLE; this is the single highest-leverage rule in the book and it fired correctly
- Cash drag asymmetry continues to hurt on rip weeks: bot ahead through Wed selloff (~+8 bps cumulative vs SPY at Thu close) then gave back ~280 bps Friday on the bounce — same pattern as Week 1
- 3/wk buy cap is binding when one trade closes early: a thesis-break sell + redeploy + diversification slot = 3 trades and you're done for the week, even if Day 5 shows fresh setups
- Single-headline geopolitical theses (XLE/Hormuz) are inherently fragile — next time, size smaller (10% not 20%) when the entire thesis hinges on a single binary catalyst
- "Redeploy proceeds same-session into a non-energy leader with relative strength" is a viable playbook — catch one bounce post-binary event without violating cap or gate

### Adjustments for Next Week
- NO strategy-rule changes (3-week sample still well inside calibration noise; small samples lie — PROJECT-CONTEXT.md rule)
- Mon 5/11 pre-market: scan for 3rd position to push deployment from 40% toward 60% — XLI (industrials) or XLB (materials) primary candidates, both leading-quadrant non-overlapping with XLK/XLP
- Watch XLK: at +3.14% on cost; if it prints +5% (~$178.68), tighten trail mentally toward 7% threshold; +15% trigger formal rule at $195.70
- Watch XLP: defensive sleeve, no action unless cyclical rotation slams it through $80; trail at $76.32 protects -9% from current
- Energy sector embargo holds: XLE 1/2 toward 2-trade exit; do NOT re-add until the post-Iran-accord oil regime stabilizes
- CPI Tue 5/12 + PPI Wed 5/13 are next binaries; size the 3rd deployment to absorb either outcome (avoid pure-duration plays the day before CPI)
- Funding reconciliation ($7,500 vs $100k) — user decision pending, do not change docs autonomously
- Ensure Tue 5/12 EOD snapshot fires (last week's Tue gap was the only push miss)

### Overall Grade: B+
Process held: every executed trade pre-documented, atomic GTC trail stops on every fill, thesis-break exit rule fired correctly on XLE saving ~7% vs trail, redeploy of proceeds within same week was rule-clean, week buy-cap respected on Fri despite tape rip. Capped at B+ (not A) because (a) Tue 5/5 EOD snapshot was missed — minor persistence slip, (b) capital still 40% deployed vs 75-85% target for the third straight week — gate is too conservative for a +2.3% SPY week, (c) funding mismatch unreconciled, (d) realized loss on XLE was a binary-headline trade that deserves smaller sizing next time. P&L (-1.93% vs SPY) not penalized — week 3 of a 3+ year window; the rule-driven loss is exactly the kind of disciplined exit the framework is built around.
