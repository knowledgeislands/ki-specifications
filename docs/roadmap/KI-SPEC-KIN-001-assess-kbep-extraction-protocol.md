---
id: KI-SPEC-KIN-001
area: KIN
title: Assess KBEP extraction protocol
kind: investigate
project: specifications
component: knowledge-ingress
status: cancelled
resolution: merged
resolution_target: KI-SPEC-RGV-001
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-07-27T14:37:34Z
updated_at: 2026-10-07T20:37:16Z
transferred_from: knowledgeislands/ki-agentic-harness:+/_HANDOFFS/KBEP-knowledge-base-extraction-protocol.md
---

## Goal

KI Specifications holds one short informative note that gives every concern in the transferred Knowledge Base Extraction Protocol (KBEP) a disposition, draws its portable-contract boundary, and makes one recommendation: decline, retain as guidance, or carry forward as a candidate KIP for the v1 boundary review. The note is input to that review, not a proposal.

## Context

The KI Agentic Harness transferred a parked draft of the Knowledge Base Extraction Protocol (KBEP). Its useful concern is a portable way to extract reusable, provenance-bearing knowledge from source material; it explicitly does not establish a receiving repository's protocol, implementation, or priority.

The source survives only in harness history. `887da0536908` ("chore(handoffs): complete specifications transfer", 2026-07-27) deleted `+/_HANDOFFS/KBEP-knowledge-base-extraction-protocol.md` (374 lines), so the `transferred_from` path no longer resolves at harness `HEAD`; the readable revision is `887da053^` (`0b4f7732640af6ceda02668d3be901751b02bc26`). The companion `+/_HANDOFFS/knowledge-acquisition-protocols.md` at the same revision records the intended lifecycle (KAF acquisition, immutable Knowledge Export Package, KBEP extraction, KBIP governed ingress). No copy exists in KI Specifications.

KI Specifications carries no registered proposals or specifications, so there is no existing Knowledge Export Package work for KBEP to attach to; the premature `KIS-0002` Knowledge Export Package set was removed in `1a140df`. Under the dormant pre-v1 posture the guides' own route for an ecosystem-wide concern today is to record it as input to the v1 boundary review rather than register a proposal (`docs/guides/contributor/deciding-whether-a-change-needs-a-kip.md`, "What to do today").

## Boundary

- No KIP, KIS, proposal outline, schema, template, or registry change; `proposals/` and `specifications/` are untouched.
- No new directory class; the note is one file in the informative-note location.
- No normative language: no RFC 2119 keywords and no KIP or KIS number in the note.
- No wholesale copy of the source; the note summarises and cites it by repository, path, and full revision.
- No assessment of KBIP (KI-SPEC-KIN-002) or of KAF acquisition, and no edit in the harness or any other repository.

## Cancelled

Approved by Kris on 2026-10-07 under decision 17 of the state-of-play design, which approved every cancel and merge in the easiest-first delivery plan.

Resolution `merged` into [KI-SPEC-RGV-001](KI-SPEC-RGV-001-review-specifications-repository.md): the KBEP disposition depends on the authority classes that review settles. The scope worth keeping is folded into that record's Boundary and Discussion. It leaves no outstanding change of its own.

## Discussion

### Decisions under delegated autonomy

Decided by the Fable reviewer under delegated autonomy (2026-10-05), reversible:

- Run the assessment now as one short non-normative note recording the recommendation and the portable-contract boundary, with no KIP, KIS, registry, `proposals/` change, or new directory class. This is consistent with the dormant posture because the guides route an ecosystem-wide concern today to the v1 boundary review rather than to a proposal.
- Strike the former Step 4 proposal-outline route.
- Sequence the work after KI-SPEC-RGV-001 so the note lands in the location its authority inventory establishes, rather than adding unclassified material during the review.
- The note cites its source by revision, because the source survives only in harness history.

### Facts corrected during shaping

- Fable proposed `blocked_by: [KI-SPEC-RGV-001]`. The roadmap audit fails any `ready` item whose `blocked_by` names an item that is not done, and the ordering is a preference rather than build order, so it is expressed as the first Step and a Dependencies sentence with `blocked_by: []`.
- Source provenance verified: 374 lines, deleted by `887da0536908`, readable at parent `0b4f7732640af6ceda02668d3be901751b02bc26`; the companion `knowledge-acquisition-protocols.md` at that revision adds the lifecycle context the note needs.

### Owner question resolved (2026-10-05)

The 2026-10-04 question asked whether the KBEP assessment should run now as a non-normative background note or be parked until the v1 boundary review. Under Kris's delegated autonomy the Fable reviewer chose to run it now as a non-normative note, sequenced after KI-SPEC-RGV-001, with no KIP route; the same answer covers KI-SPEC-KIN-002. The choice is reversible: the note can be withdrawn or superseded by the v1 boundary review.

### Deferred to Waiting for (2026-10-06)

Moved from Now to Waiting for during the cross-repository roadmap clearance recorded in `+/_CHECKPOINTS/state-of-play.md` in `ki-arcadia-principal`. Named condition: in-flight `KI-ARCADIA-MOD-006` (Knowledge acquisition lifecycle, Ready in `ki-arcadia-principal`) and the thematic review in that checkpoint. MOD-006 is defining the operational acquisition lifecycle, provenance package and harvest checkpoint that KBEP's extraction pipeline, provenance and output structure overlap, so this assessment's portable-contract boundary and section dispositions would be drawn against a model that review may change. Its sequencing preference after KI-SPEC-RGV-001, also now Waiting for, is likewise unresolved. Return trigger: MOD-006 is accepted or redirected by the review, and Kris's specification review confirms this note is still wanted; then move back to Now. Status returns from `ready` to `draft`, as the roadmap standard requires outside Now and Next; the shaped plan is retained and needs re-confirmation through `ki-plan` on return. No step was started.

### Parked (2026-10-07)

In the state-of-play roadmap review on 2026-10-07, Kris described ki-specifications as a future concept and put the whole repository on hold with the least work possible, so this record moves from `waiting-for` to `parked`. Return trigger: Kris restarts ki-specifications as a live specification effort. The questions previously asked of Kris here are deferred with it, unanswered. On return, re-check the Current state and re-confirm the plan through `ki-plan` before moving it to Now; `status` stays `draft`.
