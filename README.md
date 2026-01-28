# SuperMarket---Sales---Analysis---PowerBI
Power BI dashboard analyzing supermarket sales performance, category insights, and monthly trends.

**Project Overview**
This project analyzes supermarket sales data to understand overall performance, category contribution, and sales trends over time.
The dashboard is designed for business users to quickly identify high-performing categories, purchasing patterns, and growth momentum.

**Dataset**
•	Source: Supermarket Sales Dataset (Kaggle / GitHub)
•	Time Period: Jan 2019 – Mar 2019
•	Granularity: Transaction level

**Key Fields Used**
•	Date
•	Product Category
•	Sales
•	Quantity
•	Unit Price

**Tools & Skills Used**
•	Power BI
•	Data modeling (Date table, relationships)
•	DAX measures
•	Time intelligence (MoM growth)
•	Data visualization & storytelling


**Dashboard Structure
PAGE 1: Category Performance Overview**
🔹 KPI Summary
•	Total Sales: 322.9K
•	Total Quantity Sold: 6K
•	Average Unit Price: 58.61

🔹 **Category Insights**
1️⃣ Total Sales by Category
•	Food & Beverages leads with highest sales contribution
•	Sales are fairly balanced across other categories
2️⃣ Quantity Sold by Category
•	Electronics followed by Food & Beverages have highest unit movement
•	Health & Beauty shows relatively lower demand
3️⃣ Average Unit Price by Category
•	Fashion Accessories and Sports & Travel have the highest average prices
•	Electronics shows lower unit price but higher volume
4️⃣ Sales Contribution (%)
•	No single category dominates
•	Indicates a diversified revenue portfolio

**PAGE 2: Time & Trend Analysis**
1️⃣ Sales Volatility with Recovery
Sales experienced a noticeable drop in February, followed by a strong rebound in March.
This suggests a short-term disruption rather than a structural demand issue.

2️⃣ Quantity Mirrors Sales Trend
The decline and recovery in sales closely track changes in quantity sold:
•	Lower transactions in February
•	Improved volume in March

3️⃣ Stable Pricing Environment
Average unit price remained relatively stable across months, implying that:
•	Sales changes were driven primarily by customer purchase frequency
•	Not by price fluctuations or discounting

4️⃣ Growth Momentum Insight
Despite the February dip, the positive MoM growth in March (+12.6%) signals:
•	Demand normalization
•	Potential effectiveness of operational or promotional recovery

________________________________________
🧠**Key Business Insights**
•	Sales growth is consistent, not volatile
•	Categories contribute evenly, reducing revenue risk
•	Higher-priced categories rely on value per transaction rather than volume
•	Growth momentum indicates potential for scaling promotional or inventory strategies

🧩**Data Modeling & DAX**
🔗 **Data Model Design**
Built a clean star-style model using:
Fact Table: supermarket_sales
Date Table: Custom calendar table created using DAX
Established a one-to-many relationship between:
Date_Table[Date] → supermarket_sales[Date]
Disabled auto date/time to avoid hidden date tables and incorrect time intelligence

⏱ **Time Intelligence Handling**
Created Year, Month Number, and Year-Month columns in Date Table
Sorted Year-Month by Month Number to ensure correct trend analysis
__________________________________________________________
**Key DAX Measures Used**
Below are the core business measures created for this analysis:
1️⃣ Total Sales
Total Sales = 
SUM(supermarket_sales[Sales])

2️⃣ Total Quantity
Total Quantity = 
SUM(supermarket_sales[Quantity])

3️⃣ Average Unit Price
Avg Unit Price = 
DIVIDE(
    [Total Sales],
    [Total Quantity]
)

4️⃣ Sales MoM % (Month-over-Month Growth)
Sales MoM % =
VAR CurrentMonthSales = [Total Sales]
VAR PreviousMonthSales =
    CALCULATE(
        [Total Sales],
        PREVIOUSMONTH('Date_Table'[Date])
    )
RETURN
DIVIDE(
    CurrentMonthSales - PreviousMonthSales,
    PreviousMonthSales
)




