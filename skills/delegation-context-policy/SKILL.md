---
name: delegation-context-policy
description: Construct bounded task packets and manage context, continuity, and integration when authorized delegation or agent reuse is actually needed. Does not authorize delegation or prescribe a hierarchy.
---

# Delegation and Context Policy

Apply within the user/host task boundary; this skill adds no authority. Use the current task context when no separate orchestration layer exists.

## Boundary and packet
Delegate only when permitted and the benefit in isolation, parallelism, specialization, or cost exceeds coordination overhead. Settle decisions owned by the parent; leave local solution reasoning to the execution owner. A bounded investigation may legitimately delegate an unresolved factual question.

For any delegation depth, provide only relevant fields:
- objective and expected result;
- settled decisions and established facts;
- change / preserve / do-not-change scope, including file ownership when agents share a workspace;
- authoritative artifacts accessible to the child;
- observable acceptance evidence;
- stop and escalation conditions.

Do not copy full skills, discarded reasoning, or review transcripts into packets. Reference available skills only when applicable; include essential constraints when the child cannot access the source. Do not delegate trivial work or fully solve an implementation merely to have a child repeat it.

## Context and continuity
When supported, explicitly choose no conversational inheritance by default: a fresh context with a sufficient packet and artifacts. Use limited history when recent conversation itself is necessary; full history only when broad task-critical context cannot reasonably be reconstructed. Follow the actual runtime schema and constraints.

Retain the execution owner for ordinary corrections, follow-up implementation, and verification within one coherent boundary. Replace it only for unavailability, misleading/inefficient context, a genuinely different task, required isolation, or runtime limits. Replacement is an explicit context reset with a fresh packet.

## Coordination and integration
While a worker runs, do useful independent work or use runtime-supported completion notifications/blocking waits. Check status when it can change an action: a blocker, decision deadline, expected checkpoint, or suspected failure. Avoid repeated no-change polling; follow host timing limits and do not invent unsupported timeout controls.

The delegating owner inspects results, resolves conflicts, integrates changes, verifies affected boundaries, and reports the integrated outcome. A child success is not integration evidence. Lower-level delegation never enlarges authority or automatically constitutes independent review.

Finish the handoff when the child knows its outcome, permitted changes, protected decisions, evidence, and return conditions. Finish the parent task only after appropriate integration or an explicit blocker handoff.
