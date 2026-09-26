# ki-specifications

This is the pre-v1 holding repository for a future Knowledge Islands-wide specification programme. Repository-level specifications remain local to their owning repositories.

## Current posture

Knowledge Islands is at v0.x, so this repository owns no active ecosystem-wide specifications. Do not add KIPs, KIS documents, or wider normative contracts until the overall Knowledge Islands v1 boundary is ready for explicit review. The remaining material describes the intended future process and is not an active specification programme.

Knowledge Islands is an open-source operating system for governed human and AI knowledge work.

## Place in the Knowledge Islands ecosystem

After the overall v1 boundary is established, KI Specifications is intended to become the canonical source for normative portable contracts, including KIPs, KIS documents, schemas, templates, conformance rules, and reference examples. Until then, concepts remain with [Arcadia Principal](https://github.com/knowledgeislands/ki-arcadia-principal), engineering practice with [Techne Principal](https://github.com/knowledgeislands/ki-techne-principal), and implementation contracts with the repository that owns each implementation.

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

No KIPs or KIS documents are currently registered. The series start afresh at `KIP-000001` and `KIS-0001`; see [proposals/README.md](proposals/README.md) and [specifications/README.md](specifications/README.md) for the registries.

## How to propose a change

New concepts, specifications, changes and extensions start life as a KIP.

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to raise one, and [docs/specification-process.md](docs/specification-process.md) for the full lifecycle from proposal through to an accepted, versioned KIS.

## Licence

This repository is licensed under the [MIT licence](LICENSE), which applies equally to specification text and to schemas.

## Future specification areas

The following are anticipated areas for future KIPs and KIS documents, alongside the Knowledge Package itself:

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
