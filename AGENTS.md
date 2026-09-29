# AGENTS.md

## Project

This repository is the Moodle MCP server. It exposes safe, explicit Moodle capabilities to AI agents through MCP.

## Source of truth

Follow this order:

1. Product and architecture documentation
2. Acceptance tests
3. Existing implementation
4. Agent assumptions

Do not invent Moodle APIs, parameters, capabilities, or behavior.

## Moodle rules

- Baseline target: Moodle 5.1 unless a task explicitly changes it.
- Prefer official Moodle APIs / Web Services over direct database access.
- Do not access Moodle databases directly when an appropriate supported API exists.
- Validate Moodle context, capabilities, permissions, and identifiers before write operations.
- Treat user, grade, enrollment, course, group, and activity data as potentially sensitive.
- Never expose tokens, passwords, session data, or internal credentials to an AI model.
- Destructive operations must be explicit and protected by confirmation at the calling application layer.

## Tool design

- Prefer semantic tools with narrow responsibilities.
- Avoid a giant action/multiplexer tool when several focused tools are possible.
- Separate read-only, write, and destructive operations.
- Define stable input/output schemas.
- Return structured, useful errors without leaking secrets.
- Keep Telegram, WhatsApp, Web Chat, and n8n outside this repository.

## Development workflow

- Work in small branches.
- One coherent change per pull request.
- Add or update acceptance tests for user-visible behavior.
- Add unit/integration tests for implementation changes.
- Review security implications for every tool that can write to Moodle.
- Never broaden scope silently.
- Do not add dependencies without a documented reason.

## First implementation rule

Before implementing a capability:

1. Locate the equivalent behavior in the existing blurr_assist project or official Moodle documentation/source.
2. Write the expected contract and acceptance criteria.
3. Identify whether it is a primitive Moodle capability or a higher-level business workflow.
4. Implement the smallest tested slice.
5. Run tests and review the diff for secrets, permissions, and accidental scope expansion.
