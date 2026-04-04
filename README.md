# n8n Workflows — Noz

A collection of production n8n workflows used to run an automated X (Twitter) content strategy for a SaaS brand.

Built using **Claude Code + Synta MCP** — which gives Claude direct read/write access to your n8n instance, allowing it to build, debug, and self-heal workflows without you touching the canvas.

> These workflows were sanitized before publishing. All API keys, credentials, and personal identifiers have been replaced with placeholder values. You will need to configure your own credentials before importing.

---

## Workflows

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [X Posting Bot](workflows/x-posting-bot.json) | 57 | Fully automated X content posting bot with AI generation and self-critique loop |
| [Research Pipeline](workflows/research-pipeline.json) | 26 | Automated content research — scrapes, aggregates, and stores data for content workflows |
| [Learning Workflow](workflows/learning-workflow.json) | 13 | Analyses post performance and extracts patterns to improve future content |

---

### 1. [X Posting Bot](workflows/x-posting-bot.json)
**57 nodes | 8 scheduled daily triggers**

Runs throughout the day across 8 content slots. Pulls context from Airtable, generates tweets with an AI agent, runs each draft through a self-critique loop, and publishes via the Twitter API. Failed critiques retry automatically; if max retries hit, the slot is skipped with a Telegram alert.

→ [Read full docs](docs/x-posting-bot.md)

---

### 2. [Research Pipeline](workflows/research-pipeline.json)
**26 nodes | 4 scheduled triggers**

Runs daily and weekly, scrapes X via Apify for defined research terms, normalises the data, and stores structured output in Airtable for the posting bot and learning workflow to consume.

→ [Read full docs](docs/research-pipeline.md)

---

### 3. [Learning Workflow](workflows/learning-workflow.json)
**13 nodes | 1 scheduled trigger**

Pulls recent tweet performance data, runs it through a Claude AI agent to extract patterns and learnings, and writes structured insights back to Airtable. The posting bot reads these learnings when generating new content — closing the feedback loop.

→ [Read full docs](docs/learning-workflow.md)

---

## How these were built

These workflows were built using [Claude Code](https://claude.ai/code) with the [Synta MCP](https://synta.io).

The Synta MCP gives Claude Code direct access to your n8n instance — it can build workflows, import them, debug broken nodes, and self-heal. Unlike the standard n8n MCP (read-only docs access), Synta's MCP actually writes to your instance.

The self-healing loop was the key unlock: when a node fails, it catches the error, fixes the node, re-triggers the workflow, and verifies the fix before continuing.

---

## Importing a workflow

1. Download the JSON file
2. In n8n: **Workflows → Import from file**
3. Replace all `YOUR_*_HERE` placeholders with your actual credentials
4. Configure Airtable base IDs, Telegram chat IDs, or Google Drive folder IDs to match your setup
5. Test on a single execution before enabling schedules

---

## Credentials required

| Service | Used in |
|---------|---------|
| Twitter / X API | X Posting Bot |
| Airtable | All three workflows |
| OpenRouter | X Posting Bot, Learning Workflow |
| Anthropic (Claude) | Learning Workflow |
| Telegram Bot | X Posting Bot (notifications) |
| Google Drive | X Posting Bot (PDF uploads) |
| Apify | Research Pipeline |
| Typefully | X Posting Bot (draft scheduling) |

---

## Notes

- All workflows were running in production at the time of export
- Sanitization was applied to credentials and personal identifiers
- Node names reflect the original content slot strategy — rename to match your own
