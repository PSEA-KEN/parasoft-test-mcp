# Parasoft Test MCP

Model Context Protocol (MCP) server for integrating Parasoft testing tools with GitHub Copilot Pro and Claude Sonnet 3.5.

## Setup Instructions

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure VS Code

Ensure you have the following VS Code extensions installed:
- GitHub Copilot
- GitHub Copilot Chat

### 3. Configure GitHub Copilot Pro

1. Open VS Code settings (Ctrl/Cmd + ,)
2. Search for "copilot"
3. Ensure the following settings are configured:
   - `github.copilot.enable`: true
   - `github.copilot.chat.enable`: true
   - `github.copilot.preferredAgent`: "claude-sonnet-3.5"

### 4. Start MCP Server

```bash
npm start
```

### 5. Verify Connection

The MCP server should be running and accessible to GitHub Copilot. You can verify this by:

1. Opening GitHub Copilot Chat
2. Asking about Parasoft testing capabilities
3. The server should respond with available testing tools

## Available Tools

### `run_parasoft_test`
Execute Parasoft test suites and return detailed results.

**Parameters:**
- `testSuite` (required): Name of the test suite to run
- `environment` (optional): Target environment (dev, test, prod)
- `parameters` (optional): Additional test parameters

### `generate_test_report`
Generate comprehensive test reports from Parasoft results.

**Parameters:**
- `format` (optional): Report format (html, pdf, json, xml)
- `includeMetrics` (optional): Include performance metrics (default: true)

### `analyze_test_coverage`
Analyze code coverage from Parasoft test results.

**Parameters:**
- `threshold` (optional): Coverage threshold percentage (default: 80)

## Configuration Files

- `.vscode/settings.json`: VS Code specific settings for Copilot and MCP
- `mcp-config.json`: MCP server configuration
- `package.json`: Node.js dependencies and scripts

## Troubleshooting

### Common Issues

1. **Request Failed Error**
   - Ensure MCP server is running (`npm start`)
   - Check VS Code settings for proper Copilot configuration
   - Verify network connectivity

2. **Claude Sonnet 3.5 Not Available**
   - Ensure you have GitHub Copilot Pro subscription
   - Update VS Code and Copilot extensions to latest versions
   - Check agent availability in Copilot settings

3. **MCP Server Connection Issues**
   - Check `mcp.log` for error messages
   - Verify Node.js version (requires >= 18.0.0)
   - Ensure all dependencies are installed

### Debug Mode

To run in debug mode:

```bash
npm run dev
```

This will start the server with Node.js inspector enabled.

## Support

For issues related to:
- Parasoft tools: Contact Parasoft support
- GitHub Copilot: Check GitHub Copilot documentation
- MCP: Refer to Model Context Protocol specification