# Moodle MCP

MCP server for exposing safe, explicit Moodle capabilities to AI agents.

## Status

Early project setup. No Moodle integration has been implemented yet.

## Goals

- Provide a reusable Moodle capability layer for AI agents.
- Support Moodle 5.1 as the initial baseline.
- Prefer official Moodle APIs / Web Services.
- Keep authentication and secrets outside the repository.
- Separate read-only, write, and destructive operations.
- Make capabilities testable and auditable.
- Keep communication channels and orchestration outside the MCP layer.

## Architecture direction

```
AI Agent
   |
   v
Moodle MCP
   |
   v
Moodle API / Web Services
   |
   v
Moodle
```

The existing blurr_assist project is a source of domain requirements and existing Moodle workflows. It is not being copied wholesale into this repository.

## Security

Real credentials must never be committed. Use environment variables locally; see .env.example and SECURITY.md.

## Development

The repository is intentionally being built spec-first:

```
Product contract
  -> acceptance tests
  -> implementation
  -> unit/integration tests
  -> security review
```

## License

MIT. See LICENSE.
