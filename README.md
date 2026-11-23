# Priorlight

![Priorlight](assets/icon.svg)

Priorlight is a remote MCP server for patent search reports and patent application drafts, with a free first look. Every output is a draft for review by a registered patent attorney or patent agent. Not legal advice.

- Site: [https://priorlight.ai](https://priorlight.ai)
- MCP endpoint: `https://priorlight.ai/mcp` (streamable HTTP, no key needed)
- Guide for assistants: [https://priorlight.ai/llms.txt](https://priorlight.ai/llms.txt)
- Support: [support@priorlight.ai](mailto:support@priorlight.ai)

## Quick start for agents

1. Call `start_here`. It explains what Priorlight does, which tool to call for each goal, current prices and how checkout works.
2. Call `preview_patentability` with a plain-text description for a free first look: how many verified related US patent records turned up, their main classes, and the 3 closest with official links. Up to 5 an hour. No opinion, nothing stored.
3. To order, call a paid tool with `terms_accepted: true`. It returns a checkout link and a `job_id`. After payment, poll `get_job`.

## Install

### Claude Code

```sh
claude mcp add --transport http priorlight https://priorlight.ai/mcp
```

### Claude, Cursor and other clients

```json
{
  "mcpServers": {
    "priorlight": {
      "type": "http",
      "url": "https://priorlight.ai/mcp"
    }
  }
}
```

Cursor: put this in `.cursor/mcp.json`.

### VS Code

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

## Tools

The server lists 20 tools in about 6,000 tokens. Full input schemas come from `tools/list`; the invention intake schema is the `priorlight://schemas/intake` resource or `get_intake_schema`.

| Tool | What it does | Cost |
| --- | --- | --- |
| `start_here` | What Priorlight does, which tool to call, prices and the paid flow. | Free |
| `preview_patentability` | Free first look from a plain-text description: count, classes and the 3 closest verified US patent records. | Free |
| `get_pricing` | Current prices and which tools each offer includes. | Free |
| `get_intake_schema` | JSON Schema for the invention `intake` object. | Free |
| `validate_intake` | Completeness score, missing fields and follow-up questions for an intake. | Free |
| `get_disclaimer` | Draft label, disclaimer and policy links. | Free |
| `get_job` | Status and result of a job. | Free |
| `plan_search` | Prior-art search strategy from an intake. | Search report |
| `run_prior_art_search` | Verified references with evidence, from a search plan. | Search report |
| `chart_reference` | Chart one verified reference against the invention's key elements. | Search report |
| `draft_patentability_opinion` | Draft patentability assessment from reference charts. | Search report |
| `draft_claims` | Draft claims from an intake. | Application draft |
| `draft_specification` | Draft specification from a claims job. | Application draft |
| `assemble_application` | Combine claims, specification and figures into one application draft. | Application draft |
| `run_bundle` | Search report, then application draft, in one call. | Bundle |
| `verify_citations` | Re-check stored references against official records. | Included |
| `generate_figures` | Draft figures with reference numerals. | Not on sale yet |
| `analyze_invention` | Key elements, alternatives and open gaps from an intake. | API key |
| `check_claims` | Lint supplied claim text. | API key |
| `quick_novelty_screen_lite` | Up to 5 verified related patents for a full intake. | API key |

## Pricing (USD)

- Patent search report: $99
- Patent application draft: $99
- Patent search report and application draft: $149
- Annual plan: $99 a month, billed $1,188 a year

`get_pricing` always returns the current prices.

## Disclaimer

Priorlight supplies automated drafts, not legal advice. No attorney-client relationship with Priorlight. Have a registered patent attorney or patent agent review before reliance or filing. Searches are not exhaustive. Priorlight does not use your inputs for model training; see the Terms and Privacy Policy.

- [Terms](https://priorlight.ai/terms)
- [Privacy](https://priorlight.ai/privacy)
- [Confidentiality and Non-Use Agreement](https://priorlight.ai/confidentiality)
- [Disclaimer](https://priorlight.ai/disclaimer)
- [Refunds](https://priorlight.ai/refunds)

## License

This repository contains listing and documentation files only. It does not include the Priorlight service source code. The hosted service, name and logo are all rights reserved. The install snippets in this README are available under the MIT License. See [LICENSE](LICENSE).
