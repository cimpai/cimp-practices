# Defining Scope

Scope defines **the boundaries of a Change**.

It explicitly states what may change and what must not change.

## Why Scope Matters

Without explicit Scope:
- "small changes" expand silently
- unrelated improvements are mixed in
- risk grows without visibility

Scope creep is not a discipline problem.  
It is a boundary problem.

## Structure

A valid Scope always contains both:

**In scope:**
- What is allowed to change
- What is intentionally affected

**Out of scope:**
- What must remain unchanged
- What is intentionally excluded

If something is not explicitly out of scope,  
it is implicitly at risk.

## Examples

### ❌ Bad Scope

> "Improve the billing system"

**Problems:**
- No boundaries
- Everything could be "in scope"
- No protection for other systems

### ✅ Good Scope

> **In scope:**
> - Invoice generation logic
> - Invoice storage schema
> - Invoice API endpoints
>
> **Out of scope:**
> - Payment processing
> - User account management
> - Reporting dashboards

**Why it's good:**
- Clear boundaries
- Protects unrelated systems
- Enables focused review

## Common Patterns

### 1. Module/Service Boundaries

```
**In scope:**
- User authentication service
- Auth token generation
- Session management

**Out of scope:**
- User profile service
- Authorization rules
- Third-party OAuth providers
```

### 2. Data Boundaries

```
**In scope:**
- Account table schema
- Account creation/update logic

**Out of scope:**
- Account metadata (JSONB)
- Related billing data
- Audit logs
```

### 3. Feature Boundaries

```
**In scope:**
- New user email validation
- Email uniqueness constraint

**Out of scope:**
- User profile editing
- User deletion
- Historical data migration
```

## Business-Limited Scope

Scope may be **deliberately limited by business decision**,  
even when broader correction is technically possible.

**Example:**
> **Out of scope:**
> - Fixing historical data inconsistencies
> - Migrating legacy accounts
>
> **Rationale:** Business decision to fix forward only.  
> Historical data will be corrected manually if needed.  
> Owner: Product Manager.

This is not a technical compromise.  
It is an explicit trade-off made under accountability.

## Scope Under Pressure

Under urgency, Scope is often relaxed first.

This is when it matters most.

If Scope cannot be stated clearly,  
the Change is not ready.

## Scope and Intent

Intent defines **why** a Change exists.

Scope defines **where** that Intent is allowed to act.

Intent without Scope is unbounded authority.

## Checklist

Before finalizing Scope:

- [ ] Both "in scope" and "out of scope" are defined
- [ ] Boundaries protect unrelated systems
- [ ] Business limitations are explicit and owned
- [ ] Scope aligns with Intent
- [ ] Scope is small enough to review effectively
