# Learning Log — Shipped Apps Project

Every session appends: date, what shipped, what was learned, what's next. This is data, not bookkeeping.

---

## Entry #1 — 2026-08-11

**Shipped:** `peptide-evidence` — first live public URL of the project.
Repo: https://github.com/neeshykha/peptide-evidence · Site: https://neeshykha.github.io/peptide-evidence/
Published the evidence-brief index + 4 compound records (BPC-157, ipamorelin, PT-141, tesamorelin) with vendor references neutralized and internal `working/` files kept private.

**Decisions made this session:**
- Audited all four candidates. Sequence locked: peptide site (today) → **KB health checker as flagship** (multi-session, Vercel + serverless) → MQD calculator (audience play) → HVAC cleaner (personal slot).
- Routine: **Ship Sunday** — weekly scheduled task that picks up state from this repo and delivers the next increment.
- Idea pipeline broadened beyond support-AI: work-side = tool building, MCPs, IoT-adjacent web tools; personal side = health, gardening, peptides/functional medicine, tennis, economics, current events, home improvement, exercise, investing.

**Learned (deployment track):**
- **A repo is a publishing pipeline, not just backup.** GitHub Pages turns any repo with an `index.html` into a website: Settings → Pages → deploy from branch → main/root. Zero config, zero build step, free hosting at `<user>.github.io/<repo>/`.
- **Static-first architecture.** This site is pure HTML with inline CSS — no build, no dependencies, nothing to break. That's why deployment took one session. The KB checker will need a serverless function (browsers can't fetch cross-origin pages — CORS), which is why it goes on Vercel.
- **Public repo hygiene:** publish the polished artifact, keep working notes private; scrub vendor/personal references before anything goes recruiter-facing; the README is part of the portfolio piece — it explains the *system*, not just the files.
- Constraint discovered: the Cowork cloud sandbox's GitHub proxy is repo-scoped and can't create repos or push to unattached ones. Workaround that works end-to-end: browser automation (repo creation, uploads, Pages config) with files staged through the session outputs folder. Ship Sunday runs will use this same path until a cleaner auth route exists.

**Next increment:** Add remaining compound records in batches (39 to go — each batch is a content update that auto-deploys on commit, reinforcing the git→live pipeline). In parallel, first KB-checker session: spec the grading rubric and scaffold the Vercel project.

## Entry #2 — 2026-08-16 (summary; full entry in the unpublished hub bundle)

**Shipped (pending publish):** Portfolio hub bundle for a new `neeshykha/portfolio` repo — landing page, README, migrated state files, and `specs/kb-health-checker-spec.md`. Delivered to Aneesh with 2-minute manual publish steps; **as of 2026-08-23 the repo does not exist yet**, so the bundle is still sitting in that session's deliverables. Until it's published, scheduled runs fall back to reading state from `peptide-evidence` — which is why this summary entry exists here.

---

## Entry #3 — 2026-08-23

**Shipped:** **KB Health Checker v1** — the flagship (queue #2) is now built and deploy-ready as a pure client-side app.
Deliverables staged: `kb-health-checker/index.html` + `README.md`. Target: new repo `neeshykha/kb-health-checker` → GitHub Pages.

Paste a help-center article (HTML or plain text) → AI-readiness grade across 5 weighted categories (structure/chunkability 25%, answer clarity 25%, self-containment 20%, machine readability 15%, language quality 15%), with per-finding "why this matters for retrieval" explanations and concrete fixes. Built-in good/bad example articles demonstrate the rubric. Verified in headless Chromium: good sample grades 100/A, bad sample 45/F, zero console errors.

**Key scope decision:** v1 is *paste-mode*, which needs no serverless function — CORS only blocks *fetching other sites' pages*, not analyzing pasted content. That unblocked shipping the flagship from a scheduled run (no browser, no WebFetch, no deploys available) and turns the Vercel + serverless work into a clean v2 increment (URL mode: paste a help-center link, grade every article) instead of a prerequisite. Lesson: **when a project's hard dependency only blocks part of the value, ship the unblocked part first.**

**Career-signal note:** the README frames the tool as encoded production diagnostic knowledge ("the copilot gave a wrong answer and the root cause was the content, not the model") — Framework #1 (SME First, Then Encode) made concrete and clickable.

**Learned (environment):** scheduled Ship Sunday runs can *author and verify* (Playwright + bundled Chromium works headlessly for smoke tests) but cannot deploy or retrieve web pages. Increment types that fit scheduled runs: specs, static apps, client-side code, repo-clone work. Peptide record batches and Pages/Vercel config need attended sessions.

**Next increment:** (a) Aneesh publishes: the hub bundle (from 8-16) and kb-health-checker (from today) — ~4 minutes total; (b) next attended session: reconcile this rubric with `specs/kb-health-checker-spec.md` from the hub bundle, then start KB checker v2 (Vercel serverless URL mode) or a peptide record batch; (c) next scheduled run: MQD calculator scaffold is the best static-first candidate if v2 needs attended time.
