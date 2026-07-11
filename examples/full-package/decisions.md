# Decisions

Prose expansion of the `decisions` entries in `manifest.json`, with the fuller reasoning that does not fit in each entry's `rationale`.

## DEC-001 — Models are replaceable execution engines, not stores of organisational knowledge

Status: accepted (2026-02-10)

The alternative considered was to let organisational knowledge accumulate inside a single provider's conversation or fine-tuning history.
That approach was rejected because it ties the organisation's accumulated judgement to one vendor's product roadmap, pricing, and continuity, and because it cannot be audited, versioned, or shared across the humans and agents who need it.
Keeping knowledge in the kernel and its modules, expressed as Knowledge Packages, means the organisation can add, drop, or federate across model providers without losing what it has learned, and can inspect and govern that knowledge directly.

## DEC-002 — Adopt a hierarchical continual-improvement loop

Status: accepted (2026-03-04)

The alternative considered was flat, per-module improvement, where each kernel module maintains and improves its own knowledge independently.
That was rejected because it duplicates effort: a lesson learned by one module (for example, a better way to phrase a particular class of request to a given model) would have to be rediscovered independently by every other module.
The hierarchical loop, promoting lessons from task to module to kernel, lets an improvement made anywhere eventually raise the baseline for the whole system, at the cost of needing an explicit, governed promotion step at each level (see `governance.promotionPolicy`) rather than letting improvement happen silently.

## DEC-003 — Kernel modules are the unit of domain specialisation, not forks of the kernel

Status: accepted (2026-04-18); supersedes DEC-000

An earlier decision (DEC-000, not retained in this package) proposed letting domain teams fork the kernel itself when they needed specialised behaviour.
That was superseded once early module development showed forking would fragment governance and scheduling behaviour across forks, and would make it hard to apply a kernel-level improvement to every domain team at once.
Instead, kernel modules extend a single shared kernel through a defined module interface; domain teams (illustrated here by Humans Not Robots, Equal Remedy, and Kit-Legal) own their module's knowledge and workflow, but never fork the kernel's scheduling or governance behaviour.
