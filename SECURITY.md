# Security policy

This repository holds specifications, schemas, governance documents and reference examples. It contains no runtime code and is not deployed anywhere.

## Scope

The following are in scope for a security report:

- Flaws in a schema (for example [schemas/knowledge-package.schema.json](schemas/knowledge-package.schema.json)) that would allow a manifest with security-relevant consequences to validate when it should not — for example a classification or privilege field that can be omitted, spoofed, or misinterpreted due to an ambiguous or incorrect schema constraint.
- Ambiguities in specification text that could lead implementers to mishandle classification, privilege, or access-control-relevant fields in a Knowledge Package.

The following are out of scope, because this repository does not contain them:

- Vulnerabilities in any implementation, tool, or service that consumes these specifications or schemas (report those to the relevant implementation's own repository).
- General documentation errors with no security consequence (raise these as ordinary issues or pull requests per [CONTRIBUTING.md](CONTRIBUTING.md)).

## Reporting

Please report suspected security issues privately, using [GitHub security advisories](https://github.com/knowledgeislands/ki-specifications/security/advisories/new) on `knowledgeislands/ki-specifications`, rather than a public issue.

We will acknowledge reports and work with you on disclosure timing once a fix or specification clarification is agreed.

## Bounty

No bounty is offered for security reports against this repository.
