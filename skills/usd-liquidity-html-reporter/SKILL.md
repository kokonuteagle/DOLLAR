---
name: usd-liquidity-html-reporter
description: Set up and run recurring or one-off USD liquidity plumbing reports as mobile-first institutional HTML. Use when the user wants a shareable OpenClaw-ready workflow that asks only for report cadence/time on first setup, then automatically generates complete HTML reports about dollar liquidity, QT/QE, reserves, ON RRP, TGA, Treasury issuance, repo plumbing, dealer capacity, financial conditions, and global dollar liquidity.
---

# USD Liquidity HTML Reporter

## Overview
Create institution-style HTML liquidity reports from official data and automate recurring delivery with cron. On first-time setup, ask only for cadence/time if the user has not already given it. After that, create or update the recurring job, generate HTML reports, and archive dated copies under `reports/`.

## Quick start
Use this skill in three modes:

1. **Recurring setup**
   - Trigger when the user wants the repo or workspace to become a turnkey recurring report system.
   - Ask only one question if needed: the report cadence/time.
   - Infer timezone from the current session unless the user overrides it.

2. **One-off run now**
   - Generate a fresh HTML report immediately.
   - Save the dated file under `reports/`.

3. **Refresh an existing setup**
   - Reuse the existing cadence, repo path, and report style.
   - Only ask follow-up questions if the path/target is ambiguous.

## Setup workflow
1. **Ask only for cadence/time if missing**
   - Ask a single compact question such as:
     - `리포트 주기만 정하면 된다. 예: 매일 07:00 KST / 매주 일요일 19:00 KST / 평일 08:00 KST 중 어떤 식으로 할까?`
   - Do not ask extra setup questions unless the repo target or delivery target is genuinely unclear.

2. **Infer defaults**
   - Timezone: current session timezone.
   - 관심 자산: `broad risk assets` unless the user specifies BTC, Nasdaq, bonds, gold, etc.
   - 최근 이벤트 / 가설: only include if the user supplied them.
   - Repo root: current working repo if one is present; otherwise the current workspace root.

3. **Load the detailed references**
   - Read `references/data-playbook.md` before collecting data.
   - Read `references/html-report-spec.md` before rendering HTML.
   - Use `references/cron-automation.md` when creating or updating the recurring job.
   - Use `assets/report-shell.html` as the rendering scaffold when useful.

4. **Create/update the recurring job**
   - Use an isolated `agentTurn` cron job.
   - Use a stable job name such as `usd-liquidity-html-report` or a localized equivalent.
   - Put explicit trigger phrases in the cron prompt so this skill re-triggers on future runs.
   - Pass the repo/report target path in the cron message so the run knows where to write files.

5. **Generate the report**
   - Save the dated report as `reports/YYYY-MM-DD_usd_liquidity_analysis_report.html`.
   - Do not overwrite or periodically refresh `index.html` unless the user explicitly asks for a latest-report landing page.
   - If the repo is git-tracked, commit changes. Push if auth is available.
   - If push is unavailable, still write files and state that push/auth is pending.

## Report run rules
- Put the most important verdict on the first screen.
- Separate stock from flow.
- Separate reserves from ON RRP/TGA reallocation.
- Separate accounting liquidity from market-felt liquidity.
- Keep official-data dates distinct from daily market dates.
- Treat dealer/bank capacity as a transmission bottleneck, not an afterthought.
- Avoid bumper-sticker conclusions like `liquidity up = risk assets up`.
- If a required series is missing, say `확인 불가` and identify why it matters.

## File outputs
Use these defaults unless the user asks otherwise:

- Archive copy: `reports/YYYY-MM-DD_usd_liquidity_analysis_report.html`
- Skill spec: keep under `skills/usd-liquidity-html-reporter/`
- `index.html` is optional and should stay untouched unless the user explicitly asks for a latest-report landing page.

## Delivery behavior
- For interactive one-off runs, send the HTML file back to the user when possible.
- For recurring runs, prefer writing/updating the repo first. If channel delivery is available and appropriate, also send the HTML file or a short completion note.
- If the repo is being shared publicly, keep the visible report institutional and process-free. Do not expose setup chatter inside the HTML.
