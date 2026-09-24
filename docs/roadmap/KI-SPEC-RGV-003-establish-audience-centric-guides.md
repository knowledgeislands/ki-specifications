---
id: KI-SPEC-RGV-003
title: Establish audience-centric guides
area: RGV
theme: repository-governance
horizon: now
status: draft
blocks: []
blocked_by: []
transferred_from: ki-website
baseline_ref: null
created_at: 2026-09-21T17:20:00Z
updated_at: 2026-09-24T09:14:00Z
---

## Goal

Someone proposing a change to a specification, and someone implementing one, each find practical instructions for doing so in a guide collection grouped by audience.

## Context

`ki-specifications` has no `docs/guides/` and does not declare `ki-guides`. Its README carries How to propose a change, which is practical instruction for a real audience sitting in a reference document.

This repository is the normative standards and governance layer: it holds proposals, accepted specifications, JSON Schemas, governance rules, and templates. `docs/specs/` is rightly the point of the repository, and this item does not touch it. But a normative corpus has procedural readers as well as normative ones — someone raising a KIP, someone implementing an accepted KIS, someone deciding whether a change needs a proposal at all — and the how of those tasks is guide material, not specification material.

KI Website now declares, for every page it publishes under `apps/site/src/guidance/`, the exact upstream document and pinned ref that page was written from, and a `verify:guidance --network` sweep reports the pages whose source has moved. The site intends to derive public guidance for this project from this repository's own guides and cite them at a pinned ref, so the quality and stability of `docs/guides/` here directly determines the quality of what the site can publish.

That is a pull, not an obligation: KI Website derives, it does not own. This repository decides what its guides say and when they change.

Separately, `KI-HARNESS-GOV-083` has clarified `ki-guides`: audience directories are recommended when stable reader groups make a collection easier to navigate, while flat and mixed collections remain valid. This item therefore stands on this repository's own readers and routing needs, not a universal Harness requirement.

## Boundary

Adopted into `Now` by explicit approval, so this is prioritised work rather than intake. It remains `status: draft`: `ki-plan` shapes it to `Ready` before any implementation, and this repository still owns its plan and sequencing.

This item does not touch `docs/specs/`. The normative corpus is what this repository is for, and nothing here proposes restating a specification as a guide — the division is that a specification says what is true and a guide says how to do something.

KI Website derives and cites; it does not own this collection and must not be given approval rights over it.

## Shaping

- Decide whether the procedural audiences are distinct enough to warrant separate directories, or whether one contributor audience covers proposing and implementing alike.
- Move the README's How to propose a change into the guide that owns it.
- Settle the line between a guide and a governance rule. Where the process is normative, the specification is authoritative and the guide walks a reader through it rather than restating it.
- Decide whether the KIP/KIS lifecycle needs a guide of its own, since a reader meeting it for the first time has to infer it from the corpus.
- Declare `[skills.ki-guides]` in `.ki.toml` and run the guides audit to gate the result.

## Current state

No `docs/guides/` directory and no `[skills.ki-guides]` in `.ki.toml`. The only procedural instruction is the README's How to propose a change section. `docs/specs/` holds the normative corpus and is out of scope here.

## Steps

- [ ] Name the procedural audiences this repository has.
- [ ] Create `docs/guides/README.md` as the collection index, routing by audience and nothing else.
- [ ] Create one directory per named audience, each with its own index.
- [ ] Move the README's How to propose a change material into the guide that owns it.
- [ ] Write the missing guides: raising a KIP, implementing an accepted KIS, and deciding when a change needs a proposal.
- [ ] Record where a guide defers to a normative rule rather than restating it.
- [ ] Declare `[skills.ki-guides]` in `.ki.toml`.
- [ ] Run the guides audit and repair what it reports.

## Files touched

`docs/guides/` (new), `.ki.toml`, `README.md`.

## Verify

`ki repo audit --skill ki-guides --repo .` passes, and `ki repo audit --skill ki-authoring --repo .` passes over the collection.

## Dependencies / blocks

Nothing blocks this. `KI-HARNESS-GOV-083` is advisory rather than a universal migration requirement; this item's audience grouping remains justified by the repository-local reader distinctions described above. KI Website intends to derive public guidance from these guides and cite them at a pinned ref, but it derives rather than owns and its schedule does not gate this work.

## Documentation impact

### Decision Records

No decision record is needed. Audience-centric grouping is the house arrangement `ki-guides` already encodes, so adopting it here is conformance rather than a new decision. One becomes owed only if this repository concludes it needs an exception.

### Specifications

No behaviour-level contract changes. This item changes only where instructions live and who they are written for.

### Guides

This item is entirely guide impact: it establishes or completes the collection, its audience directories, and their indexes.

### Roadmap

No further roadmap change is expected. If writing the guides exposes behaviour that cannot honestly be explained, that is a separate item raised at the time.

## Discussion

Shaping settles how far this goes, not whether it happens. The prompting question is whether a reader who has never opened this repository can do what it is for without reading source.
