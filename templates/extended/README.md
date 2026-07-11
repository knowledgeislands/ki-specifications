# Extended template

Targets **Extended** [conformance](../../specifications/KIS-0001-knowledge-package/conformance.md): Standard plus `constraints`, `terminology`, `deliverables`, `references`, `governance`, `history`, and `related`.

## Usage

1. Copy this directory to your new package's location and rename it to your package's slug.
2. In `manifest.json`, replace every `REPLACE-...` placeholder, the placeholder `uuid`, and the placeholder dates with real content, including `constraints`, `terminology`, `deliverables`, `references`, `governance`, `history`, and `related`.
3. Replace the placeholder text in `digest-executive.md`, `digest-technical.md`, `decisions.md`, and `handover.md`, or remove the ones you don't need along with their `digests`/`artefacts` entries in `manifest.json`.
4. Validate per [`../../tooling/README.md`](../../tooling/README.md):

   ```sh
   bun x ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d manifest.json
   ```
