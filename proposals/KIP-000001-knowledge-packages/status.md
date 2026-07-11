# KIP-000001 — Status

- Number: KIP-000001
- Title: Introduce Knowledge Packages as a Core Knowledge Islands Primitive
- Current status: Accepted
- Implemented by: [KIS-0001 — Knowledge Package](../../specifications/KIS-0001-knowledge-package/)

## Status history

| Date | Status | Note |
| --- | --- | --- |
| 2026-07-11 | Draft | Proposal drafted to establish the Knowledge Package primitive. |
| 2026-07-11 | Review | Proposal circulated for review. |
| 2026-07-11 | Accepted | Accepted; commissions KIS-0001. |

All three transitions carry the same date because this proposal was adopted as part of the initial bootstrap of the specification repository. The acceptance was **editorial** — it records the founding decision to establish the Knowledge Package rather than the outcome of an open review round. Subsequent proposals will pass through `Draft → Review → Accepted` over real elapsed time.

## Resolution

Accepted on 2026-07-11. The proposal is implemented by the normative specification [KIS-0001 — Knowledge Package](../../specifications/KIS-0001-knowledge-package/), which defines the manifest, its required and optional fields, the identifier scheme, the lifecycle, the classification and governance model, the promotion relation, and the conformance criteria, with an accompanying JSON Schema and worked examples.

## Unresolved questions carried into KIS-0001

The following were left open by this proposal and are carried into the specification and its future revisions to resolve:

- **Package signing and integrity.** How, if at all, a package's authenticity and integrity are attested, so a recipient can trust that a package is what it claims to be and has not been altered in transit.
- **Transport bindings.** How packages are exchanged between tools, agents and modules in practice — the concrete carriage, distribution and discovery mechanisms — which this proposal deliberately leaves out of the format itself.
- **Promotion tooling.** The concrete mechanics of the governed promotion step from package content to canonical organisational knowledge, including the review workflow and how the `promotedTo` relation is recorded and verified.
