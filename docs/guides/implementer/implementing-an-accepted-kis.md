# Implementing an accepted KIS

Use this guide when you are building a tool, package, or integration against a published KIS (Knowledge Islands Specification). It tells you what a specification's status and version promise, how to read it, how to check your output, and how to feed back what you learn.

## Before you start

Knowledge Islands is pre-v1, and no KIS document is currently published. The Knowledge Package schema, templates, and examples in this repository are illustrative: you can validate against them, but no specification yet makes them a conformance contract. Until a KIS is published, treat anything you build against them as an experiment that may need to change.

## 1. Check the status and version

Every KIS records its status and semantic version in the status block of its `README.md`. Read both before you build.

| Status       | What it means for you                                                                 |
| ------------ | ------------------------------------------------------------------------------------- |
| `Draft`      | Published and ready to build against, but not yet proven. Expect change.              |
| `Active`     | Proven by real implementation experience. Safe to depend on for new work.             |
| `Deprecated` | Existing conformant work stays valid, but do not start new work against it.           |
| `Superseded` | Replaced. Follow the pointer to the successor KIS.                                    |

The version tells you what can change under you. A patch change is editorial and never changes what a conformant implementation does. A minor change adds compatible material and leaves existing conformant packages valid. A major change can break conformance and always comes from a new proposal. Pin the version you implemented against and record it in your own documentation.

## 2. Read the normative text

A KIS separates normative sections, which define conformance, from informative sections, which explain and illustrate. Build only to the normative text. Capitalised requirement keywords in normative sections carry their RFC 2119 and RFC 8174 meanings; informative examples and notes never add a requirement.

Where the normative text seems to contradict an informative example, the normative text wins. Report the contradiction (see step 4).

## 3. Validate your output

Where a specification adopts the Knowledge Package schema, validate each manifest against `schemas/knowledge-package.schema.json`. With Bun:

```sh
bun x ajv-cli validate --spec=draft2020 -c ajv-formats -s schemas/knowledge-package.schema.json -d <manifest>
```

Without Bun, replace `bun x` with `npx`. Replace `<manifest>` with the path to the `manifest.json` you want to check.

This command checks the manifest against the schema, not against the whole specification: a schema-valid manifest can still break a normative rule that the schema cannot express. Check those rules by reading the normative text against your output.

To start a package rather than write one from scratch, copy the template in `templates/` that matches your conformance level (`minimal`, `standard`, or `extended`), then validate it.

## 4. Report what you learn

Implementation experience is how a `Draft` KIS becomes `Active`, so your findings matter.

- **A typo, broken link, or unclear wording that does not change meaning** - open a pull request; it is errata.
- **A rule that is ambiguous, contradictory, or impossible to implement** - open an issue naming the KIS number, its version, the section, and what you tried.
- **A working implementation** - open an issue saying what you built, which version you built against, and any structural problem you hit. Reports of no problems count as evidence too.

## Check you are done

- You recorded the KIS number and version you implemented against.
- Every manifest you produce validates against the schema.
- You checked your output against every normative rule the schema cannot express.
- Anything you could not resolve is reported as an issue.

## When things go wrong

- **Validation fails with an unknown format error.** Include `-c ajv-formats` in the command; the schema uses string formats such as dates.
- **The KIS you built against moves to a new major version.** Your implementation stays conformant to the version you pinned. Plan the upgrade from the new version's change notes rather than tracking the latest text.
- **The KIS is marked `Deprecated` or `Superseded`.** Existing conformant work remains valid; start new work against the successor.
