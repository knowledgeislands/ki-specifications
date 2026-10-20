---
id: KI-SPEC-RGV-004
area: RGV
title: Archify status flow diagrams
kind: deliver
project: observatory
component: repository-governance
priority: medium
size: s
status: done
blocks: []
blocked_by: []
baseline_ref: 5e401df87c02a592992c83c697188fcda5e120d0
created_at: 2026-10-19T07:37:29Z
updated_at: 2026-10-20T06:46:20Z
---

# KI-SPEC-RGV-004: Archify Status Flow Diagrams

## Goal

The two status-flow diagrams in `docs/specification-process.md`, KIP and KIS, are Archify lifecycle diagrams with committed JSON sources and SVGs, embedded above the original Mermaid until the owner signs them off, so that this repository keeps its diagrams under the one Knowledge Islands diagram standard.

## Context

Kris Brown decided on 19 October 2026, in the Observatory work in Knowledge Islands Principal, that Archify through `ki-diagrams` is the one diagram standard and that existing Mermaid is replaced wherever Archify can carry it: "if they can be replaced with archify they should be, e.g. activity diagrams. Flag any others that don't and I'll decide about them too." Each repository converts its own diagrams. The decisions are recorded as DIAGRAM-STANDARD, DIAGRAM-REPLACE and DIAGRAM-MIGRATION in the Observatory decisions log.

A survey on 19 October 2026 found two Mermaid fences here, both `stateDiagram-v2`:

- `docs/specification-process.md`, the KIP status flow: Draft, Review (with a revised self-loop), Accepted, Rejected, Withdrawn, Implemented and Superseded.
- `docs/specification-process.md`, the KIS status flow: Draft, Active, Deprecated and Superseded.

Archify reads `stateDiagram` as its `lifecycle` type, so both carry by meaning without loss. The pilot in Knowledge Islands Principal shows the shape: the [Acquisition Process](https://github.com/knowledgeislands/ki-principal/blob/main/Pillars/Philosophy/Model/Processes/Acquisition%20Process/Acquisition%20Process.md) note embeds its SVG above a collapsed `<details>` block holding the original Mermaid, with the JSON source beside the note.

## Boundary

- In: one Archify lifecycle source and SVG per status flow, traced to the lines of `docs/specification-process.md` and to the specification documents that define each status; the image above each original fence, with the fence kept in a collapsed `<details>` block until sign-off; removing the fences once the owner signs off.
- In: a plain light export until the `ki-diagrams` KI-theme export exists, then a re-export.
- Out: changing any status, transition or specification text.

## Current state

`docs/specification-process.md` carries the two status flows only as Mermaid `stateDiagram-v2` fences, at lines 56 to 71 (KIP) and 75 to 82 (KIS) at `6b4e2e3`. The repository has no `docs/diagrams/` folder and does not declare `[skills.ki-diagrams]`, so nothing checks its diagrams. The prose at line 21 draws `Implemented -> Superseded` for a KIP, while line 18, `GOVERNANCE.md` and the Mermaid fence draw `Accepted -> Superseded`; this record carries the Mermaid by meaning and does not settle that difference.

## Steps

- [x] Write `docs/diagrams/kip-status.lifecycle.json` and `docs/diagrams/kis-status.lifecycle.json` as Archify lifecycle sources carrying every state and transition of the two Mermaid fences, each state citing its line in `docs/specification-process.md` at revision `6b4e2e3`.
- [x] Finalize both at showcase quality outside the repository and export each as a static `light` SVG to `docs/diagrams/<slug>.svg` with the `ki-diagrams` exporter.
- [x] Add `docs/diagrams/diagrams.toml` and `docs/diagrams/README.md` from the `ki-diagrams` templates, with `svg_form = "light"` and `last_checked` at the traced revision.
- [x] Embed each SVG above its original fence in `docs/specification-process.md`, moving the fence into a collapsed `<details>` block that says it is kept until sign-off.
- [x] Declare `[skills.ki-diagrams]` in `.ki.toml` so the repository audit checks the diagram set.
- [x] Run the checks under Verify and complete the review packet.
- [x] Rework after the failed acceptance review of 20 October 2026: relabel the KIP `Accepted -> Implemented` transition and the `Implemented` sublabel without a publication trigger, relabel the KIS `Active -> Deprecated` transition without a required reason, re-export both SVGs in the `ki` form, set `svg_form = "ki"` and drop the plain-light notes, then re-run the checks and refresh the review packet.

## Files touched

- `docs/diagrams/kip-status.lifecycle.json`, `docs/diagrams/kip-status.svg`, `docs/diagrams/kis-status.lifecycle.json`, `docs/diagrams/kis-status.svg`, `docs/diagrams/diagrams.toml`, `docs/diagrams/README.md` (new).
- `docs/specification-process.md`.
- `.ki.toml`.
- This record.

## Verify

- `archify validate lifecycle` and `archify finalize lifecycle ... --quality showcase` pass for both sources, with every gate passing.
- The exporter writes both SVGs without refusal, and neither SVG nor source carries a local path.
- `rumdl check` passes on the changed Markdown, and every JSON and TOML file parses.
- `ki repo audit --repo . --skill ki-diagrams` reports no failure; its only warnings are the two retained Mermaid fences (DIAG-7), expected until sign-off.
- `ki repo audit --repo .` reports no new failure against the baseline.

## Dependencies / blocks

The KI-theme static export is ki-agentic-harness work under the [`ki-diagrams` standard](https://github.com/knowledgeislands/ki-agentic-harness/blob/main/skills/governance/ki-diagrams/references/standards-diagrams.md). It has landed: the installed exporter supports `--form ki`, and both SVGs now use it.

## Documentation impact

### Decision Records

None: the diagram standard is already decided as DIAGRAM-STANDARD and DIAGRAM-REPLACE in the Observatory work and recorded in the `ki-diagrams` standard.

### Specifications

None: no status, transition or normative text changes; the diagrams redraw the existing informative flows.

### Guides

`docs/specification-process.md` gains the two embedded SVGs, and `docs/diagrams/README.md` indexes them for readers.

### Roadmap

None here. Removing the Mermaid fences after sign-off is the last step of this same record's boundary, taken at acceptance.

## Review

### Delivered

Both status flows in `docs/specification-process.md` are Archify lifecycle diagrams, with committed JSON sources and static SVGs in the Knowledge Islands theme under `docs/diagrams/`, listed in a `ki-diagrams` manifest and README, and embedded above the original Mermaid fences, which stay in collapsed `<details>` blocks until the owner signs the diagrams off. This rework answers the failed acceptance review of 20 October 2026: the KIP diagram no longer names a publication trigger for `Implemented`, the KIS diagram no longer presents a typical deprecation reason as a required condition, and the promised KI-theme re-export is done. No status, transition or specification text changed, and the `text` sketch at line 21 is untouched. Baseline `5e401df87c02a592992c83c697188fcda5e120d0`; the sources trace `docs/specification-process.md`, `GOVERNANCE.md` and `proposals/README.md` at `6b4e2e3`, whose content is identical at the baseline. Not done, by the boundary's own condition: removing the fences, which waits for sign-off.

### Change Summary

- `docs/diagrams/kip-status.lifecycle.json`: the `Accepted -> Implemented` arrow reads `mark implemented` instead of `KIS published`, and the `Implemented` sublabel reads `mandate fulfilled by its KIS` instead of `its KIS is published`, so the diagram names no trigger where lifecycle step 7 and the governance pipeline disagree. The state now also cites `GOVERNANCE.md` line 26 beside its lifecycle line.
- `docs/diagrams/kis-status.lifecycle.json`: the `Active -> Deprecated` arrow reads `deprecate` instead of `successor intended`, since the prose gives a successor only as the typical reason.
- `docs/diagrams/kip-status.svg` and `docs/diagrams/kis-status.svg`: re-exported in the `ki` form from the corrected sources.
- `docs/diagrams/diagrams.toml`: `svg_form = "ki"` for both diagrams, and `last_checked` advanced past the explanatory edit.
- `docs/diagrams/README.md` and `docs/specification-process.md`: the notes promising a later KI-theme re-export are removed; the README says the SVGs are static KI-theme exports.
- Decisions: neutral wording rather than governance wording for the KIP trigger, because the review allowed either and the neutral form settles nothing the owner has not settled. Archify allows at most three sources per state, so `Implemented` cites lifecycle line 17, the Mermaid line and `GOVERNANCE.md` line 26, not also line 34. Unchanged from delivery: the `docs/diagrams/` layout, the grouped withdrawal arrow, and KIP `Superseded` following the Mermaid fence and line 18.

### Verification

- `archify validate lifecycle --repo-root --quality showcase`: pass for both sources, 0 errors, 0 warnings.
- `archify finalize lifecycle --repo-root --quality showcase`: pass for both, all four gates (validate, deliver, check, browser check) passing.
- `export-svg.ts --form ki`: both SVGs written without refusal; neither carries a `<style>`, `var(` or `@font-face`, and no source or SVG carries a local path.
- `rumdl check` on the changed Markdown: pass. Every JSON and TOML file parses.
- `ki repo audit --skill ki-diagrams`: no failure; the two DIAG-7 warnings for the retained fences, as planned.
- `ki repo audit --repo .` on local `main`: no failure; in the linked worktree only the RUNTIMES-2 and REPO-REG-1 failures that come from an unregistered worktree, as at delivery. `last_checked` was advanced to the correction commit, whose explanatory edit to `docs/specification-process.md` is outside `stale_when`.
- Visual check: both SVGs rendered to PNG with `rsvg-convert` and inspected; every state and transition of both fences is present and legible, with the corrected labels.

### Outstanding concerns

- The fences remain until the owner signs the diagrams off; removing them is the last step of this record's own boundary, for the acceptor once sign-off is given.
- The `text` sketch at line 21 of `docs/specification-process.md` still draws `Implemented -> Superseded` for a KIP, and lifecycle step 7 still ties `Implemented` to Draft publication against governance step 4. Both are specification text, out of this record's boundary and with the owner.

### Post-change review

The goal is met and the three review findings are closed: both flows are Archify diagrams in the Knowledge Islands theme, traced and embedded, with wording that adds no condition the prose does not state. Scope held to the diagram sources, their exports, the manifest and the two explanatory notes. Regression risk is low: informative documentation only. Ready for a fresh independent review and the owner's look at the two images.

### Mini recap

Corrected the KIP `Implemented` trigger wording and the KIS deprecation label, re-exported both diagrams in the KI theme, and refreshed the manifest and notes; every planned check passed, with the two expected fence warnings. Concerns: fence removal on sign-off, and the two specification-text inconsistencies with the owner. Learning route, not promoted: Archify's three-source limit per state is worth a line in the `ki-diagrams` standard's tracing guidance.

## Done

Accepted 20 October 2026 by the independent Codex reviewer under Kris Brown's quoted overnight acceptance grant on the review packet above.

## Discussion

Handed over from the Observatory work under the cross-repository choreography in Knowledge Islands Principal's `AGENTS.md`. This repository owns its priority, plan and execution.

### Independent acceptance review - 20 October 2026

Verdict: failed review; returned to `in-progress` under the independently reviewed overnight acceptance brief. No acceptance or pruning took place. The review packet and immutable baseline remain intact. The state and transition sets exactly match the retained Mermaid, including the revision loop, withdrawal from Draft and Review, and supersession from Accepted. Both committed SVGs are legible on visual inspection.

Transition wording needs correction before sign-off. The KIP arrow labelled `KIS published` and the Implemented sublabel `its KIS is published` imply implementation follows Draft publication. `GOVERNANCE.md` pipeline step 4 and `docs/specification-process.md` From Accepted KIP to KIS step 4 require implementation experience, promotion of the KIS to Active, and then the KIP's Implemented marker. The earlier lifecycle step 7 contradicts this; the diagram must avoid presenting that disputed publication trigger as settled. Use wording consistent with governance, or neutral wording that adds no disputed trigger, without changing specification text. The KIS arrow `successor intended` also makes a typical reason for deprecation appear to be a necessary condition; the prose says typically, so use an unqualified deprecation action or preserve that qualification.

The KI-theme re-export is no longer blocked on exporter availability: the installed `ki-diagrams` exporter supports `--form ki`, and this review successfully exported the KIP viewer in that form outside the repository. Complete the promised re-export for both diagrams, update `svg_form` and the associated explanatory text, and refresh verification evidence before returning for acceptance. Keep the original Mermaid until the corrected diagrams receive sign-off.

Independent checks passed: exact six-heading Review packet and all planned checkboxes; all JSON and TOML parsing; diagram privacy and pinned-source checks; exact state and transition comparison; both Archify showcase finalizations, including validation, delivery, provenance and browser gates; both light SVG exports; Markdown lint; roadmap, authoring and diagrams audits; and the full repository audit with zero failures and five warnings. The diagrams audit retains its two expected Mermaid warnings. A first parallel finalization met Archify's shared-directory delivery lock; serial retry passed without changing sources.

The informative KIP sketch remains untouched, as instructed. Its `Implemented -> Superseded` edge conflicts with governance, lifecycle step 8 and both status diagrams; `Accepted -> Superseded` is the supported editorial correction, subject to the owner's separate disposition. No new work record was captured, no conform or hook change was run, and no remote operation was made.

### Rework - 20 October 2026

All three findings addressed in the overnight burndown under OVERNIGHT-BURNDOWN: neutral `Implemented` wording, an unqualified deprecation action, and the KI-theme re-export with `svg_form = "ki"`. The Mermaid stays until sign-off and the specification sketch is untouched. Returned to awaiting review for a fresh independent review.

### Independent re-review and acceptance - 20 October 2026

Verdict: pass after rework at `14687c09a8991dc48b7218c34d93aed704910f22`. The three earlier findings are closed: KIP implementation wording adds no disputed publication trigger, KIS deprecation adds no required successor condition, and both static SVGs use the KI theme. Exact state, transition, initial-state and terminal-state comparisons pass against the retained Mermaid and the pinned source revision. Both images are legible on independent visual inspection.

Authority: Kris Brown, 20 October 2026, granted overnight acceptance: "if you can quickly now accept ... accepting new things that are waiting with you and pruning those ... getting the roadmaps down to zero". The ways-of-working decisions log reads this back under OVERNIGHT-BURNDOWN, and this run's explicit acceptance grant names exactly this record after rework. This is independent review, not delivery self-acceptance. The accepted diagram sign-off completes the outstanding in-scope fence-removal step: both folded Mermaid copies are removed, with the JSON sources and pinned provenance retained. No record is pruned.

Independent gates pass: both Archify showcase validations and finalizations, including validate, deliver, strict provenance check and real-browser check; both KI-theme SVG exports; exact review-packet headings and completed Steps; JSON and TOML parsing; private-path and static-SVG checks; Markdown lint; roadmap, authoring, diagrams and full repository audits with zero failures. The pre-existing authoring-template and other repository warnings are outside this acceptance boundary; no conform or hook change is made. Archify update checks are disabled for the brief's no-network boundary.

The specification-text concerns remain outside this diagram delivery and are already with the owner through SPEC-SKETCH in the ways-of-working decisions log and the prior review. My independent view is that `Accepted -> Superseded` is the supported correction to the informative sketch: governance, lifecycle step 8 and both diagram generations agree, and `Implemented` is terminal. The sketch remains byte-for-byte unchanged. The earlier lifecycle step 7's Draft-publication trigger also conflicts with governance step 4 and the later implementation-experience step; the neutral diagram wording faithfully avoids deciding that separate text correction. No new work record is captured under CAPTURE-GATE.
