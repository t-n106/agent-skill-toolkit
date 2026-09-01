---
name: planning
description: >
  Turn an established objective, requirements, and relevant design decisions
  into an executable sequence. Use when work has meaningful dependencies,
  uncertainty ordering, checkpoints, parallelism, or multiple milestones. Skip
  for straightforward single-step work.
---

# Planning

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

## Purpose

Use this skill to decide **how to sequence justified work toward an established
objective**.

Planning does not own:

- product requirement authority;
- architecture authority unless already delegated;
- execution itself;
- acceptance of unapproved scope.

A plan organizes authorized work. It must not become a mechanism for inventing
more work.

Primary rule:

> Plan only as far as needed to make the next meaningful execution safe,
> coherent, and goal-directed.

---

## 1. Plan From the Goal Backward

Start with:

- target outcome;
- acceptance criteria;
- scope and non-goals;
- locked design decisions;
- known constraints;
- current state.

Identify the minimum chain of outcomes required to reach acceptance.

Prefer outcome-oriented milestones over lists of files, classes, or tools.

---

## 2. Respect Dependency Order

Identify dependencies that materially constrain sequence.

Examples:

- requirement must be settled before design;
- provider fact must be verified before implementation depends on it;
- interface must exist before integration;
- migration preparation must precede irreversible cutover;
- test fixture or reproduction may be needed before a risky correction.

Do not serialize independent work merely because a numbered plan looks tidy.

Do not parallelize tightly coupled work when integration cost exceeds the
benefit.

---

## 3. Order Uncertainty Deliberately

When a later step depends on an uncertain fact, decide whether to resolve that
uncertainty early.

Prefer early investigation when:

- it can invalidate substantial downstream work;
- the observation is cheap and safe;
- the decision is hard to reverse;
- the uncertainty affects scope or architecture.

Defer uncertainty when:

- it does not affect the next justified step;
- evidence will become cheaper later;
- the work is easily reversible;
- resolving it now would create speculative research.

Use `problem-solving` or `research` when the uncertainty itself requires a
specialized method.

---

## 4. Prefer Vertical Progress

When practical, plan thin end-to-end slices that prove a meaningful behavior or
integration boundary.

A useful slice should answer a real question or deliver an observable outcome.

Avoid decomposing only by technical layer when that delays evidence until the
end.

However, do not force a vertical slice when the work is inherently a bounded
infrastructure or research task.

---

## 5. Put Reversible Work Before Irreversible Work

Where sequence is flexible:

1. gather cheap evidence;
2. make reversible changes;
3. verify assumptions;
4. make higher-cost or irreversible commitments only when justified.

Irreversible or destructive actions should have an explicit checkpoint when the
established authority boundary requires one.

---

## 6. Define Meaningful Checkpoints

Use checkpoints when the next stage legitimately depends on:

- user alignment;
- higher-level decision;
- external evidence;
- completion of a risky migration step;
- independent review;
- acceptance of a milestone.

A checkpoint should correspond to a real decision or evidence boundary.

Do not add gates merely to make the process look controlled.

---

## 7. Keep Tasks Executable

A task or milestone should make clear, where relevant:

- intended outcome;
- bounded scope;
- dependencies;
- acceptance evidence;
- stop condition;
- authority-sensitive uncertainty.

Avoid vague tasks such as:

- "make everything consistent";
- "finish architecture";
- "improve robustness";
- "research all edge cases".

Do not over-specify local implementation steps that belong to the execution
owner.

---

## 8. Do Not Plan Unapproved Work

Keep separate:

- committed work;
- conditional future work;
- proposals;
- possible follow-ups.

Do not pull future candidates into the current plan merely because they are
known.

A plan is not a backlog expansion mechanism.

---

## 9. Update From Evidence

A plan is provisional with respect to execution evidence.

When evidence invalidates an assumption:

- update the affected dependency or milestone;
- preserve unaffected decisions;
- avoid rebuilding the entire plan without need;
- escalate only when the new evidence changes a decision outside current
  authority.

Do not continue a stale plan merely because it was previously written down.

---

## 10. Planning Output

Prefer a compact result containing only what helps execution:

### Goal
The accepted outcome.

### Current state
Only facts needed to understand the starting point.

### Milestones / sequence
Outcome-oriented steps in dependency order.

### Verification / checkpoint
Evidence or authority boundary after consequential steps.

### Next executable unit
The smallest meaningful next unit that can proceed now.

### Deferred / unresolved
Only items that materially affect later work.

Do not create a detailed plan for steps that are both obvious and reversible.

---

## Completion Rule

Planning is sufficient when the next execution owner can start a meaningful unit
of work with dependencies, scope, and stop conditions clear enough to avoid
avoidable rework or unauthorized expansion.

The objective is:

**goal-directed sequencing with minimum necessary planning overhead.**
