# TaskFlow MCP Server

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue)](https://www.typescriptlang.org/)

> **Universal Task Management for Any Project**

A Model Context Protocol (MCP) server that provides automated task management with GitHub Copilot integration. Control your entire workflow using natural language - no CLI commands needed.

**Works with:** Laravel, Node.js, Python, React, Vue, Angular, .NET, Go, Rust, and any project type!

## ✨ Features

- 🤖 **GitHub Copilot Integration** - Control everything via natural language chat
- 🌐 **Multilingual Support** - English and Vietnamese (Tiếng Việt)
- 🎯 **Auto-generated Copilot Instructions** - Zero configuration, ready immediately after setup
- 📋 **Smart Task Management** - Create, track, and complete tasks with AI assistance
- 🔄 **Workflow Automation** - Automatic status updates, git commits, and progress tracking
- 🎯 **Task Dependencies** - Track relationships and validate circular dependencies
- 📊 **Real-time Dashboard** - Statistics, progress metrics, and task overview
- ⚡ **High Performance** - 99% faster with caching and indexing (tested with 100+ tasks)
- 🔗 **Git Integration** - Auto-commit and push when completing tasks
- 📚 **Documentation Generation** - Auto-generate changelogs, API docs, and architecture overviews
- 🏛️ **Architecture Decisions** - Record and track ADRs with full-text search
- 🌍 **Universal Support** - Works with any programming language or framework

## 🚀 Quick Start

### Installation

```bash
npm install -g @ptnghia/taskflow-mcp
```

> **Note:** The old package `taskflow-mcp` (v1.0.32) is outdated. Use `@ptnghia/taskflow-mcp` for latest v1.10.0 with 54 tools.

> **Verify your version:**
> ```bash
> npm list -g @ptnghia/taskflow-mcp
> # Should show: @ptnghia/taskflow-mcp@1.10.0
> ```

> **Windows Users:** If you get "command not found" after installation, you may need to:
> 1. Close and reopen PowerShell/Terminal
> 2. Or restart VS Code
> 3. Or add npm global bin to PATH (see troubleshooting below)

### Initialize in Your Project

```bash
cd /path/to/your/project
taskflow init
```

> **Troubleshooting "taskflow command not found":** See [Common Issues](#common-issues) section below.

The wizard will:
- Auto-detect your project type (Laravel, Node.js, React, etc.)
- **Select your preferred language** (English or Vietnamese)
- Create `.plans/` directory structure
- Generate `taskflow.config.json`
- Set up task templates
- **Auto-create `.github/copilot-instructions.md`** - GitHub Copilot ready immediately!

### Configure VS Code

Add to your project's `.vscode/mcp.json`:

```json
{
  "servers": {
    "taskflow": {
      "command": "node",
      "args": [
        "/usr/local/lib/node_modules/taskflow-mcp/dist/index.js"
      ],
      "env": {
        "WORKSPACE_ROOT": "${workspaceFolder}"
      }
    }
  }
}
```

> **Important:** Update the path in `args` based on your installation:
> - **Linux/macOS global:** `/usr/local/lib/node_modules/taskflow-mcp/dist/index.js`
> - **Windows global:** `C:\\Users\\YourUsername\\AppData\\Roaming\\npm\\node_modules\\taskflow-mcp\\dist\\index.js`
> - **Local install:** `${workspaceFolder}/node_modules/taskflow-mcp/dist/index.js`
>
> See `.vscode-example/mcp.json.example` for detailed examples and configuration options.

#### Finding Your Installation Path

```bash
# Find npm global modules location
npm root -g
# Append: /taskflow-mcp/dist/index.js to the output
```

#### Enabling Advanced Tools (Optional)

To enable all 54 tools (default is 40 core tools), add to `env`:

```json
"env": {
  "WORKSPACE_ROOT": "${workspaceFolder}",
  "TASKFLOW_ENABLE_ADVANCED_TOOLS": "true"
}
```

This enables 14 additional tools: batch operations, rebuilds, template CRUD, detailed views, and utilities. See `TOOLS_ORGANIZATION.md` for complete list.

### Reload VS Code

Press `Ctrl+Shift+P` → "Developer: Reload Window"

### Verify Installation

Open GitHub Copilot Chat and try:
```
💬 "List all active tasks"
💬 "Show task statistics"
```

If you see TaskFlow responding, you're all set! 🎉

## 💬 Usage Examples

Control TaskFlow using natural language with GitHub Copilot Chat:

### Create Tasks
```
💬 "Create a feature task for User Authentication with high priority"
💬 "Add a bug fix task for login validation issue"
```

### Manage Workflow
```
💬 "List all active tasks"
💬 "Show me task #001"
💬 "Start task #002"
💬 "Complete task #002"  → Auto commits & pushes!
```

### Track Dependencies & Relationships 🆕
```
💬 "Task #005 depends on task #003"
💬 "Link task #017 as parent of task #015"
💬 "Task #012 is related to task #010"
💬 "Show relationships for task #017 with transitive data"
💬 "Find all tasks related to task #015"
💬 "Validate dependencies for all tasks"
```

### Get Insights
```
💬 "Show task statistics"
💬 "Generate a changelog for this month"
💬 "Analyze codebase structure"
```

### Learn from Mistakes (v1.6.0)
```
💬 "Record lesson: TypeScript shebang breaks vitest"
💬 "List all lessons about testing"
💬 "Search lessons for 'circular dependency'"
💬 "Get lessons context for typescript errors"
```

### AI-Powered Features (v1.7.0-v1.9.0) 🤖
```
💬 "Recommend next task to work on"
💬 "Break down task #015 into subtasks"
💬 "Generate insights from all testing lessons"
💬 "Find reusable code snippets in the project"
💬 "Suggest refactoring opportunities"
💬 "Generate test cases for UserController"
💬 "Predict project bottlenecks"
💬 "Estimate completion time for task #020"
💬 "Build knowledge graph of tasks and decisions"
```

### Tool Organization (v1.10.0) 🎯

By default, TaskFlow shows **40 core tools** for a clean experience. Enable all **54 tools** by adding to `.vscode/mcp.json`:

```json
"env": {
  "WORKSPACE_ROOT": "${workspaceFolder}",
  "TASKFLOW_ENABLE_ADVANCED_TOOLS": "true"
}
```

**Advanced Tools (14):**
- `batch-update-tasks` - Update multiple tasks at once
- `rebuild-index` - Rebuild task index
- `check-git-status` - Check git repository status
- `create-project-vision` - Create project vision document
- `sync-todo-list` - Sync todo list with tasks
- `generate-documentation` - Generate project documentation
- `get-decision` - Get detailed ADR content
- `get-lesson` - Get detailed lesson content
- `get-lessons-context` - Get context from lessons
- `find-related-tasks` - Find related tasks
- `create-custom-template` - Create custom task template
- `delete-custom-template` - Delete custom template
- `validate-step` - Alias for mark-step
- `taskflow-mark` - Alias for mark-step

📚 See `TOOLS_ORGANIZATION.md` for complete documentation.

## 🎯 Key Benefits

- ⏱️ **Save Time** - Automate repetitive task operations
- 🧠 **Stay Focused** - Natural language interface, no context switching
- 📈 **Track Progress** - Real-time statistics and visualization
- 🤝 **Collaborate** - Clear task structure for team coordination
- 🔒 **Never Lose Work** - Automatic git integration and backups

## 📚 Documentation

### Core Features

- **54 MCP Tools** - Complete task lifecycle management with smart organization
  - **40 Core Tools** (always enabled) - Essential features for daily workflow
    - 13 Task Management tools (create, list, get, search, start, complete, etc.)
    - 5 Context & Vision tools (dashboard, stats, project vision, analyze codebase)
    - 3 Architecture Decision tools (record, list, search)
    - 3 Lessons Learned tools (record, list, search)
    - 3 Task Relationship tools (link, unlink, get relationships)
    - 2 Template tools (list, get content)
    - 3 AI Smart Recommendations 🤖 (recommend next task, suggest breakdown, lesson insights)
    - 3 Code Intelligence 🧠 (code snippets, refactoring suggestions, test generation)
    - 3 Predictive Analytics 🔮 (bottleneck prediction, time estimation, knowledge graph)
  - **14 Advanced Tools** (optional) - Enable with `TASKFLOW_ENABLE_ADVANCED_TOOLS=true`
    - Batch operations, rebuilds, template CRUD, detailed views, aliases
    - See `TOOLS_ORGANIZATION.md` for complete list

### Project Types Supported

| Type | Language | Auto-Detected From |
|------|----------|-------------------|
| Laravel | PHP | `composer.json` + `artisan` |
| Node.js | JavaScript/TypeScript | `package.json` |
| Python | Python | `requirements.txt`, `pyproject.toml` |
| React | JavaScript/TypeScript | `package.json` with React |
| Vue | JavaScript/TypeScript | `package.json` with Vue |
| Angular | TypeScript | `angular.json` |
| .NET | C# | `*.csproj`, `*.sln` |
| Go | Go | `go.mod` |
| Rust | Rust | `Cargo.toml` |
| Generic | Any | Fallback for other projects |

### Configuration

TaskFlow uses `taskflow.config.json` for project-specific settings. See `taskflow.config.json.example` for a complete template.

Example configuration:
```json
{
  "project": {
    "name": "my-app",
    "type": "nodejs",
    "language": "TypeScript"
  },
  "workflow": {
    "statuses": ["Not Started", "In Progress", "Completed"],
    "priorities": ["High", "Medium", "Low"]
  },
  "git": {
    "enabled": true,
    "autoCommit": true,
    "autoPush": true
  }
}
```

## 🔧 Requirements

- **Node.js** 18+ 
- **VS Code** with GitHub Copilot extension
- **Git** (optional, for auto-commit feature)

## 📖 Examples

See `.plans-example/` directory for:
- Task structure examples
- Template files (feature, bugfix, refactor)
- Directory organization guide

## 🐛 Troubleshooting

### MCP Server Not Working

1. **Check MCP is enabled**: 
   - Settings → search "mcp" 
   - Ensure `github.copilot.chat.mcp.enabled` is `true`

2. **Verify correct path**: 
   - Check `.vscode/mcp.json` points to correct `index.js` location
   - Use `npm root -g` to find global modules path
   - Windows: Use double backslashes `\\` in paths

3. **Rebuild if needed**: 
   ```bash
   cd /path/to/TaskFlow
   npm run build
   ```

4. **Check output panel**: 
   - `Ctrl+Shift+U` → "GitHub Copilot Chat - MCP"
   - Look for error messages

5. **Reload VS Code**: 
   - `Ctrl+Shift+P` → "Developer: Reload Window"
   - MCP changes require reload

### Common Issues

**"taskflow command not found" or "taskflow is not recognized"**

After installing globally, the command might not be available immediately. Try these solutions:

1. **Close and reopen your terminal/PowerShell**
   ```bash
   # Close terminal and open new one, then try:
   taskflow init
   ```

2. **Check if npm global bin is in PATH**
   ```bash
   # Check npm global bin path:
   npm bin -g
   # Windows: C:\Users\YourUsername\AppData\Roaming\npm
   # Linux/macOS: /usr/local/bin
   ```

3. **Add npm global bin to PATH (Windows)**
   - Press `Win + X` → System → Advanced system settings
   - Environment Variables → Edit PATH
   - Add: `C:\Users\YourUsername\AppData\Roaming\npm`
   - Restart terminal

4. **Use npx instead** (no PATH configuration needed)
   ```bash
   npx taskflow-mcp init
   ```

5. **Manual setup without taskflow command**
   ```bash
   # Create directory structure manually:
   mkdir .plans .plans/active .plans/backlog .plans/completed
   mkdir .plans/decisions .plans/lessons
   mkdir .github
   
   # Copy config from repository:
   # Download taskflow.config.json.example and .github/copilot-instructions.md
   # from: https://github.com/ptnghia/TaskFlow
   ```

**"Tool does not have a description" warnings**

You installed the **old package** (`taskflow-mcp@1.0.32`). Install the new package:

```bash
# Uninstall old version
npm uninstall -g taskflow-mcp
npm cache clean --force

# Install latest version
npm install -g @ptnghia/taskflow-mcp

# Verify version
npm list -g @ptnghia/taskflow-mcp  # Should show 1.10.0
```

Then update `.vscode/mcp.json` path (run `npm root -g` to find it) and reload VS Code.

**"Cannot find module"**
- Path in `.vscode/mcp.json` is incorrect
- Run `npm root -g` and verify path
- On Windows, use absolute path with `\\`

**"No tools available"**
- MCP not enabled in settings
- Check `github.copilot.chat.mcp.enabled` is `true`
- Restart VS Code after enabling

**"WORKSPACE_ROOT not set"**
- Add `"WORKSPACE_ROOT": "${workspaceFolder}"` to `env`
- Reload VS Code after adding

**Advanced tools not showing**
- Add `"TASKFLOW_ENABLE_ADVANCED_TOOLS": "true"` to `env`
- Reload VS Code
- Verify with: `💬 "What tools are available?"`

### Need Help?

- 📖 **Setup Issues?** See [SETUP_GUIDE.md](SETUP_GUIDE.md) for detailed troubleshooting
- 🐛 **Check** [GitHub Issues](https://github.com/ptnghia/TaskFlow/issues)
- 📝 **See** [VERSION.md](VERSION.md) for detailed changelog
- 📂 **Review** example files in `.plans-example/` and `.vscode-example/`

## 🤝 Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🌟 Support

If you find TaskFlow useful, please give it a star on [GitHub](https://github.com/ptnghia/TaskFlow)! ⭐

---

**TaskFlow MCP** - Making development workflow smarter, one task at a time.

**Version:** 1.10.0 | **Author:** Phan Trung Nghĩa | **License:** MIT
