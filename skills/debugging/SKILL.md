---
name: debugging
description: Diagnose software failures whose cause is unclear using reproduction, runtime evidence, and discriminating observations. Skip diagnostic ceremony for obvious low-risk fixes.
---

# Debugging

Apply within the user/host task boundary; this skill adds no authority. Use the current task context when no separate orchestration layer exists.

## Diagnose and correct
1. Establish the original failure when practical: reproduction, failing assertion, stack trace, relevant input/output, state, or dependency behavior. Record the expected behavior and environment needed to interpret it.
2. Form a small set of plausible causes and choose an observation that distinguishes them. Inspect caller/callee, process, storage, service, configuration/runtime, or source/generated-artifact boundaries when relevant.
3. A reasonable initial fix is allowed. After a speculative fix fails, obtain new information before another unsupported patch. If logging adds no information, change technique rather than add volume.
4. Correct the supported cause. Distinguish a symptom workaround from a confirmed root-cause fix; return a broader scope dependency if correction exceeds the assignment.
5. Recheck the original failure and affected protected behavior. Add regression checks only for concrete affected risks. Remove temporary diagnostics and bypasses unless they have ongoing value.

## Escalation and completion
Use `problem-solving` only when broader uncertainty or a stalled investigation needs a different strategy; do not reload it to repeat this diagnostic loop. Routine verification stays here; load `evaluation-verification` only if evidence design is itself non-trivial.

Do not force unavailable, unsafe, or disproportionately expensive execution. Report static evidence separately from runtime verification and remaining hypotheses. A plausible patch alone is not proof of resolution.
