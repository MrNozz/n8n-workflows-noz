# Lead Finder

**97 nodes | Prospect discovery**

## What it does
Discovers and pulls potential leads matching your ideal customer profile from LinkedIn. Uses Apify for scraping or LinkedIn API depending on your configuration.

## Triggers
Called by the main orchestration workflow (Execute Workflow trigger).

## Data flow
1. Receives search parameters (job title, company size, industry, location etc.)
2. Runs scraper/API to pull matching profiles
3. Normalises and deduplicates results
4. Returns structured lead list to caller

## Credentials to configure
- `YOUR_APIFY_API_KEY_HERE` (or LinkedIn API credentials)
- `YOUR_AIRTABLE_API_KEY_HERE`
- Search criteria configured inside Set nodes

## Notes
- Customise the search parameters in the Set nodes to match your ICP
- Built-in deduplication checks Airtable before adding new leads
