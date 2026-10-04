---
id: KI-SPEC-RGV-003
title: Establish audience-centric guides
area: RGV
theme: repository-governance
horizon: now
status: done
blocks: []
blocked_by: []
transferred_from: ki-website
baseline_ref: 580d475ab7028d68054f327bb9feda96c539f69a
created_at: 2026-09-21T17:20:00Z
updated_at: 2026-10-04T12:40:00Z
---

## Goal

Someone proposing a change to a specification, and someone implementing one, each find practical instructions for doing so in a guide collection grouped by audience.

## Context

`ki-specifications` has no `docs/guides/` and does not declare `ki-guides`. Its README carries How to propose a change, which is practical instruction for a real audience sitting in a reference document.

This repository is the normative standards and governance layer: it holds proposals, accepted specifications, JSON Schemas, governance rules, and templates. `docs/specs/` is rightly the point of the repository, and this item does not touch it. But a normative corpus has procedural readers as well as normative ones — someone raising a KIP, someone implementing an accepted KIS, someone deciding whether a change needs a proposal at all — and the how of those tasks is guide material, not specification material.

KI Website now declares, for every page it publishes under `apps/site/src/guidance/`, the exact upstream document and pinned ref that page was written from, and a `verify:guidance --network` sweep reports the pages whose source has moved. The site intends to derive public guidance for this project from this repository's own guides and cite them at a pinned ref, so the quality and stability of `docs/guides/` here directly determines the quality of what the site can publish.

That is a pull, not an obligation: KI Website derives, it does not own. This repository decides what its guides say and when they change.

Separately, `KI-HARNESS-GOV-083` has clarified `ki-guides`: audience directories are recommended when stable reader groups make a collection easier to navigate, while flat and mixed collections remain valid. This item therefore stands on this repository's own readers and routing needs, not a universal Harness requirement.

## Boundary

Adopted into `Now` by explicit approval, so this is prioritised work rather than intake. It remains `status: draft`: `ki-plan` shapes it to `Ready` before any implementation, and this repository still owns its plan and sequencing.

This item does not touch `docs/specs/`. The normative corpus is what this repository is for, and nothing here proposes restating a specification as a guide — the division is that a specification says what is true and a guide says how to do something.

KI Website derives and cites; it does not own this collection and must not be given approval rights over it.

### Planning decisions

Planning decisions taken against the repository at `5c0a85e`:

- **Audiences.** Two stable procedural readers, held to different reach under the `ki-guides` self-containment rule. A `contributor` changes the corpus (decides whether a change needs a proposal, raises and stewards a KIP); that reader works in this tree and may be told about governance artefacts by name. An `implementer` builds against what the corpus produces (a KIS, schema, template, or example); that reader has the published artefacts, not `docs/roadmap/` or `docs/decisions/`, so implementer guides stay bounded by those artefacts. Maintainer stewardship is covered by the contributor guides rather than a third directory, because a single maintainer currently performs it and the steps are the same KIP lifecycle seen from the other side.
- **Dormant posture.** The repository is dormant pre-v1 and accepts no new KIPs or KIS documents. Every guide states that posture first and tells the reader what to do today (route repository-level contracts to their owning repository; raise an issue to discuss an ecosystem-wide concern) before describing the future process it walks through. No guide invents a KIS, schema rule, or conformance claim.
- **Guide versus governance rule.** `GOVERNANCE.md`, `docs/specification-process.md`, `docs/numbering.md`, and `docs/versioning.md` remain the authoritative process sources. Guides walk the reader through the sequence and name those documents in prose (never link them, per the self-containment rule); they do not restate role authority, numbering invariants, or versioning semantics beyond what the reader needs to act.
- **Lifecycle guide.** No separate lifecycle guide. The raising-a-KIP guide carries a short at-a-glance lifecycle sufficient to act; the full informative lifecycle stays in `docs/specification-process.md`.
- **Existing guide-like documents.** `docs/adoption-guide.md` and `tooling/README.md` are left in place. Relocating them is part of the clean-end-state review in KI-SPEC-RGV-001 and is out of scope here.
- **Moving the README section.** README `## How to propose a change` becomes a short pointer to `docs/guides/`. CONTRIBUTING stays the authoritative home of the KIP file set and numbering request steps, because `GOVERNANCE.md` and `docs/specification-process.md` route to it; its `## Raising a KIP` section gains a pointer to the guide walk-through. The guide restates only what a reader needs to act (self-containment) and follows CONTRIBUTING's five-file set; the minimum-file discrepancy with `proposals/README.md` is left to KI-SPEC-RGV-001.

## Current state

At `5c0a85e`: no `docs/guides/`, no `[skills.ki-guides]` in `.ki.toml` (`ki repo audit --skill ki-guides` therefore refuses the selector). Procedural instruction sits in README `## How to propose a change` (two sentences of pointers) and CONTRIBUTING `## Raising a KIP`. The normative corpus is `proposals/` and `specifications/`, both empty registries; there is no `docs/specs/`. Full `ki repo audit --repo .` passes.

## Steps

- [x] Declare `[skills.ki-guides]` in `.ki.toml` through `ki repo skill add ki-guides --repo .`.
- [x] Create `docs/guides/README.md`: scope statement, dormant-posture note, and routing to the two audience indexes only.
- [x] Create `docs/guides/contributor/README.md` and `docs/guides/implementer/README.md`, each indexing its guides.
- [x] Write `docs/guides/contributor/deciding-whether-a-change-needs-a-kip.md`: today's dormant answer; then errata versus new KIS version versus superseding KIS versus new KIP, naming `GOVERNANCE.md` as authority.
- [x] Write `docs/guides/contributor/raising-a-kip.md`: preconditions, directory and file set, placeholder number and maintainer assignment, review and revision, outcome, at-a-glance lifecycle, verification and recovery; following the CONTRIBUTING file set and numbering steps without replacing them.
- [x] Write `docs/guides/implementer/implementing-an-accepted-kis.md`: confirm KIS status and version, read normative sections only, validate a Knowledge Package manifest against `schemas/knowledge-package.schema.json` with the documented AJV command (the schema, not a KIS, is what the command checks), report implementation experience or suspected errata, and what Draft versus Active means for the implementer.
- [x] Replace README `## How to propose a change` with a pointer to the guide collection, and add a pointer from CONTRIBUTING `## Raising a KIP` to the guide walk-through, leaving its file set and numbering steps in place.
- [x] Run the verification set and repair what it reports.

## Files touched

- `.ki.toml`
- `docs/guides/README.md`, `docs/guides/contributor/` (README and two guides), `docs/guides/implementer/` (README and one guide) — all new
- `README.md`, `CONTRIBUTING.md`
- This roadmap record

## Verify

1. `ki repo audit --skill ki-guides --repo .` passes.
2. `ki repo audit --skill ki-authoring --repo .` passes.
3. `ki repo audit --repo .` passes in full.
4. `rumdl check docs/guides README.md CONTRIBUTING.md` reports no issues.
5. Self-containment: every relative `](...)` target in `docs/guides/**/*.md` resolves with `test -e` and lies inside `docs/guides/`; every relative link in `README.md` and `CONTRIBUTING.md` resolves.
6. Every guide file under `docs/guides/` contains the sentinel phrase `pre-v1`, and `grep -rEn '\b(MUST|SHOULD|MAY|SHALL)\b' docs/guides` returns nothing.

## Dependencies / blocks

Originates from KI Website (`transferred_from: ki-website`); the Website derives and cites this collection but neither blocks nor is blocked by this item. Independent of KI-SPEC-RGV-001, which may later relocate `docs/adoption-guide.md` and `tooling/README.md` into this collection; KI-SPEC-KIN-001 and KI-SPEC-KIN-002 are unaffected.

## Documentation impact

### Decision Records

None; the audience split is local information architecture under `ki-guides`.

### Specifications

None; no KIS or schema changes.

### Guides

Establishes `docs/guides/` with contributor and implementer collections.

### Roadmap

None beyond this record.

## Delegation

Single lane; no delegation needed.

## Review

### Delivered

The approved boundary: a `docs/guides/` collection grouped by two audiences (contributor, implementer), `[skills.ki-guides]` declared, README and CONTRIBUTING routing to the collection. Excluded as planned: `docs/adoption-guide.md` and `tooling/README.md` relocation, any KIP/KIS/schema change. Baseline `580d475ab7028d68054f327bb9feda96c539f69a`; delivered in the commit that sets this record to `awaiting-review`.

### Change Summary

- `.ki.toml` - `[skills.ki-guides]` added (via `ki repo skill add ki-guides`, relocated to the Governance and runtime block).
- `docs/guides/README.md` - collection entry point: scope, pre-v1 posture, audience routing.
- `docs/guides/contributor/README.md`, `deciding-whether-a-change-needs-a-kip.md`, `raising-a-kip.md` - today's dormant route first, then the four change routes and the KIP walk-through; authorities named in prose, not linked.
- `docs/guides/implementer/README.md`, `implementing-an-accepted-kis.md` - status and version meaning, normative-only reading, schema validation (explicitly not KIS validation), and feedback routes; bounded to published artefacts.
- `README.md` - `## How to propose a change` now routes to the guides; `CONTRIBUTING.md` - pointer to the guides while remaining the file-set and numbering authority.

### Verification

1. `ki repo audit --skill ki-guides --repo .` - PASS.
2. `ki repo audit --skill ki-authoring --repo .` - PASS.
3. `ki repo audit --repo .` - PASS, 19 skills.
4. `rumdl check docs/guides README.md CONTRIBUTING.md` - no issues in 8 files.
5. Relative-link scan: every `docs/guides` target resolves inside `docs/guides/`; every README and CONTRIBUTING relative link resolves.
6. Every guide file contains `pre-v1`; the capitalised-keyword grep over `docs/guides` returns nothing.

### Outstanding concerns

- Source process documents disagree on when a KIP becomes `Implemented`: `docs/specification-process.md` and `CONTRIBUTING.md` say on KIS publication at `Draft`, `GOVERNANCE.md` says on KIS promotion to `Active`. The guide follows the former and defers to the named authorities; reconciliation belongs to KI-SPEC-RGV-001, alongside the three-versus-five file-set discrepancy in `proposals/README.md`.

### Post-change review

The goal is met for both named audiences without touching the normative corpus. Scope held to the planned files. Regression risk is low: additive documentation plus two pointer edits, all audits green. Ready for independent acceptance review.

### Mini recap

Established an audience-grouped guide collection that a pinned KI Website citation can derive from. Learning route: the process-document contradictions above feed KI-SPEC-RGV-001; no promotion is proposed.

## Done

Accepted 2026-10-04 against the six-part Review packet at delivery commit `234c846`. An independent reviewer re-ran every Verify gate (full, `ki-guides`, and `ki-authoring` audits PASS; `rumdl` clean; self-containment, sentinel, and keyword scans clean), confirmed factual consistency with the process documents, and returned ACCEPT; closure is recorded under the owner's delegated roadmap authority of that date. Non-blocking editorial notes for a later pass: the implementer guide's "change notes" names an artefact no KIS file set defines, and the deciding guide's promise that a maintainer "will record" an issue for the v1 review describes no defined mechanism; both fit the KI-SPEC-RGV-001 reconciliation.

## Discussion

### Readiness - 2026-10-04

Shaped under the owner's delegated roadmap authority of 2026-10-04 and checked by an independent reviewer, whose amendments (CONTRIBUTING remains the authoritative file-set home; the implementer guide validates against the schema, not a KIS; mechanical self-containment and posture checks) are applied above. Marked `ready` on that basis.
