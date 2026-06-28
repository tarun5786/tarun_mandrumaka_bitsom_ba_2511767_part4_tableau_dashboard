# Chart Selection Justification

## Design Philosophy

Every chart in this dashboard was chosen to answer a specific business
question as clearly as possible. Charts were not added for decoration —
each one serves a distinct analytical purpose for the retail leadership team.

The overarching design principles applied throughout:
- Red/green diverging color scale used consistently (green = good, red = bad)
- All monetary values formatted in ₹ with M suffix for readability
- Percentages shown with 2 decimal places for precision
- Charts sorted by value (descending) unless time-series order matters
- Minimal clutter legends floated, axes cleaned, gridlines reduced

---

## Chart 1: Sales Trend - Dual Line Chart

**Business Question:** How are sales changing over time?

**Chart Type Chosen:** Line chart (dual lines — 2024 vs 2025)

**Why this chart:**
A line chart is the standard choice for showing change over a continuous
time dimension. It makes trends, peaks, and dips immediately visible.
Showing 2024 and 2025 as two separate colored lines enables direct
year-over-year comparison on the same axis — a bar chart would have
made this comparison harder to follow across 24 months.

**Design decisions:**
- X-axis: Month granularity (not year or quarter) to show seasonal patterns
- Y-axis: SUM(Sales) in ₹M
- Color: Year (2024=blue, 2025=orange) distinct, colorblind-safe pair
- Labels: Monthly values shown on each data point for precision
- No dual axis keeps the view clean and unambiguous

**Alternatives considered:**
- Bar chart: Rejected - harder to show trend direction across 24 months
- Area chart: Rejected - overlapping areas would confuse 2024 vs 2025

---

## Chart 2: Regional Performance - Bar Chart with Dual Axis

**Business Question:** Which region performs best in sales and profit?

**Chart Type Chosen:** Vertical bar chart with profit margin line overlay

**Why this chart:**
A bar chart is ideal for comparing discrete categories (4 regions).
The height of each bar immediately communicates relative sales size.
Adding profit margin as a dual-axis line overlay allows two different
metrics (₹ sales and % margin) to be shown together without confusion.
Color encoding bars by profit value adds a third dimension of information.

**Design decisions:**
- Sorted descending by sales (South → North → West → East)
- Bars colored by profit (green gradient - darker = more profit)
- Profit margin line in contrasting color for visibility
- Labels on each bar showing exact ₹ values

**Alternatives considered:**
- Map chart: Considered but rejected - India map in Tableau requires
  geocoding configuration; bar chart communicates the same information
  more reliably and clearly
- Highlight table: Rejected - less intuitive for magnitude comparison

---

## Chart 3: Category & Sub-Category Profitability — Horizontal Bar Chart

**Business Question:** Which categories and sub-categories drive profit or losses?

**Chart Type Chosen:** Horizontal bar chart with red-green diverging color

**Why this chart:**
Horizontal bars work better than vertical bars when category labels are
long (sub-category names like "Furnishings", "Accessories"). The bars
are easy to compare in length. The red-green diverging color on profit
margin immediately signals which sub-categories are profitable (green)
and which are loss-making (red) — no numbers needed to understand the story.

Nesting sub-categories under categories creates a natural hierarchy that
shows both the category-level and sub-category-level picture simultaneously.

**Design decisions:**
- Sorted by sales within each category (descending)
- Red-Green diverging color centered at 0% margin
- Profit labels on each bar for exact figures
- Horizontal layout to accommodate long sub-category names

**Alternatives considered:**
- Treemap: Considered — good for showing proportional size, but less
  effective at showing negative values (losses) clearly
- Stacked bar: Rejected — harder to compare individual sub-categories

---

## Chart 4: Discount Impact on Profit Margin - Bar Chart

**Business Question:** How does discount level relate to profit margin?

**Chart Type Chosen:** Bar chart with red-green diverging color

**Why this chart:**
The discount data has 6 distinct fixed values (0%, 5%, 10%, 15%, 20%,
25%, 30%, 35%) which means a scatter plot would produce vertical columns
of stacked dots — not a meaningful visual pattern. A bar chart using
pre-defined discount bands (0%, 1-10%, 11-20%, 21-30%, >30%) groups
orders into meaningful business categories and shows the clear staircase
pattern of declining margins as discounts increase.

The red-green diverging color reinforces the message: the >30% bar
is dark red (loss-making) while 0% is dark green (highest margin).
A dashed reference line at 0% marks the break-even point clearly.

**Design decisions:**
- Discount bands as X-axis (ordered low to high)
- Profit margin % on Y-axis
- Red-green diverging color on bars
- Reference line at 0% labeled "Break Even"
- Labels on each bar showing exact margin %

**Alternatives considered:**
- Scatter plot: Tested but rejected — 4,200 dots stack in vertical
  columns at fixed discount values, making the pattern impossible to read
- Line chart: Rejected — discount bands are categories, not continuous

---

## Chart 5: Shipping Performance - Stacked Bar Chart

**Business Question:** Which shipping mode causes delivery delays?

**Chart Type Chosen:** Stacked bar chart colored by shipping delay bucket

**Why this chart:**
A stacked bar chart is ideal here because it shows two things simultaneously:
(1) the total order volume per ship mode (bar height), and (2) the
composition of delivery speeds within each mode (color segments).
This makes it immediately clear that Standard Class has the highest
volume AND the worst delivery performance — both insights in one visual.

The Shipping Delay Bucket calculated field categorizes delivery days
into meaningful business labels (Same Day, Fast, Standard, Slow, Very Slow)
rather than raw numbers, making the chart interpretable by non-technical
leadership.

**Design decisions:**
- X-axis: Ship Mode (sorted by speed: Same Day → Standard Class)
- Y-axis: Count of orders
- Color: Shipping delay bucket (green = fast, red = slow)
- Labels: Order count per segment

**Alternatives considered:**
- Heatmap: Considered but requires more explanation for executives
- Simple bar: Rejected — loses the delivery performance breakdown

---

## Chart 6: Customer Segment - Side-by-Side Bar Chart

**Business Question:** Which customer segment has higher sales and profit?

**Chart Type Chosen:** Side-by-side bar chart

**Why this chart:**
Side-by-side bars allow direct comparison of two metrics (Sales and Profit)
across three segments simultaneously. Placing Sales and Profit bars next
to each other for each segment makes the profit-to-sales ratio visually
intuitive without requiring calculation. The color gradient shows
profit margin differences across segments at a glance.

**Design decisions:**
- Grouped by Customer Segment (Consumer, Corporate, Home Office)
- Side-by-side bars for Profit and Sales
- Color by profit margin (lighter = lower margin)
- Labels on all bars for exact values

**Alternatives considered:**
- Pie chart: Rejected - poor for comparing two metrics simultaneously
- Scatter plot: Rejected - only 3 data points, overkill for this view

---

## Chart 7: Return Analysis - Bar Chart by Category and Segment

**Business Question:** Which segment or category has higher return risk?

**Chart Type Chosen:** Bar chart grouped by Category and Region

**Why this chart:**
A grouped bar chart reveals both dimensions of return risk simultaneously —
which category has high returns AND which segments are affected. The
red-green diverging color on return rate % makes high-risk combinations
(red bars) immediately visible. This is more informative than a simple
category-level bar because it shows whether the return problem is
concentrated in specific regions or widespread.

**Design decisions:**
- X-axis: Category × Segment grouping
- Y-axis: Return rate %
- Red-green diverging color (red = high returns = bad)
- Labels showing exact return rate % on each bar

**Alternatives considered:**
- Heat map: Considered — good for this use case but less intuitive
  for executives unfamiliar with Tableau
- Highlight table: Rejected — numbers alone less impactful than bars

---

## KPI Cards — Text Mark (Big Number)

**Business Question:** What are the headline metrics at a glance?

**Chart Type Chosen:** Single number text display (no axes, no chart)

**Why this approach:**
KPI cards serve a different purpose from analytical charts — they give
executives an instant snapshot of the most important numbers without
requiring any interpretation. Four KPIs were chosen:

| KPI | Value | Why Important |
|---|---|---|
| Total Sales | ₹217.02M | Overall business size |
| Total Profit | ₹33.31M | Absolute profit generated |
| Profit Margin | 15.35% | Efficiency of sales |
| Return Rate | 4.55% | Customer satisfaction signal |

These four numbers answer "how is the business doing?" in under 5 seconds.
They also update dynamically when dashboard filters are applied — allowing
leadership to instantly see KPIs for any region, category, or segment.

---

## Filter Design

Three interactive filters were added to the dashboard:

| Filter | Type | Purpose |
|---|---|---|
| Region | Checkbox dropdown | Isolate geographic performance |
| Category | Checkbox dropdown | Focus on one product category |
| Customer Segment | Checkbox dropdown | Segment-level deep dive |

Cross-dashboard filter actions were also configured so clicking any
chart element (e.g. a region bar) automatically filters all other
charts - enabling drill-down without manual filter changes.

**Why these filters:**
These three dimensions represent the most common questions leadership
asks: "How is the South doing?", "How is Furniture performing?",
"How are Corporate customers behaving?" The filters answer all three.
