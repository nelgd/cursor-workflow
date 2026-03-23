---
name: add-endpoint
description: Adds a backend endpoint with validation, tests, and documentation.
---

## Workflow: Add a New API Endpoint

### Step 1: Discover Patterns
- Find existing endpoint definitions (routes, controllers, handlers).
- Note the project's layering: handler → service → repository.
- Identify the validation, error handling, and response formatting patterns.

### Step 2: Define the Endpoint
- HTTP method and path (following existing naming conventions).
- Request body / query params / path params with types.
- Response shape and status codes (success + error cases).
- Authentication and authorization requirements.

### Step 3: Implement
- Add the route registration.
- Add the handler/controller with input validation.
- Add the service-layer logic.
- Add data access if needed (queries, models).
- Wire up middleware (auth, logging) consistent with other endpoints.

### Step 4: Validate Inputs
- Add validation for all user-provided inputs.
- Return 422 with specific field-level error messages for invalid input.
- Sanitize inputs that will be stored or rendered.

### Step 5: Write Tests
- Unit test the handler with mocked service.
- Unit test the service with mocked repository.
- Integration test the full endpoint (if the project has integration tests).
- Test cases: happy path, validation errors, not found, unauthorized.

### Step 6: Update Documentation
- Add the endpoint to API docs or OpenAPI spec.
- Include request/response examples.
- Document any new environment variables or configuration.

### Step 7: Verify
- Run linter on all touched files.
- Run the new tests.
- Run existing tests for the same module to check for regressions.

### Step 8: Summarize
- List all files created or modified.
- Note any follow-up work (e.g., frontend integration, monitoring alerts).
- Flag any risks or assumptions.
