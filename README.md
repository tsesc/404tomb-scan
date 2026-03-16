# 404Tomb Scan

A coding agent skill that scans [404tomb.com](https://404tomb.com)'s dead startup database (1000+ failed products) before you start building new ideas.

## What it does

When you describe a new startup idea, this skill automatically:

1. Generates relevant search keywords from your idea
2. Searches the 404tomb.com API for similar dead products
3. Filters results semantically for true relevance
4. Reports matching products with lifespan, tags, and lessons
5. Provides pattern analysis, differentiation opportunities, and a risk verdict

## Installation

> Installation differs by platform. Claude Code and Cursor have built-in plugin support. Codex, OpenCode, and Gemini CLI require manual setup.

### Claude Code (via Marketplace)

Add the marketplace, then install:

```
/plugin marketplace add tsesc/404tomb-marketplace
/plugin install 404tomb-scan@404tomb-marketplace
```

### Cursor

In Cursor Agent chat:

```
/add-plugin 404tomb-scan
```

Or search for "404tomb-scan" in the plugin marketplace.

### Codex

Tell Codex:

```
Fetch and follow instructions from https://raw.githubusercontent.com/tsesc/404tomb-scan/refs/heads/main/.codex/INSTALL.md
```

### OpenCode

Tell OpenCode:

```
Fetch and follow instructions from https://raw.githubusercontent.com/tsesc/404tomb-scan/refs/heads/main/.opencode/INSTALL.md
```

### Gemini CLI

```bash
gemini extensions install https://github.com/tsesc/404tomb-scan
```

To update:

```bash
gemini extensions update 404tomb-scan
```

### Verify Installation

Start a new session and describe a startup idea (e.g., "I want to build an AI travel planner"). The agent should automatically invoke the 404tomb-scan skill and report similar failed products.

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
