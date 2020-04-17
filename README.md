
									Amazon Hot New Releases 
ReadMe File

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






