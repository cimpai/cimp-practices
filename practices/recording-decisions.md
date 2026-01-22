# Recording Decisions

A Decision is an **explicit commitment** made under uncertainty.

Decisions connect Intent to Change and assign responsibility.

## Why Decisions Must Be Fixed

Undocumented Decisions disappear.

When they disappear:
- alternatives are reconsidered repeatedly
- the same debates resurface
- responsibility becomes unclear
- incidents lack context

Fixing Decisions preserves intent across time.

## What a Decision Is

A Decision:
- chooses one option among alternatives
- accepts specific trade-offs
- commits the system to a direction
- has an identifiable owner

## What a Decision Is Not

A Decision is not:
- consensus ("everyone agreed")
- a vague agreement
- an implementation detail
- a post-hoc justification

## Decision Record Structure

A Decision record typically includes:
- context
- decision statement
- alternatives considered
- rationale
- consequences
- owner
- date

Brevity is a virtue.

## Examples

### ❌ Bad Decision Record

> "We decided to use PostgreSQL"

**Problems:**
- No context (why?)
- No alternatives (what else was considered?)
- No rationale (why PostgreSQL?)
- No owner
- No date

### ✅ Good Decision Record

> **Context:** Need to store user profile data with uniqueness constraints on email.
>
> **Decision:** Use separate table `user_profile` with PRIMARY KEY on `email`, instead of JSONB in `user.metadata`.
>
> **Alternatives Considered:**
> 1. Keep in JSONB with application-level uniqueness check
> 2. Use PostgreSQL UNIQUE constraint on JSONB field
> 3. Use separate table (chosen)
>
> **Rationale:**
> - Database-level uniqueness is more reliable
> - Easier to query and index
> - Normalized structure supports future requirements
>
> **Consequences:**
> - Requires migration of existing data
> - Adds complexity (two sources of truth during transition)
> - Better long-term maintainability
>
> **Owner:** Data engineer
>
> **Date:** YYYY-MM-DD

**Why it's good:**
- Clear context
- Explicit alternatives
- Documented rationale
- Acknowledged consequences
- Owner and date

## When to Record Decisions

Record decisions when:
- choosing between significant alternatives
- accepting trade-offs
- making architectural choices
- setting constraints or policies
- changing direction from previous decisions

Don't record:
- trivial implementation choices
- obvious selections
- temporary workarounds (unless they become permanent)

## Decisions vs Implementation

Implementation may evolve.

The Decision remains stable unless explicitly revisited.

Changing implementation does not automatically change the Decision.

Changing the Decision requires a new Decision.

**Example:**
> **Decision (YYYY-MM-DD):** Use separate table for user profiles
>
> **Implementation (YYYY-MM-DD):** Added database entity
>
> **Implementation (YYYY-MM-DD):** Optimized queries
>
> The Decision stays the same. Only implementation changes.

## Decision Ownership

Every Decision must have:
- a single accountable owner
- a clear scope
- an explicit rationale

Many people may contribute.

One person decides.

## Decisions Under Uncertainty

Decisions are made without complete information.

This is expected.

A good Decision:
- states assumptions
- acknowledges uncertainty
- accepts bounded risk

Waiting for certainty is itself a Decision.

## Decision Drift

Decision drift occurs when:
- implementation diverges silently
- constraints erode
- ownership is lost

Drift is prevented by:
- explicit records
- periodic review
- visible ownership

## Where to Record Decisions

Decisions can be recorded in:
- Change Plan documents (section "Decisions")
- Architecture Decision Records (ADR)
- Dedicated decision log
- Code comments (for code-level decisions)

Choose what works for your team.

## Checklist

Before finalizing a Decision:

- [ ] Context is clear
- [ ] Decision statement is explicit
- [ ] Alternatives are documented
- [ ] Rationale is explained
- [ ] Consequences are acknowledged
- [ ] Owner is assigned
- [ ] Date is recorded

## Example Template

```
## Decision: [Title]

**Context:** [Why this decision is needed]

**Decision:** [What we decided]

**Alternatives Considered:**
1. [Alternative 1] - [Why rejected]
2. [Alternative 2] - [Why rejected]
3. [Chosen alternative] - [Why chosen]

**Rationale:** [Why this decision]

**Consequences:** [What this means]

**Owner:** [Name/Role]

**Date:** YYYY-MM-DD
```
