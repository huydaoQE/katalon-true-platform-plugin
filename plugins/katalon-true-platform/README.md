# Katalon True Platform Codex Plugin

This plugin bundles Katalon True Platform/TestOps workflows for Codex.

## Included Skills

- `katalon-platform-setup`: Set up, verify, and troubleshoot Katalon MCP connectivity.
- `katalon-create-test-cases`: Create, update, organize, and link manual test cases.
- `katalon-execute-test`: Create manual runs, Run with AI, schedule automated suites, and summarize results.
- `katalon-upload-report`: Run automation and upload Katalon, JUnit, or Playwright reports.
- `katalon-release-analyze`: Analyze release readiness from Katalon quality data.
- `katalon-trueplatform-testing`: End-to-end requirement-to-execution workflow.

## Bundled MCP Server

The plugin declares `katalon-prod-mcp` in `.mcp.json`:

```json
{
  "mcpServers": {
    "katalon-prod-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://<your.sub.domain>.katalon.io/mcp",
        "--transport",
        "http-first"
      ]
    }
  }
}
```

Codex loads this MCP configuration from the plugin manifest through:

```json
{
  "mcpServers": "./.mcp.json"
}
```

Replace `<your.sub.domain>` with the Katalon subdomain for the workspace you want to use. `npx -y mcp-remote ...` installs or resolves the `mcp-remote` package when the MCP server is started. Authentication is handled through the browser/OAuth flow; do not paste passwords, tokens, cookies, JWTs, or callback URLs into chat.

## Marketplace Entry

This plugin is distributed through the repository marketplace at:

```text
.agents/plugins/marketplace.json
```

It exposes this plugin from:

```text
./plugins/katalon-true-platform
```
