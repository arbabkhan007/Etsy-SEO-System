# Data source — Apify Etsy Search Scraper (optional, for the Competitor SERP phase)

**Satisfies System Law 2 (Zero-Hallucination Evidence Traceability):** every competitor statistic below traces to a live run id and a dataset row. Tag outputs `[Data Source: Apify etsy-search-scraper run <runId>]`.

## When to use
Use this source for the competitor SERP check when the agent cannot fetch Etsy search pages directly (Etsy's `/search` is robots-disallowed and sits behind DataDome, so direct fetches are often blocked or inconsistent). The Actor runs on the user's own proxy (Apify residential by default) and returns the rendered results as rows.

## Setup (once)
Add to the agent's MCP config:

```json
{ "mcpServers": { "apify": { "url": "https://mcp.apify.com/?tools=publicrecords/etsy-search-scraper", "headers": { "Authorization": "Bearer <APIFY_TOKEN>" } } } }
```

Free Apify account; $6 per 1,000 listing rows; a blocked page is not charged.

## Call
```json
{ "queries": ["<primary keyword>"], "maxPages": 2 }
```

## Fields the SERP phase consumes
| SERP-phase need | row field |
|---|---|
| competitor titles for the title-pattern scan | `title` |
| price band (min / median / max) | `price`, `currency` |
| social proof on page 1 | `rating_value`, `review_count` (`review_count_approx` = Etsy rounded) |
| badge presence | `bestseller`, `star_seller`, `etsys_pick`, `popular_now` |
| paid vs organic density | `is_ad` (from Etsy's own slot list; `null` = unknown) |
| who owns the page | `shop_name`, `position` |

## Difficulty inputs
- **Ad density** = ads / rows on page 1.
- **Badge density** = rows with any of bestseller/star_seller/etsys_pick ÷ rows.
- **Review floor** = 25th-percentile `review_count` on page 1.
Report these three with the run id; the skill's existing difficulty logic consumes them unchanged.

## Caveats
- Results reflect what Etsy shows a logged-out visitor from the proxy's region.
- Etsy caps a query at 20 pages; 2 pages are enough for the SERP check.
