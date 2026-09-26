# AGENTS.md - KI Specifications

This is the runtime-neutral working convention for KI Specifications. The README is the entry point for the repository's normative scope, KIP/KIS model, and contribution workflow.

## Progress and commits

- Give concise progress updates at meaningful checkpoints and at least every few minutes during sustained work.
- Commit only a completed, verified unit of work. Stage explicit paths for that unit and do not combine it with unrelated working-tree changes.
- If a unit cannot yet be verified, report the checkpoint and leave it uncommitted until its verification is complete.

## Cross-repository choreography

- Arcadia Principal, the KI Agentic Harness, `tools-ki`, KI Specifications, and the KI Website may add a concrete handoff item to one another's Stream or roadmap. The receiving repository owns its priority, plan, and execution.
- Record the originating repository and item, then state whether the handoff `blocks` or is `blocked by` the local item. Keep the relationship reciprocal where both items exist.
- Prefer independently executable, non-blocking work. Mark an item as blocking only when it is a genuine prerequisite; otherwise let the receiving repository schedule it in its own horizon.

## Specification posture

- This repository is dormant while Knowledge Islands remains at v0.x; it owns no active ecosystem-wide specifications before the overall v1 boundary is reviewed.
- Keep repository-level specifications in their owning repositories.
- Treat the KIP/KIS material here as the future process, not authority to begin an ecosystem-wide specification programme.
