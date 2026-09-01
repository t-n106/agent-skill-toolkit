# Minimal Routing / Orchestration Example

This toolkit does not prescribe a specific routing or orchestration architecture. Skills may be invoked directly, or a host environment may use a thin routing / orchestration layer to recognize when a conditional skill is required.

## Task-boundary fallback

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This makes the skills usable both with and without a dedicated routing/orchestration layer. A routing layer may select skills, but it is not required merely to establish a usable task boundary.

## Minimal rule

> Before substantial work, identify whether any conditional skill's trigger is materially present. Load only those skills. Do not load the full toolkit by default.

## Example routing table

| Situation | Load |
|---|---|
| Creating/reusing an agent boundary or transferring context | `delegation-context-policy` |
| Product intent, user-visible behavior, or requirement approval is unresolved | `requirement-alignment-gate` |
| Independent review has material verification value | `review-cycle-policy` |
| Accepted intent is not operational enough to implement or evaluate | `requirements-specification` |
| Multiple consequential structures or boundaries are plausible | `solution-design` |
| Meaningful dependency, ordering, checkpoint, or parallelism problem exists | `planning` |
| Source-sensitive or current facts are missing | `research` |
| Evidence exists but requires comparison, interpretation, or robustness analysis | `analysis` |
| Findings must become a recommendation or choice | `synthesis-decision` |
| Success/failure evidence or claim strength is non-trivial | `evaluation-verification` |
| The path is unclear because material uncertainty remains | `problem-solving` |
| Software behavior is wrong and the cause is not established | `debugging` |

## Example thin routing layer

```text
Keep role identity, authority, scope, and stop conditions in the host environment.

Before substantial work:
1. classify the current responsibility and authority boundary;
2. inspect the routing table;
3. load only the conditional skills whose triggers materially apply;
4. perform the work under those skills;
5. re-check routing when the task state materially changes.

Do not treat a loaded method as additional authority.
Do not load every method as a checklist.
```

## Direct skill use

A routing layer is optional. If a user or host application already knows which capability is needed, it may invoke that skill directly.

Examples:

- source-sensitive fact gathering → `research`
- interpreting collected evidence → `analysis`
- diagnosing an unclear software failure → `debugging`
- turning accepted intent into operational requirements → `requirements-specification`

## Important

A routing layer should recognize triggers without already needing the target skill. If a trigger cannot be described outside the skill, the boundary is probably too circular or too fine-grained.
