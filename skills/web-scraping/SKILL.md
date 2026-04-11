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

## Execution Flow

Apify runs are asynchronous. Every request follows 3 steps:

1. **Start a run** -- POST to the actor API, receive a run ID and dataset ID
2. **Poll until done** -- GET the run status, wait for `SUCCEEDED`
3. **Fetch results** -- GET the dataset items (returns a JSON array)

Typical run time: 30 seconds to 5 minutes depending on the actor and page count.

## Common Actors

| Actor | Use Case | Actor ID |
|-------|----------|----------|
| Web Scraper | General-purpose scraping with custom page function | `apify~web-scraper` |
| Cheerio Scraper | Fast HTML scraping without browser rendering | `apify~cheerio-scraper` |
| Playwright Scraper | JavaScript-heavy sites needing full browser | `apify~playwright-scraper` |
| Website Content Crawler | Extract text content from entire sites | `apify~website-content-crawler` |

Browse more actors at [apify.com/store](https://apify.com/store?fpr=rush).

## Complete Example (Python)

```python
import requests, os, time

TOKEN = os.environ["APIFY_API_TOKEN"]
BASE = "https://api.apify.com/v2"

# Step 1: Start the run
response = requests.post(
    f"{BASE}/acts/apify~web-scraper/runs?token={TOKEN}",
    json={
        "startUrls": [{"url": "https://example.com"}],
        "maxPagesPerCrawl": 10,
    },
)
response.raise_for_status()
run = response.json()["data"]
run_id = run["id"]
dataset_id = run["defaultDatasetId"]

# Step 2: Poll until done
while True:
    status = requests.get(
        f"{BASE}/actor-runs/{run_id}?token={TOKEN}"
    ).json()["data"]["status"]
    if status == "SUCCEEDED":
        break
    if status in ("FAILED", "ABORTED", "TIMED-OUT"):
        raise RuntimeError(f"Run failed: {status}")
    time.sleep(5)

# Step 3: Fetch results
items = requests.get(
    f"{BASE}/datasets/{dataset_id}/items?token={TOKEN}"
).json()
```

## Output Format

Output format varies by actor. Check the actor's page on [Apify Store](https://apify.com/store?fpr=rush) for the specific output schema.

For verified output formats, see the dedicated skills in this collection: Threads Scraper, Threads Replies, Google News, Google Maps, YouTube Email, and TikTok Comments.

## Error Handling

| Error | Cause | Fix |
|-------|-------|-----|
| 401 Unauthorized | Invalid or missing API token | Check `APIFY_API_TOKEN` |
| 404 Not Found | Actor ID is wrong | Verify the actor ID (format: `owner~actor-name`) |
| Run status `FAILED` | Actor error (bad input, site blocking, etc.) | Check run log at `https://api.apify.com/v2/actor-runs/{RUN_ID}/log` |
| Run status `TIMED-OUT` | Crawl exceeded timeout | Reduce `maxPagesPerCrawl` or increase timeout in run options |

## Tips

- Use `maxPagesPerCrawl` to limit costs during development.
- Use `Website Content Crawler` (`apify~website-content-crawler`) for RAG pipelines -- it outputs clean text.
- Use `Cheerio Scraper` (`apify~cheerio-scraper`) for speed when pages don't need JavaScript rendering.
- Use `Playwright Scraper` (`apify~playwright-scraper`) for JavaScript-heavy SPAs.
- Set `APIFY_API_TOKEN` in `.claude/settings.json` env block for persistent access.
- For social media scraping, use the dedicated skills in this collection (Threads, Google News, Google Maps, YouTube Email, TikTok Comments).

## Links

- [Apify Actor Store](https://apify.com/store?fpr=rush)
- [Apify API docs](https://docs.apify.com/api/v2)
- **`references/api-reference.md`** -- Full Apify API endpoints and parameters
