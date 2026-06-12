# Odoo Apps Store Scraper & Market Intelligence Engine

[![Apify Marketplace](https://img.shields.io/badge/Apify-Marketplace-FF7754)](https://apify.com/foxpink/odoo-apps-market-intelligence)
[![GitHub](https://img.shields.io/badge/GitHub-Repo-181717)](https://github.com/FoxPink/odoo-apps-market-intelligence)

> Scrape, analyze, and export Odoo Apps Store data with filters. **Version comparison across Odoo 15-18 included.** Find market gaps, estimate competitor revenue, and discover profitable niches.

---

## Features

- **Browse & Filter** — Search by keyword, Odoo version (10.0-19.0), category (18 categories), price (Free/Paid), and author
- **Smart Sorting** — Sort by downloads, estimated revenue, or rating
- **Estimated Revenue** — `price x purchases` — find goldmine modules
- **Version Comparison (new)** — Compare price, screenshots, dependencies, and reviews across Odoo versions 15.0-18.0 for each app
- **Rich Detail Data** — Technical name, license, lines of code, supported versions, screenshots, user reviews, last updated, created on
- **Competitor Matrix** — Category breakdown with revenue comparison and top authors ranking
- **Version Adoption Trends** — Distribution of apps across Odoo versions
- **Zero DOM** — Cheerio-based, no browser, fast and cheap

## Input

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `searchKeyword` | string | `""` | Search for specific apps |
| `odooVersion` | enum | All | Filter by version (10.0-19.0) |
| `category` | enum | All | 18 categories (Accounting, eCommerce, etc.) |
| `filterType` | enum | All | Free, Paid, or All |
| `freeAppsOnly` | boolean | `false` | Show only free apps |
| `authorSearch` | string | `""` | Filter by developer name |
| `sortBy` | enum | — | `downloads`, `revenue`, or `rating` |
| `maxItems` | integer | `500` | Max apps (max 5000) |
| `scrapeDetails` | boolean | `true` | Visit detail pages for richer data |
| **`enableVersionComparison`** (new) | boolean | `false` | Compare app data across supported Odoo versions |

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
| `rating` / `ratingCount` | number | 4.8 / 270 |
| `latestVersion` | string | "17.0" |
| `supportedVersions` | array | ["16.0","17.0","18.0"] |
| `screenshots` | array | URL list |
| `reviews` | array | Author, date, rating, text |
| `dependencies` | array | Module dependencies |
| `lastUpdated` / `createdOn` | string | Date strings |
| **`versionComparison`** (new) | object | `{ "16.0": { price, screenshots, dependencies }, "18.0": {...} }` |
| `versionAdoptionPercent` | object | Adoption distribution |

Plus a `summary` entry with aggregate stats, category breakdown, top authors ranking, and version adoption trends.

---

## Pricing

**$0.05 per 1,000 results.** One result = one app record. Lightweight Cheerio scraper keeps compute costs minimal.

---

## Quick Start

```bash
curl -X POST https://api.apify.com/v2/acts/foxpink~odoo-apps-market-intelligence/runs \
  -H "Content-Type: application/json" \
  -d '{
    "searchKeyword": "payment",
    "odooVersion": "18.0",
    "sortBy": "revenue",
    "maxItems": 100,
    "scrapeDetails": true,
    "enableVersionComparison": true
  }' \
  "https://api.apify.com/v2/acts/foxpink~odoo-apps-market-intelligence/runs?token=YOUR_API_TOKEN"
```

---

## Competitive Landscape

Odoo Market Intel is the **only** Odoo Apps Store scraper on the Apify Marketplace. Zero competition — premium pricing justified by monopoly position and B2B enterprise use case.

---

## Compatibility

- 100% Node.js (18+)
- CheerioCrawler — fast, low memory
- No browser, no headless, no DOM
