# Company Research

**22 nodes | Company intelligence enrichment**

## What it does
Takes a list of leads and enriches each one with company-level context — size, industry, recent news, tech stack, funding status etc.

## Triggers
Called by the main orchestration workflow.

## Data flow
1. Receives lead list
2. For each lead: pulls company data via API/scraper
3. Enriches the lead record with company intelligence
4. Returns enriched leads to caller

## Credentials to configure
- `YOUR_COMPANY_RESEARCH_API_KEY_HERE` (e.g. Clearbit, Apollo, or similar enrichment API)
- `YOUR_AIRTABLE_API_KEY_HERE`

## Notes
- Swap in your preferred enrichment provider — the pattern works with any API that returns company data by domain or name
