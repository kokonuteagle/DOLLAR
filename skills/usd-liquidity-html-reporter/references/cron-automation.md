# Cron Automation

Use this reference when the user wants the repo/workflow to become recurring.

## Goal
After first setup, the workflow should ask only for cadence/time, then handle future runs automatically.

## First-time setup behavior
If the user has not supplied cadence/time, ask only one concise question:
- `리포트 주기만 정하면 된다. 예: 매일 07:00 KST / 매주 일요일 19:00 KST / 평일 08:00 KST 중 어떤 식으로 할까?`

Infer everything else unless ambiguous:
- timezone: current session timezone
- 관심 자산: broad risk assets unless specified
- repo path: current repo root if available
- archive path: `reports/YYYY-MM-DD_usd_liquidity_analysis_report.html`
- do not update `index.html` unless the user explicitly asks for a latest-report landing page

## Cron job pattern
Use an isolated `agentTurn` cron job.
Recommended job name:
- `usd-liquidity-html-report`

Recommended cron prompt contents:
- explicit trigger phrase: `Run recurring USD liquidity plumbing HTML report`
- current repo root path
- archive output path convention under `reports/`
- `index.html` should not be touched unless the user explicitly requests a latest-report landing page
- reminder to use official-data-first workflow
- reminder to update the latest HTML and archive a dated copy
- reminder to commit and push if git auth is available

## Run behavior inside the cron turn
1. Trigger this skill again with a clear message.
2. Read `references/data-playbook.md`.
3. Read `references/html-report-spec.md`.
4. Generate the HTML report.
5. Write:
   - `reports/YYYY-MM-DD_usd_liquidity_analysis_report.html`
   - leave `index.html` unchanged unless the user explicitly asked for it to be refreshed
6. If the repo is git-tracked:
   - `git add index.html reports ...`
   - `git commit`
   - `git push` if auth is available
7. If push/auth fails:
   - leave the local commit or working tree ready
   - report exactly what blocked the push

## Delivery guidance
- If interactive channel delivery is possible and appropriate, send the HTML file back to the user.
- If not, at minimum ensure the repo copy is updated and report the written paths.

## Safety / quality
- Do not keep asking setup questions after cadence is given unless the target path is truly unclear.
- Do not fabricate data when a primary source is unavailable.
- Keep the visible HTML institutional and process-free.
