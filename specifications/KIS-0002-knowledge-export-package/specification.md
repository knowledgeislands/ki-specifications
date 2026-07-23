# KIS-0002 — Core specification

Status: Draft Version: 0.1.0

This section is normative.

## Boundary

A Knowledge Acquisition Framework connector MUST emit a KEP before a Knowledge Base Extraction Protocol process interprets source material. A KEP MUST NOT contain extracted knowledge, semantic classifications, deduplicated concepts, Knowledge Base governance, or publication decisions. Downstream consumers MUST retain lineage to the KEP.

## Canonical layout

```text
kep/
├── kep.toml
├── source/
│   ├── originals/
│   └── records/
├── assets/
├── relationships/native.jsonl
└── checksums/sha256sums.txt
```

Originals are unchanged user-provided exports; records preserve available source identifiers, roles, order, timestamps, and links; assets preserve original bytes; relationships contain only source-native evidence. Empty directories MAY be absent.

## Immutability and identity

An emitted KEP is immutable. Checkpoints, browser state, credentials, caches, and logs MUST remain outside it. A changed capture boundary produces a new KEP.

`checksums/sha256sums.txt` MUST list every payload file except itself and `kep.toml`, in lexicographic path order with LF line endings. `payload_sha256` is the SHA-256 digest of those checksum bytes; `package_id` MUST equal `kep:sha256:<payload-sha256>`. Identical normalised source inputs, connector version, and capture boundary MUST produce identical payload paths, relationship order, checksum bytes, and identity.
