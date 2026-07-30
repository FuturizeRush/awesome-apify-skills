# Apify API Reference

## Authentication

Send the token through an `Authorization: Bearer <token>` header. Do not place
tokens in URLs, logs, or saved command history.

Get your token: [console.apify.com/account/integrations](https://console.apify.com/account/integrations?fpr=rush)

## Core Endpoints

### Run an Actor

```
POST https://api.apify.com/v2/acts/{actorId}/runs
Authorization: Bearer <token>
Content-Type: application/json

{
  "startUrls": [{"url": "https://example.com"}],
  "maxPagesPerCrawl": 10
}
```

Response:
```json
{
  "data": {
    "id": "run_abc123",
    "status": "RUNNING",
    "defaultDatasetId": "dataset_xyz"
  }
}
```

### Check Run Status

```
GET https://api.apify.com/v2/actor-runs/{runId}
Authorization: Bearer <token>
```

Statuses: `READY`, `RUNNING`, `SUCCEEDED`, `FAILED`, `ABORTING`, `ABORTED`, `TIMING-OUT`, `TIMED-OUT`

### Get Dataset Items

```
GET https://api.apify.com/v2/datasets/{datasetId}/items
Authorization: Bearer <token>
```

Query parameters:
- `format` -- `json` (default), `csv`, `xlsx`, `xml`
- `limit` -- Max items to return
- `offset` -- Skip first N items

### Get Key-Value Store Record

```
GET https://api.apify.com/v2/key-value-stores/{storeId}/records/{key}
Authorization: Bearer <token>
```

## Actor Input Schema

Each actor has its own input schema. Common fields:

| Field | Type | Description |
|-------|------|-------------|
| `startUrls` | `array` | URLs to start crawling from |
| `maxPagesPerCrawl` | `integer` | Limit total pages crawled |
| `maxConcurrency` | `integer` | Max parallel requests |
| `proxyConfiguration` | `object` | Proxy settings |

Check actor-specific input at: `https://apify.com/{username}/{actor-name}/input-schema`
