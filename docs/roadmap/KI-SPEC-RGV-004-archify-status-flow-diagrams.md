---
id: KI-SPEC-RGV-004
area: RGV
title: Archify status flow diagrams
kind: deliver
project: observatory
component: repository-governance
priority: medium
size: s
status: in-progress
horizon: now
blocks: []
blocked_by: []
baseline_ref: 5e401df87c02a592992c83c697188fcda5e120d0
created_at: 2026-10-19T07:37:29Z
updated_at: 2026-10-20T06:41:01Z
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

The KI-theme static export is ki-agentic-harness work under the [`ki-diagrams` standard](https://github.com/knowledgeislands/ki-agentic-harness/blob/main/skills/governance/ki-diagrams/references/standards-diagrams.md). It does not block this record: export plain light now and re-export when the theme lands.

## Documentation impact

### Decision Records

None: the diagram standard is already decided as DIAGRAM-STANDARD and DIAGRAM-REPLACE in the Observatory work and recorded in the `ki-diagrams` standard.

### Specifications

None: no status, transition or normative text changes; the diagrams redraw the existing informative flows.

### Guides

`docs/specification-process.md` gains the two embedded SVGs, and `docs/diagrams/README.md` indexes them for readers.

### Roadmap

None here. Removing the Mermaid fences after sign-off and the KI-theme re-export are later steps of this same record's boundary, taken at acceptance or when the theme lands.

## Review

### Delivered

Both status flows in `docs/specification-process.md` are now Archify lifecycle diagrams, with committed JSON sources and static light SVGs under `docs/diagrams/`, listed in a `ki-diagrams` manifest and README, and embedded above the original Mermaid fences, which stay in collapsed `<details>` blocks until the owner signs the diagrams off. No status, transition or specification text changed. Baseline `5e401df87c02a592992c83c697188fcda5e120d0`; the sources trace `docs/specification-process.md`, `GOVERNANCE.md` and `proposals/README.md` at `6b4e2e3`, whose content is identical at the baseline. Not done, by the boundary's own conditions: removing the fences, which waits for sign-off, and the KI-theme re-export, which waits for the `ki-diagrams` KI-theme export.

### Change Summary

- `docs/diagrams/kip-status.lifecycle.json` and `docs/diagrams/kis-status.lifecycle.json`: Archify lifecycle sources, every state citing its prose line and Mermaid line, `meta.repository` pinned to the public revision `6b4e2e3` so source links resolve on GitHub.
- `docs/diagrams/kip-status.svg` and `docs/diagrams/kis-status.svg`: static `light` exports from the `ki-diagrams` exporter.
- `docs/diagrams/diagrams.toml` and `docs/diagrams/README.md`: the manifest, with `svg_form = "light"`, and the reader index. `last_checked` is `63d7bfc`, the delivery commit, because embedding the images changed a traced file in a way outside `stale_when`.
- `docs/specification-process.md`: each SVG above its fence, the fence inside `<details>` with a note that it is kept until sign-off.
- `.ki.toml`: declares `[skills.ki-diagrams]`, so the audit now checks the set and warns on the two kept fences.
- Decisions: the forms follow the `ki-diagrams` standard's `docs/diagrams/` layout rather than the pilot's note-side placement, because this is a project repository and not a knowledge-base island. Archify draws the two `withdraw` transitions, from Draft and from Review, as one arrow leaving a dashed group around both states; the meaning is unchanged. KIP `Superseded` follows the Mermaid fence and line 18 (`Accepted -> Superseded`), not the `text` sketch at line 21.

### Verification

- `archify validate lifecycle --quality showcase`: pass for both sources, 0 errors, 0 warnings.
- `archify finalize lifecycle --quality showcase`: pass for both, every gate passing including the browser check.
- `export-svg.ts --form light`: both SVGs written without refusal; no local path in any source or SVG.
- `rumdl check` on the changed Markdown: pass. Every JSON and TOML file parses.
- `ki repo audit --skill ki-diagrams`: no failure; two DIAG-7 warnings for the retained fences, as planned. On local `main` the full audit first warned DIAG-4 for both diagrams, because the embedding edit changed the traced `docs/specification-process.md` after `last_checked`; the change is outside `stale_when`, so `last_checked` was advanced and the warning cleared.
- `ki repo audit --skill ki-work-roadmap` and `--skill ki-repo-specifications`: pass.
- `ki repo audit --repo .` in the linked worktree: the record's ITEM-3 failure is cleared and no new failure appears; the remaining RUNTIMES-2 and REPO-REG-1 failures are the same with and without this change and come from the unregistered worktree, whose ignored runtime skill links are absent.
- Visual check: both SVGs rendered to PNG and inspected; every state and transition of both fences is present and legible.

### Outstanding concerns

- The fences remain until the owner signs the diagrams off; removing them is the last step of this record's own boundary, for the acceptor once sign-off is given.
- The KI-theme re-export remains open in this record's boundary until the `ki-diagrams` KI-theme export lands.
- The `text` sketch at line 21 of `docs/specification-process.md` draws `Implemented -> Superseded` for a KIP, against line 18, `GOVERNANCE.md` and the Mermaid fence. Out of this record's boundary; raised to the owner in the run report.

### Post-change review

The goal is met: both flows are Archify diagrams under the one diagram standard, traced and embedded, with the Mermaid kept for comparison. Scope held to the diagrams, their manifest, the embedding and the declaration. Regression risk is low: the change is informative documentation plus one skill declaration whose only new findings are the two expected warnings. Ready for acceptance once the owner has looked at the two images.

### Mini recap

Delivered the KIP and KIS status flows as Archify lifecycle diagrams in light SVG, embedded above the kept Mermaid, and adopted `ki-diagrams` here; every planned check passed, with the two expected fence warnings. Concerns: fence removal on sign-off, the theme re-export, and the line-21 sketch. Learning route, not promoted: the `ki-diagrams` standard could say how a project repository whose diagrams illustrate a document, rather than a system, places them; the `docs/diagrams/` layout worked here.

## Discussion

Handed over from the Observatory work under the cross-repository choreography in Knowledge Islands Principal's `AGENTS.md`. This repository owns its priority, plan and execution.

### Independent acceptance review - 20 October 2026

Verdict: failed review; returned to `in-progress` under the independently reviewed overnight acceptance brief. No acceptance or pruning took place. The review packet and immutable baseline remain intact. The state and transition sets exactly match the retained Mermaid, including the revision loop, withdrawal from Draft and Review, and supersession from Accepted. Both committed SVGs are legible on visual inspection.

Transition wording needs correction before sign-off. The KIP arrow labelled `KIS published` and the Implemented sublabel `its KIS is published` imply implementation follows Draft publication. `GOVERNANCE.md` pipeline step 4 and `docs/specification-process.md` From Accepted KIP to KIS step 4 require implementation experience, promotion of the KIS to Active, and then the KIP's Implemented marker. The earlier lifecycle step 7 contradicts this; the diagram must avoid presenting that disputed publication trigger as settled. Use wording consistent with governance, or neutral wording that adds no disputed trigger, without changing specification text. The KIS arrow `successor intended` also makes a typical reason for deprecation appear to be a necessary condition; the prose says typically, so use an unqualified deprecation action or preserve that qualification.

The KI-theme re-export is no longer blocked on exporter availability: the installed `ki-diagrams` exporter supports `--form ki`, and this review successfully exported the KIP viewer in that form outside the repository. Complete the promised re-export for both diagrams, update `svg_form` and the associated explanatory text, and refresh verification evidence before returning for acceptance. Keep the original Mermaid until the corrected diagrams receive sign-off.

Independent checks passed: exact six-heading Review packet and all planned checkboxes; all JSON and TOML parsing; diagram privacy and pinned-source checks; exact state and transition comparison; both Archify showcase finalizations, including validation, delivery, provenance and browser gates; both light SVG exports; Markdown lint; roadmap, authoring and diagrams audits; and the full repository audit with zero failures and five warnings. The diagrams audit retains its two expected Mermaid warnings. A first parallel finalization met Archify's shared-directory delivery lock; serial retry passed without changing sources.

The informative KIP sketch remains untouched, as instructed. Its `Implemented -> Superseded` edge conflicts with governance, lifecycle step 8 and both status diagrams; `Accepted -> Superseded` is the supported editorial correction, subject to the owner's separate disposition. No new work record was captured, no conform or hook change was run, and no remote operation was made.
