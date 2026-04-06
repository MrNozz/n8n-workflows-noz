# LinkedIn Lead Generation

A suite of 5 interconnected n8n workflows for automated LinkedIn prospecting — from finding leads to researching companies to scoring and outreach. Built with Claude Code + Synta MCP.

## Workflows

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [LinkedIn Lead Generation Main](workflows/linkedin-lead-generation-main.json) | 96 | Master orchestration workflow — coordinates the full lead generation pipeline |
| [Lead Finder](workflows/lead-finder.json) | 97 | Discovers and pulls potential leads matching your ICP |
| [Company Research](workflows/company-research.json) | 22 | Enriches leads with company-level intelligence |
| [Lead Scorer](workflows/lead-scorer.json) | 25 | AI-powered scoring of leads based on fit criteria |
| [Outreach Agent](workflows/outreach-agent.json) | 38 | Personalised outreach generation and sequencing |

## How it works

1. **Lead Finder** discovers prospects based on your criteria
2. **Company Research** enriches each lead with company context
3. **Lead Scorer** runs AI scoring to prioritise the best leads
4. **Outreach Agent** generates personalised messages for top-scored leads
5. **Main workflow** orchestrates the full pipeline end-to-end

## How to import
1. Import all JSONs from `workflows/` into your n8n instance
2. Start with the sub-workflows (Lead Finder, Company Research, Lead Scorer, Outreach Agent)
3. Import the Main workflow last — it references the sub-workflows
4. Replace all `YOUR_*_HERE` placeholders with your credentials
5. See `docs/` for full setup instructions per workflow

## Services required
LinkedIn API / Apify (LinkedIn scraper), AI provider (OpenRouter/Anthropic), Airtable (data storage), email provider for outreach

## Notes
- All credentials and personal identifiers were removed before publishing
- Built and iterated using Claude Code + Synta MCP — see root README for context
