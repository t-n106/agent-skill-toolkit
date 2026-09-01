---
name: delegation-context-policy
description: >
  Conditional policy for agent delegation and context transfer. Use when one
  agent delegates to another, when choosing context inheritance, when deciding
  whether to reuse or replace an execution agent, or when lower-level delegated agents
  are introduced.
---

# Delegation and Context Policy

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

## Purpose

Use this skill only when an agent boundary is actually being created, reused, or changed.

It governs:

- execution packet construction;
- delegation granularity;
- context inheritance and isolation;
- execution-agent continuity and replacement;
- lower-level delegated-agent delegation;
- integrated-result responsibility;
- duplicated-reasoning control.

Primary principle:

> Pass the information needed to execute the decision, not the history needed to recreate the decision.

---

# 1. Delegation Boundary

Higher-level agents define the boundary. Lower-level agents execute inside it.

Use:

`higher layer defines boundary → lower layer executes`

Avoid:

`higher layer fully reasons implementation → lower layer repeats reasoning → executes`

unless independent investigation or verification was intentionally requested.

Delegation transfers work, not governing authority.

---

# 2. When Delegation Is Worthwhile

Delegate when it materially improves one or more of:

- responsibility separation;
- isolation;
- parallelism;
- specialization;
- context efficiency;
- execution cost;
- targeted verification.

Avoid delegation when coordination cost dominates the work.

Do not manufacture hierarchy for trivial work or split tightly coupled reasoning across many agents without a clear benefit.

---

# 3. Execution Packet

For non-trivial delegation, pass a bounded packet containing only what is needed.

Include, where relevant:

- **Decision** — what the parent has already established;
- **Objective** — what outcome the child agent must produce;
- **Change** — what may be changed or implemented;
- **Preserve** — what must remain intact;
- **Do not change** — what is outside the execution boundary;
- **Acceptance criteria** — observable completion conditions;
- **Stop when** — where control must return;
- **Escalate if** — what evidence requires higher-level reconsideration;
- **Established facts** — only facts required for execution;
- **Relevant artifacts** — files, specs, logs, source locations, or other necessary evidence;
- **Review focus** — only risks likely to matter later.

Do not over-specify implementation algorithms or local delegated-agent allocation unless they are actual requirements.

Do not under-specify authority, scope, or stop boundaries.

---

# 4. Context Inheritance

When the runtime can control conversational context inheritance, choose the inheritance level explicitly.

Default:

**No inheritance.** Start from fresh conversational context and provide a bounded task packet plus direct access to authoritative project artifacts.

A model change, difficult task, or already-available parent history is not by itself a reason to inherit conversation history.

## Limited inheritance

Use limited inheritance only when a small amount of recent conversation is itself task-critical and is not reasonably persisted elsewhere.

Use the smallest sufficient amount.

## Full inheritance

Full inheritance is exceptional.

Use it only when broad historical conversation is materially required and cannot reasonably be reconstructed from artifacts plus a bounded packet.

Do not use full inheritance by default, for convenience, merely because the task is complex, or because the parent failed to summarize settled decisions.

Context inheritance is not a substitute for orchestration. Runtime-specific controls belong in platform notes, not in this policy.

---

# 5. Context Efficiency

Optimize duplicated reasoning across the hierarchy, not prompt size alone.

Before delegation ask:

> What does the child agent need to execute the current decision?

Pass settled decisions, bounded requirements, necessary artifacts, necessary evidence, and execution-specific constraints.

Avoid full parent reasoning history, discarded alternatives, irrelevant previous conversation, entire project context merely to rediscover scope, adjudicated review transcripts, and artifacts already determined irrelevant.

Context isolation is both a responsibility-boundary mechanism and a resource-efficiency mechanism.

---

# 6. Parent → Execution Owner Delegation

The parent should settle decisions inside its authority before assigning meaningful execution.

The execution owner receives the execution boundary, not an unresolved parent problem the parent could have decided first.

The parent should normally avoid implementation-level over-specification.

The execution owner should retain ordinary solution authority inside the settled boundary.

The parent controls the context boundary it passes downward.

---

# 7. Execution-Agent Continuity

Within one coherent execution boundary, preserve the existing execution agent when practical.

Prefer continuation for ordinary corrections, additional implementation, additional verification, review findings, defects in the agent's previous work, and small follow-up changes inside established acceptance criteria.

Returning control does not make the execution agent disposable.

Replace it only when materially justified, for example when it is unavailable, retained context has become misleading or inefficient, the new work is a genuinely different execution boundary, isolation from prior assumptions is needed, or runtime limitations prevent continuation.

Replacement is an explicit context reset. Normally start the replacement with fresh bounded context.

---

# 8. Execution Owner → Lower-Level Delegated-Agent Delegation

Good lower-level delegated-agent tasks include isolated investigation, clearly bounded code changes, mechanical transformations, targeted tests, specialized execution subtasks, and targeted verification that does not pretend to be independent review at the decision boundary.

The execution owner remains responsible for interpreting output, reviewing changes, resolving conflicts, integration, verification, and reporting the integrated result upward.

Do not simply forward raw delegated-agent output.

Do not use lower-level delegated agents to bypass authority limits. If the execution owner lacks authority to finalize a requirement, a lower-level delegated agent also lacks that authority unless explicitly granted.

---

# 9. Lower-Level Delegated-Agent Task Packet

Provide, where relevant:

- objective;
- scope;
- constraints;
- acceptance criteria;
- established facts;
- relevant artifacts;
- expected output;
- escalation conditions;
- known authority or alignment boundaries.

Prefer direct artifact inspection over copied parent history. Use fresh bounded context by default.

---

# 10. Integrated Result

The delegating execution owner remains accountable for the integrated result.

Before returning upward, normally:

1. inspect delegated-agent outputs;
2. resolve conflicts;
3. integrate relevant changes;
4. run appropriate verification;
5. confirm the execution objective is met;
6. confirm no delegated agent crossed authority or scope boundaries.

A successful lower-level task does not automatically make the integrated result correct.

---

# 11. Anti-Duplication Rules

Treat these as delegation/context defects:

- passing full history merely for convenience;
- giving a delegated agent enough context to redo settled higher-level reasoning;
- repeatedly transferring the same large unresolved context across models;
- spawning replacement agents for ordinary corrections;
- delegating trivial work where coordination cost dominates;
- vague delegation such as "make everything consistent";
- copying complete skill text into every task packet;
- forwarding raw lower-level delegated-agent transcripts upward without integration.

Translate only applicable constraints into the bounded task packet.

---

# 12. Completion Rule

A delegation boundary is well formed when the child agent can answer:

- What outcome do I own?
- What may I change?
- What must I preserve?
- What decisions are already locked?
- What evidence proves completion?
- When must I stop and return control?

The context objective is:

**minimal but sufficient context, with no unnecessary transfer of reasoning history or authority.**
