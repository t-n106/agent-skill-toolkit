---
name: solution-design
description: Choose the smallest sufficient structure when consequential responsibilities, interfaces, state ownership, or architectural alternatives need resolution. Skip obvious local implementation choices.
---

# Solution Design

Apply within the user/host task boundary; this skill adds no authority. Use the current task context when no separate orchestration layer exists.

## Design method
1. Start from established outcomes, constraints, protected contracts, non-goals, acceptance conditions, and relevant existing boundaries. Do not rediscover settled intent.
2. Separate the required property from a candidate mechanism. For example, preventing stale results from overwriting current intent does not by itself require a particular cancellation or serialization mechanism.
3. Define only boundaries that affect correctness, ownership, change isolation, or integration: responsibilities, state, data flow, persistence, failures, or external interfaces.
4. Compare credible alternatives only when trade-offs matter. Use requirement fit, risk, coupling, reversibility, operational complexity, verification, migration cost, or resource limits as relevant.
5. Choose the least complexity that fully satisfies current requirements. Minimum sufficient structure is not necessarily the smallest diff. Avoid hypothetical frameworks, plugin systems, compatibility layers, or abstractions without current need.
6. Make important correctness properties observable without building disproportionate infrastructure. For unresolved assumptions, seek cheap evidence, defer the choice, or use a reversible in-scope provisional choice. Route genuine product decisions to the requirement authority.

## Result
Return consequential responsibilities, interfaces/invariants, decisions and rationale, plus only material open assumptions or rejected alternatives that prevent re-litigation. Stop when execution can begin without rediscovering major structural decisions; preserve local implementation freedom.

An applicable scope policy constrains design; this skill is not permission to add requirements or turn every implementation choice into architecture documentation.
