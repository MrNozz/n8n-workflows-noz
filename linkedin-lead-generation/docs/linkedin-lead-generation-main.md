# LinkedIn Lead Generation Main

**96 nodes | Master orchestration workflow**

## What it does
Coordinates the full LinkedIn lead generation pipeline. Triggers the sub-workflows in sequence — finding leads, researching companies, scoring, and preparing for outreach.

## Triggers
Schedule-based or manual trigger. Configure the schedule to match your prospecting cadence.

## Data flow
1. Trigger fires
2. Calls **Lead Finder** sub-workflow to discover prospects
3. Passes leads to **Company Research** for enrichment
4. Sends enriched leads to **Lead Scorer** for AI scoring
5. Routes top-scored leads to **Outreach Agent**
6. Logs results to Airtable

## Credentials to configure
- `YOUR_AIRTABLE_API_KEY_HERE`
- `YOUR_AIRTABLE_BASE_ID_HERE`
- Sub-workflow IDs (update after importing the sub-workflows into your instance)

## Notes
- Import sub-workflows first, then update the Execute Workflow node IDs in this workflow to match your imported versions
