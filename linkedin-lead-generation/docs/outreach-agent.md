# Outreach Agent

**38 nodes | Personalised outreach generation**

## What it does
Takes top-scored leads and generates personalised outreach messages using an AI agent. Sequences the messages and optionally sends or queues them for review.

## Triggers
Called by the main orchestration workflow.

## Data flow
1. Receives high-score leads
2. For each lead: AI agent generates a personalised message using lead + company context
3. Message is logged to Airtable
4. Optionally sends via email/LinkedIn or queues for manual review

## Credentials to configure
- `YOUR_OPENROUTER_API_KEY_HERE` or `YOUR_ANTHROPIC_API_KEY_HERE`
- `YOUR_EMAIL_API_KEY_HERE` (if sending automatically)
- `YOUR_AIRTABLE_API_KEY_HERE`
- Outreach prompt/tone in the agent system prompt — customise to your brand voice

## Notes
- By default the workflow logs drafts to Airtable for review before sending — safer for most use cases
- Enable auto-send only after reviewing a batch of drafts first
