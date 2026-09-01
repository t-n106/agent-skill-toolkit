# Routing Smoke Tests

Use these as lightweight checks after changing routing rules. The objective is not to solve the task; it is to verify that the expected skill set is selected without unnecessary additions.

| Scenario | Expected | Normally avoid |
|---|---|---|
| Delegate one bounded task to a fresh execution agent | `delegation-context-policy` | review unless independently justified |
| Accepted behavior exists but acceptance criteria are ambiguous | `requirements-specification` | alignment unless user choice is actually unresolved |
| User must choose between two externally visible behaviors | `requirement-alignment-gate` | silently choosing with design/planning |
| Two plausible module boundaries have meaningful trade-offs | `solution-design` | research unless external facts are missing |
| Five known tasks have real dependency and checkpoint constraints | `planning` | design if structure is already settled |
| Current provider/API behavior must be established from sources | `research` | synthesis before evidence exists |
| Collected evidence must be normalized and compared | `analysis` | more research unless a material evidence gap remains |
| Several findings must become one recommendation with caveats | `synthesis-decision` | taking a decision outside current authority |
| A result appears complete but failure evidence is non-trivial | `evaluation-verification` | automatic independent review unless it adds value |
| Non-trivial uncertainty with several plausible explanations | `problem-solving` | debugging unless it is a software failure |
| Reproducible software defect with unclear cause | `debugging`; optionally `problem-solving` | requirements/design unless the defect exposes them |
| High-consequence integrated change after self-verification | `review-cycle-policy`; reviewer may use `evaluation-verification` | automatic re-review after every correction |

A good routing system should also skip methods for obvious, low-risk, directly executable work.

## Task-boundary compatibility checks

| Scenario | Expected boundary behavior |
|---|---|
| Direct skill use with no orchestration layer | Use the user/host task context as the working boundary; do not invent extra authority |
| Host persona or role already defines scope/constraints | Preserve that role, scope, and constraints while applying the selected skill |
| Routing/orchestration layer defines authority and stop conditions | Follow that established boundary; the loaded skill must not override it |
| No explicit role, authority, or scope exists | Infer only the minimum working boundary from the current task; do not expand scope merely because a method suggests more work |
