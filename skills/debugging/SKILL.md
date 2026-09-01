---
name: debugging
description: Apply software-specific evidence gathering to bugs whose cause is not already obvious. Use runtime behavior, failures, tests, logs, state inspection, or minimal reproductions to distinguish causes; avoid repeated speculative fix loops. Use general problem-solving principles for broader uncertainty and respect the established task boundary for authority, delegation, and context transfer.
---

# Debugging

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

Use this skill when software behaves incorrectly and the cause is not already
obvious.

This is a software-specific specialization of evidence-grounded problem
solving. It defines useful debugging observations and completion evidence; it
does not redefine agent authority, delegation topology, or requirement scope.

If the defect is directly evident and the correction is low-risk, fix and
verify it without unnecessary diagnostic ceremony.

---

## 1. Establish the Failure

When practical, reproduce or otherwise establish the original failing behavior
before changing code.

Useful evidence may include:

- the full exception or stack trace;
- failed assertions or tests;
- runtime state and relevant variable values;
- branch or control-flow information;
- inputs and outputs at system boundaries;
- focused logging or debugger inspection;
- a minimal reproduction;
- dependency or external-system behavior.

Prefer direct evidence over assumptions about what the code "should" be doing.

---

## 2. Diagnose Before Repeated Fixing

A reasonable initial hypothesis or obvious fix is allowed.

The anti-pattern is:

`guess -> modify -> fail -> guess -> modify -> fail`

without materially new evidence.

For a non-obvious defect, normally:

1. inspect existing evidence;
2. form a small number of plausible causes;
3. choose an observation that distinguishes them;
4. perform the observation or focused experiment;
5. update the diagnosis from the result;
6. fix the cause when sufficiently established;
7. verify against the original failure.

If a speculative fix fails, the next step should normally increase information,
not merely produce another unsupported patch.

---

## 3. Prefer Discriminating Observations

Ask what uncertainty an observation is intended to resolve.

Prefer the smallest observation that materially distinguishes current
hypotheses.

Do not add diagnostics merely because the cause is unclear.

Avoid the observation equivalent of a speculation loop:

`add logging -> unclear -> add more logging -> unclear`

If an observation provides little information, change the observation or the
diagnostic technique rather than increasing diagnostic volume.

---

## 4. Treat Boundaries as Evidence Sources

When relevant, inspect behavior at boundaries such as:

- caller -> callee;
- frontend -> backend;
- process -> process;
- application -> database;
- application -> external service;
- source -> generated artifact;
- configuration -> runtime state.

A boundary observation can often distinguish whether the fault is in data,
control flow, transformation, environment, or integration.

Do not broaden investigation without a reason tied to the observed failure.

---

## 5. Separate Root Cause From Symptom

A patch that suppresses the visible error is not necessarily a fix.

Prefer an explanation that accounts for the observed failure and is supported
by evidence.

If the root cause is not sufficiently established, say so and avoid presenting
a symptom workaround as a confirmed root-cause fix.

If the real cause requires scope or authority beyond the current assignment,
use the established escalation or authority boundary rather than applying a misleading local patch.

---

## 6. Use General Problem Solving When Needed

Load or apply `problem-solving` when debugging expands into broader uncertainty,
multiple competing explanations, repeated failed approaches, or a need to
reconsider decomposition or investigation strategy.

For isolation, delegation, context inheritance, or investigation handoff, use
the established delegation or orchestration policy, when present, rather than duplicating those rules
here.

---

## 7. Verify the Fix

A bug is not resolved merely because modified code looks plausible.

Whenever practical, use evidence that would have exposed the original failure.

Prefer:

`failure established -> cause identified -> fix applied -> original failure no longer occurs`

over:

`code changed -> looks correct`

Add broader regression checks when justified by the affected boundary and risk;
do not expand verification mechanically.

---

## 8. Clean Up Diagnostics

Temporary diagnostics should normally be removed after the investigation unless
they provide ongoing value.

Do not unintentionally leave behind:

- temporary logging;
- debug prints;
- ad hoc instrumentation;
- diagnostic-only code;
- temporary bypasses.

Do not force runtime experiments when execution would be unsafe, destructive,
disproportionately expensive, or unavailable. In those cases, distinguish
static evidence from remaining hypotheses.
