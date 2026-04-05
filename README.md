# DOLLAR

Mobile-first institutional USD liquidity reports for OpenClaw.

## What this repo is for

This repo is set up so an OpenClaw user can drop the repo contents into a workspace and use the included skill to:

- ask only for the report cadence/time on first setup
- create a recurring cron workflow
- generate complete HTML liquidity reports
- keep `index.html` refreshed with the latest report
- archive dated report copies under `reports/`

## Main files

- `index.html` — latest report
- `reports/` — dated archived HTML reports
- `skills/usd-liquidity-html-reporter/` — OpenClaw skill folder
- `dist/usd-liquidity-html-reporter.skill` — packaged skill file

## OpenClaw usage

Copy the `skills/usd-liquidity-html-reporter/` folder into your OpenClaw workspace `skills/` directory, or copy this repo into a workspace and keep the folder structure intact.

Then prompt OpenClaw with something like:

- `달러 유동성 HTML 리포트 세팅해줘`
- `USD liquidity recurring HTML report setup`

The skill is designed to ask only for cadence/time if missing, then handle the recurring setup and HTML report generation workflow.

## Skill structure

- `SKILL.md` — setup and run workflow
- `references/data-playbook.md` — official-data-first pull and interpretation rules
- `references/html-report-spec.md` — institutional HTML output spec
- `references/cron-automation.md` — recurring cron setup behavior
- `assets/report-shell.html` — reusable HTML shell
