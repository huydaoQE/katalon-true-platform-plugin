# Katalon True Platform Plugin Marketplace

<img src="plugins/katalon-true-platform/assets/katalon-logo.svg" width="72" alt="Katalon logo">

Codex plugin marketplace for Katalon True Platform/TestOps workflows.

This repository is structured as a marketplace source so Codex can render plugin metadata, logo, description, and install policy before installation.

## Install

```bash
codex plugin marketplace add huydaoQE/katalon-true-platform-plugin
```

If the marketplace is already configured, update it with:

```bash
codex plugin marketplace upgrade katalon-true-platform
```

Then open **Plugins** in Codex and install **Katalon True Platform**.

## Why This Layout

Codex reads `.agents/plugins/marketplace.json` from the marketplace root. The marketplace entry points to the plugin with a local path:

```json
{
  "source": {
    "source": "local",
    "path": "./plugins/katalon-true-platform"
  }
}
```

That lets Codex inspect `plugins/katalon-true-platform/.codex-plugin/plugin.json` directly and display the full plugin name, logo, description, capabilities, and prompts in the Plugin Directory.

## Repository Layout

```text
.agents/plugins/marketplace.json
plugins/katalon-true-platform/
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

The plugin declares `katalon-prod-mcp`, backed by `mcp-remote`:

```text
npx -y mcp-remote https://<your.sub.domain>.katalon.io/mcp --transport http-first
```

Replace `<your.sub.domain>` with the Katalon subdomain for the workspace you want to use. Authentication is handled through the browser/OAuth flow. Do not paste passwords, tokens, cookies, JWTs, or callback URLs into chat.

## Plugin Metadata

- Name: `katalon-true-platform`
- Version: `0.1.0`
- Publisher: `huydaoQE`
- Category: `Productivity`
- Capabilities: `Read`, `Write`, `Interactive`
