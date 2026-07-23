# Knowledge Islands Proposals (KIPs)

This directory holds the Knowledge Islands Proposals — the persuasive, architectural documents through which new foundational concepts, specifications, changes and extensions to Knowledge Islands are argued and reviewed.

A Knowledge Islands Proposal (KIP) makes the case for a change. It sets out a problem, argues a direction, weighs the alternatives, and asks for a decision. A KIP is informative and architectural rather than normative: it explains _why_ something should exist and _what shape_ it should take. When a KIP is accepted, the normative detail — the fields, rules and conformance criteria an implementation must satisfy — is written up as a Knowledge Islands Specification (KIS) under [`../specifications/`](../specifications/). Proposals persuade; specifications bind.

Each KIP lives in its own directory named `KIP-NNNNNN-<slug>` (six-digit number, never reused) and carries, at minimum, a `README.md` index, a `proposal.md`, and a `status.md`. Most also carry a `rationale.md` and an `alternatives.md`. KIP numbers and KIS numbers are assigned independently.

For how a proposal is raised, reviewed and progressed through its statuses, see the specification process at [`../docs/specification-process.md`](../docs/specification-process.md) and the project governance at [`../GOVERNANCE.md`](../GOVERNANCE.md).

## Statuses

A KIP moves through `Draft → Review → Accepted | Rejected | Withdrawn`. An `Accepted` proposal becomes `Implemented` once its specification is published, and may later become `Superseded` by a subsequent proposal.

## Registry

| Number | Title | Status | Created | Resolution |
| --- | --- | --- | --- | --- |
| [KIP-000001](KIP-000001-knowledge-packages/) | Introduce Knowledge Packages as a Core Knowledge Islands Primitive | Accepted | 2026-07-11 | Accepted 2026-07-11; implemented by [KIS-0001](../specifications/KIS-0001-knowledge-package/) |
| [KIP-000002](KIP-000002-knowledge-export-package/) | Introduce the Knowledge Export Package | Implemented | 2026-07-23 | Implemented by [KIS-0002](../specifications/KIS-0002-knowledge-export-package/) |
