---
id: KI-SPEC-KIN-001
area: KIN
title: Assess KBEP extraction protocol
kind: investigate
project: specifications
component: knowledge-ingress
horizon: hold
hold:
  reason: parked
  condition: Kris restarts the ki-specifications live specification effort
status: draft
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-07-27T14:37:34Z
updated_at: 2026-10-07T14:10:13Z
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

## Current state

At `49403d3` (2026-10-05), KI Specifications has no KBEP proposal, KIS, schema, note, or conformance claim, and its KIP and KIS registries are empty following the deliberate reset of premature normative content in `1a140df`. `docs/` already holds informative documents, each opening with an informative marker. The KBEP source has twelve top-level sections: Purpose, Scope, Supported Source Types, Objectives, Principles, Knowledge Units, Extraction Pipeline (six stages: Source Capture, Knowledge Extraction, Knowledge Normalisation, Relationship Discovery, Provenance, Quality Review), Confidence, Knowledge Status, Recommended Output Structure, Non-Goals, and Success Criteria. Its own status block says it is a parked handoff whose concrete pipeline, source-type support, and output format must not be implemented without a receiving-repository decision.

## Steps

- [ ] Confirm KI-SPEC-RGV-001's authority inventory has fixed the informative note location (default `docs/`) before writing; if that inventory has not yet run, use `docs/` and say so in Discussion.
- [ ] Read the source with `git -C ../ki-agentic-harness show 887da053^:+/_HANDOFFS/KBEP-knowledge-base-extraction-protocol.md`, together with `+/_HANDOFFS/knowledge-acquisition-protocols.md` at the same revision.
- [ ] Establish whether KBEP's purpose, scope, source types, knowledge units, six-stage pipeline, provenance, confidence, knowledge status, and output structure describe a portable concern at all, as distinct from one knowledge base's operating practice.
- [ ] Draw the portable-contract boundary and give each of the twelve source sections one disposition: candidate portable contract, retained as guidance, deferred, or out of scope.
- [ ] Write `docs/kbep-extraction-assessment.md` (or the same filename in the confirmed location): open with "This document is informative throughout.", state the single recommendation (decline, retain as guidance, or candidate KIP for the v1 boundary review) with its reasoning, include the disposition table, and cite the source as `knowledgeislands/ki-agentic-harness` `+/_HANDOFFS/KBEP-knowledge-base-extraction-protocol.md` at `0b4f7732640af6ceda02668d3be901751b02bc26`.
- [ ] Run Verify and record the recommendation in one sentence under Discussion for KI-SPEC-KIN-002 to consume.

## Files touched

- `docs/kbep-extraction-assessment.md` (new; location per KI-SPEC-RGV-001, default `docs/`)
- `docs/roadmap/KI-SPEC-KIN-001-assess-kbep-extraction-protocol.md`

## Verify

1. `ki repo audit --repo . --progress never` passes (the CI gate, `.github/workflows/ci.yml:59`).
2. `ki repo audit --repo . --skill ki-work-roadmap` passes.
3. `rumdl check .`, `rumdl fmt --check .`, and `rumdl check --enable MD057 .` report no issues.
4. `grep -nwE 'MUST|REQUIRED|SHALL|SHOULD|RECOMMENDED|MAY|OPTIONAL' docs/kbep-extraction-assessment.md` returns nothing.
5. `grep -nE 'KIP-[0-9]|KIS-[0-9]' docs/kbep-extraction-assessment.md` returns nothing.
6. `grep -n '0b4f7732640af6ceda02668d3be901751b02bc26' docs/kbep-extraction-assessment.md` finds the provenance citation, and `head -3 docs/kbep-extraction-assessment.md` shows the informative marker.
7. `git diff --exit-code <baseline_ref> -- proposals specifications schemas templates examples` reports no change.
8. The note gives a disposition for each of the twelve source sections and exactly one recommendation.

## Dependencies / blocks

Parked. Return trigger: Kris restarts ki-specifications as a live specification effort. The earlier waiting-for condition and return trigger under Discussion are superseded until then.

This item has no prerequisite and blocks nothing. It prefers to run after KI-SPEC-RGV-001 so the note lands where that review's authority inventory confirms informative notes belong; that is a sequencing preference, not build order, so `blocked_by` stays empty and the first Step carries the check. KI-SPEC-KIN-002 prefers to run after this item and consumes its recommendation. The originating harness handoff neither blocks nor is blocked by this recipient-owned assessment.

## Documentation impact

### Decision Records

None. The note is informative and its recommendation is reversible input to the v1 boundary review; any later decision to open a KIP belongs to that review.

### Specifications

None. No KIP, KIS, schema, or registry changes, and the note carries no normative requirement.

### Guides

None. The note follows the existing "What to do today" route in the contributor guides and changes no practical workflow.

### Roadmap

KI-SPEC-KIN-002 takes this item's recommendation as input. A "candidate KIP" recommendation is carried by the note itself as v1 boundary review input; no new roadmap item opens while the repository is dormant.

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
