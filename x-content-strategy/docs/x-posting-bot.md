# JB - Posting Bot

**57 nodes | 8 scheduled daily triggers**

## What it does
Fully automated X (Twitter) content posting bot. Runs throughout the day, generates tweets using an AI agent with context from Airtable, runs each tweet through a self-critique loop, and publishes via the Twitter API.

## Triggers
8 schedule triggers, each representing a content slot:

| Time | Slot Type |
|------|-----------|
| 7am | Wildcard |
| 9am | Exploit |
| 12pm | Experiment |
| 2pm | Exploit |
| 4pm | Synta CTA |
| 7pm | Wildcard |
| 9pm | Exploit |
| 11pm | Experiment |

Each slot type has a different content goal (viral/opinion, proven angle, test, product CTA).

## Data flow

1. **Schedule trigger fires** for a given slot
2. **Airtable prefetch**: pulls recent tweets, learning patterns, weekly research rollup, weekly analysis
3. **Slot context node**: injects slot-specific instructions (tone, goal, constraints)
4. **AI Generate Tweet**: LLM generates a tweet draft (Sonnet 4.5 via OpenRouter)
5. **Self-Critique agent**: reviews the draft against quality criteria
6. **Critique Gate**: if draft passes → continue; if fail → increment attempt counter
7. **Attempt Check**: if max retries hit → skip slot and notify via Telegram; else loop back
8. **Save to Airtable**: approved draft stored
9. **Post to Twitter**: publishes via HTTP Request to Twitter API
10. **Telegram confirmation**: sends success or failure notification
11. **Airtable update**: marks record as posted

## External services
- **Airtable** — stores tweet drafts, performance data, research, learning patterns
- **OpenRouter** (Sonnet 4.5, Kimi K2.6, GPT-4o-mini) — AI generation and critique
- **Twitter/X API** — posting
- **Telegram** — notifications
- **Google Drive** — PDF uploads (used for CTA slot lead magnet)
- **Typefully** — draft creation for scheduled posts

## Credentials to configure
- `YOUR_TWITTER_API_KEY_HERE` — Twitter API v2 credentials
- `YOUR_AIRTABLE_API_KEY_HERE` — Airtable personal access token
- `YOUR_OPENROUTER_API_KEY_HERE` — OpenRouter API key
- `YOUR_TELEGRAM_BOT_TOKEN_HERE` — Telegram bot token
- `YOUR_TELEGRAM_CHAT_ID_HERE` — Telegram chat ID for notifications
- `YOUR_GOOGLE_DRIVE_FOLDER_ID_HERE` — Google Drive folder for PDF uploads
- `YOUR_TYPEFULLY_API_KEY_HERE` — Typefully API key

## Airtable tables required
- Recent Tweets table
- Learning Patterns table
- Daily Research table
- Weekly Analysis table
- Weekly Research Rollup table

You'll need to update all Airtable base IDs and table IDs to match your own setup.

## Notes
- The self-critique + retry loop means the bot will attempt up to N times before skipping a slot
- Slot context nodes contain the prompt logic for each slot type — customise these to match your content strategy
- The 4pm slot generates a PDF lead magnet and uploads it to Google Drive before posting
