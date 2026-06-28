

## Business Problem Summary

The retail leadership team needed an executive dashboard to monitor
sales performance, profitability, customer segments, category performance,
shipping efficiency, discount impact, and return patterns across 2024-2025.

The dashboard answers one core business question:
**Where is the business making money, where is it losing money,
and what should leadership do about it?**

---

## Dataset Description

**File:** `data/dashboard_sales_data.xlsx`
**Rows:** 4,200 orders
**Date Range:** January 2024 – December 2025
**Source:** Retail transaction data for an Indian retail business

### Field Summary

| Field | Type | Description |
|---|---|---|
| order_id | String/Dimension | Unique order identifier |
| order_date | Date | Date order was placed |
| ship_date | Date | Date order was shipped |
| customer_id | String/Dimension | Unique customer identifier |
| customer_segment | String/Dimension | Consumer, Corporate, Home Office |
| region | String/Dimension | North, South, East, West |
| state | String/Dimension | Indian state |
| city | String/Dimension | City within state |
| category | String/Dimension | Furniture, Office Supplies, Technology |
| sub_category | String/Dimension | 10 product sub-categories |
| product_name | String/Dimension | Individual product name |
| ship_mode | String/Dimension | Same Day, First, Second, Standard Class |
| sales | Float/Measure | Revenue in ₹ |
| quantity | Integer/Measure | Units ordered |
| discount | Float/Measure | Discount proportion (0.20 = 20%) |
| profit | Float/Measure | Profit in ₹ (can be negative) |
| return_flag | Binary/Dimension | 0 = kept, 1 = returned |
| delivery_days | Integer/Measure | Days from order to delivery |
| customer_rating | Float/Measure | Rating on 1-5 scale |
| campaign_channel | String/Dimension | Organic, Paid, Email, Social, Referral |

---

## Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`
**Tool:** Tableau Public Desktop Edition 2025.3.2

### Sheets in Workbook

| Sheet Name | Chart Type | Purpose |
|---|---|---|
| Sales Trend | Dual line chart | Monthly sales 2024 vs 2025 |
| Regional Performance | Bar + dual axis line | Sales and margin by region |
| Category Performance | Horizontal bar | Sub-category profitability |
| Discount Impact | Bar chart | Discount band vs profit margin |
| Shipping Performance | Stacked bar | Order counts by ship mode and delay |
| Customer Segment | Side-by-side bar | Sales and profit by segment |
| Return Analysis | Bar chart | Return rate by category and segment |
| KPI Sales | Text/number | Total Sales KPI card |
| KPI Profit | Text/number | Total Profit KPI card |
| KPI Profit_margin | Text/number | Profit Margin % KPI card |
| KPI Return | Text/number | Return Rate % KPI card |
| Dashboard 1 | Dashboard | Full executive dashboard |

---

## Calculated Fields Created

| Field Name | Formula | Type |
|---|---|---|
| Profit Margin | SUM([Profit]) / SUM([Sales]) | Measure (%) |
| Cost | [Sales] - [Profit] | Measure (₹) |
| Average Order Value | SUM([Sales]) / COUNTD([Order Id]) | Measure (₹) |
| Return Rate | SUM([Return Flag]) / COUNT([Order Id]) | Measure (%) |
| Shipping Delay Bucket | IF/ELSEIF on [Delivery Days] | Dimension (text) |
| Discount Band | IF/ELSEIF on [Discount] | Dimension (text) |

---

## Dashboard and Filters

### Interactive Filters
- **Region:** Filter all charts by North, South, East, or West
- **Category:** Filter by Furniture, Office Supplies, or Technology
- **Customer Segment:** Filter by Consumer, Corporate, or Home Office

### Filter Actions
Cross-dashboard filter actions are configured so clicking any data point
(region bar, category bar, ship mode bar) filters all other charts
simultaneously. Click blank space to reset all filters.

---

## Key Business Insights

1. Sales grew 4.3% YoY (₹10.62 Cr in 2024 → ₹11.07 Cr in 2025)
2. Technology drives 84% of profit at 18.2% margin
3. Furniture destroys value — only 6.9% margin, all sub-categories red
4. Discounts above 30% generate -4.95% margin (loss-making orders)
5. Standard Class shipping: 47% of orders delivered slowly (5-6 days)
6. All 3 customer segments perform equally — no segment intervention needed
7. Furniture East return rate: 9.77% — more than double the 4.55% average
8. Organic channel drives 40% of all orders
9. Mid-year revenue dip (June-August) is a recurring seasonal pattern
10. Copiers is the single most profitable sub-category (₹73.10 Lakh profit)

---

## Dashboard Story Summary

The dashboard tells one coherent story:
**Technology is the profit engine. Furniture is the problem.
Heavy discounts explain why. Fix discounts and Furniture, and
the business significantly improves overall profitability.**

Full story: `outputs/dashboard_story.md`

---

## Assumptions and Limitations

1. `order_date` and `ship_date` auto-detected as Date type by Tableau
2. `return_flag` converted from Measure to Dimension (binary 0/1)
3. `discount` is a proportion — 0.20 means 20% (not 20)
4. `profit` can be negative — represents loss-making orders
5. `campaign_channel` has some null values — excluded from channel analysis
6. Geographic fields represent Indian locations (state, city)
7. `delivery_days` = 0 for Same Day orders — valid, not missing data
8. `customer_rating` is on a 1–5 scale (dataset average: 4.06)
9. Data covers only 2024-2025 — no historical baseline before 2024
10. No customer-level aggregation — CLV and repeat rates not calculable

---

## Screenshots Included

| File | Contents |
|---|---|
| screenshots/full_dashboard.png | Complete executive dashboard |
| screenshots/sales_trend_view.png | Sales trend line chart |
| screenshots/regional_performance_view.png | Regional bar chart |
| screenshots/category_profitability_view.png | Category profitability chart |
| screenshots/filter_interaction_view.png | Dashboard with filter applied |
