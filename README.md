# 🍫 ChocolateSales: Global Retail Analysis

![Power BI](https://img.shields.io/badge/Power_BI-Data_Visualization-yellow)
![DAX](https://img.shields.io/badge/DAX-Advanced_Analytics-blue)
![Power Query](https://img.shields.io/badge/Power_Query-ETL-orange)

This Power BI project provides a comprehensive analysis of global chocolate sales for a retail business. The goal was to transform raw transactional data into actionable business intelligence, focusing on revenue growth, seasonal trends, and salesperson efficiency.

---

## 📊 Dataset Description
The analysis is based on a [Kaggle dataset](https://www.kaggle.com/datasets/atharvasoundankar/chocolate-sales/data) containing chocolate sales transactions with the following attributes:

| Attribute | Description |
| :--- | :--- |
| **Sales Person** | The individual responsible for the sale. |
| **Country** | Geographic market location. |
| **Product** | Specific chocolate SKU. |
| **Date** | Transaction timestamp (2022–2024). |
| **Amount** | Total revenue per transaction. |
| **Boxes Shipped** | Quantity of product sold. |

> **Project Constraint: Temporal Scope**
> * **Data Range:** January 2022 – August 2024.
> * **Analytical Impact:** This report focuses on Year-to-Date (YTD) performance. By excluding the Q4 holiday rush (Sept–Dec), the analysis provides a "baseline" view of the business, highlighting the Valentine's Day (Feb) and mid-year (June) peaks without the skew of end-of-year gifting surges. This allows for a more accurate assessment of "everyday" consumer behavior and sales rep consistency.

---

## 🛠️ Tech Stack & Skills
* **Power BI:** Data visualization and report authoring.
* **Power Query (M):** Data cleaning, type transformation, and handling null values.
* **DAX (Data Analysis Expressions):** Created advanced measures for time-intelligence and cumulative analysis.
* **Data Modeling:** Implementation of a **Star Schema** with a dedicated Date Dimension table for optimized performance.

---

## 🧪 Advanced DAX Used
I implemented custom DAX logic to drive the analytical depth of the report:

### 1. Year-over-Year (YoY) Growth
```dax
YoY Sales Growth = 
VAR LastYear = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Calendar'[Date]))
RETURN DIVIDE([Total Revenue] - LastYear, LastYear, 0)
```
### 2. Pareto (Running Total %)
```dax
Running Total % = 
DIVIDE(
    CALCULATE([Total Revenue], FILTER(ALLSELECTED('Table'[Product]), [Total Revenue] >= [Total Revenue])),
    CALCULATE([Total Revenue], ALLSELECTED('Table'[Product]))
)
```
---

## 🖥️ Dashboard Pages

### 1️⃣ Sales Overview
- High-level KPIs
- Ribbon Charts for market rankings over time
- Geographic Map of global revenue distribution
- Monthly revenue trend analysis

### 2️⃣ Team Performance
- Decomposition Tree for root-cause analysis of revenue drivers
- Scatter Plot to identify salesperson performance outliers
- Salesperson efficiency comparison across markets

---

## 📈 Key Insights & Findings

### 1. High-Level Performance & Growth
**Strong Expansion:**  
The business achieved a **54% YoY Sales Growth**, indicating a strong upward trajectory in market demand.

**Seasonal Peaks:**  
Revenue shows a distinct **“M-shape” pattern** across 2022–2024:
- Peaks: January and June
- Consistent trough: April

This pattern likely aligns with:
- New Year's / Valentine's demand
- Mid-year inventory cycles

---

### 2. Product Portfolio (The 80/20 Rule)
**Pareto Insight:**  
The top **5–7 products** (including Smooth Silky, 50% Dark, and White Choc) generate the majority of total revenue.

**Product Volatility:**  
The Ribbon Chart shows significant **rank-swapping month-to-month**, suggesting:
- Customer preferences are highly seasonal
- Promotions strongly influence demand
- Limited long-term brand loyalty to specific flavors

---

### 3. Geographic & Team Efficiency
**Market Leaders:**  
Top-performing markets:
- Australia — $3.65M
- UK — $3.37M

**Salesperson Productivity:**  
Top revenue contributors:
- Ches Bonnell (> $1M)
- Oby Sorrel (> $1M)

**Boutique vs Volume Sellers:**  
The scatter plot identifies a **premium seller archetype**:
- High revenue
- Lower box volume
- Focus on luxury/high-ticket products

---

## 🖼️ Dashboard Preview
![choco1](https://github.com/user-attachments/assets/69a1d143-d74f-473f-8569-48b33019b2b3)
![choco2](https://github.com/user-attachments/assets/f2a3f2ba-10c9-42ce-9ca7-afbed26c94de)

## 💡 Business Recommendations

### 1️⃣ Address the April Revenue Dip
**Finding:**  
Consistent sales decline in April across all years.

**Recommendation:**  
Launch a **Spring Promotion Campaign**:
- Limited-time flavors
- Loyalty incentives
- Experimental bundles

April is ideal for experimentation due to lower operational risk.

---

### 2️⃣ SKU Rationalization (Pareto Strategy)
**Finding:**  
~75% of revenue comes from ~25% of products.

**Recommendation:**  
Optimize inventory by:
- Discontinuing low-performing SKUs
- Prioritizing “star” products like Smooth Silky and 50% Dark
- Reducing storage and operational costs

---

### 3️⃣ Market-Specific Ad Spend & Localization
**Finding:**  
Australia and the UK are their top selling markets. 
The Country Slicer shows that regional taste differences exist:
- Australia → 50% Dark Bites
- UK → Peanut Butter Cubes

**Recommendation:**  
Shift from global campaigns to **localized data-driven marketing**:
- Allocate ~60% of marketing budget to top markets
- Customize creatives based on regional preferences

---

### 4️⃣ Sales Mentorship Program
**Finding:**  
Clear divide between:
- High-volume sellers
- High-margin boutique sellers

**Recommendation:**  
Create a **cross-mentorship program**:
- Volume sellers learn premium upselling
- Boutique sellers learn frequency optimization

---

## 🚀 How to Use

1. Download the `.pbix` file from this repository.
2. Open using Power BI Desktop.
3. Navigate between dashboard pages.
4. Use the **Country Slicer** on Page 1:
   - Dynamic titles and visuals update automatically based on selection.


---

## 📂 Files
- `Chocolate_Sales.pbix` — Main dashboard file
- `Chocolate_Sales.pdf` — Dashboard PDF file

---


## 👤 Author
Valarie K

---

