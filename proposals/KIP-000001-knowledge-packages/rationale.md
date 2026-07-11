# KIP-000001 — Rationale

This document sets out the design reasoning behind the Knowledge Package as proposed in [`proposal.md`](proposal.md). It explains why the primitive takes the shape it does, so that the choices are on the record and can be revisited deliberately rather than by accident.

## Why a manifest-plus-artefacts shape

We chose a structured manifest that points to Markdown artefacts, rather than either a single opaque blob or a pile of loose documents, because the two halves do different jobs and both are needed.

The manifest is legible structured data. It is what lets tools, planners and agents find, filter, govern, de-duplicate and route packages without parsing prose: identity, classification, ownership, lifecycle state, tasks with status and dependencies, decisions with status, relations to other packages. Structure is what makes a package machine-actionable and governable.

The artefacts — the executive digest, the technical digest, and any supporting material — are Markdown, because the substance of cognitive work is prose meant for humans to read, and Markdown is portable, diffable, legible without special tooling, and equally comfortable for a person or a model. Forcing that content into rigid fields would strip it of the nuance that makes it worth keeping; leaving everything as prose would make it ungovernable. The manifest governs; the artefacts carry the meaning. Keeping the heavy content in referenced artefacts also keeps the manifest small enough to pass around and reason over cheaply.

## Why governed promotion

We separated the package from the organisation's canonical knowledge, and made the transition between them a governed step, because working state and retained knowledge have different truth conditions. A package is provisional by nature — it holds assumptions that may be wrong, decisions that may be reversed, open questions not yet answered. Promoting all of that automatically into the organisation's durable record would pollute the record with unsettled material and remove the very human review point whose absence we criticise in vendor memory. Promotion is therefore explicit, human-reviewed, and recorded via a `promotedTo` relation, so the organisation's canonical knowledge earns its status rather than accumulating it by default.

## Why classification is first-class

Classification (`public`, `internal`, `confidential`, `privileged`) is a required property that travels with the package, rather than an optional tag or an external overlay, because the package is designed to move. A portable unit that can be handed between people, agents and modules must carry its own handling rules with it; the moment classification is separable from the package, it can be lost in transit, and confidential or privileged material can cross a boundary silently. Making it a required field means every package states its sensitivity, every tool can gate on it, and there is no default-open failure mode.

## Why models are treated as replaceable execution engines

The whole design keeps durable state outside the model because the alternative — state living inside a model's memory — welds the organisation's knowledge to a particular provider and a particular model version, and forfeits the freedom to choose the best engine for each job. Knowledge Islands is explicitly built on a federation of models across several execution routes; that federation only delivers value if models can be swapped, mixed and upgraded freely. Treating the model as an interchangeable engine and the package as the persistent state is what preserves that freedom, and it is why a package must be fully self-describing and model-independent: nothing in it should depend on which engine produced or will continue it.

## Why a minimal required core

We keep the mandatory fields to the few that identify, classify, own and summarise a package, and make everything else optional, because adoption is the binding constraint. A primitive that demands a great deal of structure before it yields any value will be routed around — people will simply keep talking to an assistant. A minimal core lets a package be as cheap as a single digest with an identifier and a classification, while the optional fields let it grow into a full programme of work when the work justifies it. The richness is available but never up front. This also future-proofs the format: optional fields and an extension mechanism let domains and tools carry what they need without forcing that weight onto every package or requiring a format revision for every new need.
