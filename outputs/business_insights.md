# Business Insights

## Overview

This file documents at least 9 business insights derived from the
Executive Sales Dashboard, covering all required analysis areas:
sales trend, regional performance, category profitability, customer
segment behavior, discount impact, shipping delivery performance,
return patterns, and business risk or opportunity.

Each insight follows the format:
1. Observation from dashboard
2. Data evidence
3. Recommended action or follow-up question

---

## Calculated Fields Reference

| Field | Formula | Purpose |
|---|---|---|
| Profit Margin | SUM([Profit]) / SUM([Sales]) | % of revenue that becomes profit |
| Cost | [Sales] - [Profit] | Derived cost per transaction |
| Average Order Value | SUM([Sales]) / COUNTD([Order Id]) | Revenue per unique order |
| Return Rate | SUM([Return Flag]) / COUNT([Order Id]) | % of orders returned |
| Shipping Delay Bucket | IF/ELSEIF on Delivery Days | Categorizes delivery speed |
| Discount Band | IF/ELSEIF on Discount | Groups discount into business tiers |

---

## Insight 1: Sales Trend Mid-Year Dip is a Recurring Pattern

**Observation from dashboard:**
The Sales Trend line chart shows both 2024 and 2025 experience a sharp
revenue dip in the middle of the year before recovering strongly.

**Data evidence:**
- August 2024: ₹6.30M lowest month across both years
- June-July 2025: ₹7.19M and ₹7.26M weakest 2025 months
- February 2024: ₹10.49M strongest early 2024 month
- August-September 2025: ₹10.86M strongest 2025 month
- YoY growth: ₹10.62 Crore (2024) → ₹11.07 Crore (2025) = +4.3%

**Recommended action:**
Design targeted promotional campaigns for June-August to reduce
mid-year revenue dips. Investigate whether the dip is driven by
demand seasonality or supply/operational constraints.

---

## Insight 2: Regional Performance - South Leads but All Regions Are Equal

**Observation from dashboard:**
The Regional Performance bar chart shows South with the highest sales
but all four regions operate at nearly identical profit margins.

**Data evidence:**
- South: ₹64.69M sales, 15.5% margin (highest)
- North: ₹54.56M sales, 15.2% margin
- West: ₹48.91M sales, 15.1% margin
- East: ₹48.86M sales, 15.6% margin
- Margin range across all regions: only 0.5 percentage points

**Recommended action:**
Regional execution is not the problem. Leadership should not reallocate
resources between regions. Focus improvement efforts on company-wide
category and discount policy instead.

---

## Insight 3: Category Profitability Technology vs Furniture Gap is Critical

**Observation from dashboard:**
The Category Profitability chart shows all Technology sub-categories
in deep green and all Furniture sub-categories in deep red.

**Data evidence:**
- Technology margin: 18.2% on ₹15.39 Crore sales (₹28.04M profit)
- Furniture margin: 6.9% on ₹5.16 Crore sales (₹3.56M profit)
- Office Supplies margin: 14.9% on ₹1.15 Crore sales
- Copiers: ₹73.10 Lakh profit highest sub-category
- Furniture generates only 10.7% of total profit despite 23.8% of sales
- 288 orders (6.9%) have negative profit majority are Furniture

**Recommended action:**
Shift sales mix toward Technology. Review Furniture product portfolio
and consider discontinuing the lowest-margin sub-categories unless
strategic reasons justify their inclusion.

---

## Insight 4: Discount Impact — Heavy Discounts Destroy Profitability

**Observation from dashboard:**
The Discount Impact bar chart shows a clear staircase decline in profit
margin as discount percentage increases, turning negative above 30%.

**Data evidence:**
- 0% discount: 20.56% margin (1,024 orders)
- 1-10% discount: 17.01% margin (979 orders)
- 11-20% discount: 13.63% margin (1,047 orders)
- 21-30% discount: 8.05% margin (1,086 orders)
- More than 30% discount: -4.95% margin (64 orders)
- Total loss from negative-profit orders: ₹-5.74 Lakh

**Recommended action:**
Immediately cap discounts at 20% maximum. Require VP-level approval
for any discount above 15%. This single policy change would eliminate
all loss-making orders and lift overall margin by approximately 0.3%.

---

## Insight 5: Customer Segment All Segments Perform Equally

**Observation from dashboard:**
The Customer Segment side-by-side bar chart shows remarkably similar
sales and profit figures across all three segments.

**Data evidence:**
- Home Office: ₹74.50M sales, 15.5% margin, 1,446 orders
- Consumer: ₹71.89M sales, 15.3% margin, 1,355 orders
- Corporate: ₹70.63M sales, 15.2% margin, 1,399 orders
- Difference between highest and lowest segment: only ₹3.87M (5.5%)

**Recommended action:**
No segment intervention needed. Growth strategy should focus on
increasing order frequency and average order value across all segments
rather than shifting the segment mix. Consider loyalty programs to
increase repeat purchase rates in all three segments.

---

## Insight 6: Shipping Performance Standard Class Has a Delay Crisis

**Observation from dashboard:**
The Shipping Performance stacked bar chart reveals Standard Class —
the most-used mode — has the largest proportion of slow deliveries.

**Data evidence:**
- Standard Class: 2,435 orders (58% of all orders), ₹12.28 Crore
- Of those: 1,141 orders (47%) in "Slow (5-6 days)" bucket
- Only 201 Standard Class orders (8%) delivered in 1-2 days
- Same Day: 241 orders — 100% delivered on time (0 days)
- First Class: 630 orders — mostly Fast (1-2 days) delivery
- Average delivery days by mode:
  - Same Day: 0.4 days | First Class: 1.8 days
  - Second Class: 2.7 days | Standard Class: 4.7 days

**Recommended action:**
Audit Standard Class logistics partners and establish formal SLAs.
Communicate realistic delivery windows to customers at checkout.
For high-value orders above ₹50,000, auto-upgrade to First Class.

---

## Insight 7: Return Analysis - Furniture East is a Crisis

**Observation from dashboard:**
The Return Analysis chart shows Furniture in all regions has elevated
return rates, with East being the most severe at nearly 10%.

**Data evidence:**
- Overall company return rate: 4.55% (191 orders returned)
- Furniture East: 9.77% return rate — highest in the entire dataset
- Furniture North: 7.50% | Furniture South: 7.30% | Furniture West: 6.42%
- Technology returns: all regions between 2.84% and 4.15%
- Office Supplies returns: all regions between 2.72% and 4.23%
- Revenue at risk from returns: ₹87.62 Lakh in returned sales

**Recommended action:**
Conduct immediate product quality audit for all Furniture lines with
focus on East region distribution. Review product descriptions and
images for accuracy. Investigate whether delivery damage during transit
is contributing to returns. Set 5% return rate as KPI target for Furniture.

---

## Insight 8: Campaign Channel Organic is the Top Channel

**Observation from dashboard:**
Organic channel drives the most orders and sales of all campaign channels.

**Data evidence:**
- Organic: 1,694 orders (40.3%), ₹88.78M sales, ₹13.44M profit
- Paid: 849 orders (20.2%), ₹40.11M sales, ₹6.05M profit
- Email: 657 orders (15.6%), ₹34.51M sales, ₹5.36M profit
- Social: 584 orders (13.9%), ₹31.10M sales, ₹4.91M profit
- Referral: 392 orders (9.3%), ₹21.21M sales, ₹3.34M profit
- Null/untracked: 24 orders with no channel attribution

**Recommended action:**
Invest in SEO and content marketing to further grow the Organic channel.
Review Paid channel ROI it drives 20% of orders but requires budget
investment unlike Organic. Improve referral program to grow the
lowest-volume channel which has strong margin characteristics.

---

## Insight 9: Business Risk Furniture Is a Triple Threat

**Observation from dashboard:**
Combining insights from three charts reveals Furniture faces simultaneous
profitability, returns, and discount problems — making it the single
biggest risk to business health.

**Data evidence:**
- Furniture margin: 6.9% (vs 18.2% Technology)
- Furniture return rate: 6.4–9.8% across regions (vs 2.8–4.2% Technology)
- Furniture discount concentration: highest discount bands are dominated
  by Furniture orders, directly causing negative-profit orders
- Furniture generates ₹5.60 Lakh in losses from negative-profit orders
  (97% of all losses in the business)

**Recommended action:**
Convene a dedicated Furniture strategy review with leadership. Consider:
(1) Hard discount caps specifically for Furniture (max 15%)
(2) Product quality improvement program for high-return items
(3) Premium pricing repositioning to restore margins
(4) Discontinuation of consistently loss-making SKUs

---

## Insight 10: Business Opportunity - Average Order Value by Sub-Category

**Observation from dashboard:**
Technology sub-categories generate significantly higher average order
values than other categories, offering a high-leverage upsell opportunity.

**Data evidence:**
- Copiers: highest average order value in the dataset
- Accessories and Phones: second and third highest
- Machines: large individual order values
- Office Supplies: consistently low average order values
- Furniture: moderate order values but poor margin

**Recommended action:**
Train sales team to upsell Technology accessories with every Technology
hardware purchase. Bundle Accessories with Phones and Copiers. This
increases average order value in the highest-margin category simultaneously.
