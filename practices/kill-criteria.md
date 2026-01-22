# Kill Criteria

Kill Criteria define **conditions under which a Change must be stopped, rolled back, or reconsidered**, regardless of effort already invested.

## Why Kill Criteria Matter

Without Kill Criteria:
- effort becomes a justification
- escalation replaces reasoning
- bad changes persist because they are "almost done"
- teams drift into hero mode

Most damaging changes are not bad ideas.  
They are good ideas that were not stopped in time.

## What Kill Criteria Are

Kill Criteria are:
- explicit stop conditions
- defined *before or during* execution
- independent of sunk cost
- enforced by governance, not emotion

## What Kill Criteria Are Not

Kill Criteria are not:
- rollback plans (those describe *how* to revert)
- risk descriptions (those describe *what might happen*)
- monitoring alerts (those are operational tools)
- post-hoc justifications

## Structure

A minimal Kill Criteria definition may include:
- 1–3 explicit stop conditions
- a clear owner
- a decision path when triggered

Clarity matters more than completeness.

## Examples

### ❌ Bad Kill Criteria

> "If something goes wrong, we'll rollback"

**Problems:**
- Vague ("something goes wrong" = undefined)
- No owner
- No decision path

### ✅ Good Kill Criteria

> 1. **Performance degradation:** p95 latency exceeds 500ms (current: 200ms)  
>    => Stop deployment, rollback immediately  
>    Owner: Platform lead
>
> 2. **Data integrity:** Any duplicate records detected  
>    => Stop migration, investigate root cause  
>    Owner: Data engineer
>
> 3. **Business impact:** Customer complaints > 5 in first hour  
>    => Rollback, reassess approach  
>    Owner: Product manager

**Why it's good:**
- Specific, measurable conditions
- Clear actions
- Assigned owners

## Common Categories

### 1. Constraint Violations

```
1. Uniqueness constraint violated => Stop, investigate
2. Data loss detected => Rollback immediately
```

### 2. Performance Degradation

```
1. Latency exceeds SLA threshold => Stop deployment
2. Error rate > 1% => Rollback
```

### 3. Business Impact

```
1. Revenue impact > $X => Stop, reassess
2. Customer complaints > threshold => Rollback
```

### 4. Operational Instability

```
1. System crashes > 2 in first hour => Rollback
2. Cannot observe change effects => Stop, add monitoring
```

### 5. Scope Expansion

```
1. Change requires modifying unrelated systems => Stop, split scope
2. Additional dependencies discovered => Reassess approach
```

## Kill Criteria and Sunk Cost

Kill Criteria explicitly counter **sunk cost fallacy**.

Once a Kill Criterion is met:
- prior effort is irrelevant
- progress does not justify continuation
- stopping is success, not failure

**Example:**
> We've spent 2 weeks on this migration, but if data integrity is compromised, we stop.  
> The 2 weeks don't matter. Stopping is the right decision.

## Ownership

Kill Criteria must have:
- a clear owner empowered to stop the Change
- explicit authority to override momentum
- protection from blame for stopping

Stopping a Change requires more courage than continuing it.

## Kill Criteria Under Pressure

Kill Criteria matter most under urgency.

During incidents or high-pressure situations:
- teams default to action
- escalation accelerates
- reflection is suppressed

Predefined Kill Criteria reintroduce boundaries when thinking degrades.

## Checklist

Before finalizing Kill Criteria:

- [ ] 1–3 explicit stop conditions defined
- [ ] Each condition is measurable/observable
- [ ] Clear owner for each criterion
- [ ] Decision path when triggered
- [ ] Protection from blame for stopping
- [ ] Independent of sunk cost

## Example Template

```
## Kill Criteria

1. [Condition 1] => [Action]  
   Owner: [Name/Role]

2. [Condition 2] => [Action]  
   Owner: [Name/Role]

3. [Condition 3] => [Action]  
   Owner: [Name/Role]
```
