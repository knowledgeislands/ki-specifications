# AGENTS.md - KI Specifications

This is the runtime-neutral working convention for KI Specifications. The README is the entry point for the repository's normative scope, KIP/KIS model, and contribution workflow.

## Progress and commits

- Give concise progress updates at meaningful checkpoints and at least every few minutes during sustained work.
- Commit only a completed, verified unit of work. Stage explicit paths for that unit and do not combine it with unrelated working-tree changes.
- If a unit cannot yet be verified, report the checkpoint and leave it uncommitted until its verification is complete.

## Cross-repository choreography

- Arcadia Principal, the KI Agentic Harness, KI Specifications, and the KI Website may add a concrete handoff item to one another's Stream or roadmap. The receiving repository owns its priority, plan, and execution.
- Record the originating repository and item, then state whether the handoff `blocks` or is `blocked by` the local item. Keep the relationship reciprocal where both items exist.
- Prefer independently executable, non-blocking work. Mark an item as blocking only when it is a genuine prerequisite; otherwise let the receiving repository schedule it in its own horizon.

## Specification authority

- KIPs are proposals; KIS documents are the normative specifications produced from accepted proposals.
- An Active KIS governs implementations that claim conformance within its scope.
- Keep explanatory publication in the website and implementation-specific tooling in the harness; this repository owns portable normative contracts.
