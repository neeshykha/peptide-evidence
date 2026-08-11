# Peptide Evidence Brief

A structured evidence-grading system for research peptides. Each compound gets a standalone record graded under a fixed, frozen rubric — with every claim traced to a primary source (PMID / NCT / DOI / named FDA document) and every gap stated explicitly.

**Live site:** https://neeshykha.github.io/peptide-evidence/

## What this is

Compounds sold as "research chemicals" are marketed with claims that range from well-supported to pure extrapolation. This project grades what is and isn't established, compound by compound, using a three-axis rubric that is never averaged into a single score:

- **Evidence Level (L1–L5)** — from systematic reviews of RCTs down to in-vitro/animal-only evidence
- **Indication Match** — does the evidence match the use, route, *and dose* actually being marketed?
- **Source Independence** — independent replication vs. single-sponsor or commercial-only literature

Where the grade differs between the indication studied and the indication marketed, both are reported — a single number would hide the finding.

## Method highlights

- **Per-claim provenance.** Every claim carries a retrieval status: `retrieved`, `abstract-only`, or flagged as learned-from-summary (which excludes it from any synthesis until upgraded).
- **Enforced search order.** Registries and FDA documents before PubMed, vendor pages last and only for market facts — never for evidence claims.
- **Absence is a finding.** "No registered human trials as of [date]" is recorded as a result, not skipped.
- **Corrections stay visible.** Withdrawn claims keep an inline correction note so errors are auditable and can't silently reappear.
- **Mandatory counterbalance.** Every record includes unfavorable findings and a "what would change this grade" section in both directions.

## What this is not

Not a purchasing guide, not medical advice, and not an endorsement of any compound. Records deliberately exclude dosing protocols, sourcing advice, and vendor recommendations. Where a dose appears, it appears only as a fact about what was studied or sold, for the route/dose mismatch analysis.

## Stack

Static HTML — each record is a fully self-contained page (inline CSS, no dependencies, no build step), published via GitHub Pages. Records are produced by an AI-assisted research pipeline running under a written protocol, with a separate adversarial audit pass run in a clean context.

## Status

4 of 43 planned records published. The index tracks the full queue, grading criteria, and known limitations.
