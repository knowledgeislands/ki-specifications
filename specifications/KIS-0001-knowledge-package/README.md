# KIS-0001 — Knowledge Package

Status: Draft
Version: 1.0.0
Date: 2026-07-11
Implements: [KIP-000001 — Knowledge Packages](../../proposals/KIP-000001-knowledge-packages/)

## Overview

KIS-0001 is the normative specification for the **Knowledge Package**: the unit in which Knowledge Islands captures, governs, and hands over cognitive work.
A Knowledge Package bundles a machine-readable manifest with its supporting artefacts so that the work — its intent, decisions, tasks, deliverables, provenance, and governance — is portable across people, agents, and models.

This document set is normative except where a section or paragraph is explicitly marked *(informative)*.
The machine-readable form of the manifest is the [JSON Schema](../../schemas/knowledge-package.schema.json); where prose and schema appear to differ, the schema governs the shape of the manifest and this specification governs its meaning.

## Document set

| Document | Purpose |
| --- | --- |
| [specification.md](specification.md) | Core normative specification: identity, versioning, artefacts, relationships, validation. |
| [terminology.md](terminology.md) | Normative definitions of the terms used throughout the set. |
| [manifest.md](manifest.md) | Field-by-field reference for the manifest, mirroring the schema. |
| [lifecycle.md](lifecycle.md) | Lifecycle states, transitions, and their rules. |
| [conformance.md](conformance.md) | The three conformance levels and how a package declares one. |
| [provenance.md](provenance.md) | Provenance and history requirements; auditability. |
| [governance.md](governance.md) | Ownership, stewardship, review, and retention. |
| [promotion.md](promotion.md) | Promotion of package content to canonical knowledge. |
| [security-and-classification.md](security-and-classification.md) | Classification levels, handling, and inheritance. |
| [extension-model.md](extension-model.md) | The `extensions` object and forward-compatibility rules. |

## Conformance summary

A conforming Knowledge Package MUST have a manifest that validates against the [schema](../../schemas/knowledge-package.schema.json) and MUST satisfy the checklist for its declared conformance level.
The three levels are **Minimal**, **Standard**, and **Extended**; see [conformance.md](conformance.md).
A package that does not declare a level is treated as **Minimal** for validation.

## Reading order

Read [terminology.md](terminology.md) first, then [specification.md](specification.md) for the core model.
Consult [manifest.md](manifest.md) alongside the [schema](../../schemas/knowledge-package.schema.json) when authoring a manifest.
The remaining documents deepen individual concerns and may be read as needed.
