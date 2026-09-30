# WRITER MCP

Plugin that connects agents to [WRITER](https://writer.com) through WRITER’s official hosted [Model Context Protocol](https://modelcontextprotocol.io/) server. One standard interface for governed WRITER tools, workflows, deliverables, and company context.

Run WRITER playbooks, check on runs, and pull deliverables into the current work from any MCP-compatible application.

Closed beta: Playbooks and deliverables.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **WRITER MCP**.
3. Click **Install**, then complete the WRITER sign-in prompt.

Or run `/add-plugin writer-mcp` in chat.

## MCP

```json
{
  "mcpServers": {
    "writer": {
      "type": "http",
      "url": "https://api.writer.com/v1/mcp"
    }
  }
}
```

## Setup

WRITER’s MCP server uses OAuth 2.1 with PKCE and dynamic client registration, so there is nothing to register and no client ID or secret to configure.

1. Install the plugin.
2. Complete the WRITER OAuth login in the browser when your client prompts.
3. Tool calls run with your own WRITER permissions: you see the playbooks and deliverables your WRITER seat can access.

Access requirements:

- A WRITER account with a seat in an organization enrolled in the Playbooks and deliverables closed beta.
- The server requests the `mcp:playbooks` and `mcp:deliverables` scopes. Clients that discover scopes from the OAuth metadata get these automatically.
- Access tokens last one hour and refresh automatically; you may be asked to sign in again after a day.
- Requests are rate limited per organization.

## Tools

| Tool | What it does |
| --- | --- |
| `list_playbooks` | List published playbooks you own or that are shared with you |
| `get_playbook` | Get one playbook and its declared inputs |
| `run_playbook` | Start a run; returns a `run_id` immediately |
| `upload_file` | Upload a file to use as a run input |
| `get_run` | Get the current status of a run |
| `list_runs` | List runs started through MCP, newest first |
| `get_run_output` | Get the final text and deliverables of a finished run |
| `resume_run` | Answer a run that is waiting for user input |
| `cancel_run` | Cancel a run |
| `list_deliverables` | List deliverables you own |
| `download_deliverable` | Download a deliverable produced by a run |
| `download_owned_deliverable` | Download a deliverable you own |

Runs are asynchronous: start one with `run_playbook`, poll `get_run` until it finishes, then read `get_run_output`.

## Network and data

This plugin ships no code. It only points your client at `https://api.writer.com/v1/mcp` and its OAuth authorization server at `https://app.writer.com`. No credentials are stored in the plugin.

## Docs

- WRITER developer docs: https://dev.writer.com
- Support: https://support.writer.com

## License

MIT
