# Handover

Prose expansion of the `handover` object in `manifest.json`: what the pilot team needs to know to resume this package.

## Context

The kernel scheduling interface (T-1, deliverable D-1) and the hierarchical learning design (T-2, deliverable D-2) are both complete and have been promoted to canonical knowledge by the Architecture Review Board (see `history`). The federated-execution pilot (T-3) is in progress: the Humans Not Robots and Kit-Legal modules are being run against GPT, Claude, and a local model on matched tasks, comparing output quality and cost per route. Raw pilot results are held internally by the Architecture Review Board; only the summarised report becomes part of this package, as deliverable D-3.

## Resume points

- Finish T-3: complete the federated-execution pilot and write up D-3, the pilot report comparing quality and cost across GPT, Claude, and a local model for the two piloted modules.
- Start T-4 once T-3 has produced enough real cases: write the model-route fallback policy, using the pilot's observed failures and near-misses to decide what happens when a preferred route is unavailable mid-task.
- Resolve the open question on how the hierarchical learning loop should weight two conflicting lessons arriving from different modules at the same time; the pilot is expected to surface at least one real instance of this.
- Any promotion of pilot findings into canonical knowledge requires Architecture Review Board sign-off per `governance.promotionPolicy`, the same as for D-1 and D-2.
