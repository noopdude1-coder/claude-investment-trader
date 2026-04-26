# Trading Strategy

## Mission
Beat SPY on a risk-adjusted (Sharpe) basis over the challenge window. Stocks only — no options, ever.

## Capital & Account
- Starting capital: ~$7,500 (2026 Traditional IRA contribution limit, under-50)
- Account type: Traditional IRA on Alpaca (cash account, no margin)
- Instruments: Stocks ONLY — no options, no crypto, no futures
- PDT rule: does NOT apply (PDT is a margin-account rule; IRAs are cash accounts)
- Settlement: T+1 (sale proceeds available next business day)
- Tax drag: none — gains/losses are tax-neutral inside the IRA

## Performance Benchmarks
- **Primary scorecard:** Sharpe ratio vs SPY's Sharpe over the same window
- **Secondary:** total return vs SPY, total return vs RSP (equal-weight S&P 500), max drawdown, information ratio
- **Honest calibration:** 6 months of swing-trading data is mostly noise. Year 1 is for validating mechanics, not declaring victory. A real verdict needs 3+ years.

## Core Rules (non-negotiable)
1. NO OPTIONS — ever
2. Target 75–85% deployed
3. 5–6 open positions at a time, max 20% each ($1,500 max position at start)
4. 10% trailing stop on every position as a real GTC order — never mental
5. Cut losers at -7% manually (no hoping, no averaging down)
6. Tighten trail: 7% at +15%, 5% at +20%
7. Never within 3% of current price; never move a stop down
8. Max 3 new trades per week
9. Follow sector momentum — don't force a thesis if the sector is rolling over
10. Exit a sector after 2 consecutive failed trades in that sector
11. Patience > activity. A week with zero trades can be the right answer.

## Buy-Side Gate
Every check must pass before any buy order. If any fail, skip the trade and log the reason.
- Total positions after fill ≤ 6
- Trades placed this week (incl this one) ≤ 3
- Position cost ≤ 20% of equity ($1,500 cap at $7,500 starting equity)
- Position cost ≤ available **settled** cash (T+1 — do NOT use buying_power on a cash account)
- Specific catalyst documented in today's RESEARCH-LOG entry
- Instrument is a stock

## Sell-Side Rules (evaluated at midday and opportunistically)
- Unrealized loss ≤ -7% → close immediately
- Thesis broken (catalyst invalidated, sector rolling, news event) → close, even if not at -7%
- Up ≥ +20% → tighten trailing stop to 5%
- Up ≥ +15% → tighten trailing stop to 7%
- 2 consecutive failed trades in a sector → exit all positions in that sector

## Entry Checklist
Document all four before placing:
- What is the specific catalyst today?
- Is the sector in momentum?
- What is the stop level (7–10% below entry)?
- What is the target (minimum 2:1 risk/reward)?

## Differences from the Original Guide (IRA-specific)
- PDT fallback ladder (trailing → fixed → queue) is unnecessary — every stop is a real GTC trailing stop on first try
- "PDT-blocked, set tomorrow AM" workflow is removed from market-open routine
- daytrade_count check in the buy-side gate is removed (no PDT in IRA)
- All P&L is tax-neutral, so no need to weight short-term vs long-term gains in exit decisions
- Use **settled cash**, not buying_power, when sizing — Alpaca's buying_power on a cash account can include unsettled proceeds

## Why These Rules Exist
Inherited from Nate Herk's 30-day live challenge: tight stops shook the bot out of winners repeatedly, overtrading cost several percent in one bad week, and a single options trade wiped out a full month of gains. Inheriting that discipline is cheaper than re-learning it.
