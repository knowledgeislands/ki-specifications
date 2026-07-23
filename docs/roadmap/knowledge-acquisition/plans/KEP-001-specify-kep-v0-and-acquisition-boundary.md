---
id: 'KEP-001'
title: Specify Knowledge Export Package v0 and the acquisition boundary
status: in-progress
roadmap: knowledge-acquisition/specify-knowledge-export-package-v0-and-the-acquisition-boundary
blocks: —
blocked-by: —
---

## Context

The KI Agentic Harness GOV-001 handoff establishes a lifecycle in which KAF preserves source evidence in a Knowledge Export Package (KEP), KBEP extracts reusable knowledge, and KBIP governs ingress. This repository owns the portable normative KEP and KAF contracts that an implementation may claim to follow.

The first consumer is the planned `ki acquire chatgpt import` command in `knowledgeislands/tools-ki`. It must not decide the KEP format independently.

## Current state

The repository has existing knowledge-package proposals and specifications, but no adopted KEP v0 contract for source-system acquisition. The harness supplied an implementation-ready brief; it is input, not a normative specification.

## Steps

1. Map the proposed KEP lifecycle onto the existing KIP/KIS vocabulary and decide the canonical specification identifier, publication location, and conformance relationship.
2. Specify the KEP v0 directory payload, manifest fields, content-derived identity, provenance, record inventory, asset inventory, native relationships, omissions, and checksum contract.
3. Define deterministic generation and validation requirements, including immutable payload boundaries and the exclusion of checkpoints, browser state, credentials, caches, and logs.
4. Define the KAF connector boundary and the user-assisted ChatGPT import profile without specifying browser automation, APIs, authenticated scraping, extraction, or ingress.
5. Publish conformance fixtures and a validator-oriented error model sufficient for a separate `tools-ki` implementation to prove a KEP is complete or explain its omissions.
6. Link the KEP to the downstream KBEP and KBIP boundaries, preserving upstream lineage and naming deferred schema decisions explicitly.
7. Run the repository's documentation, specification, roadmap, and link checks; prepare this plan for manual acceptance.

## Files touched

- the adopted KEP/KAF specification and its index or proposal material
- conformance fixtures and validation documentation
- `docs/roadmap/knowledge-acquisition/ROADMAP.md` and this plan

## Verify

1. The published contract distinguishes KAF acquisition, immutable KEP evidence, KBEP extraction, and KBIP ingress without overlapping responsibilities.
2. A conforming implementation can deterministically validate records, assets, relationships, omissions, and checksums without access to the original source system.
3. The ChatGPT profile uses only user-provided local material and excludes credentials, browser control, network access, and inferred knowledge relationships.
4. The examples and fixture vocabulary are sufficient for the `tools-ki` acquisition plan to implement its output without recreating the format design.
5. Relevant repository checks pass.

## Dependencies / blocks

Origin: `ki-agentic-harness` GOV-001, recorded done. This plan is a genuine prerequisite for the acquisition output contract in `tools-ki`; the receiving repository owns its own plan and schedule.
