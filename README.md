# Jobup.ch Jobs Scraper

Extract structured data from [jobup.ch](https://jobup.ch) — jobup.ch — Switzerland's second-largest job board. Workload % filters, direct apply URLs, and incremental change tracking.

**[Jobup.ch Jobs Scraper on Apify →](https://apify.com/blackfalcondata/jobup-ch-scraper)**

---

## Key features

**Search with filters** — Search by keyword and location. Filter by country, employment type, and more.

**Detail enrichment** — Fetch full job descriptions, employer profiles, contact information for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

---

## Use cases

**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from jobup.ch on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from jobup.ch.

---

## Quick start

```json
{
  "query": "software engineer",
  "maxResults": 50,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job search keywords. |
| `country` | enum | `"CH"` | Which market to search. |
| `location` | string | — | City or region to search in (e.g. Zurich, Bern, Basel). |
| `employmentType` | enum | `""` | Filter by employment type. |
| `maxResults` | integer | `25` | Maximum total results (0 = unlimited). |
| `includeDetails` | boolean | `true` | Fetch full job details. |
| `descriptionMaxLength` | integer | `0` | Truncate description to N chars. 0 = no truncation. |
| `compact` | boolean | `false` | Core fields only (for AI-agent/MCP workflows). |
| `incrementalMode` | boolean | `false` | Compare against previous run state. |
| `stateKey` | string | — | Stable identifier for tracked universe. |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape jobup.ch?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->

---

## Related products by Black Falcon Data

- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 04*
