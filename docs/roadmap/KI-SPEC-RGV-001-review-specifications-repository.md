---
id: KI-SPEC-RGV-001
area: RGV
title: Review KI Specifications
kind: deliver
purpose: corrective
project: specifications
component: repository-governance
horizon: hold
hold:
  reason: parked
  condition: Kris restarts the ki-specifications live specification effort
status: draft
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-07-27T15:28:48Z
updated_at: 2026-10-07T14:10:13Z
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
- No KBEP or KBIP content; KI-SPEC-KIN-001 and KI-SPEC-KIN-002 own those assessments.
- `docs/adoption-guide.md` and `tooling/README.md` stay where they are; they gain cross-links, not a move into `docs/guides/`.

## Current state

Refreshed at `49403d3` (2026-10-05). The repository is in its declared dormant pre-v1 posture: `proposals/` and `specifications/` hold only empty registry READMEs, so there is no existing KIP or KIS document set to review; no tracked `.ki-meta/` file remains; root `.gitignore` is marker-bounded; and `ki repo audit --repo .` passes across 19 skills, including `ki-guides`, which KI-SPEC-RGV-003 added with a contributor and implementer guide collection under `docs/guides/`. `rumdl check .`, `rumdl fmt --check .`, and `rumdl check --enable MD057 .` (relative links) are clean across 54 files.

Known disagreements across the retained process material, verified at `49403d3`:

- `Implemented` marker. `GOVERNANCE.md:26` and `docs/specification-process.md:34` mark a KIP `Implemented` when its KIS is promoted to `Active`; `docs/specification-process.md:17`, `CONTRIBUTING.md:39`, and the `README.md` KIP/KIS model paragraph mark it on KIS publication at `Draft`. `docs/specification-process.md` therefore contradicts itself.
- KIP file set. `CONTRIBUTING.md` requires a fixed five-file KIP set (`README.md`, `proposal.md`, `rationale.md`, `alternatives.md`, `status.md`); `proposals/README.md:7` requires a minimum of three.
- KIS file set. `docs/specification-process.md:32` says the KIS file set is described in `specifications/README.md`, which describes none; neither did the pre-reset README at `1a140df^`. The two pre-reset KIS sets both carried `README.md`, `specification.md`, `conformance.md`, and `manifest.md`, plus topic files.
- Guide-shaped documents. `docs/adoption-guide.md` and `tooling/README.md` sit outside `docs/guides/` with no link to it.
- Illustrative material. No KIS adopts `schemas/`, `templates/`, or `examples/`. The schema `description` already says "informative pending an accepted proposal" and `templates/README.md` says no KIS defines the levels normatively, but `examples/README.md`, `tooling/README.md`, and `docs/adoption-guide.md` carry no such statement, and `docs/adoption-guide.md:29` speaks of itself as a specification ("Nothing in this specification assumes ...").
- Validation command. All seven tracked manifests (`examples/*/manifest.json`, `schemas/examples/*.json`, `templates/*/manifest.json`) validate, but only with `npx -y -p ajv-cli -p ajv-formats ajv validate ...`. The documented `bun x ajv-cli validate ... -c ajv-formats` and `npx ajv-cli validate ... -c ajv-formats` forms both fail with "Cannot find module 'ajv-formats'". The failing form appears in `CLAUDE.md:25`, `tooling/README.md:10` and `:16`, `docs/guides/implementer/implementing-an-accepted-kis.md:33`, `templates/README.md:26`, and `templates/{minimal,standard,extended}/README.md:13`.

## Steps

- [ ] Build the authority inventory: classify every tracked file outside `docs/roadmap/` as normative, informative, illustrative, generated, historical, or operational, and record it as a table under `### Authority inventory` in this record's Discussion. Confirm `docs/` as the location for informative notes and widen the `docs/` row of the `README.md` repository map to name informative assessment notes. Compare the stated ecosystem responsibility with the harness, `tools-ki`, Website, and Arcadia boundaries without importing their implementation detail.
- [ ] Reconcile the `Implemented` marker to KIS promotion to `Active`: conform `docs/specification-process.md:17`, `CONTRIBUTING.md:39`, and the `README.md` KIP/KIS model paragraph to `GOVERNANCE.md:26` and `docs/specification-process.md:34`.
- [ ] Conform `proposals/README.md` to the fixed five-file KIP set in `CONTRIBUTING.md`, citing `CONTRIBUTING.md` as the authority rather than restating a divergent rule.
- [ ] Add the KIS file set that `docs/specification-process.md:32` already claims `specifications/README.md` describes: `README.md` with the status block the implementer guide relies on, `specification.md`, and `conformance.md`, with further topic files permitted. Describe it as future process, consistent with the dormant posture.
- [ ] Mark `schemas/`, `templates/`, `examples/`, and `docs/adoption-guide.md` explicitly "illustrative, not adopted by any KIS": add the statement to `examples/README.md`, `tooling/README.md`, and `docs/adoption-guide.md`; align the wording in `templates/README.md` and the schema `description`; and replace the "this specification" self-reference in `docs/adoption-guide.md`.
- [ ] Replace the failing manifest validation command in all eight occurrences listed under Current state with one form verified to work (currently `npx -y -p ajv-cli -p ajv-formats ajv validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d <manifest>`, or a Bun equivalent proven by running it).
- [ ] Add a cross-link from `docs/adoption-guide.md` and `tooling/README.md` to `docs/guides/README.md`, leaving both files in place.
- [ ] Decide whether any stable repository-shape rule belongs in the shared `ki-repo-specifications` skill (harness `skills/repo-structure/ki-repo-specifications`). Keep repository-specific detail local, record the outcome in Discussion, and route only a genuinely reusable contract change to the harness through a focused recipient item.
- [ ] Align entry-point and contributor documentation with the reviewed end state, run the complete Verify set, and record any deliberately deferred normative question as a separate roadmap item rather than an ambiguous TODO.

## Files touched

- `README.md`, `CONTRIBUTING.md`, `CLAUDE.md`, `docs/specification-process.md`, `docs/adoption-guide.md`
- `proposals/README.md`, `specifications/README.md`
- `schemas/knowledge-package.schema.json` (`description` string only)
- `templates/README.md`, `templates/{minimal,standard,extended}/README.md`, `examples/README.md`, `tooling/README.md`
- `docs/guides/implementer/implementing-an-accepted-kis.md` (validation command only)
- `docs/roadmap/KI-SPEC-RGV-001-review-specifications-repository.md`, plus any focused follow-up roadmap item the review justifies

`GOVERNANCE.md`, `docs/numbering.md`, and `docs/versioning.md` are read as authorities and are not expected to change.

## Verify

1. `ki repo audit --repo . --progress never` passes (the CI gate, `.github/workflows/ci.yml:59`).
2. `ki repo audit --repo . --skill ki-work-roadmap` and `ki repo audit --repo . --skill ki-repo-specifications` pass.
3. `rumdl check .` and `rumdl fmt --check .` report no issues.
4. `rumdl check --enable MD057 .` reports no issues, so every relative link resolves (MD057 is disabled in `.rumdl.toml` and enabled here for this check only).
5. `for m in examples/*/manifest.json schemas/examples/*.json templates/*/manifest.json; do npx -y -p ajv-cli -p ajv-formats ajv validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d "$m" || exit 1; done` reports all seven valid, and the documented command, run exactly as written, validates `examples/minimal-package/manifest.json`.
6. `grep -rn "bun x ajv-cli\|npx ajv-cli" --exclude-dir=.git --exclude-dir=roadmap .` returns nothing.
7. `grep -n "Implemented" README.md CONTRIBUTING.md GOVERNANCE.md docs/specification-process.md` shows every lifecycle claim tying `Implemented` to KIS promotion to `Active`.
8. `grep -n "at minimum" proposals/README.md` returns nothing, and `specifications/README.md` names the KIS file set.
9. `grep -n "this specification" docs/adoption-guide.md` returns nothing; `examples/README.md`, `tooling/README.md`, and `docs/adoption-guide.md` each contain the illustrative statement.
10. `git ls-files proposals specifications` lists only the two registry READMEs, and `git ls-files | grep -c '\.ki-meta/'` prints `0`.

## Dependencies / blocks

Parked. Return trigger: Kris restarts ki-specifications as a live specification effort. The earlier waiting-for condition and return trigger under Discussion are superseded until then.

This review has no prerequisite and blocks nothing. KI-SPEC-KIN-001 and KI-SPEC-KIN-002 prefer to run after it so their informative notes land in the location its authority inventory confirms; that is a sequencing preference, not build order, so `blocks` stays empty.

The review may cite implementation evidence from other repositories, but it does not edit them. A reusable shared-standard change requires a separately accepted recipient item in the harness.

## Delegation

- Round 1 - research and mechanical: build the authority inventory and re-confirm the Current state disagreements with exact source locations; read-only; gate: inventory table and reproducible command output.
- Round 2 - implementation: apply the reconciliation, illustrative marking, validation command, and cross-link Steps in exclusive file groups (process documents; registries; illustrative material and tooling; guide command); gate: each group passes Verify 3 and 4.
- Round 3 - orchestrator: run the complete Verify set, record the shared-skill outcome, and prepare the record for review.

## Documentation impact

### Decision Records

None. The reconciliation conforms documents to their existing named authorities, and the choices made are reversible editorial calls recorded under Discussion rather than structural or adoption decisions.

### Specifications

No KIS exists, so no behaviour-level contract changes. The retained future-process documents (`docs/specification-process.md`, `CONTRIBUTING.md`, `proposals/README.md`, `specifications/README.md`) are edited only to agree with one another.

### Guides

`docs/guides/implementer/implementing-an-accepted-kis.md` receives the working validation command; no other guide text changes, because the guides already defer to the authority documents and agree with the reconciled model. `docs/adoption-guide.md` and `tooling/README.md` gain cross-links to `docs/guides/README.md`.

### Roadmap

KI-SPEC-KIN-001 and KI-SPEC-KIN-002 read the confirmed informative-note location before writing. Any deferred normative question becomes a separate `RGV` item, and any reusable shared-skill change becomes a harness recipient item through the `ki-trades` route.

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
