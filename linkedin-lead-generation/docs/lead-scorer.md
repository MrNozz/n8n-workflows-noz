# Lead Scorer

**25 nodes | AI-powered lead scoring**

## What it does
Takes enriched leads and scores them using an AI agent based on your defined ICP criteria. Outputs a score and a short reasoning summary per lead.

## Triggers
Called by the main orchestration workflow.

## Data flow
1. Receives enriched lead list
2. For each lead: passes profile + company data to AI scoring agent
3. Agent evaluates fit against ICP criteria
4. Returns score (0-100) + reasoning
5. Updates Airtable with score

## Credentials to configure
- `YOUR_OPENROUTER_API_KEY_HERE` or `YOUR_ANTHROPIC_API_KEY_HERE`
- `YOUR_AIRTABLE_API_KEY_HERE`
- Scoring criteria defined in the AI agent system prompt — customise to match your ICP

## Notes
- The scoring prompt is the key thing to customise — the more specific your ICP, the better the scores
