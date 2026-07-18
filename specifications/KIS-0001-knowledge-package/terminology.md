# KIS-0001 — Terminology

Status: Draft Version: 1.0.0

This document defines the terms used across the KIS-0001 document set. Definitions here are normative. The key words MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, and OPTIONAL are to be interpreted as described in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174) when, and only when, they appear in capitals.

## Core terms

**Knowledge Package** — A governed unit of cognitive work, consisting of a manifest and its associated artefacts, identified by a stable identifier and published as an immutable version. A Knowledge Package is the subject of this specification.

**Manifest** — The structured, machine-readable description of a Knowledge Package. The manifest is the authoritative record of the package's identity, state, content references, provenance, and governance. Its normative form is `manifest.json`; see [manifest.md](manifest.md).

**Artefact** — Any file that forms part of a Knowledge Package other than the manifest itself — for example a digest, a deliverable, a source document, or a handover note. Artefacts are referenced from the manifest by relative path.

**Digest** — A short summary of the package intended for a particular audience. The `executive` digest is written for a non-specialist reader; the `technical` digest is written for an implementer. A digest is either an inline `summary` or a `path` to a Markdown artefact.

**Party** — A named actor referenced by the manifest. A party has a `type` of `human`, `agent`, or `organisation`.

**Owner** — A party accountable for a Knowledge Package. A package MUST declare at least one owner.

**Steward** — A party responsible for the day-to-day care of a package on the owner's behalf, including review, promotion, and retention decisions. Stewardship is optional; see [governance.md](governance.md).

**Task** — A discrete item of work recorded in the manifest, with an identifier, a title, and a status.

**Deliverable** — A named output the package is expected to produce, optionally pointing to an artefact.

**Decision** — A recorded choice with an identifier, a title, and an optional status of `proposed`, `accepted`, or `superseded`.

**Provenance** — The record of who created the package, from what sources, and by what method; see [provenance.md](provenance.md).

**History** — The append-only sequence of events (`created`, `updated`, `promoted`, and so on) that a package has undergone.

**Handover** — The material that lets a different party — often a fresh agent — resume the work without re-deriving its context.

**Promotion** — The governed act of publishing a package's content as canonical organisational knowledge. Promotion is distinct from the lifecycle; see [promotion.md](promotion.md).

**Lifecycle** — The set of states a package moves through from `draft` to a terminal `archived` or `superseded` state; see [lifecycle.md](lifecycle.md).

**Classification** — The sensitivity label of a package: `public`, `internal`, `confidential`, or `privileged`; see [security-and-classification.md](security-and-classification.md).

**Conformance level** — The declared depth of conformance a package claims: `minimal`, `standard`, or `extended`; see [conformance.md](conformance.md).

**Extension** — Namespaced, non-standard data carried in the `extensions` object; see [extension-model.md](extension-model.md).

**Canonical knowledge** _(informative)_ — Organisational knowledge that has been accepted as authoritative, typically as the result of promotion. Its own representation is outside the scope of KIS-0001.
