# Kernel scheduling interface specification

This is the normative description of deliverable D-1, referenced from `manifest.json` (`deliverables[0].path`, `artefacts.kernel-scheduling`).

## Purpose

The kernel scheduling interface decides, for a given Knowledge Package and the kernel module handling it, which model to dispatch the work to and over which execution route.

## Inputs to a scheduling decision

- The package's `classification`, which constrains which routes and providers are permissible.
- The owning kernel module's declared model and route preferences, if any.
- The availability of each federated model (GPT, Claude, Gemini, or a local model) at dispatch time.
- Cost and latency budget carried on the task, where the module has set one.

## Execution routes

Three routes are recognised: subscription-native (a human's own model subscription drives the work interactively), API (programmatic dispatch to a provider's API), and local (a model running on infrastructure the organisation controls). A package MUST be able to move between routes across its life without losing governed context, because that context lives in the package, not in any route's session state.

## Output of a scheduling decision

A scheduling decision selects exactly one (model, route) pair for a given dispatch, and records that choice against the task in `history` once the task completes, so the choice is auditable after the fact.
