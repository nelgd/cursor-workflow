---
name: security-review
description: Performs a focused security review of code changes or a specific module.
---

## Workflow: Security Review

### Step 1: Scope the Review
- Identify the files, endpoints, and data flows under review.
- Determine the trust boundaries — where does untrusted input enter?
- Note what sensitive data is handled (PII, credentials, tokens, financial data).

### Step 2: Input Validation
- [ ] All user inputs validated at the boundary (type, length, format, range).
- [ ] SQL queries use parameterized statements — no string concatenation.
- [ ] HTML output is escaped to prevent XSS.
- [ ] File paths are sanitized to prevent directory traversal.
- [ ] Deserialization is restricted to expected types.

### Step 3: Authentication & Authorization
- [ ] Endpoints enforce authentication where required.
- [ ] Authorization checks use the current user's permissions, not client-provided roles.
- [ ] Session tokens are generated with sufficient entropy.
- [ ] Password handling uses bcrypt/scrypt/argon2 — never plain text or weak hashes.
- [ ] Token expiration and refresh are implemented correctly.

### Step 4: Data Protection
- [ ] Sensitive data is encrypted at rest and in transit.
- [ ] Secrets are not hardcoded — loaded from environment or secret manager.
- [ ] Logs do not contain sensitive data (passwords, tokens, PII).
- [ ] Error messages do not leak internal details (stack traces, SQL, file paths).
- [ ] PII handling complies with relevant regulations (GDPR, CCPA).

### Step 5: Access Control
- [ ] Principle of least privilege applied to service accounts and API keys.
- [ ] CORS configured to allow only expected origins.
- [ ] Rate limiting in place for public endpoints.
- [ ] Admin endpoints are not accessible without elevated permissions.

### Step 6: Dependencies
- [ ] No known vulnerabilities in direct dependencies (run `npm audit`, `go vuln check`, etc.).
- [ ] Dependencies are pinned to specific versions.
- [ ] No unnecessary dependencies added.

### Step 7: Report

```
## Security Review Report

### Scope
<files and systems reviewed>

### Findings

#### Critical
- <finding with location and remediation>

#### High
- <finding with location and remediation>

#### Medium
- <finding with location and remediation>

#### Low / Informational
- <finding>

### Not Reviewed
- <areas explicitly out of scope>

### Verdict
PASS / FAIL / CONDITIONAL PASS (with required remediations)
```
