# Execution Plan

An Execution Plan breaks down a Change into **small, verifiable steps**.

Each step should be:
- independently testable
- reversible if needed
- observable

## Why Execution Plans Matter

Without an Execution Plan:
- changes become monolithic
- rollback becomes all-or-nothing
- progress is hard to measure
- risks accumulate silently

A good Execution Plan enables:
- incremental progress
- early risk detection
- partial rollback
- clear checkpoints

## Structure

Each step should include:
- **Name:** What we're doing
- **Action:** Specific tasks
- **Result:** How we verify completion
- **Rollback:** How to undo if needed (optional)

## Examples

### ❌ Bad Execution Plan

> 1. Implement the feature
> 2. Test it
> 3. Deploy

**Problems:**
- Vague ("implement" = undefined)
- No verification criteria
- No rollback plan
- Steps are too large

### ✅ Good Execution Plan

> ### Step 1 - Create database table
> - Create migration `YYYYMMDDHHMMSS-create-user-profile-table.ts`
> - Add table `user_profile` with columns: `email`, `user_id`, ...
> - Add unique constraint on `email`
> - **Result:** Migration runs successfully on staging
> - **Rollback:** Drop table migration

> ### Step 2 - Backfill existing data
> - Write SQL script to migrate data from `user.metadata` to `user_profile`
> - Run script on staging, verify data integrity
> - **Result:** All existing users have corresponding `user_profile` records
> - **Rollback:** Delete all rows from `user_profile`

> ### Step 3 - Add API endpoint
> - Create `POST /users/:id/profile` endpoint
> - Add validation for email uniqueness
> - **Result:** API returns 409 when email already exists
> - **Rollback:** Remove endpoint, keep table

**Why it's good:**
- Specific, actionable steps
- Clear verification criteria
- Independent steps (can stop after any step)
- Rollback defined

## Common Patterns

### 1. Database Changes

```
### Step 1 - Add column (nullable)
- Add migration with nullable column
- Deploy to staging
- **Result:** Column exists, existing rows have NULL

### Step 2 - Backfill data
- Run data migration script
- Verify all rows have values
- **Result:** No NULL values in new column

### Step 3 - Make column NOT NULL
- Add constraint migration
- Deploy to staging
- **Result:** Constraint enforced, no errors
```

### 2. API Changes

```
### Step 1 - Add new endpoint (parallel to old)
- Create new endpoint, keep old one
- Deploy to staging
- **Result:** Both endpoints work

### Step 2 - Migrate clients
- Update clients to use new endpoint
- Deploy clients
- **Result:** All traffic uses new endpoint

### Step 3 - Remove old endpoint
- Remove old endpoint code
- Deploy
- **Result:** Old endpoint returns 404
```

### 3. Feature Flags

```
### Step 1 - Add feature flag (disabled)
- Add flag, default to false
- Deploy
- **Result:** Feature is off for all users

### Step 2 - Enable for internal users
- Set flag to true for test accounts
- Verify behavior
- **Result:** Feature works for test accounts

### Step 3 - Enable for all users
- Set flag to true globally
- Monitor metrics
- **Result:** Feature works, no errors
```

## Step Size

Steps should be:
- **Small enough** to verify independently
- **Large enough** to make meaningful progress

**Rule of thumb:** Each step should take 1–4 hours,  
and be independently deployable if possible.

## Verification

Each step needs a **verification criterion**.

Good verification:
- ✅ "Migration runs without errors"
- ✅ "All tests pass"
- ✅ "API returns 200 for valid input"

Bad verification:
- ❌ "Looks good"
- ❌ "Seems to work"
- ❌ "No obvious problems"

## Rollback

Not every step needs rollback, but consider:
- Can we undo this step?
- What happens if we stop here?
- Is the system in a safe state?

**Example:**
> Step 1: Add nullable column → Safe, can drop column  
> Step 2: Backfill data → Safe, can delete rows  
> Step 3: Add NOT NULL constraint → Harder to rollback, but safe if Step 2 succeeded

## Dependencies

If steps depend on each other, make it explicit:

```
### Step 2 - Add validation (depends on Step 1)
- Requires: Step 1 completed
- Add validation logic
- **Result:** Validation rejects invalid input
```

## Progress Tracking

Use checkboxes to track progress:

```
### Step 1 - Create table
- [x] Migration written
- [x] Tested on staging
- [ ] Deployed to production
```

## Checklist

Before finalizing Execution Plan:

- [ ] Steps are small and independent
- [ ] Each step has verification criteria
- [ ] Rollback is considered for risky steps
- [ ] Dependencies are explicit
- [ ] Steps can be stopped at any point
- [ ] Progress is trackable
