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

| Skill | Apify Actor | Standalone |
|-------|-------------|------------|
| [Web Scraping](skills/web-scraping/) | General-purpose ([Actor Store](https://apify.com/store?fpr=rush)) | — |
| [Threads Scraper](skills/threads-scraper/) | [meta-threads-scraper](https://apify.com/futurizerush/meta-threads-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/threads-scraper-skill) |
| [Threads Replies](skills/threads-replies/) | [threads-replies-scraper](https://apify.com/futurizerush/threads-replies-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/threads-replies-skill) |
| [Google News](skills/google-news/) | [google-news-scraper](https://apify.com/futurizerush/google-news-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/google-news-scraper-skill) |
| [Google Maps](skills/google-maps/) | [google-maps-scraper](https://apify.com/futurizerush/google-maps-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/google-maps-scraper-skill) |
| [YouTube Email](skills/youtube-email/) | [youtube-email-scraper](https://apify.com/futurizerush/youtube-email-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/youtube-email-scraper-skill) |
| [TikTok Comments](skills/tiktok-comments/) | [tiktok-comment-scraper](https://apify.com/futurizerush/tiktok-comment-scraper?fpr=rush) | [repo](https://github.com/FuturizeRush/tiktok-comment-scraper-skill) |

All output field names verified from real API runs. All Actor URLs verified accessible (HTTP 200).

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
- [Claude Code Skills Documentation](https://docs.claude.com/en/docs/claude-code/plugins)

## License

MIT
