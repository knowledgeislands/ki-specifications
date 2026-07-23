# KIS-0002 — Conformance

Status: Draft Version: 0.1.0

This section is normative.

A validator MUST parse `kep.toml`, verify layout, checksum ordering and digests, inventory counts, package identity, and relationship JSON. It MUST reject escaping or duplicate paths, absent references, changed bytes, and invalid JSON without mutating the package. It SHOULD report declared omissions without treating them as hidden failure.

The v0 ChatGPT connector accepts a user-prepared local capture directory. It MAY preserve project membership, message order, author role, timestamps, identifiers, attachments, generated assets, and explicit links when available.

It MUST NOT control a browser, contact ChatGPT, call an undocumented API, read profiles/cookies/tokens, discover a repository, or mutate the source session. It MUST NOT extract, summarise, deduplicate, classify, or govern knowledge.
