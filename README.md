# E-Commerce-purchase-Funnel-Analysis

Where do visitors leave an online store's purchase funnel, who leaves, and what could be changed? This project analyzes about 900,000 website sessions from the Google Merchandise Store (Aug 2016 to Aug 2017).

## Key findings
- 902,755 sessions, 11,535 purchases: overall conversion 1.28% (1.40% when counting unique users instead of sessions).
- The biggest loss is before the first product view: 86.26% of sessions (778,704) leave without opening a product page.
- Mobile converts at 0.41% against 1.58% on desktop. New visitors convert at 0.64% against 3.53% for returning visitors.
- Referral traffic is 29.01% of sessions but converts at 0.11% (YouTube sent 212,521 sessions and produced 11 purchases).
- Countries outside the US bring 59.63% of sessions but only 4.85% of purchases.

All findings are associations from observational data, not proven causes. The report lists three recommendations written as hypotheses, with the metric to track and a proposed A/B test.

## Tools
Google BigQuery, PostgreSQL (SQL: CTEs, window functions), Python (pandas, SQLAlchemy, Jupyter), Excel (interactive dashboard)

## Project contents
- `reports/` - full written report (PDF)
- `notebooks/` - analysis notebook
- `sql/` - BigQuery extraction and PostgreSQL scripts
- `excel/` - interactive dashboard (filters by device, visitor type, traffic medium and country)
- `images/` - dashboard screenshots

## How to reproduce
1. Run `sql/01_bigquery_extraction.sql` in BigQuery (free sandbox) and export the result as CSV. Replace YOUR_PROJECT_ID with your own Google Cloud project ID.
2. Create a PostgreSQL database and run `sql/02_postgres_setup_and_dedup.sql` to load the CSV and build the cleaned table.
3. Copy `.env.example` to `.env` and fill in your database details.
4. Install the libraries (`pip install -r requirements.txt`) and run the notebook.

## Data
Google Analytics sample dataset (Google Merchandise Store), a public dataset on BigQuery. The data file is not included because of its size.

## Limitations
2016-2017 data from one store; session-level (not person-level); stage counts ignore order; only five funnel stages; segments were not controlled for each other; no significance tests; no cost or margin data.

## Dashboard
![Dashboard](images/dashboard_default.png)
