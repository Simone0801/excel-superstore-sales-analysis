# E-Commerce Commercial & Profitability Analysis (Superstore)
### Executive Excel & Power Query BI Dashboard for Retail Performance

---

## Project Overview
An end-to-end commercial analytics project built in Microsoft Excel and Power Query to analyze four years (2014–2017) of U.S. retail transaction data, comprising 9,994 transaction records across 5,009 distinct orders.

The primary business objective was to uncover margin leaks, evaluate discounting effectiveness, assess regional performance, and identify high-leverage growth opportunities for executive leadership.

---

## Dashboard Preview

| Multi-Year Performance Trend | Profitability by Subcategory |
| :---: | :---: |
| ![Multi-Year Performance](1_Yearly_Performance.png) | ![Profit by Subcategory](2_Profit_By_Subcategory.png) |

| Margin Destruction by Discount Band | Top 10 Profit States |
| :---: | :---: |
| ![Discount Margin](3_Profit_Margin_By_Discount.png) | ![Top States](4_Top_10_States_Profit.png) |

---

## Key Business Questions Addressed
1. **Profitability Health:** Which product categories and sub-categories are draining company profits, and by how much?
2. **Discount Sensitivity:** Does aggressive discounting drive profitable volume, or does it destroy profit margins?
3. **Geographic Performance:** Which regions and states generate high revenue but negative bottom-line returns?
4. **Segment Profitability:** Which customer segments (Consumer, Corporate, Home Office) deliver the highest return on sales?
5. **Time Series & Seasonality:** How consistent is year-over-year expansion, and how does margin hold during peak Q4 volume?
6. **Fulfillment Performance:** How do shipping modes relate to sales, profitability, and delivery times?

---

## Data Architecture & Technical Workflow

### 1. Extraction, Transformation & Loading (ETL) — Power Query (M)
* **Ingestion & Data Typing:** Handled decimal parsing, locale-independent date transformations, and standardized schemas.
* **Feature Engineering:**
  * `Profit Margin %`: Calculated as aggregated Profit divided by aggregated Sales, ensuring accurate weighted margin calculations across different analytical dimensions.
  * `Days to Ship`: Derived shipping duration `Duration.Days([Ship Date] - [Order Date])`.
  * `Profit Flag`: Conditional segmentation (`Profitable`, `Break-even`, `Loss`).
  * `Discount Band`: Categorized into `No Discount` (0%), `Low` (1–20%), `Mid` (21–40%), and `High` (>40%).
  * `Time Intelligence`: Extracted Year, Quarter, and standardized English Month names.

### 2. Analytical Backend — Pivot Tables & Data Modeling
* Single-source analytical backend built on the cleaned transaction dataset, supported by 11 PivotTables.
* Fully linked Slicers (`Region` and `Order Year`) driving synchronized cross-filtering.
* Single-level category hierarchies and subtotal management to prevent distorted trendlines.

### 3. Executive Dashboard Interface
* **5 Dynamic KPI Cards:** Total Sales, Total Profit, Profit Margin %, Order Count, and Average Order Value dynamically linked to active slicer filters.
* **Diverging Profit Bar Chart:** Subcategories sorted ascending to immediately spotlight loss-makers (Tables, Bookcases, Supplies).
* **Multi-Year Trend Analysis:** Clean annual progression tracking Sales vs. Profit.
* **Discount Band Margin Matrix:** Visual evidence of margin erosion across discount thresholds.
* **Segment & Regional Performance Charts:** Top 10 profit states and category-by-segment margin distributions.

---

## Core Business Findings & Data Insights

| Analysis Area | Key Metric | Business Finding |
| :--- | :--- | :--- |
| **Top-Line Growth** | **+51.4% Sales** | Revenue expanded from \$484k (2014) to \$733k (2017). |
| **Bottom-Line Growth** | **+88.6% Profit** | Net profit surged from \$49.5k to \$93.4k (Profitability Improvement: Profit margin increased from 10.2% in 2014 to 12.7% in 2017, indicating an improvement in overall sales profitability.). |
| **Q4 Sales Contribution** | **38.2%** | Q4 generated $878k in sales and $110.6k in profit across the four-year period, with an aggregated profit margin of 12.6%.  |
| **Discount Impact** | **-$135,376 Profit** | Transactions with discounts above 20% generated an aggregated loss of $135,376, corresponding to a weighted profit margin of -37.3%. The Mid (21–40%) and High (>40%) discount bands recorded margins of -15.3% and -77.4%, respectively. | 
| **Product Leaks** | **-$22,387 Drag** | Tables (-$17.7k), Bookcases (-$3.5k), and Supplies (-$1.2k) are operating at a net loss. |
| **Regional Profitability Risks** | **Texas & Ohio** | Texas recorded a loss of $25.7k (-15.1% margin), while Ohio recorded a loss of $17.0k (-21.7% margin). These states represent priority areas for further investigation into discounting and product profitability. |
| **Powerhouse States** | **California & NY** | California (\$76.4k profit) and New York (\$74.0k profit) drive over 52% of total company profit. |

---

## Strategic Executive Recommendations

1. **Implement Discount Governance Guardrails:**
   * Cap discretionary sales discounts at a maximum of **20%**.
   * Require Regional VP approval for any discount between 21%–40%, and prohibit discounts >40% outside of clearance liquidation. 
   * Conduct controlled discount policy experiments to evaluate the potential profitability impact of reducing discounts above 20%, while monitoring sales volume and customer retention.
2. **Review Furniture Portfolio Profitability:**
   * Investigate the underlying drivers of negative profitability in Tables and Bookcases.
   * Evaluate pricing strategies, discount policies, and product-level performance before considering portfolio restructuring.
   * Conduct a regional breakdown to identify where these products generate the largest losses.
3. **Introduce Profitability-Based Sales Performance Monitoring:**
   * Complement revenue-based performance tracking with profitability KPIs.
   * Monitor low-margin and loss-making orders to identify potential improvements in discount management and commercial decision-making.
4. **Prioritize High-Margin Product Categories:**
   * Evaluate growth opportunities in Technology, which records an overall profit margin of 17.4%.
   * Investigate Office Supplies within the Home Office segment, which achieves a 20.84% profit margin.
   * Assess customer acquisition costs and incremental profitability before reallocating marketing resources.

---

## How to Explore & Run
1. **Clone or Download the Repository:**
   ```bash
   git clone https://github.com/Simone0801/excel-superstore-sales-analysis.git
   cd excel-superstore-sales-analysis
   ```
2. **Interact with the Dashboard:**
   * Open `Data Analysis project - Superstore.xlsx` in Microsoft Excel.
   * Toggle dynamic slicers (`Region`, `Order Year`) to filter KPI cards and charts in real time.
   * View the standalone executive PDF presentation at `Dashboard_Presentation.pdf`.

---

## Repository Contents
* `Data Analysis project - Superstore.xlsx` — Fully interactive Excel workbook with Power Query ETL, PivotTables, and Dashboard.
* `Dashboard_Presentation.pdf` — Executive presentation PDF formatted for instant one-page landscape review.
* `1_Yearly_Performance.png` — Multi-year trend chart (Sales vs. Profit dual axis).
* `2_Profit_By_Subcategory.png` — Diverging profit chart highlighting loss-makers vs. growth drivers.
* `3_Profit_Margin_By_Discount.png` — Profit Margin by Discount Band Chart.
* `4_Top_10_States_Profit.png` — Geographic profit leader rankings.
* `5_Profit_Margin_By_Segment.png` — Category margin distribution across customer segments.
* `Sample - Superstore.csv` — Raw dataset (9,994 records).
* `README.md` — Project documentation and executive summary.

