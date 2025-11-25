# TaskFlow Changelog

## v1.10.0 (November 25, 2025)

### 🎯 Tool Organization System
- Split 54 tools into 40 core (always on) + 14 advanced (optional)
- Add `TASKFLOW_ENABLE_ADVANCED_TOOLS` environment variable
- Create `TOOLS_ORGANIZATION.md` documentation
- Better UX with fewer default tools

## v1.9.0 (November 25, 2025)

### 🔮 Predictive Analytics
- `predict-bottlenecks` - Identify project risks
- `estimate-completion-time` - Time estimation with confidence intervals
- `build-knowledge-graph` - Connect tasks, lessons, and decisions

## v1.8.0 (November 25, 2025)

### 🧠 Code Intelligence
- `get-code-snippets` - Extract reusable code patterns
- `suggest-refactoring` - AI-powered refactoring suggestions
- `generate-test-cases` - Generate comprehensive test templates

## v1.7.0 (November 25, 2025)

### 🤖 Smart Recommendations
- `recommend-next-task` - AI task prioritization
- `suggest-task-breakdown` - Auto-break down complex tasks
- `get-lesson-insights` - Generate insights from lessons

## v1.6.0 (November 25, 2025)

### 🧠 Lessons Learned System
- 5 new tools for recording and learning from mistakes
- 19 new tests (87 total)
- Categories and severity levels

## v1.0.0

🎉 **Initial Release** - Universal Task Management MCP Server

## Features

### ✨ Core Features
- **Universal Project Support** - Works with Laravel, Node.js, Python, React, Vue, Angular, .NET, Go, Rust, and any project type
- **14 MCP Tools** - Complete task lifecycle management through GitHub Copilot Chat
- **Interactive Setup Wizard** - Auto-detects project type and configures automatically
- **Config-Driven Architecture** - Customizable via `taskflow.config.json`
- **Git Integration** - Auto-commit and push on task completion
- **Task Templates** - Pre-built templates for feature, bugfix, and refactoring tasks

### 🛠️ MCP Tools

#### Task Management (4 tools)
- `create-task` - Create new tasks from templates
- `list-tasks` - List tasks by status (active/completed/backlog)
- `get-task` - Get detailed task information
- `search-tasks` - Search tasks by title, ID, or type

#### Workflow Management (5 tools)
- `start-task` - Move task from backlog to active
- `complete-task` - Complete task with auto git commit/push
- `update-task-status` - Update task status manually
- `mark-step` - Mark individual steps as completed
- `add-note` - Add notes, blockers, or deviations

#### Dashboard & Statistics (4 tools)
- `get-dashboard` - View main dashboard overview
- `get-stats` - Get task statistics and metrics
- `get-next-task-id` - Get next available task ID
- `check-git-status` - Check git repository status

### 📦 Project Type Support

Auto-detection for 10 project types:
- Laravel (PHP)
- Node.js (JavaScript/TypeScript)
- Python (Django/Flask)
- React
- Vue
- Angular
- .NET (C#)
- Go
- Rust
- Generic (fallback)

### 🎯 Setup Wizard

Interactive CLI wizard (`taskflow init`) that:
- Detects project type automatically
- Creates `taskflow.config.json`
- Sets up `.plans/` directory structure
- Generates project-specific task templates
- Provides next steps for VS Code configuration

## Installation

### From GitHub
```bash
git clone https://github.com/ptnghia/TaskFlow.git
cd TaskFlow
npm install
npm run build
npm link
```

### Usage
```bash
cd /path/to/your/project
taskflow init
```

## Requirements

- Node.js 18+
- VS Code with GitHub Copilot extension
- Git (optional, for auto-commit feature)

## Configuration

Configure VS Code by adding to `.vscode/mcp.json`:

```json
{
  "servers": {
    "taskflow": {
      "command": "node",
      "args": ["/path/to/TaskFlow/dist/index.js"],
      "env": {
        "WORKSPACE_ROOT": "${workspaceFolder}"
      }
    }
  }
}
```

## Usage Examples

```
💬 "Create a feature task for User Authentication with high priority"
💬 "List all active tasks"
💬 "Start task #001"
💬 "Mark step 2 of task #001 as completed"
💬 "Complete task #001"  ← Auto commits and pushes to git
💬 "Show task statistics"
```

## What's Next?

### Planned for v1.1.0
- Task dependencies validation
- More project type templates
- Task export (PDF, HTML)
- Customizable task workflows

### Planned for v2.0.0
- Multi-user task assignment
- Slack/Discord notifications
- Integration with Jira/Trello
- Team collaboration features

## Known Issues

None reported yet. Please create an issue if you find any bugs.

## Contributors

- Pham Thanh Nghia (@ptnghia)

## Links

- [GitHub Repository](https://github.com/ptnghia/TaskFlow)
- [Documentation](https://github.com/ptnghia/TaskFlow#readme)
- [Issues](https://github.com/ptnghia/TaskFlow/issues)

---

Thank you for using TaskFlow! ⭐ Star us on GitHub if you find this useful!
