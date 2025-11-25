# TaskFlow Setup Guide

## Installation Methods

### Recommended: Install from npm

```bash
# Uninstall old version if exists
npm uninstall -g taskflow-mcp

# Install latest version
npm install -g @ptnghia/taskflow-mcp

# Verify version
npm list -g @ptnghia/taskflow-mcp
# Should show: @ptnghia/taskflow-mcp@1.10.0
```

### Alternative: Install from GitHub

```bash
npm install -g https://github.com/ptnghia/TaskFlow.git
```

### Old Package (Not Recommended)

```bash
npm install -g taskflow-mcp
# This installs outdated v1.0.32 with only 18 tools
```

## Installation Issues

### Issue: "taskflow command not found" after `npm install -g taskflow-mcp`

**Symptoms:**
```
taskflow : The term 'taskflow' is not recognized as the name of a cmdlet, function, script file, or operable program.
```

**Root Cause:**
npm global bin directory is not in system PATH.

**Solutions:**

#### Solution 1: Restart Terminal (Easiest)
Close and reopen your terminal/PowerShell, then try again:
```bash
taskflow init
```

#### Solution 2: Check npm Global Bin Path
```bash
# Find where npm installs global packages
npm bin -g

# Windows typical output:
# C:\Users\YourUsername\AppData\Roaming\npm

# Linux/macOS typical output:
# /usr/local/bin
```

#### Solution 3: Add to PATH (Windows)

**Method A - Using PowerShell (Temporary):**
```powershell
# Add to PATH for current session only
$env:Path += ";C:\Users\YourUsername\AppData\Roaming\npm"

# Now try:
taskflow init
```

**Method B - Using System Settings (Permanent):**
1. Press `Win + X` → System
2. Click "Advanced system settings"
3. Click "Environment Variables"
4. Under "User variables", select "Path" → Edit
5. Click "New" and add: `C:\Users\YourUsername\AppData\Roaming\npm`
6. Click OK on all dialogs
7. **Restart terminal** and try: `taskflow init`

#### Solution 4: Add to PATH (Linux/macOS)

Add to `~/.bashrc` or `~/.zshrc`:
```bash
export PATH="$PATH:/usr/local/bin"
```

Then reload:
```bash
source ~/.bashrc  # or source ~/.zshrc
taskflow init
```

#### Solution 5: Use npx (No PATH needed)

```bash
# Use npx to run without installing globally
npx taskflow-mcp init
```

This works immediately without PATH configuration.

#### Solution 6: Manual Setup

If all else fails, set up manually:

```bash
# 1. Create directory structure
mkdir -p .plans/{active,backlog,completed,decisions,lessons}
mkdir -p .github

# 2. Download example files from GitHub
# Visit: https://github.com/ptnghia/TaskFlow
# Download:
# - taskflow.config.json.example → rename to taskflow.config.json
# - templates/copilot/en/generic.md → .github/copilot-instructions.md

# 3. Configure .vscode/mcp.json
# Follow guide in .vscode-example/mcp.json.example
```

## Verification

After setup, verify TaskFlow is working:

### 1. Check Command Available
```bash
taskflow --version
# Should show: TaskFlow MCP v1.10.0 (or current version)
```

### 2. Check Files Created
```bash
ls .plans/
# Should show: active/ backlog/ completed/ decisions/ lessons/

ls .github/
# Should show: copilot-instructions.md

ls taskflow.config.json
# Should exist
```

### 3. Test MCP in VS Code

1. Open VS Code
2. Reload: `Ctrl+Shift+P` → "Developer: Reload Window"
3. Open GitHub Copilot Chat
4. Try: `💬 "List all tasks"`

If TaskFlow responds, setup is complete! 🎉

## Still Having Issues?

### Wrong Version or Old Tools?

If you see tools like `hello`, `initProject`, `listTasks` instead of `create-task`, `list-tasks`:

**You installed the old package (`taskflow-mcp@1.0.32`)!**

**Solution - Install new package:**

```bash
# 1. Uninstall old version
npm uninstall -g taskflow-mcp

# 2. Clear npm cache
npm cache clean --force

# 3. Install latest version
npm install -g @ptnghia/taskflow-mcp

# 4. Verify version
npm list -g @ptnghia/taskflow-mcp
# Should show: @ptnghia/taskflow-mcp@1.10.0

# 5. Update .vscode/mcp.json path (if needed)
# Find new path:
npm root -g
# Then: /@ptnghia/taskflow-mcp/dist/index.js

# 6. Reload VS Code
# Ctrl+Shift+P → "Developer: Reload Window"
```

**Expected tools in v1.10.0:**
- ✅ `create-task`, `list-tasks`, `get-task`, `search-tasks` (NOT `initProject`, `showTask`)
- ✅ 40 core tools by default (or 54 with advanced enabled)
- ✅ No warnings about "Tool does not have a description"

### Check npm Installation

1. **Check npm installation:**
   ```bash
   npm list -g taskflow-mcp
   # Should show installed version
   ```

2. **Reinstall if needed:**
   ```bash
   npm uninstall -g taskflow-mcp
   npm cache clean --force
   npm install -g taskflow-mcp
   ```

3. **Check Node.js version:**
   ```bash
   node --version
   # Should be 18.0.0 or higher
   ```

### MCP Configuration Issue

If you see old tools in VS Code MCP:

1. **Check `.vscode/mcp.json` path points to correct version:**
   ```json
   {
     "servers": {
       "taskflow": {
         "command": "node",
         "args": [
           // Make sure this points to NEW installation
           "/usr/local/lib/node_modules/taskflow-mcp/dist/index.js"
         ]
       }
     }
   }
   ```

2. **Find the correct path:**
   ```bash
   # Find where new version is installed
   npm root -g
   # Then append: /taskflow-mcp/dist/index.js
   
   # Example:
   # Linux/macOS: /usr/local/lib/node_modules/taskflow-mcp/dist/index.js
   # Windows: C:\Users\YourUsername\AppData\Roaming\npm\node_modules\taskflow-mcp\dist\index.js
   ```

3. **Update `.vscode/mcp.json` with correct path**

4. **Reload VS Code:**
   - `Ctrl+Shift+P` → "Developer: Reload Window"

5. **Verify in Copilot Chat:**
   ```
   💬 "What tools are available?"
   ```
   
   Should see: create-task, list-tasks, etc. (NOT initProject, showTask)

### Open GitHub Issue

4. **Open GitHub Issue:**
   If none of the above works, please open an issue at:
   https://github.com/ptnghia/TaskFlow/issues
   
   Include:
   - Operating system (Windows/Linux/macOS)
   - Node.js version (`node --version`)
   - npm version (`npm --version`)
   - Output of `npm bin -g`
   - Full error message
