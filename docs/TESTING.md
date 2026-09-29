# Testing Strategy

Testing follows the product contract.

## Required layers

### Unit tests

Test:

- input validation
- tool schemas
- Moodle service mapping
- error handling
- secret redaction
- operation classification

### Integration tests

Use a dedicated non-production Moodle instance.

Verify real Moodle API interactions for the supported capability.

### Acceptance tests

Describe the behavior an AI agent should be able to perform through the MCP tool.

Example structure:

- Given a known test Moodle environment
- When the agent calls a specific tool with valid inputs
- Then the expected Moodle state or response is returned
- And no credential value is exposed

## Security checks

Every change must check:

- no credentials committed
- no secrets in logs
- no sensitive data unnecessarily returned
- permissions/capabilities validated
- destructive operations protected by confirmation at the application layer

## Compatibility

The initial baseline is Moodle 5.1.

Changes that depend on another Moodle version must state that dependency explicitly.
