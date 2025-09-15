# Tableau Dashboard Spec — GLP-1 Market Access (FR, DE, UK)

This guide builds four Tableau views using the exported CSVs from the Colab notebook (`tableau_master_latest.csv`, `tableau_country_avg_price.csv`, `tableau_brand_avg_price.csv`).

## Common Fields
- **Dimensions:** `country`, `brand`, `year`, `status`
- **Measures:** `monthly_price_eur`, `access_score`, `monthly_gdp_pc`, `price_pct_of_monthly_gdp_pc`

## Calculated Fields
1. **Access Category (string)**
```
IF [access_score] = 2 THEN "Reimbursed"
ELSEIF [access_score] = 1 THEN "Conditional"
ELSE "Not reimbursed"
END
```
2. **Latest Year Filter (boolean)**
```
[year] = { FIXED : MAX([year]) }
```
3. **Affordability Label (string)**
```
STR(ROUND([price_pct_of_monthly_gdp_pc],1)) + "%"
```

---

## View 1 — Access Map
**Goal:** Country-level color by access score; tooltip shows status and brands.

- Data: `tableau_master_latest.csv`
- Filters: `Latest Year Filter` = TRUE; optional `brand` multi-select
- **Marks:** Map
  - Color: `access_score` (stepped 0–2); add color legend labels via **Access Category**
  - Detail: `country`
  - Tooltip: `country`, `brand`, `status`, `access_score`
- **Tip:** For only three countries, a symbol map also works (bubbles sized by `access_score`).

---

## View 2 — Price Comparison (Bars)
**Goal:** Compare monthly price by country for a selected brand.

- Data: `tableau_master_latest.csv`
- Filters: `Latest Year Filter` = TRUE; `brand` (single-select parameter recommended)
- **Columns:** `country`
- **Rows:** `monthly_price_eur`
- **Marks:** Bar
- **Tooltip:** `brand`, `country`, `monthly_price_eur`
- **Sort:** Descending by `monthly_price_eur`

---

## View 3 — Affordability Scatter
**Goal:** Relate affordability to income.

- Data: `tableau_master_latest.csv`
- Filters: `Latest Year Filter` = TRUE; `brand` (single-select)
- **Columns:** `monthly_gdp_pc`
- **Rows:** `price_pct_of_monthly_gdp_pc`
- **Marks:** Circle
  - Label: `country`
  - Tooltip: `country`, `brand`, `monthly_gdp_pc`, `price_pct_of_monthly_gdp_pc`
- Add trend line (optional).

---

## View 4 — Reimbursement Matrix (Heatmap)
**Goal:** Country × Brand access score matrix.

- Data: `tableau_master_latest.csv`
- Filters: `Latest Year Filter` = TRUE
- **Columns:** `brand`
- **Rows:** `country`
- **Marks:** Square
  - Color: `access_score` (0/1/2)
  - Label: `Access Category` (or the numeric score)
- **Tooltip:** `country`, `brand`, `status`

---

## Dashboard Layout
- **Top KPI Band** (Text Table):
  - # of brands analyzed, # countries, average access score, highest price (brand/country).
- **Two-column grid**:
  - Left: **Access Map** (or Matrix)
  - Right: **Price Comparison** (bars)
- **Bottom full-width**: **Affordability Scatter**
- **Global Filters**: `year` (default latest), `brand` (multi-select)

## Publishing
- Publish to **Tableau Public**.
- Add the link and screenshots to README.