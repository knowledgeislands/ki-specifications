# Numbering

This section is informative.

## KIP numbers

KIPs are numbered `KIP-NNNNNN`, a six-digit, zero-padded, sequential number, for example `KIP-000001`.

## KIS numbers

KIS documents are numbered `KIS-NNNN`, a four-digit, zero-padded, sequential number, for example `KIS-0001`.

## Assignment

- Numbers are assigned by maintainers, at the point a KIP or KIS is registered in draft (see [specification-process.md](specification-process.md)).
- Numbers are sequential within their own series, starting from `1`.
- Numbers are never reused, even if the KIP is later rejected or withdrawn, or the KIS is later superseded.
- The KIP series and the KIS series are numbered independently of one another; a KIP's number has no fixed relationship to the number of any KIS it produces.

## Directory naming

Each KIP and KIS is a directory named `<number>-<slug>`, where `<slug>` is a short, kebab-case, human-readable description of the subject:

- `proposals/KIP-000001-knowledge-packages/`
- `specifications/KIS-0001-knowledge-package/`

The slug is chosen at registration and, once published, is not renamed even if the document's title later changes, since existing links and references depend on it.
