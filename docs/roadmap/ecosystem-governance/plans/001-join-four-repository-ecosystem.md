---
id: '001'
title: Join the four-repository ecosystem contract
status: in-progress
roadmap: ecosystem-governance/join-the-four-repository-ecosystem-contract
blocks: —
blocked-by: —
---

## Context

KI Specifications is the normative standards and governance layer for the Knowledge Islands ecosystem. It needs to join the shared repository contract as the canonical source for formal portable specifications, schemas, templates, and conformance rules.

## Current state

The repository already defines the KIP/KIS lifecycle and identifies itself as normative, but it has no Decision Records collection or governed project roadmap beyond this new plan scaffold. Its relationship to Arcadia Principal, the harness, and the website is not yet stated.

## Steps

1. [ ] Adopt the mirrored GDR001/GDR002 foundations and add Decision Records governance to `.ki-config.toml`.
2. [ ] Add the four-repository role, working, commit, and choreography conventions to repository orientation.
3. [ ] Re-bootstrap the repository so its declared Decision Records and roadmap checkers are self-contained.
4. [ ] Run the repository audit and verify the roadmap and decision indexes.
5. [ ] Close the plan through the plan lifecycle after the unit is committed and verified.

## Files touched

- `.ki-config.toml`
- `AGENTS.md`
- `README.md`
- `docs/decisions/`
- `docs/roadmap/`
- `.ki-meta/`

## Verify

`./.ki-meta/bin/ki-audit` passes, the two foundational GDRs are indexed, and the repository's four-way role agrees with the other three mirrors.

## Dependencies / blocks

This is independently executable. The website can publish Specifications after its own vendor/publication plan consumes this repository as a source.
