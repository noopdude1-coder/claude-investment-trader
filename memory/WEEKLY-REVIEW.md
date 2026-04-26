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
