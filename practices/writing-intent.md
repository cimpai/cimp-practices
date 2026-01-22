# Writing Intent

Intent defines **why a change exists**.

A good Intent is falsifiable, outcome-oriented, and acknowledges trade-offs.

## Checklist

Before finalizing Intent, verify:

- [ ] Can this intent be proven wrong?
- [ ] Would two reasonable people interpret success the same way?
- [ ] Is the urgency real or implied?
- [ ] Are trade-offs acknowledged?
- [ ] Is there a clear owner?

## Structure

A minimal Intent statement usually fits in **3–6 lines**:

```
**Goal:** [Concrete, measurable outcome]

**Not goal:** [What we explicitly are NOT doing]

**Why now:** [Why this change is necessary now]

**Trade-off:** [What compromise we're accepting]

**Owner:** [Accountable decision-maker]
```

## Examples

### ❌ Bad Intent

> "Improve performance"

**Problems:**
- Not falsifiable (how do we know it improved?)
- Not outcome-oriented (what outcome matters?)
- No urgency
- No trade-offs

### ✅ Good Intent

> **Goal:** Reduce p95 latency of user profile reads from ~450ms to under 200ms under peak load.  
> **Not goal:** Rewrite the entire profile service.  
> **Why now:** Current latency blocks onboarding enterprise customers who require <300ms SLA.  
> **Trade-off:** Increased memory usage (~2GB per instance).  
> **Owner:** Backend platform lead.

**Why it's good:**
- Falsifiable (can measure p95 latency)
- Outcome-oriented (specific metric with target)
- Urgency explained (blocks enterprise onboarding)
- Trade-off acknowledged (memory cost)

## Common Pitfalls

1. **Intent describes solution, not problem**
   - ❌ "Introduce Redis caching"
   - ✅ "Reduce latency to meet SLA"

2. **Intent is too vague**
   - ❌ "Make it more reliable"
   - ✅ "Reduce error rate from 2% to <0.1%"

3. **Intent lacks urgency**
   - ❌ "Improve user experience"
   - ✅ "Fix checkout flow before Black Friday (2 weeks)"

4. **Intent ignores trade-offs**
   - ❌ "Add monitoring without any cost"
   - ✅ "Add monitoring, accepting 5% overhead"

## Intent vs Solution

Intent should remain stable even if the solution changes.

If changing the solution requires rewriting the Intent,  
the Intent was likely a solution description.

**Example:**
- Intent: "Reduce checkout latency to <200ms"
- Solution A: Add caching
- Solution B: Optimize database queries
- Solution C: Use CDN

The Intent stays the same. Only the solution changes.

## Reviewing Intent

Before accepting a change, ask:

1. **Falsifiability:** Can we measure if this succeeded?
2. **Clarity:** Would a new team member understand the goal?
3. **Urgency:** What happens if we delay this?
4. **Trade-offs:** What are we giving up?
5. **Ownership:** Who is accountable?

If these questions cannot be answered,  
the change is not ready.
