---
name: requirement-alignment-gate
description: Handle material product or scope decisions outside existing authorization, including proposed behavior and exploratory UX awaiting a real user decision. Skip ordinary solution choices and already authorized work.
---

# Requirement Alignment Gate

Apply within the user/host task boundary; this skill adds no authority. Use the current task context when no separate orchestration layer exists.

## Classify before gating
Requirement authority belongs to the user unless delegated. Solution authority belongs to the agent within the established scope. Reuse authorization and decisions already present in the conversation or governing artifacts; no special approval phrase is required.

Distinguish:
- **Proceed:** ordinary implementation, bug fixes restoring intended behavior, test repairs, and reversible design choices within authorized intent. Record a material provisional assumption when needed and continue.
- **Prepare a decision:** a genuinely new feature, mandatory field, changed intended workflow, expanded acceptance criterion, or material unresolved product choice outside delegated discretion.
- **Honor an explicit checkpoint:** the user requested proposal/mock review before implementation, or a governing authority boundary requires it.

Visible UI work, multiple possible designs, or an unspecified detail alone do not establish a checkpoint. A request to build or improve a result normally includes reasonable solution discretion within that request. Reversibility does not authorize unrelated new product scope.

## Explore without promoting
For a real unresolved requirement, complete the bounded investigation and minimum self-verified artifact needed to judge it. Clearly separate confirmed requirements, proposals, assumptions, and recommendations.

Provisional behavior may exist in the evaluation artifact, but must not silently become canonical requirements, production behavior, migration commitments, downstream contracts, tests, or Definition of Done. Keep proposal-specific plans conditional. Continue unrelated authorized work; stop only propagation that depends on the unresolved decision.

## Handoff and resume
Present the concrete decision, why it matters, relevant facts, options/recommendation, reviewable artifact when useful, and downstream consequence. Human judgment should not substitute for unfinished authorized investigation.

After acceptance, resume execution and update status within the authorized artifact/scope boundary. Use `requirements-specification` only if accepted intent still needs substantial elaboration. Do not re-request approval for routine implementation or infer broader propagation permission than the accepted request grants.

Completion is either resumed authorized execution or a decision-ready handoff at a genuine authority boundary—not a mandatory pause for every ambiguity.
