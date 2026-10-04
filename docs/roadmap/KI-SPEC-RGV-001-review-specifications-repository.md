---
id: KI-SPEC-RGV-001
area: RGV
title: Review KI Specifications
theme: repository-governance
horizon: next
status: draft
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-07-27T15:28:48Z
updated_at: 2026-10-04T12:15:00Z
---

## Goal

Achieve the stated outcome: Review KI Specifications as a complete repository.

## Context

KI Specifications is the normative home for portable Knowledge Islands contracts, but its repository was bootstrapped before the current `ki` CLI and before its KIP/KIS model had been tested against sustained use. A close review is needed before expanding that normative surface.

This is a clean-end-state review, not a compatibility migration. It must identify the actual authority boundaries and retain only the repository structure, lifecycle, documentation, and tooling that the current model needs.

## Boundary

Keep the work limited to the stated surface.

## Current state

Refreshed at `234c846` (2026-10-04). The repository is in its declared dormant pre-v1 posture: `proposals/` and `specifications/` hold only empty registry READMEs; no tracked `.ki-meta/` file remains; root `.gitignore` is marker-bounded; the GitHub description matches `.ki.toml`; and `ki repo audit --repo .` passes across 19 skills, including `ki-guides`, which KI-SPEC-RGV-003 added with a contributor and implementer guide collection under `docs/guides/`. The ignore, `.ki-meta/`, README-drift, and description outcomes originally listed here are therefore delivered; the remaining work is the judgement review.

Known disagreements across the retained process material, found while writing the guides:

- `GOVERNANCE.md` marks a KIP `Implemented` when its KIS is promoted to `Active`; `docs/specification-process.md` and `CONTRIBUTING.md` mark it on KIS publication at `Draft`.
- `CONTRIBUTING.md` requires a fixed five-file KIP set; `proposals/README.md` requires a minimum of three.
- `docs/specification-process.md` says the KIS file set is described in `specifications/README.md`, which describes none.
- `docs/adoption-guide.md` and `tooling/README.md` are guide-shaped documents outside `docs/guides/`.
- `schemas/`, `templates/`, and `examples/` remain, with no KIS adopting them, and `docs/adoption-guide.md` speaks of them as a specification ("Nothing in this specification assumes ...").

## Steps

- [ ] Inventory the complete repository authority surface and record which files are normative, informative, generated, illustrative, historical, or operational. Compare the stated ecosystem responsibility with the harness, `tools-ki`, Website, and Arcadia boundaries without importing their implementation detail.
- [ ] Reconcile the KIP/KIS governance model across `README.md`, `GOVERNANCE.md`, `CONTRIBUTING.md`, numbering, lifecycle, versioning, registries, status files, and Decision Records. Resolve contradictory status, version, authority, amendment, and publication claims through one clean current model.
- [ ] Review each existing KIP and KIS document set for internal completeness, correct lifecycle state, provenance to its originating decision, and an explicit normative-versus-informative boundary. Do not expand KBEP or KBIP here; keep their assessment plans independent.
- [ ] Review schemas, templates, examples, and tooling guidance against the specifications they claim to represent. Remove or correct unsupported conformance claims, stale anticipated behaviour, invalid fixtures, and duplicated authority; retain concrete validation evidence.
- [ ] Decide whether any stable repository-shape rule belongs in the shared `ki-specifications` skill. Keep repository-specific detail local; route only a genuinely reusable contract change to the harness through a focused recipient item.
- [ ] Align entry-point and contributor documentation with the reviewed end state, run the complete verification set, and record any deliberately deferred normative question as a separate roadmap item rather than leaving an ambiguous TODO.

## Files touched

- Repository authority and contribution documents at the root and under `docs/`
- `proposals/`, `specifications/`, `schemas/`, `templates/`, `examples/`, and `tooling/`
- `.ki.toml` and authoring configuration, only if the review changes them
- Repository roadmap files and any focused outbound recipient brief justified by the review

## Verify

1. `ki repo audit --repo .`
2. `ki repo audit --repo . --skill ki-roadmap`
3. `ki repo audit --repo . --skill ki-decision-records`
4. `bun x prettier --check '**/*.{md,json,jsonc,yaml,yml}'`
5. `bun x markdownlint-cli2`
6. Validate every tracked example manifest against `schemas/knowledge-package.schema.json` with the documented AJV command.
7. Confirm no tracked `.ki-meta/` executor, vendored checker, retired capability name, or duplicate KIP/KIS registry claim remains.
8. `ki repo audit --skill ki-repo --repo .` passes the compositional ignore contract.

## Dependencies / blocks

This review is independent of the open KBEP and KBIP assessments. Those plans preserve transferred ideas but must not define or expand the repository model while this review is active.

The review may cite implementation evidence from other repositories, but it does not directly edit them. A reusable shared-standard change requires a separately accepted recipient item in the harness.

## Documentation impact

### Decision Records

None.

### Specifications

Update affected specification records when review findings establish a behaviour change.

### Guides

Update contributor guidance only where the review changes the practical workflow.

### Roadmap

Capture any non-trivial follow-up as separately prioritised roadmap work.

## Delegation

- Round 1 — research: inventory authority, lifecycle claims, corpus status, and cross-repository boundaries; read-only; gate: evidence matrix with exact source locations.
- Round 1 — mechanical: inventory tracked legacy/runtime footprint, configuration drift, links, schemas, templates, examples, and current audit findings; read-only; gate: reproducible command output.
- Round 2 — judgment: reconcile the one intended KIP/KIS and repository model from Round 1 evidence; gate: maintainer review before normative or governance edits.
- Round 3 — implementation: apply the accepted clean end state in exclusive file groups; gate each group independently before commit.

## Discussion

### Pickup checkpoint — 2026-09-28

At inspected local `main` `3e059cc00d5c03b5b8c9ed8c19070139485ad9fc`, parts of the old Current state are historical: `7e950a5cab3392b723e8e22dc3f2e4f385b2408b` conformed root `.gitignore` to marker-bounded rules; `b6aeaec` retired the vendored `.ki-meta/` checker footprint (no tracked `.ki-meta/` files remain); `1a140df06b626abc77424c2ca855a48867edcaf1` removed the premature KIP/KIS document sets, leaving only the two registry READMEs; and `4f7a13cd6e176d116812c546d2e251d9ea01ba1c` made `README.md`, `AGENTS.md`, and `.ki.toml` state the pre-v1 dormant posture. A fresh `ki repo audit --repo .` reported PASS across 19 selected skills, including `ki-repo`, `ki-work-roadmap`, and `ki-decision-records`. These mechanical results do not complete the requested authority inventory, reconcile every KIP/KIS governance claim, validate remaining schemas/templates/examples, or supply the judgment and owner review this record asks for. The original forty-two-file footprint and two draft KIS claims should not be treated as current; the Step checkboxes and `next`/`draft` lifecycle remain unchanged. Before implementation, reconcile the destination branch, linked tasks, and retained worktrees, then re-scope the clean-end-state review against the dormant posture and current files. This checkpoint is pickup guidance, not an execution block or authority grant; absent evidence does not release any owner or lift a hold. Closure requires independent review of exact delivery, verification, explicit owner acceptance, and retention until explicit pruning selection.

### Compositional ignore handoff

The receiver-local outcome and source provenance now live in this canonical record, so the Harness projection of `TRD-bd26687c` can be retired after this update is committed. The handoff does not broaden the review or grant Harness authority over its priority, implementation, review, or acceptance.

### Blocker - owner decision needed (2026-10-04)

The remaining Steps are judgement work whose Round 2 gate already requires maintainer review before any normative or governance edit. The deciding question is not mechanical: under the dormant posture, should the retained future-process material (`GOVERNANCE.md` pipeline, `docs/specification-process.md`, `docs/numbering.md`, `docs/versioning.md`) and the Knowledge Package `schemas/`, `templates/`, and `examples/` be kept and reconciled as the intended v1 process, trimmed to a minimal holding statement, or moved out as illustrative material? Each answer produces a different clean end state. The record stays `draft` until Kris chooses; once chosen, it can be re-shaped to Ready with the Current state disagreements above as its first reconciliation list.
