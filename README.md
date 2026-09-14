# Revelara plugin

Reliability intelligence for coding agents. This plugin connects your agent to the hosted Revelara MCP server at `https://api.revelara.ai/mcp`.

The server gives the agent evidence for reliability decisions:

- **Incidents**: a curated corpus of public production incidents, with links to the original reports.
- **Risks**: your organization's risk register, with mapped controls and evidence.
- **Controls**: a reliability controls catalog, with STPA-inspired safety views.
- **Knowledge**: distilled facts, procedures, patterns, and graded practices.
- **Graph**: the links between incidents, technologies, services, and controls.
- **Service catalog**: tiers, owners, stacks, and dependencies.

All 22 tools only read data. All results are scoped to your organization.

## Install

### Claude Code

```sh
claude plugin marketplace add revelara-ai/revelara-plugin
claude plugin install revelara@revelara
```

Then run `/mcp`, select `revelara`, and sign in.

### Cursor

Install `revelara` from the Cursor Marketplace, or add the MCP server from `mcp.json` in this repository.

### Gemini CLI

```sh
gemini extensions install https://github.com/revelara-ai/revelara-plugin
```

### Any MCP client

Add a Streamable HTTP server with the URL `https://api.revelara.ai/mcp`. The server uses OAuth 2.1 with dynamic client registration. It is also listed in the MCP Registry as `ai.revelara/mcp`.

## Account

You need a Revelara account. Create one at https://app.revelara.ai.

## Code scanning

The plugin includes a `setup` skill. It connects the MCP server and, if you want, installs the [`rvl`](https://github.com/revelara-ai/rvl-cli) scanner. The scanner runs locally, and your code never leaves your machine.

## Links

- Documentation: https://app.revelara.ai/help/mcp
- Privacy policy: https://revelara.ai/privacy
- Terms: https://revelara.ai/terms
- Support: team@revelara.ai

## License

Apache-2.0. See [LICENSE](LICENSE).
