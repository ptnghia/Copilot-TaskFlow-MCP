# TaskFlow Tools Organization

## Overview

TaskFlow MCP có **54 tools** được tổ chức thành 2 nhóm:
- **40 Core Tools** (luôn bật): Các tools thiết yếu cho workflow hàng ngày
- **14 Advanced Tools** (tắt mặc định): Các tools nâng cao, ít dùng hơn

## Core Tools (40 tools - Always Enabled)

### Task Management (4 tools)
- `create-task` - Tạo task mới
- `list-tasks` - Liệt kê tasks theo status
- `get-task` - Xem chi tiết task
- `search-tasks` - Tìm kiếm tasks

### Workflow (5 tools)
- `start-tasks` - Bắt đầu task
- `complete-tasks` - Hoàn thành task
- `update-tasks-status` - Cập nhật trạng thái
- `add-note` - Thêm ghi chú
- `mark-step` - Đánh dấu checklist step

### Dependencies (3 tools)
- `update-task-dependencies` - Cập nhật dependencies
- `validate-dependencies` - Kiểm tra circular dependencies
- `list-task-dependencies` - Xem danh sách dependencies

### Dashboard & Stats (4 tools)
- `get-dashboard` - Xem dashboard overview
- `get-stats` - Thống kê tasks
- `get-next-tasks-id` - Lấy ID task tiếp theo
- `filter-tasks` - Lọc tasks theo criteria

### Task Context (2 tools)
- `analyze-codebase` - Phân tích codebase structure
- `get-task-context` - Lấy context đầy đủ của task

### Project Vision (2 tools)
- `get-project-vision` - Xem project vision
- `validate-task-alignment` - Kiểm tra task có align với vision

### Lessons Learned (3 tools)
- `record-lesson-learned` - Ghi lại bài học từ lỗi
- `search-lessons` - Tìm kiếm lessons
- `get-lesson-insights` - Phân tích trends & patterns

### Architecture Decisions (3 tools)
- `record-decision` - Ghi lại quyết định kiến trúc
- `search-decisions` - Tìm kiếm ADRs
- `list-decisions` - Liệt kê tất cả ADRs

### Relationships (3 tools)
- `link-tasks` - Tạo mối quan hệ giữa tasks
- `unlink-tasks` - Xóa mối quan hệ
- `get-task-relationships` - Xem relationships của task

### Templates (2 tools)
- `get-template-content` - Xem nội dung template
- `list-templates` - Liệt kê templates available

### AI Recommendations (3 tools) - v1.7.0
- `recommend-next-task` - AI đề xuất task tiếp theo
- `suggest-task-breakdown` - Tự động chia task thành subtasks
- `get-lesson-insights` - Phân tích lessons với AI

### Code Intelligence (3 tools) - v1.8.0
- `get-code-snippets` - Trích xuất code patterns
- `suggest-refactoring` - Phân tích code và đề xuất refactoring
- `generate-test-cases` - Tự động tạo test cases

### Predictive Analytics (3 tools) - v1.9.0
- `predict-bottlenecks` - Dự đoán bottlenecks trong dự án
- `estimate-completion-time` - Ước tính thời gian hoàn thành
- `build-knowledge-graph` - Xây dựng knowledge graph

## Advanced Tools (14 tools - Optional)

Các tools này **TẮT mặc định** để giảm độ phức tạp. Bật khi cần thiết.

### Batch Operations (1 tool)
- `batch-update-tasks` - Cập nhật nhiều tasks cùng lúc

### System Maintenance (2 tools)
- `rebuild-index` - Rebuild task index
- `check-git-status` - Kiểm tra git repository

### Advanced Vision (1 tool)
- `create-project-vision` - Tạo project vision mới
- `sync-todo-list` - Đồng bộ todo list

### Documentation (1 tool)
- `generate-documentation` - Tạo changelog/API/architecture docs

### Detailed Views (2 tools)
- `get-decision` - Xem chi tiết đầy đủ của ADR
- `get-lesson` - Xem chi tiết đầy đủ của lesson

### Advanced Relationships (1 tool)
- `find-related-tasks` - Tìm tasks liên quan theo depth

### Template Management (3 tools)
- `create-template` - Tạo custom template
- `update-template` - Cập nhật template
- `delete-template` - Xóa template

### Tool Aliases (2 tools)
- `validate-step` - Alias của mark-step
- `taskflow-mark` - Alias của mark-step

## Cách Bật Advanced Tools

### Trong VS Code

Chỉnh sửa file `.vscode/mcp.json`:

```json
{
  "servers": {
    "taskflow": {
      "command": "node",
      "args": ["path/to/dist/index.js"],
      "env": {
        "WORKSPACE_ROOT": "/path/to/workspace",
        "TASKFLOW_ENABLE_ADVANCED_TOOLS": "true"  // Thêm dòng này
      }
    }
  }
}
```

### Trong GitHub Copilot Settings

1. Mở GitHub Copilot Settings
2. Tìm phần MCP Servers
3. Click vào TaskFlow server
4. Thêm environment variable:
   - Key: `TASKFLOW_ENABLE_ADVANCED_TOOLS`
   - Value: `true`
5. Restart VS Code

## Lợi Ích

### Mặc Định (40 Core Tools)
✅ Đơn giản, dễ sử dụng  
✅ Bao gồm tất cả tính năng thiết yếu  
✅ Performance tốt hơn (ít tools hơn)  
✅ Ít overwhelming cho người mới  

### Khi Bật Advanced (54 Tools)
✅ Truy cập đầy đủ tất cả tính năng  
✅ Batch operations cho power users  
✅ Template customization  
✅ Chi tiết đầy đủ cho lessons/decisions  

## Kiến Trúc

```
src/tools/
├── index.ts              # Export coreTools, advancedTools, allTools
├── optional-tools.ts     # Definition của advanced tools
├── task-management.ts    # 4 core tools
├── workflow.ts           # 8 tools (5 core + 3 advanced)
├── dashboard.ts          # 7 tools (4 core + 3 advanced)
├── lessons-tools.ts      # 5 tools (3 core + 2 advanced)
├── adr.ts               # 4 tools (3 core + 1 advanced)
├── relationships.ts      # 4 tools (3 core + 1 advanced)
├── templates.ts          # 4 tools (2 core + 2 advanced)
├── vision.ts            # 4 tools (2 core + 2 advanced)
├── context.ts           # 3 core tools
├── ai-recommendations.ts # 3 core tools (v1.7.0)
├── code-intelligence.ts  # 3 core tools (v1.8.0)
└── predictive-analytics.ts # 3 core tools (v1.9.0)
```

## Version History

- **v1.9.0** - Tool organization: 40 core + 14 advanced
- **v1.8.0** - Code Intelligence (3 tools)
- **v1.7.0** - AI Recommendations (3 tools)
- **v1.6.0** - Base 45 tools

---

**Default Mode:** 40 Core Tools  
**Advanced Mode:** 54 Total Tools  
**Easy to Enable:** One environment variable
