---
name: analysis
description: >
  Transform an established evidence set into structured findings. Use when the
  task requires comparison, pattern detection, relative performance,
  quantitative interpretation, causal caution, sensitivity checks, or
  explanation of what the evidence implies. Do not use merely to gather facts.
---

# Analysis

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

## Purpose

Use this skill to determine **what can reasonably be inferred from the available
evidence**.

Analysis begins after enough relevant evidence exists.

It does not own:

- source acquisition;
- requirement authority;
- preference or policy decisions not implied by evidence;
- final acceptance;
- implementation.

Primary rule:

> Structure the evidence so that conclusions follow from explicit comparisons,
> assumptions, and uncertainty rather than narrative momentum.

---

## 1. Define the Analytical Question

State what the analysis is trying to determine.

Examples:

- Which option performs better under the relevant criteria?
- Is an observed change unusual relative to a baseline?
- Which factors plausibly explain the result?
- Is a pattern robust across periods or subsets?
- What evidence supports or weakens the working hypothesis?

Avoid analyzing every available dimension merely because data exists.

---

## 2. Establish Comparable Units and Baselines

Before comparing values or cases, check whether they are genuinely comparable.

Consider, where relevant:

- period;
- denominator;
- scale;
- population;
- market or environmental regime;
- measurement definition;
- missing data;
- survivorship or selection effects.

Choose a baseline that matches the actual question.

Absolute performance, relative performance, and change from baseline answer
different questions.

---

## 3. Separate Observation From Interpretation

Distinguish:

- **observation** — directly visible in the evidence;
- **relationship** — variables move together or differ systematically;
- **interpretation** — a proposed explanation;
- **causal claim** — requires stronger evidence than correlation or sequence.

Do not convert "happened before" or "moves with" into causation without
sufficient support.

---

## 4. Examine Alternative Explanations

For material conclusions, ask what else could explain the observation.

Relevant checks may include:

- confounders;
- selection bias;
- base-rate effects;
- sample size;
- outliers;
- regime change;
- measurement artifacts;
- omitted variables;
- reverse causality.

Do not generate speculative counterarguments with no plausible connection to
the evidence.

---

## 5. Quantify When It Improves Understanding

Use calculations, normalized measures, distributions, confidence intervals,
scenario ranges, or sensitivity analysis when they materially clarify the
question.

Do not add numerical precision that the source data cannot support.

When a result depends strongly on an assumption, show that dependency instead
of hiding it behind a single point estimate.

---

## 6. Test Robustness

For consequential findings, check whether the conclusion survives reasonable
changes such as:

- alternate baseline;
- different period;
- removal of an outlier;
- plausible parameter range;
- subgroup split;
- alternative but valid definition.

A finding that disappears under a small reasonable change should be reported as
fragile.

Do not perform exhaustive sensitivity analysis when the decision is insensitive
to the uncertainty.

---

## 7. Preserve Negative and Null Results

A lack of evidence can be informative.

Report when:

- an expected relationship does not appear;
- evidence is too weak to distinguish alternatives;
- a hypothesis loses support;
- a result is statistically or practically negligible;
- available data cannot answer the question.

Do not force every analysis to produce a positive finding.

---

## 8. Use the Minimum Sufficient Analytical Structure

Choose the representation that best exposes the relevant relationship:

- comparison table;
- ranked factors;
- timeline;
- cohort or subgroup comparison;
- distribution;
- scenario analysis;
- causal diagram;
- concise narrative.

Do not build a dashboard or model merely because the data can support one.

---

## 9. Analysis Output

A useful analysis result normally contains:

### Question / baseline
What was evaluated and against what reference.

### Findings
The strongest evidence-backed patterns or differences.

### Interpretation
What those findings plausibly imply, clearly separated from observation.

### Counterevidence / limitations
Material factors that weaken or bound the conclusion.

### Robustness
Whether the conclusion changes under reasonable alternatives.

### Remaining uncertainty
Only uncertainty that matters to the next decision.

Do not make a final choice merely because one finding is interesting. Use a
decision-synthesis method when trade-offs or authority remain.

---

## Completion Rule

Analysis is sufficient when the next decision-maker can see which conclusions
are strongly supported, which depend on assumptions, which alternatives remain
plausible, and what uncertainty materially remains.

The objective is:

**evidence-to-finding transformation without overstating causality, precision,
or robustness.**
