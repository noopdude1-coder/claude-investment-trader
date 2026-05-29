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

## Week ending 2026-05-15

Third full trading week. Zero trades — five sequential HOLDs through a triple-binary macro stack (CPI Tue, PPI Wed, Retail Sales Thu) plus the Powell→Warsh Fed-chair transition. Wed's triple-hot PPI (+6.0% YoY) tripped the pre-committed "defer-all-buys" rule; Friday's last buy slot was deliberately left unused despite 4 of 5 conditional gates clearing. Both carried positions (XLK, XLP) net green at week end. Capital ~40.5% deployed — fifth straight week below target.

### Stats
| Metric | Value |
|--------|-------|
| Starting portfolio | $100,470.41 |
| Ending portfolio | $100,629.11 |
| Week return | +$158.70 (+0.16%) |
| SPY week return | +0.16% ($737.395 → $738.55, bot-logged EOD mids) |
| RSP week return | N/A — Perplexity returned only intraday snapshots ($203.40 5/14), no clean week-ending closes |
| Bot vs SPY | ~+0.00% (essentially flat — first non-lagging week of the phase) |
| Bot vs RSP | N/A |
| Rolling 20d Sharpe (bot) | N/A — insufficient data (~14 EOD snapshots) |
| Rolling 20d Sharpe (SPY) | N/A — insufficient data |
| Max drawdown (week) | -0.53% (Thu close $101,163.65 → Fri close $100,629.11) |
| Information ratio (vs SPY, rolling) | N/A — insufficient data |
| Trades | 0 (W:0 / L:0 / open:2 carried) |
| Win rate (closed) | N/A — no closed trades |
| Best trade | XLK +3.37% (open) |
| Worst trade | N/A — no closed/losing trades (XLP +0.96% open is the laggard) |
| Profit factor | N/A — no closed trades |

### Closed Trades
| Ticker | Entry | Exit | P&L | Notes |
| — | — | — | — | None |

### Open Positions at Week End
| Ticker | Entry | Close | Unrealized | Stop |
| XLK | $170.17 (117 sh, 5/7) | $175.90 | +$670.41 (+3.37%) | $162.1935 (trail 10%, HWM $180.215) |
| XLP | $83.8515 (238 sh, 5/4) | $84.66 | +$192.42 (+0.96%) | $77.013 (trail 10%, HWM $85.57) |

### Process Metrics (mechanics validation — first 30–90 days)
- Rule-adherence: buy-gate considered 5/5 sessions, 0 trades placed — all 5 HOLDs rule-correct (CPI-eve Mon defer; CPI Tue defer; Wed PPI printed triple-hot +6.0% YoY / +1.4% MoM, tripping the pre-committed "Hot-PPI → defer ALL buys this week" rule; Thu honored it; Fri's five-gate scorecard cleared 4/5 — gate (e) Warsh-not-hawkish failed — so the last slot was left unused). 0 rule violations.
- Time-to-stop-placement after fill: N/A — no fills this week.
- Research-log completeness: N/A — 0 executed trades; 5/5 sessions had a fully pre-documented HOLD decision with rationale and conditional watchlist.
- Routine push success rate: 13 / 15 expected commits pushed (5 pre-market ✓ Mon-Fri, 5 EOD ✓ Mon-Fri, 3/5 midday ✓ — Tue/Wed/Thu logged; Mon 5/11 and Fri 5/15 midday produced no commit); no merge conflicts; auto-merge clean.
- Notification delivery: Discord webhook live; pre-market + EOD recaps delivered each day, no failures observed.

### What Worked
- Pre-committed "Hot-PPI → defer all buys" rule fired exactly as written. Wed's PPI breached both thresholds (+6.0% YoY vs +5.0% trigger; +1.4% MoM vs +0.5%); the rule removed Friday discretion and the bot honored it even with 4 of 5 conditional gates clearing — textbook ex-ante discipline.
- Navigated a triple-binary week (CPI / PPI / Retail Sales) plus a Fed-chair transition with zero portfolio damage and zero forced trades — patience > activity executed cleanly five days running.
- First non-lagging week of the phase: bot tracked SPY dead even (~+0.00%) vs ~-80 to -190 bps gaps in Weeks 1-2; XLP's defensive bid absorbed the CPI/PPI heat while XLK held its 52-wk-high regime.
- Both positions stayed thesis-intact and net green through three hot inflation prints — no -7% breach, no thesis-break, trail stops ratcheted (XLK HWM → $180.215, XLP HWM → $85.57) with no manual intervention.
- Every entry decision pre-documented in RESEARCH-LOG with explicit conditional gates set the prior day — the Friday five-gate scorecard was scored against criteria written Thursday, not invented same-day.

### What Didn't Work
- Capital still ~40.5% deployed vs the 75-85% target — fifth straight week under-deployed; the gate has now skipped a third position for 10+ consecutive sessions. Rule-compliant, but the structural gap is real.
- SPY pulled further ahead on the phase scoreboard: +3.44% vs bot +0.63% (~281 bps gap) — the under-deployment cost is cumulative even in a flat week.
- Two midday routine commits missed (Mon 5/11, Fri 5/15) — 13/15 push success, a minor persistence slip mirroring last week's Tue 5/5 gap.
- RSP benchmark unavailable for the third review running — Perplexity returns only intraday snapshots, no clean Friday closes; vs-RSP scoring still blocked.
- Funding mismatch ($7,500 IRA in strategy doc vs $100k paper account) is in week 4 unreconciled — still a pending user decision.

### Key Lessons
- A pre-committed, threshold-based rule ("Hot-PPI YoY ≥+5.0% → defer all buys") is far more robust than same-day discretion: it fired on Wednesday and made Friday's decision automatic despite a tempting 4/5 gate clear. Write the rule before the catalyst, not during it.
- A constructive tape on a hot print (SPY +0.64% on +6.0% PPI) is suspicious, not confirmatory — looking through it would have been a discretionary override of a working rule.
- The buy-gate's conservatism is genuinely costly on a multi-week rally, but five straight HOLDs across three macro binaries is the gate doing its job — the fix is deliberate Monday deployment on a clean tape, not loosening the gate from a 4-week sample.
- Defensive/growth sleeve pairing (XLP + XLK) is doing its diversification job: XLP caught the inflation-print bid, XLK held the AI-momentum regime — the two-sector mix tracked SPY flat through a noisy week.

### Adjustments for Next Week
- NO strategy-rule changes (4-week sample; small samples lie — PROJECT-CONTEXT.md calibration reminder). The hot-PPI rule and buy-gate both performed as designed.
- Mon 5/18 pre-market: capital deployment is the top priority — fresh 3-trade budget, no hot-PPI overhang. Deploy a 3rd position (XLU or XLI) at ~$19.5k with 10% trail GTC IF the buy-gate clears on a live quote with a same-day catalyst; target pushing 40% → 60%.
- Re-assess XLU once the Warsh chair vote / rate path is clearer — rate-sensitivity is the swing factor; XLI (Leading quadrant, AI-capex/defense) is the cleaner momentum alternative if the tape stays cyclical-bid.
- Watch XLK: +3.37% on cost, HWM $180.215, trail $162.1935; no stop-tighten trigger met (+15% threshold is $195.70). Semis ~49% weight = Trump-Xi summit headline beta — thesis-break cut applies on any chip-export shock.
- Ensure midday routine persists Mon-Fri — two missed commits this week (Mon/Fri); midday is part of the 5-run daily cadence.
- Funding reconciliation ($7,500 vs $100k) — week 4 pending; user decision, do not change docs autonomously.

### Overall Grade: A-
Strongest process week of the phase. Every one of five HOLD decisions was rule-correct; the pre-committed Hot-PPI defer-all-buys rule fired flawlessly and made Friday's last-slot decision automatic despite 4/5 conditional gates clearing — exactly why rules are written ex-ante. Three macro binaries plus a Fed-chair transition navigated with zero forced trades and zero portfolio damage; both positions thesis-intact and net green; bot tracked SPY dead even for the first time in the phase. Capped at A- (not A) because (a) two midday routine commits were missed — a recurring minor persistence slip, (b) capital is ~40.5% deployed for the fifth straight week — rule-compliant but the structural under-deployment gap to SPY keeps compounding, (c) the funding mismatch is week 4 unreconciled. P&L (flat) not penalized — grade reflects process adherence in the first 90 days, and this week's adherence was near-perfect.

## Week ending 2026-05-22

Fourth full trading week. Second consecutive zero-trade week — five sequential HOLDs through NVDA earnings (Wed AMC) and the first post-Warsh FOMC minutes (Wed 2pm). The pending XLI 3rd-position deploy was scored buy-gate PASS (catalyst included) by Thu and Fri, yet blocked both days by the bot's own "confirmed-strength tape by 11am" conditional — a gate not written in the rulebook. Both carried positions (XLK, XLP) net green; XLK printed a fresh phase high +6.01%. Capital ~40.8% deployed — tenth straight session below the 75-85% target.

### Stats
| Metric | Value |
|--------|-------|
| Starting portfolio | $100,629.11 |
| Ending portfolio | $101,187.76 |
| Week return | +$558.65 (+0.56%) |
| SPY week return | ~+1.2% ($738.55 5/15 → $747.47 5/22, Investing.com clean close; Perplexity cross-check ~+1.0%) |
| RSP week return | N/A — Perplexity returned only Monday/intraday snapshots ($202.80 5/18), no clean Fri 5/15 or 5/22 close |
| Bot vs SPY | -0.65% |
| Bot vs RSP | N/A |
| Rolling 20d Sharpe (bot) | ~3.4 annualized — FIRST computation (20 trading days just reached); small-sample noise, May 5 EOD snapshot reconstructed from Alpaca last_equity. Do not read edge into it. |
| Rolling 20d Sharpe (SPY) | N/A — phase-long stale/wide SPY EOD quotes (ap=0) prevent a clean daily return series |
| Max drawdown (week) | -0.09% (Mon close $100,737.03 → Tue close $100,643.02) |
| Information ratio (vs SPY, rolling) | N/A — no clean SPY daily series |
| Trades | 0 (W:0 / L:0 / open:2 carried) |
| Win rate (closed) | N/A — no closed trades |
| Best trade | XLK +6.01% (open) |
| Worst trade | N/A — no closed/losing trades (XLP +1.13% open is the laggard) |
| Profit factor | N/A — no closed trades |

### Closed Trades
| Ticker | Entry | Exit | P&L | Notes |
| — | — | — | — | None |

### Open Positions at Week End
| Ticker | Entry | Close | Unrealized | Stop |
| XLK | $170.17 (117 sh, 5/7) | $180.39 | +$1,195.74 (+6.01%) | $163.557 (trail 10%, HWM $181.73) |
| XLP | $83.8515 (238 sh, 5/4) | $84.80 | +$225.74 (+1.13%) | $78.0255 (trail 10%, HWM $86.695) |

### Process Metrics (mechanics validation — first 30–90 days)
- Rule-adherence: buy-gate considered 5/5 sessions, 0 trades placed. Mon–Wed HOLDs rule-correct (no same-day catalyst for XLI/XLU + two unhedged binaries — NVDA earnings, FOMC minutes — ahead). Thu & Fri: XLI scored buy-gate PASS on all six checks (catalyst included), but the bot's self-added "confirmed-strength tape by 11am" conditional did not clear — skips were defensible but driven by an unwritten gate, not the documented rules. 0 documented-rule violations.
- Time-to-stop-placement after fill: N/A — no fills this week.
- Research-log completeness: N/A — 0 executed trades; 5/5 sessions had a fully pre-documented decision (HOLD Mon–Wed, conditional-deploy plan Thu–Fri with explicit gates).
- Routine push success rate: 10 / 15 expected commits pushed (5 pre-market ✓ Mon–Fri, 5 EOD ✓ Mon–Fri, 0/5 midday — no midday commits all week); no merge conflicts; auto-merge clean.
- Notification delivery: Discord webhook live; pre-market + EOD recaps delivered each day, no failures observed.

### What Worked
- Five HOLDs through NVDA earnings + the first post-Warsh FOMC minutes — both binaries cleared with zero portfolio damage; XLK absorbed NVDA's -3% AH (a beat across the board plus a $91B Q2 guide, +$3.6B above consensus) without a thesis-break.
- XLK rode to a fresh phase high — +6.01% on cost, fresh HWM $181.73 Friday, trail ratcheted to $163.557 with no manual intervention.
- Both sleeves stayed thesis-intact and net green all week; the XLP defensive sleeve cushioned the two down sessions.
- Bot beat SPY on the week's risk-off days — defensive XLP sleeve + light deployment doing their job on a soft tape.
- Every session's decision pre-documented in RESEARCH-LOG with explicit conditional gates set the prior day.

### What Didn't Work
- Second consecutive zero-trade week; capital ~40.8% deployed — tenth straight session below target. Core Rule 2 ("target 75–85% deployed") has now been unmet for two full weeks.
- The XLI deploy was scored buy-gate PASS (all six checks, catalyst included) by Thu and Fri, yet blocked both days by an unwritten "confirmed-strength tape by 11am" conditional the bot layered on top of the rulebook. The binding constraint is now a self-imposed discretionary gate, not the documented rules.
- SPY pulled ~65 bps ahead on the week (+1.2% vs +0.56%); the phase gap to SPY persists (~240–280 bps depending on SPY proxy).
- Midday routine produced zero commits all week (10/15 push success, down from 13/15 last week) — a persistence regression.
- RSP benchmark unavailable for the fourth review running — Perplexity returns only Monday/intraday snapshots, no clean Friday closes.
- Funding mismatch ($7,500 IRA in strategy doc vs $100k paper account) is in week 5 unreconciled — still a pending user decision.

### Key Lessons
- Gold-plating the rulebook is itself a process failure. The written six-check buy-gate cleared Friday; an extra, undocumented "confirmed-strength tape" gate is what blocked the deploy. Either codify a discretionary tape filter into TRADING-STRATEGY.md or drop it — running an unwritten gate that silently overrides a core rule (75–85% deployment) is the worst of both.
- "Patience > activity" (Rule 11) permits zero-trade weeks, but it does not override Core Rule 2's deployment target indefinitely. Two consecutive empty weeks at ~40% is the rulebook fighting itself — patience is being stretched to excuse non-deployment.
- Sector-ETF rotation theses are inherently thematic, not same-day-news-driven; demanding a "specific same-day catalyst" for an ETF in a Leading quadrant structurally blocks deployment. The 5/22 entry resolved this by scoring the NVDA-guide AI-capex readthrough as a valid documented catalyst — that interpretation should be the standard going forward.
- 20 trading days reached: the first rolling Sharpe is computable (~3.4 indicative) but it is small-sample noise — the calibration reminder applies, do not infer edge.

### Adjustments for Next Week
- NO strategy-rule changes this week (calibration discipline). But the deployment gap is now formally on the clock: if a third week passes without a deploy on a clearing gate, the buy-gate's catalyst wording — or the unwritten tape filter — needs an explicit revision, not continued discretion.
- Mon 5/25 is Memorial Day — US markets closed. First session Tue 5/26: deploy XLI as the 3rd position at ~$19,500 / 10% trail GTC IF the written six-check buy-gate clears — do NOT add an unwritten tape-confirmation gate on top. The Leading-quadrant rotation + NVDA $91B-guide AI-capex readthrough is a documented catalyst.
- Target: push deployment from ~41% toward 60% with the XLI add; consider a 4th sleeve (XLU or XLB) later in the week if the gate clears, working toward the 75–85% band.
- Restore the midday routine commit cadence — zero midday commits this week.
- Watch XLK: +6.01% on cost, fresh HWM $181.73, trail $163.557; no stop-tighten trigger met (+15% threshold $195.70). Hold unconditionally absent a >3% intraday breakdown.
- Watch XLP: +1.13% on cost, trail $78.0255 (~8% cushion). Hold unconditionally.
- Funding reconciliation ($7,500 vs $100k) — week 5 pending; user decision, do not change docs autonomously.

### Overall Grade: B
Zero documented-rule violations and five rule-defensible HOLDs through two binaries; both positions thesis-intact and net green; XLK at a fresh phase high. The grade drops from last week's A- because (a) the binding constraint on deployment is now an unwritten discretionary gate the bot layered on top of its own rulebook — process drift, not process discipline; (b) Core Rule 2's 75–85% deployment target has gone unmet for two full weeks / ten sessions, with "patience" stretched to excuse it; (c) the midday routine produced zero commits all week (10/15 push success, down from 13/15); (d) the funding mismatch is week 5 unreconciled. P&L (-65 bps vs SPY) not penalized — the grade reflects process, and the process this week revealed a real gap between the written rules and the bot's actual behavior.

## Week ending 2026-05-29

Fifth full trading week (4-session, Memorial Day Mon closed). Capital-deployment box finally checked: XLI buy filled Tue 5/26 @ $173.86, pushing deployment 40.8% → 60.84% — first session above 50% in the phase. The Tue deploy cleared both the written six-check buy-gate AND the previously-unwritten "tape-confirmation" gate which was explicitly pre-documented Sun/Mon as a five-check scorecard (partial mitigation of last week's process drift). Wed/Thu/Fri considered a fourth deploy (XLF/XLV) but no clear-leader breakout cleared the bar; 2 of 3 weekly buy slots burned unused. All three positions (XLK, XLP, XLI) net P&L positive at week end despite XLP's Friday risk-on rotation hit; XLK printed a fresh phase high +12.11% on cost.

### Stats
| Metric | Value |
|--------|-------|
| Starting portfolio | $101,187.76 |
| Ending portfolio | $101,898.19 |
| Week return | +$710.43 (+0.70%) |
| SPY week return | ~+1.80% (Barchart 5-day per Perplexity; bot's EOD bid proxy $723.82 → $756.24 ≈ +4.5% likely overstated by stale ap pattern) |
| RSP week return | +0.91% (Perplexity / Barchart 5-day) |
| Bot vs SPY | -1.10% (using Perplexity +1.80%) |
| Bot vs RSP | -0.21% |
| Rolling 20d Sharpe (bot) | ~3.0–3.5 annualized indicative — 21-day sample; small-sample noise, do not infer edge |
| Rolling 20d Sharpe (SPY) | N/A — phase-long stale/wide SPY EOD quotes prevent a clean daily return series |
| Max drawdown (week) | 0.00% EOD basis (monotonically up Mon→Fri: $101,187.76 → $101,534.33 → $101,674.03 → $101,888.18 → $101,898.19) |
| Information ratio (vs SPY, rolling) | N/A — no clean SPY daily series |
| Trades | 1 (W:0 / L:0 / open:3 carried) |
| Win rate (closed) | N/A — no closed trades |
| Best trade | XLK +12.11% (open, fresh phase high; ~2.9 pts from +15% trail-tighten trigger at $195.70) |
| Worst trade | N/A — no closed trades (XLP -1.15% open is the laggard; XLI -0.25% essentially flat) |
| Profit factor | N/A — no closed trades |

### Closed Trades
| Ticker | Entry | Exit | P&L | Notes |
| — | — | — | — | None |

### Open Positions at Week End
| Ticker | Entry | Close | Unrealized | Stop |
| XLK | $170.17 (117 sh, 5/7) | $190.77 | +$2,410.20 (+12.11%) | $172.467 (trail 10%, HWM $191.63) |
| XLP | $83.8515 (238 sh, 5/4) | $82.89 | -$228.84 (-1.15%) | $78.0255 (trail 10%, HWM $86.695) |
| XLI | $173.86 (115 sh, 5/26) | $173.43 | -$49.45 (-0.25%) | $157.374 (trail 10%, HWM $174.86) |

### Process Metrics (mechanics validation — first 30–90 days)
- Rule-adherence: 5/5 sessions considered (Mon market closed, no action expected; Tue–Fri considered). 1 trade placed (XLI Tue) cleared all six written buy-gate checks AND the pre-documented five-check tape-confirmation scorecard (SPY +0.45% vs Fri mid, VIX 16.85 < 20, XLI +0.6% open no breakdown, no weekend shock, WTI < $100) — the previously-unwritten tape filter from Week 4 was explicitly written into Sun/Mon research before firing, partial mitigation of last week's "gold-plating" finding. Wed/Thu/Fri considered a fourth deploy (XLF/XLV); no clear-leader breakout cleared. 0 documented-rule violations.
- Time-to-stop-placement after fill: XLI fill 13:40:38 UTC → trail GTC stop submitted 13:40:51 UTC = **~13 seconds**, well under the 30-second target.
- Research-log completeness: 1 / 1 executed trade had pre-documented catalyst (XLI: Leading-sector rotation, AI-capex / data-center / electrification readthrough, cooling oil tailwind for transports, Iran-peace-deal weekend risk-on bias — all documented in 5/26 entry).
- Routine push success rate: 10 / 14 expected trading-day commits pushed (5 pre-market ✓ Mon–Fri, 5 EOD ✓ Mon–Fri, 0/4 midday — third consecutive week with zero midday commits); 1 market-open ✓ for the Tue XLI deploy; auto-merge clean.
- Notification delivery: Discord webhook live; pre-market + EOD + market-open recaps delivered each day, no failures observed.

### What Worked
- The XLI deploy finally cleared the deployment gap. Tue 5/26 fired the documented standing plan from the prior weekly review — written buy-gate clean (6/6 checks, catalyst included), tape-confirmation scorecard pre-documented Sun/Mon (5/5 checks), 10% GTC trail placed atomically (~13s post-fill). The "patience > activity" stretch was broken on the right day, not loosened mid-week.
- XLK ripped to a fresh phase high +12.11% on cost ($2,410 unrealized, HWM $191.63) — six consecutive green prints, no thesis break, trail advanced from $163.557 → $172.467 across the week, no manual intervention. The growth sleeve is the unambiguous winner of the phase.
- Three-sector mix (XLK growth + XLP defensive + XLI cyclical) absorbed Friday's risk-on rotation cleanly: XLK +2.10% offset XLP -1.82%, XLI -0.21% (flat); net bot +0.05% on the day. Diversification doing its job.
- The previously-unwritten "tape-confirmation" gate from Week 4 was promoted to a pre-documented five-check scorecard in the 5/25 and 5/26 research entries before the deploy — partial fix of last week's "gold-plating" process drift, even though TRADING-STRATEGY.md is not yet amended.
- Five consecutive green EOD prints Mon (flat) → Fri; max drawdown 0.00% on EOD basis; phase cumulative pushed from +1.19% to +1.90% — best week of the phase.

### What Didn't Work
- Capital still ~60.84% deployed vs the 75–85% target — fifth straight week the lower band hasn't been touched; the 4th-position bar ("clear-leader breakout from XLF/XLV") cleared on no session Wed/Thu/Fri. Two of three weekly buy slots burned unused.
- SPY pulled ~110 bps ahead on the week (~+1.80% vs +0.70%); phase gap to SPY widened ~80 bps (per bid proxy) to ~402 bps; XLP's Friday -1.82% defensive rotation hit was the single biggest sleeve drag.
- Midday routine produced zero commits for the third consecutive week — 10/14 push success rate excluding market-open; persistent cadence regression that's now a multi-week pattern, not a one-off slip.
- Funding mismatch ($7,500 IRA in strategy doc vs $100k paper account) is in week 6 unreconciled — still a pending user decision.
- SPY benchmark quality remains poor: the EOD `ap=0` stale-ask pattern persists phase-wide, forcing reliance on bid proxies or external Perplexity snapshots; rolling SPY Sharpe still can't be computed cleanly.
- RSP benchmark snapshot available this week (+0.91%) but Perplexity returns inconsistent date anchoring — vs-RSP scoring usable but not fully calibrated.

### Key Lessons
- A pre-committed deployment plan ("on Tue, deploy XLI as the 3rd position IF the written six-check gate clears — do NOT add an unwritten tape filter on top") survived contact with the open and fired cleanly. That's the rule-writing → rule-following loop closing correctly, exactly what process discipline looks like.
- Promoting an unwritten gate to a documented pre-trade scorecard is a partial fix, but the right end-state is to either codify the tape filter into TRADING-STRATEGY.md or drop it. Three consecutive weeks of "fourth position considered, no clear leader" suggests the catalyst bar for an ETF rotation deploy is structurally too high (relative to the rulebook's intent) — a sector-ETF entering a Leading quadrant on relative-strength IS the catalyst.
- XLK is now ~2.9 pts of upside away from the +15% tighten-to-7% trail rule firing — a single +2.5% session triggers it. The bot needs to execute this stop-tighten the moment XLK closes ≥ $195.70 without hesitation; this is a Tier-1 rule that has never fired in the phase and is overdue for live execution.
- Three sectors finally producing real diversification benefit: Friday's XLK +2.10% / XLP -1.82% rotation netted to a tiny gain; without XLK the bot loses 30+ bps on the day. The "two-sector mix" lesson from Week 3 graduated cleanly to a "three-sector mix" lesson this week.

### Adjustments for Next Week
- NO strategy-rule changes this week (5-week sample; small samples lie — PROJECT-CONTEXT.md calibration reminder still binding). The hot-PPI rule, six-check buy-gate, and pre-committed deployment plan all performed as designed.
- Mon 6/1 pre-market: re-evaluate a fourth-position deploy (XLF, XLV, or XLB) at ~$19,500 / 10% trail GTC IF the written six-check buy-gate clears on a live quote with a documented sector-rotation catalyst — do NOT require an undocumented "tape-confirmation breakout" beyond the written gate; an ETF entering or holding a Leading quadrant IS the catalyst. Target: push deployment from ~61% toward 80%, into the lower band of the 75–85% target.
- Watch XLK closely Mon: +12.11% on cost, HWM $191.63, trail $172.467; **+15% tighten-to-7% trigger fires at a close ≥ $195.70 (~+2.5% from current $190.77)**. Execute the trail-tighten the moment the trigger clears — this rule has not fired all phase and is the highest-leverage one currently on the table.
- Watch XLP: -1.15% on cost after Friday's rotation hit; thesis intact, trail at $78.0255 (~5.6% below current $82.89); hold unconditionally unless defensive thesis breaks or stop trips.
- Watch XLI: -0.25% on cost (essentially flat, day 4 of seasoning); manual -7% cut at $161.69; hold unconditionally absent a thesis break.
- Restore the midday routine commit cadence — three consecutive weeks with zero midday commits. Investigate whether the routine is firing-but-not-committing or not firing at all; this is a mechanics-validation failure if it persists into week 7.
- Funding reconciliation ($7,500 vs $100k) — week 6 pending; user decision, do not change docs autonomously.

### Overall Grade: B+
Strongest week of the phase on every dimension that matters in mechanics-validation: the deployment gap finally narrowed via a clean, pre-documented Tue XLI deploy that cleared both the written buy-gate AND a now-pre-documented tape scorecard (partial fix of last week's process drift); XLK printed a fresh phase high +12.11% with the trail advancing every session; three-sector diversification worked exactly as designed on Friday's risk-on rotation; max DD 0.00% on EOD basis with six consecutive green prints; rule-adherence clean (1/1 deploy, 3/3 considered HOLDs, 0 violations); time-to-stop-placement ~13 seconds (best of phase). Capped at B+ (not A-) because (a) capital is still 60.84% deployed vs the 75–85% target — fifth straight week under the band, with 2 of 3 weekly buy slots burned unused, (b) the midday routine has now produced zero commits for three consecutive weeks — that's a pattern, not a slip, (c) the tape-filter mitigation is partial: documented pre-trade but not yet codified in TRADING-STRATEGY.md, (d) the funding mismatch is week 6 unreconciled, (e) the +15% trail-tighten trigger on XLK is overdue to fire and we'll see Mon whether the rule executes live. P&L (-110 bps vs SPY) not penalized — the grade reflects process, and process this week was the cleanest of the phase.
