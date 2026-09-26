# ki-specifications

@AGENTS.md

This is the dormant pre-v1 home for a future Knowledge Islands-wide specification programme. Repository-level specifications remain local to their owning repositories until the overall Knowledge Islands v1 boundary is explicitly reviewed. Start with [README.md](README.md) for the repository map and current posture.

## Orientation

- `proposals/` — KIPs, one directory per proposal (`KIP-000001-<slug>/`); registry in `proposals/README.md`.
- `specifications/` — KIS documents, one directory per specification (`KIS-0001-<slug>/`); registry in `specifications/README.md`.
- `schemas/` — machine-readable JSON Schemas (Draft 2020-12) plus valid example manifests under `schemas/examples/`.
- `templates/`, `examples/` — conformant Knowledge Package starting points and reference packages.
- `docs/` — process, numbering, versioning, adoption, architecture context.

## Working rules

- Normative and informative text are kept explicitly separate; RFC 2119/8174 keywords (capitalised) appear only in normative text, and never in KIPs.
- One paragraph per line — never hard-wrap prose mid-sentence. Relative links only. British English (artefact, organisation). Footnote markers `†‡§¶‖`, never `*`.
- Numbers are assigned once and never reused: `KIP-NNNNNN` (6 digits), `KIS-NNNN` (4 digits), independent series — see [docs/numbering.md](docs/numbering.md).
- Any change to accepted normative content goes through a KIP; editorial fixes are patch-version errata — see [docs/versioning.md](docs/versioning.md).
- Keep the repository generic and organisation-neutral; domain modules appear only as illustrative examples in informative text.

## Validation

- Manifests against the schema: `bun x ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d <manifest>` (fallback: a small ajv script — see [tooling/README.md](tooling/README.md)).
- Repo self-audit: `ki repo audit --repo .`.
- Every JSON file must parse; every relative Markdown link must resolve; all example and template manifests must validate.
