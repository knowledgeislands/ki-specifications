# KIS-0001 — Manifest Reference

Status: Draft Version: 1.0.0

This document is a field-by-field reference for the Knowledge Package manifest. It mirrors the [JSON Schema](../../schemas/knowledge-package.schema.json), which is the normative machine-readable form. Where this prose and the schema differ on the _shape_ of a field, the schema governs.

`manifest.json` is the normative serialization. A YAML serialization is a permitted equivalent: it MUST represent the same data model and MUST round-trip to and from the JSON form without loss.

## Root fields

| Field              | Type                   | Required | Notes                                                                       |
| ------------------ | ---------------------- | -------- | --------------------------------------------------------------------------- |
| `specVersion`      | semver string          | Yes      | Version of KIS-0001 the package conforms to.                                |
| `id`               | string                 | Yes      | `ki:pkg:<namespace>/<slug>@<semver>`; the `@<semver>` MUST equal `version`. |
| `uuid`             | UUID v4                | Yes      | Stable across all versions of the package.                                  |
| `name`             | string                 | Yes      | Human-readable name.                                                        |
| `version`          | semver string          | Yes      | Package version.                                                            |
| `lifecycle`        | enum                   | Yes      | See [lifecycle.md](lifecycle.md).                                           |
| `classification`   | enum                   | Yes      | See [security-and-classification.md](security-and-classification.md).       |
| `created`          | date-time              | Yes      | ISO 8601, UTC.                                                              |
| `owners`           | array of Party         | Yes      | At least one.                                                               |
| `digests`          | object                 | Yes      | MUST contain `executive`; MAY contain `technical`.                          |
| `description`      | string                 | No       | Longer prose description.                                                   |
| `updated`          | date-time              | No       | ISO 8601, UTC.                                                              |
| `conformanceLevel` | enum                   | No       | `minimal`, `standard`, or `extended`.                                       |
| `tags`             | array of string        | No       | Free-form labels.                                                           |
| `decisions`        | array of Decision      | No       | Recorded choices.                                                           |
| `assumptions`      | array of string        | No       | Stated assumptions.                                                         |
| `constraints`      | array of string        | No       | Stated constraints.                                                         |
| `terminology`      | array of Term          | No       | Local definitions.                                                          |
| `openQuestions`    | array of string        | No       | Unresolved questions.                                                       |
| `tasks`            | array of Task          | No       | Work items.                                                                 |
| `deliverables`     | array of Deliverable   | No       | Expected outputs.                                                           |
| `references`       | array of Reference     | No       | External or internal references.                                            |
| `provenance`       | Provenance             | No       | See [provenance.md](provenance.md).                                         |
| `governance`       | Governance             | No       | See [governance.md](governance.md).                                         |
| `handover`         | Handover               | No       | Resumption material.                                                        |
| `history`          | array of HistoryEvent  | No       | Append-only event log.                                                      |
| `related`          | array of Related       | No       | Relationships to other packages or resources.                               |
| `artefacts`        | object (string → path) | No       | Map of artefact-kind to relative path.                                      |
| `extensions`       | object                 | No       | Namespaced extension data; see [extension-model.md](extension-model.md).    |

The root object sets `additionalProperties: false`: a member not listed above (and outside `extensions`) is invalid.

## Defined objects

### Party

`{ name, type, role?, contact? }` — `type` is one of `human`, `agent`, `organisation`. Used by `owners`, `governance.steward`, `governance.reviewers`, `provenance.createdBy`, `history[*].actor`, and `tasks[*].assignee`.

```json
{ "name": "A. Rivera", "type": "human", "role": "lead-architect" }
```

### Digest

`{ summary? , path? }` — at least one of `summary` (inline text) or `path` (a relative path to a Markdown artefact) MUST be present.

```json
{ "executive": { "summary": "One-paragraph summary for a non-specialist." } }
```

### Task

`{ id, title, status, description?, assignee?, dependsOn?[], deliverables?[] }` — `status` is one of `todo`, `in_progress`, `blocked`, `done`, `cancelled`.

```json
{ "id": "T-1", "title": "Draft the interface", "status": "in_progress", "dependsOn": [] }
```

### Deliverable

`{ id, title, description?, path?, status? }`.

```json
{ "id": "D-1", "title": "Interface specification", "path": "deliverables/interface.md" }
```

### Decision

`{ id, title, status?, date?, rationale?, supersedes? }` — `status` is one of `proposed`, `accepted`, `superseded`.

```json
{ "id": "DEC-001", "title": "Models are engines, not stores", "status": "accepted" }
```

### Reference

`{ title?, uri?, path?, note? }` — at least one member MUST be present. Used both by `references` and by `provenance.sources`.

```json
{ "title": "KIP-000001", "path": "../../proposals/KIP-000001-knowledge-packages/proposal.md" }
```

### Provenance

`{ createdBy (Party), sources?[] (Reference), method? }`.

```json
{ "createdBy": { "name": "KI Core", "type": "organisation" }, "method": "Synthesised from workshop notes." }
```

### HistoryEvent

`{ timestamp, actor (Party), action, note? }`.

```json
{ "timestamp": "2026-01-15T10:00:00Z", "actor": { "name": "KI Core", "type": "organisation" }, "action": "created" }
```

### Handover

`{ instructions?, path?, context?, resumePoints?[] }` — at least one member MUST be present.

```json
{ "instructions": "Resume with T-2.", "resumePoints": ["Finish the design note."] }
```

### Governance

`{ steward? (Party), reviewers?[] (Party), promotionPolicy?, retention? }`.

```json
{ "steward": { "name": "K. Osei", "type": "human", "role": "steward" } }
```

### Related

`{ relationship, id? , uri?, note? }` — `relationship` is one of `supersedes`, `supersededBy`, `dependsOn`, `derivedFrom`, `relatesTo`, `partOf`, `promotedTo`; at least one of `id` or `uri` MUST be present.

```json
{ "id": "ki:pkg:acme/foo@1.0.0", "relationship": "supersededBy" }
```

Each defined object also sets `additionalProperties: false`, except `extensions`, which is deliberately open.
