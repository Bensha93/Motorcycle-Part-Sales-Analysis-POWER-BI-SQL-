
# Motorcycle Part Sales Analysis

## **Description**  
This project focuses on analyzing motorcycle part sales data to uncover trends, calculate key performance indicators (KPIs), and provide actionable insights. Using SQL, the dataset is cleaned, transformed, and queried to generate monthly and daily sales trends, customer behaviors, and performance metrics.

[Motorcycle_Powerbi](https://github.com/user-attachments/assets/4fd53d0b-46c4-4dc5-9367-1d8cf642a6ea)

---

## **Table of Contents**  
1. **[Project Overview](#project-overview)**  
2. **[Key Features](#key-features)**  
3. **[SQL Highlights](#sql-highlights)**  
4. **[Insights and Outcomes](#insights-and-outcomes)**  
5. **[How to Use](#how-to-use)**  
6. **[Tools and Technologies](#tools-and-technologies)**  
7. **[Future Enhancements](#future-enhancements)**  
8. **[License](#license)**  

---

## **Project Overview**  
The project involves:  
- **Data Preparation**: Cleaning and standardizing the `motorcycle_part_sales` dataset.  
- **Sales Analysis**: Identifying total sales, orders, and quantity trends on monthly and daily levels.  
- **Trend Analysis**: Understanding weekday vs. weekend performance, comparing daily sales to averages, and analyzing sales by location and category.  
- **KPI Calculation**: Tracking Month-over-Month (MOM) growth in sales, orders, and quantities.  

---

## **Key Features**  
- **Data Cleaning**: Handled null values, standardized data types, and removed unnecessary columns.  
- **Monthly Sales Trends**: Calculated total sales, MOM differences, and growth percentages.  
- **Daily Performance**: Analyzed daily sales trends and their comparison with averages.  
- **Category Insights**: Explored sales by product line, customer type, and warehouse location.  
- **Weekday vs. Weekend Analysis**: Highlighted performance differences based on the day of the week.  

---

## **SQL Highlights**  
### **Monthly Sales Calculation**  
```sql
SELECT  
    MONTH(date) AS month_sales,  
    ROUND(SUM(unit_price * quantity)) AS Total_Sales  
FROM motorcycle_part_sales  
GROUP BY MONTH(date);
```  

### **MOM Growth Analysis**  
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

### **Daily Sales Trends**  
```sql
SELECT  
    DAY(date) AS day_of_month,  
    ROUND(SUM(unit_price * quantity), 1) AS total_sales  
FROM motorcycle_part_sales  
WHERE MONTH(date) = 6  
GROUP BY DAY(date);
```  

---

## **Insights and Outcomes**  
- **Seasonal Trends**: MOM growth highlighted periods of peak sales.  
- **Daily Performance**: Certain days consistently outperformed others, with higher sales on weekends.  
- **Warehouse Insights**: High-performing warehouses were identified, aiding resource allocation.  
- **Category Analysis**: Helped understand customer behavior across product lines and client types.  

---

## **How to Use**  
1. Clone the repository:  
   ```bash
   git clone https://github.com/your-username/motorcycle-part-sales-analysis.git
   ```  
2. Load the `motorcycle_part_sales` table into your SQL database.  
3. Run the SQL queries in order to:  
   - Clean and transform the data.  
   - Generate monthly and daily sales reports.  
   - Extract insights on customer behavior and product performance.  

---

## **Tools and Technologies**  
- **SQL**: For data cleaning and querying.  
- **Database**: Tested with MySQL and PostgreSQL.  
- **Visualization**: (Optional) Use tools like Tableau or Power BI to create charts and dashboards.  

---

## **Future Enhancements**  
- Automate sales and performance reporting with stored procedures.  
- Build real-time dashboards for trend monitoring.  
- Expand analysis to include profit and customer segmentation.  

