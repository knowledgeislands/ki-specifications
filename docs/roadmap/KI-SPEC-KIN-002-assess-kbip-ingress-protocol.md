---
id: 'KI-SPEC-KIN-002'
title: Assess KBIP knowledge-base-ingress protocol
theme: knowledge-ingress
horizon: soon
status: open
blocks: []
blocked-by: []
baseline-ref: null
transferred-from: knowledgeislands/ki-agentic-harness:+/_HANDOFFS/KBIP-knowledge-base-ingress-protocol.md
---

## Goal

Achieve the stated outcome: Assess KBIP knowledge-base-ingress protocol.

## Context

The KI Agentic Harness transferred a parked draft of the Knowledge Islands Knowledge Base Ingress Protocol (KBIP). Its useful concern is the boundary between extracted material and governed, evolving canonical knowledge, while its concrete lifecycle, governance model, and output structure remain unadopted.

KI Specifications is the normative home for portable contracts. This assessment determines whether KBIP defines a portable specification concern, which parts belong to Knowledge Base implementation guidance rather than a KIP/KIS, and how it should relate to any KBEP conclusion.

## Boundary

Keep the work limited to the stated surface.

## Shaping

### Current state

The handoff exists only in the harness working area. KI Specifications has no adopted KBIP proposal, KIS, schema, or conformance claim. Current specifications establish Knowledge Packages and Knowledge Export Packages, not an agreed protocol for canonicalising imported knowledge into a governed knowledge base.

### Steps

1. Compare the transferred KBIP stages and concepts with the repository's existing KIP/KIS material, especially provenance, governance, lifecycle, and Knowledge Export Package boundaries.
2. Separate candidate portable contract requirements from repository-specific Knowledge Base operations, implementation choices, and aspirational model detail.
3. Determine the dependency relationship to the KBEP assessment without treating that assessment as an adopted prerequisite.
4. Record a recommendation to decline, route into existing work, or open a separately numbered KIP with a bounded problem statement, explicit non-goals, and proposed evidence needed before a KIS.

### Files touched

- `proposals/` — only if the assessment recommends and receives approval for a new or amended KIP.
- `specifications/` — only after an accepted KIP establishes a normative scope.
- `docs/roadmap/knowledge-ingress/` — plan lifecycle and local roadmap state.

### Verify

1. The assessment explicitly distinguishes KBEP extraction from KBIP governed ingress and names the relationship between the two.
2. Every recommended normative requirement has a clear portable boundary; implementation-specific governance workflow and storage choices are excluded or routed elsewhere.
3. Any proposed work identifies its KIP/KIS lifecycle route and does not claim adoption before a maintainer decision.
4. Relevant Markdown and roadmap audits pass after the resulting scoped change.

### Dependencies / blocks

This transferred record is deliberately open in `Soon`: no readiness approval has been given, and the work does not block a local `Next` item. The originating handoff neither blocks nor is blocked by this recipient-owned assessment; it supplies background while KI Specifications owns the adoption decision. Its assessment should use the KBEP disposition as input where available, but it has no plan-level blocker and can independently establish that no portable ingress specification is warranted.

## Discussion
