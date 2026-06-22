# ClickUp MCP

**Source**: https://clawhub.ai/pvoo/clickup-mcp

Access ClickUp via official MCP server. Full workspace search, task management, time tracking, comments, chat, and docs.

## Setup

### Option 1: Direct OAuth (Supported Clients Only)

ClickUp MCP only allows OAuth from allowlisted clients: Claude Desktop, Claude Code, Cursor, VS Code, Windsurf, ChatGPT

```bash
# Claude Code
claude mcp add clickup --transport http https://mcp.clickup.com/mcp
# Then /mcp in session to authorize
```

### Option 2: mcporter (Recommended)

1. Authorize via Claude Code
2. Extract token: `jq -r '.mcpOAuth | to_entries | .[] | select(.key | startswith("clickup")) | .value.accessToken' ~/.claude/.credentials.json`
3. Add to `~/.clawdbot/.env`: `CLICKUP_TOKEN=your_token`
4. Configure mcporter with baseUrl and headers

## Available Tools (32)

### Search
- `clickup_search` - Universal search across tasks, docs, dashboards, chat, files

### Tasks
- `clickup_create_task` - Create task with name, description, status, assignees, due date, priority
- `clickup_get_task` - Get task details
- `clickup_update_task` - Update any task field
- `clickup_attach_task_file` - Attach file to task
- `clickup_add_tag_to_task` / `clickup_remove_tag_from_task`

### Comments
- `clickup_get_task_comments` - Get all comments
- `clickup_create_task_comment` - Add comment (supports @mentions)

### Time Tracking
- `clickup_start_time_tracking` - Start timer
- `clickup_stop_time_tracking` - Stop timer
- `clickup_add_time_entry` - Log time manually
- `clickup_get_task_time_entries` - Get time entries
- `clickup_get_current_time_entry` - Check active timer

### Workspace
- `clickup_get_workspace_hierarchy` - Full structure (Spaces, Folders, Lists)
- `clickup_create_list` / `clickup_create_folder`
- `clickup_get_list` / `clickup_get_folder`
- `clickup_update_list` / `clickup_update_folder`

### Members
- `clickup_get_workspace_members` - List all members
- `clickup_find_member_by_name` - Find by name/email

### Chat
- `clickup_get_chat_channels` - List channels
- `clickup_send_chat_message` - Send message

### Docs
- `clickup_create_document` - Create Doc
- `clickup_list_document_pages` / `clickup_get_document_pages`
- `clickup_create_document_page` / `clickup_update_document_page`

## Usage Examples

```bash
# Search
mcporter call 'clickup.clickup_search(keywords: "Q4 marketing", count: 10)'

# Create Task
mcporter call 'clickup.clickup_create_task(name: "Review PR #42", list_id: "901506994423", status: "to do")'

# Start Timer
mcporter call 'clickup.clickup_start_time_tracking(task_id: "abc123", description: "Working on feature")'
```

---

*Install date: 2026-04-27*
