## Step by step dax solution

## Calculated columns In Power Bi

i used calculated column in dax to create a new column joining the first name and last name to create a new column called full name

![Customer table showing fullnames](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-02%20120731.png)

After creating our full names column in our customer table, i used the if statememnt 
in power bi to bin the ages from the age column into groups.

![image showing binned ages](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-02%20123040.png)


A last purchase date column was created in our customer table, extracting the last day
that a customer made a purchase, this was accomplished by using the MAXX function and also 
the RELATEDTABLE function in powerbi .The MAXX function is used to find the maximum value of an expression for all rows in a table. 
This function takes a table as its first argument and an expression as its second argument.It went through the order date column and returned the latest order for each customer.
While Dax turns off our relationship,Relatedtable function enables me to use the relationship
tables share to access columns of the other tables.

![image showing last purchase date for all customers](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-02%20131230.png)


While perusing Through the data it came to my knowledge that internet sales table which is supposed to 
be the fact table lacked a relationship to the temperature table, so i had to create a temperature key 
in our internet sales table using calculated columns in power bi by joining 2 columns,one column from
sales territory table and another from the date table.
The related function in powerbi was used to accomplish this feet.
        RELATED is a Power BI DAX function that allows you to fetch a value from a column in a related table. Crucially, 
        this function only works if there's a relationship between the current table and the table where the desired column is located.

![image showing created temperature key column](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-03%20122701.png)

Further more in my sales territory region i used calculated columns to create a total transaction column
for each sales territory region. the function countrows and related table were used to accomplish this.
        the function countrows went to our internet sales table and counted the rows
        for each time a sales territory region appeared.

![image showing total transactions column for each region](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-03%20123818.png)

Further in the sales territory region table, a region volume column was created, counting each total transaction
for each region and binning them into either High, Medium or Low volume. this was done using the switch function in power bi

        the switch function is used to evaluate a single condition across several possible matches

![region volume column](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-03%20130049.png)


## Calculated Measures in Power Bi

Calculated measures, also known as formula measures, are a feature in Power BI that allows users to create new measures by using functions and calculations.

All measures were created on the internet sales table.

the first measure created was finding the amount of total sales. The sum function was used to achieve this.
        the SUM function adds all the values in a single column to return the result.

![Image showing formula for creating total sales measure.](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-03%20135410.png)

The next measure which was created is the total cost . The sum function was used here as well.
        Total cost = SUM('internet sales'[Total Production cost])

After that the total transaction measure was created, counting the number of all transactions.
        total transactions= countrows('internet sales')

The measure of profit was created, subtracting the total cost from total sales

![image showing profit measure](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-03%20141155.png)

Then the profit margin measure was created, to figure out our profit in percentage, 
the divide function was used, then the measure was formatted into percentage

![image showing profit margin measure](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-03%20141939.png)

the next measure created was for the total sales for all countries excluding any NA values.
this was achieved using,the if statement,isblank function,calculate the all function in Power Bi
        ISBLANK() function Checks whether a value is blank, and returns TRUE or FALSE.
        CALCULATE function is It is defined as “evaluating an expression within a modified filter context.” 
        An expression, which typically represents a measure, includes functions such as SUM, AVERAGE, and COUNT. 
        This expression is evaluated in the context of one or more filters.

![measure showing sales for all countries](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-04%20114936.png)


The calculate function was used again to get the total sales specifically for just united states.

![image showing total sales measure ofr united states](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-04%20120251.png)

The same measure was created for just canada

Then a measure for the total sales for United states and canada was created  using the || to symbolize as or

    Total sales (us & canada)= 
    calculate(
        [total sales],
        'sales territory'[sales territory country]= "United States" ||
        'sales territory'[sales territory country]= "Canada"
    )

### Time series analysis under calculated measures

a year to date measure was created using the totalytd function in powerbi
        TotalYTD function Evaluates the specified expression over the interval which begins on the first day of the year and
        ends with the last date in the specified date column after applying specified filters.

![image showing totalytd measure](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-04%20131019.png)

Fiscal year to date or ytd was created using dax functions in power bi, 
selecting june 30th as our fiscal year

![image showing fiscal year todate sales measure](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-05%20111157.png)

A prior year sales measure was also created comparing years sales.

![image showing prior year sales](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-05%20114037.png)

Each week day was also calculated and summed to show the most profitable weekday
        ytd sales(weekdays)=
        totalytd(
            [total sales],
            'date'[date ],
            'date'[day number of week] in {2,3,4,5,6}
        )

### Semi additive measures under calculated measures in power bi
 a semi-additive measure uses SUM to aggregate over some dimensions and a different aggregation over other dimensions 

 Trying to get the closing balance the inventory , a product inventory measure was created

 ![image showing product inventory](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-05%20121432.png)

 A closing balance measure was created for each month using the calculate function and lastnonblank function
    the LASTNONBLANK function returns only the months that closing balance is not blank

![image showing closing balance measure](https://github.com/techbeast911/DAX_IN_POWER_BI/blob/main/Img/Screenshot%202024-12-05%20121902.png)