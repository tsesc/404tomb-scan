# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **multi-agent plugin** that provides a single skill (`404tomb-scan`) for scanning [404tomb.com](https://404tomb.com)'s dead startup database. It follows the [superpowers](https://github.com/obra/superpowers) plugin architecture to support Claude Code, Cursor, Codex, OpenCode, and Gemini CLI.

## Architecture

```
.claude-plugin/plugin.json        # Claude Code plugin manifest (no skills path — Claude discovers via directory)
.cursor-plugin/plugin.json        # Cursor manifest (includes skills/ + hooks/ paths)
.codex/INSTALL.md                 # Codex manual install guide
.opencode/INSTALL.md              # OpenCode manual install guide
.opencode/plugins/404tomb-scan.js # OpenCode system prompt injection plugin
gemini-extension.json             # Gemini CLI extension config
GEMINI.md                         # Gemini context file (@imports SKILL.md)
hooks/hooks.json                  # SessionStart hook definition
hooks/session-start               # Bash script: reads SKILL.md, escapes to JSON, injects as context
hooks/run-hook.cmd                # Cross-platform polyglot wrapper (cmd.exe + bash)
skills/404tomb-scan/SKILL.md      # The actual skill — all scanning logic lives here
```

**Key distinction:** `.claude-plugin/plugin.json` does NOT include a `"skills"` path (matches superpowers convention for Claude Code). `.cursor-plugin/plugin.json` DOES include `"skills": "./skills/"` and `"hooks"` paths.

## 404tomb.com API

The skill queries these endpoints:

- `GET /api/search/dead?category=all&q={keyword}&limit=500` — search by keyword. Parameter is `q` (NOT `query`). Default limit is 30.
- `GET /api/tags` — returns 181 tags with `{id, name, product_count}`
- `GET /api/products/filter?category={tagId}&limit=500` — filter by tag ID
- `GET /api/stats` — returns `{dead_count}` (currently 1000+)

## Plugin Distribution

- **Marketplace repo:** [tsesc/404tomb-marketplace](https://github.com/tsesc/404tomb-marketplace) contains `.claude-plugin/marketplace.json` listing this plugin
- **Install flow:** `/plugin marketplace add tsesc/404tomb-marketplace` → `/plugin install 404tomb-scan@404tomb-marketplace`

## Conventions

- All shell scripts must use LF line endings (enforced by `.gitattributes`)
- `hooks/session-start` must remain executable (`chmod +x`)
- `hooks/run-hook.cmd` is a polyglot file — valid as both cmd.exe batch and bash script
- Version is tracked in both `.claude-plugin/plugin.json` and `.cursor-plugin/plugin.json` — keep in sync
