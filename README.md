# HMRC Tax Gap Analysis

Excel analysis of HMRC's Measuring Tax Gaps 2026 data, comparing how the UK tax gap changed by tax type, with an introductory SQL learning exercise.

## Aim
To compare how the UK tax gap has changed by type of tax, using HMRC's official statistics.

## Data
HMRC, Measuring tax gaps 2026 edition (published 23 June 2026), Table 1.1: Percentage tax gap by type of tax.

## Tools
- Microsoft Excel: calculations, charts and presentation.
- SQLite via SQLite Online: an AI-assisted SQL learning exercise.

## Method
- Extracted the percentage tax gap for each tax type.
- Compared 2005–06 with 2024–25 and calculated the change in percentage points.
- Compared Corporation Tax from 2019–20, because HMRC notes a step change in that series that year, partly due to improved data collection.
- Built charts to show the changes.
- Extended the analysis with a guided SQL exercise to calculate percentage changes for four tax categories.

## Findings
- The overall tax gap fell from 7.5% to 6.4%.
- VAT had the biggest improvement among the categories compared between 2005–06 and 2024–25, falling from 14.1% to 6.6% (−7.5 percentage points).
- Excise duties fell from 8.3% to 5.5%.
- Income Tax, NICs and Capital Gains Tax changed little, falling from 4.5% to 4.0%.
- Corporation Tax moved the opposite way, rising from 15.6% (2019–20) to 18.1% (2024–25).

## SQL Extension: Introductory Learning Exercise

To extend my existing Excel analysis, I used an AI-assisted query in SQLite to calculate tax-gap percentage changes between 2005–06 and 2024–25.

AI guidance helped generate and explain the query. I ran it, compared the outputs with the expected results, checked the percentage-point differences against my spreadsheet calculations, and presented both measures together in Excel.

### SQL Query

The imported data used generic column names:
- `c1`: tax type
- `c2`: tax gap in 2005–06
- `c3`: tax gap in 2024–25

```sql
SELECT
    c1 AS tax_type,
    c2 AS gap_2005_06,
    c3 AS gap_2024_25,
    ROUND(
        (CAST(c3 AS REAL) - CAST(c2 AS REAL))
        / NULLIF(CAST(c2 AS REAL), 0) * 100,
        1
    ) AS percentage_change
FROM tax_gap
LIMIT 4 OFFSET 2;
```

### Results

| Tax type | 2005–06 tax gap (%) | 2024–25 tax gap (%) | Change (percentage points) | Percentage change (%) |
|---|---:|---:|---:|---:|
| Overall | 7.5 | 6.4 | −1.1 | −14.7 |
| VAT | 14.1 | 6.6 | −7.5 | −53.2 |
| Income Tax, NICs and Capital Gains Tax | 4.5 | 4.0 | −0.5 | −11.1 |
| Excise Duties | 8.3 | 5.5 | −2.8 | −33.7 |

### What I Learned
This guided exercise introduced me to selecting columns, naming output fields and performing calculations in SQL.

It also helped me distinguish between two measures:
- Percentage-point change: the later percentage minus the earlier percentage.
- Percentage change: the difference divided by the earlier value, multiplied by 100.

For example, the overall tax gap fell by 1.1 percentage points, equivalent to a 14.7% decrease relative to its 2005–06 level.

This was an introductory, AI-assisted exercise rather than an independently written SQL project. I am continuing to develop my understanding of SQL.

## Limitations
- The two most recent years are projections, and HMRC revises past estimates as more data becomes available.
- HMRC advises focusing on trends rather than exact figures.
- The Corporation Tax series is not directly comparable with years before 2019–20.
- The SQL exercise covers four selected categories rather than the full dataset.
- The SQL query uses row positions (`LIMIT 4 OFFSET 2`) to select the intended records in this imported table. For a more reusable analysis, the table should have meaningful column names and explicit filtering and ordering.

# HMRC Tax Gap Analysis

Excel analysis of HMRC's Measuring Tax Gaps 2026 data, comparing how the UK tax gap changed by tax type, with an introductory SQL learning exercise.

## Aim
To compare how the UK tax gap has changed by type of tax, using HMRC's official statistics.

## Data
HMRC, Measuring tax gaps 2026 edition (published 23 June 2026), Table 1.1: Percentage tax gap by type of tax.

## Tools
- Microsoft Excel: calculations, charts and presentation.
- SQLite via SQLite Online: an AI-assisted SQL learning exercise.

## Method
- Extracted the percentage tax gap for each tax type.
- Compared 2005–06 with 2024–25 and calculated the change in percentage points.
- Compared Corporation Tax from 2019–20, because HMRC notes a step change in that series that year, partly due to improved data collection.
- Built charts to show the changes.
- Extended the analysis with a guided SQL exercise to calculate percentage changes for four tax categories.

## Findings
- The overall tax gap fell from 7.5% to 6.4%.
- VAT had the biggest improvement among the categories compared between 2005–06 and 2024–25, falling from 14.1% to 6.6% (−7.5 percentage points).
- Excise duties fell from 8.3% to 5.5%.
- Income Tax, NICs and Capital Gains Tax changed little, falling from 4.5% to 4.0%.
- Corporation Tax moved the opposite way, rising from 15.6% (2019–20) to 18.1% (2024–25).

## SQL Extension: Introductory Learning Exercise

To extend my existing Excel analysis, I used an AI-assisted query in SQLite to calculate tax-gap percentage changes between 2005–06 and 2024–25.

AI guidance helped generate and explain the query. I ran it, compared the outputs with the expected results, checked the percentage-point differences against my spreadsheet calculations, and presented both measures together in Excel.

### SQL Query

The imported data used generic column names:
- `c1`: tax type
- `c2`: tax gap in 2005–06
- `c3`: tax gap in 2024–25

```sql
SELECT
    c1 AS tax_type,
    c2 AS gap_2005_06,
    c3 AS gap_2024_25,
    ROUND(
        (CAST(c3 AS REAL) - CAST(c2 AS REAL))
        / NULLIF(CAST(c2 AS REAL), 0) * 100,
        1
    ) AS percentage_change
FROM tax_gap
LIMIT 4 OFFSET 2;
```

### Results

| Tax type | 2005–06 tax gap (%) | 2024–25 tax gap (%) | Change (percentage points) | Percentage change (%) |
|---|---:|---:|---:|---:|
| Overall | 7.5 | 6.4 | −1.1 | −14.7 |
| VAT | 14.1 | 6.6 | −7.5 | −53.2 |
| Income Tax, NICs and Capital Gains Tax | 4.5 | 4.0 | −0.5 | −11.1 |
| Excise Duties | 8.3 | 5.5 | −2.8 | −33.7 |

### What I Learned
This guided exercise introduced me to selecting columns, naming output fields and performing calculations in SQL.

It also helped me distinguish between two measures:
- Percentage-point change: the later percentage minus the earlier percentage.
- Percentage change: the difference divided by the earlier value, multiplied by 100.

For example, the overall tax gap fell by 1.1 percentage points, equivalent to a 14.7% decrease relative to its 2005–06 level.

This was an introductory, AI-assisted exercise rather than an independently written SQL project. I am continuing to develop my understanding of SQL.

## Limitations
- The two most recent years are projections, and HMRC revises past estimates as more data becomes available.
- HMRC advises focusing on trends rather than exact figures.
- The Corporation Tax series is not directly comparable with years before 2019–20.
- The SQL exercise covers four selected categories rather than the full dataset.
- The SQL query uses row positions (`LIMIT 4 OFFSET 2`) to select the intended records in this imported table. For a more reusable analysis, the table should have meaningful column names and explicit filtering and ordering.

## Files
- `HMRC-tax-gap-analysis.xlsx`: original Excel analysis, data and charts.
- `tax type-tax gap.pdf`: formatted table comparing tax-gap values, percentage-point changes and SQL-calculated percentage changes.
- The SQL query and its results are also documented in this README.
