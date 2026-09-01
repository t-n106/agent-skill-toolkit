---
name: synthesis-decision
description: >
  Integrate established requirements, research, analysis, constraints, risks,
  and competing options into a decision or decision-ready recommendation. Use
  when evidence is distributed across multiple findings or trade-offs. Preserve
  authority boundaries and state what would change the decision.
---

# Synthesis and Decision

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

## Purpose

Use this skill to answer:

> Given what is established, what should be concluded or chosen now?

Synthesis combines evidence across sources and analyses.

Decision selects an option only when the current task role has authority to do so.

This skill does not grant requirement, product, decision, or orchestration authority.

Primary rule:

> Integrate evidence according to explicit decision criteria; do not let the
> loudest finding or longest analysis become the decision by default.

---

## 1. Define the Decision

Before comparing options, identify:

- decision to be made;
- decision owner;
- available options, including "defer" or "gather more evidence" when real;
- governing requirements and constraints;
- criteria that materially distinguish options.

If the decision owner is the user or another authorized decision owner, produce a decision-ready
recommendation rather than silently finalizing the choice.

---

## 2. Weight Evidence by Relevance and Strength

Not all evidence deserves equal weight.

Consider:

- directness to the decision;
- source quality;
- freshness;
- analytical robustness;
- applicability to the current context;
- sample or evidence coverage;
- independence from other evidence.

Do not count multiple derivative sources as multiple independent confirmations.

Do not discard minority evidence merely because most sources point elsewhere.

---

## 3. Compare Options Against the Same Criteria

Use a common decision frame.

Possible criteria include:

- requirement fit;
- expected benefit;
- downside risk;
- reversibility;
- cost;
- time;
- uncertainty;
- operational complexity;
- verification strength;
- strategic fit.

Use only criteria relevant to the actual decision.

Avoid scorecards whose numeric weights imply more precision than the evidence
supports.

---

## 4. Preserve Counter-Thesis

For the leading option, identify the strongest credible reason it could be
wrong.

Ask:

- Which assumption is doing the most work?
- What evidence most weakens the recommendation?
- What alternative performs better under a plausible different condition?
- What future observation would invalidate the current choice?

The purpose is to expose decision sensitivity, not to manufacture false balance.

---

## 5. Treat Reversibility as Decision Information

When evidence is incomplete, a reversible decision may be justified sooner than
an irreversible one.

For irreversible or high-consequence choices, require stronger evidence or an
appropriate authority checkpoint.

Do not choose a more complex reversible architecture merely to avoid making any
commitment.

---

## 6. Decide, Defer, or Escalate Explicitly

A valid result can be:

- choose option A;
- choose option B;
- run a bounded experiment first;
- defer because the decision has no current value;
- escalate because authority is external;
- remain undecided because evidence cannot distinguish options.

Do not disguise indecision as a vague recommendation.

Do not force a choice when the value of additional evidence exceeds the cost of
waiting.

---

## 7. State Confidence Proportionally

Confidence should reflect:

- evidence strength;
- agreement across independent evidence;
- robustness;
- uncertainty in key assumptions;
- consequence of being wrong.

Use qualitative confidence when quantitative calibration is unavailable.

Do not use strong language merely because a decision is required.

---

## 8. Decision Output

A useful decision packet normally contains:

### Decision / recommendation
The selected action or the recommendation to the decision owner.

### Why
The few strongest reasons tied to explicit criteria.

### Counter-thesis / key risk
The strongest credible challenge.

### Confidence
Proportional to evidence and uncertainty.

### What would change the decision
Specific evidence, threshold, event, or assumption failure that should trigger
reconsideration.

### Deferred items
Only follow-ups that matter after the decision.

Do not repeat the entire research and analysis history.

---

## Completion Rule

Synthesis is sufficient when the decision owner can see the recommended choice,
its evidence basis, material downside, uncertainty, and reconsideration trigger
without redoing the underlying analysis.

The objective is:

**a compact, evidence-weighted decision that remains honest about authority and
uncertainty.**
