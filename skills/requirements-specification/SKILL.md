---
name: requirements-specification
description: >
  Convert an accepted objective or user intent into a compact, explicit,
  testable requirement set without inventing requirement authority. Use when
  behavior, constraints, non-goals, acceptance criteria, or open questions need
  to be made operational before design or execution.
---

# Requirements Specification

## Task Boundary

Respect any authority, scope, role, and constraints already established by the user, host environment, or routing/orchestration layer. If none are explicitly defined, treat the current task context as the working boundary.

This skill does not expand that boundary unless the governing context explicitly authorizes it.

---

## Purpose

Use this skill to turn intent into a decision-ready or execution-ready statement
of **what must be true**.

This is a specification method, not a requirement-approval mechanism.

It does not grant authority to:

- invent product intent;
- approve a proposal;
- expand feature scope;
- resolve a user-choice boundary;
- choose implementation architecture.

When requirement authority is unresolved, use the established alignment/authority
boundary. A specification may describe a proposal, but it must not silently promote
that proposal into an approved requirement.

Primary rule:

> Make the required outcome explicit without adding requirements merely to make
> the solution easier to design or implement.

---

## 1. Establish Requirement Status First

Before elaborating a requirement, distinguish where possible:

- **confirmed** — explicitly approved or authoritative;
- **derived constraint** — necessarily follows from a confirmed requirement or
  governing contract;
- **proposal** — potentially useful but not approved;
- **assumption** — temporarily used because evidence or authority is missing;
- **open question** — must remain unresolved until evidence or authority settles
  it.

Do not collapse these states into one list called "requirements".

If continuing depends on approving a proposal or resolving user intent, stop at
the established requirement-alignment boundary.

---

## 2. Define the Outcome Before the Mechanism

Specify the externally meaningful result before deciding how to implement it.

Capture, when relevant:

- user or system objective;
- observable behavior;
- inputs and outputs;
- invariants and guarantees;
- constraints;
- non-goals;
- failure or unavailable states;
- acceptance criteria;
- unresolved questions.

Prefer statements about **what must hold** over statements about **which module,
class, framework, schema, algorithm, or architecture must exist**, unless the
mechanism itself is already an approved constraint.

---

## 3. Preserve Scope Boundaries

A specification should reduce ambiguity, not expand ambition.

Do not automatically add:

- desirable adjacent features;
- future extensibility;
- generic frameworks;
- extra configuration;
- broad compatibility goals;
- speculative safety rules;
- new UI behavior;
- implementation convenience requirements.

Record useful extras separately as proposals when they matter.

A missing detail is not automatically a requirement gap. Some details belong to
solution design or implementation discretion.

---

## 4. Make Requirements Observable

Where practical, express important requirements so that a later agent can tell
whether they are satisfied.

Useful forms include:

- given / when / then behavior;
- allowed and prohibited states;
- before / after relationships;
- preserved invariants;
- explicit failure outcomes;
- measurable bounds when truly required;
- examples that clarify meaning without becoming the only valid case.

Avoid acceptance criteria that merely restate an implementation task, such as:

> "Create class X"

when the real requirement is behavioral.

---

## 5. Separate Requirements From Acceptance Evidence

A requirement defines what must be true.

Acceptance criteria define how sufficient evidence can demonstrate that the
requirement is met.

Do not overspecify a single test implementation unless that test mechanism is
itself required.

Prefer criteria that allow later verification to choose the strongest practical
evidence.

---

## 6. Handle Ambiguity Deliberately

For each material ambiguity, determine whether it is:

- resolvable from an authoritative artifact;
- resolvable from external evidence;
- a solution choice inside existing authority;
- a requirement decision requiring judgment from the user or another authorized decision owner.

Resolve the first two when justified.

Leave solution choices to design or execution.

Do not disguise the final category as an assumption merely to keep work moving.

---

## 7. Maintain Traceability Without Bureaucracy

For consequential requirements, preserve enough provenance to explain where the
requirement came from.

Possible sources include:

- explicit user decision;
- canonical product document;
- governing contract;
- accepted prior decision;
- externally imposed constraint.

Do not build a heavy traceability system when a short source note is sufficient.

The objective is to prevent accidental requirement invention, not to maximize
process artifacts.

---

## 8. Completion Output

A useful requirement packet is compact and normally contains:

### Objective
What outcome is being pursued.

### Confirmed requirements
Only established requirements and necessary derived constraints.

### Non-goals / preserve
What the current work must not silently expand or change.

### Acceptance criteria
Observable evidence of success.

### Proposals
Only when useful; clearly marked as unapproved.

### Open questions
Only material unresolved questions, with the authority or evidence needed to
resolve them.

Do not produce sections that have no content merely for ceremony.

---

## Completion Rule

Requirements are sufficiently specified when design or execution can proceed
without needing to invent product intent, while remaining ambiguity is clearly
classified and routed to the correct authority or evidence source.

The objective is:

**enough specification to preserve intent and enable verification, without
turning implementation detail or agent preference into requirement authority.**
