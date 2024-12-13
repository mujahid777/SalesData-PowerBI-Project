# Sales Data Analysis PowerBI Project

## OBJECTIVE :

To create a one-page sales report dashboard that effectively showcases Sales Insights, we’ll need to consider the data sources provided and how best to visualize the information. Feel free to use your imagination to best represent the data you have available.

1.	Sales (folder by year)
2.	Categories (Excel)
3.	Geography (Excel)
4.	Product (CSV / Database)
5.	SalesRep (Excel)
6.	SubCategories (Excel)

## Data Gathering / Requirement:

Create a mechanism to load all the files from the sales folder in a single Sales fact table.

> The mechanism needs to be resilient as:

 - Removing a file from the sales folder does not create an error for missing files.
 
 - Adding a new yearly sales file will automatically be loaded in the fact query upon refresh.

## Data Modeling: 
Task 2.1: 
> Do the respective transformations to the Sales fact table in order to split the Country form the City in field “Location”. Make sure you set up the correct Data Type to allow Geo maps.
Do the necessary updates in the Date field to make sure you can setup the Date format.

Task 2.2: 
> Create unique key (GeoKey) in Sales and Geography table

Task 2.3:
> The Dimensional queries SalesRep and Sub Category need additional treatment. Some ID columns have the following format:

| SalesRepID  |
| :---------- | 
| ID-6        | 
| ID-7        |
| ID-5        |        
| ID-3        | 
| ID-1        | 
| ID-1        |
| ID-2        |
| ID-4        |

Create a small function that removes the “ID - ” part of these columns that you can invoke and reuse for these two queries to clean the IDs.

Task 2.4: 
> Create the Data Model connecting all tables and using the Calendar table already set up in the pbix.

## DAX calculations

Task 3.1:
> Calculate Total Revenue in Sales table, using the Product’s Retail Price, and multiplying it by the Units.

**Total Revenue = SUMX(Sales, Sales[Units] * RELATED(Product[Retail Price]))**

Task 3.2:
> Calculate Total Cost in Sales table, using the Product’s Standard Cost, and multiplying it by the Units.

**Total Cost = SUMX(Sales, Sales[Units] * RELATED(Product[Standard Cost]))**

Task 3.3:
> Calculate Gross Profit in Sales: Total Revenue – Total Cost

**Gross Profit = [Total Revenue] - [Total Cost]**

Task 3.4:
> Calculate a Gross profit MoM growth Change% measure that could benefit us in decision making.

**MoM Growth = (Gross Profit[Current Month] - Gross Profit[Previous Month]) / Gross Profit[Previous Month]**

Task 3.5:
> Calculate a measure for AVG sales per day – this is the average sum of Total Revenue per day based on the Dates of actual Sales.

**AVG Sales per Day = AVERAGEX(VALUES(Date[Date]), [Total Revenue])**

Task 3.7: 
> Breakdown Analysis by Product (drop or increase)
Calculate the following time measures:
-	This is QBR Report. So QoQ Growth is required.

**QoQ Growth = (Gross Profit[Current Quarter] - Gross Profit[Previous Quarter]) / Gross Profit[Previous Quarter]**

>	Use the measures and calculations to assemble a sales reports with different visuals to best show the Sales Insights in one page Dashboard. Feel free to use your imagination to best represent the data you have available.
If you plot Month on x-axis, make sure the months are sorted from Jan-Dec.

### Dashboard :

![dashboard](https://github.com/mujahid777/SalesData-PowerBI-Project/blob/main/Sales%20Analysis%20Dashboard.png)

### Report :

![report](https://github.com/mujahid777/SalesData-PowerBI-Project/blob/main/Sales%20Analysis%20report.png)

# Insights :

#### 1.	January and February Drop:
> Gross profit starts at 7.31M in January but drops to 6.48M in February, indicating a sharp decline in profit. This could suggest seasonal effects or lower sales performance.
#### 2.	Recovery from March to July:
> From March (7.33M), the gross profit exhibits a steady rise, peaking in July at 7.93M, suggesting strong mid-year performance.
#### 3.	Post-July Decline:
> After the July peak, the gross profit decreases to 7.23M in August and continues fluctuating around 7.18M in September.
#### 4.	October Spike, November Dip, and December Recovery:
> Gross profit climbs to 7.52M in October but dips sharply to 6.74M in November. However, it recovers in December, reaching 7.32M, potentially reflecting end-of-year seasonal trends.






