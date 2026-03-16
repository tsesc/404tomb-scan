# 404Tomb Scan

A coding agent skill that scans [404tomb.com](https://404tomb.com)'s dead startup database (1000+ failed products) before you start building new ideas.

## What it does

When you describe a new startup idea, this skill automatically:

1. Generates relevant search keywords from your idea
2. Searches the 404tomb.com API for similar dead products
3. Filters results semantically for true relevance
4. Reports matching products with lifespan, tags, and lessons
5. Provides pattern analysis, differentiation opportunities, and a risk verdict

## Supported Agents

| Agent | Install Method |
|-------|---------------|
| **Claude Code** | `claude plugin add tsesc/404tomb-scan` |
| **Cursor** | Clone + `.cursor-plugin/` |
| **Codex** | See [.codex/INSTALL.md](.codex/INSTALL.md) |
| **OpenCode** | See [.opencode/INSTALL.md](.opencode/INSTALL.md) |
| **Gemini CLI** | `gemini extensions install tsesc/404tomb-scan` |

## Usage

Just describe your idea — the skill triggers automatically when brainstorming new products.

```
I want to build an AI-powered travel planner
```

The skill will scan 404tomb.com and report similar failed products with analysis.

You can also invoke it directly:

```
/404tomb-scan
```

## License

MIT
