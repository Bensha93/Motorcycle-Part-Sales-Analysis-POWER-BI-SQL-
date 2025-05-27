
# 🏍️ Motorcycle Part Sales Analysis

This project delivers a comprehensive analysis of motorcycle part sales using SQL and Power BI. It identifies key sales trends, performance metrics, and actionable business insights to support data-driven decision-making.

---

## 📊 Project Overview

The analysis focuses on:

* Cleaning and transforming the `motorcycle_part_sales` dataset.
* Analyzing monthly and daily sales trends.
* Investigating customer behavior and product performance.
* Evaluating key performance indicators (KPIs) such as Month-over-Month (MoM) growth.
* Comparing weekday vs. weekend sales patterns.
* Visualizing results using **Power BI**.

---

## ⚙️ Tools & Technologies

* **SQL** – Data preparation and querying (MySQL/PostgreSQL compatible)
* **Power BI** – Data visualization and dashboard creation
* **Excel/CSV** – Optional data import/export formats

---

## 🔧 Key Features

* **Data Cleaning**: Null handling, type standardization, and column pruning
* **Monthly Sales Trends**: Sales totals, MoM growth calculations, trend analysis
* **Daily Sales Analysis**: Identifies top-performing days; compares daily vs. average sales
* **Category Insights**: Revenue breakdown by product line, customer type, and warehouse
* **Weekday vs. Weekend Patterns**: Assesses operational performance across the week

---

## 📌 SQL Highlights

**Monthly Sales Summary:**

```sql
SELECT  
    MONTH(date) AS month_sales,  
    ROUND(SUM(unit_price * quantity)) AS Total_Sales  
FROM motorcycle_part_sales  
GROUP BY MONTH(date);
```

**MoM Growth Calculation:**

```sql
SELECT  
    MONTH(date) AS month,  
    ROUND(SUM(unit_price * quantity)) AS total_sales,  
    (SUM(unit_price * quantity) - LAG(SUM(unit_price * quantity), 1)  
     OVER (ORDER BY MONTH(date))) / LAG(SUM(unit_price * quantity), 1)  
     OVER (ORDER BY MONTH(date)) * 100 AS mom_increase_percentage  
FROM motorcycle_part_sales  
GROUP BY MONTH(date);
```

---

## 📈 Insights & Outcomes

* **Seasonal Trends**: Peak sales months identified through MoM tracking
* **Customer Behavior**: Weekends consistently outperformed weekdays in sales volume
* **Warehouse Optimization**: Top-performing warehouses revealed, supporting strategic allocation
* **Product Line Analysis**: Customer preferences and profitability trends discovered by category

---

## ✅ Recommendations

Based on the analysis:

1. **Optimize Weekend Operations**: Enhance staffing and stock availability on weekends to capitalize on higher sales.
2. **Boost High-Performing Warehouses**: Allocate more inventory and marketing to top-performing locations.
3. **Expand Popular Categories**: Focus promotions and upselling on top-selling part categories.
4. **Monitor MoM Trends**: Regularly track growth metrics to detect early signs of performance shifts.
5. **Implement Real-Time Dashboards**: Use Power BI to automate daily sales tracking and decision support.

---

## 🧪 How to Use

1. Clone the repository:

```bash
git clone https://github.com/your-username/motorcycle-part-sales-analysis.git
```

2. Load the `motorcycle_part_sales` data into your SQL environment.
3. Run the SQL scripts in the `/sql` folder to:

   * Clean and transform data
   * Calculate KPIs and trends
4. Open the Power BI report (`.pbix` file) to explore dashboards and visualizations.

---

## 🚀 Future Enhancements

* Automate SQL KPIs with stored procedures
* Add profit margin and customer segmentation metrics
* Integrate forecasting models for sales prediction
* Enhance Power BI interactivity with slicers and drill-throughs

---

