# Sales & Customer Funnel Report
**Objective**:

This project aims to get insights from sales data using Power BI, focusing on customer behaviour, transaction performance and regional sales trends. The dashboard enables stakeholders to make data-driven decisions based on real-time, visual insights.

**About the Project:**

By analyzing detailed sales data, I built an interactive dashboard that answers key business questions around customer retention, payment preferences, product performance, and geographical sales distribution.
This project follows a complete BI workflow:
- Business Understanding & Requirement Gathering
- Data Cleaning, Modeling & Transformation in Power BI
- DAX Calculations for KPIs and Trends
- Dashboard Design & Insights Generation

**Key Features:**

- Sales & Customer Funnel Analysis Filters
- KPI Analysis: Net Sales, Quantity, Total Customers & Repeat Customers
- Payment Method Breakdown to reveal transaction preferences
- Hourly Net Sales Trends for time-of-day analysis
- Product Type Performance by revenue and quantity
- City and Province-wise Sales Distribution via maps and bar charts
- Customer Segmentation (One-time vs. Repeat Buyers)
- Customer Lifetime Value Metrics: Repeat Rate & Purchase Frequency

**Key Insights from the Dashboard:**

- Nearly 46% of customers are repeat buyers, indicating strong retention.
- Shoes is the top-performing category, dominating sales volume and revenue.
- Shopify Payments is the most used payment method, accounting for nearly 60% of transactions.
- Washington tops in total customers, net sales, and repeat customer count.
- Peak purchasing hours reveal valuable marketing & operational optimization windows.

**Data:**

Includes order-level data such as:
- Product category
- Payment method
- Timestamps (date & hour)
- Customer ID (for repeat tracking)
- City, Province, Country
- Net Sales, Quantity

**Key Business Questions Addressed**

- What is the overall sales performance by region, product, and hour of the day?
- Which payment methods are most preferred by customers?
- What is the repeat purchase rate, and how does it vary by region or product?
- Which cities/provinces drive the most sales?
- What is the lifetime value and purchase frequency of repeat customers?

**Business Impact & Highlights**

- Supports data-driven marketing by revealing peak hours and high-LTV segments
- Enables inventory planning by identifying top-selling product types
- Guides customer retention strategy through repeat customer behavior tracking
- Highlights regional performance, assisting in location-specific promotions

**Screenshots**



**Tools & Technologies Used**

- Power BI for data visualization
- Excel for raw data preparation and formatting
- DAX for calculated columns & KPIs


**Queries implemented for analysis**

**Repeat Customers =**

    CALCULATE(COUNTROWS(VALUES(sales[Customer Id])),
        FILTER(VALUES(sales[Customer Id]),
            CALCULATE(DISTINCTCOUNT(sales[Order Number])) > 1
        ))

**Single Order Customers =**

    CALCULATE(COUNTROWS(VALUES(sales[Customer Id])),
        FILTER(VALUES(sales[Customer Id]),
            CALCULATE(DISTINCTCOUNT(sales[Order Number])) = 1
        ))

**Total Customers =** 

    DISTINCTCOUNT(sales[Customer Id])

**Repeat Rate =** 

    [Repeat Customers] / [Total Customers]

**Total Quantity =** 
    
    SUM(sales[Quantity])

**Life Time Value =** 
    
    
    [Net Sales]/[Total Customers]

**Map Title =** 

    "Regional Overview - Province & Cities by " & SELECTEDVALUE('Select Measure'[Dynamic Title])

**Net Avg Order Value =** 

    AVERAGE(sales[Subtotal Price])

**Net Sales =** 

    SUM(sales[Subtotal Price])

**Purchase Frequency =** 

    DISTINCTCOUNT(sales[Order Number])/[Total Customers]

**Product Title =** 

    SELECTEDVALUE('Select Measure'[Dynamic Title]) & " by Product Type"

**Trend Title =** 

    SELECTEDVALUE('Select Measure'[Dynamic Title]) & " Trend Over Time"

**Gateway Title =** 

    SELECTEDVALUE('Select Measure'[Dynamic Title]) & " by Gateway Payment Method"

