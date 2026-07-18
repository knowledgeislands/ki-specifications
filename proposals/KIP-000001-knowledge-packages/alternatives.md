# KIP-000001 — Alternatives Considered

This document records the approaches we weighed as ways to carry shared cognitive work between people, agents and models, and why each was rejected in favour of the Knowledge Package proposed in [`proposal.md`](proposal.md). Throughout, we test each option against the four requirements the primitive exists to meet: **portability** (moves freely across tools, models and time), **governance** (has a steward, an audit trail, and a human review point), **provenance** (records who and what produced the content, from what sources), and **model independence** (does not bind the organisation's knowledge to one provider or model).

## Shared vector / embedding memory stores

_What it solves._ A shared embedding store lets many sessions and agents retrieve relevant prior context by similarity, and scales to large volumes of material without manual organisation.

_Why it fails._ An embedding store is opaque: a person cannot read, diff, or reason about what it holds, which defeats governance and makes a human review point impossible. It carries no reliable provenance — retrieved fragments arrive without a trustworthy record of origin, authorship or method. It has no natural place for classification to gate handling, so confidential and privileged material leak by similarity. And it is not a unit of work anyone can pick up and continue: it is a retrieval substrate, not a resumable, self-describing package. It fails on governance, provenance, and classification, and only partially serves portability.

## Vendor memory APIs and direct model-to-model memory sharing

_What it solves._ Vendor memory features and direct memory transfer between models make continuity almost free within one ecosystem — an assistant "remembers" across sessions with no effort from the user.

_Why it fails._ This is the anti-pattern the proposal is written against. It binds the organisation's accumulated understanding to one provider's representation and interface, forfeiting model independence and portability. The store is opaque and ungoverned — no reviewable record of what entered it, on whose authority, or when, and no checkpoint at which a human can inspect or reject what is carried forward. Classification is not enforced, so sensitive material crosses boundaries implicitly. And because the state lives inside the model, the organisation loses the ability to swap that model for a better or cheaper one. It fails on portability, governance, model independence, and classification alike.

## Plain documents / wikis without a manifest or governance

_What it solves._ Ordinary documents and wiki pages are legible, portable, and familiar; people already know how to write and read them, and they carry prose content well.

_Why it fails._ Without a structured manifest there is no machine-actionable identity, classification, lifecycle, task state, or relations — so tools and agents cannot reliably find, filter, gate, or resume the work, and a package cannot state its own sensitivity. Without governance conventions there is no steward, retention rule, promotion gate, or dependable audit trail; without a provenance record the origin and method of the content are unrecorded. Plain documents satisfy portability but fail governance, provenance and machine-actionable classification. The Knowledge Package is, in effect, this option plus the manifest and governance that make it dependable.

## Per-model fine-tuning as organisational memory

_What it solves._ Fine-tuning a model on an organisation's material bakes domain knowledge directly into the engine, so it is available at inference without retrieval.

_Why it fails._ Fine-tuned weights are the least portable and least legible form imaginable: knowledge is fused into one model's parameters, unreadable, un-diffable, ungovernable, and impossible to audit or selectively retract. Provenance and classification cannot be represented at all once material is absorbed into weights. It is the strongest possible violation of model independence — the knowledge _is_ the model — and it cannot represent in-flight, resumable work at all. It fails every requirement.

## Chat-transcript export

_What it solves._ Exporting the raw conversation preserves the full record of what was said, cheaply and without any new format, so nothing is lost.

_Why it fails._ A transcript is unstructured and undistilled: the decisions, assumptions, open questions and tasks are buried in a linear log that a human or agent must re-read and re-reason to recover, which defeats fast resumption. It carries no manifest, so no identity, classification, lifecycle or relations; no governance and no promotion gate; and only incidental provenance. It is tied to the exporting vendor's format and is often unusable by a different model without transformation. It fails on governance, classification and machine-actionability, and serves portability and provenance only weakly.

## Conclusion

Every alternative fails at least two of the four requirements, and the two that come closest — plain documents and chat-transcript export — fail precisely for want of a structured, governed manifest. The Knowledge Package is the minimal shape that satisfies all four: a legible manifest that carries identity, classification, lifecycle, tasks, relations and provenance for governance and machine-actionability, pointing to Markdown artefacts that carry the meaning, all model-independent and portable by construction.
