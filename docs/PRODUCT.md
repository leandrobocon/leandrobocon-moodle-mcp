# Product Contract

## Purpose

Create a reusable MCP capability layer that allows AI agents to operate Moodle through explicit, typed, permission-aware tools.

## Scope

The initial product focuses on Moodle capabilities and workflows already proven in blurr_assist, while making them reusable outside n8n.

### In scope

- Moodle authentication and configuration at runtime
- Course and activity discovery
- User and enrollment operations
- Groups and cohorts where supported by the chosen Moodle API
- Activity creation and configuration where supported
- Reporting and read operations
- Higher-level workflows derived from proven blurr_assist behavior
- Audit-friendly structured responses

### Out of scope

- Telegram integration
- WhatsApp integration
- Web Chat UI
- n8n workflow orchestration
- AI model selection
- Direct database administration
- Generic Moodle administration that has not yet been specified

## Design principles

1. Security first.
2. Official Moodle APIs before custom mechanisms.
3. Explicit schemas over free-form commands.
4. Read-only operations should be easy to inspect and test.
5. Writes must validate permissions and inputs.
6. Destructive operations require explicit confirmation at the calling application layer.
7. Every capability must have tests.
8. Business rules belong in the service and tool layer, not in chat-channel workflows.
9. The MCP layer must remain independently usable by multiple agents.

## Capability model

Capabilities are classified as:

- read: no Moodle state mutation
- write: creates or updates state
- destructive: deletes or otherwise causes irreversible or high-impact state changes

## First milestone

Choose one existing blurr_assist process and migrate only that process into a tested MCP capability.

The process must be documented before implementation.
