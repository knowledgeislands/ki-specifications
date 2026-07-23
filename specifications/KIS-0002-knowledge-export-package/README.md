# KIS-0002 — Knowledge Export Package

Status: Draft Version: 0.1.0 Date: 2026-07-23 Implements: [KIP-000002](../../proposals/KIP-000002-knowledge-export-package/)

KIS-0002 specifies a Knowledge Export Package (KEP): immutable, provenance-preserving source evidence emitted before knowledge extraction or Knowledge Island ingress.

This document set is normative except where marked informative. The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** follow RFC 2119 and RFC 8174.

| Document                             | Purpose                                             |
| ------------------------------------ | --------------------------------------------------- |
| [specification.md](specification.md) | Boundary, layout, immutability, and identity.       |
| [manifest.md](manifest.md)           | Normative `kep.toml` fields and checksum semantics. |
| [conformance.md](conformance.md)     | Validator requirements and the ChatGPT profile.     |
