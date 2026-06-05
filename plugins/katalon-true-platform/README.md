# Katalon True Platform Plugin

This plugin bundles Katalon True Platform/TestOps workflows for Codex and Claude Code. The platform wrappers live in `.codex-plugin/plugin.json` and `.claude-plugin/plugin.json`; the skills and assets are shared.

## Included Skills

- `katalon-platform-setup`: Set up, verify, and troubleshoot Katalon MCP connectivity.
- `katalon-create-test-cases`: Create, update, organize, and link manual test cases.
- `katalon-execute-test`: Create manual runs, Run with AI, schedule automated suites, and summarize results.
- `katalon-upload-report`: Run automation and upload Katalon, JUnit, or Playwright reports.
- `katalon-test-case-to-playwright-script`: Convert Katalon Platform manual test cases into Playwright TypeScript automation with POM and fixtures.
- `katalon-playwright-execute`: Execute Playwright scripts or suites, upload reports to Katalon Platform, and return the result URL.
- `katalon-release-analyze`: Analyze release readiness from Katalon quality data.
- `katalon-trueplatform-testing`: End-to-end requirement-to-execution workflow.

## Bundled MCP Server

The Codex wrapper declares `katalon-prod-mcp` in `.mcp.json`:

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

Claude Code uses the same bundled skills. If Claude Code does not load `.mcp.json` from the plugin automatically in your environment, configure the same Katalon MCP server in Claude's MCP configuration before using the MCP-dependent workflows.

## Marketplace Entry

This plugin is distributed through the repository marketplaces at:

```text
.agents/plugins/marketplace.json
.claude-plugin/marketplace.json
```

It exposes this plugin from:

```text
./plugins/katalon-true-platform
```
