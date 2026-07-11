# KIS-0001 — Extension Model

Status: Draft
Version: 1.0.0

KIS-0001 defines a small, stable core and a single controlled place for non-standard data: the `extensions` object.
This lets implementers carry their own data without forking the schema, and lets the specification evolve without breaking existing packages.

## The `extensions` object

The root `extensions` object is the only place in the manifest where members outside this specification are permitted.
Everywhere else the schema sets `additionalProperties: false`, so an unrecognised member is an error.
The `extensions` object itself is open: its members are not constrained by the schema beyond being valid JSON.

## Namespacing convention

Members of `extensions` MUST be namespaced by a reverse-DNS key that the extension's author controls, for example `org.example.billing`.
This avoids collisions between independently authored extensions.
The value under a namespace key MAY be any JSON value; its internal shape is defined by the extension's author, not by this specification.

```json
"extensions": {
  "org.example.billing": { "costCentre": "CC-1234" }
}
```

## Forward-compatibility rules

A consumer MUST ignore any `extensions` member it does not understand, and MUST NOT treat an unknown member as an error.
A producer MUST NOT rely on a consumer honouring an extension; the meaning of a package MUST be complete without its extensions.
An extension MUST NOT be used to contradict or override a standard field — for example to weaken a `classification` or to record a lifecycle transition that the core forbids.

Because unknown extension members are ignored rather than rejected, adding a new extension is always backward-compatible.

## What future KIS documents may standardise *(informative)*

Extensions are a proving ground.
Data that proves broadly useful in the `extensions` space is a candidate for standardisation in a future KIS document or a later version of this schema — for example signed history events, per-artefact classification, richer task models, or promotion targets with typed metadata.
When such data is standardised, the corresponding extension namespace SHOULD be retired in favour of the standard field.
