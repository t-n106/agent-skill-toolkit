---
name: solution-design
description: >
  Convert established requirements and constraints into a smallest-sufficient
  solution structure. Use when multiple plausible structures, interfaces,
  boundaries, data flows, or architectural choices materially affect the
  outcome. Do not use for obvious local implementation choices.
---

# Solution Design

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

## Purpose

Use this skill to decide **how an established requirement should be structured**
before detailed execution when the structural choice materially matters.

This skill owns design method, not requirement authority, task authority, or
implementation ownership.

It does not authorize:

- adding product requirements;
- expanding scope for elegance or future-proofing;
- producing a framework merely because reuse is possible;
- turning a reversible implementation choice into a mandatory architecture;
- replacing planning or execution with design documentation.

Primary rule:

> Design from required properties and constraints, then choose the smallest
> structure that satisfies them with acceptable risk.

---

## 1. Start From Established Inputs

Before designing, identify only what materially constrains the solution:

- objective;
- confirmed requirements;
- non-goals;
- protected contracts;
- relevant existing system boundaries;
- operational or safety constraints;
- acceptance criteria;
- known environmental constraints.

Do not rediscover or redefine requirements inside design.

If a structural decision depends on unresolved product intent, use the established
requirement authority path instead of deciding it as architecture.

---

## 2. Separate Required Properties From Chosen Mechanisms

For each important design choice ask:

> What property must the solution provide?

Then distinguish that property from one possible mechanism.

Examples:

- requirement: stale work must not overwrite newer user intent;
- mechanism candidates: generation token, cancellation, identity check,
  serialized queue.

Do not freeze a mechanism merely because it is the first plausible one.

Conversely, do not generate alternatives when the mechanism is already fixed by
an authoritative contract or the choice is trivial.

---

## 3. Identify Real Design Boundaries

Design only the boundaries that materially affect correctness, ownership,
change isolation, or integration.

Possible boundaries include:

- module or component responsibility;
- input/output contract;
- state ownership;
- process or service boundary;
- data transformation boundary;
- failure boundary;
- external-provider boundary;
- persistence boundary;
- user-visible vs internal representation.

Avoid inventing boundaries solely to make a diagram symmetrical or to prepare
for hypothetical future features.

---

## 4. Compare Alternatives Only When the Choice Matters

Generate alternatives when:

- more than one credible structure exists;
- the choice has meaningful consequences;
- evidence or trade-offs can distinguish them.

Compare only on relevant dimensions, such as:

- requirement fit;
- correctness risk;
- reversibility;
- coupling;
- operational complexity;
- verification difficulty;
- migration cost;
- performance or resource constraints when material.

Do not create a long option matrix for a locally obvious choice.

---

## 5. Prefer Reversible Commitments

When two designs satisfy current requirements similarly, prefer the choice that
preserves future correction at lower cost.

Delay irreversible commitments when important evidence is still missing.

However, do not add abstraction solely to preserve every possible future
option. Reversibility must have a realistic expected value.

---

## 6. Use the Smallest Sufficient Architecture

Prefer the least structural complexity that fully satisfies current approved
requirements and known constraints.

Treat these as warning signs:

- generic framework before a second real use case exists;
- plugin architecture for hypothetical extensibility;
- shared abstraction whose consumers need materially different semantics;
- infrastructure introduced only to support a future possibility;
- duplicated compatibility layers with no current migration need;
- extensive defensive machinery unrelated to observed risk.

When an applicable anti-overengineering or scope policy exists, it constrains this
skill.

Do not interpret "smallest sufficient" as "smallest diff". A slightly broader
change may be necessary to create the correct responsibility boundary.

---

## 7. Design for Evidence

A design should make important correctness properties observable where
practical.

Consider:

- where failures become visible;
- what state can be inspected;
- how boundaries can be tested;
- whether critical behavior can be reproduced;
- whether the chosen structure hides ambiguity or failure.

Do not build observability infrastructure beyond the risk and scope of the
current problem.

---

## 8. Preserve Open Decisions

When evidence is insufficient for a design choice:

- identify the unresolved assumption;
- determine the cheapest useful evidence;
- defer the choice if practical;
- use a reversible temporary structure only when justified;
- escalate if the choice exceeds current authority.

Do not convert "we need to choose something" into false certainty.

---

## 9. Design Output

A useful design result is normally compact:

### Chosen structure
The responsibilities and boundaries that materially matter.

### Key decisions
Only consequential design decisions.

### Rationale
Why the structure fits the requirements and constraints.

### Interfaces / invariants
Only contracts needed for execution or verification.

### Rejected alternatives
Only when understanding the trade-off prevents future re-litigation.

### Open assumptions
Only material unresolved design uncertainty.

Do not produce architecture documentation whose detail exceeds execution need.

---

## Completion Rule

Design is sufficient when the execution owner can implement the approved
requirements without needing to rediscover consequential structural decisions,
while local implementation freedom remains open.

The objective is:

**a smallest-sufficient, requirement-driven structure with explicit boundaries
and no speculative architecture.**
