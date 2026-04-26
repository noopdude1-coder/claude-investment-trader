# Claude Investment Trader (AI Experiment)

Autonomous Claude Code trading agent running on a Traditional IRA at Alpaca. Built on Nate Herk's Opus 4.7 Trading Bot blueprint, adapted for an IRA cash account ($7,500 starting capital, no PDT, T+1 settlement).

## Quickstart

1. Push this repo to GitHub (private to start, can flip to public for the dashboard later).
2. Sign up: Alpaca (paper first), Perplexity (API access — not Pro), Discord (create a webhook on a channel).
3. `cp env.template .env`, fill in credentials. **Never commit `.env`.**
4. Local smoke test: open this directory in Claude Code, run `/portfolio`. Should print account + positions cleanly.
5. Install the Claude GitHub App on this repo.
6. Create the five cloud routines per `routines/README.md`. **Toggle "Allow unrestricted branch pushes" on each.**
7. Hit "Run now" on the pre-market routine and watch the logs. If it commits + pushes, the rest will work.

## Running locally on Windows

The wrapper scripts are bash. Use Git Bash or WSL on Windows. PowerShell will not run them.

## Repo layout

```
CLAUDE.md                      # Loaded every Claude Code session
memory/                        # The agent's persistent state — committed to main
  TRADING-STRATEGY.md          # Rulebook
  TRADE-LOG.md                 # Trades + EOD snapshots
  RESEARCH-LOG.md              # Daily pre-market research
  WEEKLY-REVIEW.md             # Friday recaps
  PROJECT-CONTEXT.md           # Mission, calibration reminders
routines/                      # Cloud routine prompts (production)
.claude/commands/              # Ad-hoc local slash commands
scripts/                       # API wrappers — only path to the outside world
  alpaca.sh                    # Trading
  perplexity.sh                # Research
  discord.sh                   # Notifications (Discord webhook)
docs/                          # Public GitHub Pages dashboard
  index.html                   # Single-page dashboard (Chart.js + marked.js via CDN)
  equity.json                  # EOD snapshot history — appended to daily by daily-summary
  latest-week.md               # Last weekly review section — overwritten by weekly-review
```

## Public dashboard (GitHub Pages)

The repo includes a `docs/` folder that GitHub Pages can serve as a free public dashboard. Equity curve vs SPY, current positions, latest weekly review.

To enable:
1. Push the repo to GitHub (must be public for free Pages — or use any plan that supports private Pages).
2. Settings → Pages → Source: **Deploy from a branch** → Branch: **main** / **/docs** → Save.
3. Wait ~1 minute. Live at `https://<your-username>.github.io/<repo-name>/`.

The bot updates the dashboard automatically: `docs/equity.json` after every market close, `docs/latest-week.md` every Friday afternoon. No extra cron jobs needed — the data write is part of the existing daily-summary and weekly-review routines.

## Strategy at a glance

Stocks only. Max 5-6 positions, max 20% each, max 3 new trades per week. 10% trailing stop on every position as a real GTC order. Cut losers at -7%. Tighten to 7% at +15%, to 5% at +20%. Patience > activity.

Full rules: `memory/TRADING-STRATEGY.md`.

## Source

- Setup blueprint: Nate Herk's "Opus 4.7 Trading Bot" (AI Automation Society). Original PDF not redistributed — see [Nate Herk on YouTube](https://www.youtube.com/@nateherk) for context.
- IRA-specific strategy delta: [`Trading Strategy.pdf`](./Trading%20Strategy.pdf)
