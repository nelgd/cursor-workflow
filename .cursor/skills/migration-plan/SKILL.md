---
name: migration-plan
description: Plans a safe, reversible data or schema migration with rollback strategy.
---

## Workflow: Plan a Migration

### Step 1: Assess the Current State
- Document the current schema, data shape, or system state.
- Identify all services and queries that depend on the affected tables/collections.
- Estimate the data volume (row counts, table sizes) that will be affected.
- Check for active connections, locks, or replication lag concerns.

### Step 2: Define the Target State
- Document the desired schema, data shape, or system state.
- Identify what changes are backward-compatible and what are breaking.
- Determine if a transition period is needed (both old and new code running simultaneously).

### Step 3: Plan the Migration Steps
For each step, specify:
- The exact DDL or DML to run.
- Whether it requires a maintenance window or can run online.
- Estimated duration based on data volume.
- What to monitor during execution.

Typical step order for schema changes:
1. Add new columns/tables (non-breaking).
2. Deploy code that writes to both old and new locations.
3. Backfill existing data to the new location.
4. Deploy code that reads from the new location.
5. Remove the old columns/tables (breaking — do this in a later release).

### Step 4: Write the Rollback Plan
For each migration step, document the exact rollback:
- Rollback SQL/commands.
- Data recovery procedure if data was transformed.
- Point of no return (if any) — the step after which rollback becomes significantly harder.

### Step 5: Define Validation Queries
Write queries to verify:
- Data integrity after migration (counts, checksums, spot checks).
- No orphaned records or broken foreign keys.
- Application health metrics are within normal range.

### Step 6: Plan the Execution
- [ ] Migration tested on a staging environment with production-like data.
- [ ] Rollback tested on staging.
- [ ] Monitoring dashboards identified for during-migration observation.
- [ ] Communication plan for stakeholders (downtime window, expected impact).
- [ ] Runbook written with step-by-step execution instructions.

### Step 7: Produce the Migration Document

```
## Migration: <name>

### Summary
<what changes and why>

### Impact
- Tables affected: <list>
- Estimated data volume: <rows/size>
- Estimated duration: <time>
- Downtime required: yes/no

### Steps
1. <step> — <online/offline> — <estimated time>
2. ...

### Rollback
1. <rollback for step 1>
2. ...

### Point of No Return
<step N, or "fully reversible">

### Validation
- <query and expected result>

### Risks
- <risk and mitigation>
```
