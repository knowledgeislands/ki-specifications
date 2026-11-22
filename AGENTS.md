# AGENTS.md - KI Specifications

This is the runtime-neutral working convention for KI Specifications. The README is the entry point for the repository's normative scope, KIP/KIS model, and contribution workflow.

## Orientation

- `proposals/` — KIPs, one directory per proposal (`KIP-000001-<slug>/`); registry in `proposals/README.md`.
- `specifications/` — KIS documents, one directory per specification (`KIS-0001-<slug>/`); registry in `specifications/README.md`.
- `schemas/` — machine-readable JSON Schemas (Draft 2020-12) plus valid example manifests under `schemas/examples/`.
- `templates/`, `examples/` — conformant Knowledge Package starting points and reference packages.
- `docs/` — process, numbering, versioning, adoption, architecture context.

## Working rules

- The repository keeps seven top-level areas: `proposals/`, `specifications/`, `schemas/`, `templates/`, `examples/`, `docs/` and `tooling/`. Their internal contents evolve; the areas themselves stay (REPO-OTHERS a, 22 November 2026, when `ki-repo-specifications` retired into the general Project shape).
- Normative and informative text are kept explicitly separate; RFC 2119/8174 keywords (capitalised) appear only in normative text, and never in KIPs.
- Relative links only. British English (artefact, organisation). Markdown otherwise follows `ki-authoring`.
- Numbers are assigned once and never reused: `KIP-NNNNNN` (6 digits), `KIS-NNNN` (4 digits), independent series — see [docs/numbering.md](docs/numbering.md).
- Any change to accepted normative content goes through a KIP; editorial fixes are patch-version errata — see [docs/versioning.md](docs/versioning.md).
- Keep the repository generic and organisation-neutral; domain modules appear only as illustrative examples in informative text.

## Validation

- Manifests against the schema: `bun x ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d <manifest>` (fallback: a small ajv script — see [tooling/README.md](tooling/README.md)).
- Repo self-audit: `ki repo audit --repo .`.
- Every JSON file must parse; every relative Markdown link must resolve; all example and template manifests must validate.

## Commits

Commits follow `ki-git`. If a unit cannot yet be verified, report the checkpoint and leave it uncommitted until its verification is complete.

## Cross-repository choreography

- Knowledge Islands Principal, the KI Agent Backpack, `tools-ki`, KI Specifications, the KI Website, the Techne Harness, and `tools-techne` hand work and rollouts to one another as a line in the receiving work's `messages.md`, or State of play's where no work owns it, never as a record in one another's Stream, roadmap, or triage, as Kris set under HANDOFF-AS-MESSAGE on 2026-10-20: "Handoffs are not roadmap items ... A rollout that needs people to make those changes sooner rather than later must go as a message". The receiving repository owns its priority, plan, and execution, and only it captures a record, for work genuinely deferred that it owns.
- State the need, and link only what may be linked, as `ki-work-roadmap` sets for work another repository must deliver.
- Prefer independently executable, non-blocking work. Mark an item as blocking only when it is a genuine prerequisite; otherwise let the receiving repository schedule it in its own horizon.

## Specification posture

- This repository is dormant while Knowledge Islands remains at v0.x; it owns no active ecosystem-wide specifications before the overall v1 boundary is reviewed.
- Keep repository-level specifications in their owning repositories.
- Treat the KIP/KIS material here as the future process, not authority to begin an ecosystem-wide specification programme.
