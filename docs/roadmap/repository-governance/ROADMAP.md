---
code: RGV
---

# Repository governance roadmap

## Blocking

Actively broken, or blocking the `Next` horizon: takes priority over everything else and must clear before `Next` work proceeds. Empty means nothing is on fire.

## Next

Scoped and ready to start — the immediate queue, picked up before anything in **Soon** or **Future**.

### Review KI Specifications as a complete repository

Review the repository end to end before expanding its normative surface: re-evaluate the KIP/KIS authority model, proposal and specification lifecycle, repository structure, source and supporting documentation, current tool configuration, and accumulated governance drift.

Keep this review separate from the narrow KBEP and KBIP assessments. It should establish which parts of the repository remain correct, which need a clean-end-state cutover, and what evidence is required before deeper specification work proceeds.

**Plan:** [KIS-RGV-001](plans/KIS-RGV-001-review-specifications-repository.md)

## Soon

Understood and roughly scoped but not yet started — worth doing once the **Next** queue clears, ahead of anything still speculative.

## Waiting for

Worth doing, but presently blocked on an external dependency or decision. Revisit when its named condition changes; do not use this horizon for intentionally paused work.

## Parked

Intentionally paused work with no current attention. Revisit only when its priority or named return trigger changes.

## Future

Speculative or not yet scoped — items marked _(candidate)_ need a scoping pass (or a decision to drop them) before they're actionable.
