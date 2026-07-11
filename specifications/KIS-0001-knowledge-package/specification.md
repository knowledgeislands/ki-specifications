# KIS-0001 — Knowledge Package Specification

Status: Draft
Version: 1.0.0
Date: 2026-07-11
Implements: [KIP-000001 — Knowledge Packages](../../proposals/KIP-000001-knowledge-packages/)

## 1. Scope

This specification defines the Knowledge Package: its identity, its manifest, its artefacts, and the rules that govern its lifecycle, provenance, governance, promotion, classification, and extension.
It defines what a conforming package MUST contain and how a validator determines conformance.
It does not define a transport, a storage format beyond the manifest, an MCP interface, or any dependency on a particular large-language-model provider.

The key words MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, and OPTIONAL are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174) when, and only when, they appear in capitals.
Terms are defined in [terminology.md](terminology.md).

## 2. Package identity

A Knowledge Package has two identifiers.

The `uuid` is a UUID version 4 that identifies the package across all of its versions.
It MUST remain stable for the life of the package and MUST NOT be reused for any other package.

The `id` is a human-readable identifier of the form `ki:pkg:<namespace>/<slug>@<semver>`.
The `namespace` SHOULD identify the owning organisation or domain; the `slug` names the package; the `@<semver>` segment is the package version.
The `id` MUST match the pattern given in the [schema](../../schemas/knowledge-package.schema.json), and its `@<semver>` segment MUST equal the `version` field.

## 3. Versioning

Package versions follow [Semantic Versioning 2.0.0](https://semver.org).
Each published version of a package is immutable: once a version has been published, its manifest and artefacts MUST NOT be changed.
A new version of the package is a new `id` (with a new `@<semver>`) carrying the *same* `uuid`.

A change that alters the meaning or removes content of a package MUST increment at least the minor version; a change that breaks a consumer's reasonable expectations MUST increment the major version.
Editorial changes that do not change meaning MAY increment the patch version.

## 4. Required and optional content

A conforming manifest MUST provide the following core fields: `specVersion`, `id`, `uuid`, `name`, `version`, `lifecycle`, `classification`, `created`, `owners` (at least one), and `digests` (with at least an `executive` digest).
All other fields are OPTIONAL at the schema level; individual conformance levels require more, as set out in [conformance.md](conformance.md).

The `specVersion` field MUST state the version of KIS-0001 the package conforms to.
Consumers MUST reject a manifest whose `specVersion` they do not support.

Artefacts referenced by the manifest — via `digests[*].path`, `deliverables[*].path`, `references[*].path`, `handover.path`, `provenance.sources[*].path`, or the `artefacts` map — MUST be given as paths relative to the package root and SHOULD resolve to a file present in the package.

## 5. Tasks and deliverables

Work in progress is represented as `tasks`; expected outputs are represented as `deliverables`.
Each task has an `id`, a `title`, and a `status` drawn from `todo`, `in_progress`, `blocked`, `done`, or `cancelled`.
A task MAY declare `dependsOn` (task ids) and `deliverables` (deliverable ids); a referenced id SHOULD exist within the same manifest.
Each deliverable has an `id` and a `title` and MAY point to an artefact by `path`.

## 6. Decisions, constraints, and open questions

A package MAY record `decisions`, `constraints`, `assumptions`, `terminology`, and `openQuestions` to make its reasoning explicit and reusable.
A decision has a `status` of `proposed`, `accepted`, or `superseded`; a superseding decision SHOULD name the decision it `supersedes`.

## 7. Relationships

Relationships to other packages or resources are recorded in `related`.
Each entry names a `relationship` — one of `supersedes`, `supersededBy`, `dependsOn`, `derivedFrom`, `relatesTo`, `partOf`, or `promotedTo` — and identifies the other party by `id` or `uri`.
Relationships SHOULD be reciprocal where both parties are packages: a package that declares `supersedes` on another SHOULD be matched by a `supersededBy` on that other package.

## 8. Ownership and governance

A package MUST declare at least one `owner`.
Stewardship, review, promotion policy, and retention are recorded in `governance`; see [governance.md](governance.md).

## 9. Provenance

A package SHOULD record `provenance` describing who created it, from what `sources`, and by what `method`.
Provenance and history MUST survive handover and promotion unchanged; see [provenance.md](provenance.md).

## 10. Lifecycle, archival, and supersession

A package's `lifecycle` field records its current state; the states and transitions are defined in [lifecycle.md](lifecycle.md).
An `archived` package MUST NOT be modified except to record its supersession.
A package in the `superseded` state MUST carry a `related` entry with relationship `supersededBy` identifying its successor.

## 11. Validation requirements

A package is conforming if, and only if:

1. its manifest validates against the [JSON Schema](../../schemas/knowledge-package.schema.json) for its `specVersion`; and
2. it satisfies the checklist for its declared `conformanceLevel` (or the Minimal checklist if none is declared); and
3. every artefact path in the manifest resolves within the package.

A validator MUST report which of these checks failed.
A validator MUST NOT treat unknown members of the `extensions` object as errors; see [extension-model.md](extension-model.md).
