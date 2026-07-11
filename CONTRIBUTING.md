# Contributing

Thank you for your interest in improving the Knowledge Islands specifications.

Every substantive change — a new foundational concept, a new specification, or a change or extension to an existing one — starts life as a **KIP** (Knowledge Islands Proposal).

Small, purely editorial fixes (typos, broken links, formatting) may be raised as an ordinary pull request against the affected file without a KIP.

## Raising a KIP

A KIP is a directory under [proposals/](proposals/) named `KIP-NNNNNN-<slug>`, containing a fixed file set.

Follow the structure established by [proposals/KIP-000001-knowledge-packages/](proposals/KIP-000001-knowledge-packages/):

| File | Purpose |
| --- | --- |
| `README.md` | Summary, status, links to the other files |
| `proposal.md` | The proposal itself: motivation, scope, the change being proposed |
| `rationale.md` | Why this approach, what problem it solves, design reasoning |
| `alternatives.md` | Alternatives considered and why they were not chosen |
| `status.md` | Status history: dates, decisions, links to discussion |

### Numbering request process

1. Open a draft pull request with your proposal directory using a placeholder number (for example `KIP-XXXXXX-your-slug`).
2. A maintainer assigns the next sequential `KIP-NNNNNN` number at draft registration and renames the directory.
3. Numbers are sequential within the KIP series, assigned only by maintainers, and are never reused, even if a KIP is later rejected or withdrawn.
4. The KIP series and the KIS series are numbered independently; a KIP number has no fixed relationship to any KIS number it later produces.

See [docs/numbering.md](docs/numbering.md) for the full numbering rules, and [docs/specification-process.md](docs/specification-process.md) for the complete lifecycle.

## Review expectations

- A KIP moves from `Draft` to `Review` once its file set is complete and it is ready for scrutiny.
- Reviewers check: is the problem real and clearly scoped, is the proposed change consistent with existing KIS documents and terminology, are alternatives fairly represented, is the change minimal and extensible rather than over-specified.
- The outcome of review is `Accepted`, `Rejected`, or `Withdrawn` by the author.
- An `Accepted` KIP is later marked `Implemented` once its corresponding KIS is published; see [GOVERNANCE.md](GOVERNANCE.md) for decision-making authority.

## Authoring rules

These apply to every document in this repository, proposals and specifications alike.

- **RFC 2119 / RFC 8174 keywords** — MUST, MUST NOT, SHOULD, SHOULD NOT, MAY (capitalised) are used only in normative text, in specification documents, and are cited once per document set as deriving their meaning from RFC 2119 and RFC 8174.
- **Normative vs informative** — every specification document clearly separates normative content from informative content, using explicit "This section is normative." / "This section is informative." markers or dedicated sections. Proposals and process documents are informative throughout unless stated otherwise.
- **Relative links only** — link to other files in this repository with relative paths; do not use bare or absolute URLs for content that lives here.
- **One paragraph per line** — never hard-wrap prose mid-sentence; each paragraph is a single line, with a blank line between paragraphs; headings, list items and table rows each sit on their own line.
- **British English** — for example "artefact", "organisation", "licence" as a noun in prose (the file itself is still named `LICENSE`).
- **Footnote markers** — where a wide table would otherwise need to be squeezed or a header abbreviated cryptically, move the detail into a footnote below the table and mark the cell with `†`, `‡`, `§`, `¶`, `‖` (doubling if more are needed). Never use `*`, which collides with Markdown emphasis.

## Questions

If you are unsure whether a change needs a KIP, open an issue describing the change and ask; a maintainer will advise.
