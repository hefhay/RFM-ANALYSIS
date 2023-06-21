# RFM-ANALYSIS

## INTRODUCTION
Welcome to a data analysis project on RFM analysis, a powerful tool in the arsenal of data analysts to uncover valuable insights about customer behavior. In today's competitive business landscape, understanding customer preferences and identifying their value is crucial for driving growth, enhancing customer experiences, and optimizing marketing strategies.
RFM analysis, an acronym for Recency, Frequency, and Monetary, is a method widely employed by data analysts and marketers to segment customers based on their purchasing patterns. By evaluating these three fundamental aspects of customer behavior, RFM analysis enables organizations to gain a comprehensive understanding of their customer base and make data-driven decisions to maximize business outcomes.
I will explore the core concepts of RFM analysis, discuss its significance in modern business environments, and provide step-by-step instructions on implementing RFM analysis using various analytical tools and techniques.

## DATA SOURCE
The dataset was gotten from a youtube page i came across while searching for a perfect dataset i could use. The youtube page is UrBizEdge

## PROBLEM STATEMENT
The problem at hand is to develop a robust RFM analysis methodology that allows us to efficiently segment customers, uncover valuable patterns in customer behavior, and provide actionable recommendations for marketing, retention, and revenue optimization strategies.

## DATA CLEANING AND TRANSFORMATION
I got information about the columns in the dataset and i noticed the date column wasn't in the right data type so it was changed to the right data type.
The transaction ID and the costomer ID was also changed from  an integer data type to a string since the numbers are just for identification purposes.

## ANALYSIS
Now to start our analysis on RFM. I created a new table 'rfm_table'. I created the table  by grouping the customer ID with the recent date of the each customer ID as 'Date'. 

We get the most recent date in the dataset where a customer purchased goods and assume this date as a reference to which the recency could be calculated called the recent_date(the most recent date we got here could be stipulated by the client or in some cases we use today's date as the most recent date).

We create a recency column in the rfm_table and this is gotten by the getting the difference in days from the recent_date and the most recent date each customer purchased goods.

A frequency table was also created and it was grouped by the customer ID and the count of the transaction ID of each customer to get how frequent each customer has purchased goods

And the monetary table was also created by grouping by the customer ID and the sum of all revenue each customer ID has spent. 

After getting the three tables, I merged them by the customer ID.

We divide each of the three categories into percentiles (20,40,60,80) creating 5 categories (1,2,3,4,5)
The recency cetegory is created in descending order since the the customer with the lowest recency are valuable than those with high recency while other categories are arranged in ascending order.

The values (1,2,3,4,5) gotten in each category are categorical values so the data type is changed from integers to strings and they are later merged together (concatenation) in this order; (recency_category, frequency_category, monetary_category) and this is called the rfm_score.

We import another table into our database called tge segment scores table and it consist of the customers segment and the rfm_score. On importing the table, i noticed that the rfm_score was an integer datatype and it includes decimals which i converted and removed the decimals

A new RFM_Table was obtained by merging the rfm_ table we had before and the segment_scores_table and they were both joined together on the rfm_score.
