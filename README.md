# ecommerce-sales-analysis-excel
E-commerce sales analysis and dashboard built with Microsoft Excel and Power Query.

# Project Overview
This project analyzes e-commerce sales data using Microsoft Excel to identify key trends and business insights across revenue, profitability, products, customers, countries, age groups, and shipping performance.

The project follows an end-to-end analytics workflow, beginning with data preparation in PostgreSQL and continuing with data validation, transformation, analysis, and dashboard development in Excel.

# Objective
The objective of this analysis was to transform transactional sales data into meaningful business insights and create an interactive Excel dashboard that summarizes overall business performance.

The analysis focused on answering eight key business questions:

1. What is the total revenue, and how has it trended over time?
2. Which product category generates the most revenue?
3. What are the top 10 best-selling products by revenue?
4. What is the overall profit margin, and which category is most profitable?
5. Which country contributes the most revenue?
6. Who are the top 10 customers by total spend?
7. What is the customer distribution by age group?
8. What is the average shipping time across all orders?

# Tools Used
- PostgreSQL — Data extraction and preparation
- Power Query — Data validation and transformation
- Microsoft Excel — Analysis and dashboard development
- Pivot Tables — Data aggregation and business analysis
- Pivot Charts — Data visualization

# Data Preparation
The dataset was initially prepared in PostgreSQL by joining the sales fact table with the customer and product dimension tables.
The resulting dataset was exported and imported into Excel Power Query for further validation and transformation.

# Power Query Work
The following tasks were performed:
- Confirmed appropriate data types
- Converted Birthdate from Text to Date
- Checked numeric fields for invalid negative or zero values
- Trimmed and standardized text fields
- Verified gender and marital status values
- Renamed columns for presentation
- Created a Customer Name field
- Calculated Age: This was calculated using the formula: =IF([@Birthdate]="", "Unknown", DATEDIF([@Birthdate], TODAY(), "Y"))
- Created Age Group: This was calculated using the formula: =IFS([@Age]="Unknown", "Unknown",[@Age]<=55, "40-55", [@Age]<=70, "56-70", [@Age]<=85, "71-85", [@Age]>85, "86+")
- Calculated Profit: This was calculated using the formula: =[@[Sales Amount]] - [@Cost]
- Calculated Profit Margin: This was calculated using the formula: =IF([@Sales Amount]]=0,0,[@Profit]/[@Sales Amount]])
- Created Order Year: This was calculated using the formula: =YEAR([@[Order Date]])
- Created Order Month: This was calculated using the formula: =TEXT([@[Order Date]], "mmmm")
- Created Shipping Check

# Shipping Check
Shipping Check was calculated by subtracting:
(Shipping Date - Order Date)

The result was 7 days for records with valid Order Dates.

There were 19 missing Order Dates, while Shipping Dates were populated throughout the dataset.

# Final Dataset
The final dataset contained:
60,398 rows. No accidental row loss was identified during the Power Query process.

# Key Performance Indicators
The dashboard contains six key performance indicators:

**KPI	Result**
- Total Revenue: $29,356,250
- Total Profit: $11,686,000
- Profit Margin: 40%
- Total Orders: 27,659
- Total Quantity: 60,423
- Shipping Time: 7 Days

# KPI Definitions
- Total Revenue: Sum of Sales Amount.

- Total Profit: Sum of Profit.

- Profit Margin: Total Profit ÷ Total Revenue.

- Total Orders: Distinct count of Order Number.

- Total Quantity: Sum of Quantity.

- Shipping Time: Average Shipping Check.

# Business Analysis
1. Revenue Trend
The revenue trend analysis covered 2011–2014, with 2014 containing January data only.
- **Year	Revenue**
- 2011 - $7,075,088
- 2012 - $5,842,231
- 2013 - $16,344,878
- 2014 - $45,642

Revenue declined from 2011 to 2012 before increasing significantly in 2013.

The monthly analysis showed particularly strong revenue performance toward the end of 2013, with November and December recording some of the highest monthly sales.

Note: The trend analysis excludes records associated with the 1900 and 2010 entries identified during the date validation process.

2. Revenue by Category
- **Category - Revenue**
- Accessories: $700,262
- Bikes: $28,316,272
- Clothing: $339,716

Bikes were the highest revenue-generating category, contributing $28.3 million in sales.

3. Top 5 Products by Revenue
- **Rank - Product - Revenue**
1. Mountain-200 Black- 46 - $1,373,454
2. Mountain-200 Black- 42 - $1,363,128
3. Mountain-200 Silver- 38 - $1,339,394
4. Mountain-200 Silver- 46 - $1,301,029
5. Mountain-200 Black- 38 - $1,294,854

The top 5 best-selling products are all bikes, primarily Mountain-200, confirming Bikes as the company's core revenue driver, consistent with the category breakdown.

4. Profitability by Category
- **Category	  Revenue	        Profit	      Profit Margin**
- Accessories	  $700,262	      $439,605	    63%
- Bikes	        $28,316,272	    $11,109,565	  39%
- Clothing	    $339,716	      $136,830	    40%
- **Total	      $29,356,250	    $11,686,000	  40%**

The overall profit margin was 40%.

Accessories had the highest profit margin at 63%, while Bikes generated the highest total profit because of their significantly greater revenue volume.

5. Revenue by Country
- **Country	      Revenue**
- United States	  $9,162,327
- Australia	      $9,060,172
- United Kingdom	$3,391,376
- Germany	        $2,894,066
- France	        $2,643,751
- Canada	        $1,977,738
- n/a	            $226,820

The United States generated the highest revenue at $9.16 million, closely followed by Australia at $9.06 million.

6. Top 5 Customers by Total Spend
- **Rank	Customer	Total Spend**
1	Jordan Turner	    $15,998
2	Willie Xu	        $13,489
3	Kaitlyn Henderson	$13,294
4	Nichole Nara	    $13,294
5	Margaret He	      $13,268

Jordan Turner had the highest total spend at $15,998.

7. Age Group Analysis
- **Age Group	Sales	Order Count**
- 40–55	  $15,471,026	  30,313
- 56–70	  $10,798,928	  21,844
- 71–85	  $2,890,240	  7,582
- 86+	    $140,052	    580
- Unknown	$56,004	      79

The 40–55 age group generated the highest sales and recorded the highest order activity.

The 56–70 age group was the second-largest segment.

8. Average Shipping Time was:
7 days

Shipping Check was calculated as the difference between the Shipping Date and the Order Date.

The 19 records with missing Order Dates produced blank Shipping Check values and were excluded from the average calculation.

# Dashboard
The final Excel dashboard provides a visual summary of the analysis.

**KPI Cards**
- Total Revenue
- Total Profit
- Profit Margin
- Total Orders
- Total Quantity
- Shipping Time

**Visualizations**
- Revenue Trend by Year
- Revenue by Category
- Overall Profit Margin by Category
- Revenue by Country
- Revenue by Age Group 
- Revenue by Top 5 Best-Selling Products
- Amount Spent by Top 5 Customers

# Interactive Filters
The dashboard includes slicers that allow users to explore the analysis by relevant dimensions, including:

- Order Month
- Category
- Country
- Age Group

# Key Insights
- Bikes generated the highest revenue, contributing $28.3 million in sales.
- 2013 was the strongest year in the analyzed period, generating $16.3 million in revenue.
- Accessories had the highest profit margin, at 63%.
- The United States was the highest-revenue country, generating $9.16 million.
- Mountain-200 variants dominated the top product rankings.
- Customers aged 40–55 generated the highest sales and order activity.
- Average shipping time was 7 days.
- 19 records had missing Order Dates, which affected time-based analysis but did not result in row loss from the final dataset.

# Conclusion
This project demonstrates the use of SQL and Excel to transform transactional data into actionable business insights.

The workflow covered data preparation, validation, transformation, KPI development, Pivot Table analysis, data visualization, and dashboard design.

The completed dashboard provides a concise view of revenue, profitability, products, customers, geographic performance, and shipping efficiency.

This project strengthened my practical skills in Excel analytics, Power Query, Pivot Tables, data visualization, KPI development, and business-focused data analysis.
