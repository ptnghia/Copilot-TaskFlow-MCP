# .plans Directory Structure

This directory contains task management files. When you run `taskflow init`, this structure will be created in your project.

## Structure

```
.plans/
├── README.md              # Dashboard overview
├── active/                # Tasks currently in progress
├── backlog/               # Tasks not yet started
├── completed/             # Archived completed tasks (organized by month)
├── templates/             # Task templates (feature, bugfix, refactor)
└── decisions/             # Architecture Decision Records (ADR)
```

## Task Files

Each task is a markdown file with:
- Task metadata (ID, type, priority, status)
- Description and goals
- Acceptance criteria
- Technical details
- Progress tracking

## Example Task

See `templates/` for task templates you can use as reference.

## Usage

After initializing TaskFlow in your project:

```bash
taskflow init
```

You can manage tasks via GitHub Copilot Chat:
- "Create a feature task for User API"
- "List all active tasks"
- "Complete task #001"

See [README.md](../README.md) for full documentation.
