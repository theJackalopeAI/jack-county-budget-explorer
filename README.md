# Jack County Budget Explorer

A public, searchable view of Jack County budget information prepared for SkewTheFuture.com.

## Purpose

The Budget Explorer is intended to make county budget records easier to search, compare and understand without changing the underlying public records.

The project is designed to help readers:

- search by department, precinct, account or keyword
- review budget line items on a phone or desktop
- compare fiscal years
- distinguish accounting reclassifications from actual changes in compensation or spending
- trace figures back to the county's source documents

## Current source set

The built-in Jack County dataset uses:

- FY2026-2027 proposed budget, Work Budget Version 0003, dated September 10, 2026
- FY2025-2026 adopted budget, adopted August 25, 2025

The September work budget is an image-only scan. The Explorer data was rebuilt from its OCR source lines using column-aware parsing and internal arithmetic checks. The FY2025-2026 adopted values were rebuilt from the text-readable adopted budget.

Rows that do not pass the parsing checks are marked **Needs source review** and the September numeric fields are withheld rather than guessed. The current build has 1,856 rows that passed the automated checks and 141 rows marked for source review.

## Employee compensation note

Some employee compensation that was previously shown as a separate stipend may be moved into the regular salary line. A higher salary line therefore does not necessarily represent an equivalent new raise or bonus.

Where the public records allow a reliable match, the Explorer should distinguish among:

- actual changes in employee compensation
- amounts reclassified from stipend to salary
- staffing or other payroll changes

The underlying figures and source records should be used to verify each individual case.

## Other entities and dataset schema

Version 2 can load another normalized Budget Explorer JSON dataset locally in the user's browser. The file is not uploaded to a server.

A normalized file can use this structure:

```json
{
  "meta": {
    "entity": "Example Taxing Entity",
    "title": "Example Budget Explorer",
    "current_document": "FY2026-2027 proposed budget",
    "comparison_document": "FY2025-2026 adopted budget",
    "schema_version": "2.0"
  },
  "records": []
}
```

Each record should include at least:

`fund_code`, `fund`, `department_code`, `department`, `type`, `account`, and `account_name`.

The Jack County build also uses fields such as `fy27_proposed`, `fy26_current`, `fy26_adopted`, `fy26_ytd`, `fy25_actual`, `fy24_actual`, `page`, `adopted_page`, `verification`, and `raw`.

A future version can add a guided CSV/PDF normalization workflow for additional Jack County taxing entities.

## Source and methodology

This repository is intended to preserve:

1. the interactive Budget Explorer
2. source budget documents or links to the official records
3. cleaned data used by the Explorer
4. notes describing transformations, corrections and updates

SkewTheFuture.com: Complex public decisions explained.
