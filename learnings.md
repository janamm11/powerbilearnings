# 📊 Power BI Learning Journey

This repo documents everything I learned while studying Power BI —
from building charts to writing DAX formulas and cleaning data in Power Query.
Written in simple words so I can come back and revise quickly. (my notebook file note was refined by LLM for better understsanding)

---

## 📁 What is Inside

| Topic | What I Learned |
|---|---|
| Visuals | Line chart, Scatter plot, Funnel, Globe, Table |
| Power Query | Data cleaning, profiling, merging, pivot/unpivot |
| DAX | Formulas, measures, filters, time intelligence |

---

# 📊 Part 1 — Power BI Visuals

A quick reference for every chart I practiced — what it is, when to use it, and what story it tells.

---

## 1. Bar Chart
**What I did:** Sum of Sales by City

- Shows one value across many categories
- Horizontal bars make it easy to read long category names like city names
- Automatically ranks from highest to lowest — New York City had the highest sales at 256K
- **Use when:** Comparing a single metric across many items (cities, products, regions)

---

## 2. Pie and Donut Chart
**What I did:** Sales by Segment (Consumer, Corporate, Home Office)

- Both show part-to-whole relationship — how much each piece contributes to total
- Pie is fully filled, Donut has a hole in the middle (you can put a number inside)
- Shows percentage automatically — Consumer was 50.56%, Corporate 30.74%, Home Office 18.7%
- **Use when:** You have 3–5 categories and want to show proportion of a total
- **Avoid when:** Too many categories — slices get too small to read

---

## 3. Clustered Column Chart
**What I did:** Sales by Category and Segment

- Groups bars side by side for easy comparison within a category
- I compared Consumer, Corporate and Home Office sales within each Category (Technology, Furniture, Office Supplies)
- **Use when:** You want to compare two dimensions together — like category AND segment at the same time

---

## 4. Line Chart
**What I did:** Profit by Ship Mode

- Shows values as points connected by a line
- Good for seeing which item is highest or lowest at a glance
- **Use when:** Comparing a metric across categories where order or trend matters — like ship modes ranked by profit

---

## 5. Line and Stacked Column Chart
**What I did:** Sales and Profit by Year and Segment

- Combines two chart types in one visual
- Stacked columns show Sales broken by Segment (Consumer, Corporate, Home Office)
- Line on top shows Profit trend over years
- Has **drill down arrows** — you can go from Year → Quarter → Month → Day
- **Use when:** You want to show two different metrics together over time — one as volume (columns) and one as trend (line)

---

## 6. Line and Clustered Column Chart
**What I did:** Sales and Quantity by Year and Category

- Similar to above but columns are clustered (side by side) instead of stacked
- Columns show Sales by Category per year, Line shows Quantity trend
- **Use when:** You want to compare categories side by side AND show a second metric as a trend — good when categories should not be stacked

---

## 7. Scatter Plot with Play Axis
**What I did:** Sum of Sales vs Sum of Profit by Order Date

- Each dot represents one data point — plots two large numbers against each other (X and Y axis)
- **Play Axis** — drag a date column here and press Play
  - The dots animate automatically over time showing how Sales and Profit moved together date by date
- **Use when:** Comparing two numerical columns to see if they move together, and you want to show change over time through animation

---

## 8. Map Visual
**What I did:** Sales by City across the US

- Plots data on a real world map using city or country names
- Bubble size = value (bigger bubble = more sales)
- Most sales were concentrated in US cities — visible instantly on the map
- **Use when:** Your data has geographic information like city, state, or country and you want to show where values are highest

---

## 9. Table and Matrix

**Table**
- Shows raw data row by row — Country, City, Sum of Sales, Sum of Profit, Region
- Good for exact numbers when you need to see details
- **Use when:** Audience needs precise values not just visual trends

**Matrix**
- Like a pivot table — rows and columns both carry dimensions
- I had Region across columns and City down rows, showing Sales and Profit for each combination
- Supports expand/collapse to drill into sub-levels
- **Use when:** You need to compare two dimensions against each other in a grid format

---

## 10. Funnel Chart
**What I did:** Number of customers at different stages — Prospects → Leads → Interested → Converted

- Each stage must be smaller than the one before — shows drop off at each step
- 100 Prospects → 80 Leads (80%) → 20 Interested (20%) → 10 Converted (10%)
- **Use when:** You have sequential stages like a sales pipeline, hiring process, or customer journey

---

## 11. Gauge Chart
**What I did:** Profit with Min, Max and Target values

- Shows a single value on a dial — like a speedometer
- Displays current value (286K profit), with a minimum, maximum and target range
- Instantly shows whether you are below or above target
- **Use when:** You want to show progress toward a single goal or target — KPI tracking

---

## 12. KPI Card
**What I did:** Profit vs Target by Month — December showed 43.37K against a target of 20K (+116.85%)

- Shows one metric, its target, and the % difference in a clean card format
- Green/red color tells you instantly if target was met or missed
- **Use when:** You want to highlight one important metric and how it compares to a goal

---

## 13. Key Influencers
**What I did:** What influences Profit to decrease?

- Automatically analyzes your data and tells you which columns most affect a target metric
- Found that when Discount = 1, Profit decreases by 129.2 on average
- Two tabs — Key Influencers (what drives it) and Top Segments (which groups are affected)
- **Use when:** You want Power BI to automatically find what is causing a metric to go up or down — no manual analysis needed

---

## 14. Decomposition Tree
**What I did:** Breaking down Sum of Profit (286K) → by Category → by Sub-Category

- Starts with a total value and lets you drill down to find where it comes from
- Technology (145K) → Copiers (55K) was the top contributor
- Furniture had the lowest profit (18K)
- **Use when:** You want to explore what is driving a number by breaking it down level by level

---

## 15. Q&A Visual
**What I did:** Typed "which is the category with minimum profit" — it answered Furniture

- You type a question in plain English and Power BI finds the answer from your data
- Good for quick ad-hoc questions without building a new visual
- **Note:** This feature is retiring in December 2026

---

## 🗂️ Quick Reference

| Chart | Best Used For |
|---|---|
| Bar Chart | Compare one metric across many categories |
| Pie / Donut | Part of whole — proportions (max 5 categories) |
| Clustered Column | Compare two dimensions side by side |
| Line Chart | Trend or ranking across categories |
| Line + Stacked Column | Two metrics over time — volume + trend |
| Line + Clustered Column | Two metrics over time — compare categories + trend |
| Scatter + Play Axis | Two numbers vs each other, animated over time |
| Map | Geographic distribution of values |
| Table | Exact raw numbers |
| Matrix | Two dimensions in a grid — like pivot table |
| Funnel | Sequential stages with drop off |
| Gauge | Progress toward a single target |
| KPI Card | One metric vs its goal |
| Key Influencers | What is causing a metric to change |
| Decomposition Tree | Break a total down level by level |
| Q&A | Ask questions in plain English |

## 🔧 Part 2 — Power Query (Data Cleaning)

Power Query is where you **clean and shape your data** before building visuals.
Open it via: `Home → Transform Data`

### Why Use It
- Fix messy data so visuals work correctly
- Structure tables the way Power BI expects

---

### Data Profiling
Go to `View` tab inside Power Query to turn these on:

| Feature | What it Shows |
|---|---|
| Column Distribution | How values are spread across the column |
| Column Quality | Valid %, Error %, Empty % for each column |
| Column Profile | Min, Max, Count, Avg + which value appears how many times |

> **Important:** Distinct vs Unique are NOT the same thing!
> - **Distinct** = all different values including blank
> - **Unique** = values that appear only once
> - For a column to be a **Primary Key** → Distinct count must equal Unique count AND have no nulls

---

### Combining Tables

**Append** = stack tables on top of each other (like adding more rows)
```
File → Append Queries → Append Queries as New
(use "as New" if you don't want to change your original table)
```

**Merge** = join tables like SQL joins
```
File → Merge Queries
```

| Join Type | What it Does |
|---|---|
| Inner Join | Only matching rows from both tables |
| Left Outer | All left rows + matching right rows |
| Right Outer | All right rows + matching left rows |
| Left Anti | Left rows that have NO match in right (A - B) |
| Right Anti | Right rows that have NO match in left (B - A) |
| Full Outer | All rows from both tables |

---

### Group By
Summarize data by a column — like `GROUP BY` in SQL.
Example: Total sales per region, count of orders per customer.

---

### Pivot, Unpivot and Transpose

| Operation | What it Does | Where |
|---|---|---|
| Transpose | Rows become columns, columns become rows | Transform tab |
| Pivot | Spreads one column's values into multiple columns, handles duplicates by aggregating | Transform tab |
| Unpivot | Opposite of pivot — collapses multiple columns into rows | Transform tab |

**Pivot example:**

Before:
| Name | Product | Sales |
|---|---|---|
| Ram | Apple | 10 |
| Ram | Apple | 2 |
| Ram | Banana | 5 |

After pivot on Product, sum of Sales:
| Name | Apple | Banana |
|---|---|---|
| Ram | 12 | 5 |

---

### Split Column by Delimiter
- `Add Column → Split Column → By Delimiter`
- Example: `/jan,roll,man/` → splits into `jan`, `roll`, `man` in separate columns
- Use **Transform Column** to remove unwanted characters or signals from data

---

## 🧮 Part 3 — DAX (Data Analysis Expressions)

DAX is the formula language of Power BI. You use it to create **calculated columns and measures.**

---

### Creating a Date Table
`Modeling → New Table`

```dax
Date column = CALENDAR(DATE(2024,01,01), DATE(2025,01,01))

month number     = MONTH('Date column'[Date].[Date])
weekday          = WEEKDAY('Date column'[Date].[Date], 1)
month short name = FORMAT('Date column'[Date].[Date], "MMM")
```

---

### Text Functions

| Function | What it Does | Example |
|---|---|---|
| CONCATENATE | Joins two columns | `CONCATENATE(col1, col2)` |
| LEFT | Extract characters from left | `LEFT([column], 3)` → first 3 letters |
| RIGHT | Extract characters from right | `RIGHT([column], 3)` → last 3 letters |
| MID | Extract from any position | `MID([column], 1, 4)` → 4 letters from position 1 |
| LEN | Count characters in a value | `LEN([column])` |

**Adding a separator in CONCATENATE:**
```dax
-- adds "-" between two values
con2fun = CONCATENATE(CONCATENATE([month short name], "-"), [Weekshortname])
```

---

### Aggregation Functions

| Normal (whole column) | Iterative (row by row first) |
|---|---|
| SUM | SUMX |
| MIN | MINX |
| MAX | MAXX |
| AVERAGE | AVERAGEX |
| COUNT | COUNTX |

> **Key difference:**
> - `SUM` → adds up all values in a column directly
> - `SUMX` → goes row by row, calculates something, then adds it all up
> - Use SUMX when you need to **do math per row first** (like doubling each value before summing)

```dax
-- Sum of len func column only for December rows
sumx fun = SUMX(
  FILTER('Date column', 'Date column'[month short name] = "DEC"),
  'Date column'[len func]
)
```

---

### CALCULATE — The Most Important DAX Function

`CALCULATE(expression, filter)` — it **overrides the current filter context**

Think of it like this:
```
Normal:    "Give me total sales"           → uses whatever filter is active
CALCULATE: "Give me total sales, but only for DEC" → forces its own filter
```

```dax
-- Sum of month numbers but only for December
calculate func = CALCULATE(
  SUM('calculated table'[month number]),
  'Date column'[month short name] = "DEC"
)
```

---

### ALL, ALLEXCEPT, ALLSELECTED

| Function | What it Does |
|---|---|
| ALL | Removes ALL filters from a table or column |
| ALLEXCEPT | Removes all filters EXCEPT the ones you specify |
| ALLSELECTED | Keeps only the filters the user selected in slicers |

```dax
-- Each month's share of total (removes date filter for denominator)
Divide fun = DIVIDE(
  SUM('Date column'[month number]),
  CALCULATE(SUM('Date column'[month number]), ALL('Date column'))
)
```

---

### Logical Functions

| Function | What it Does |
|---|---|
| AND(a, b) | True only if BOTH conditions are true |
| OR(a, b) | True if at least ONE condition is true |
| NOT(condition) | Flips true to false and false to true |
| SWITCH(TRUE(), condition, result, ...) | Like a CASE WHEN in SQL |

```dax
-- Returns cost price if > 0, otherwise returns sales price
switch fun = SWITCH(
  TRUE(),
  SUM(Example[cost price]) > 0, SUM(Example[cost price]),
  SUM(Example[sales price])
)
```

---

### Date & Time Functions

```dax
-- Difference between two dates
Datediff fun = DATEDIFF(DATE(2026,01,01), DATE(2025,01,01), YEAR)
```

---

### Time Intelligence Functions

These help you calculate **running totals over time periods.**

| Function | What it Means |
|---|---|
| TOTALQTD | Total from start of current Quarter to today |
| TOTALMTD | Total from start of current Month to today |
| TOTALYTD | Total from start of current Year to today |
| SAMEPERIODLASTYEAR | Same date range but from last year |

```dax
total QTD = TOTALQTD(SUM('calender table'[profit]), 'calender table'[Date].[Date])
total MTD = TOTALMTD(SUM('calender table'[profit]), 'calender table'[Date].[Date])
total YTD = TOTALYTD(SUM('calender table'[profit]), 'calender table'[Date].[Date])

-- Compare this year vs last year
same period last year = CALCULATE(
  SUM('calender table'[profit]),
  SAMEPERIODLASTYEAR('calender table'[date].[date])
)
```

---

### Creating a Separate Measures Table
Keeping all measures in one clean table is good practice.

```
Home → Enter Data → Name it "Measures" → Load
Then move measures: select measure → Home → choose destination table
```

---

## 💡 Quick Revision Cheatsheet

```
Drill down chart   → explore Year > Month > Day
Play axis          → animate scatter plot over time
Funnel             → stage by stage drop off
Power Query        → clean before you visualize
Distinct ≠ Unique  → blank counts as distinct
Append             → add rows
Merge              → join tables (like SQL)
SUM vs SUMX        → column total vs row by row then total
CALCULATE          → override filter context
ALL                → remove all filters
TOTALYTD/MTD/QTD   → running totals by time period
SAMEPERIODLASTYEAR → year over year comparison
```

---

*Learning Power BI hands-on. More projects and notes coming soon.*


used llm to refine my notebook file--

