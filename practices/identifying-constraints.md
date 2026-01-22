# Identifying Constraints

Constraints define **boundaries that must hold** regardless of how a Change is implemented.

They protect the system from unacceptable outcomes.

## Why Constraints Matter

Without explicit constraints:
- violations look like surprises
- root cause analysis becomes vague
- accountability disappears

Constraints turn surprises into signals.

## What Constraints Are

Constraints define:
- conditions that must remain true
- assumptions that cannot be violated
- boundaries enforced by business, law, or architecture

## What Constraints Are Not

Constraints are not:
- goals (those describe desired outcomes)
- preferences (those are choices)
- implementation details (those are how, not what)
- optimizations (those improve performance)

## Types of Constraints

### 1. Data Integrity

```
1. Uniqueness: One email cannot belong to multiple accounts
2. Non-nullability: User ID must always exist
3. Referential integrity: Foreign keys must reference existing records
```

### 2. Business Rules

```
1. Non-reuse: Soft-deleted accounts do not free email for reuse
2. Immutability: Historical transactions cannot be modified
3. Authorization: Users can only access their own data
```

### 3. Performance

```
1. Latency: API responses must be < 200ms (p95)
2. Throughput: System must handle 1000 req/s
3. Availability: Uptime must be > 99.9%
```

### 4. Compliance

```
1. Data retention: Logs must be kept for 7 years
2. Privacy: PII must be encrypted at rest
3. Audit: All changes must be logged
```

### 5. Architectural

```
1. Isolation: Modules must not depend on each other directly
2. Boundaries: Core must not depend on adapters
3. Contracts: API contracts must not break backward compatibility
```

## Invariants

An **Invariant** is a constraint that must hold **at all times**.

Examples:
- balances must never become negative
- data must never be lost
- access must always be authorized

All invariants are constraints.  
Not all constraints are invariants.

## Explicit vs Implicit

Most systems operate with implicit constraints:
- "this must never happen"
- "we assume this is safe"
- "this is not supposed to change"

Implicit constraints are fragile.

Undocumented constraints are eventually violated.

## How to Identify Constraints

### 1. Ask "What Must Not Break?"

For each Change, ask:
- What must remain true?
- What assumptions are we making?
- What would cause unacceptable outcomes?

### 2. Review Existing Code

Look for:
- Database constraints (UNIQUE, NOT NULL, FOREIGN KEY)
- Validation logic
- Error handling
- Comments about "must" or "never"

### 3. Review Business Requirements

Look for:
- Regulatory requirements
- Contractual obligations
- Service level agreements
- Business rules

### 4. Review Architecture

Look for:
- Design principles
- Architectural patterns
- Module boundaries
- API contracts

## Documenting Constraints

Constraints should be:
- explicit
- testable
- owned

**Example:**
```
## Constraints

1. **Uniqueness:** One email cannot belong to multiple accounts
   - Enforced by: PRIMARY KEY on user.email
   - Owner: Data engineer
   - Test: Attempt to insert duplicate email fails

2. **Non-reuse:** Soft-deleted accounts do not free email for reuse
   - Enforced by: No DELETE on user table
   - Owner: Product manager
   - Test: Deleted account's email still exists in user table
```

## Constraints and Change

Every Change must be evaluated against constraints.

If a Change violates a constraint:
- it must be rejected
- or the constraint must be consciously revised

Silent violation is the worst outcome.

## Changing Constraints

Constraints are not suggestions.

They are **non-negotiable boundaries**  
until explicitly changed.

Changing a constraint requires:
- explicit decision
- documented rationale
- accepted risk

**Example:**
```
## Constraint Change

**Original:** Accounts must have unique email addresses

**New:** Accounts can have duplicate email addresses

**Rationale:** Support for shared accounts (e.g., family accounts)

**Risk:** Potential confusion in user identification

**Owner:** Product manager

**Decision Date:** YYYY-MM-DD
```

## Checklist

Before finalizing Constraints:

- [ ] Constraints are explicit (not implicit)
- [ ] Each constraint is testable/verifiable
- [ ] Constraints are owned
- [ ] Constraints are documented
- [ ] Change is evaluated against all constraints
- [ ] Constraint changes are explicit decisions

## Example Template

```
## Constraints / Invariants

1. [Constraint 1]  
   - Enforced by: [How]
   - Owner: [Who]
   - Test: [How to verify]

2. [Constraint 2]  
   - Enforced by: [How]
   - Owner: [Who]
   - Test: [How to verify]
```
