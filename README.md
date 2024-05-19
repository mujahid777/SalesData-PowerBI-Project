# PowwrBI-Project

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


> > > > > > > > > > > > 
