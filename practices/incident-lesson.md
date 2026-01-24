# Incident Lesson

This practice defines the role and nature of an **INCIDENT_LESSON** in CIMP.

An INCIDENT_LESSON captures **generalized knowledge**
derived from a change, failure, or surprise.

It exists to separate learning from reaction.

---

## Statement

An INCIDENT_LESSON represents **reusable system knowledge**.

It is created when observation reveals
a pattern that can affect future changes.

If knowledge cannot be generalized,
it is not considered a lesson.

---

## Position in the Learning Loop

An INCIDENT_LESSON occupies a single position
in the Change Learning Loop:

```
RETRO
↓
INCIDENT_LESSON
↓
PRACTICE
```

It exists between observation and normalization.

Collapsing these stages weakens learning.

---

## What an Incident Lesson Captures

An INCIDENT_LESSON captures:

- a repeatable failure or risk pattern
- a missing or violated invariant
- a detection or feedback gap
- the conditions under which the pattern emerges

It focuses on **why the system allowed the outcome**,
not on how the outcome was fixed.

---

## What an Incident Lesson Is Not

An INCIDENT_LESSON is not:

- an incident report
- a timeline of events
- a root cause analysis
- a remediation plan
- a list of action items

Those artifacts describe events or responses.

A lesson describes **transferable knowledge**.

---

## Generalization Requirement

A lesson must be **independent of a specific implementation**.

It must:
- apply to future changes
- remain valid after refactoring
- survive technology replacement
- be understandable without incident context

If a lesson depends on a particular service, tool, or code path,
it is considered incomplete.

---

## Strength of a Lesson

A strong INCIDENT_LESSON:

- names an invariant explicitly
- explains how it was bypassed or missing
- identifies why detection was insufficient
- suggests a direction for prevention

A weak lesson:
- restates symptoms
- focuses on human error
- depends on vigilance
- cannot be enforced structurally

Weak lessons do not justify practices.

---

## Relationship to Practice

An INCIDENT_LESSON may:
- result in no practice
- result in one practice
- result in multiple practices

This is acceptable.

A practice must never exist without a lesson,
but a lesson does not always require a practice.

The transition from lesson to practice
is defined separately.

---

## Failure Mode

A common failure mode is to skip generalization.

This occurs when:
- lessons mirror incident descriptions
- fixes are treated as lessons
- knowledge remains tied to context

In this case, the system reacts,
but does not learn.

---

## Final note

Incidents reveal what the system allows,
not what people intended.

An INCIDENT_LESSON exists to preserve that knowledge
after urgency has passed.

Learning begins when patterns outlive events.
