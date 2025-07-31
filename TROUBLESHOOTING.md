# Troubleshooting Guide: GitHub Copilot Pro with Claude Sonnet 3.5 and MCP

## Issue: Request Failed Error

If you're experiencing "request failed" errors when using GitHub Copilot Pro with Claude Sonnet 3.5 in Agent mode, follow this troubleshooting guide.

### Prerequisites Check

1. **GitHub Copilot Pro Subscription**
   - Ensure you have an active GitHub Copilot Pro subscription
   - Check at: https://github.com/settings/copilot

2. **VS Code Extensions**
   - Install/Update GitHub Copilot extension
   - Install/Update GitHub Copilot Chat extension
   - Restart VS Code after installation

3. **Node.js Version**
   ```bash
   node --version  # Should be >= 18.0.0
   ```

### Step-by-Step Solution

#### Step 1: Verify MCP Server
```bash
# In the project directory
npm install
npm test
npm start
```

#### Step 2: Configure VS Code Settings
Open VS Code settings (Ctrl/Cmd + ,) and verify:

```json
{
  "github.copilot.enable": {
    "*": true
  },
  "github.copilot.chat.enable": true,
  "github.copilot.preferredAgent": "claude-sonnet-3.5",
  "github.copilot.chat.model": "claude-sonnet-3.5"
}
```

#### Step 3: Restart VS Code
1. Close VS Code completely
2. Reopen the workspace
3. Wait for extensions to initialize

#### Step 4: Test Integration
1. Open GitHub Copilot Chat (Ctrl/Cmd + Shift + I)
2. Type: "Can you help me run Parasoft tests?"
3. The MCP server should respond with available testing tools

### Common Fixes

#### Fix 1: Authentication Issues
```bash
# Sign out and sign back into GitHub
gh auth logout
gh auth login
```

#### Fix 2: Clear VS Code Cache
1. Close VS Code
2. Delete: `~/.vscode/extensions` (backup first)
3. Reinstall Copilot extensions

#### Fix 3: Network/Proxy Issues
- Check corporate firewall settings
- Verify proxy configuration in VS Code
- Try from a different network

#### Fix 4: Agent Availability
If Claude Sonnet 3.5 is not available:
1. Check GitHub Copilot Pro status
2. Try with default agent first
3. Update to latest VS Code version

### Advanced Debugging

#### Enable Debug Logging
```json
{
  "mcp.logging.level": "debug",
  "github.copilot.advanced": {
    "debug.overrideEngine": "claude-sonnet-3.5"
  }
}
```

#### Check MCP Connection
```bash
# View MCP logs
tail -f mcp.log

# Test MCP server directly
node mcp-server/index.js
```

### Error Messages and Solutions

| Error | Solution |
|-------|----------|
| "Agent not available" | Check Copilot Pro subscription |
| "Connection timeout" | Restart MCP server |
| "Authentication failed" | Re-authenticate with GitHub |
| "Model not found" | Verify Claude Sonnet 3.5 availability |

### Still Having Issues?

1. Check GitHub Status: https://www.githubstatus.com/
2. VS Code Issues: https://github.com/microsoft/vscode/issues
3. Copilot Support: https://support.github.com/

### Success Indicators

✅ MCP server starts without errors
✅ Copilot Chat responds to queries
✅ Claude Sonnet 3.5 is active
✅ Parasoft tools are accessible through chat