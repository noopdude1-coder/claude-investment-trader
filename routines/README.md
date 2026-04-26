# Cloud Routines

Each `.md` file in this directory is the prompt for one Claude Code cloud routine. Paste **verbatim** into the routine's prompt field — do not paraphrase. The env-var check block and the commit-and-push step are load-bearing.

## One-time setup per routine

1. Install the Claude GitHub App on this repo (least-privilege, repo-only).
2. In each routine's environment settings, **toggle ON "Allow unrestricted branch pushes"**. Without this, `git push origin main` silently fails. This is the #1 first-run failure.
3. Add these env vars to each routine (NOT to a `.env` file in the repo):
   - `ALPACA_API_KEY`, `ALPACA_SECRET_KEY`
   - `ALPACA_ENDPOINT` (optional), `ALPACA_DATA_ENDPOINT` (optional)
   - `PERPLEXITY_API_KEY`, `PERPLEXITY_MODEL` (optional, defaults to `sonar`)
   - `DISCORD_WEBHOOK_URL` (one URL is the entire credential)

## Cron schedules (America/Chicago — adjust if your timezone differs)

| Routine        | Cron          | Local time             |
|----------------|---------------|------------------------|
| pre-market     | `0 6 * * 1-5` | 6:00 AM CT, weekdays   |
| market-open    | `30 8 * * 1-5`| 8:30 AM CT, weekdays   |
| midday         | `0 12 * * 1-5`| 12:00 PM CT, weekdays  |
| daily-summary  | `0 15 * * 1-5`| 3:00 PM CT, weekdays   |
| weekly-review  | `0 16 * * 5`  | 4:00 PM CT, Fridays    |

The market opens 8:30 AM CT and closes 3:00 PM CT. If you set the routine timezone to `America/New_York`, shift each cron forward by 1 hour.

## Why no `.env` file in the cloud

The wrapper scripts read `.env` first, then fall back to process env. In the cloud:
- A committed `.env` would leak credentials.
- A runtime-created `.env` is either a leak (if pushed) or wasted work (if not).
- Worst case: agent sees "key not set," helpfully creates a `.env` as a workaround, leaks credentials.

Every routine prompt contains an explicit "DO NOT create a `.env` file" block. Re-paste the prompt verbatim if you ever see the agent try.
