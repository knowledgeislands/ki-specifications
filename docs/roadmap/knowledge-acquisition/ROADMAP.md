---
code: KEP
---

# Knowledge acquisition roadmap

## Blocking

Actively broken, or blocking the `Next` horizon: takes priority over everything else and must clear before `Next` work proceeds. Empty means nothing is on fire.

## Next

Scoped and ready to start — the immediate queue, picked up before anything in **Soon** or **Future**.

### Specify Knowledge Export Package v0 and the acquisition boundary

Adopt the portable KEP contract that sits between faithful source acquisition and downstream knowledge extraction. It must give the first `ki acquire` implementation a deterministic, provenance-preserving output without defining a connector implementation or Knowledge Base ingress.

**Plan:** [KEP-001](plans/KEP-001-specify-kep-v0-and-acquisition-boundary.md)

## Soon

Understood and roughly scoped but not yet started — worth doing once the **Next** queue clears, ahead of anything still speculative.

## Waiting for

Worth doing, but presently blocked on an external dependency or decision. Revisit when its named condition changes rather than treating it as dormant local work.

## Future

Speculative or not yet scoped — items marked _(candidate)_ need a scoping pass (or a decision to drop them) before they're actionable.
