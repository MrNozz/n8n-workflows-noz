# n8n Workflows — Noz

A growing collection of production n8n workflows, open sourced for the community.

Built using **Claude Code + Synta MCP** — which gives Claude direct read/write access to your n8n instance, allowing it to build, debug, and self-heal workflows without touching the canvas manually.

> All credentials, API keys, and personal identifiers have been sanitized. Replace `YOUR_*_HERE` placeholders with your own values before importing.

---

## Collections

| Collection | Workflows | Description |
|---|---|---|
| [X Content Strategy](x-content-strategy/) | 3 | Automated X posting bot, research pipeline, and learning loop |
| [LinkedIn Lead Generation](linkedin-lead-generation/) | 5 | Full LinkedIn prospecting pipeline — find, research, score, outreach |

---

## How these were built

All workflows were built and iterated using [Claude Code](https://claude.ai/code) with the [Synta MCP](https://synta.io).

The Synta MCP gives Claude actual read/write access to your n8n instance — not just docs lookups. It builds workflows directly, imports them, debugs broken nodes, and self-heals when something fails.

If you want to adapt these for your own use, that's the recommended approach:
- Connect Claude Code to your n8n instance via Synta MCP
- Describe what you want to change in plain English
- Claude will handle the wiring, test it, and fix anything that breaks

Takes about 5-10 minutes to get set up once you have your API tokens ready.

---

## Importing a workflow

1. Download the JSON from the relevant `workflows/` folder
2. In n8n: **Workflows → Import from file**
3. Replace all `YOUR_*_HERE` placeholders with your credentials
4. Read the `docs/` folder for setup notes per workflow
5. Test with a single manual execution before enabling schedules

---

## More workflows coming

This repo will be updated regularly with new workflow collections. Star it to stay updated.
