# KIS-0002 — Manifest reference

Status: Draft Version: 0.1.0

This section is normative.

```toml
format = "kep"
format_version = "0.1.0"
package_id = "kep:sha256:<payload-sha256>"
payload_sha256 = "<payload-sha256>"
omissions = []
normalisations = []
checksum_manifest = "checksums/sha256sums.txt"

[connector]
id = "<stable connector identifier>"
version = "<connector version>"
mode = "user-assisted"

[source]
system = "<source system>"
capture_boundary = "<bounded selection>"

[inventory]
records = 0
assets = 0
relationships = 0
```

The manifest MUST be UTF-8 TOML. It MUST NOT contain secrets, cookies, browser-profile paths, resumable state, or a non-deterministic generation timestamp. Inventory counts MUST match the payload. Omission and normalisation arrays MUST truthfully describe incomplete capture or intentional change.
