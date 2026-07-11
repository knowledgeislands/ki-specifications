# Architecture context

This document is informative throughout.

This document describes where Knowledge Packages sit within the wider Knowledge Islands architecture, so that the specifications in this repository can be read with the right mental model, without this repository itself depending on, or normatively defining, that wider architecture.

## The kernel and its modules

Knowledge Islands is built around a stable, open-source kernel: a small, generic set of concepts and mechanisms (of which the Knowledge Package is one) for governed human and AI knowledge work.

Around that kernel, organisations build domain-specific kernel modules that encode their own knowledge, process, and judgement.

Humans Not Robots, Equal Remedy and Kit-Legal are used here purely as illustrative examples of the kind of organisation-specific module the kernel supports; this repository defines the kernel-level specifications and stays organisation-neutral, naming no module as privileged or required.

Future organisation-specific modules are expected to follow the same pattern: proprietary domain knowledge, built on the open kernel, without needing to fork or duplicate it.

## Federated execution

Knowledge Islands work is executed across multiple, federated execution environments: GPT, Claude, Gemini, and local models, among others.

Execution routes are similarly plural: subscription-native access, direct API access, and fully local execution are all supported, not treated as alternatives to be chosen once and locked in.

## Models as replaceable execution engines

A recurring architectural principle is that the model is a replaceable execution engine, not the place where organisational learning lives.

Organisational learning — what was decided, why, what was tried and rejected, what the organisation now knows — is retained in the Knowledge Islands kernel and its modules, and in the Knowledge Packages that carry work between people, agents, and models, rather than in any one model's own memory or fine-tuning.

This is what makes the package the durable shared state of the system: a package outlives any single execution session or any single model, and can be picked up by a different human, agent, or model without losing context (see [adoption-guide.md](adoption-guide.md) for handover and resumption).

## Hierarchical continual improvement

Improvement in this architecture is intended to happen hierarchically: individual packages accumulate decisions, tasks and provenance; useful, validated content from packages is promoted into canonical organisational knowledge (see [../specifications/KIS-0001-knowledge-package/promotion.md](../specifications/KIS-0001-knowledge-package/promotion.md)); and canonical knowledge in turn shapes kernel modules and, over time, the kernel itself, through the normal KIP process described in [specification-process.md](specification-process.md).

## Licensing note

The kernel is open source; the specifications, schemas and governance in this repository are part of that open kernel and remain the intellectual property of Kit.

Organisations are expected to build proprietary kernel modules around the open kernel, under their own licensing terms, for their own domain knowledge.

This repository itself makes no organisation-specific claims and defines no module; it is limited to the generic, kernel-level standards that any module or execution environment can build against.
