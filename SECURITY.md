# Security

## Non-negotiable rules

1. Never commit Moodle tokens, passwords, API keys, cookies, session IDs, webhook secrets, or private certificates.
2. Never place real credentials in source code, examples, fixtures, README files, issues, or documentation.
3. Use environment variables or a dedicated secret manager for runtime credentials.
4. Test data must use synthetic credentials and non-production Moodle instances.
5. Logs and error messages must redact authentication material and sensitive personal data.
6. Destructive Moodle operations must be explicitly identified and require a confirmation flow at the application layer.
7. The MCP server must not expose raw credentials to the model or return them through tool output.
8. Prefer Moodle official APIs and capability/context checks over direct database access.
9. Security-sensitive changes require review before merge.
10. If a credential is accidentally committed, treat it as compromised: revoke or rotate it first, then remove it from source and, when necessary, repository history.

## Local development

Create `.env` from `.env.example`. Do not commit `.env`.

## Credential handling

The server should load credentials only at runtime. Tool schemas and tool results must never contain the credential value.

## Reporting

Do not report secrets in issues or pull requests. Describe the secret type and location using a redacted reference.
