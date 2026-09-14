---
name: setup
description: Set up Revelara in this environment. Use when the user asks to set up, connect, or install Revelara, when a Revelara MCP tool fails with an authentication error, or before the first Revelara code scan.
---

# Set up Revelara

Revelara has two parts. Do step 1 for everyone. Do step 2 only if the user wants to scan code.

## 1. Connect the MCP server

This plugin already declares the `revelara` MCP server at `https://api.revelara.ai/mcp`. It uses OAuth, so no API key goes in a config file.

1. Tell the user to authenticate the server:
   - Claude Code: run `/mcp`, select `revelara`, and complete the browser sign-in.
   - Cursor: open Settings > MCP and sign in to `revelara`.
   - Gemini CLI: run `/mcp auth revelara`.
2. If the user has no Revelara account, send them to https://app.revelara.ai to create one.
3. Verify: call `search_controls` with the query `timeout`. A list of controls with `RC-` IDs means the connection works.

## 2. Install the scanner (optional)

The `rvl` CLI scans a codebase for reliability risks. The scan runs locally and customer code never leaves the machine.

1. Install:
   - macOS or Linux with Homebrew: `brew install --cask revelara-ai/tap/rvl`
   - Other platforms: download a release archive from https://github.com/revelara-ai/rvl-cli/releases and put its contents on `PATH`.
2. Run these in the repository root. `rvl login` asks for an API key, which the user creates in the Revelara app.
   ```sh
   rvl login
   rvl init
   rvl doctor
   ```
   `rvl init` installs the full Revelara skill set (scan, fix, ask, and the practice assessments) for the current agent.
3. Run `rvl scan` and show the user the result.

Do not print, echo, or store the API key in any file other than the one `rvl login` writes.
