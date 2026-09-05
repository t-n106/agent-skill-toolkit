---
name: requirements-specification
description: Make accepted intent operational as observable requirements, constraints, non-goals, and acceptance criteria. Use when material ambiguity obstructs design or execution; not to approve new scope.
---

# Requirements Specification

Apply within the user/host task boundary; this skill adds no authority. Use the current task context when no separate orchestration layer exists.

## Specify outcomes
1. Reuse the active request and authoritative artifacts. Distinguish confirmed requirements, necessary derived constraints, proposals, assumptions, and open questions. Preserve enough provenance for consequential requirements to prevent accidental invention.
2. Describe what must hold: observable behavior, inputs/outputs, invariants, constraints, non-goals, and material failure states. Prescribe a mechanism only when it is itself an established requirement.
3. Express acceptance in observable terms such as given/when/then, allowed states, preserved relationships, or genuinely required measurable bounds. Separate the success condition from the particular test implementation.
4. Resolve ambiguity from authoritative artifacts or available evidence. Leave ordinary implementation choices to execution; use `requirement-alignment-gate` only for material requirement decisions outside current authority.
5. Record useful extras as proposals rather than requirements. Do not add speculative extensibility, compatibility, UI behavior, configuration, or convenience requirements.

## Result and stopping point
Return only useful fields: objective, established requirements and source, non-goals/preserved behavior, acceptance conditions, and material proposals/open questions. Omit empty sections.

Proceed when execution can satisfy intent without inventing product decisions. Reversible choices within the authorized scope may use explicit provisional assumptions; neither an assumption nor a test may silently establish a new product requirement. Block only work that depends on unresolved authority.
