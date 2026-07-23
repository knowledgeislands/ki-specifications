# KIP-000002 — Rationale

Acquisition needs fidelity and provenance; extraction needs interpretation; governed ingress needs policy. A KEP keeps those responsibilities separate, so an acquired source record cannot silently become purported organisational knowledge.

The canonical v0 encoding is a directory so it is inspectable, preserves asset bytes, and has a stable payload identity. Archives may become a transport encoding later, but are not an alternate payload identity.
