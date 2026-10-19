---
id: KI-SPEC-RGV-004
area: RGV
title: Archify status flow diagrams
kind: deliver
project: observatory
component: repository-governance
priority: medium
size: s
status: draft
horizon: now
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-10-19T07:37:29Z
updated_at: 2026-10-19T23:32:23Z
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

## Dependencies / blocks

The KI-theme static export is ki-agentic-harness work under the [`ki-diagrams` standard](https://github.com/knowledgeislands/ki-agentic-harness/blob/main/skills/governance/ki-diagrams/references/standards-diagrams.md). It does not block this record: export plain light now and re-export when the theme lands.

## Discussion

Handed over from the Observatory work under the cross-repository choreography in Knowledge Islands Principal's `AGENTS.md`. This repository owns its priority, plan and execution.
