# Adoption guide

This section is informative.

This guide describes how an organisation or tool adopts Knowledge Packages, without assuming any particular persistence layer, transport, or model provider.

## Pick a conformance level

Decide which conformance level fits the work at hand: `minimal`, `standard`, or `extended` (see [../specifications/KIS-0001-knowledge-package/conformance.md](../specifications/KIS-0001-knowledge-package/conformance.md) for the exact requirements of each).

A short-lived, low-stakes task may only need `minimal`; ongoing, governed work usually warrants `standard` or `extended`.

## Create a package from a template

Start from the template matching the chosen conformance level in [../templates/](../templates/), rather than writing a manifest from scratch.

Each template is a minimal, valid file set that can be copied and filled in.

## Validate

Validate the manifest against the schema before treating it as conformant; see [../tooling/README.md](../tooling/README.md) for the current validation command.

Validate again after any edit that changes required fields, adds an extension, or changes lifecycle or classification.

## Store anywhere

A Knowledge Package is a plain directory of files with a `manifest.json` at its root.

Nothing in this specification assumes GitHub, or any specific version control or file-hosting system, as the only place a package may live; a package may equally live in a database, an object store, a local filesystem, or elsewhere, provided the manifest and its referenced artefacts remain together and addressable.

Likewise, nothing assumes the Model Context Protocol (MCP) as the only transport by which a package is read or written; MCP is one convenient way to expose packages to an agent, not a requirement of the format itself.

## Handover and resumption

When a package changes hands between a human and an agent, or between two agents, populate the manifest's `handover` object with enough instructions, context, and `resumePoints` that the new owner can pick the work up without needing the previous owner's private context.

See [../specifications/KIS-0001-knowledge-package/manifest.md](../specifications/KIS-0001-knowledge-package/manifest.md) for the `handover` shape.

## Promotion into canonical knowledge

Promotion is the governed act of moving content from a package into an organisation's canonical knowledge; it is deliberately not a lifecycle state a package moves through on its own.

Treat promotion as a decision, not an automatic side effect of a package reaching `completed`: record who approved it, what was promoted, and where it landed, using the package's `governance` and `related` (relationship `promotedTo`) fields, and follow whatever governance process the adopting organisation runs for canonical knowledge.

See [../specifications/KIS-0001-knowledge-package/promotion.md](../specifications/KIS-0001-knowledge-package/promotion.md) for the normative detail.
