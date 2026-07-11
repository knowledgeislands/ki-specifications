# Minimal template

Targets **Minimal** [conformance](../../specifications/KIS-0001-knowledge-package/conformance.md): the required core fields and an executive digest, nothing more.

## Usage

1. Copy this directory to your new package's location and rename it to your package's slug.
2. In `manifest.json`, replace `REPLACE-namespace`, `REPLACE-slug`, the placeholder `uuid`, `name`, `owners`, `created`, and the `digests.executive` values with real content.
3. Replace the placeholder text in `digest-executive.md`.
4. Validate per [`../../tooling/README.md`](../../tooling/README.md):

   ```sh
   bun x ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d manifest.json
   ```
