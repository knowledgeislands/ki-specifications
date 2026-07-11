# Standard template

Targets **Standard** [conformance](../../specifications/KIS-0001-knowledge-package/conformance.md): Minimal plus `decisions`, `assumptions`, `openQuestions`, `tasks`, `provenance`, `handover`, and a technical digest.

## Usage

1. Copy this directory to your new package's location and rename it to your package's slug.
2. In `manifest.json`, replace `REPLACE-namespace`, `REPLACE-slug`, the placeholder `uuid`, `name`, `owners`, `created`, `description`, `decisions`, `assumptions`, `openQuestions`, `tasks`, `provenance`, and `handover` with real content.
3. Replace the placeholder text in `digest-executive.md`, `digest-technical.md`, `decisions.md`, and `handover.md`, or remove the ones you don't need along with their `digests`/`artefacts` entries in `manifest.json`.
4. Validate per [`../../tooling/README.md`](../../tooling/README.md):

   ```sh
   bun x ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d manifest.json
   ```
