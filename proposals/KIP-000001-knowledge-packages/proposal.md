# KIP-000001 — Introduce Knowledge Packages as a Core Knowledge Islands Primitive

- Status: Accepted
- Created: 2026-07-11
- Accepted: 2026-07-11
- Implemented by: [KIS-0001 — Knowledge Package](../../specifications/KIS-0001-knowledge-package/)

## Summary

This proposal introduces the Knowledge Package as a core primitive of Knowledge Islands: a portable, self-describing, governed unit of shared cognitive work that captures the state of an ongoing piece of thinking — its digests, decisions, assumptions, open questions, tasks, deliverables, provenance and governance — in a form that any competent human or AI agent can pick up and continue. The package exists so that the understanding built up during knowledge work is not stranded inside a single AI conversation or a single vendor's private memory, but is held as an organisational artefact that outlives any one model, tool, session or person.

## The problem: knowledge trapped in conversations and vendor memories

Most of the reasoning that happens when people work with AI assistants is thrown away. A rich problem is explored across a long conversation — options are weighed, constraints surface, decisions are made, dead ends are ruled out — and then the session ends. What survives is, at best, a final answer stripped of the reasoning that produced it, and at worst nothing at all. The next person, or the next agent, or the same person a fortnight later, starts again from a blank prompt.

Where that context does persist, it persists in the wrong place. It lives in a vendor's conversation history, or in a proprietary "memory" feature bolted onto one assistant, keyed to one account, readable only through that vendor's interface and only by that vendor's model. The organisation that paid for the thinking cannot see it, cannot govern it, cannot move it, and cannot audit it. When the subscription lapses, the seat is reassigned, or the vendor changes the product, the accumulated understanding evaporates. Knowledge that ought to be an organisational asset is instead an accident of where a conversation happened to occur.

This is the gap Knowledge Islands sets out to close. The organisation's retained knowledge should live in the organisation's own governed modules, not inside a model or a vendor account. But to get there we need a concrete unit — a shape that in-flight cognitive work can be captured in, moved around in, and resumed from. That unit is the Knowledge Package.

## Why not simply share memory between models?

An obvious-looking shortcut is to let models share memory directly — to have one assistant's memory populate another's, or to rely on ever-larger vendor memory features as the substrate for organisational knowledge. We reject this direction deliberately, for several compounding reasons.

- **Vendor lock-in.** Direct model-to-model memory ties the organisation's accumulated understanding to a particular provider's representation and interface. The knowledge becomes only as portable, and only as durable, as that vendor's product decisions.
- **Opacity.** Vendor memories are typically opaque stores — embeddings or private state a person cannot read, diff, or reason about. Knowledge the organisation depends on should be legible to the people accountable for it.
- **No governance or audit.** There is no reviewable record of what entered the memory, who put it there, on what authority, or when. Organisational knowledge needs stewardship, retention rules, and an audit trail; a private memory blob offers none.
- **Privacy and classification leakage.** When memory flows implicitly between models and sessions, confidential or privileged material crosses boundaries it should never cross, with no gate to stop it. Classification has to be a first-class, enforceable property of the unit — not an afterthought.
- **No human review point.** Implicit memory sharing removes the moment at which a human can inspect, correct, approve or reject what is being carried forward. Governed knowledge needs that checkpoint.
- **Model replaceability is lost.** If understanding lives inside a specific model's memory, the organisation can no longer freely swap that model for a better, cheaper or differently-specialised one. The knowledge and the execution engine become welded together, which is exactly backwards.

Knowledge Islands treats models as replaceable execution engines and keeps the durable state outside them. A Knowledge Package is that externalised state.

## What we propose: a portable shared cognitive work unit

We propose that Knowledge Islands define the Knowledge Package as its unit of shared cognitive work: a manifest-plus-artefacts bundle, identified by a stable identifier and described by structured metadata, that any tool or agent in the ecosystem can produce, read, update and hand on. The manifest is legible structured data; the substantive content lives in Markdown artefacts the manifest points to. The package is designed to be handed between humans and agents freely, and to be resumed by a different human or a different agent from the one that created it.

### Capabilities a package must carry

To serve as the shared cognitive work unit, a package needs to carry — at least optionally — the following, so that whoever picks it up has what they need to continue:

- **Identity and metadata** — a stable identifier, title, description, classification, ownership, timestamps and version, so the package can be referenced, governed and de-duplicated.
- **Executive digest** — a short, human-facing summary of what this work is and where it stands, readable by a non-specialist stakeholder.
- **Technical digest** — a fuller, working-level summary for whoever will actually continue the work.
- **Decisions** — what has been decided, with rationale and status, so choices are not silently re-litigated.
- **Assumptions** — what the work currently takes to be true, made explicit so it can be challenged.
- **Constraints** — the boundaries the work must respect.
- **Terminology** — the definitions this work relies on, so a new reader shares the same vocabulary.
- **Open questions** — what remains unresolved, so the next worker knows where to look.
- **Tasks** — the units of work outstanding, with status and dependencies, so effort can be resumed and coordinated.
- **Deliverables** — what the work is meant to produce, and the state of each.
- **References** — the external and internal sources the work draws on.
- **Provenance** — who and what created the content, from which sources, by what method, so the work can be trusted and traced.
- **Governance and classification** — the steward, promotion policy, retention, and a classification (`public`, `internal`, `confidential`, `privileged`) that travels with the package and gates how it may be handled.
- **Agent handover instructions** — explicit guidance and resume points for an agent asked to take the work forward.
- **Lifecycle state** — where the package sits in its own lifecycle (an in-progress package can be `draft`, `active`, `superseded` or `archived`; note this is the *package's* lifecycle, not the maturity of the knowledge it may later become).
- **History** — a record of the events that shaped the package, for audit and understanding.
- **Related artefacts** — links to other packages and knowledge it supersedes, is superseded by, depends on, is part of, or has been promoted to.

Not all of this is mandatory. The proposal is that the *required core* be kept minimal — enough to identify, classify, own and summarise a package — and everything else be optional, so a package can be as light as a single digest or as rich as a full programme of work. The normative division between required and optional is left to the specification.

### Human and agent interoperability and resumption

The point of this shape is interoperability across both people and agents, and across time. Because the package is self-describing and model-independent, a package created in a conversation with one assistant can be continued in a conversation with a different one; a package left by a colleague can be resumed by another; a package parked for a month can be picked up with its decisions, assumptions and open questions intact. The executive and technical digests give a human a fast way in; the handover instructions and resume points give an agent an explicit way in; the tasks, decisions and open questions tell either what remains to be done.

## How packages relate to the Knowledge Islands architecture

Knowledge Islands is an architectural kernel with domain-specific modules layered on top, drawing on a federation of subscription-native AI models routed through several execution paths, with a planner that orchestrates work and a hierarchy that improves the organisation's knowledge over time. Domain modules — for illustration only, things like a Humans Not Robots (HNR) module, an Equal Remedy (ER) module, or a Kit-Legal module — hold the specialised knowledge of a particular area. The Knowledge Package sits underneath all of this as the primitive that in-flight work is carried in.

- **The kernel** defines and understands the package primitive; every module and tool speaks it.
- **The planner and orchestration layer** produce and consume packages: a planner can emit a package describing work to be done, agents can update it as they progress, and the package is how the state of orchestrated work is handed on and resumed.
- **Kernel modules** attach their domain knowledge to packages and draw on packages relevant to their domain, without the package format needing to know anything domain-specific.
- **Knowledge promotion** is where packages meet the organisation's durable, canonical knowledge. A package is working material — the live state of a piece of thinking. Some of what a package contains will, once settled and reviewed, deserve to become canonical organisational knowledge held in a module. That transition is *promotion*, and it is deliberately a governed step with a human review point, not an automatic consequence of a package existing. Package content and promoted canonical knowledge are distinct: the package is the workbench, the promoted knowledge is what has earned a place in the organisation's retained record. The `promotedTo` relation records where package content has been elevated.

This keeps a clean separation: models are replaceable engines; packages hold the state; modules hold the domain knowledge; promotion is the governed gate between working state and retained knowledge.

## Risks and mitigations

- **Over-formalisation.** A unit that demands too much structure will not be used; people will route around it. *Mitigation:* keep the required core minimal, make almost everything optional, and let packages be as light as a single digest.
- **Stale packages.** Packages capture a moment; left untended they drift out of date and mislead. *Mitigation:* first-class lifecycle state and history, an `updated` timestamp, and `supersedes`/`supersededBy` relations so a package can be explicitly retired or replaced rather than lingering ambiguously.
- **Classification mishandling.** A portable unit that moves freely can carry confidential or privileged material across boundaries it should not. *Mitigation:* classification is a required, first-class property that travels with the package and gates handling; governance carries the steward and retention; promotion is a human-reviewed gate.
- **Adoption friction.** A new primitive competes with the path of least resistance — just talking to an assistant. *Mitigation:* make packages cheap to produce and consume, let planners and agents emit and update them automatically, and design the digests so the human cost of engaging with a package is low.

## What this proposal asks for

This proposal asks that Knowledge Islands adopt the Knowledge Package as a core primitive, and that its acceptance commission a normative specification — [KIS-0001 — Knowledge Package](../../specifications/KIS-0001-knowledge-package/) — defining the manifest, its required and optional fields, the identifier scheme, the lifecycle, the classification and governance model, the promotion relation, and the conformance criteria, together with a JSON Schema and worked examples.

See [`rationale.md`](rationale.md) for the design reasoning, [`alternatives.md`](alternatives.md) for the options considered and rejected, and [`status.md`](status.md) for status history and the questions carried into the specification.
