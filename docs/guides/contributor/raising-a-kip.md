# Raising a KIP

Use this guide to take a new proposal from an idea to a maintainer decision. A KIP (Knowledge Islands Proposal) is the deliberative record of what was proposed, why, and how it was decided; an accepted KIP is the mandate to draft a KIS (Knowledge Islands Specification).

## Before you start

Knowledge Islands is pre-v1. Until the overall v1 boundary has been reviewed, this repository registers no new KIPs, and a proposal opened now will not be numbered. If you have an ecosystem-wide concern today, open an issue instead; [Deciding whether a change needs a KIP](deciding-whether-a-change-needs-a-kip.md) explains what to do with it. The steps below describe the process once the programme is active.

Confirm the change really needs a KIP. Editorial fixes and compatible additions to an existing KIS do not; the deciding guide covers those routes.

## The lifecycle at a glance

```text
Draft -> Review -> Accepted -> Implemented -> Superseded
                -> Rejected
Draft or Review -> Withdrawn
```

`Rejected` and `Withdrawn` proposals stay in the repository as a permanent record, and their numbers are never reused. A KIP becomes `Implemented` once the KIS it mandated has been published.

## 1. Prepare the proposal directory

Create a directory under `proposals/` with a placeholder number and a short kebab-case slug, for example `proposals/KIP-XXXXXX-your-slug/`. Choose the slug with care: once the KIP is published the slug is not renamed, even if the title changes.

Add the file set:

| File              | What it holds                                                     |
| ----------------- | ----------------------------------------------------------------- |
| `README.md`       | Summary, status, and links to the other files                     |
| `proposal.md`     | The proposal itself: motivation, scope, and the change proposed   |
| `rationale.md`    | Why this approach, what problem it solves, and the design reasoning |
| `alternatives.md` | Alternatives considered and why they were not chosen              |
| `status.md`       | Status history: dates, decisions, and links to discussion         |

Write the proposal as informative text throughout. Capitalised requirement keywords belong only in the normative sections of a KIS, never in a KIP. Follow the repository's authoring rules: one paragraph per line, relative links for content in this repository, and British English.

## 2. Obtain a number

1. Open a draft pull request containing the proposal directory under its placeholder number.
2. A maintainer assigns the next sequential six-digit number, for example `KIP-000001`, and renames the directory. The KIP is now `Draft`.
3. Do not choose a number yourself. Numbers are assigned only by maintainers, are sequential within the KIP series, and are independent of the KIS series.

## 3. Take it through review

1. When the file set is complete and ready for scrutiny, record the move to `Review` in `status.md`.
2. Reviewers ask whether the problem is real and clearly scoped, whether the change is consistent with existing KIS documents and terminology, whether the alternatives are fairly represented, and whether the change is minimal and extensible rather than over-specified.
3. Revise `proposal.md`, `rationale.md`, or `alternatives.md` in response, and record each round in `status.md`. A KIP may cycle through review as often as needed.

## 4. Reach a decision

A maintainer records the outcome and its date in `status.md`:

- `Accepted` - the KIP proceeds and becomes the mandate to draft a KIS. A maintainer assigns the KIS number and the KIS is published at `Draft`; the KIP is then marked `Implemented`.
- `Rejected` - the KIP does not proceed. Its directory stays as the record.
- `Withdrawn` - you may withdraw your own KIP at any point before acceptance.

## Check you are done

- The directory carries its assigned number and the full five-file set.
- `status.md` records every state change with a date and a link to the discussion.
- Every relative link in the proposal resolves.

## When things go wrong

- **The pull request has no number after review starts.** Ask the maintainer on the pull request; do not renumber it yourself.
- **Review shows the change is really editorial or a compatible addition.** Withdraw the KIP and take the route the deciding guide describes.
- **Your proposal overlaps another open KIP.** Say so in `alternatives.md` and link the other proposal; a maintainer decides whether to merge, sequence, or reject one of them.

## Where the rules live

`CONTRIBUTING.md` is the authority for the KIP file set and the numbering request steps, `GOVERNANCE.md` for who decides, `docs/numbering.md` for numbering, and `docs/specification-process.md` for the full lifecycle. If this guide and those documents disagree, they win.
