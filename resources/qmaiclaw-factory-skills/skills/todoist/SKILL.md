---
name: todoist
description: Manage Todoist tasks and projects via the Todoist REST API. Use when a user wants to add, complete, or search Todoist tasks.
homepage: https://todoist.com
metadata: {"openclaw":{"emoji":"✅","requires":{"bins":["curl"],"env":["TODOIST_API_KEY"]}}}
---

# Todoist

Use the Todoist REST API to manage tasks and projects.

## Setup

Get your API token from: https://todoist.com/settings/integrations/developer

```bash
export TODOIST_API_KEY="your-api-key-here"
```

## Common Commands

**Tasks:**
- List active tasks: `curl -s -H "Authorization: Bearer $TODOIST_API_KEY" "https://api.todoist.com/rest/v2/tasks"`
- Add task: `curl -s -X POST "https://api.todoist.com/rest/v2/tasks" -H "Authorization: Bearer $TODOIST_API_KEY" -H "Content-Type: application/json" -d '{"content": "Buy groceries", "priority": 4}'`
- Complete task: `curl -s -X POST "https://api.todoist.com/rest/v2/tasks/{task_id}/close" -H "Authorization: Bearer $TODOIST_API_KEY"`
- Delete task: `curl -s -X DELETE "https://api.todoist.com/rest/v2/tasks/{task_id}" -H "Authorization: Bearer $TODOIST_API_KEY"`

**Projects:**
- List projects: `curl -s -H "Authorization: Bearer $TODOIST_API_KEY" "https://api.todoist.com/rest/v2/projects"`
- Create project: `curl -s -X POST "https://api.todoist.com/rest/v2/projects" -H "Authorization: Bearer $TODOIST_API_KEY" -H "Content-Type: application/json" -d '{"name": "Work Projects"}'`

## Notes

- Task IDs come from listing tasks first
- Use `--json` output where available for easier parsing