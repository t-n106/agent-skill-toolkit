---
name: evaluation-verification
description: Design or interpret non-trivial acceptance evidence for a claim or deliverable. Use when evidence strength or coverage is uncertain; routine checks do not require this skill, and it does not mandate a reviewer.
---

# Evaluation and Verification

Apply within the user/host task boundary; this skill adds no authority. Use the current task context when no separate orchestration layer exists.

## Evidence method
1. Identify material claims and established acceptance conditions. For each, identify an observable success condition, plausible failure, evidence source, and coverage limit. Do not invent new product requirements to make evaluation easier.
2. Prefer evidence that would differ if the claim were false: original reproduction, boundary checks, source comparisons, holdout data, sensitivity checks, contract-derived tests, or artifact inspection as appropriate.
3. Cover consequential normal, negative, boundary, failure, state/timing, integration, and regression behavior only where relevant. Test the original risk and protected behavior, not merely convenient properties.
4. Distinguish verified, partially verified, inferred, unverified, and contradicted claims. Passing tests prove only what their coverage supports.
5. Use independent evidence where shared assumptions could hide failure: another data source, alternate calculation, holdout, or contract-derived check. Creating a separate reviewer is governed by the host and `review-cycle-policy`, not this method.
6. Stop when criteria and material risks are sufficiently covered, or disclose the specific unavailable evidence and its effect on acceptance. Repeat/broaden checks only when they can resolve a concrete remaining risk or required gate.

## Result
Report material claims, evidence/outcomes, coverage limits, status, and remaining acceptance-relevant risk. A plausible artifact is not a verified outcome; a static check is not runtime validation. Do not report unexecuted scenarios as passed tests.
