# JB - Learning Workflow

**13 nodes | 1 scheduled trigger**

## What it does
Performance analysis and learning extraction workflow. Pulls recent tweet performance data, runs it through an AI agent to identify patterns and learnings, and stores structured insights back to Airtable. The Posting Bot reads these learnings to inform future tweet generation.

## Trigger
Single daily schedule trigger.

## Data flow

1. **Schedule trigger fires**
2. **Airtable fetch** — pulls recent posted tweets with performance metrics
3. **Data merge** — consolidates tweet data
4. **Code node** — prepares and formats data for AI analysis
5. **AI Agent (Claude)** — analyses performance, extracts patterns, identifies what's working
6. **Airtable write** — stores learning patterns for downstream use

## External services
- **Airtable** — source of tweet performance data + destination for learning patterns
- **Anthropic (Claude)** — AI analysis via lmChatAnthropic node

## Credentials to configure
- `YOUR_AIRTABLE_API_KEY_HERE` — Airtable personal access token
- `YOUR_ANTHROPIC_API_KEY_HERE` — Anthropic API key
- Airtable base ID and table IDs for posted tweets and learning patterns tables

## Notes
- This workflow closes the feedback loop: post → measure → learn → apply
- The AI agent prompt is in the agent node — customise to match your content goals and what signals you care about
- Learnings are consumed by the Posting Bot's prefetch step
