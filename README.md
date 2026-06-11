# Odoo Apps Store Market Intelligence

[![Apify Marketplace](https://img.shields.io/badge/Apify-Marketplace-FF7754)](https://apify.com/foxpink/odoo-apps-market-intelligence)
[![GitHub](https://img.shields.io/badge/GitHub-Repo-181717)](https://github.com/FoxPink/odoo-apps-market-intelligence)

> Scrape, analyze, and export Odoo Apps Store data with filters. Find market gaps, estimate competitor revenue, and discover profitable niches.

---

## Features

- **Browse & Filter** — Search by keyword, Odoo version, category, price (Free/Paid), and author
- **Smart Sorting** — Sort by downloads, estimated revenue, or rating
- **Free-Only Mode** — Override price filter to show only free apps
- **Rich Data** — Title, author, price, rating, purchases, technical name, license, lines of code, supported versions
- **Killer Feature: Estimated Revenue** — `price × purchases` — sort by this to find goldmine modules
- **CSV/JSON Export** — 6 API endpoints ready for Excel or ETL pipelines
- **Zero DOM** — Cheerio-based, no browser, fast and cheap

## Use Cases

| Who | Why |
|-----|-----|
| Odoo Developers | Find high-demand, low-competition niches |
| Odoo Partners | Track competitor pricing and market share |
| Investors | Estimate module revenue before acquisition |
| Product Managers | Validate new module ideas with real market data |

## Input

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `searchKeyword` | string | `""` | Search for specific apps |
| `odooVersion` | enum | All | Filter by Odoo version (10.0–19.0) |
| `category` | enum | All | Filter by category (18 categories) |
| `filterType` | enum | All | Free, Paid, or All |
| `freeAppsOnly` | boolean | `false` | Override: show only free apps (ignores filterType) |
| `authorSearch` | string | `""` | Filter by developer/author name |
| `sortBy` | enum | — | Sort order: `downloads`, `revenue`, or `rating` |
| `maxItems` | integer | `500` | Max apps to scrape (max 5000) |
| `scrapeDetails` | boolean | `true` | Visit detail pages for richer data |

## Output

Each record:

| Field | Type | Example |
|-------|------|---------|
| `title` | string | "Shopify Odoo Connector" |
| `technicalName` | string | "shopify_ept" |
| `author` | string | "Emipro Technologies" |
| `category` | string | "eCommerce" |
| `price` | number | 465.06 |
| `currency` | string | "EUR" |
| `purchases` | integer | 2301 |
| `estimatedRevenue` | number | 1070103.06 |
| `rating` | number | 4.8 |
| `ratingCount` | integer | 270 |
| `latestVersion` | string | "17.0" |
| `supportedVersions` | array | ["16.0","17.0","18.0"] |
| `license` | string | "OPL-1" |
| `linesOfCode` | integer | 14329 |
| `summary` | string | "Shopify Odoo Connector" |
| `appUrl` | string | "https://apps.odoo.com/..." |

Plus a `summary` entry with aggregate stats (total, avg price, estimated total revenue).

## Pricing

**$0.01 per 1,000 results.** One result = one app record. Lightweight Cheerio scraper keeps compute costs minimal.

## Quick Start

```bash
curl -X POST https://api.apify.com/v2/acts/foxpink~odoo-apps-market-intelligence/runs \
  -H "Content-Type: application/json" \
  -d '{
    "searchKeyword": "payment",
    "odooVersion": "18.0",
    "filterType": "Paid",
    "freeAppsOnly": false,
    "authorSearch": "VentorTech",
    "sortBy": "revenue",
    "maxItems": 100,
    "scrapeDetails": true
  }' \
  "https://api.apify.com/v2/acts/foxpink~odoo-apps-market-intelligence/runs?token=YOUR_API_TOKEN"
```

## Compatibility

- 100% Node.js (18+)
- No browser, no headless, no DOM
- CheerioCrawler — fast, low memory
- ESM (ECMAScript Modules)

## MCP / AI Agent Usage

```json
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["-y", "@apify/mcp-server"],
      "env": { "APIFY_TOKEN": "YOUR_API_TOKEN" }
    }
  }
}
```
