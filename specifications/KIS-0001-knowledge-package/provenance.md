# KIS-0001 — Provenance

Status: Draft
Version: 1.0.0

Provenance records where a Knowledge Package came from; history records what has happened to it.
Together they make a package auditable.

## Provenance

The `provenance` object records:

- `createdBy` — the party that created the package (REQUIRED when `provenance` is present).
- `sources` — the references the package was derived from (OPTIONAL; each is a Reference).
- `method` — a short description of how the package was produced (OPTIONAL).

A package SHOULD record `provenance`; the Standard conformance level requires it.
Where a package is derived from other Knowledge Packages, those SHOULD appear both in `provenance.sources` and, where the relationship is structural, in `related`.

## History

The `history` array is the event log of the package.
Each event has a `timestamp`, an `actor` (a party), an `action`, and an optional `note`.
Typical actions include `created`, `updated`, `handover`, `promoted`, `archived`, and `superseded`.

History SHOULD be append-only: existing events SHOULD NOT be edited or removed, and new events are added to the end.
Because published versions are immutable, the history carried by a published version is a snapshot as at that version; a later version extends it.

## Auditability

Provenance and history MUST survive handover and promotion unchanged.
A handover MUST NOT discard the receiving party's ability to see who created the package and what has happened to it, and promotion MUST NOT rewrite the record of how the package came to be.

An actor recorded in provenance or history MAY be a `human`, an `agent`, or an `organisation`; agent authorship MUST be recorded as such rather than being attributed to a human.

*(Informative)* Cryptographic signing of history events is out of scope for KIS-0001 but is a candidate for a future extension; see [extension-model.md](extension-model.md).
