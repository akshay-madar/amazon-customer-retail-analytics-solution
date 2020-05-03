# Amazon - Customer and Retail Analytics Solution for ECommerce

## Motivation:
Amazon sells millions of products through thousands of sellers on its platforms. This portfolio of product varies widely across different product categories and even different times of the year. To boost visibility and popularity of products, Amazon hosts a New Releases ranking of top 100 products of all categories, a list which is updated hourly. To enable sellers insert their products into this list and move them further up the order, it is crucial to gain an understanding of which factors influence their ranks and how. Our objective is to build statistical model on publicly available data from Amazon so that sellers and ultimately Amazon can leverage our insights to push their products up the trending ladder.

### But why Amazon?
Because it is the world's largest online marketplace, with more than 310 active user base, and sells more than 12 millions products across different categories.

<p align="center">
  <img width="560" height="400" src="https://media.giphy.com/media/3JVHCwSgWWDUVMiTQs/giphy.gif">
</p>

## 1. Objective:





## Business Use Case:
- Scraped key data metrics of 700+ products on Amazon to identify drivers affecting the Top-100 Trending ranking
- Identified high value customers to enhance promotional outreach by using RFM analysis and predicting churn with ~93% accuracy


									Amazon Hot New Releases 


Detailed overview of all the steps to follow:

	1.) Run the “product and review links.ipynb” file to get the links of individual categories. Make sure to change the link for each category. The category links will be dynamic and updates 
    	    every hour. After exporting the results to CSV file, the product links in the csv file have to be considered only till "ProducID". This needs to be done because, the link gets changed 
    	    dynamically every hour and the hyperlink changes. 		Output file obtained: cumulative links.csv

	2.) Use the product links and review links obtained from the previous step and run the “Reviews and # of images.ipynb” to scrape the top reviews of each of the product. 
            This file also gives number of images displayed for each product.     Output file obtained: cumulative review.csv
 

	3.) Run the “Sentiment Analysis.ipynb” file to get the sentiment score of each review. Azure API is used to get the sentiment score. 	After appending the sentiment scores to the file
            generated in step 2 we obtain cumulative sentiments.csv

	4.) Run the “Product Attributes.ipynb” file to get the attributes of each product. Following attributes can be obtained (price, average rating, number of ratings, number of reviews,
            number of answered questions, prime category, Discount) cumulative sentiments.csv

	5.) Use “Data cleaning.ipynb” to merge all the datasets obtained above. output file obtained: modelfile.csv

	6.) Use “LinearRegression.R” to get the regression results.


Data Dictionary for the csv file : modelfile.csv

	Rank -> Rank of the product (for the specific category)
	Category -> Product Category field
	Product Link -> Link of the product needed to access the data
	Name - > Product Name
	Avg_Rating -> Rating of the product
	Review_link -> Hyperlink 
	rating_count -> Number f ratings (in number) given to the product and its different from average rating
	prime -> prime delivery or not
	Images -> Number of images for each product
	sentiment score -> sentiment score extracted from the top 10 reviews
	Answered Questions - > Number of answered questions present for the product
	Price -> Price of the product
	Discount -> Discount (in percentage) offered per product
	Customer_review_count -> Number of customer reviews for each product

Data Dictionary for the csv file : cumulative reviews.csv

	Rank -> Rank of the product (for the specific category)
	Category -> Product Category field
	review -> review of the product
	sentiment score -> sentiment score extracted from the top 10 reviews

Data Dictionary for the csv file : cumulative attributes.csv

	Rank -> Rank of the product (for the specific category)
	Product Link -> Link of the product needed to access the data
	Answered Questions - > Number of answered questions present for the product
	Price -> Price of the product
	Discount -> Discount (in percentage) offered per product
	Customer_review_count -> Number of customer reviews for each product
	Category -> Product Category field

Data Dictionary for the csv file : cumulative links.csv

	Rank -> Rank of the product (for the specific category)
	Category -> Product Category field
	Product Link -> Link of the product needed to access the data
	Name - > Product Name
	Avg_Rating -> Rating of the product
	Review_link -> Hyperlink 
	rating_count -> Number f ratings (in number) given to the product and its different from average rating
	prime -> prime delivery or not
	Images -> Number of images for each product






