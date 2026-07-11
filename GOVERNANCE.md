# Governance

This document describes who decides what happens in this repository, and how.

## Roles

- **Author** — the person or organisation who drafts a KIP. Anyone may be an Author; authorship does not require any standing role in the project.
- **Editor** — a person who stewards a specific KIP or KIS through its lifecycle: keeping its files consistent, incorporating review feedback, and preparing it for a maintainer decision. An Editor may or may not be the original Author.
- **Maintainer** — a person with authority to assign KIP and KIS numbers, decide the outcome of review (`Accepted`, `Rejected`, merging a `Superseded` marker, and so on), and change this governance document itself.

## Decision-making

Decisions are made by maintainer consensus.

This project is currently bootstrapped with a single maintainer (Kris Brown).

That is stated here plainly rather than dressed up as a committee: as further maintainers join, this section will be updated to describe how consensus is reached among them, and what happens when they disagree.

## The KIP → KIS pipeline

In summary (see [docs/specification-process.md](docs/specification-process.md) for full detail):

1. A KIP is drafted, numbered, and moves `Draft → Review`.
2. Review concludes with `Accepted`, `Rejected`, or the author's own `Withdrawn`.
3. An `Accepted` KIP is drafted into a KIS, which starts at status `Draft`.
4. Once there is real implementation experience against a Draft KIS, it is promoted to `Active`, and the originating KIP is marked `Implemented`.
5. An `Accepted` KIP may later be marked `Superseded` if a subsequent KIP replaces its intent before, or instead of, implementation.
6. An `Active` KIS may later be marked `Deprecated` and eventually `Superseded` by a later KIS.

## Amending an accepted KIS

Not every change to a published KIS requires a new KIP. Three routes exist, and choosing the right one matters:

- **Errata** — a correction to the text that does not change meaning: a typo, a broken link, a clarified example that was already implied. Maintainers may apply errata directly, and it is not a version-changing event.
- **New version of the same KIS** — a substantive but compatible or breaking change to the specification's content. This follows the versioning rules in [docs/versioning.md](docs/versioning.md): editorial changes are a patch, compatible additions are a minor version, and breaking changes require a new KIP and are a major version.
- **Superseding KIS** — where the change is significant enough that the old specification should be retired in favour of a new document (a new KIS number), rather than a new version of the same one. This itself requires a KIP, and the old KIS is marked `Superseded` with a pointer to its replacement.

## Changing this document

This governance document is itself subject to KIP: any change to roles, decision-making, or the pipeline described here is proposed, reviewed, and accepted the same way as any other specification change, per [CONTRIBUTING.md](CONTRIBUTING.md).
