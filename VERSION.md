# TaskFlow MCP Server - Version History

## v1.10.0 (November 25, 2025) - Tool Organization System

### 🎯 Major Features
- **Tool Organization** - Split 54 tools into core (40) and advanced (14)
  - Core tools always enabled for clean UX
  - Advanced tools optional via `TASKFLOW_ENABLE_ADVANCED_TOOLS=true`
  - Better organization and discoverability
  
- **Core Tools (40)** - Essential features always available
  - Task Management (13 tools)
  - Context & Vision (5 tools)
  - Decisions (3 tools)
  - Lessons (3 tools)
  - Relationships (3 tools)
  - Templates (2 tools)
  - AI Smart Recommendations (3 tools)
  - Code Intelligence (3 tools)
  - Predictive Analytics (3 tools)
  
- **Advanced Tools (14)** - Optional features
  - Batch operations, rebuilds, detailed views
  - Template creation/deletion
  - Aliases and utilities

### 📚 Documentation
- New file: `TOOLS_ORGANIZATION.md` - Complete tool reference
- Updated `.vscode/mcp.json` with usage instructions
- Environment variable configuration guide

### ✅ Tasks Completed
- #010: Tool Organization System (2h)

---

## v1.9.0 (November 25, 2025) - Predictive Analytics

### 🔮 Major Features
- **Predictive Analytics** - AI-powered project predictions
  - New tool: `predict-bottlenecks` - Identify project bottlenecks
  - New tool: `estimate-completion-time` - Estimate task completion
  - New tool: `build-knowledge-graph` - Connect tasks/lessons/decisions

### ✅ Tasks Completed
- #007: predict-bottlenecks Tool (2.5h)
- #008: estimate-completion-time Tool (2h)
- #009: build-knowledge-graph Tool (3h)

---

## v1.8.0 (November 25, 2025) - Code Intelligence

### 🧠 Major Features
- **Code Intelligence** - Smart code analysis tools
  - New tool: `get-code-snippets` - Extract reusable code patterns
  - New tool: `suggest-refactoring` - AI refactoring suggestions
  - New tool: `generate-test-cases` - Generate test templates

### ✅ Tasks Completed
- #004: get-code-snippets Tool (2h)
- #005: suggest-refactoring Tool (2.5h)
- #006: generate-test-cases Tool (2h)

---

## v1.7.0 (November 25, 2025) - Smart Recommendations

### 🤖 Major Features
- **AI Smart Recommendations** - Intelligent task suggestions
  - New tool: `recommend-next-task` - AI task prioritization
  - New tool: `suggest-task-breakdown` - Auto-break down tasks
  - New tool: `get-lesson-insights` - Generate insights from lessons

### ✅ Tasks Completed
- #001: recommend-next-task Tool (2h)
- #002: suggest-task-breakdown Tool (3h)
- #003: get-lesson-insights Tool (2h)

---

## v1.6.0 (November 25, 2025) - Lessons Learned System

### 🧠 Major Features
- **Lessons Learned System** - AI-powered learning from coding mistakes
  - New tool: `record-lesson-learned` - Document problems and solutions
  - New tool: `list-lessons` - Browse lessons with filtering (category, tags, severity)
  - New tool: `get-lesson` - Retrieve full lesson content by ID
  - New tool: `search-lessons` - Full-text search across lessons
  - New tool: `get-lessons-context` - AI-optimized context for learning
  
- **Lesson Management** - Complete infrastructure
  - Auto-numbering system (0001-9999)
  - Markdown storage in `.plans/lessons/`
  - JSON index for fast metadata lookups
  - Categories: Testing, Build, Git, Performance, API, TypeScript, Dependencies, Configuration, Other
  - Severity levels: critical 🔴, major 🟡, minor 🟢

### 📊 Testing & Validation
- Added 19 comprehensive tests for lessons functionality
- Total test count: 68 → **87 tests**
- 100% pass rate maintained
- Coverage: saveLesson, loadLesson, getLessonsList, searchLessons, edge cases

### 📚 Documentation Updates
- Updated README.md with Lessons Learned section
- Tool count increased: 32 → **36 tools**
- Added natural language examples
- First lesson recorded: TypeScript Shebang Breaking Vitest

### ✅ Tasks Completed
- #031: Infrastructure Setup (3h)
- #032: record-lesson-learned Tool (2h)
- #033: list-lessons Tool (1.5h)
- #034: get-lesson Tool (1h)
- #035: search-lessons Tool (2h)
- #036: get-lessons-context AI Tool (2h)
- #037: Unit Tests (3h)
- #038: Documentation (2h)

---

## v1.5.0 (November 25, 2025) - Simplified Tools Architecture

### 🎯 Major Improvements
- **Simplified Tool Structure** - Reduced from 61 tools (with aliases) to **32 core tools**
  - Removed 34 redundant alias tools
  - Kept only 2 working aliases (validate-step, taskflow-mark)
  - Cleaner tool definitions and better maintainability
  
- **Tool Organization** - Clear categorization
  - 4 Task Management tools
  - 8 Workflow tools
  - 7 Dashboard/Statistics tools
  - 4 Project Vision tools
  - 3 AI Context tools
  - 4 ADR tools
  - 2 Alias tools

### 📊 Testing & Validation
- Comprehensive MCP tool testing
- All 32 tools verified working correctly
- Performance benchmarks maintained
- Cache hit rate optimization

### 🧹 Code Cleanup
- Removed backup files (index-backup-v134.ts, index-broken.ts, index-temp.ts)
- Cleaned up test result files
- Organized project structure
- Updated all documentation

### 📚 Documentation Updates
- Updated README.md with accurate tool counts
- Updated VERSION.md with v1.5.0 changelog
- Updated PROJECT-STRUCTURE.md
- Corrected all tool references from 61 to 32

---

## v1.3.0 (November 24, 2025) - AI Context Engine

### 🤖 Major Features
- **AI Context Engine** - Comprehensive context for AI coding assistants
  - New tool: `analyze-codebase` - Project structure & tech stack detection
  - New tool: `get-task-context` - Task info with git diffs & related tasks
  - New tool: `generate-documentation` - Auto-generate 4 doc types
  - New tool: `record-decision` - Architecture Decision Records (ADR)
  - New tool: `list-decisions` - Browse all ADRs with filtering
  - New tool: `get-decision` - Get full ADR content
  - New tool: `search-decisions` - Search ADRs by keyword

### 🎯 Codebase Analysis
- **Tech Stack Detection**
  - Auto-detect Laravel, Node.js, React, Vue, Express
  - Parse package.json, composer.json for versions
  - Framework & library identification
  
- **Directory Scanning**
  - Configurable depth (default: 5 levels)
  - Ignores vendor, node_modules, .git
  - Tree structure visualization
  
- **Code Statistics**
  - Total files, lines of code
  - File counts by type (PHP, JS, TS)
  - Task-to-file mapping from git history

### 📋 Task Context System
- **Comprehensive Task Information**
  - Task metadata (title, type, priority, status)
  - Description & technical decisions
  - Blockers & notes extraction
  
- **Git Integration**
  - Full git diff from task commit
  - Configurable max diff lines (default: 500)
  - Automatic truncation for large diffs
  
- **Related Tasks**
  - Dependencies (tasks this depends on)
  - Blocked tasks (tasks depending on this)
  - Status indicators for each
  
- **File Tracking**
  - List of modified files
  - Git history analysis
  - Up to 20 files displayed

### 📚 Documentation Generation
- **4 Documentation Types**
  1. **Changelog** - Monthly grouping, organized by type
  2. **API Docs** - Tech stack, endpoints, features
  3. **Architecture** - System overview, tech table, directory tree
  4. **Summary** - Statistics, recent activity, current work
  
- **Features**
  - Markdown/HTML output support
  - Task link inclusion
  - Date range filtering
  - Auto-generated from tasks

### 🏛️ Architecture Decision Records (ADR)
- **ADR Creation**
  - Standard template (Context, Decision, Alternatives, Consequences)
  - Auto-numbering (0001, 0002, etc.)
  - 4 statuses: proposed, accepted, deprecated, superseded
  - Link to related tasks
  
- **ADR Management**
  - List all ADRs with status grouping
  - Filter by status or related task
  - Full-text search across all ADRs
  - Stored in .plans/decisions/
  
- **Benefits**
  - Capture "why" not just "what"
  - Prevent repeated mistakes
  - Improve AI code suggestions
  - Knowledge retention

### 🔧 MCP Tools (27 total, +7 new)
- 4 Task Management tools
- 8 Workflow tools
- 4 Dashboard/Stats tools
- 3 Project Vision tools
- 1 Git integration tool
- **3 AI Context tools (NEW)** ⭐
- **4 ADR tools (NEW)** ⭐

### 📈 Performance
- Fast codebase analysis (< 2 seconds)
- Efficient directory scanning
- Cached task lookups
- Optimized git operations

### 💡 Impact
- **Better AI Suggestions** - AI có full context về project
- **Auto Documentation** - Docs luôn sync với code
- **Knowledge Retention** - ADRs giữ lại decisions
- **Traceability** - Link tasks ↔ decisions ↔ code
- **Faster Onboarding** - New devs understand instantly

### 🎯 Use Cases
1. **AI Coding** - Provide context cho GitHub Copilot
2. **Code Review** - Get task context với git diff
3. **Documentation** - Auto-generate changelog, API docs
4. **Architecture** - Record & search design decisions
5. **Onboarding** - Understand project structure quickly

---

## v1.2.0 (November 23, 2025) - Project Vision Management

### 🎯 Major Features
- **Project Vision Tools** - AI-powered project requirements management
  - New tool: `get-project-vision` - View PROJECT.md content
  - New tool: `create-project-vision` - AI-generate PROJECT.md
  - New tool: `validate-task-alignment` - Check task alignment with vision

- **PROJECT.md Template** (1,150 lines)
  - Vision & mission statements
  - Project goals (Primary, Secondary, Long-term)
  - Product philosophy & principles
  - Functional requirements (Must-have, Planned, Future)
  - User personas (5 detailed profiles)
  - Technical architecture & stack
  - Success metrics (KPIs)
  - Competitive positioning
  - Strategic roadmap alignment
  - Definition of done

### ✨ New Capabilities
- **AI-Generated PROJECT.md**
  - Auto-generate from project context
  - Customizable sections
  - Version tracking
  - Change log

- **Task Alignment Validation**
  - 4 automated checks:
    1. Referenced in PROJECT.md
    2. Priority alignment
    3. Dependencies defined
    4. Task type relevance
  - Alignment score: 0-100%
  - Recommendations for misaligned tasks

### 🔧 MCP Tools (20 total, +3 new)
- 4 Task Management tools
- 8 Workflow tools (including 3 dependency tools)
- 4 Dashboard/Stats tools
- **3 Project Vision tools (NEW)** ⭐
- 1 Git integration tool

### 💡 Benefits
- **Setup nhanh** - AI generate PROJECT.md in 5 seconds
- **Giữ định hướng** - All tasks check alignment with vision
- **Tránh scope creep** - Misaligned tasks get warnings
- **Onboarding dễ** - New devs understand project instantly
- **Decision making** - Clear vision → faster decisions

### 📁 Files Changed
- `src/index.ts`: +250 lines (3 new methods: getProjectVision, createProjectVision, validateTaskAlignment)
- `PROJECT.md`: +1,150 lines (new template)
- `README.md`: Updated documentation for 3 new tools

### 🔗 Commits
- `c24dbcb` - feat: Add 3 MCP tools for project vision management + PROJECT.md template

---

## v1.1.0 (November 23, 2025) - Performance Optimization

### 🚀 Major Features
- **Task Caching System** with 5-minute TTL
  - 99.1% performance improvement
  - 106x speedup (16.16ms → 0.12ms)
  - Automatic cache invalidation
  - Cache statistics tracking

- **Task Index System** with persistent JSON storage
  - 78.3% performance improvement
  - 4.6x speedup (4.65ms → 1.01ms)
  - 3-tier lookup optimization (Cache → Index → Full Scan)
  - Auto-save every 5 minutes

- **New MCP Tool:** `rebuild-index`
  - Manual index rebuild capability
  - Corruption recovery

### 🧪 Testing
- Added 15 comprehensive unit tests for `validateDependencies`
- All tests passing (63/63 total)
- Performance validation: 50-task chain < 100ms

### 🐛 Bug Fixes
- Fixed TypeScript errors in `mcp-tools.test.ts`
- Fixed TypeScript errors in `search-filter.test.ts`
- Resolved Bug #018 - MCP tools disabled issue

### 📊 Performance Results
- **Target:** 50% improvement
- **Achieved:** 99.1% improvement ✅
- **Cache hit rate:** 77.8% after mixed operations
- **Index lookup:** 1.01ms average

### 📁 Files Changed
- `src/index.ts`: +350 lines (TaskCache + TaskIndexManager)
- `tests/validate-dependencies.test.ts`: +404 lines (new)
- `scripts/benchmark.mjs`: +98 lines (new)
- `scripts/benchmark-cache.mjs`: +214 lines (new)
- `scripts/benchmark-index.mjs`: +120 lines (new)

### 🔗 Commits
- `9993612` - feat: Add caching and indexing for 99.1% performance improvement
- `7f4349c` - test: Add comprehensive unit tests for validateDependencies

---

## v1.0.0 (November 20-22, 2025) - Initial Release

### ✨ Core Features
- **Task Management**
  - Create, read, update, delete tasks
  - Task lifecycle: backlog → active → completed
  - Priority levels: High, Medium, Low
  - Task types: feature, bugfix, refactor

- **Dependency Management**
  - Task dependencies with validation
  - Circular dependency detection
  - Dependency chain visualization
  - Incomplete dependency warnings

- **Search & Filtering**
  - Text search (title, description, ID)
  - Filter by priority, type, status
  - Date range filtering
  - Dependency-based filtering

- **Batch Operations**
  - Batch status updates
  - Batch priority changes
  - Batch dependency management
  - Dry-run mode

- **Git Integration**
  - Auto-commit with task context
  - Auto-push to remote
  - Git repository detection
  - Branch status tracking

- **Todo List System**
  - Auto-generated todo lists
  - Markdown format
  - Sync to file
  - Priority sorting

### 🔧 MCP Tools (20 total)
1. `create-task` - Create new task from template
2. `list-tasks` - List all tasks with filtering
3. `get-task` - Get detailed task content
4. `start-task` - Move task to active
5. `complete-task` - Mark task as completed
6. `update-task-status` - Change task status
7. `update-task-dependencies` - Manage dependencies
8. `validate-dependencies` - Check dependency validity
9. `list-task-dependencies` - View dependency tree
10. `mark-step` - Mark checklist item as complete
11. `add-note` - Add note to task
12. `get-next-task-id` - Get next available ID
13. `get-dashboard` - View README dashboard
14. `search-tasks` - Search by text
15. `filter-tasks` - Advanced filtering
16. `batch-update-tasks` - Batch operations
17. `sync-todo-list` - Generate todo list
18. `get-stats` - View statistics
19. `check-git-status` - Check git repository
20. `get-search-view-results` - Integration with VS Code search

### 🧪 Testing
- 48/53 tests passing
- Unit tests for search/filter (25 tests)
- Integration tests for MCP tools
- Task lifecycle tests

### 📁 Project Structure
```
.plans/
├── active/          # Tasks in progress
├── backlog/         # Planned tasks
├── completed/       # Archived tasks by month
│   └── 2025-11/
├── templates/       # Task templates
└── README.md        # Dashboard
```

### 🎯 Completed Tasks
- #005 - Task Dependencies & Validation System
- #006 - Testing Suite (Unit & Integration Tests)
- #007 - Advanced Search & Filtering System
- #019 - Batch Operations System
- #020 - Auto Sync Todo List

### 🔗 Repository
- GitHub: https://github.com/ptnghia/TaskFlow
- npm: taskflow-mcp (planned)
- MCP Registry: Pending submission

---

## v0.1.0 (November 15-19, 2025) - Prototype

### Initial Development
- Basic task CRUD operations
- File-based storage system
- Task templates (feature, bugfix, refactor)
- Markdown-based task format
- MCP server setup with @modelcontextprotocol/sdk

---

## Version Naming Convention

- **Major (x.0.0)**: Breaking changes, major feature additions
- **Minor (1.x.0)**: New features, backward compatible
- **Patch (1.1.x)**: Bug fixes, performance improvements

---

## Support

- Issues: https://github.com/ptnghia/TaskFlow/issues
- Discussions: https://github.com/ptnghia/TaskFlow/discussions
- Email: ptnghia.dev@gmail.com

---

**Last Updated:** November 23, 2025
