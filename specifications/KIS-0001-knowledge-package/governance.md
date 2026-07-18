# KIS-0001 — Governance

Status: Draft Version: 1.0.0

Governance records who is accountable for a Knowledge Package and under what rules it is cared for, reviewed, promoted, and retained.

## Ownership

A package MUST declare at least one `owner` in the root `owners` array. An owner is a party — `human`, `agent`, or `organisation` — accountable for the package. Where accountability rests with an organisation, the owner SHOULD be that organisation; individuals may additionally be listed with a `role`.

## Stewardship and review

The `governance` object records the operating arrangements:

- `steward` — the party responsible for day-to-day care of the package on the owner's behalf.
- `reviewers` — parties who review the package before significant actions such as promotion.
- `promotionPolicy` — the rule that must be satisfied before the package's content may be promoted (see [promotion.md](promotion.md)).
- `retention` — how long the package is kept and when its classification or state is reviewed.

The Standard conformance level requires `governance` with a named `steward`. A steward SHOULD be distinct from the sole reviewer of the same action where independent review is intended.

## Interaction with classification

Governance operates within the constraints of the package's `classification` (see [security-and-classification.md](security-and-classification.md)). A steward MUST NOT take an action — including promotion, handover, or a change of classification — that would breach the handling requirements of the current classification. Lowering a package's classification is a governance action that MUST be explicit and recorded in `history`; it MUST NOT happen as a side effect of any other action.

## Interaction with promotion

Promotion is a governed action: it MUST satisfy the `promotionPolicy` recorded in `governance`, and where `reviewers` are named, their review is part of that policy unless the policy states otherwise. Promotion MUST NOT implicitly lower classification; see [promotion.md](promotion.md).

## Retention and archival

When a package reaches the end of its retention, the steward SHOULD move it to `archived` (see [lifecycle.md](lifecycle.md)) rather than deleting it, so that its provenance and history remain auditable. An archived package MUST NOT be modified except to record supersession.
