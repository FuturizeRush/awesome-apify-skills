# Awesome Apify Skills for Claude Code

A collection of Claude Code skills for web scraping and data extraction with [Apify](https://apify.com?fpr=rush) actors. Install all skills at once, or pick individual ones.

## What This Does

Install this plugin and Claude Code learns how to scrape websites, extract data, and run Apify actors on your behalf. Just say:

- *"Scrape this website for product prices"*
- *"Get the latest AI news from Google News"*
- *"Find coffee shops in Taipei with emails"*
- *"Scrape replies from this Threads post"*
- *"Find YouTube channels about AI with contact emails"*
- *"Get comments from this TikTok video"*

Claude handles the API calls, waits for results, and returns structured data.

## Setup

1. Get an [Apify API token](https://console.apify.com/account/integrations?fpr=rush)

2. Add to your `.claude/settings.json`:
```json
{
  "env": {
    "APIFY_API_TOKEN": "your-token-here"
  }
}
```

3. Add the marketplace and install skills:
```bash
# Add the marketplace
/plugin marketplace add FuturizeRush/awesome-apify-skills

# Install individual skills
/plugin install threads-scraper@apify-skills
/plugin install google-news-scraper@apify-skills
```

Or install standalone repos directly (see links below).

## Skills

| Skill | Description | Apify Actor | Standalone |
|-------|-------------|-------------|------------|
| [Web Scraping](skills/web-scraping/) | Scrape websites and extract structured data | [Actor Store](https://apify.com/store?fpr=rush) | — |
| [Threads Scraper](skills/threads-scraper/) | Scrape Threads posts by user, keyword, or search | [meta-threads-scraper](https://apify.com/futurizerush/meta-threads-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/threads-scraper-skill) |
| [Threads Replies](skills/threads-replies/) | Extract replies and comments from Threads posts | [threads-replies-scraper](https://apify.com/futurizerush/threads-replies-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/threads-replies-skill) |
| [Google News](skills/google-news/) | Search and extract news articles with full content | [google-news-scraper](https://apify.com/futurizerush/google-news-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/google-news-scraper-skill) |
| [Google Maps](skills/google-maps/) | Extract business listings with emails, ratings, hours | [google-maps-scraper](https://apify.com/futurizerush/google-maps-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/google-maps-scraper-skill) |
| [YouTube Email](skills/youtube-email/) | Find email addresses and contacts from YouTube channels | [youtube-email-scraper](https://apify.com/futurizerush/youtube-email-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/youtube-email-scraper-skill) |
| [TikTok Comments](skills/tiktok-comments/) | Extract comments and replies from TikTok posts | [tiktok-comment-scraper](https://apify.com/futurizerush/tiktok-comment-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/tiktok-comment-scraper-skill) |
| [ATS Job Postings](skills/ats-job-postings/) | New job postings since a date or window from Ashby, Greenhouse, Lever and SmartRecruiters boards. | [publicrecords/ashby-jobs-scraper](https://apify.com/publicrecords/ashby-jobs-scraper) | — |
| [Company Social Links](skills/company-social-profiles/) | Company domain or name to official LinkedIn, X, YouTube, Instagram and Facebook links, with evidence. | [publicrecords/company-social-profile-finder](https://apify.com/publicrecords/company-social-profile-finder) | — |
| [Etsy Market Research](skills/etsy-market-research/) | Etsy search listings and shop daily/7-day/28-day sales from public shop counters. | [publicrecords/etsy-search-scraper](https://apify.com/publicrecords/etsy-search-scraper) | — |
| [Calibration Ledger](skills/forecast-track-record/) | Forecast track records for IMF, OECD, Fed, ECB SPF and listed issuers (errors and bias). | [publicrecords/calibration-ledger](https://apify.com/publicrecords/calibration-ledger) | — |
| [Google Ads Transparency](skills/google-ads-transparency/) | Competitor Google ads from the Ads Transparency Center, with first and last shown dates. | [publicrecords/google-ads-transparency-scraper](https://apify.com/publicrecords/google-ads-transparency-scraper) | — |
| [Gov Tenders & Grants](skills/gov-tenders-and-grants/) | Official public procurement and grants: Grants.gov, SAM.gov, USAspending, UK Find a Tender, EU TED, and Legistar meetings. | [publicrecords/grants-gov-scraper](https://apify.com/publicrecords/grants-gov-scraper) | — |
| [Sports Odds](skills/sports-odds/) | Live odds from 24 Kambi-powered sportsbooks, with every book's price and the best price per outcome. | [publicrecords/sports-odds-api](https://apify.com/publicrecords/sports-odds-api) | — |
| [Tennis Scores](skills/tennis-scores/) | ATP and WTA match scores, tournament draws and tour rankings. Called through the Apify API with your own token (Standby/MCP is not built). | [publicrecords/tennis-scores-api](https://apify.com/publicrecords/tennis-scores-api) |
| [Spotify Play Counts](skills/spotify-play-counts/) | Play counts for tracks on a Spotify album, artist or playlist, plus monthly listeners. | [publicrecords/spotify-play-count-scraper](https://apify.com/publicrecords/spotify-play-count-scraper) | — |

All output field names verified from real API runs.

## Contributing

Have a useful Apify workflow? Add a new skill! Contributions for **any** Apify actor are welcome — not just the ones listed here.

1. Create a directory under `skills/`
2. Add a `SKILL.md` with YAML frontmatter (see existing skills for format)
3. Add reference files under `references/` if needed
4. Open a PR

See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## Disclosure

Some skills in this collection use actors built by the maintainer ([@FuturizeRush](https://apify.com/futurizerush?fpr=rush)). Links to Apify include an affiliate tracking parameter. Community contributions for any Apify actor are welcome.

## Links

- [Apify Platform](https://apify.com?fpr=rush)
- [Apify Actor Store](https://apify.com/store?fpr=rush)
- [Claude Code Plugins Documentation](https://code.claude.com/docs/en/plugins)

## License

MIT
