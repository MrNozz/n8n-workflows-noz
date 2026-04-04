# n8n Workflows — Noz

A collection of production n8n workflows used to run an automated X (Twitter) content strategy for a SaaS brand.

Built using **Claude Code + Synta MCP** — which gives Claude direct read/write access to your n8n instance, allowing it to build, debug, and self-heal workflows without you touching the canvas.

> These workflows were sanitized before publishing. All API keys, credentials, and personal identifiers have been replaced with `YOUR_CREDENTIAL_HERE` or `YOUR_KEY_HERE` style placeholders. You will need to configure your own credentials before importing.

---

## Workflows

### 1. [JB - Posting Bot](workflows/jb-posting-bot.json)
**57 nodes | 8 scheduled daily triggers**

Fully automated X posting bot. Runs throughout the day across 8 defined content slots (Wildcard, Exploit, Experiment, CTA), pulling context from Airtable, generating tweets with an AI agent, running a self-critique loop, and publishing via Twitter API.

→ [Read full docs](docs/jb-posting-bot.md)

---

### 2. [Research Pipeline](workflows/research-pipeline.json)
**26 nodes | 4 scheduled triggers**

Content research pipeline. Runs on a mix of daily and weekly schedules, scrapes and aggregates research via Apify, stores structured output in Airtable for downstream content agents to consume.

→ [Read full docs](docs/research-pipeline.md)

---

### 3. [JB - Learning Workflow](workflows/jb-learning-workflow.json)
**13 nodes | 1 scheduled trigger**

Post-performance analysis workflow. Pulls recent tweet performance data, runs it through an AI agent to extract patterns and learnings, and logs structured insights back to Airtable for the posting bot to reference.

→ [Read full docs](docs/jb-learning-workflow.md)

---

## How these were built

These workflows were built using [Claude Code](https://claude.ai/code) with the [Synta MCP](https://synta.io).

The Synta MCP gives Claude Code direct access to your n8n instance — it can build workflows, import them, debug broken nodes, and self-heal. Unlike the standard n8n MCP (which is read-only docs access), Synta's MCP actually writes to your instance.

The self-healing loop was the key unlock: when a node fails, it catches the error, fixes the node, re-triggers the workflow, and verifies the fix before continuing.

---

## Importing a workflow

1. Download the JSON file
2. In n8n: **Workflows → Import from file**
3. Replace all `YOUR_*_HERE` placeholders with your actual credentials
4. Configure any Airtable base IDs, Telegram chat IDs, or Google Drive folder IDs to match your setup
5. Test on a single execution before enabling schedules

---

## Credentials required

| Service | Used in |
|---|---|
| Twitter / X API | Posting Bot |
| Airtable | All three workflows |
| OpenRouter | Posting Bot, Learning Workflow |
| Anthropic (Claude) | Learning Workflow |
| Telegram Bot | Posting Bot (notifications) |
| Google Drive | Posting Bot (PDF uploads) |
| Apify | Research Pipeline |
| Typefully | Posting Bot (draft creation) |

---

## Notes

- All workflows were running in production at the time of export
- Sanitization was applied automatically — if you spot anything sensitive that was missed, open an issue
- Node names reflect actual slot strategy (Wildcard, Exploit, Experiment) — rename to match your own content strategy
