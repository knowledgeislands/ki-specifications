# Technical digest

## Kernel and modules

The kernel is a small, provider-neutral core responsible for three things: scheduling work to a model and execution route, enforcing governance (classification, promotion policy, retention), and mediating the interface between kernel modules and federated models. It holds no domain knowledge of its own; all domain knowledge lives in kernel modules, each of which is a self-contained extension covering a particular class of work. This package uses Humans Not Robots, Equal Remedy, and Kit-Legal purely as illustrative module names to make the pattern concrete; none of the normative content here depends on their specifics.

## Federated execution

A task's Knowledge Package does not name a specific model. Instead the kernel's scheduling interface (`artefacts/kernel-scheduling.md`) selects a model and an execution route (subscription-native, API, or local) at dispatch time, based on the task's requirements, the classification of the package, and the routes currently available. Because the package carries its own digests, decisions, and history, a task can move from one model to another, or from one route to another, mid-life without losing governed context: the receiving model reads the package, not a prior conversation.

## Hierarchical learning

The hierarchical learning design (`artefacts/hierarchical-learning.md`) defines a three-level propagation path for lessons: task, module, kernel. A lesson learned while executing a single task is first captured against that task's package; if it generalises, it is promoted into the owning module's retained knowledge; if it generalises further still, it is promoted into the kernel itself. Promotion at each level is a governed action (see `governance.promotionPolicy`), not an automatic one, and is recorded in `history`. The open question this package has not yet resolved is how to weight two lessons that arrive from different modules at the same time and appear to conflict; T-4 exists to answer it once the federated-execution pilot (T-3) has produced enough real conflicts to reason from.

## Federated-execution pilot (T-3, in progress)

The pilot runs the same package through the Humans Not Robots and Kit-Legal modules against GPT, Claude, and a local model, comparing output quality and cost per route. Raw pilot results are held internally by the Architecture Review Board and are out of scope for this public-classification package; the summarised report will become deliverable D-3.
