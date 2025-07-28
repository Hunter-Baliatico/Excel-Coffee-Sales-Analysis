# Coffee Sales Dashboard (Excel Project)

This project showcases a full data analysis process using Microsoft Excel, built around a fictional coffee company’s sales data. From raw files to a clean, interactive dashboard, the goal was to tell a clear story using real-world analytics skills.

The work involved cleaning and enriching datasets, applying formulas to shape the data, and using PivotTables and charts to uncover key insights. While this project focuses on coffee sales, the approach is applicable to any business looking to understand performance across time, customer segments, and geography.
<img width="1537" height="806" alt="Dashboard" src="https://github.com/user-attachments/assets/7f4e26a7-e54f-4910-84bf-b608253ca4ca" />


---

## Dataset Overview

| Sheet       | Description                                      |
|-------------|--------------------------------------------------|
| `orders`    | Raw transactional data (products + customers)    |
| `customers` | Customer names, contact info, country, loyalty   |
| `products`  | Coffee catalog with size, price, roast, and type |

---

## Objective

- Clean and connect coffee order data using formulas and lookups  
- Use PivotTables and charts to extract key sales insights  
- Build a polished Excel dashboard for interactive exploration  
- Generate valuable and actionable recommendations
---

## Tools & Excel Features Used

- XLOOKUP, INDEX-MATCH, nested IF() functions  
- PivotTables and PivotCharts  
- Data cleaning: duplicates, formatting, missing values  
- Slicers and Timeline for dashboard interactivity  
- Custom layout and color formatting for clarity and impact

---

## Process Breakdown

### 1. Data Cleaning

Customer and product fields were filled using lookup functions.

**Before Cleaning Preview**  
<img width="1098" height="462" alt="Raw Data" src="https://github.com/user-attachments/assets/c5629099-dd39-407d-9c3e-a7738db1092b" />


**After Cleaning Preview**
<img width="1720" height="402" alt="Cleaned Data" src="https://github.com/user-attachments/assets/9b9fbdc2-5f72-4f93-a5d6-beac3fe9c3d1" />

**Country XLOOKUP Formula**

This formula uses XLOOKUP to fetch each customer's country from the `customers` sheet using their `Customer ID` as a key. This enables region-level segmentation in the dashboard.

```excel
=XLOOKUP(C2,customers!$A$1:$A$1001,customers!$G$1:$G$1001,,0)
```

**Loyalty Card XLOOKUP Formula**

Similar to the country lookup, this XLOOKUP retrieves the Loyalty Card status for each customer. This enables slicing the dashboard by customer type for behavioral comparison.

```excel
=XLOOKUP([@[Customer ID]],customers!$A$1:$A$1001,customers!$I$1:$I$1001,,0)
```

**Index-Match Formula**

This INDEX-MATCH combination pulls product-specific details such as coffee type, roast type, size, and unit price from the `products` sheet based on `Product ID`. It is used as an alternative to XLOOKUP for flexibility.

```excel
=INDEX(products!$A$1:$G$49,MATCH(orders!$D2,products!$A$1:$A$49,0),MATCH(orders!I$1,products!$A$1:$G$1,0))
```

**Sales Multiplication Formula**

A simple calculated column that multiplies `Quantity` by `Unit Price` to retrieve the total sales per row.

```excel
=L2*E2
```

---

### 2. Data Transformation

Used nested If statements to improve readability and dashboard usability.

**Formatting IF Formula (Coffee Type)**

This nested IF() formula changes the shortened (`Rob`, `Exc`, `Lib`,`Ara`.) to readable coffee type names (`Robusta`, `Excelsa`, `Liberica`,`Arabica`.).

```excel
=IF(I2="Rob","Robusta",IF(I2="Exc","Excelsa",IF(I2="Ara","Arabica",IF(I2="Lib","Liberica",""))))
```

**Formatting IF Formula 2 (Roast Type)**

This formula changes roast type abbreviations (`M`, `L`, `D`) into full names for use in slicers and charts.

```excel
=IF(J2="M","Medium",IF(J2="L","Light",IF(J2="D","Dark","")))
```
---

### 3. Standard Data Cleaning Tasks

In addition to formula-driven transformation, basic cleanup steps ensured consistency across the dataset:

- **Date Formatting**:Date fields were reformatted for grouping in timeline visuals.
- **Currency Formatting**: Prices and totals were formatted as currency with no decimals to improve clarity.
- **Duplicate Checks**: Checked for and removed duplicate records to prevent incorrect counts ins sections.
- **Column Renaming & Sorting**: Column names were clarified for easier reference in PivotTables.


---

### Interactivity

- **Timeline filter** allows monthly sales exploration  
<img width="1091" height="148" alt="Dashboard Timeline" src="https://github.com/user-attachments/assets/624652ba-4f60-425e-994a-67bcdcb4b725" />


- **Slicers** enable filtering by Roast Type, Size, and Loyalty Card for all graphs
<img width="445" height="174" alt="Roast Type - Size - Loyalty Card Slicers" src="https://github.com/user-attachments/assets/3470d369-2ec5-4cee-8834-96576953d6d2" />


---

## Visualizations & Key Insights

### Total Sales Over Time  
Sales patterns reveal that Arabica and Liberica consistently generate strong monthly sales, with clear revenue peaks in January, March, October, and December. This pattern may suggest seasonal demand, possibly driven by colder weather.  
<img width="1089" height="543" alt="Sales Over Time Line Chart" src="https://github.com/user-attachments/assets/22740f1e-c31d-4dfa-9aad-de3449ad819e" />


---

### Top 5 Customers  
The top five customers contributed a notable portion of total revenue, each placing multiple high-value orders. Their behavior suggests high engagement and a strong product fit, making them ideal candidates for targeted retention strategies  
<img width="444" height="249" alt="Top 5 Customers Bar Chart" src="https://github.com/user-attachments/assets/3a331c8f-273b-4e7b-913a-005492b1f4c3" />


---

### Sales by Country  
Sales are mostly concentrated in the U.S., with smaller but notable contributions from Ireland and the U.K. This suggests strong brand awareness or operational presence in the U.S., while international markets may be underdeveloped.   
<img width="445" height="288" alt="Sales By Country Pie Chart" src="https://github.com/user-attachments/assets/a15bec19-e7c1-4a9f-94dc-0aea070f6894" />


---

## Actionable Insights & Recommendations

- **Customer Retention**: The top 5 customers account for a significant portion of revenue. Consider improving the  loyalty to retain and expand this high-value segment.

- **Geographic Focus**: With the U.S. driving over 80% of sales, targeted marketing efforts in underperforming regions like the U.K. may increase geographic balance.

- **Product Strategy**: Arabica consistently leads in sales. Consider bundling it with other roast types or promoting it during peak months to maximize revenue.

- **Sales Seasonality**: Sales often peak during the first and last quarters of each year. Running seasonal promotions or subscription models during these periods could amplify returns.

---

## Files Included

| File | Description |
|------|-------------|
| `Coffee_Sales_Raw.xlsx`          | Original dataset before cleaning or enrichment |
| `Coffee_Sales_Dashboard.xlsx`    | Final workbook with cleaned data, formulas, and dashboard |
| `screenshots/`                   | Project visuals and formula captures |
| `README.md`                      | Project documentation (this file) |

---

## Author

**Hunter Baliatico**  
Aspiring Data Analyst | Excel, SQL, Tableau  
[LinkedIn](https://www.linkedin.com) | 
