# Assistant Buyer Dashboard — Project Specification

## 1. Project Overview

**Reference materials:**
- Inspiration dashboard/notebook: [Zara Sales Analysis (GitHub)](https://github.com/Mehdi-Benbiba/Zara-Sales-analysis/blob/main/Zara%20sales%20dashboard.pdf)
- Dataset: [Retail Fashion Boutique Data – Sales Analytics 2025 (Kaggle)](https://www.kaggle.com/datasets/pratyushpuri/retail-fashion-boutique-data-sales-analytics-2025)

**Purpose:**
Demonstrate how an assistant buyer could use retail sales, inventory, pricing, markdown, seasonality, and product data to make better buying and merchandising decisions.

**Objective:**
Help an assistant buyer quickly identify:
- Which fashion products are performing well
- Which products may need attention
- Where inventory/markdown decisions should be made

...using only the sales-related, stock, pricing, and product data actually available.

**Critical data constraint:** The dataset has Stock Quantity but **no direct units-sold / sales-volume field**. Nothing in this project should imply or fake sales volume.

---

## 2. Scope — Only 4 Things to Build

### 2.1 Executive Dashboard
- Total products
- Total inventory units
- Average price
- Average markdown
- Low-stock count

### 2.2 Product Performance Table
Columns:
- Product
- Category
- Brand
- Current price
- Stock quantity
- Markdown %
- Rating
- Buyer recommendation

### 2.3 Buyer Recommendations (Rule-Based Prototype)
Rules use **only the columns we actually have**. Explicitly a prototype, not Aritzia's actual buying methodology.

| Flag | Criteria |
|---|---|
| 🔥 **BUY / PRIORITIZE** | Low stock + Low/no markdown + Good rating |
| 👀 **MONITOR** | Moderate stock / moderate performance |
| 🛑 **HOLD / REVIEW** | High stock + High markdown + Poor rating and/or high returns |

### 2.4 Visualizations
As many as help buyer decision-making, focused on a **different story** than the Zara dashboard:
Inventory, product assortment, pricing, markdown, customer ratings, returns, seasonal inventory, buyer attention.

---

## 3. Top KPI Cards (5 required)

| # | KPI | Calculation |
|---|---|---|
| a | Total Inventory | Sum of Stock Quantity |
| b | Total Products | Count of unique Product IDs |
| c | Avg Current Price | Average of Current Price |
| d | Avg Markdown | Average of Markdown % |
| e | Return Rate | % of records with a Return Status indicating a return |

**Rule:** Format professionally. Do not make up numbers — everything calculated directly from the dataset.

---

## 4. Visualizations Spec

### Viz #1 — Inventory by Category (Required · Hero)
- **Type:** Horizontal bar chart
- **Title:** "Inventory by Category"
- **X-axis:** Total Stock Quantity
- **Y-axis:** Category
- **Business question:** "Where are we carrying the most inventory?"

### Viz #2 — Stock Quantity vs. Markdown % (Required · Hero)
- **Type:** Scatter plot
- **Title:** "Stock Quantity vs. Markdown %"
- **X-axis:** Markdown %
- **Y-axis:** Stock Quantity
- **Each point:** one product/record
- **Business question:** "Identify potential relationships between inventory levels and markdowns."
- **Interpretation quadrants:**
  - High stock + high markdown → potential overstock / review
  - High stock + low markdown → monitor inventory
  - Low stock + low markdown → potentially healthy product
  - Low stock + high markdown → investigate
- **Note:** This is the dashboard's core analytical story (vs. just displaying totals). Do not claim these are Aritzia's real buying rules — prototype only.

### Viz #3 — Inventory Distribution by Season (Required)
- **Type:** Donut chart
- **Title:** "Inventory Distribution by Season"
- **Data:** Total Stock Quantity by Season
- **Business question:** "Which seasons represent the largest share of our inventory?"

### Viz #4 — Average Markdown by Season (Required)
- **Type:** Bar chart
- **Title:** "Average Markdown by Season"
- **Data:** Average Markdown % per Season
- **Business question:** "Which seasons are relying most heavily on markdowns?"

### Viz #5 — Return Rate by Category (Required)
- **Type:** Bar chart
- **Title:** "Return Rate by Category"
- **Calculation:** Return Rate = Number of Returned Records / Total Records, grouped by Category
- **Business question:** "Are certain categories experiencing more returns?"
- **Note:** Do not infer *why* returns happen unless the dataset directly supports it.

### Viz #6 — Top 10 Products by Inventory (Required)
- **Type:** Table
- **Title:** "Top 10 Products by Inventory"
- **Columns:** Product Name/ID, Category, Brand, Stock Quantity, Current Price, Markdown %
- **Sort:** Descending by Stock Quantity
- **Note:** Replaces the "Top 10 Best Sellers" concept from the Zara dashboard — we have no sales volume data, so **never label these "best sellers."**

### Viz #7 — Price vs. Customer Rating (Optional)
- **Type:** Scatter plot
- **Title:** "Price vs. Customer Rating"
- **X-axis:** Current Price
- **Y-axis:** Customer Rating
- **Each point:** one product/record
- **Interpretation quadrants:**
  - High price + high rating → potential premium performer
  - Low price + high rating → potential value opportunity
  - High price + low rating → review
  - Low price + low rating → potentially weak product
- **Note:** Optional — do not sacrifice the core dashboard to build this.

---

## 5. Buyer Alerts / Recommendations Section

A small **"Buyer Attention"** panel. Rule-based, **not AI-generated**. Calculated directly from the dataset.

| Alert | Trigger | Recommendation Language |
|---|---|---|
| **Overstock Review** | Relatively high Stock Quantity AND relatively high Markdown % | "Review for potential overstock." |
| **Markdown Review** | Categories with high average Markdown % | "Review markdown strategy." |
| **Return Review** | Categories with high Return Rate | "Review product/return patterns." |
| **Low Inventory** | Products with relatively low Stock Quantity | "Monitor availability." |

**Language rule:** Never frame these as actual purchasing decisions. Use hedged language only: "Buyer Attention," "Review," "Monitor," "Potential Overstock."

---

## 6. Explicit Out-of-Scope (Do NOT Build)

For a 6-hour project scope, exclude:
- Machine learning
- Demand forecasting
- Supplier management
- Procurement / Purchase Orders
- SQL database
- Login system
- AI chatbot
- APIs
- Complex optimization
- Fake sales columns
- Fake supplier data

---

## 7. Guiding Principles

1. Calculate everything directly from the dataset — never fabricate numbers.
2. Never imply sales volume exists when only stock quantity does.
3. All buyer rules/recommendations are clearly labeled as a **prototype/decision-support tool**, not real retail methodology.
4. Return-related visuals describe *what* is happening, not *why*, unless the data supports a causal claim.
5. The Stock Quantity vs. Markdown % scatter plot is the analytical centerpiece — prioritize polish here.
