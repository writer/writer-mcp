# Writer MCP

Cursor plugin for Writer’s hosted MCP server. One standard interface for governed Writer tools, workflows, deliverables, and company context.

Connects to `https://api.writer.com/v1/mcp` with OAuth. Closed beta: Playbooks and deliverables.

## What it includes

- Hosted Writer MCP at `https://api.writer.com/v1/mcp` (OAuth, permissions follow your Writer seat)
- Playbooks: list, get, and run playbooks you can access in Writer
- Runs: check status, list runs, resume or cancel
- Deliverables: list outputs, get run output, and download deliverables

## When to use it

Use when someone wants to run a Writer playbook from Cursor, check a run, or pull a deliverable into the current work — without rebuilding a one-off integration.
