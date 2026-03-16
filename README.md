# 404Tomb Scan

[English](README.md) | [繁體中文](README.zh-TW.md)

404Tomb Scan is a skill for your coding agent that automatically scans [404tomb.com](https://404tomb.com)'s database of 1000+ dead internet products before you invest time building a new idea.

## How it works

When you describe a new startup idea, your coding agent doesn't just start building. It first checks [404tomb.com](https://404tomb.com) — a digital graveyard cataloging failed internet products — to find similar ideas that have already died.

The skill generates multiple search keywords from your idea, queries the 404tomb API in parallel, then uses semantic judgment to filter out false positives. For each relevant match, it reports what the product did, how long it lived, and what you can learn from its failure.

After listing matches, it synthesizes patterns across similar failures and provides differentiation opportunities — concrete ways your idea could avoid the same fate. Every scan ends with a verdict: **safe**, **proceed with caution**, or **graveyard is full of these**.

Because the skill triggers automatically when you brainstorm, you don't need to do anything special. Your coding agent just knows to check the graveyard first.

## Installation

**Note:** Installation differs by platform. Claude Code and Cursor have built-in plugin marketplaces. Codex, OpenCode, and Gemini CLI require manual setup.

### Claude Code (via Plugin Marketplace)

In Claude Code, register the marketplace first:

```bash
/plugin marketplace add tsesc/404tomb-marketplace
```

Then install the plugin from this marketplace:

```bash
/plugin install 404tomb-scan@404tomb-marketplace
```

### Cursor (via Plugin Marketplace)

In Cursor Agent chat, install from marketplace:

```text
/add-plugin 404tomb-scan
```

or search for "404tomb-scan" in the plugin marketplace.

### Codex

Tell Codex:

```
Fetch and follow instructions from https://raw.githubusercontent.com/tsesc/404tomb-scan/refs/heads/main/.codex/INSTALL.md
```

**Detailed docs:** [.codex/INSTALL.md](.codex/INSTALL.md)

### OpenCode

Tell OpenCode:

```
Fetch and follow instructions from https://raw.githubusercontent.com/tsesc/404tomb-scan/refs/heads/main/.opencode/INSTALL.md
```

**Detailed docs:** [.opencode/INSTALL.md](.opencode/INSTALL.md)

### Gemini CLI

```bash
gemini extensions install https://github.com/tsesc/404tomb-scan
```

To update:

```bash
gemini extensions update 404tomb-scan
```

### Verify Installation

Start a new session in your chosen platform and describe a startup idea (for example, "I want to build an AI travel planner" or "let's make a meditation app"). The agent should automatically invoke the 404tomb-scan skill and report similar failed products.

## What's Inside

### Skills

- **404tomb-scan** — Multi-keyword API search against 404tomb.com with semantic filtering, pattern analysis, and risk verdicts

### API Reference

The skill uses the following 404tomb.com endpoints:

| Endpoint | Purpose |
|----------|---------|
| `GET /api/search/dead?category=all&q={keyword}&limit=500` | Search dead products by keyword |
| `GET /api/tags` | List all 181 product categories with counts |
| `GET /api/products/filter?category={tagId}&limit=500` | Filter by category tag |
| `GET /api/stats` | Get total deceased product count |

## Updating

Skills update automatically when you update the plugin:

```bash
/plugin update 404tomb-scan
```

## License

MIT License - see LICENSE file for details.

## Support

- **Issues**: https://github.com/tsesc/404tomb-scan/issues
- **Marketplace**: https://github.com/tsesc/404tomb-marketplace
