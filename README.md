# Retail Analysis and Customer Segmentation
## Dataset Information:
This is a transnational data set which contains all the transactions occuring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail. The company mainly sells unique all-occassion gifts. Many customers of the company are wholesalers.
- **Dataset Characteristics:** Multivariate, Sequential, Time-Series.
- **Number of Instances:** 5,41,909
- **Number of Attributes:** 08
- **Associated Tasks:** Classification, Clustering.
#### Attribute Information:
- **InvoiceNo:** Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction. If this code starts with letter 'c', it indicated a cancellation.
- **StockCode:** Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.
- **Description:** Product (item) name. Nominal.
- **Quantity:** The quantities of each product (item) per transaction. Numeric.
- **InvoiceDate:** Invoice Date and time. Numeric, the day and time when each transaction was generated.
- **UnitPrice:** Unit price. Numeric, Product price per unit in sterling.
- **CustomerID:** Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.
- **Country:** Country name. Nominal, the name of the country where each customer resides.
## Dataset Overview:
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Dataset%20Overview.png?raw=true)
## Exploratory Data Analysis:
The top 10 most popular items are sold in/to the UK. Apparently paper craft little birdie is very popular, along with medium ceramic top storage jar. I will remove the items with 'NaN' descriptor. These entries associated with nan CustomerID entries and 131 lower case descriptions which describe problems with the orders and no details of the item ordered. In addition, the data for United Kingdom contains negative values associated with negative UnitPrice values. Removing the rows containing NaN values therefore cleans several issues that complicate this analysis in the absence of the data owner.
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/EDA.png?raw=true)
## Further Exploration and Trend Analysis:
How many unique descriptors are there in "Descriptions"?
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Further%20Exploration.png?raw=true)
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/newplot.png?raw=true)
## Investigation of Top CustomerID basket:
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Top%2050%20Largest%20Baskets.png?raw=true)
## Investigation of StockCode:
- There are some non-integer values in StockCodes which correspond with order descriptions that are not items.
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/ISC1.png?raw=true)
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/ISC2.png?raw=true)
## Feature Engineering:
- Moving on from exploratory data analysis, are there any features that can be created in order to categorize/cluster aspects of the data and aid machine learning?
## Investigation the Total Amount Spent per Customers:
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/ITASC.png?raw=true)
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Total%20Spend%20per%20Country.png?raw=true)
#### Top Purchasers
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Top%20Purchasers.png?raw=true)
#### Locate the Country of Origin of the Top 50 Biggest Spenders
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Top%2050%20Biggest%20Spenders.png?raw=true)






