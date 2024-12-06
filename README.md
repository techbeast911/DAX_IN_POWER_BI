# DAX_IN_POWER_BI

Power BI Project Showcase: Mastering DAX Step by Step!

I recently completed an exciting project using Power BI and DAX to perform advanced data modeling and analysis. Here’s a breakdown of the steps and techniques I implemented:
🔹 Calculated Columns in Power BI

    Full Name Column:
    Created a column combining first and last names in the customer table.

    Age Binning:
    Used an IF statement to categorize customer ages into bins for better demographic analysis.

    Last Purchase Date:
    Leveraged the MAXX and RELATEDTABLE functions to extract the last purchase date for each customer.

    Temperature Key:
    Resolved a missing relationship between the internet sales and temperature tables by creating a calculated column using the RELATED function.

    Transaction Analysis by Region:
        Counted transactions in each sales territory using COUNTROWS.
        Binned transaction volumes into High, Medium, and Low using the SWITCH function.

🔹 Calculated Measures in Power BI

    Core Metrics:
        Total Sales and Total Cost using the SUM function.
        Profit as the difference between Total Sales and Total Cost.
        Profit Margin as a percentage using the DIVIDE function.

    Filtered Metrics:
        Sales for all countries, excluding blanks, using CALCULATE and ISBLANK.
        Sales for specific countries like the US and Canada using filters within the CALCULATE function.

    Combined Metrics:
    Created a measure for total sales for both the US and Canada using the OR (||) operator.

🔹 Time Series Analysis

    Year-to-Date (YTD) Sales:
    Utilized TotalYTD to calculate cumulative sales within the calendar year.

    Fiscal Year Sales:
    Defined June 30th as the fiscal year-end to calculate fiscal YTD sales.

    Prior Year Comparison:
    Built a measure to compare sales year-over-year.

    Most Profitable Weekday:
    Summed weekday sales to identify the most profitable days.

🔹 Semi-Additive Measures

    Product Inventory:
    Created a measure to track inventory levels over time.

    Closing Balance:
    Used LASTNONBLANK and CALCULATE to calculate the closing balance for each month.

This project was a deep dive into the power of DAX for solving complex data challenges and creating insightful metrics. 🚀 Let me know your thoughts or if you'd like to collaborate on future Power BI projects!
