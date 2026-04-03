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

### How many results can I get from jobup.ch?

The number of results depends on the search query and available listings on jobup.ch. Use the `maxResults` parameter to control how many results are returned per run. Set it to `0` for unlimited results.

### Does Jobup.ch Scraper support recurring monitoring?

Yes. Enable incremental mode to only receive new or changed listings on subsequent runs. This is ideal for scheduled monitoring where you want to track changes over time without re-processing the full dataset.

### Can I filter by workload percentage?

Yes. jobup.ch listings include `employmentGrades` — a range of workload percentages (e.g. 80–100%). These are returned as structured data on every result.

### Can I integrate Jobup.ch Scraper with other apps?

Yes. Jobup.ch Scraper works with Apify's [integrations](https://apify.com/integrations) to connect with tools like Zapier, Make, Google Sheets, Slack, and more. You can also use webhooks to trigger actions when a run completes.

### Can I use Jobup.ch Scraper through an MCP Server?

Yes. Apify provides an [MCP Server](https://apify.com/apify/actors-mcp-server) that lets AI assistants and agents call this actor directly. Use compact mode and `descriptionMaxLength` to keep payloads manageable for LLM context windows.

### Is it legal to scrape jobup.ch?

This actor extracts publicly available data from jobup.ch. Web scraping of public information is generally considered legal, but you should always review the target site's terms of service and ensure your use case complies with applicable laws and regulations, including GDPR where relevant.

---

## Known limitations

- Contact email addresses are not available — jobup.ch encrypts recipient tokens server-side. Contact name and phone are returned where provided.
- Search results are limited to Switzerland. jobup.ch does not serve other markets.
- Job listings that require a login to view full details are not enriched beyond the SERP fields.
- Result counts vary by query specificity — broad searches return more results but with lower relevance.

---

## Related products by Black Falcon Data

- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 04*
