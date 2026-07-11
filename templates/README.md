# Templates

Three starting points for a new Knowledge Package, one per [conformance level](../specifications/KIS-0001-knowledge-package/conformance.md): [`minimal/`](minimal/), [`standard/`](standard/), and [`extended/`](extended/).

Each higher template includes everything in the level below it, so `standard/` is a superset of `minimal/`, and `extended/` is a superset of `standard/`.

## Which one to start from

- **`minimal/`** — the smallest schema-valid package: just the required core fields and an executive digest. Good for a quick note or a short-lived scratch package.
- **`standard/`** — adds `decisions`, `assumptions`, `openQuestions`, `tasks`, `provenance`, `handover`, and a technical digest. The right default for ordinary in-progress work that another person or agent might need to pick up.
- **`extended/`** — adds `constraints`, `terminology`, `deliverables`, `references`, `governance`, `history`, and `related`. Use this for packages destined for promotion, long-lived reference material, or anything with material decisions and predecessor/successor relationships worth recording.

## How to use a template

1. Copy the template directory to where your new package will live, and rename it to your package's slug.
2. Open `manifest.json` and replace every placeholder value (`REPLACE-...`, the placeholder UUID, the placeholder dates) with real values for your package.

   - Set `id` to `ki:pkg:<your-namespace>/<your-slug>@<version>`, matching `version` exactly in the `@<semver>` segment.
   - Generate a fresh UUID v4 for `uuid` — it must stay stable across every future version of this package.
   - Set `created` (and, once you make a change, `updated`) to real ISO 8601 UTC timestamps.

3. Fill in the placeholder Markdown artefacts (`digest-executive.md`, and for `standard`/`extended`, `digest-technical.md`, `decisions.md`, `handover.md`) with real content, or delete the ones you don't need and remove the corresponding `digests`/`artefacts` entries from `manifest.json`.
4. Validate the manifest against the schema per [`../tooling/README.md`](../tooling/README.md):

   ```sh
   bun x ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d path/to/your-package/manifest.json
   ```

5. Once the manifest is schema-valid, check it against the checklist for your intended [conformance level](../specifications/KIS-0001-knowledge-package/conformance.md) and set `conformanceLevel` accordingly.

See [`../examples/`](../examples/) for two fully worked packages, one at Minimal and one at Extended conformance.
