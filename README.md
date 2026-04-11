# Awesome Apify Skills for Claude Code

Claude Code skills for web scraping and data extraction with [Apify](https://apify.com?fpr=rush) actors.

## What This Does

Install this plugin and Claude Code learns how to scrape websites, extract data, and run Apify actors on your behalf. Just say:

- *"Scrape this website for product prices"*
- *"Extract all articles from this blog"*
- *"Crawl this site and get the content for my RAG pipeline"*

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

3. Install the plugin:
```bash
claude --plugin-dir /path/to/awesome-apify-skills
```

## Skills

| Skill | Description |
|-------|-------------|
| [Web Scraping](skills/web-scraping/) | Scrape websites and extract structured data using Apify actors |

## Contributing

Have a useful Apify workflow? Add a new skill:

1. Create a directory under `skills/`
2. Add a `SKILL.md` with YAML frontmatter (see existing skills for format)
3. Add reference files under `references/` if needed
4. Open a PR

See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## Links

- [Apify Platform](https://apify.com?fpr=rush)
- [Apify Actor Store](https://apify.com/store?fpr=rush)
- [Rush's Apify Actors](https://airush.dev/)
- [Claude Code Skills Documentation](https://docs.claude.com/en/docs/claude-code/plugins)

## License

MIT
