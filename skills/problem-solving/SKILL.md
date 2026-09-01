---
name: problem-solving
description: Apply lightweight, evidence-grounded problem solving to non-trivial tasks where uncertainty, investigation, multiple plausible explanations, meaningful risk, or repeated failure makes deliberate reasoning useful. Do not use for simple, obvious, low-risk work that can be completed directly.
---

# Problem Solving

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

Use this skill for non-trivial problems where the main challenge is reducing
uncertainty and choosing a justified intervention.

Do not invoke it merely for ceremony.

Simple, obvious, low-risk work should normally be completed directly.

## Design Philosophy

This skill governs **how to reduce uncertainty and act on evidence**.

It does not define:

- agent authority;
- delegation topology;
- requirement ownership;
- review ownership;
- context inheritance mechanics;
- source-quality research methodology;
- analytical comparison methodology;
- decision authority.

When the user, host environment, routing/orchestration layer, or another applicable policy defines those boundaries, obey that boundary.

Preserve the purpose of a rule when literal compliance would add more process
than the problem requires.

When the main work is acquiring trustworthy source evidence, use `research`.
When the evidence is already established and the main work is interpreting or
comparing it, use `analysis`. Use this skill when the central difficulty is the
uncertainty-reduction loop itself.

---

## 1. Reason From Evidence

Reason while reasoning can materially reduce uncertainty.

When further reasoning cannot improve confidence without new information,
prefer obtaining evidence that distinguishes between plausible explanations.

Choose observations by considering:

- expected information gain;
- cost;
- risk;
- reversibility;
- availability;
- time.

Prefer the lowest-cost, acceptably safe observation that is expected to
materially reduce uncertainty.

Do not repeatedly generate substantially equivalent hypotheses without
materially new evidence.

Do not gather evidence blindly. Each observation should answer a useful
question, distinguish hypotheses, or eliminate plausible alternatives.

If useful evidence cannot be obtained at acceptable cost or risk, continue with
reasoned analysis, preserve the uncertainty, or escalate through the established
authority boundary.

---

## 2. Keep Facts, Attempts, and Hypotheses Distinct

Do not silently promote an explanation into a fact.

When useful, distinguish:

- **FACT** — directly established information;
- **OBSERVATION** — observed behavior or state;
- **ATTEMPT** — an action already tried;
- **RESULT** — what happened;
- **HYPOTHESIS** — an explanation not yet established;
- **CONSTRAINT** — a condition the solution must respect.

A compact investigation record is often sufficient:

`attempt -> result -> implication`

Failed attempts are useful when they eliminate explanations or constrain the
next decision.

---

## 3. Change Method When Learning Stops

A failed attempt should produce information.

If repeated reasoning, experiments, or fixes stop reducing uncertainty, do not
continue the same loop merely with different wording or slightly different
changes.

Reassess:

- assumptions;
- competing explanations;
- available evidence;
- observation method;
- decomposition;
- whether the current execution context or authority is sufficient.

Change the diagnostic or problem-solving method when the current method is no
longer informative.

---

## 4. Observe Broadly, Intervene Narrowly

Understand enough surrounding context to avoid a local but incorrect solution.

Distinguish between:

- changes required to achieve the current objective;
- desirable but unnecessary improvements;
- unrelated findings.

Prefer the **minimum sufficient intervention**, not merely the smallest textual
change.

Do not silently expand scope for cleanup, abstraction, refactoring,
optimization, or unrelated improvement.

If correctness genuinely requires broader scope, make that dependency explicit
through the established authority boundary.

---

## 5. Use Execution Context Deliberately

Direct work is preferred when coordination overhead would exceed the benefit.

Isolation, delegation, or a different execution context may be useful when it
offers meaningful advantage through specialization, parallelism, tool access,
context isolation, or lower execution cost.

This skill may identify that a different execution context would help, but it
does not authorize a new delegation route.

When a routing/orchestration layer is present, use its established delegation and context policy.

Preserve decision-relevant investigation history across any context boundary;
do not transfer long discarded reasoning merely because it exists.

---

## 6. Verify Outcomes

Do not treat a plausible action as a successful action.

When practical, verify important outcomes using evidence that would distinguish
success from failure.

Completion claims should be proportional to the strength of available
verification.

If verification is incomplete, distinguish established results from inference
and remaining uncertainty.

---

## Practical Loop

For a non-trivial problem:

1. establish what is known and what remains uncertain;
2. form a small number of plausible explanations or approaches;
3. identify the cheapest safe evidence that can distinguish them;
4. observe or test;
5. update from the result;
6. change method if the loop stops producing information;
7. make the minimum sufficient intervention;
8. verify the outcome;
9. preserve or escalate unresolved uncertainty through the established authority boundary.

Do not turn this loop into mandatory ceremony when the answer is already clear.
