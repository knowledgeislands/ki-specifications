---
id: KI-SPEC-RGV-004
area: RGV
title: Archify status flow diagrams
kind: deliver
project: observatory
component: repository-governance
priority: medium
size: s
status: ready
horizon: now
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-10-19T07:37:29Z
updated_at: 2026-10-20T06:32:30Z
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

- [ ] Write `docs/diagrams/kip-status.lifecycle.json` and `docs/diagrams/kis-status.lifecycle.json` as Archify lifecycle sources carrying every state and transition of the two Mermaid fences, each state citing its line in `docs/specification-process.md` at revision `6b4e2e3`.
- [ ] Finalize both at showcase quality outside the repository and export each as a static `light` SVG to `docs/diagrams/<slug>.svg` with the `ki-diagrams` exporter.
- [ ] Add `docs/diagrams/diagrams.toml` and `docs/diagrams/README.md` from the `ki-diagrams` templates, with `svg_form = "light"` and `last_checked` at the traced revision.
- [ ] Embed each SVG above its original fence in `docs/specification-process.md`, moving the fence into a collapsed `<details>` block that says it is kept until sign-off.
- [ ] Declare `[skills.ki-diagrams]` in `.ki.toml` so the repository audit checks the diagram set.
- [ ] Run the checks under Verify and complete the review packet.

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

## Discussion

Handed over from the Observatory work under the cross-repository choreography in Knowledge Islands Principal's `AGENTS.md`. This repository owns its priority, plan and execution.
