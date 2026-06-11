# Odoo Apps Store Market Intelligence

<p align="center">
  <a href="https://apify.com/foxpink/odoo-apps-market-intelligence">
    <img src="https://img.shields.io/badge/Run_on_Apify_Cloud-0.01_per_1k_results-FF7754?style=for-the-badge&logo=apify" alt="Run on Apify Cloud">
  </a>
</p>

<p align="center">
  <a href="https://apify.com/foxpink/odoo-apps-market-intelligence">
    <img src="https://img.shields.io/badge/Apify-Store-FF7754?style=flat-square" alt="Apify Store">
  </a>
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="MIT">
</p>

Scrape, analyze, and export **Odoo Apps Store** data with filters. Find market gaps, estimate competitor revenue, and discover profitable niches — all at **$0.01/1k results**.

---

## Why This Actor?

| Problem | Solution |
|---------|----------|
| Manual Odoo Store research takes hours | Bulk scrape 1000s of apps in minutes |
| Can't estimate competitor revenue | `estimatedRevenue = price x purchases` |
| No easy CSV export | 5 API endpoints ready |
| Browser scrapers are slow & expensive | Cheerio = 10x faster, minimal compute |

## Features

- Filter by keyword, Odoo version (10.0-19.0), category (18 categories), price (Free/Paid), and author name
- Sort by downloads, estimated revenue, or rating
- Free-only mode: override price filter to show only free apps
- Extract title, technical name, author, price, rating, purchases, license, dependencies, lines of code
- **Killer feature**: sort by `estimatedRevenue` to find goldmine modules
- Cheerio-based = fast, cheap, no browser
- Export JSON, CSV, filtered views

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
    "maxItems": 100
  }' \
  "https://api.apify.com/v2/acts/foxpink~odoo-apps-market-intelligence/runs?token=YOUR_API_TOKEN"
```

## Sample Output

| Field | Example |
|-------|---------|
| title | Shopify Odoo Connector |
| technicalName | shopify_ept |
| author | Emipro Technologies |
| price | 465.06 |
| purchases | 2,301 |
| estimatedRevenue | 1,070,103.06 |
| rating | 5.0 |
| ratingCount | 270 |
| latestVersion | 17.0 |
| supportedVersions | 16.0, 17.0, 18.0 |
| license | OPL-1 |
| linesOfCode | 14,329 |

## Pricing

**$0.01 per 1,000 results.** One result = one app record. Lightweight Cheerio scraper keeps compute costs minimal.

---

<p align="center">
  Built by <a href="https://apify.com/foxpink">Nguyen Anh Duy</a> — FoxPink Studio
</p>
