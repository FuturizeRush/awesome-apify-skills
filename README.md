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

3. Install the full collection:
```bash
claude mcp add-plugin /path/to/awesome-apify-skills
```

Or install individual skills (see links below).

## Skills

| Skill | Description | Standalone |
|-------|-------------|------------|
| [Web Scraping](skills/web-scraping/) | Scrape websites and extract structured data using Apify actors | — |
| [Threads Scraper](skills/threads-scraper/) | Scrape Meta Threads posts, search by keyword or hashtag | [repo](https://github.com/FuturizeRush/threads-scraper-skill) |
| [Threads Replies](skills/threads-replies/) | Extract replies and comments from Threads posts | [repo](https://github.com/FuturizeRush/threads-replies-skill) |
| [Google News](skills/google-news/) | Search and extract news articles with full content | [repo](https://github.com/FuturizeRush/google-news-scraper-skill) |
| [Google Maps](skills/google-maps/) | Extract business listings with emails, ratings, hours | [repo](https://github.com/FuturizeRush/google-maps-scraper-skill) |
| [YouTube Email](skills/youtube-email/) | Find email addresses and contacts from YouTube channels | [repo](https://github.com/FuturizeRush/youtube-email-scraper-skill) |
| [TikTok Comments](skills/tiktok-comments/) | Extract comments and replies from TikTok posts | [repo](https://github.com/FuturizeRush/tiktok-comment-scraper-skill) |

All output field names are verified from real API runs.

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
