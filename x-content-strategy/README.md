# X Content Strategy

A suite of 3 interconnected n8n workflows for fully automated X (Twitter) content — built with Claude Code + Synta MCP.

## Workflows

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [X Posting Bot](workflows/x-posting-bot.json) | 57 | Automated X posting across 8 daily content slots with AI generation + self-critique loop |
| [Research Pipeline](workflows/research-pipeline.json) | 26 | Scrapes and aggregates research via Apify, stores to Airtable for content workflows |
| [Learning Workflow](workflows/learning-workflow.json) | 13 | Analyses post performance, extracts patterns, feeds learnings back to the posting bot |

## How to import
1. Download the JSON from `workflows/`
2. In n8n: **Workflows → Import from file**
3. Replace all `YOUR_*_HERE` placeholders with your credentials
4. See `docs/` for full setup instructions per workflow

## Services required
Twitter/X API, Airtable, OpenRouter, Anthropic, Telegram, Google Drive, Apify, Typefully
