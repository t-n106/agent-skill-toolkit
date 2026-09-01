# Agent Skill Toolkit

A reusable set of conditional agent skills for structured reasoning, delegation, alignment, review, and verification.

This distribution intentionally does **not** prescribe a specific routing or orchestration implementation. It can be used directly as individual skills, or integrated into an existing agent, orchestrator, system prompt, or other host environment.

## Design Principle

> Keep role identity, authority, scope, and routing in the host environment. Load reusable methods and policies only when their distinct work is needed.

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

The goal is not to minimize the number of skills. The goal is to minimize **always-loaded context** while keeping responsibilities explicit, composable, and reusable.

## Included Skills

### Governance policies

- `delegation-context-policy` — agent boundaries, task packets, context inheritance, continuity, and integration responsibility.
- `requirement-alignment-gate` — requirement authority, proposals, user alignment, and propagation boundaries.
- `review-cycle-policy` — conditional independent review, adjudication, correction, and re-review.

### Thinking methods

- `requirements-specification` — turn accepted intent into observable requirements, constraints, non-goals, acceptance criteria, and open questions.
- `solution-design` — choose consequential structure, boundaries, interfaces, state ownership, and trade-offs.
- `planning` — order justified work by dependencies, uncertainty, checkpoints, parallelism, and executable units.
- `research` — establish trustworthy facts from sources with provenance, freshness, and contradiction handling.
- `analysis` — interpret evidence through comparison, normalization, alternative explanations, robustness, and quantitative reasoning.
- `synthesis-decision` — combine evidence and constraints into a recommendation or decision when the current task role owns that authority.
- `evaluation-verification` — define evidence that distinguishes success from failure and calibrate claims to evidence strength.
- `problem-solving` — reduce uncertainty using evidence, hypotheses, information gain, method changes, and minimum sufficient intervention.
- `debugging` — diagnose non-obvious software failures using reproduction, runtime evidence, discriminating observations, root-cause discipline, and regression verification.

## Conceptual Workflow

When a task actually needs every stage, the methods can compose as:

`Intent → Requirements → Design → Planning → Research → Analysis → Synthesis / Decision → Execution → Evaluation / Verification → Output`

This is a conceptual lifecycle, **not a mandatory checklist**. Skip stages that are already settled, trivial, or irrelevant.

`problem-solving` and `debugging` are cross-cutting methods that can be inserted wherever uncertainty or software failure appears.

## Governance vs. Method

A critical rule:

> A method skill never increases authority.

Examples:

- `requirements-specification` can clarify a proposal but cannot approve it.
- `solution-design` can identify a better behavior but cannot silently make it a requirement.
- `research` can establish new facts but facts do not grant requirement authority.
- `synthesis-decision` can recommend a choice but cannot take a user-owned decision.
- `evaluation-verification` can find insufficient evidence but cannot redefine acceptance criteria without authority.

Use governance policies for authority and agent boundaries. Use thinking methods for reasoning procedures.

## Integration

An optional routing / orchestration layer should keep only enough routing knowledge to recognize when a skill is needed.

For example:

- delegation or context transfer → `delegation-context-policy`
- unresolved user-visible requirement → `requirement-alignment-gate`
- independent assurance has material value → `review-cycle-policy`
- accepted intent is not operational enough → `requirements-specification`
- consequential structural choice exists → `solution-design`
- meaningful dependency/order problem exists → `planning`
- source-sensitive facts are missing → `research`
- evidence exists but needs interpretation → `analysis`
- findings must become a recommendation → `synthesis-decision`
- completion evidence is non-trivial → `evaluation-verification`
- uncertainty itself is blocking progress → `problem-solving`
- software behavior is wrong and cause is unclear → `debugging`

See `docs/ROUTING_ORCHESTRATION_EXAMPLE.md` for a minimal integration example.

## Anti-Overengineering Rule

Do not load a skill simply because it is the next box in the conceptual workflow.

A skill should be used only when its distinct responsibility is materially present.

Do not create another skill merely because a topic can be named. A separate skill is justified when it has:

1. an independently recognizable trigger;
2. enough content that is unnecessary outside that trigger;
3. a clear responsibility boundary without circular loading;
4. reusable value beyond one narrow case, unless intentionally domain-specific;
5. behavioral value that exceeds the routing cost it introduces.

## Directory Layout

```text
skills/
  delegation-context-policy/
  requirement-alignment-gate/
  review-cycle-policy/
  requirements-specification/
  solution-design/
  planning/
  research/
  analysis/
  synthesis-decision/
  evaluation-verification/
  problem-solving/
  debugging/

docs/
  ROUTING_ORCHESTRATION_EXAMPLE.md
  ROUTING_SMOKE_TESTS.md
```

## What Is Not Included

This package does not prescribe:

- a specific model or vendor;
- a specific decision-owner / execution-owner hierarchy;
- a mandatory multi-agent topology;
- a particular runtime or skill loader;
- a universal authority model;
- automatic use of every skill.

Adapt routing and authority to your own environment.

## Platform notes

The skills are platform-neutral. Runtime-specific mappings are kept outside the skill policy under `docs/platform-notes/`.

- `docs/platform-notes/codex.md` — Codex-specific context-inheritance mapping (for example, `fork_turns`).


## License

MIT License. See [`LICENSE`](LICENSE).
