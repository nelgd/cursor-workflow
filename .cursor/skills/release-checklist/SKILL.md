---
name: release-checklist
description: Runs through a pre-release checklist to validate readiness for deployment.
---

## Workflow: Release Checklist

### Step 1: Code Freeze Verification
- [ ] All planned features for this release are merged.
- [ ] No open PRs that should be included.
- [ ] Feature flags are set correctly for the release.

### Step 2: Test Suite
- [ ] Full test suite passes (unit, integration, e2e).
- [ ] No new test failures compared to the previous release.
- [ ] Flaky tests are documented and triaged (not just skipped).

### Step 3: Static Analysis
- [ ] Linter passes with zero errors on the release branch.
- [ ] No new security vulnerabilities in dependency scan.
- [ ] No new high/critical issues in static analysis.

### Step 4: Database
- [ ] All migrations run cleanly on a fresh database.
- [ ] All migrations run cleanly on a production-like database copy.
- [ ] Rollback migrations tested.
- [ ] No data loss risk identified.

### Step 5: Configuration
- [ ] Environment variables documented for any new config.
- [ ] Secrets rotated if needed.
- [ ] Feature flags reviewed and documented.

### Step 6: Performance
- [ ] No performance regressions in benchmark tests.
- [ ] Load test results reviewed (if applicable).
- [ ] Resource limits (memory, CPU, connections) checked.

### Step 7: Documentation
- [ ] Changelog updated with all user-facing changes.
- [ ] API docs updated for any endpoint changes.
- [ ] Deployment runbook updated if the process changed.
- [ ] Breaking changes documented with migration guides.

### Step 8: Deployment Readiness
- [ ] Deployment to staging successful.
- [ ] Smoke tests pass on staging.
- [ ] Rollback plan documented and tested.
- [ ] Monitoring and alerting in place for key metrics.
- [ ] On-call team briefed on the release.

### Step 9: Sign-Off
- Report the checklist results.
- Flag any items that failed or were skipped.
- Recommend GO or NO-GO with reasoning.
