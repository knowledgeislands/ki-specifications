# ki-specifications

This repository is the normative standards and governance layer for the Knowledge Islands ecosystem.

It holds the proposals, accepted specifications, JSON Schemas, governance rules, templates and reference examples that define how Knowledge Packages, and the wider Knowledge Islands architecture, are built and evolved.

Knowledge Islands is an open-source operating system for governed human and AI knowledge work.

## Place in the Knowledge Islands ecosystem

KI Specifications is the canonical source of normative portable contracts, including KIPs, KIS documents, schemas, templates, conformance rules, and reference examples. It formalises concepts established in [Arcadia Principal](https://github.com/knowledgeislands/ki-arcadia-principal) and implementation evidence from the [KI Agentic Harness](https://github.com/knowledgeislands/ki-agentic-harness); an Active KIS governs implementations that claim conformance within its scope.

The [KI Website](https://github.com/knowledgeislands/ki-website) may vendor source-labelled specification material for autonomous public publication, while this repository remains canonical for the normative contracts. The mirrored [ecosystem decision](docs/decisions/GDR-KI-ARCADIA-002-knowledge-islands-ecosystem-fundamentals.md) defines the four authorities and publication flows.

## The KIP/KIS model

A **KIP** (Knowledge Islands Proposal) is a reviewable proposal for a new foundational concept, specification, change or extension.

KIPs are numbered `KIP-NNNNNN` (six digits) and move through a lifecycle of `Draft → Review → Accepted | Rejected | Withdrawn`, then `Implemented` once a corresponding specification is published, and eventually `Superseded`.

Anyone may draft a KIP; maintainers assign the number and steward it through review.

A **KIS** (Knowledge Islands Specification) is the normative document produced once a KIP is accepted.

KIS documents are numbered `KIS-NNNN` (four digits) independently of the KIP series, and move through `Draft → Active → Deprecated → Superseded`, starting Draft and becoming Active once there is real implementation experience against it.

Together the two series separate the deliberative process (KIP: should we do this, and how) from the durable normative outcome (KIS: this is how it works today), so specifications can change carefully while proposals can be debated freely.

## Repository map

| Directory         | Purpose                                                                                  |
| ----------------- | ---------------------------------------------------------------------------------------- |
| `proposals/`      | KIP proposals: the deliberative record of what was proposed, why, and how it was decided |
| `specifications/` | KIS documents: the accepted, normative specifications of the ecosystem                   |
| `schemas/`        | JSON Schemas that machines validate Knowledge Packages and other artefacts against       |
| `templates/`      | Starter file sets for creating new Knowledge Packages at each conformance level          |
| `examples/`       | Worked, valid reference packages illustrating the schema and conventions                 |
| `docs/`           | Process, versioning, adoption and architectural context documentation                    |
| `tooling/`        | Guidance on validating packages today, and on tooling anticipated in future              |

## Current documents

| Number                                                          | Title              | Status   |
| --------------------------------------------------------------- | ------------------ | -------- |
| [KIP-000001](proposals/KIP-000001-knowledge-packages/README.md) | Knowledge Packages | Accepted |
| [KIS-0001](specifications/KIS-0001-knowledge-package/README.md) | Knowledge Package  | Draft    |

## How to propose a change

New concepts, specifications, changes and extensions start life as a KIP.

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to raise one, and [docs/specification-process.md](docs/specification-process.md) for the full lifecycle from proposal through to an accepted, versioned KIS.

## Licence

This repository is licensed under the [MIT licence](LICENSE), which applies equally to specification text and to schemas.

## Future specification areas

The following are anticipated areas for future KIPs and KIS documents, beyond the Knowledge Package covered by KIS-0001:

- KI kernel
- Kernel modules
- Planner and orchestration
- Workspaces
- Knowledge promotion
- Skills
- Tools and MCP adapters
- Evaluation
- Identity
- Provenance
- Storage and persistence providers
