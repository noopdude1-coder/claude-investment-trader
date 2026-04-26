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

**REVIEW BLOCKED — environment not provisioned.**

All required secrets missing from process env: `ALPACA_API_KEY`,
`ALPACA_SECRET_KEY`, `PERPLEXITY_API_KEY`, `DISCORD_WEBHOOK_URL`.

- Could not pull account/positions (alpaca.sh failed: `ALPACA_API_KEY not set in environment`).
- Could not fetch SPY/RSP benchmark returns (perplexity unavailable).
- Discord alert about the missing vars fell through to local
  NOTIFICATIONS.md (gitignored) — will not reach the user channel.

### Action required
- Re-export the four secrets in the cloud routine env before next scheduled run.
- Verify `DISCORD_WEBHOOK_URL` first — without it, future failures will be silent.

### Overall Grade: N/A — review not executable
