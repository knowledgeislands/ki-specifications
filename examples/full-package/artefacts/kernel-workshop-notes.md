# Kernel architecture workshop notes, February 2026

Source material referenced from `manifest.json` (`provenance.sources[0].path`).

## Attendees

Knowledge Islands Core architecture group, including the lead architect and the steward.

## Summary

Three workshop sessions in February 2026 worked through the shape of the kernel scheduling interface and the case for a hierarchical learning loop over a flat, per-module alternative. The scheduling discussion converged on treating execution route (subscription-native, API, local) as orthogonal to model choice, so either can change independently. The learning-loop discussion produced the three-level (task, module, kernel) propagation path later written up as deliverable D-2, and identified the still-open question of how to reconcile conflicting lessons from different modules. These notes were synthesised into the kernel scheduling interface specification (D-1) and the hierarchical learning design note (D-2), then reviewed by the lead architect and the Architecture Review Board before promotion.
