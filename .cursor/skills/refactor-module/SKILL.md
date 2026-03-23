---
name: refactor-module
description: Safely refactors a module while preserving behavior and maintaining test coverage.
---

## Workflow: Refactor a Module

### Step 1: Understand the Current State
- Read the module and map its public API (exported functions, types, interfaces).
- Identify all callers and dependents (search for imports/usages across the codebase).
- Run existing tests and record the pass/fail baseline.
- Note the current test coverage for the module.

### Step 2: Define the Goal
- What specific problem does this refactor solve? (readability, performance, extensibility, duplication)
- What is the target structure?
- What must NOT change? (public API, behavior, performance characteristics)

### Step 3: Plan the Changes
- List each transformation as a discrete step.
- Order steps so that tests pass after each one (never break-then-fix).
- Identify which steps can be done as independent commits.

### Step 4: Execute Incrementally
For each step:
1. Make the change.
2. Run tests.
3. Run linter.
4. Verify no public API changes (unless intentional).
5. If tests fail, fix before moving to the next step.

### Step 5: Verify Thoroughly
- Run the full test suite for the module.
- Run tests for all modules that depend on this one.
- Compare the public API before and after — flag any unintended changes.
- Check for performance regressions if the module is on a hot path.

### Step 6: Clean Up
- Remove dead code introduced during the refactor.
- Update imports if file paths changed.
- Update documentation if the module's structure or usage changed.

### Step 7: Summarize
- Describe what changed and why.
- List before/after structure if it helps clarity.
- Note any follow-up refactors that are now possible but were out of scope.
