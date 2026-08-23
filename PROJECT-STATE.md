# Project State — Shipped Apps Portfolio

**Read this first in any new session (including Ship Sunday runs).** It is the continuity file: current status, queue, and operating rules. Update it every session alongside LEARNING-LOG.md.

## Mission

Aneesh has 17+ production AI automations but nothing public. Every unit of work moves something closer to a URL a recruiter can click. "Done" = live and linkable, never "works on my machine."

## Operating rules

1. Web-first for portfolio pieces. No installs, no Mac apps for public work.
2. 3:1 public-to-personal project ratio.
3. Static-first, backend only when genuinely needed (and then it's a portfolio story).
4. Every session ends with something deployed or deployable.
5. Append to LEARNING-LOG.md every session: date, shipped, learned, next.
6. Metric that matters: live URLs, not sessions held.

## Idea pipeline scope (set 2026-08-11)

Work-side: tool building, MCPs, web tools useful in IoT or similar environments — not just support-AI. Personal side: health, gardening, peptides, functional medicine research, tennis, economics, current events, home improvement, exercise, investing. Claude justifies picks; Aneesh vetoes.

## Portfolio queue

| # | Project | Status | Notes |
|---|---------|--------|-------|
| 0 | portfolio hub | **AWAITING ANEESH'S PUBLISH** (bundle delivered 2026-08-16) | Repo `neeshykha/portfolio` with landing page, README, state files, kb-checker spec. Until published, scheduled runs read state from peptide-evidence. Do NOT rebuild the bundle. |
| 1 | peptide-evidence | **LIVE** — https://neeshykha.github.io/peptide-evidence/ | 4/43 records published. Record batches need attended sessions (source retrieval). |
| 2 | KB health checker | **LIVE 2026-08-23** — https://neeshykha.github.io/kb-health-checker/ (flagship) | v1 paste-mode, pure client-side. Repo `neeshykha/kb-health-checker`, Pages on main/root, About metadata set. Verified live in-browser: "Load bad example" → 45/F. v2 = URL-fetch mode on Vercel + serverless (CORS) in attended sessions; reconcile rubric with `specs/kb-health-checker-spec.md` from hub bundle. |
| 3 | MQD calculator | Queued — next static-first candidate for a scheduled run | Pure client-side. Verify current Delta MQD earn rules + Medallion thresholds at build time (needs attended web access). Audience play: r/delta, FlyerTalk. |
| 4 | HVAC export cleaner | Backlog (personal slot) | Drag-drop CSV cleaner, port of existing Python rules to browser JS. |

## Environment facts (save future sessions the discovery cost)

- GitHub account: **neeshykha** (also has: claude-resume-pipeline, claude-memory, deflection-audit).
- Cowork cloud sandbox GitHub proxy is **repo-scoped**: authenticated as neeshykha but cannot create repos or push to repos not attached to the session. `add_repo` is not available in Cowork.
- Working path: Claude-in-Chrome browser automation (user is logged into GitHub) for repo creation, file uploads (`/upload/main/<dir>` URLs), and settings. Files must be staged in the session outputs folder (`/mnt/user-data/outputs/...`) for the extension's file_upload to accept them.
- Peptide dataset source of truth: `~/Downloads/ShipSunday/peptide-evidence-dataset/` on Aneesh's Mac (device bridge; request folder access). Moved 2026-08-23 from `~/Downloads/` into the consolidated `ShipSunday/` folder (which also holds the state files and `kb-health-checker/`); Aneesh may relocate that folder again, so if the path misses, search for `peptide-evidence-dataset` rather than assuming. Publish only index + compounds/ — `working/` stays private. Scrub vendor names (index carried nexaph.com references; neutralized in the published copy).
- GitHub Pages: enabled, deploy-from-branch, main / root.
- **Scheduled (Ship Sunday) runs specifically:** no WebFetch (permission-gated — every URL returns PROVENANCE_REQUIRED), no browser automation, no device bridge. WebSearch works but sources can't be opened. Public repos DO clone read-only via `git clone` — that's how state is recovered. Playwright + bundled Chromium (`/opt/pw-browsers/chromium`, playwright-core, `--no-sandbox`) works headlessly for verifying built pages. Fit for scheduled runs: authoring/build increments (specs, static apps, client-side code). Not fit: peptide record batches (source retrieval), repo creation, Pages/Vercel config.
- State-file continuity: whichever repo the state files live in must actually receive the updated copies, or the next run re-discovers everything. Fastest path while the hub is unpublished: upload updated PROJECT-STATE.md + LEARNING-LOG.md to peptide-evidence via `github.com/neeshykha/peptide-evidence/upload/main`.

## Routine

**Ship Sunday** — weekly scheduled task, Sundays 10:00 AM ET. Each run: read this file + LEARNING-LOG.md from the repo, deliver the next increment, append log entry, update this file.
