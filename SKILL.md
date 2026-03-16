---
name: 404tomb-scan
description: Use when brainstorming a new startup idea, product concept, or side project - scans 404tomb.com's dead startup database to find similar failed products and extract lessons before investing time building
---

# 404Tomb Scan

## Overview

Before building something new, check if similar ideas have already died. 404tomb.com is a graveyard of 1000+ failed internet products — scanning it first saves you from repeating history.

## When to Use

- Before starting a new startup idea or side project
- When evaluating a product concept
- When someone pitches you an idea and you want a quick reality check
- **NOT** for: researching established companies, market analysis beyond failed products

## Language

Always respond in the same language the user used to describe their idea. If the user writes in English, output in English. If in 繁體中文, output in 繁體中文. This overrides any global language setting.

## How It Works

### Step 1: Generate Search Keywords

From the user's idea, brainstorm 3-6 search keywords covering:
- **Core function** (e.g., "image compress", "photo optimize")
- **Broader domain** (e.g., "image", "photo", "media")
- **Use case** (e.g., "developer tool", "API", "SaaS")
- **Chinese equivalent** if applicable (e.g., "图片压缩")

### Step 2: Search via API

For EACH keyword, fetch:

```
GET https://404tomb.com/api/search/dead?category=all&q={keyword}&limit=500
```

Use WebFetch (Claude Code), web_fetch (Codex), fetch_webpage (Gemini), or equivalent HTTP tool to call the API. Run multiple keywords in parallel when possible.

**IMPORTANT:**
- Search parameter is `q` (NOT `query`)
- `limit` defaults to 30, must set higher to get all results
- Returns products where name OR description matches the keyword
- Run multiple searches with different keywords for thorough coverage

Response format:
```json
{
  "total": 128,
  "products": [{
    "name": "...",
    "description": "...",
    "launch_date": "YYYY-MM-DD",
    "death_date": "YYYY-MM-DD",
    "lifespan_width": 5,
    "tags": ["AI Chatbots", "..."]
  }]
}
```

### Step 3: Filter & Rank by Relevance

Many results will be loosely related. Use semantic judgment to:
1. **Discard** products that merely mention the keyword but do a completely different thing
2. **Rank** remaining by similarity to user's actual idea
3. **Keep top 5-10** most relevant matches

### Step 4: Report Findings

For each match:

| Field | Info |
|-------|------|
| Name | Product name |
| What it did | 1-sentence summary from description |
| Lifespan | launch_date → death_date (X months) |
| Tags | Category tags |
| Similarity | Why this is relevant to the user's idea |
| Lesson | What can be learned from its failure |

### Step 5: Synthesize

- **Pattern analysis**: Common failure patterns among similar products
- **Differentiation opportunities**: How the user's idea could avoid the same fate
- **Risk factors**: Red flags based on the graveyard data
- **Verdict**: safe / proceed with caution / graveyard is full of these

## Additional API Endpoints

- `GET /api/tags` — returns all 181 tags with `{id, name, product_count}`
- `GET /api/products/filter?category={tagId}&limit=500` — filter by tag ID
- `GET /api/stats` — returns `{dead_count}` total deceased count

## Common Mistakes

- **Using `query` instead of `q`** — the API search parameter is `q`, `query` is ignored
- **Only searching one keyword** — always search 3-6 variations to catch different phrasings
- **Not filtering results semantically** — keyword matches are broad, many are false positives
- **Ignoring Chinese-language entries** — many entries are Chinese products with valuable context
- **Dismissing short-lived products** — a 1-month lifespan often means fundamentally flawed, not just poorly executed
