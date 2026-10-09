---
id: KI-SPEC-RGV-001
area: RGV
title: Review KI Specifications
kind: deliver
purpose: corrective
project: specifications
component: repository-governance
status: cancelled
resolution: rejected
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-07-27T15:28:48Z
updated_at: 2026-10-09T21:08:04Z
---

## Goal

KI Specifications presents one consistent account of its retained future process: every tracked file has a recorded authority class, the KIP/KIS process documents agree with the documents the guides name as authority, and the Knowledge Package schema, templates, and examples are explicitly marked illustrative with a validation command that actually works. The dormant pre-v1 posture is preserved unchanged.

## Context

KI Specifications is the normative home for portable Knowledge Islands contracts, but its repository was bootstrapped before the current `ki` CLI and before its KIP/KIS model had been tested against sustained use. A close review is needed before expanding that normative surface.

This is a clean-end-state review, not a compatibility migration. It must identify the actual authority boundaries and retain only the repository structure, lifecycle, documentation, and tooling that the current model needs. Kris set the dormant posture in `4f7a13c` ("docs: mark specifications dormant before v1"): the retained process material describes the intended future process and is not an active specification programme. This review reconciles that material editorially; it does not reposition it.

## Boundary

- No trimming, relocation, or deletion of retained process material (`GOVERNANCE.md`, `docs/specification-process.md`, `docs/numbering.md`, `docs/versioning.md`) or of `schemas/`, `templates/`, and `examples/`.
- No KIP, KIS, or registry entry; `proposals/` and `specifications/` keep only their registry READMEs.
- No structural change to `schemas/knowledge-package.schema.json`, its `$id`, or any template or example manifest; only README prose and the schema `description` string may change.
- No change to `.ki.toml`, CI, or `.rumdl.toml`, and no edit in any other repository. A reusable shared-standard change is routed as a separate recipient item.
- No KBEP or KBIP informative note before the authority inventory confirms the informative-note location. The KBEP and KBIP dispositions merged from KI-SPEC-KIN-001 and KI-SPEC-KIN-002 follow it inside this record; see "Merged KBEP and KBIP assessments" under Discussion.
- `docs/adoption-guide.md` and `tooling/README.md` stay where they are; they gain cross-links, not a move into `docs/guides/`.


## Cancelled

Cancelled 2026-10-09 as rejected, approved by Kris Brown (state-of-play decisions log, Decision 22): Kris chose not to keep this as a work record. It is kept as an idea in Arcadia's specification-review Project (`ki-arcadia-principal`, `Streams/Projects/specification-review.md`). It leaves no outstanding change. The unstarted delivery plan is removed from this record; Git history holds it.

## Discussion

### Decisions under delegated autonomy

Decided by the Fable reviewer under delegated autonomy (2026-10-05), reversible:

- Keep the dormant posture Kris set in `4f7a13c` and retain the process material as described future process; do not trim or relocate it, because that would reverse an owner positioning choice whereas reconciliation is editorial.
- Resolve each disagreement mechanically: the document the guides name as authority wins and the others conform (`CONTRIBUTING.md` for the KIP file set; the lifecycle authority for `Implemented`, giving `Implemented` on KIS `Active`).
- `specifications/README.md` gains the KIS file set it is already claimed to describe.
- `schemas/`, `templates/`, `examples/`, and `docs/adoption-guide.md` receive an explicit "illustrative, not adopted by any KIS" statement.
- `docs/adoption-guide.md` and `tooling/README.md` stay in place with cross-links to `docs/guides/`.
- The authority inventory is a table in this record's Discussion. `docs/architecture-context.md` was the alternative, but it describes the wider ecosystem architecture rather than file authority, so it does not fit.
- Refresh the stale Verify list to the current toolchain.

### Facts corrected during shaping

- Lifecycle authority. `docs/guides/contributor/raising-a-kip.md:71` names `docs/specification-process.md`, not `GOVERNANCE.md`, as the lifecycle authority, and `GOVERNANCE.md` as the authority for who decides. `docs/specification-process.md` contradicts itself (line 17 against line 34). The decided outcome stands: its process step at line 34 agrees with `GOVERNANCE.md:26`, so `Implemented` on `Active` is the reading both authorities share, and line 17 conforms. The `README.md` KIP/KIS model paragraph was a further unlisted disagreement.
- KIS file set. No version of `specifications/README.md`, including the pre-reset one at `1a140df^`, ever described a file set; the set is derived from the two pre-reset KIS directories.
- Illustrative marking is partly in place already (schema `description`, `templates/README.md`).
- Validation. There are seven tracked manifests, not two, and every documented ajv command fails because `ajv-formats` is not resolvable from the `ajv-cli` package alone.
- Toolchain. `--skill ki-roadmap` is no longer a declared skill (the audit rejects it), and Prettier and markdownlint are replaced by rumdl per `.rumdl.toml`.
- Shared skill. The declared shared repository-shape skill is `ki-repo-specifications`, not `ki-specifications`.
- There is no existing KIP or KIS document set, so the former Step to review each set was dropped.

### Pickup checkpoint - 2026-09-28

At inspected local `main` `3e059cc00d5c03b5b8c9ed8c19070139485ad9fc`, parts of the old Current state are historical: `7e950a5cab3392b723e8e22dc3f2e4f385b2408b` conformed root `.gitignore` to marker-bounded rules; `b6aeaec` retired the vendored `.ki-meta/` checker footprint (no tracked `.ki-meta/` files remain); `1a140df06b626abc77424c2ca855a48867edcaf1` removed the premature KIP/KIS document sets, leaving only the two registry READMEs; and `4f7a13cd6e176d116812c546d2e251d9ea01ba1c` made `README.md`, `AGENTS.md`, and `.ki.toml` state the pre-v1 dormant posture. A fresh `ki repo audit --repo .` reported PASS across 19 selected skills, including `ki-repo`, `ki-work-roadmap`, and `ki-decision-records`. These mechanical results do not complete the requested authority inventory, reconcile every KIP/KIS governance claim, validate remaining schemas/templates/examples, or supply the judgment and owner review this record asks for. The original forty-two-file footprint and two draft KIS claims should not be treated as current. Before implementation, reconcile the destination branch, linked tasks, and retained worktrees. This checkpoint is pickup guidance, not an execution block or authority grant; absent evidence does not release any owner or lift a hold. Closure requires independent review of exact delivery, verification, explicit owner acceptance, and retention until explicit pruning selection.

### Compositional ignore handoff

The receiver-local outcome and source provenance now live in this canonical record, so the Harness projection of `TRD-bd26687c` can be retired after this update is committed. The handoff does not broaden the review or grant Harness authority over its priority, implementation, review, or acceptance.

### Owner question resolved (2026-10-05)

The 2026-10-04 question asked whether the retained future-process documents and the Knowledge Package `schemas/`, `templates/`, and `examples/` should be kept and reconciled, trimmed to a minimal holding statement, or moved out as illustrative material. Under Kris's delegated autonomy the Fable reviewer chose to keep and reconcile them, with the illustrative material marked in place rather than moved, as recorded under Decisions under delegated autonomy. The choice is reversible: a later owner decision to trim or relocate can follow this review without undoing it.

### Deferred to Waiting for (2026-10-06)

Moved from Now to Waiting for during the cross-repository roadmap clearance recorded in `+/_CHECKPOINTS/state-of-play.md` in `ki-arcadia-principal`. Named condition: Kris's planned review and discussion of every specification across the projects, which follows the thematic review in that checkpoint. This record is not an evidence-gathering assessment: it decides which document wins each disagreement (`Implemented` on KIS `Active`, the five-file KIP set, the KIS file set) and how illustrative material is marked. Those choices were made under delegated autonomy and are exactly what Kris's specification review will confirm or change, so delivering them now could be undone by that review. Return trigger: Kris's specification review settles the retained future process and the repository's posture; then reconfirm Current state and move back to Now. The broken manifest validation command (Current state, "Validation command") is a mechanical fix independent of those decisions and could be split out if Kris wants it earlier. Status returns from `ready` to `draft`, as the roadmap standard requires outside Now and Next; the shaped plan is retained and needs re-confirmation through `ki-plan` on return. No step was started.

### Parked (2026-10-07)

In the state-of-play roadmap review on 2026-10-07, Kris described ki-specifications as a future concept and put the whole repository on hold with the least work possible, so this record moves from `waiting-for` to `parked`. Return trigger: Kris restarts ki-specifications as a live specification effort. The questions previously asked of Kris here are deferred with it, unanswered. This includes the earlier offer to split out the broken manifest validation command (the ajv validation fix): it is not split out and stays deferred with this record. On return, re-check the Current state and re-confirm the plan through `ki-plan` before moving it to Now; `status` stays `draft`.

### Merged KBEP and KBIP assessments (2026-10-07)

Kris approved merging KI-SPEC-KIN-001 (Assess the KBEP extraction protocol) and KI-SPEC-KIN-002 (Assess the KBIP ingress protocol) into this record on 2026-10-07, under decision 17 of the state-of-play design, because both dispositions depend on the authority classes this review settles.

The kept scope: after the authority inventory, write one short informative note for each transferred draft protocol. The KBEP note gives every concern in the Knowledge Base Extraction Protocol a disposition, draws its portable-contract boundary, and recommends one of decline, retain as guidance, or carry forward as a candidate KIP for the v1 boundary review. The KBIP note separates extraction (KBEP) from governed ingress (KBIP), separates portable-contract candidates from Knowledge Base implementation guidance, names the relationship between the two protocols, and makes one recommendation as input to the v1 boundary review. Neither note is a proposal: no KIP or KIS number, no RFC 2119 keywords, and no wholesale copy of the source. Both sources survive only in KI Agentic Harness history at `0b4f7732640af6ceda02668d3be901751b02bc26` (`+/_HANDOFFS/KBEP-knowledge-base-extraction-protocol.md` and `+/_HANDOFFS/KBIP-knowledge-base-ingress-protocol.md`), with the companion `+/_HANDOFFS/knowledge-acquisition-protocols.md` recording the intended lifecycle.

The full shaped assessments are at their last open revisions: [KI-SPEC-KIN-001](https://github.com/knowledgeislands/ki-specifications/blob/fd96a5e/docs/roadmap/KI-SPEC-KIN-001-assess-kbep-extraction-protocol.md) and [KI-SPEC-KIN-002](https://github.com/knowledgeislands/ki-specifications/blob/fd96a5e/docs/roadmap/KI-SPEC-KIN-002-assess-kbip-ingress-protocol.md). This record's Steps, Files touched and Verify predate the merge; on return, `ki-plan` re-plans them to include both notes.
