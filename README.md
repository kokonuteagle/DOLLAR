# DOLLAR

Institutional-style HTML liquidity reports and the prompt/skill spec used to generate them.

## Included

- `index.html` — latest mobile-first institutional USD liquidity report
- `reports/2026-04-05_usd_liquidity_analysis_report_institutional.html` — dated report archive copy
- `skills/usd_liquidity_plumbing.md` — official-data-first liquidity plumbing skill spec

## Report focus

The report framework is built around six layers:

1. Fed balance sheet and policy implementation
2. Money markets and repo plumbing
3. Treasury cash and debt management
4. Bank and dealer balance-sheet constraints
5. Financial conditions
6. Global dollar liquidity

## Notes

- Primary sources are preferred wherever possible: Fed, NY Fed, U.S. Treasury, Chicago Fed, OFR, BIS.
- Some market series may be rendered from secondary distribution endpoints when direct machine-readable pulls are not practical in a given run.
- The HTML report is designed for mobile viewing first, with institution-style presentation.
