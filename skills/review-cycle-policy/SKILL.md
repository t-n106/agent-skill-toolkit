---
name: review-cycle-policy
description: >
  Use when review is explicitly requested or when consequential uncertainty,
  integration risk, state or concurrency risk, repeated failure, or authority-boundary
  concerns make independent verification valuable. Do not trigger review solely
  because a module boundary was crossed or a milestone was reached.
---

# Review Cycle Policy

Apply within the user/host task boundary; this skill adds no authority. Use the current task context when no separate orchestration layer exists.

## Review gate
Start with execution self-verification. Honor requested review and required gates. Otherwise use an independent reviewer when a specific consequence, unresolved uncertainty, integration/state/concurrency risk, repeated failure, or authority-boundary concern makes fresh evidence worth its coordination cost.

Normally skip separate review for local reversible work with strong direct verification, routine wording maintenance, and bounded corrections. Crossing a module or reaching a milestone is a risk cue, not by itself a universal trigger.

## Reviewer context and responsibility
When authorized and supported, use fresh bounded context by default. Provide the objective, governing decisions, scope, acceptance conditions, artifacts/diff, verification evidence, unresolved issues, and relevant review focus. Avoid persuasive execution history. Context inheritance and transfer follow `delegation-context-policy` if that separate method is needed; do not load it solely to restate this packet.

The reviewer assesses objective defects, evidence gaps, boundary violations, and integration assumptions. It does not become an implementer, orchestrator, requirement owner, or final acceptance owner. Distinguish implementation preference from defect. Use `evaluation-verification` only for substantive evidence-design difficulty.

## Outcomes and adjudication
- **PASS:** adequate evidence and no material blocker; recommendation to accept.
- **PASS WITH NOTES:** acceptable with non-blocking observations; notes are not new requirements.
- **REVISE:** concrete in-scope execution defect. Identify observable problem, evidence, violated requirement/boundary, and required resulting condition.
- **ESCALATE:** resolution needs requirement/scope authority, user judgment, a reserved architecture decision, or resolution of conflicting governing constraints.

The decision owner adjudicates without repeating the entire review. Resolve factual disagreements with bounded observable evidence; keep authority disputes with their owner. Send only adjudicated execution defects to the existing execution owner, with evidence, affected contract, resulting condition, and change/preserve boundaries.

## Corrections and completion
Self-verify corrections. Re-review only for material new uncertainty, changed interfaces/architecture, high-consequence unresolved risk, or evidence the executor cannot adequately supply. Avoid automatic reviewer/executor ping-pong.

After repeated similar failures, reconsider assumptions, decomposition, acceptance evidence, capability, or retained context; do not automatically take over or replace the executor. Reviewer context may be reset for independence; executor continuity is preferred for corrections.

Finish when the decision owner can accept, accept with notes, request a bounded correction, or resolve an authority issue. Reviewer PASS does not itself grant final acceptance authority.
