# Public dashboard

This folder is the source for the public GitHub Pages dashboard. The bot writes to `equity.json` after every market close and to `latest-week.md` after every Friday's weekly review.

## One-time setup

1. Push the repo to GitHub.
2. Settings → Pages → Source: **Deploy from a branch** → Branch: **main** / **/docs** → Save.
3. Wait ~1 minute. The dashboard will be live at `https://<your-username>.github.io/<repo-name>/`.
4. (Optional) Add the URL to the repo's "About" section so visitors can find it.

## Files

- `index.html` — single-page dashboard (Chart.js + marked.js via CDN, no build step)
- `equity.json` — array of EOD snapshots; appended to each weekday by the daily-summary routine
- `latest-week.md` — last Friday's weekly review section in raw markdown; overwritten by the weekly-review routine

## equity.json shape

```json
[
  {
    "date": "2026-04-27",
    "equity": 7500.00,
    "spy_close": 580.12,
    "day_pl_pct": 0.0,
    "phase_pl_pct": 0.0,
    "trades_today": 0,
    "open_positions": [
      { "symbol": "XOM", "shares": 12, "entry": 140.50, "current": 142.30, "stop": 128.07, "unrealized_pct": 1.28 }
    ]
  }
]
```

The dashboard normalizes both bot equity and SPY close to 100 on the first snapshot, so the chart shows relative performance from inception.
