# VS Code Configuration Examples

This directory contains example configuration files for TaskFlow MCP Server.

## Files

### mcp.json.example

Example MCP server configuration for VS Code. This file shows how to configure TaskFlow for different installation methods and operating systems.

## Quick Setup

1. Copy `mcp.json.example` to your project's `.vscode/mcp.json`
2. Uncomment and adjust the `args` path based on your installation
3. Save and reload VS Code (`Ctrl+Shift+P` → "Developer: Reload Window")

## Finding Node Modules Path

### Linux/macOS
```bash
npm root -g
# Example output: /usr/local/lib/node_modules
# Path: /usr/local/lib/node_modules/taskflow-mcp/dist/index.js
```

### Windows (PowerShell)
```powershell
npm root -g
# Example output: C:\Users\YourUsername\AppData\Roaming\npm\node_modules
# Path: C:\Users\YourUsername\AppData\Roaming\npm\node_modules\taskflow-mcp\dist\index.js
```

## Environment Variables

### WORKSPACE_ROOT (Required)
- Points to your project directory
- Use `${workspaceFolder}` variable for automatic detection

### TASKFLOW_ENABLE_ADVANCED_TOOLS (Optional)
- Set to `"true"` to enable all 54 tools
- Default: Only 40 core tools enabled
- See `TOOLS_ORGANIZATION.md` for complete tool list

## Troubleshooting

If MCP server doesn't work:

1. **Verify path is correct**: Make sure the path points to actual `index.js` file
2. **Use absolute paths on Windows**: Don't use `~` or relative paths
3. **Check permissions**: Ensure Node.js has execute permissions
4. **Reload VS Code**: After changes, always reload VS Code
5. **Check output**: `Ctrl+Shift+U` → "GitHub Copilot Chat - MCP" for errors

## Example Configurations

### Global Installation (Linux/macOS)
```json
{
  "servers": {
    "taskflow": {
      "command": "node",
      "args": ["/usr/local/lib/node_modules/taskflow-mcp/dist/index.js"],
      "env": {
        "WORKSPACE_ROOT": "${workspaceFolder}"
      }
    }
  }
}
```

### Global Installation (Windows)
```json
{
  "servers": {
    "taskflow": {
      "command": "node",
      "args": ["C:\\Users\\YourUsername\\AppData\\Roaming\\npm\\node_modules\\taskflow-mcp\\dist\\index.js"],
      "env": {
        "WORKSPACE_ROOT": "${workspaceFolder}"
      }
    }
  }
}
```

### Local Installation (Any OS)
```json
{
  "servers": {
    "taskflow": {
      "command": "node",
      "args": ["${workspaceFolder}/node_modules/taskflow-mcp/dist/index.js"],
      "env": {
        "WORKSPACE_ROOT": "${workspaceFolder}"
      }
    }
  }
}
```

### Development Mode (Any OS)
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

### With Advanced Tools Enabled
```json
{
  "servers": {
    "taskflow": {
      "command": "node",
      "args": ["/usr/local/lib/node_modules/taskflow-mcp/dist/index.js"],
      "env": {
        "WORKSPACE_ROOT": "${workspaceFolder}",
        "TASKFLOW_ENABLE_ADVANCED_TOOLS": "true"
      }
    }
  }
}
```
