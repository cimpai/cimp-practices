# Practices

This directory contains practical guides for applying CIMP
in real systems.

Practices in this repository are treated as **outputs of learning**.

They exist because systems encountered:
- changes
- incidents
- surprises
- failed assumptions

and converted that experience into reusable guidance.

Practices do **not** define canonical concepts
and are **not part of the CIMP Canon**.

---

## Relationship to the Canon

Canonical concepts, boundaries, invariants, and lifecycles are defined in the CIMP Canon and the root `README.md`.

Practices exist **downstream** of the Canon.

They are derived from retrospectives and incident lessons
through the **Change Learning Loop**:

```
CHANGE_PLAN
↓
RETRO
↓
INCIDENT_LESSON
↓
PRACTICE
↓
ENFORCEMENT
```

A practice without a traceable origin
is considered provisional.

---

## Nature of Practices

Practices are:
- experience-based
- context-aware
- allowed to evolve

Practices are **not**:
- canonical rules
- mandates
- definitions
- best-practice collections

They may change without requiring a canon update.

---

## Available Practices

### Change Planning Practices

These practices focus on the **entry point of the Change Learning Loop**.

They describe how to write effective CHANGE_PLAN documents:
how intent is formed, boundaries are defined,
constraints are identified, execution is planned,
and outcomes are observed.

These practices do not represent learning outcomes.
They prepare a change to be executed and observed
so that learning can later occur.

- **[Writing Intent](./writing-intent.md)**  
  How to write falsifiable, outcome-oriented Intent

- **[Defining Scope](./defining-scope.md)**  
  How to set clear boundaries for Changes

- **[Identifying Constraints](./identifying-constraints.md)**  
  How to find and document constraints

- **[Kill Criteria](./kill-criteria.md)**  
  How to define stop conditions for Changes

- **[Recording Decisions](./recording-decisions.md)**  
  How to document explicit commitments

- **[Execution Plan](./execution-plan.md)**  
  How to break down Changes into verifiable steps

- **[Observation Plan](./observation-plan.md)**  
  How to observe Changes after execution

---

### Learning & Normalization Practices

These practices define how **observation becomes learning**
and how learning is converted into durable system behavior.

They apply to the **middle of the Change Learning Loop**
and prevent retrospectives and incidents
from degrading into reaction rituals.

- **[Retro as Observation](./retro-as-observation.md)**  
  Defines RETRO as an observational artifact, not a decision forum

- **[Incident Lesson](./incident-lesson.md)**  
  Defines how generalized knowledge is extracted from incidents

- **[From Lesson to Practice](./lesson-to-practice.md)**  
  Defines when and how lessons become normative practices

---

## Using Practices

Practices are meant to be **applied consciously**.

You may:
- adapt them to your context
- combine them
- ignore them if they do not apply

However:

> If a practice consistently prevents a class of failure,  
> it should eventually be enforced
> through checklists, constraints, or governance.

Practices are a bridge between experience and enforcement.

---

## Evolution

Practices evolve faster than the Canon.

When a practice:
- becomes universally applicable
- protects a fundamental invariant
- stops being context-dependent

it may inform future canonical clarification.

Until then, practices remain flexible by design.
