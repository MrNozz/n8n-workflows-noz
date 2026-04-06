# Research Pipeline

**26 nodes | 4 scheduled triggers**

## What it does
Automated content research pipeline. Runs on daily and weekly schedules, scrapes data from X using Apify, aggregates and structures it, and stores the output in Airtable for downstream content workflows to consume.

## Triggers

| Schedule | Purpose |
|----------|---------|
| Daily 8am | Primary research terms |
| Daily 7pm | Primary research terms (second run) |
| Mon/Wed/Fri | Secondary research terms |
| Sunday 6pm | Rotating weekly terms |

## Data flow

1. **Schedule trigger fires**
2. **Research terms injected** (via Set node or code depending on schedule)
3. **Apify scrape** runs against X for each term
4. **Data merge** combines results from parallel scrapes
5. **Code node** normalises and structures the data
6. **Airtable write** stores structured research output

## External services
- **Apify** — X scraping
- **Airtable** — research storage

## Credentials to configure
- `YOUR_APIFY_API_KEY_HERE` — Apify personal API token
- `YOUR_AIRTABLE_API_KEY_HERE` — Airtable personal access token
- Airtable base ID and table IDs for your research tables

## Notes
- Terms are configured inside the workflow nodes — update them to match your own research focus
- The rotating Sunday terms allow you to vary research angles week to week
- Output is consumed by the JB - Posting Bot and Learning Workflow
