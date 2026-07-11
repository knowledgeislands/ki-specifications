# Hierarchical learning design note

This is the normative description of deliverable D-2, referenced from `manifest.json` (`deliverables[1].path`, `artefacts.hierarchical-learning`).

## The three levels

Lessons propagate through three levels: task, module, kernel.

1. **Task level** — a lesson is first captured against the specific task's Knowledge Package where it was observed (for example, a decision or an entry in `history`).
2. **Module level** — if the lesson generalises beyond that one task, it is promoted into the owning kernel module's retained knowledge, so every future task routed through that module benefits from it.
3. **Kernel level** — if the lesson generalises beyond that one module, it is promoted further into the kernel itself, so every module benefits.

## Promotion is governed, not automatic

Promotion at each level is a deliberate, governed action, subject to the promoting party's `governance.promotionPolicy`, and is recorded as a `history` event with `action: "promoted"`.
Promotion is not a lifecycle state: a package can be `active`, `paused`, or `completed` and still have content promoted out of it.

## Open question

How the loop should weight two lessons arriving from different modules at the same time, when they appear to conflict, is not yet resolved; see the package's `openQuestions` and task T-4.
