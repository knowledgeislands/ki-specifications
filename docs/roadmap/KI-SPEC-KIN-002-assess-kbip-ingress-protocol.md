---
id: KI-SPEC-KIN-002
area: KIN
title: Assess KBIP ingress protocol
theme: knowledge-ingress
horizon: parked
status: draft
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-07-27T14:37:34Z
updated_at: 2026-10-07T08:20:00Z
transferred_from: knowledgeislands/ki-agentic-harness:+/_HANDOFFS/KBIP-knowledge-base-ingress-protocol.md
---

## Goal

KI Specifications holds one short informative note that assesses the transferred Knowledge Islands Knowledge Base Ingress Protocol (KBIP). It separates extraction (KBEP) from governed ingress (KBIP), separates portable-contract candidates from Knowledge Base implementation guidance, names the relationship between the two protocols, and makes one recommendation as input to the v1 boundary review.

## Context

The KI Agentic Harness transferred a parked draft of the Knowledge Islands Knowledge Base Ingress Protocol (KBIP). Its useful concern is the boundary between extracted material and governed, evolving canonical knowledge, while its concrete lifecycle, governance model, and output structure remain unadopted.

The source survives only in harness history. `887da0536908` ("chore(handoffs): complete specifications transfer", 2026-07-27) deleted `+/_HANDOFFS/KBIP-knowledge-base-ingress-protocol.md` (334 lines), so the `transferred_from` path no longer resolves at harness `HEAD`; the readable revision is `887da053^` (`0b4f7732640af6ceda02668d3be901751b02bc26`). The companion `+/_HANDOFFS/knowledge-acquisition-protocols.md` at the same revision places KBIP after KBEP in the intended lifecycle and records that KBIP preserves a governance boundary and immutable upstream lineage. No copy exists in KI Specifications.

KI Specifications is intended to become the normative home for portable contracts after the v1 boundary review, but under the dormant pre-v1 posture the guides route an ecosystem-wide concern today to that review rather than to a proposal. This assessment therefore records a disposition; it does not open a KIP route.

## Boundary

- No KIP, KIS, proposal outline, schema, template, or registry change; `proposals/` and `specifications/` are untouched.
- No new directory class; the note is one file in the informative-note location.
- No normative language: no RFC 2119 keywords and no KIP or KIS number in the note.
- No wholesale copy of the source; the note summarises and cites it by repository, path, and full revision.
- No reassessment of KBEP: the KI-SPEC-KIN-001 recommendation is taken as input, not reopened.
- No Knowledge Base governance workflow, storage, or publication mechanics are specified; those are routed to implementation guidance by name only.
- No edit in the harness or any other repository.

## Current state

At `49403d3` (2026-10-05), KI Specifications has no KBIP proposal, KIS, schema, note, or conformance claim. No KIS is registered, and no Knowledge Export Package material remains: the premature `KIS-0002` Knowledge Export Package set was removed in `1a140df`. The only related material is the illustrative Knowledge Package schema, templates, and examples, whose schema carries `provenance`, `governance`, `lifecycle`, and `history` fields. The KBIP source has eleven top-level sections: Purpose, Separation of Concerns, Objectives, Import Lifecycle (seven stages: Intake, Classification, Canonicalisation, Relationship Enrichment, Governance Assignment, Publication, Continuous Evolution), Canonical Knowledge, Trust Levels, Knowledge Maturity, Provenance, Continuous Collaboration, Recommended Output Structure, and End Goal. Its own status block says it is a parked handoff whose import lifecycle, governance model, and output structure must not be implemented without a receiving-repository decision.

## Steps

- [ ] Confirm KI-SPEC-RGV-001's authority inventory has fixed the informative note location (default `docs/`) and that KI-SPEC-KIN-001 has recorded its KBEP recommendation before writing; if either has not yet run, use `docs/`, treat the KBEP disposition as open, and say so in the note and in Discussion.
- [ ] Read the source with `git -C ../ki-agentic-harness show 887da053^:+/_HANDOFFS/KBIP-knowledge-base-ingress-protocol.md`, together with `+/_HANDOFFS/knowledge-acquisition-protocols.md` at the same revision.
- [ ] Compare KBIP's stages and concepts with the KBEP note and with the illustrative Knowledge Package schema's `provenance`, `governance`, `lifecycle`, and `history` fields, without treating either as adopted.
- [ ] Separate candidate portable-contract concerns from Knowledge Base implementation guidance, operating choices, and aspirational model detail, and give each of the eleven source sections one disposition: candidate portable contract, Knowledge Base implementation guidance, deferred, or out of scope.
- [ ] Name the relationship between KBEP extraction and KBIP governed ingress, including what KBIP assumes of KBEP output and the upstream lineage it preserves.
- [ ] Write `docs/kbip-ingress-assessment.md` (or the same filename in the confirmed location): open with "This document is informative throughout.", state the single recommendation (decline, retain as Knowledge Base guidance, or candidate KIP for the v1 boundary review) with its reasoning, include the disposition table and the KBEP/KBIP relationship, link the KBEP note, and cite the source as `knowledgeislands/ki-agentic-harness` `+/_HANDOFFS/KBIP-knowledge-base-ingress-protocol.md` at `0b4f7732640af6ceda02668d3be901751b02bc26`.
- [ ] Run Verify and record the recommendation in one sentence under Discussion.

## Files touched

- `docs/kbip-ingress-assessment.md` (new; location per KI-SPEC-RGV-001, default `docs/`)
- `docs/roadmap/KI-SPEC-KIN-002-assess-kbip-ingress-protocol.md`

## Verify

1. `ki repo audit --repo . --progress never` passes (the CI gate, `.github/workflows/ci.yml:59`).
2. `ki repo audit --repo . --skill ki-work-roadmap` passes.
3. `rumdl check .`, `rumdl fmt --check .`, and `rumdl check --enable MD057 .` report no issues.
4. `grep -nwE 'MUST|REQUIRED|SHALL|SHOULD|RECOMMENDED|MAY|OPTIONAL' docs/kbip-ingress-assessment.md` returns nothing.
5. `grep -nE 'KIP-[0-9]|KIS-[0-9]' docs/kbip-ingress-assessment.md` returns nothing.
6. `grep -n '0b4f7732640af6ceda02668d3be901751b02bc26' docs/kbip-ingress-assessment.md` finds the provenance citation, and `head -3 docs/kbip-ingress-assessment.md` shows the informative marker.
7. `git diff --exit-code <baseline_ref> -- proposals specifications schemas templates examples` reports no change.
8. The note gives a disposition for each of the eleven source sections, distinguishes KBEP extraction from KBIP governed ingress and names their relationship, routes governance workflow and storage choices to implementation guidance, and makes exactly one recommendation.

## Dependencies / blocks

Parked. Return trigger: Kris restarts ki-specifications as a live specification effort. The earlier waiting-for condition and return trigger under Discussion are superseded until then.

This item has no prerequisite and blocks nothing. It prefers to run after KI-SPEC-RGV-001, so the note lands where that review's authority inventory confirms informative notes belong, and after KI-SPEC-KIN-001, so it can take the KBEP recommendation as input. Both are sequencing preferences, not build order, so `blocked_by` stays empty and the first Step carries the checks. The originating harness handoff neither blocks nor is blocked by this recipient-owned assessment.

## Documentation impact

### Decision Records

None. The note is informative and its recommendation is reversible input to the v1 boundary review; any later decision to open a KIP belongs to that review.

### Specifications

None. No KIP, KIS, schema, or registry changes, and the note carries no normative requirement.

### Guides

None. The note follows the existing "What to do today" route in the contributor guides and changes no practical workflow.

### Roadmap

No follow-on item. A "candidate KIP" recommendation is carried by the note itself as v1 boundary review input, and anything routed to Knowledge Base implementation guidance is named for its owning repository without opening a handoff while the repository is dormant.

## Discussion

### Decisions under delegated autonomy

Decided by the Fable reviewer under delegated autonomy (2026-10-05), reversible:

- Use the same non-normative note route as KI-SPEC-KIN-001, explicitly separating extraction (KBEP) from governed ingress (KBIP), separating portable-contract candidates from Knowledge Base implementation guidance, and naming the relationship between the two; no KIP, KIS, or registry change.
- Correct the stale Current state claim that current specifications establish Knowledge Packages and Knowledge Export Packages.
- Sequence the work after KI-SPEC-RGV-001 and after KI-SPEC-KIN-001, because the note takes the KBEP disposition as input.
- The note cites its source by revision, because the source survives only in harness history.

### Facts corrected during shaping

- The former Current state said current specifications establish Knowledge Packages and Knowledge Export Packages. No KIS is registered; `1a140df` removed the `KIS-0001` Knowledge Package and `KIS-0002` Knowledge Export Package sets, and only the illustrative Knowledge Package schema, templates, and examples remain. The former first Step compared KBIP with "existing KIP/KIS material" and so now compares it with the KBEP note and the illustrative schema fields instead.
- Fable proposed `blocked_by: [KI-SPEC-RGV-001, KI-SPEC-KIN-001]`. The roadmap audit fails any `ready` item whose `blocked_by` names an item that is not done, and the ordering is a preference rather than build order, so it is expressed as the first Step and a Dependencies sentence with `blocked_by: []`.
- Source provenance verified: 334 lines, deleted by `887da0536908`, readable at parent `0b4f7732640af6ceda02668d3be901751b02bc26`.

### Owner question resolved (2026-10-05)

The 2026-10-04 question asked whether the KBIP assessment should run now as a non-normative background note or be parked until the v1 boundary review. Under Kris's delegated autonomy the Fable reviewer chose to run it now as a non-normative note, sequenced after KI-SPEC-RGV-001 and KI-SPEC-KIN-001, with no KIP route; the same answer covers KI-SPEC-KIN-001. The choice is reversible: the note can be withdrawn or superseded by the v1 boundary review.

### Deferred to Waiting for (2026-10-06)

Moved from Now to Waiting for during the cross-repository roadmap clearance recorded in `+/_CHECKPOINTS/state-of-play.md` in `ki-arcadia-principal`. Named condition: in-flight `KI-ARCADIA-MOD-006` (Knowledge acquisition lifecycle, Ready in `ki-arcadia-principal`) and the thematic review in that checkpoint, plus KI-SPEC-KIN-001, whose recommendation this item consumes and which is now Waiting for on the same condition. MOD-006's stage owners, harvest checkpoint and imperfect-routing handling overlap KBIP's governed ingress directly. Return trigger: KI-SPEC-KIN-001 returns to Now and its recommendation lands; then move back to Now. Status returns from `ready` to `draft`, as the roadmap standard requires outside Now and Next; the shaped plan is retained and needs re-confirmation through `ki-plan` on return. No step was started.

### Parked (2026-10-07)

In the state-of-play roadmap review on 2026-10-07, Kris described ki-specifications as a future concept and put the whole repository on hold with the least work possible, so this record moves from `waiting-for` to `parked`. Return trigger: Kris restarts ki-specifications as a live specification effort. The questions previously asked of Kris here are deferred with it, unanswered. On return, re-check the Current state and re-confirm the plan through `ki-plan` before moving it to Now; `status` stays `draft`.
