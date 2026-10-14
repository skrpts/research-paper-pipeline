# Release Notes

## v1.1.30
GH#1058 — the pipeline could not run. Literature mapping now runs before thesis construction, as the documented stages always said it did.

Thesis construction read the literature review's output while running *first*, so that reference could never resolve and the step halted before any work was done — the paper pipeline produced nothing. Two fixes, because reordering alone would only have moved the problem:

- **Stage order** — literature mapping (Stage 2) now runs before thesis construction (Stage 3), matching this workflow's own stage documentation.
- **Two mislabelled inputs** — the literature map's "research question" slot was wired to the *thesis* step, and the thesis's "research question" slot would have resolved to the literature map after the reorder. Both now take the subject area and discipline you supply directly.
- **A duplicate stage** — the literature-map document step named the literature-map prompt a second time, which the engine never ran. It is now a plain template step, matching the paper-template step beside it.

Behaviour change: the thesis statement is now informed by the literature map, which is what the pipeline always claimed. No input you provide today changes, and nothing is removed.

## v1.1.29
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.1.28
GH#745 — declare per-step `output: {name, type}` on every execution step (thesis/text, literature_map/text, draft/text, citations/list, paper_template/text, literature_map_doc/text, polished_paper/text, evidence_report/text, consistency_verdict/decision). Lights up the #744 rich flow-map with named, typed outputs. Content-only; no bindings or logic changes.

## v1.1.27
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 13 inline shared-content files and declare 13 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.1.26
Wave 2: re-signed with canonical engine signing pipeline.

## v1.1.25
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.1.24
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.1.23
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.1.22
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
