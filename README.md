# 📊 Global Sales Performance Dashboard | Power BI

An interactive **Power BI** dashboard analyzing **5,000,000+ sales transactions** across global regions, product categories, and sales channels. The project turns a large-scale, cleaned transactional dataset into a clear story about **revenue drivers, profitability patterns, and shipping efficiency**.
  
> **🔗 Live Dashboard:** https://app.powerbi.com/links/wF-RCF-JAq?ctid=4cf493e2-c44f-4a85-9650-f432e907ba34&pbi_source=linkShare
> **👤 Author:** Mohamed Tarek

---

## 📌 Overview

The goal of this project was to build an end-to-end analytics solution on a high-volume dataset (5M rows): from data cleaning and modeling, through DAX measures, to a multi-page interactive report. The dashboard answers business questions such as *which regions and products generate the most profit (not just revenue), when demand peaks, and how efficiently orders are shipped.*

---

## 🗂️ Dataset

**Source:** [Excel BI Analytics](https://share.google/WnQ9AyROteZGc896c)

- **Rows:** ~5,000,000 (cleaned)
- **Grain:** one row per sales order line
- **Fields:**

| Column | Description |
|---|---|
| Country | Country where the order was placed |
| Region | Geographic region (e.g. Sub-Saharan Africa, Europe, Asia) |
| Item Type | Product category (Beverages, Snacks, Clothes, Personal Care, Fruits, Vegetables, …) |
| Sales Channel | Online / Offline |
| Order Priority | Order urgency (Critical / High / Medium / Low) |
| Order ID | Unique order identifier |
| Order Date / Ship Date | Order placement and shipment dates |
| Units Sold | Quantity sold |
| Unit Price / Unit Cost | Price and cost per unit |
| Total Revenue / Total Cost / Total Profit | Order-level financials |

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — data modeling & report building
- **Power Query (M)** — data cleaning & transformation
- **DAX** — measures & calculated columns
- **Power BI Service** — publishing & mobile access

---

## 🧹 Data Preparation

Work performed in **Power Query** and the model before building visuals:

- Cleaned and validated 5M rows (removed blanks/duplicates, standardized data types).
- Disabled **Auto date/time** to reduce model size on the large dataset.
- Removed unused / high-cardinality columns to improve compression and performance.
- Added a dedicated **Date table** and marked it as the model's date table to enable accurate time intelligence.

---

## 🧩 Data Model

The model follows a lightweight **star-schema** approach: the sales fact table connected to a separate **Date dimension**, which keeps time-based calculations fast and reliable on 5M+ rows.

---

## 🧮 Key DAX Measures

```dax
Profit Margin % =
DIVIDE ( SUM ( Sales[Total Profit] ), SUM ( Sales[Total Revenue] ) )

Total Orders =
DISTINCTCOUNT ( Sales[Order ID] )

Avg Order Value =
DIVIDE ( SUM ( Sales[Total Revenue] ), [Total Orders] )
```

Calculated column for operational analysis (order fulfillment time):

```dax
Shipping Days =
DATEDIFF ( Sales[Order Date], Sales[Ship Date], DAY )
```

---

## 📈 Dashboard Pages & Visuals

**KPI Cards** — Total Revenue, Total Profit, Units Sold, Profit Margin %, Total Orders, Avg Order Value.

**Core visuals**
- **Line chart** — Revenue & Profit trend over time (reveals seasonality and peak months).
- **Filled map** — Revenue by Country.
- **Bar charts** — Revenue & Profit by Region and by Item Type.
- **Donut chart** — Online vs Offline sales split.
- **Matrix** — country-level breakdown of Revenue, Profit, and Units.

**Advanced / AI visuals**
- **Decomposition Tree** — breaks Total Profit down by Region → Item Type → Sales Channel.
- **Key Influencers** — highlights the factors most associated with higher profit.
- **Scatter chart** — Revenue vs Profit Margin per Item Type (surfaces high-revenue / low-margin products).

**Interactivity** — slicers for Region, Item Type, Sales Channel, Order Priority, and date range. A **mobile layout** was also configured for phone viewing.

---

## 💡 Key Insights

> Replace the bracketed values with the exact figures from your report.

- **Revenue vs profitability differ:** some product categories drive high revenue but thin margins, while others sell less yet return a higher profit margin — a distinction that reshapes where to focus.
- **Geographic concentration:** a small set of regions/countries accounts for a large share of total profit `[XX%]`, while others consume volume with weaker returns.
- **Seasonality:** sales peak around `[month/quarter]`, useful for planning inventory and campaigns.
- **Channel performance:** the Online vs Offline split is roughly `[XX% / XX%]`, showing the weight of each channel.
- **Operational efficiency:** average shipping time is `[N]` days, and varies noticeably by region — an operational lever worth monitoring.

---

## 🚀 How to Use

1. Clone or download this repository.
2. Open `5m-Sales-Records.pbix` in **Power BI Desktop**.
3. Refresh the data source if needed.
4. Or explore the published version via the **Live Dashboard** link above (opens on any device, including mobile).

---

## 🖼️ Screenshots

> Add exported images of your report pages here.

```
/screenshots
   ├── overview.png
   ├── regional-analysis.png
   └── profitability.png
```

`![Dashboard Overview](screenshots/overview.png)`

---

## 👤 Author

**Mohamed Tarek** — Data Science & AI student
Microsoft Power BI Data Analyst | Working toward PL-300

- LinkedIn: `<your LinkedIn URL>`
- GitHub: `<your GitHub URL>`
