# KIS-0001 — Promotion

Status: Draft
Version: 1.0.0

Promotion is the governed act of publishing a Knowledge Package's content as canonical organisational knowledge.
Promotion is distinct from the lifecycle: a package's `lifecycle` describes the state of the work, whereas promotion concerns whether that work's content has been accepted as authoritative.
A package MAY be promoted while remaining `active`, and an `archived` package's content MAY already have been promoted earlier in its life.

## Package content versus canonical knowledge

The content held in a Knowledge Package is *proposed* knowledge: it is owned, versioned, and governed, but it is not thereby canonical.
Canonical knowledge is the organisation's accepted, authoritative record.
Promotion is the bridge between the two.
The representation of canonical knowledge is outside the scope of KIS-0001; this specification governs only how a package records that promotion occurred.

## Recording a promotion

A promotion MUST be recorded in two ways:

1. a `related` entry with relationship `promotedTo` identifying the canonical target by `id` or `uri`; and
2. a `history` event whose `action` is `promoted`, recording the actor and timestamp.

The promotion MUST satisfy the `promotionPolicy` recorded in `governance` (see [governance.md](governance.md)); where `reviewers` are named, their review forms part of that policy unless the policy states otherwise.

## Classification is preserved

Promotion MUST NOT implicitly lower a package's `classification`.
If promoted content is to be handled at a lower classification, that reclassification MUST be a separate, explicit governance action, recorded in `history`, and subject to the handling rules in [security-and-classification.md](security-and-classification.md).
In particular, `privileged` content MUST NOT lose its handling protections merely because it has been promoted.

## Relationship to supersession

Promotion does not supersede the source package.
A promoted package remains a first-class package with its own lifecycle; if it is later replaced, that replacement is recorded through `supersedes` / `supersededBy` as usual (see [lifecycle.md](lifecycle.md)), independently of the `promotedTo` relationship.
