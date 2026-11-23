# CloudHostAI MCP client examples

Managed deployments on your own Hetzner servers: paste a Git repo and deploy in one click. Compute is billed directly by Hetzner.

This repository holds small, working examples for the hosted **CloudHostAI** MCP server. It is maintained by Elite AI Empire. The server itself is hosted; nothing here runs it.

- Product: https://cloud.eliteaiempire.com/hosting/
- MCP endpoint (streamable HTTP): `https://cloudhostai.eliteaiempire.com/mcp`
- OpenAPI: https://cloud.eliteaiempire.com/hosting/openapi.json
- Pricing, machine readable: https://cloud.eliteaiempire.com/hosting/pricing.json
- Discovery file: https://cloud.eliteaiempire.com/hosting/.well-known/mcp.json

## Tools

| Tool | What it does |
|---|---|
| `cloudhosting_list_projects` | List your projects. [scope: read] |
| `cloudhosting_get_project` | Get one project. [scope: read] |
| `cloudhosting_get_project_status` | Refresh and return the server status from Hetzner. [scope: read] |
| `cloudhosting_list_deploys` | Deploy history for a project (last 20). [scope: read] |
| `cloudhosting_get_logs` | Fetch container logs over SSH from the project server. [scope: read] |
| `cloudhosting_get_hetzner_status` | Whether your Hetzner token is connected (never returns it). [scope: read] |
| `cloudhosting_get_usage` | API/MCP calls this month against the free quota. [scope: read] |
| `cloudhosting_export` | Export all your objects (json, or csv of projects). [scope: read] |
| `cloudhosting_get_account` | Plan, project limit and usage of the account. [scope: billing] |
| `cloudhosting_create_project` | Register a project (repo + server size). Creates no server. [scope: write] |
| `cloudhosting_deploy_project` | Deploy (creates or redeploys the server in YOUR Hetzner account; Hetzner bills you). Requires confirm=true. [scope: write] |
| `cloudhosting_destroy_server` | DESTRUCTIVE: delete the project server from your Hetzner account. Requires confirm=true. [scope: write] |
| `cloudhosting_delete_project` | DESTRUCTIVE: delete a project record (server must be destroyed first). Requires confirm=true. [scope: write] |
| `cloudhosting_preview_deploy` | Dry run: check a public repo + branch and show what a deploy would create. Public, no key, creates nothing. |
| `cloudhosting_get_pricing` | Public plan prices and the agent API quota. |
| `get_company_info` | Who runs CloudHostAI, what it does, contact and legal links. Public, no key. |
| `list_pricing` | Current plans and prices in USD: plan, interval, amount_usd, currency, what_you_get. No account needed. |
| `get_checkout_link` | Checkout URL for a plan. With no arguments: the main paid plan. Where the site supports it the URL is a Stripe-hosted Checkout session (created unpaid; a human  |
| `search_site` | Keyword search over the public pages of cloudhostai.eliteaiempire.com. Public, no key. |

## Try it

```bash
bash examples/initialize.sh
python3 examples/client.py
```

`examples/client.py` uses only the Python standard library. It sends `initialize` and `tools/list` and prints the result. No key is needed for the public read tools. Tools that need an account say so in their description.

## Registry

Listed in the official MCP registry. Server manifest: `server.json`.

## Licence

MIT. See `LICENSE`.
