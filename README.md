# Customer_Segmentation_Capstone_1


DESCRIPTION:

In this repository, you will find the analyzes of customer segmentation analysis

DATA:

In the repository

examples of some important used methods:

#manulapating the dataframe by using str.contains

	df[df.InvoiceNo.str.contains('C')==True]

#using groupby for two times 

	df.groupby(['InvoiceNo','CustomerID']).count().reset_index().groupby('CustomerID').count().sort_values('InvoiceNo')

#one row lag for the date column

	df_uk_gp_date['Data_lagged']=(df_uk_gp_date.sort_values(by=['date'], ascending=True).groupby(['CustomerID'])['date'].shift(-1))

#differences between first and last orders

	df_uk.groupby(['CustomerID'])
	.agg({'Quantity':'sum','UnitPrice': 'mean', 'date': lambda x: x.max() - x.min()}).reset_index()['date']

#generation a column for the date from Timestamp values

	df_uk.InvoiceDate.apply(lambda x: datetime(x.to_pydatetime().year,(x.to_pydatetime().month),(x.to_pydatetime().day)))

#dividing quartiles

	pd.qcut(df_rfm['InvoiceNo'], q = 4, labels = False)

Some insights:

1. After processing the data, the Kmeans cluster method has used, and it made three clusters.

2. When we grouped clusters, we may understand clıusters followings;
	 Cluster 0: The first cluster belongs to the "Best Customers" segment which we saw earlier as they purchase recently, frequent buyers, and spent the most 

	 Cluster 1: The second cluster can be interpreted as passer customers as their last purchase is long ago, purchased very few, and spent little. The company has to come up with new strategies to make them permanent members. Low-value customers

	 Cluster 2: The third cluster is more related to the "Almost Lost" segment as they Haven’t purchased for some time, but used to purchase frequently and spent a lot.

3. According to time analysis of data, transaction, quantity, and total revenue has increased from time to time, but from August to December it has raised dramatically. On the other hand, the average of unit prices picked in July, then in the rest of year, it is almost between 5 and 10. Moreover, the number of sold products' transactions is similar to quantity, transaction, and total revenue whereas the number of return products' transactions went up in December as well. 

4. In order to increase the sales of the given company;
	
	4.1 The attention of first cluster customers should be continued with different policies

	4.2 Since the second cluster customers return the website even after a long time, their transactions are still low. Therefore, their attention can be captured with some recommendations products, or other policies 

	4.3 For the third cluster customers, the targeting policy should be revisited, then designed from the beginning and according to their features.

5. In time, sold and return graphs shows similar tendencies, except December, the characteristics of the month thus should be reconsidered. Moreover from august to December, the indicators were in positive trends, so that the policies which were followed in that time should be repeated. On the other hand, the average unit prices follow a different path, and it picked in June. Since it is an important input to get a higher rate of return, the situation in June should be analyzed as well. Last but not least, if there is a trade-off between the unit price and other variables, the equilibrium point should be carefully considered. 









