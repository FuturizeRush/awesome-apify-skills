---
name: Web Scraping with Apify
description: |
  This skill should be used when the user asks to
  "scrape a website", "extract data from a page",
  "crawl a URL", "get content from a website",
  "use Apify to scrape", "run an Apify actor",
  "extract structured data from the web",
  or needs to collect data from websites at scale.
version: 0.1.0
---

# Web Scraping with Apify

Scrape websites and extract structured data using Apify actors through their REST API. No browser automation setup needed -- Apify handles the infrastructure.

## Prerequisites

Set the `APIFY_API_TOKEN` environment variable. Get a token at [console.apify.com/account/integrations](https://console.apify.com/account/integrations?fpr=rush).

## Quick Start

Run any Apify actor via the REST API:

```bash
curl -X POST "https://api.apify.com/v2/acts/apify~web-scraper/runs?token=$APIFY_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"startUrls": [{"url": "https://example.com"}]}'
```

Then fetch results:

```bash
curl "https://api.apify.com/v2/datasets/{DATASET_ID}/items?token=$APIFY_API_TOKEN"
```

## Common Actors

| Actor | Use Case | Actor ID |
|-------|----------|----------|
| Web Scraper | General-purpose scraping with custom page function | `apify/web-scraper` |
| Cheerio Scraper | Fast HTML scraping without browser rendering | `apify/cheerio-scraper` |
| Playwright Scraper | JavaScript-heavy sites needing full browser | `apify/playwright-scraper` |
| Website Content Crawler | Extract text content from entire sites | `apify/website-content-crawler` |

Browse more actors at [apify.com/store](https://apify.com/store?fpr=rush).

## Workflow

### 1. Start an Actor Run

```python
import httpx, os

APIFY_TOKEN = os.environ["APIFY_API_TOKEN"]

response = httpx.post(
    f"https://api.apify.com/v2/acts/apify~web-scraper/runs?token={APIFY_TOKEN}",
    json={
        "startUrls": [{"url": "https://example.com"}],
        "maxPagesPerCrawl": 10,
    },
)
run = response.json()["data"]
run_id = run["id"]
```

### 2. Wait for Completion

```python
import time

while True:
    status = httpx.get(
        f"https://api.apify.com/v2/actor-runs/{run_id}?token={APIFY_TOKEN}"
    ).json()["data"]["status"]
    if status in ("SUCCEEDED", "FAILED", "ABORTED"):
        break
    time.sleep(5)
```

### 3. Get Results

```python
dataset_id = run["defaultDatasetId"]
items = httpx.get(
    f"https://api.apify.com/v2/datasets/{dataset_id}/items?token={APIFY_TOKEN}"
).json()
```

## Tips

- Use `maxPagesPerCrawl` to limit costs during development.
- Use `Website Content Crawler` for RAG pipelines -- it outputs clean text.
- Use webhooks instead of polling for production workflows.
- Set `APIFY_API_TOKEN` in `.claude/settings.json` env block for persistent access.

## Reference Files

- **`references/api-reference.md`** -- Full Apify API endpoints and parameters
