# Deciding whether a change needs a KIP

Use this guide before you change anything in the specification corpus. It tells you which route a change takes, so that you neither open a proposal for a typo nor slip a substantive change through as an editorial fix.

## What to do today

Knowledge Islands is pre-v1. Until the overall v1 boundary has been reviewed, this repository registers no new KIPs or KIS documents and owns no active ecosystem-wide specification.

- If your concern is a contract for one repository - its command grammar, its file formats, its behaviour - raise it in that repository. Repository-level specifications stay with the repository that owns the implementation.
- If your concern is genuinely ecosystem-wide, open an issue in this repository describing the problem, who it affects, and why it cannot live in one repository. A maintainer will record it for the v1 boundary review rather than registering a proposal.
- If you have found an editorial problem in the process documents themselves - a typo, a broken link, unclear wording that does not change meaning - open an ordinary pull request.

The rest of this guide describes the routing that applies once the programme is active.

## The four routes

Every change to the corpus takes exactly one of four routes. Work through the questions in order and stop at the first that fits.

### 1. Does the change alter meaning at all?

If not, it is an **editorial fix**: a typo, a broken link, formatting, or a clarified example that was already implied by the text. Raise it as an ordinary pull request against the affected file. Applied to a published KIS it is errata - a patch-level change that does not need a proposal.

Test: would a package or tool that conformed before the change still conform after it, for exactly the same reasons? If yes, and nobody would need to change their implementation, it is editorial.

### 2. Is it a compatible addition to an existing KIS?

A new optional field, new informative guidance, or new conformance-level detail that leaves every existing conformant package valid is a **minor version** of the same KIS. The maintainers decide such changes; open an issue or pull request against the specification and explain why existing implementations are unaffected.

### 3. Does it break an existing KIS, or replace it?

Anything that would make a previously conformant package or implementation non-conformant is a **major version**, and a major version always starts with a new KIP. Where the change is large enough that the old specification should be retired in favour of a new document, it is a **superseding KIS**, which also starts with a KIP; the old KIS is later marked `Superseded` with a pointer to its successor.

### 4. Is it new?

A new foundational concept, a new specification, or an extension to the model that no existing KIS covers starts life as a **new KIP**. Follow [Raising a KIP](raising-a-kip.md).

## Changes to the process itself

Changes to roles, decision-making, or the KIP-to-KIS pipeline are themselves proposed through a KIP, because the governance document is subject to the same process as any specification.

## Where the rules live

This guide walks the routing; it does not define it. `GOVERNANCE.md` is the authority for amending an accepted KIS and for who decides, and `docs/versioning.md` is the authority for what counts as a patch, minor, or major change. If this guide and those documents disagree, they win; raise an editorial fix against this guide.

## If you are still unsure

Open an issue describing the change and ask. A maintainer will say which route applies. Asking first costs less than a proposal written for the wrong route.
