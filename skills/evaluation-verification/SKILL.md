---
name: evaluation-verification
description: >
  Design and interpret evidence for whether a claim, implementation, analysis,
  decision, model, or deliverable actually meets its objective and acceptance
  criteria. Use when verification strength materially affects confidence. This
  method does not decide who performs independent review.
---

# Evaluation and Verification

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

## Purpose

Use this skill to answer:

> What evidence would distinguish success from failure, and what does the
> available evidence actually prove?

This skill defines verification method.

It does not define:

- final acceptance ownership;
- whether a separate reviewer must be created;
- requirement authority;
- delegation topology.

The established task boundary or routing/orchestration layer, when present, decides who verifies and whether independent
review is warranted.

Primary rule:

> Match the strength of the completion claim to the strength and coverage of the
> evidence.

---

## 1. Identify the Claims Being Verified

Before choosing tests or checks, identify what is being claimed.

Examples:

- requirement is satisfied;
- defect is fixed;
- migration preserved behavior;
- analysis result is robust;
- recommendation outperforms an alternative under stated criteria;
- research finding is sufficiently supported;
- document or presentation communicates the intended conclusion accurately.

Do not verify only the easiest observable property when the real claim is
broader.

---

## 2. Trace Claims to Criteria

Use explicit requirements or acceptance criteria when available.

For each material claim, determine:

- observable success condition;
- plausible failure mode;
- evidence source;
- coverage limitation.

If no acceptance criterion exists and one is necessary to judge success, use the
appropriate requirements/authority path rather than inventing a product rule
inside verification.

---

## 3. Prefer Discriminating Evidence

Choose evidence that would meaningfully differ if the claim were false.

Possible evidence includes:

- automated tests;
- reproduction of the original failure;
- boundary and integration checks;
- comparison against authoritative source data;
- holdout or out-of-sample evaluation;
- backtest or historical validation;
- sensitivity analysis;
- manual inspection;
- diff or contract comparison;
- independent replication;
- user evaluation when the claim concerns user judgment.

A check is valuable because it can falsify a claim, not because it looks like
verification work.

---

## 4. Cover Relevant Failure Modes

Verification depth should be proportional to consequence, uncertainty, and
change scope.

When relevant, include:

- normal path;
- boundary values;
- negative or invalid inputs;
- failure states;
- state transitions;
- concurrency or timing;
- integration boundaries;
- regression of previously working behavior;
- mismatch between user-visible and internal meaning.

Do not mechanically test every category when it cannot affect the claim.

---

## 5. Distinguish Evidence Levels

Separate:

- **verified** — directly supported by appropriate evidence;
- **partially verified** — meaningful evidence exists but coverage is incomplete;
- **inferred** — plausible from related evidence but not directly checked;
- **unverified** — no sufficient evidence obtained;
- **contradicted** — evidence conflicts with the claim.

Do not report inferred behavior as verified.

Do not turn test passage into proof of requirements the tests do not cover.

---

## 6. Verify the Original Risk

For a correction, experiment, or migration, explicitly revisit the reason
verification was needed.

Examples:

- original failing reproduction no longer fails;
- stale result can no longer overwrite current intent;
- write path still does not retry;
- comparison result remains after removing an outlier;
- recommendation remains valid under the material alternate scenario.

Avoid substituting unrelated green tests for evidence against the original
failure mode.

---

## 7. Check for New Failure Introduced by the Intervention

Where practical, inspect affected boundaries and likely regressions.

Verification should test both:

- intended outcome achieved;
- material protected behavior preserved.

Do not broaden verification to the entire system when the change and risk are
well bounded.

---

## 8. Use Independence Deliberately

Independent evidence is valuable when shared assumptions could hide a defect.

Examples:

- separate reviewer;
- independent data source;
- alternate implementation of a calculation;
- holdout dataset;
- test written from the contract rather than the implementation.

The need for a separate agent is governed by the applicable review policy or host task boundary.

Do not duplicate the same reasoning and call it independent verification.

---

## 9. Stop When Evidence Is Sufficient

Continue verification while additional checks have a reasonable chance of
changing the acceptance conclusion or exposing a material risk.

Stop when:

- acceptance criteria are adequately covered;
- important failure modes have been tested proportionally;
- remaining unverified areas are immaterial or explicitly accepted;
- further checks add little evidence relative to cost.

Do not maximize test volume for its own sake.

---

## 10. Verification Output

A useful verification report normally contains:

### Claims checked
Only the material claims.

### Evidence
Checks performed and their outcomes.

### Coverage
What important behavior the evidence does and does not cover.

### Result
Verified / partially verified / inferred / unverified / contradicted as
appropriate.

### Remaining risk
Only risk that materially affects acceptance or the next step.

Do not produce a chronological testing diary unless requested.

---

## Completion Rule

Verification is sufficient when the acceptance owner can understand what the
evidence proves, what it does not prove, and whether remaining uncertainty is
material to the objective.

The objective is:

**falsifiable, proportionate evidence with no stronger completion claim than the
verification supports.**
