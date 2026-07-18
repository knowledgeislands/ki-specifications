# KIS-0001 — Security and Classification

Status: Draft Version: 1.0.0

Every Knowledge Package carries a `classification` that sets the minimum handling requirements for the package and its artefacts. The four levels, in increasing order of sensitivity, are `public`, `internal`, `confidential`, and `privileged`.

## Levels and handling

| Level | Meaning | Handling (normative) |
| --- | --- | --- |
| `public` | May be disclosed to anyone. | No restriction on distribution. |
| `internal` | For the owning organisation and its authorised parties. | MUST NOT be disclosed outside the organisation without owner authorisation. |
| `confidential` | Sensitive; restricted to named parties or roles. | Access MUST be limited to authorised parties; disclosure MUST be authorised per package. |
| `privileged` | Legal-privilege-sensitive; strictest handling. | Access MUST be limited to parties entitled to the privilege; handling MUST avoid any action that could waive privilege; disclosure requires explicit authorisation from the owner or steward. |

`privileged` is the strictest level and denotes content that is sensitive to legal privilege. A consumer that cannot enforce a package's handling requirements MUST NOT process the package.

## Inheritance to artefacts

The package `classification` applies to the manifest and to every artefact in the package. An artefact MUST NOT be treated as less sensitive than the package's classification. KIS-0001 does not define per-artefact classification; where finer-grained handling is required, a package SHOULD be split so that each package carries a single classification, or the requirement SHOULD be expressed through an extension (see [extension-model.md](extension-model.md)).

## Changing classification

Raising a package's classification is always permitted and SHOULD be recorded in `history`. Lowering a package's classification MUST be an explicit governance action, recorded in `history`, and MUST NOT occur as a side effect of promotion, handover, or any other action (see [governance.md](governance.md) and [promotion.md](promotion.md)).

## Redaction _(informative)_

Where a package must be shared at a lower classification than its content allows, the recommended pattern is to derive a _new_ package at the target classification containing only the disclosable material, and to link the two with a `related` relationship rather than editing the original. This preserves the original's provenance and history while giving the redacted view its own identity and audit trail. Redaction mechanics and tooling are out of scope for this specification.
