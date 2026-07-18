# Versioning

This section is informative.

Three distinct things carry a version number in this ecosystem, and they change for different reasons and at different rates. Keeping them distinct matters: conflating them leads to unnecessary major-version bumps in one place because of a change in another.

## (a) KIS document versions

Each KIS document carries its own semantic version, recorded in its status block (see [../specifications/KIS-0001-knowledge-package/README.md](../specifications/KIS-0001-knowledge-package/README.md)).

This version describes the specification text and the normative contract it defines:

- **Patch** — editorial changes with no effect on conformance.
- **Minor** — compatible additions, such as new optional fields.
- **Major** — breaking changes, always originating in a new KIP per [../GOVERNANCE.md](../GOVERNANCE.md).

## (b) Schema versions

The JSON Schema for a given KIS (for example [../schemas/knowledge-package.schema.json](../schemas/knowledge-package.schema.json)) carries a version as a path segment of its `$id`, for example `https://knowledgeislands.org/schemas/knowledge-package/1.0.0/knowledge-package.schema.json`.

That segment tracks the **major.minor** of the KIS it implements, not the patch: an editorial, non-conformance-affecting change to the KIS text does not require a new schema `$id`, but any minor (compatible addition) or major (breaking) change to the specification is reflected in a corresponding schema `$id` change.

The `$id` is an identifier, not a promise that the URL is resolvable; it exists so a manifest, or a tool, can state unambiguously which version of the schema it was written against.

## (c) Package versions

Each Knowledge Package carries its own semantic version inside its `id`, in the form `ki:pkg:<namespace>/<slug>@<semver>` (see the manifest specification in [../specifications/KIS-0001-knowledge-package/manifest.md](../specifications/KIS-0001-knowledge-package/manifest.md)).

This version describes the package's own content, independent of the KIS or schema version it conforms to (tracked separately by the manifest's `specVersion` field).

The same `uuid` is stable across every version of a given package; the `id`'s `@<semver>` segment changes as the package itself evolves, while `uuid` is how consumers recognise "this is a later version of the same package" rather than an unrelated one.

## Compatibility promises

| Axis                                 | What changing it promises                                                                                           |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| KIS document version (patch)         | No change in meaning; safe to re-read, nothing to re-validate                                                       |
| KIS document version (minor)         | Existing conformant packages remain conformant; new optional capability is available                                |
| KIS document version (major)         | Previously conformant packages or implementations may need changes; always via a new KIP                            |
| Schema `$id` (major.minor)           | Identifies exactly which normative contract a manifest was validated against                                        |
| Package version (`id`'s `@<semver>`) | Identifies a specific state of a specific package's content; consumers use `uuid` to track identity across versions |
