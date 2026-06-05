# Katalon True Platform Plugin Marketplace

<img src="plugins/katalon-true-platform/assets/katalon-logo.svg" width="72" alt="Katalon logo">

Codex and Claude Code plugin marketplace for Katalon True Platform/TestOps workflows.

This repository keeps one shared plugin implementation under `plugins/katalon-true-platform` and exposes it through thin platform-specific marketplace wrappers:

- `.agents/plugins/marketplace.json` for Codex.
- `.claude-plugin/marketplace.json` for Claude Code.

## Install In Codex

```bash
codex plugin marketplace add huydaoQE/katalon-true-platform-plugin
```

If the marketplace is already configured, update it with:

```bash
codex plugin marketplace upgrade katalon-true-platform
```

Then open **Plugins** in Codex and install **Katalon True Platform**.

## Install In Claude Code

```bash
claude plugin marketplace add https://github.com/huydaoQE/katalon-true-platform-plugin
claude plugin i katalon-true-platform@katalon-true-platform-marketplace
```

For local development, run Claude Code with the shared plugin directory:

```bash
claude --plugin-dir plugins/katalon-true-platform
```

## Why This Layout

Codex reads `.agents/plugins/marketplace.json` from the marketplace root. Claude Code reads `.claude-plugin/marketplace.json` from the marketplace root. Both marketplace entries point to the same shared plugin directory.

Codex uses this marketplace entry shape:

```json
{
  "source": {
    "source": "local",
    "path": "./plugins/katalon-true-platform"
  }
}
```

Claude Code uses this marketplace entry shape:

```json
{
  "source": "./plugins/katalon-true-platform"
}
```

That lets Codex inspect `plugins/katalon-true-platform/.codex-plugin/plugin.json` and Claude Code inspect `plugins/katalon-true-platform/.claude-plugin/plugin.json`, while both platforms use the same `skills/` and `assets/` folders.

## Repository Layout

```text
.agents/plugins/marketplace.json
.claude-plugin/marketplace.json
plugins/katalon-true-platform/
  .claude-plugin/plugin.json
  .codex-plugin/plugin.json
  .mcp.json
  assets/katalon-logo.svg
  skills/
```

## Included Workflows

- Set up and verify Katalon MCP connectivity.
- Create, update, organize, and link manual test cases.
- Execute manual runs, Run with AI, and automated suites.
- Upload Katalon, JUnit, and Playwright reports.
- Analyze release readiness from Katalon quality data.
- Run end-to-end requirement-to-execution testing workflows.

## Bundled MCP

The Codex plugin declares `katalon-prod-mcp`, backed by `mcp-remote`:

```text
npx -y mcp-remote https://<your.sub.domain>.katalon.io/mcp --transport http-first
```

Replace `<your.sub.domain>` with the Katalon subdomain for the workspace you want to use. Authentication is handled through the browser/OAuth flow. Do not paste passwords, tokens, cookies, JWTs, or callback URLs into chat.

Claude Code uses the same skills and setup instructions. If Claude Code does not load the bundled `.mcp.json` automatically in your environment, configure the Katalon MCP server through Claude's MCP configuration and then use the bundled skills.

## Plugin Metadata

- Name: `katalon-true-platform`
- Version: `0.1.0`
- Publisher: `huydaoQE`
- Category: `Productivity`
- Capabilities: `Read`, `Write`, `Interactive`
