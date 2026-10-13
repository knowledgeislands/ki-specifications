---
id: KI-SPEC-KIN-003
area: KIN
title: Portable live-artifact contract
status: triage
blocks: []
blocked_by: []
baseline_ref: null
created_at: 2026-10-13T04:20:57Z
updated_at: 2026-10-13T04:20:57Z
---

## Goal

KI Specifications holds one portable contract for Knowledge Base live artifacts. A live artifact is a self-contained HTML page with a Markdown manifest that runs unchanged in Cowork, the Knowledge Islands Observatory, and any MCP Apps host. The contract states the manifest fields, the page-facing `window.cowork` subset, the bridge version, and what a host must refuse.

## Context

`apps-observatory` now hosts the estate's Cowork live artifacts. It serves the page unchanged with a bridge script that provides `window.cowork` over the MCP Apps (SEP-1865) `postMessage` JSON-RPC wire. It frames the page in an opaque-origin sandbox and answers only the read tools the manifest declares. The working contract lives in that repository's decision record `docs/decisions/PDR-KI-OBSERVA-006-live-artifacts-speak-the-mcp-apps-bridge.md`, its specification area `docs/specs/artifacts.md`, and its operator guide `docs/guides/operator/open-a-live-artifact.md`. Kris decided on 2026-10-13 that the contract will live here later, and that delivery in the Observatory would not wait for it.

The working contract today:

- **Pair.** A tracked Markdown and HTML pair of the same name directly under a Knowledge Base's `Admin/Operations/Live Artifacts/`.
- **Manifest.** Frontmatter `artifact_bridge: 1`, `artifact_id`, an `artifact_tools` list of `mcp__<server>__<tool>` names, and an optional `artifact_servers` list of `alias=server` mappings. A pair without a readable manifest is refused by name and reason.
- **Page surface.** `window.cowork.callMcpTool(name, args)`, plus `askClaude` and `runScheduledTask`, which a host without them rejects with a typed unavailable error (code `-32002`).
- **Wire.** MCP Apps `ui/initialize`, `ui/notifications/initialized`, and `tools/call`. A refusal is a JSON-RPC error (code `-32001`) and never an empty answer.

`hnr-principal` and `legal-principal` carry the first two manifests.

This does not block work in `apps-observatory`, which keeps the working contract until a contract here supersedes it.

## Boundary

- Capture only. Nothing here is adopted, planned, or specified until Kris adopts it.
- The repository is dormant while Knowledge Islands is at v0.x, so adoption waits on the v1 boundary review or Kris restarting the specification effort.
- The contract would state portable behaviour only. Each host's isolation, caching, and native answering stay in that host's own specification.
- No edit in `apps-observatory`, `hnr-principal`, `legal-principal`, or any other repository.

## Discussion

The nearest fixed issuing area is `KIN`, the protocol-assessment area. The contract is a protocol for presenting Knowledge Base content rather than ingesting it, so adoption may prefer a new area. The identifier stays as issued.

Open questions for shaping:

- Whether the portable contract is a KIS in its own right or a profile of MCP Apps.
- How the bridge version evolves.
- Whether `artifact_tools` should name tools by server or by capability.
- Whether ChatGPT publication as a `ui://` resource belongs in the same contract.
