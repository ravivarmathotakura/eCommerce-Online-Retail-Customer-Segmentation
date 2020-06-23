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
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Top%20Purchasers.png?raw=true)
 ![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Top%2050%20Biggest%20Spenders1.png?raw=true)
#### Classify Customers Based on Total Spend
- Collate all the purchases made during a single order to calculate the total order value:
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Classify%20customers%20based%20on%20total%20spend.png?raw=true)
- The distribution of basket is somewhat bimodal. This histogram of basket values indicates a large number of low total value baskets and a small number of individual orders totaling high value baskets. This observation can be used to bin customers into those spending small amounts, medium amounts, and high value baskets (note the bimodal distribution above may cause an imbalance problem for machine learning)
## Clustering
- Group by CustomerID, together with sum or number of items (quantity) and the unit price
## Feature Scaling using sklearn StandardScaler
- Using the Elbow method to find the optimum number of clusters
- From 2-10 doing multiple random initializations can make a huge difference to find a better local optimal
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Clustering.png?raw=true)
## Fitting K-Means to the Dataset
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/k-mean.png?raw=true)
- Clustering appears to separate the customers based on numbers of items and total spend, which would be expected.
## Modeling
### Machine Learning Data Preparation
- A cursory examination of correlation to identify potentially problematic variables from the model training dataset.
- Heat Map to look for correlation
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/HeatMap.png?raw=true)
- Unsurprisingly, total spend correlates with quantity and the spend_label. Potentially, quantity or total spend may have to be removed for training.
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Spend%20Label.png?raw=true)
- This data is very imbalanced. For the purposes of this investigation the lower value baskets will be used for prediction.
- Below I will identify a range suitable for binning:
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Total%20Spend1.png?raw=true)
- Here we are repeating the labeling of total spend from low (0), medium (1), and high (2), but with the lower range of values.
- Numerical labels represent 0 - low value baskets, 1 - medium value baskets, 3 - higher value baskets.
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/Spend%20Label1.png?raw=true)
- The data is still unbalanced in terms of representation from high value baskets, but more balanced than the full dataset.
- Create dummy variables from the string columns (descriptions and country).
#### PCA is being performed on the 1st 100000 data points due to limited compute resource
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/PCA.png?raw=true)
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/PCA1.png?raw=true)
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/PCA2.png?raw=true)
- From the PCA analysis of the dataset, the majority of variance in the model is in the 1st principle component. It is of no great surprise that potentially, total spend is sufficient to predict the basket size label. From visualisation of the principle components, the labels are well separated/clustered, facilitating machine learning. The bimodal appearance of the data requires further investigation.
## Additional training data using 'Country' as label
![alt text](https://github.com/ravivarmathotakura/eCommerce-Online-Retail-Customer-Segmentation/blob/master/images/PCA3.png?raw=true)

