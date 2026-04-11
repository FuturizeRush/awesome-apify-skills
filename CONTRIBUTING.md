# Contributing

Thanks for your interest in contributing!

## Adding a New Skill

1. **Create a directory** under `skills/` with a descriptive name (kebab-case)

2. **Write `SKILL.md`** with:
   - YAML frontmatter: `name`, `description` (with trigger phrases), `version`
   - Clear instructions in imperative form
   - Code examples with the Apify API
   - See `skills/web-scraping/SKILL.md` as reference

3. **Add references** (optional): detailed docs under `references/`

4. **Open a PR** with:
   - What the skill does
   - Which Apify actors it uses
   - Example usage

## Skill Format

```yaml
---
name: Your Skill Name
description: |
  This skill should be used when the user asks to
  "specific action 1", "specific action 2", ...
version: 0.1.0
---

# Your Skill Name

[Content in imperative form, 1500-2000 words max]
```

## Guidelines

- Each skill should solve a real use case
- Include working code examples
- Keep SKILL.md focused; put details in `references/`
- Test that Claude Code actually triggers the skill on the intended queries
