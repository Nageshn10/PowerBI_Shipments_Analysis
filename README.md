📊 Power BI Shipments Dashboard

This project demonstrates a Power BI shipments dashboard built using a star schema data model, sample dataset, and DAX measures. It provides insights into shipments, sales, and profitability.

🏗 Data Model (Star Schema)

The dataset is structured as a star schema, with a central fact table Shipments connected to dimension tables: Products, Sales_Person, Locations, and Calendar.
This design enables efficient analysis and scalable reporting.

📊 Dashboard Overview

The dashboard highlights:

Total Sales (Amount)
Total Profit & Profit %
Total Boxes Shipped
Shipment Count
Performance by Region, Product, and Salesperson
📈 Profit Analysis

Shows profit trends, year-over-year comparisons, and variance analysis.

🗂 Dataset (Sample)

The dataset is in one Excel workbook (datasets/sample_shipments.xlsx) with multiple sheets representing a star schema model:

Sheet Name	Description
Shipments	Fact table with shipment transactions
Products	Product details (Category, Cost per box)
Sales_Person	Sales team information
Locations	Region and country information
Calendar	Date table for time intelligence

Even though it’s a sample dataset, all relationships and DAX measures work exactly like in a real project.

🔗 Relationships
Shipments[PID] → Products[PID]
Shipments[GID] → Locations[GID]
Shipments[SPID] → Sales_Person[SPID]
Shipments[Shipdate] → Calendar[cal_date]

This forms a star schema, optimized for analysis and reporting.

🧮 DAX Measures

Some key DAX measures used in the dashboard:

Total Amount = SUM(shipments[Amount])

Total Amount (Last Year) =
CALCULATE([Total Amount], SAMEPERIODLASTYEAR('calendar'[cal_date]))

Total Amount (12 Month Variance) =
VAR Ta_ly = [Total Amount (Last Year)]
RETURN IF(ISBLANK(Ta_ly), BLANK(), [Total Amount] - Ta_ly)

Total Boxes = SUM(shipments[Boxes])

Total Boxes (Last Year) =
CALCULATE([Total Boxes], SAMEPERIODLASTYEAR('calendar'[cal_date]))

Total Boxes (12 Month Variance) =
VAR Ta_ly = [Total Boxes (Last Year)]
RETURN IF(ISBLANK(Ta_ly), BLANK(), [Total Boxes] - Ta_ly)

Total Costs = SUM(shipments[Cost])

Total Profit = [Total Amount] - [Total Costs]

Profit % = DIVIDE([Total Profit], [Total Amount], 0)

Shipment Count = COUNTROWS(shipments)

Full formulas are in dax_snippets/dax_measures.md.

🚀 How to Use (Sample Data)
Open Power BI Desktop
Load the dataset: datasets/sample_shipments.xlsx
Create relationships as defined in the star schema
Apply DAX measures from dax_snippets/dax_measures.md
Explore the dashboard visuals

Note: This is sample data, but all DAX measures and visuals are fully functional.

📝 Notes
Table names must match exactly: Shipments, Products, Sales_Person, Locations, Calendar
Calendar table should be continuous and marked as a Date table
All dashboard visuals and screenshots are stored in images/
💡 Personal Note

This dashboard is created by me, using online learning resources and hands-on practice. It demonstrates:

Star schema modeling
DAX calculations for KPIs
Interactive dashboard design
Visual storytelling with Power BI

Even with sample data, the project is fully functional and illustrates all core concepts.

✅ Key Highlights
Clean, sample-ready dataset
Star schema model for performance
Fully functional DAX measures
Interactive dashboard with visuals
Screenshots and diagram included for easy understanding
