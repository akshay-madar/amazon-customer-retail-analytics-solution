# Amazon - Customer and Retail Analytics Solution for ECommerce

## Motivation:
Amazon sells millions of products through thousands of sellers on its platforms. This portfolio of product varies widely across different product categories and even different times of the year. To boost visibility and popularity of products, Amazon hosts a New Releases ranking of top 100 products of all categories, a list which is updated hourly. To enable sellers insert their products into this list and move them further up the order, it is crucial to gain an understanding of which factors influence their ranks and how. 

### But why Amazon?
Because it is the world's largest online marketplace, with more than 310 active user base, and sells more than 12 millions products across different categories.

<p align="center">
  <img width="560" height="400" src="https://media.giphy.com/media/3JVHCwSgWWDUVMiTQs/giphy.gif">
</p>

## 1. Objective:
The objective is to build statistical model on publicly available data from Amazon so that sellers and ultimately Amazon can leverage our insights to push their products up the trending ladder.

<p align="center">
  <img width="800" height="500" src="https://github.com/akshay-madar/amazon-customer-retail-analytics-solution/blob/master/amazon/data_problem.PNG">
</p>

## 2. Computational Steps:
To examine the impact of various variables on rank of sellers, Amazon is leveraged as the platform to obtain data points for few vital attributes in our solution – rank, prime delivery status, discount offered status, price, top 10 customer reviews, average rating, rating count, number of answered questions, and number of product images. Data is scraped rigourously from Amazon using BeautifulSoup, for seven different categories – **Electronics, Computers and Accessories, Clothing, Pet Supplies, Tools and Home Improvement, Toys and Games, and Grocery** – that catalyze most of the sales for Amazon. 

<p align="center">
  <img width="800" height="500" src="https://github.com/akshay-madar/amazon-customer-retail-analytics-solution/blob/master/amazon/data_collection.PNG">
</p>

<p align="center">
  <img width="800" height="500" src="https://github.com/akshay-madar/amazon-customer-retail-analytics-solution/blob/master/amazon/new_releases.PNG">
</p>

This is followed by necessary data preparation to account for skewness, and a check on correlation amongst variables.

<p align="center">
  <img width="800" height="500" src="https://github.com/akshay-madar/amazon-customer-retail-analytics-solution/blob/master/amazon/data_preparation.PNG">
</p>

<p align="center">
  <img width="760" height="500" src="https://github.com/akshay-madar/amazon-customer-retail-analytics-solution/blob/master/amazon/correlation.png">
</p>

To ensure a comprehensive analysis, top 10 customer reviews are collected which captured the overall product sentiment adequately. Thereafter, **Microsoft Azure Text Analytics API** is used to generate averaged sentiment scores for each product.

<p align="center">
  <img width="800" height="500" src="https://github.com/akshay-madar/amazon-customer-retail-analytics-solution/blob/master/amazon/sentiment.PNG">
</p>


After requisite data preparation to account for skewness in certain variables, log-log regression model was deployed to measure elasticity of rank with respect to given variables. We also accounted for synergy effect between variables and included interaction terms. The full model encompassing all product categories was run to give significant variables that affected ranking of products. For a deeper analysis into how different product categories behaved, a subsampled regression analysis for each category was also performed to see how significant the variables were for these categories.

## Insigths and Value Proposition:
There are multiple parameters which have considerable effect on the ranks of new releases. Also, the extent of impact of different parameters is different across the categories. Amazon and its sellers can benefit from the model by identifying which areas help in increasing the rank of their newly released products. The probability of higher sales increases massively due to higher visibility, if the rank increases. Also, while it is essential that sellers manage to enter this trending list of new releases, they would be able to reap maximum benefit if they move from the rank bucket of 51-100 on second page to the first page of top 50 product releases. We believe our analysis and accompanying insights would help them achieve this critical objective to stay on the trending list for longer, which would result in improved sales for their products, and edge out competing brands

## Detailed overview of steps to follow:

							Amazon Hot New Releases   


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






