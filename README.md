Sales Dashboard (Excel)
An interactive sales dashboard built in Excel with Power Query, Power Pivot, and PivotTables.
It analyzes sales across five Egyptian regions and lets the user filter by category, region, and date.
<img width="1255" height="555" alt="Scema" src="https://github.com/user-attachments/assets/5ad3940c-68f8-48f7-8ad9-72f7cf38361d" />
Key Figures
Metric	Value
Total Sales	$101,662,127
Total Orders	19,706
Total Customers	300
Units Sold	108,591
Tools
Microsoft Excel
Power Query (data cleaning and combining files)
Power Pivot (data model and relationships)
PivotTables, PivotCharts, and Slicers
Workflow
1. Data cleaning with Power Query
The full M code is in `PowerQuery.m`.
Products (CSV): set data types, proper case and trim on names and categories, remove the `$` sign from Price, fix a text value ("Two Hundred" to 200), convert Price to currency, and round up.
Customers (CSV): set data types, proper case and trim on Region and CustomerName, remove extra spaces inside Region.
Orders (folder of CSV files): combine all files with a Transform File function, keep the file name in `Source.Name`, filter out rows with an empty ProductID or Quantity, and rebuild the order date into a single Date column (replace `/` with `-`, split, detect the year, take the month from the file name, merge Days-Month-Years).
2. Data model with Power Pivot
3. <img width="1427" height="750" alt="Screenshot 2026-10-09 145657" src="https://github.com/user-attachments/assets/2c9a4ce6-fdcd-4015-8c4d-85b4362659ef" />
Table	Columns
Products	ProductID, ProductName, Category, Price
Orders	OrderID, CustomerID, ProductID, Quantity, Date, Sales
Customers	CustomerID, CustomerName, Region
Calendar	Date, Year, Month Number, Month, MMM-YYYY, Day Of Week, Date Hierarchy
Products, Customers, and Calendar each connect to Orders with a one-to-many relationship.
4. PivotTables
<img width="1049" height="533" alt="Screenshot 2026-10-09 145532" src="https://github.com/user-attachments/assets/324ef7d1-c6a0-4078-b617-5a7ee0897a85" />
Top 10 best-selling products (Sum of Sales)
Sales by category and by region
Number of orders by category
Sales and orders by month
Top 10 most requested products
Total units sold and customer count
5. Dashboard
KPI cards: Total Sales, Total Orders, Total Customers, Units Sold
Charts: top products, sales by category (pie), sales by region (donut), monthly sales and orders (column and line), orders by category, most requested products
Slicers: Category, Region, Date
Key Insights
Clothing is the top category (29%), followed by Toys (25%).
Sales are balanced across regions, from 18% (Alexandria) to 21% (Mansoura).
December is the peak month: 8.80M in sales and 1,756 orders.
The top 10 products account for about 63% of total sales.
Repository Structure
```
sales-dashboard/
├── Project.xlsx          # Workbook: data model, pivots, dashboard
├── PowerQuery.m          # Power Query (M) code
├── images/
│   ├── dashboard.png
│   ├── data-model.png
│   └── pivot-tables.png
└── README.md
```
How to Use
Download `Project.xlsx` and open it in Excel (desktop version, with Power Pivot support).
Use the slicers on the Dashboard sheet to filter by category, region, and date.
To refresh the data, update the file paths in Power Query (Data > Queries & Connections), since the queries read from local folders.
Author
Ahmed Essam
