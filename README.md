# SALES INSIGHTS - Atliq Technologies _PowerBi

#### Project - https://app.powerbi.com/groups/me/reports/3f80ea78-7060-4103-8c12-48c64ab6e7dd/ReportSection?experience=power-bi

## Table of Contents
- Problem Statement
- Solution
- Data
- Task
- Data Cleaning
- Data Modeling
- DAX
- Dashboarding
- Insights
- What I’ve Learned

## Problem Statement
AtliQ Hardware, with multiple branches across India, provides computer hardware and peripheral manufacturers to its clients. The sales director is encountering difficulties in comprehending the company’s current issues and performance, as sales are decreasing below expectations.

Whenever the director seeks updates from regional managers regarding sales and the market, they tend to sugarcoat the truth and send excessive Excel files, adding to the director’s frustration. The frustration is understandable, as humans often find it challenging to comprehend numbers from Excel files.

## Solution
As a data analyst, a solution to address the sales director’s problem at AtliQ hardware would be to BI dashboards that can help with data visualization and analysis. The sales director can use dashboard that pulls in data from various sources, including the company’s sales data, market trends, and regional manager reports. With the dashboard, the sales director can easily see the current state of the business, identify problem areas, and make data-driven decisions.

By having a clear, visual representation of the data, the sales director can also avoid relying on Excel files and sugar-coated reports from regional managers, which can lead to misunderstandings and frustration.

## Data

We are provided with the SQL dataset which contains customers, date, transactions(2), markets, and products tables. We need to provide insights using the data from those tables.

![Sales_data](https://github.com/LavanyaVishwakarma/Sales_Insights/assets/120155873/0b75ea39-95bf-42e9-bcd3-737a1cfca93f)


## Task

-  Finding Profit Margin, Sales Quantity and Revenue made in each year/month
- Analyzing top 5 customers and product by revenue
- Finding the Revenue Margin Contribution, Profit Margin Contribution and Profit % by each customer
- Finding the Revenue Margin Contribution, Profit Margin Contribution and Profit % by each Market
- Finding the Revenue trend by years
- Analyzing Revenue contribution by customer type.

## Data Cleaning

- Removed zones which were left blank in market table
- Removed sales amount which were less than 0 in sales transaction table
- Created new table called Normalized sales price to convert the USD price to INR price in sales transaction table
- Removed duplicates from currency column in sales transaction table.

## Data Modeling

And then dataset was cleaned and transformed, it was ready to the data model.

![Sales_data_model](https://github.com/LavanyaVishwakarma/Sales_Insights/assets/120155873/63411172-cc77-4668-801b-d50cc0e29817)

## Data Analysis Expressions (DAX)
Key Measures:
- Profit Margin % = `DIVIDE([Total Profit Margin],[Revenue],0)` 
- Profit Margin Contribution % = `DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))`
- Revenue = `SUM('sales transactions'[sales_amount])`
- Revenue Contribution % = `DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))`
- Revenue LY = `CALCULATE([Revenue],SAMEPERIODLASTYEAR('sales date'[date]))`
- sales quntity = `SUM('sales transactions'[sales_qty])`
- Total Profit Margin = `SUM('Sales transactions'[Profit_Margin])`

Profit Target:
  
  - Profit Target1 = `GENERATESERIES(-0.05, 0.15, 0.01)`
  - Profit Target Value = `SELECTEDVALUE('Profit Target1'[Profit Target])`
  - Target Diff = `[Profit Margin %]-'Profit Target1'[Profit Target Value]`

## Dashboarding

### Key_insights
![Key_insights](https://github.com/LavanyaVishwakarma/Sales_Insights/assets/120155873/9fc3b436-0913-4ecd-baf6-be8bd881b462)

### Profit_analysis
![profit_analysis](https://github.com/LavanyaVishwakarma/Sales_Insights/assets/120155873/d990437a-4045-41b9-b077-2afb802a34fe)

### Performance_insights
![Performance_insights](https://github.com/LavanyaVishwakarma/Sales_Insights/assets/120155873/adac799a-e8cc-4a3f-97ba-60434678760f)

## Insights 
- There is a decrease in the revenue trend from 2017–2020
- Delhi NCR is the highest contributor in Revenue and Sales quantity by Market
- E-commerce gives the highest revenue contribution by customer type
- Surat gives highest profit % by market
- Central Market contributes to more Revenue

#### Tools used:  MySQL,  Microsoft Power BI,  Power Query Editor,  DAX 

## What I’ve Learned
- How to do basic DAX calculations in measures 
- Importing data from SQL to Power BI
- Publishing report to Power BI service
- How to use basic charts for visualization
- How to use filters in charts

I have provided the pdf of my project - [Sales_Insight (1).pdf](https://github.com/LavanyaVishwakarma/Sales_Insights/files/14472120/Sales_Insight.1.pdf)

### AUTHOR - "LAVANYA VISHWAKARMA" https://www.linkedin.com/in/lavanya-vishwakarma-591059218/




