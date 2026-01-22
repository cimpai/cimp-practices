# Observation Plan

After execution, the system must be observed.

Observation answers:
- did behavior change as expected?
- were assumptions valid?
- did new risks appear?

Lack of observation turns Change into guesswork.

## Why Observation Matters

Without observation:
- changes succeed or fail invisibly
- assumptions go untested
- risks accumulate silently
- incidents surprise us

With observation:
- we know if Intent was achieved
- we detect problems early
- we validate assumptions
- we learn from changes

## What to Observe

### 1. Intent Achievement

Did the Change achieve its stated Intent?

**Example:**
> Intent: Reduce p95 latency from 450ms to <200ms
>
> Observation:
> - Monitor p95 latency metric
> - Compare before/after
> - Verify target is met

### 2. Risk Validation

Did identified risks materialize?

**Example:**
> Risk: Increased memory usage
>
> Observation:
> - Monitor memory usage per instance
> - Check for OOM errors
> - Verify within acceptable range

### 3. Constraint Compliance

Are constraints still being met?

**Example:**
> Constraint: Uniqueness of email
>
> Observation:
> - Monitor for duplicate email errors
> - Check database constraint violations
> - Verify no duplicates exist

### 4. Unexpected Behavior

Are there any surprises?

**Example:**
> Observation:
> - Monitor error rates
> - Check for new error types
> - Watch for performance anomalies

## Observation Plan Structure

An Observation Plan should include:
- **What to observe:** Metrics, logs, behaviors
- **How to observe:** Tools, queries, dashboards
- **When to observe:** Frequency, duration
- **Success criteria:** What indicates success
- **Alert thresholds:** When to investigate

## Examples

### ❌ Bad Observation Plan

> "Monitor the system"

**Problems:**
- Vague (what to monitor?)
- No success criteria
- No alert thresholds
- No duration

### ✅ Good Observation Plan

> **What to observe:**
> - p95 latency (target: <200ms)
> - Error rate (target: <0.1%)
> - Memory usage (target: <2GB per instance)
>
> **How to observe:**
> - Grafana dashboard: "API Latency"
> - Error logs: grep for ERROR
> - Prometheus: container_memory_usage_bytes
>
> **When to observe:**
> - First hour: every 5 minutes
> - First day: every hour
> - First week: daily
>
> **Success criteria:**
> - p95 latency < 200ms sustained
> - Error rate < 0.1%
> - No memory issues
>
> **Alert thresholds:**
> - p95 latency > 300ms => investigate
> - Error rate > 1% => rollback
> - Memory > 3GB => investigate

**Why it's good:**
- Specific metrics
- Clear tools
- Defined frequency
- Success criteria
- Alert thresholds

## Common Metrics

### Performance

- Latency (p50, p95, p99)
- Throughput (requests per second)
- Resource usage (CPU, memory, disk)

### Reliability

- Error rate
- Availability (uptime)
- Time to recovery

### Business

- User activity
- Transaction volume
- Revenue impact

### Data Integrity

- Constraint violations
- Data inconsistencies
- Missing data

## Observation Duration

Observation should continue until:
- Intent is verified (success or failure)
- Risks are validated (occurred or not)
- System is stable
- No surprises for reasonable period

**Rule of thumb:**
- Critical changes: 1 week minimum
- Medium changes: 3 days minimum
- Low-risk changes: 1 day minimum

## Automated vs Manual

### Automated Observation

Good for:
- Continuous monitoring
- Alerting
- Trend analysis

**Example:**
> Prometheus alerts when error rate > 1%

### Manual Observation

Good for:
- Initial validation
- Deep dives
- Contextual analysis

**Example:**
> Daily review of error logs for first week

## Observation and Kill Criteria

Observation should verify Kill Criteria are not triggered.

If a Kill Criterion is met:
- stop observation
- execute kill criteria action
- document what happened

## Observation Results

Record observation results:
- What was observed
- What changed (or didn't)
- Whether Intent was achieved
- Any surprises
- Lessons learned

**Example:**
> **Observation Results (Day 1):**
> - p95 latency: 180ms ✅ (target: <200ms)
> - Error rate: 0.05% ✅ (target: <0.1%)
> - Memory: 1.8GB ✅ (target: <2GB)
> - No surprises
> - Intent achieved

## Checklist

Before finalizing Observation Plan:

- [ ] What to observe is defined
- [ ] How to observe is specified
- [ ] When to observe is scheduled
- [ ] Success criteria are clear
- [ ] Alert thresholds are set
- [ ] Duration is defined
- [ ] Results will be recorded

## Example Template

```
## Observation Plan

**What to observe:**
- [Metric 1] (target: [value])
- [Metric 2] (target: [value])

**How to observe:**
- [Tool/Method 1]
- [Tool/Method 2]

**When to observe:**
- First hour: [frequency]
- First day: [frequency]
- First week: [frequency]

**Success criteria:**
- [Criterion 1]
- [Criterion 2]

**Alert thresholds:**
- [Metric] > [value] => [action]
```
