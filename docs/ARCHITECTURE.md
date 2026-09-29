# Architecture

## Target boundary

The MCP server is a reusable Moodle capability layer. It is not a chat interface and it is not the business workflow engine of n8n.

```
AI Agent
   |
   | MCP
   v
Moodle MCP
   |
   +--> Tool layer
   |
   +--> Moodle service layer
   |
   +--> Moodle API / Web Services
   |
   v
Moodle
```

## Responsibilities

### MCP layer

- Expose explicit tool schemas.
- Validate tool inputs.
- Classify operations as read, write, or destructive.
- Return structured results and errors.
- Avoid leaking secrets.

### Moodle service layer

- Encapsulate Moodle API calls.
- Validate Moodle-specific identifiers and permissions.
- Keep Moodle implementation details out of MCP handlers.
- Prefer official Moodle APIs.

### Channel/orchestration layer

Outside this repository:

- Telegram
- WhatsApp
- Web Chat
- n8n workflows
- Conversation memory
- Model-specific prompting

## Existing system relationship

blurr_assist remains a separate system. It may become an MCP client and continue providing channel orchestration.

Existing blurr_assist plugins and workflows are requirements and implementation references, not code to copy without review.

## Tool granularity

Prefer focused semantic tools such as:

- moodle_search_users
- moodle_get_user
- moodle_create_user
- moodle_update_user
- moodle_search_courses
- moodle_list_course_groups
- moodle_list_activities

Higher-level business workflows can be added when they represent a stable, tested domain operation.

Avoid a single generic action parameter that multiplexes unrelated operations.
