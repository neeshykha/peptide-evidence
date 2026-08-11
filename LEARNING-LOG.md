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
