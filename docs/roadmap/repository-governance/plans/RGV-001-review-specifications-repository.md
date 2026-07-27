---
id: 'RGV-001'
title: Review KI Specifications as a complete repository
status: open
roadmap: repository-governance/review-ki-specifications-as-a-complete-repository
blocks: —
blocked-by: —
baseline-ref: —
---

## Context

KI Specifications is the normative home for portable Knowledge Islands contracts, but its repository was bootstrapped before the current `ki` CLI and before its KIP/KIS model had been tested against sustained use. A close review is needed before expanding that normative surface.

This is a clean-end-state review, not a compatibility migration. It must identify the actual authority boundaries and retain only the repository structure, lifecycle, documentation, and tooling that the current model needs.

## Current state

The repository carries two draft KIS document sets, two registered KIPs, schemas, templates, examples, process documentation, and one local governance decision plus one mirrored ecosystem decision.

The current full `ki repo audit` reports README formatting drift, a stale authoring configuration, and a missing GitHub description. Forty-two tracked files remain under the retired `.ki-meta/` executor and vendored-checker footprint even though repository operations now run through the installed `ki` CLI.

The authority surface is spread across `README.md`, `GOVERNANCE.md`, `CONTRIBUTING.md`, process and versioning guides, KIP/KIS registries, per-document status files, schemas, templates, and examples. Their agreement has not yet been reviewed as one contract.

## Steps

1. Inventory the complete repository authority surface and record which files are normative, informative, generated, illustrative, historical, or operational. Compare the stated ecosystem responsibility with the harness, `tools-ki`, Website, and Arcadia boundaries without importing their implementation detail.
2. Reconcile the KIP/KIS governance model across `README.md`, `GOVERNANCE.md`, `CONTRIBUTING.md`, numbering, lifecycle, versioning, registries, status files, and Decision Records. Resolve contradictory status, version, authority, amendment, and publication claims through one clean current model.
3. Review each existing KIP and KIS document set for internal completeness, correct lifecycle state, provenance to its originating decision, and an explicit normative-versus-informative boundary. Do not expand KBEP or KBIP here; keep their assessment plans independent.
4. Review schemas, templates, examples, and tooling guidance against the specifications they claim to represent. Remove or correct unsupported conformance claims, stale anticipated behaviour, invalid fixtures, and duplicated authority; retain concrete validation evidence.
5. Remove the retired `.ki-meta/` executor and vendored-checker footprint, align repository and authoring configuration with the current direct-CLI model, and correct the repository-owned audit findings. Treat the GitHub description as repository metadata, not specification prose.
6. Decide whether any stable repository-shape rule belongs in the shared `ki-specifications` skill. Keep repository-specific detail local; route only a genuinely reusable contract change to the harness through a focused recipient item.
7. Align entry-point and contributor documentation with the reviewed end state, run the complete verification set, and record any deliberately deferred normative question as a separate roadmap item rather than leaving an ambiguous TODO.

## Files touched

- Repository authority and contribution documents at the root and under `docs/`
- `proposals/`, `specifications/`, `schemas/`, `templates/`, `examples/`, and `tooling/`
- `.ki-config.toml`, authoring configuration, and the retired `.ki-meta/` tree
- Repository roadmap files and any focused outbound recipient brief justified by the review

## Verify

1. `ki repo audit --repo .`
2. `ki repo audit --repo . --skill ki-roadmap`
3. `ki repo audit --repo . --skill ki-decision-records`
4. `bun x prettier --check '**/*.{md,json,jsonc,yaml,yml}'`
5. `bun x markdownlint-cli2`
6. Validate every tracked example manifest against `schemas/knowledge-package.schema.json` with the documented AJV command.
7. Confirm no tracked `.ki-meta/` executor, vendored checker, retired capability name, or duplicate KIP/KIS registry claim remains.

## Dependencies / blocks

This review is independent of the open KBEP and KBIP assessments. Those plans preserve transferred ideas but must not define or expand the repository model while this review is active.

The review may cite implementation evidence from other repositories, but it does not directly edit them. A reusable shared-standard change requires a separately accepted recipient item in the harness.

## Delegation

- Round 1 — research: inventory authority, lifecycle claims, corpus status, and cross-repository boundaries; read-only; gate: evidence matrix with exact source locations.
- Round 1 — mechanical: inventory tracked legacy/runtime footprint, configuration drift, links, schemas, templates, examples, and current audit findings; read-only; gate: reproducible command output.
- Round 2 — judgment: reconcile the one intended KIP/KIS and repository model from Round 1 evidence; gate: maintainer review before normative or governance edits.
- Round 3 — implementation: apply the accepted clean end state in exclusive file groups; gate each group independently before commit.
