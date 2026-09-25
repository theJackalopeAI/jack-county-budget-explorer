# Jack County Budget Explorer

A public, searchable view of Jack County budget information prepared for SkewTheFuture.com.

## Purpose

The Budget Explorer is intended to make county budget records easier to search, compare and understand without changing the underlying public records.

The public view now supports:

- browsing by **Office / Function** such as Sheriff's Office, County Judge, County Clerk, Tax Assessor-Collector, District Clerk, County Auditor and each Commissioner precinct
- filtering by fund, budget section, account or keyword
- phone-friendly line-item drill-down
- comparison of the FY2026-27 proposed work budget with the original FY2025-26 adopted budget
- source-page references and review-status indicators
- loading another normalized Budget Explorer JSON dataset locally in the browser

## Current source set

The built-in Jack County dataset uses:

- FY2026-2027 proposed budget, Work Budget Version 0003, dated September 10, 2026
- FY2025-2026 adopted budget, adopted August 25, 2025

The September work budget is an image-only scan. During the current rebuild:

- 141 rows that failed automated parsing checks were reviewed against the source PDF
- 18 of those rows were explicitly marked corrected during human review
- the County Treasurer and Tax Assessor-Collector pages, which had been omitted by the original parser, were added directly from the source documents
- the remaining rows retain automated parsing and consistency checks

The Explorer is an independent transcription, not an official Jack County publication. Transcription, OCR or data-entry errors may remain. Important figures should be verified against the official budget documents.

## Office / Function navigation

The **Office / Function** field is a public-navigation layer, not an official county accounting classification. It groups budget sections into recognizable offices or functions while preserving the underlying fund, section, account number and source page. Shared or countywide costs are not automatically allocated to individual offices.

## Other entities and dataset schema

The Explorer can load another normalized Budget Explorer JSON file locally in the browser. Data is not uploaded to a server.

A normalized file can use:

```json
{
  "meta": {
    "entity": "Example Taxing Entity",
    "title": "Example Budget Explorer",
    "current_document": "FY2026-2027 proposed budget",
    "comparison_document": "FY2025-2026 adopted budget",
    "schema_version": "3.0"
  },
  "records": []
}
```

Each record should include at least:

`fund_code`, `fund`, `department_code`, `department`, `type`, `account`, and `account_name`.

The Jack County build also uses fields such as `office`, `fy27_proposed`, `fy26_current`, `fy26_adopted`, `fy26_ytd`, `fy25_actual`, `fy24_actual`, `page`, `adopted_page`, and `verification`.

A future version can add a guided CSV/PDF normalization workflow for additional Jack County taxing entities.

## Audit trail

The repository preserves the human-reviewed exception data under the `audit/` folder so corrections can be traced back to the source-review process.

SkewTheFuture.com: Complex public decisions explained.
