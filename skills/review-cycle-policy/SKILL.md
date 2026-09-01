---
name: review-cycle-policy
description: >
  Conditional independent-review policy. Load after execution self-verification
  when consequence, uncertainty, boundary risk, or verification value justifies
  a fresh reviewer. Defines reviewer context, outcomes, adjudication, correction,
  and re-review rules without assuming a specific agent hierarchy.
---

# Review Cycle Policy

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

## Purpose

Independent review is conditional, not automatic.

Use this skill only after execution has produced a self-verified integrated result and the decision owner determines that an independent perspective may add material value.

Primary flow:

`execution self-verification → review gate → independent reviewer when justified → decision-owner adjudication`

For correctable defects:

`review finding → adjudication → existing execution owner correction → self-verification`

Re-review is conditional.

This policy decides **whether and how an independent reviewer is used**. When review itself requires non-trivial evidence design or interpretation, the reviewer may use `evaluation-verification`; that method does not decide whether an independent reviewer should exist.

---

# 1. Review Trigger

Invoke an independent reviewer when one or more materially apply:

- change crosses modules, interfaces, or system boundaries;
- failure could cause high-consequence effects;
- correctness depends on state transitions, concurrency, asynchronous behavior, API boundaries, or integration assumptions;
- the execution owner reports material uncertainty or weak verification;
- previous attempts failed in a way that benefits from a fresh perspective;
- a milestone or final integrated deliverable benefits from independent evidence;
- the decision owner identifies a specific review-sensitive risk;
- authority, requirement, or propagation boundaries may have been crossed.

Normally skip independent review when work is local and reversible, mechanically verifiable, a simple defect with strong regression coverage, documentation or wording maintenance, a bounded correction the execution owner can directly verify, exploratory work going directly to alignment, or routine work where review context cost exceeds verification value.

Trigger review because of consequence, uncertainty, boundary risk, or verification value—not merely because delegation occurred.

Review depth should be proportional to the same factors.

---

# 2. Reviewer Independence and Context

Normally use fresh bounded reviewer context.

Default when the runtime supports context controls: **no conversational history inheritance**.

Provide only:

- objective;
- relevant locked decisions;
- scope and constraints;
- acceptance criteria;
- changed artifacts or integrated result;
- relevant diff or artifact references;
- execution verification evidence;
- unresolved issues;
- targeted review focus when useful.

Do not provide full parent or execution history unless directly material.

The reviewer is intentionally disposable. Execution corrections benefit from continuity; independent review benefits from context separation.

---

# 3. Reviewer Responsibility

The reviewer independently evaluates whether the integrated result satisfies the active contract.

Focus on:

- objective defects;
- missing acceptance evidence;
- boundary violations;
- integration assumptions;
- correctness risks;
- relevant failure modes.

Distinguish defects from implementation preference.

The reviewer does not own implementation, product requirements, parent-task scope, or final acceptance.

Reviewer ideas are not automatically product requirements.

---

# 4. Review Outcomes

## PASS

Use when the objective is satisfied, acceptance criteria are met, boundaries were respected, verification is adequate, and no material blocker remains.

PASS is a recommendation. Final acceptance remains with the active decision owner.

## PASS WITH NOTES

Use when acceptable work contains non-blocking observations.

Do not turn preferences into required revisions or reviewer ideas into product scope.

## REVISE

Use when a concrete execution defect prevents acceptance and can be corrected inside normal execution authority.

A finding should identify:

- observable problem;
- supporting evidence;
- affected requirement or boundary;
- what must become true.

Do not prescribe implementation detail unless required by the contract.

REVISE normally returns to the existing execution owner.

## ESCALATE

Use when resolution depends on user intent, product requirement authority, alignment, parent-task scope, conflicting governing constraints, architecture reserved for a higher-level owner, risk policy, or unresolved authority disagreement.

Return the issue to the appropriate decision owner.

---

# 5. Adjudication

After review:

- **PASS** → accept unless another blocker exists;
- **PASS WITH NOTES** → accept or surface useful notes;
- **REVISE** → adjudicate and send a bounded correction to the existing execution owner;
- **ESCALATE** → resolve the authority issue or seek human judgment.

The decision owner should not repeat the entire review.

When execution owner and reviewer disagree:

1. prefer observable evidence;
2. determine whether the disagreement is execution-level or authority-level;
3. use bounded verification for execution disputes where possible;
4. prefer follow-up to the existing execution owner when it can resolve the evidence;
5. leave requirement, scope, propagation, alignment, and user-intent disputes with the appropriate authority owner.

Do not turn implementation preference into an authority dispute or an authority dispute into an implementation task.

---

# 6. Correction Packet

Before sending a correction, classify the finding as:

- execution defect;
- requirement issue;
- scope issue;
- alignment issue;
- higher-level decision issue.

Only execution defects should normally go directly to the execution owner.

Pass:

- concrete finding;
- supporting evidence;
- affected requirement or locked decision;
- required resulting condition;
- Change / Preserve / Do not change boundary;
- new constraints, if any.

Do not copy full reviewer transcripts or parent history.

A correction task is bounded by the concrete finding and relevant evidence.

---

# 7. Re-Review

Do not automatically invoke the reviewer again after correction.

Re-review only when materially justified, for example when the correction changed architecture or interfaces, the original defect was high consequence, the execution owner cannot directly verify resolution, correction introduced new uncertainty, or bounded evidence leaves material disagreement unresolved.

Avoid reviewer-executor ping-pong.

---

# 8. Repeated Failure

After repeated similar failure, reconsider:

- assumptions;
- task decomposition;
- delegation boundary;
- acceptance criteria;
- execution-agent capability;
- retained context;
- replacement of the execution agent;
- whether the issue is actually authority-level rather than execution-level.

Repeated failure alone is not a reason for higher-level takeover. It should produce new information.

---

# 9. Review Failure Modes

Treat these as review-design defects:

- automatic independent review for every delegation;
- automatic re-review after every correction;
- treating execution self-verification as independent review;
- making the reviewer a second implementer;
- making the reviewer a second orchestrator or decision owner;
- rejecting implementation preference instead of objective defects;
- passing full execution history when bounded evidence is sufficient;
- forwarding reviewer transcripts without adjudication;
- sending unresolved authority disagreements back as implementation work.

---

# 10. Completion Rule

Independent review is complete when the active decision owner has enough evidence to choose one of:

- accept;
- accept with non-blocking notes;
- return a bounded execution correction;
- resolve an authority or user-decision issue.

The reviewer does not own final acceptance.

The review objective is:

**add independent evidence only when its expected value exceeds its context and coordination cost.**
