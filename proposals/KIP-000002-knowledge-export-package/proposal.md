# KIP-000002 — Introduce the Knowledge Export Package

- Status: Accepted
- Created: 2026-07-23
- Accepted: 2026-07-23
- Implemented by: [KIS-0002](../../specifications/KIS-0002-knowledge-export-package/)

## Proposal

Adopt the Knowledge Export Package (KEP) as an immutable, fidelity-preserving directory package emitted by a Knowledge Acquisition Framework connector before knowledge extraction or Knowledge Island ingress.

A KEP carries a TOML manifest, unchanged originals, readable source records, byte-preserved assets, source-native relationships, checksum evidence, and declared omissions. It excludes credentials, browser state, checkpoints, logs, inferred relationships, extracted knowledge, and governance decisions.

The first connector profile is a local, user-assisted ChatGPT capture import. It consumes only material the user already obtained; it does not control a browser, contact a source API, or access authentication material.

This proposal commissions [KIS-0002](../../specifications/KIS-0002-knowledge-export-package/). It does not specify the CLI implementation, browser automation, KBEP extraction, or KBIP ingress.
