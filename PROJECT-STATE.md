# Project State — Shipped Apps Portfolio

**Read this first in any new session (including Ship Sunday runs).** It is the continuity file: current status, queue, and operating rules. Update it every session alongside LEARNING-LOG.md.

## Mission

Aneesh has 17+ production AI automations but nothing public. Every unit of work moves something closer to a URL a recruiter can click. "Done" = live and linkable, never "works on my machine."

## Operating rules

1. Web-first for portfolio pieces. No installs, no Mac apps for public work.
2. 3:1 public-to-personal project ratio.
3. Static-first, backend only when genuinely needed (and then it's a portfolio story).
4. Every session ends with something deployed — live and verified, not just deployable.
5. Append to LEARNING-LOG.md every session: date, shipped, learned, next.
6. Metric that matters: live URLs, not sessions held.

## Idea pipeline scope (set 2026-08-11)

Work-side: tool building, MCPs, web tools useful in IoT or similar environments — not just support-AI. Personal side: health, gardening, peptides, functional medicine research, tennis, economics, current events, home improvement, exercise, investing. Claude justifies picks; Aneesh vetoes.

## Portfolio queue

| # | Project | Status | Notes |
|---|---------|--------|-------|
| 0 | portfolio hub | **OVERDUE — publish on first Claude Code run** (bundle from 2026-08-16 never published) | Repo `neeshykha/portfolio`: landing page, README, state files, kb-checker spec. If the original bundle can't be found locally, rebuilding is authorized (the old do-not-rebuild rule only existed because cloud runs couldn't deploy). Once live, **state files move here.** |
| 1 | peptide-evidence | **LIVE** — https://neeshykha.github.io/peptide-evidence/ | 4/43 records published. Record batches now unblocked (Claude Code has full web access). |
| 2 | KB health checker | **LIVE 2026-08-23** — https://neeshykha.github.io/kb-health-checker/ (flagship) | v1 paste-mode, pure client-side. v2 = URL-fetch mode on Vercel + serverless (CORS); reconcile rubric with `specs/kb-health-checker-spec.md` from hub bundle. |
| 3 | MQD calculator ("MQD Runway") | **BUILT + VERIFIED 2026-09-13 — publish on first Claude Code run** | In kit `deploy/mqd-calculator/`. Target repo `neeshykha/mqd-calculator` → Pages main/root. Rules encoded as editable data (Sept 2026 snapshot: 5k/10k/15k/28k thresholds, unchanged for 2027 per Dec-2025 Delta announcement; Headstart $2,500/card; Boost $10 Reserve / $20 Platinum). 16/16 headless-Chromium checks passed. Audience play once live: r/delta, FlyerTalk. |
| 4 | KB checker v2 (URL mode) | Queued | Vercel + serverless — now feasible in any Claude Code run. |
| 5 | HVAC export cleaner | Backlog (personal slot) | Drag-drop CSV cleaner, port of existing Python rules to browser JS. Rules already encoded in the `hvac-csv-cleaner` skill. |

## Environment facts (save future sessions the discovery cost)

- **MIGRATION (2026-09-14): Ship Sunday moved from Cowork cloud scheduled runs to Claude Code** (Aneesh's Mac or headless worker node), via the ship-sunday migration kit. Claude Code runs have: full git push, `gh` CLI (repo creation, Pages config via API — see kit `bin/publish.sh`), full web access, and the local ShipSunday folder. The Cowork-era constraints below are kept only for context if a run ever happens in Cowork again.
- GitHub account: **neeshykha** (also has: claude-resume-pipeline, claude-memory, deflection-audit).
- GitHub Pages pattern: deploy-from-branch, main / root. `bin/publish.sh` in the kit does repo-create → push → Pages → About in one idempotent command; verify live with `curl -sI` (first build ~1 min).
- Peptide dataset source of truth: the **ShipSunday project folder** on Aneesh's Mac (as of 2026-08-23, `~/Documents/ShipSunday/` — the folder name is the durable handle, not the path; it has moved before). Publish only index + compounds/ — `working/` stays private. Scrub vendor names before publishing (index carried nexaph.com references; neutralized in the published copy).
- State-file continuity: whichever repo the state files live in must actually receive the updated copies (commit + push every run), or the next run re-discovers everything. State repo: **peptide-evidence** until `neeshykha/portfolio` is live, then portfolio.
- Legacy (Cowork cloud, pre-migration): sandbox GitHub proxy was repo-scoped — read-only clones only, push 403, no repo creation (re-confirmed 2026-09-13); scheduled runs had no WebFetch/browser/device bridge; workaround was staged files + manual `/upload/main` steps or Claude-in-Chrome automation in attended sessions.

## Routine

**Ship Sunday** — weekly, Sundays 10:00 AM ET, now invoked via Claude Code (cron `claude -p` on the worker node, or interactively — see kit README). Each run: pull state repo, read this file + LEARNING-LOG.md, deliver the next increment, publish + verify live, append log entry, update this file, push.
