# Tooling

There is no dedicated Knowledge Islands tooling yet.

## Validating a manifest today

Until a dedicated validator exists, validate a manifest against the schema directly with [ajv-cli](https://github.com/ajv-validator/ajv-cli):

```sh
bun x ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d <manifest>
```

The `npx` equivalent, if you are not using Bun:

```sh
npx ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d <manifest>
```

Replace `<manifest>` with the path to the `manifest.json` you want to check, for example `examples/minimal-package/manifest.json`.

## Anticipated future tooling

The following tooling is anticipated but does not exist yet:

- A dedicated validator CLI, wrapping schema validation with clearer, specification-aware error messages.
- A conformance checker, reporting which conformance level (`minimal`, `standard`, `extended`) a given package actually satisfies.
- A package scaffolder, generating a new package directory from a chosen [template](../templates/).

## Contributing tooling

Any change that is itself normative (for example, a new conformance rule the tooling would enforce) goes through a KIP per [../CONTRIBUTING.md](../CONTRIBUTING.md); the tooling that merely implements existing normative rules does not require a KIP, but is still very welcome as a pull request.
