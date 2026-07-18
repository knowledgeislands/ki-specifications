# KIS-0001 — Conformance

Status: Draft Version: 1.0.0

A Knowledge Package declares its intended depth of conformance through the `conformanceLevel` field, whose value is `minimal`, `standard`, or `extended`. A package that omits the field is validated at the **Minimal** level.

Conformance is the conjunction of two checks:

1. **Schema-valid** — the manifest validates against the [JSON Schema](../../schemas/knowledge-package.schema.json) for its `specVersion`; and
2. **Level checklist** — the manifest satisfies every item in the checklist for its declared level.

Each higher level includes every requirement of the levels below it.

## Minimal

- [ ] The manifest is schema-valid.
- [ ] `specVersion`, `id`, `uuid`, `name`, `version`, `lifecycle`, `classification`, and `created` are present and well-formed.
- [ ] At least one `owner` is declared.
- [ ] An `executive` digest is present (inline `summary` or `path`).
- [ ] The `@<semver>` segment of `id` equals `version`.

## Standard

Everything in Minimal, plus:

- [ ] `description` is present.
- [ ] `provenance` is present with a `createdBy` party.
- [ ] `history` contains at least a `created` event.
- [ ] `governance` is present and names a `steward`.
- [ ] Every artefact path referenced by the manifest resolves within the package.
- [ ] If the package represents work, `tasks` and/or `deliverables` are present.

## Extended

Everything in Standard, plus:

- [ ] A `technical` digest is present in addition to the `executive` digest.
- [ ] `decisions` are recorded for the material choices the package embodies.
- [ ] `provenance.sources` identifies the inputs the package was derived from.
- [ ] `history` is maintained append-only across the package's life.
- [ ] Relationships to predecessor, successor, or parent packages are recorded in `related` where they exist.
- [ ] `handover` material is present whenever the package is intended to be resumed by another party.

## Declaring and checking a level

A validator MUST determine the effective level from `conformanceLevel` (defaulting to Minimal), run the schema check, then run the checklist for that level. A validator MUST report the level checked and each failed item. A package MUST NOT declare a level whose checklist it does not satisfy.
