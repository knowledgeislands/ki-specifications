# KIS-0001 — Lifecycle

Status: Draft Version: 1.0.0

The `lifecycle` field records the current state of a Knowledge Package. The lifecycle describes the _state of the work_; it is distinct from promotion, which publishes the work's content as canonical knowledge (see [promotion.md](promotion.md)).

## States

| State        | Meaning                                                                         |
| ------------ | ------------------------------------------------------------------------------- |
| `draft`      | Being assembled; not yet ready to be relied upon.                               |
| `active`     | Under active work and fit to be used.                                           |
| `paused`     | Temporarily not being worked on; expected to resume.                            |
| `handover`   | Prepared for another party to take over; `handover` material SHOULD be present. |
| `completed`  | Work is finished; the package is stable but not archived.                       |
| `archived`   | Retired; retained for record. Terminal.                                         |
| `superseded` | Replaced by a successor package. Terminal.                                      |

## Transitions

| From         | Permitted next states                                       |
| ------------ | ----------------------------------------------------------- |
| `draft`      | `active`, `archived`                                        |
| `active`     | `paused`, `handover`, `completed`, `archived`, `superseded` |
| `paused`     | `active`, `handover`, `archived`, `superseded`              |
| `handover`   | `active`, `paused`, `archived`, `superseded`                |
| `completed`  | `archived`, `superseded`                                    |
| `archived`   | _(none — terminal)_                                         |
| `superseded` | _(none — terminal)_                                         |

A transition not listed above MUST NOT be recorded. Every transition SHOULD be reflected by a corresponding entry in `history`.

## Rules

An `archived` package MUST NOT be modified except to record its supersession — that is, to add a `related` entry with relationship `supersededBy` and the accompanying `history` event, and to change `lifecycle` to `superseded` if it was not already.

A package in the `superseded` state MUST carry a `related` entry with relationship `supersededBy` that identifies its successor. The successor package SHOULD carry the reciprocal `supersedes` relationship.

Because each published version is immutable (see [specification.md](specification.md) §3), a lifecycle change that alters a published manifest is itself a new version of the package, carrying the same `uuid`.
