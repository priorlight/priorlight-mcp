# Priorlight

![Priorlight](assets/icon.svg)

Priorlight is a remote MCP server for prior-art search and patent application drafts. The outputs are drafts, not legal advice.

- Site: [https://priorlight.ai](https://priorlight.ai)
- MCP endpoint: [https://priorlight.ai/mcp](https://priorlight.ai/mcp)
- Support: [support@priorlight.ai](mailto:support@priorlight.ai)

Connect over streamable HTTP. Enter your invention, run a prior-art search, and request a draft application. Read-only tools such as `get_pricing`, `get_intake_schema`, `get_disclaimer`, and `validate_intake` work without a key. Paid tools return a checkout link and a job id. Nothing paid runs until the order is paid. Poll `get_job` for the result.

## Install

The server URL is `https://priorlight.ai/mcp`. No API key is required to start.

### Claude

Add this to your Claude MCP config, or run `claude mcp add --transport http priorlight https://priorlight.ai/mcp`:

```json
{
  "mcpServers": {
    "priorlight": {
      "url": "https://priorlight.ai/mcp"
    }
  }
}
```

### Cursor

Add the same config to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "priorlight": {
      "url": "https://priorlight.ai/mcp"
    }
  }
}
```

### VS Code

Add this to `.vscode/mcp.json`, or use **MCP: Add Server** and choose HTTP:

```json
{
  "servers": {
    "priorlight": {
      "type": "http",
      "url": "https://priorlight.ai/mcp"
    }
  }
}
```

### Generic streamable HTTP

Point any MCP client that supports remote streamable HTTP at:

```
https://priorlight.ai/mcp
```

Use the streamable HTTP transport. Do not use a local command or stdio installer. This repository has no server source to run locally.

## Tools

The live server at `https://priorlight.ai/mcp` lists 18 tools (verified with `tools/list`). Every tool returns a draft, not legal advice. Have a registered patent attorney or patent agent review the result before reliance or filing.

| Tool | What it does |
| --- | --- |
| `analyze_invention` | Collect and organize the invention elements before a search or draft. |
| `assemble_application` | Assemble a draft application from confirmed facts and completed steps. |
| `chart_reference` | Chart a reference against the invention. |
| `check_claims` | Lint supplied claims. |
| `draft_claims` | Draft claims from confirmed facts. |
| `draft_patentability_opinion` | Draft a patentability assessment from confirmed facts and search results. |
| `draft_specification` | Draft the specification from confirmed facts. |
| `generate_figures` | Generate figures. The figures offer is not for sale yet. |
| `get_disclaimer` | Return the current draft / not-legal-advice label and links to Terms, Privacy, Disclaimer, and Refunds. |
| `get_intake_schema` | Return the shared Enter Your Invention schema used by `validate_intake`. |
| `get_job` | Poll a known job for status and results. |
| `get_pricing` | List public prices and which paid tools each offer includes. |
| `plan_search` | Plan a prior-art search from confirmed facts. |
| `quick_novelty_screen_lite` | A limited initial look, without a full analysis. |
| `run_bundle` | Run the search-then-draft bundle workflow. The bundle is not for sale yet. |
| `run_prior_art_search` | Run a prior-art search from confirmed facts. |
| `validate_intake` | Validate and score the details you enter for your invention. |
| `verify_citations` | Verify citations. |

## Pricing

These three offers are for sale now (one-time prices, from the live `get_pricing` tool):

- Search report: $49
- Search + assessment: $149
- Application draft: $49.99

Coming soon:

- Application draft with figures
- Search-then-draft bundle

## Disclaimer

Priorlight/CVP supplies AI drafts, not legal advice. No attorney-client relationship with CVP or Priorlight. Have a registered patent attorney or patent agent review before reliance or filing. Searches are not exhaustive. CVP does not use your inputs to train AI models; see the Terms and Privacy notice. Any purchased attorney review is provided only by Whiteford | Schell IP under its separate engagement letter.

- [Terms](https://priorlight.ai/terms)
- [Privacy](https://priorlight.ai/privacy)
- [Disclaimer](https://priorlight.ai/disclaimer)
- [Refunds](https://priorlight.ai/refunds)

## License

This repository contains listing and documentation files only. It does not include the Priorlight service source code. The hosted service, name, and logo are all rights reserved. The install snippets in this README are available under the MIT License. See [LICENSE](LICENSE).
