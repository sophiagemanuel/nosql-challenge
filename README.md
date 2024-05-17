# nosql-challenge
Module 12 Assignment

For this assignment there were three sections that I had to complete:

The first section was to set up the Database and Jupyter notebook. First we confimed our new database was created by printing the names of the databases and then assigning the database to a variable name. From here I imported the json file within our resources into our database using MongoDBCompass. I then checked to make sure there was a collection named 'establishments' and that it contained documents. 

For the second section I was then focused on updating the database. First I created a dictionary and inserted the information for Penang Flavours and inserted it into the collections by using insert_one. I then found the BuisnessTypeID and returned only BuisnessTypeID and BuisnessType fields and then updated the new resturant with the ID that was found (1). To do this I used the update_one and then '$set' to change the ID type in Penang Flavours. I then found how many documents with LocalAuthorityName contained Dover by using a query and count_document and then deleted any entry with Dover by using the same query and the delete_many function. To finish off the second section I converted latitude and longitude to decimal numbers by using update_many and '$toDouble' and then converted the RatingValue to an integer by using the update_many and '$toInt.'

For the third section I completed a number of Explatory Analysis and then converted the results into a Pandas DataFrame.
1. Which establishments have a hygiene score equal to 20? I found this by creating a query for 'scores.Hygiene':20 and then found the number of documents by using the count_document function. I then put these results into a dataframe (hygiene_df) and displayed the amount of rows by using .shape[0] and then displaying the first 10 rows.
   
2. Which establishments in London have a RatingValue greater than or equal to 4? I found this by creating a query for {'LocalAuthorityName': {'$regex': 'London'}, 'RatingValue': {'$gte': 4}}, where '$regex' finds the location names including London and '$gte' finds the rating values that are greater or equal to 4. Again, I found the number of documents by using the count_document function, put the results into a dataframe, used .shape[0] and then displayed the results of the first 10 rows.
   
3. What are the top 5 establishments with a RatingValue rating value of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"? First I printed out the results for Penang Flavours to find the latitude and longitude that I would be using for this analysis. From that I created a variable for degree_search, latitude, and longitude. I then created a query to find the rating value of 5 and then used '$gte' to find the latitude-degree_search and '$lte' to find latitude+degree_search and the same for longitude. This sets the boundary of where we can look for establishments. I then sorted the Hygiene score in ascending order and limited it to 5. Again, I took the results and converted it into a DataFrame.

4. How many establishments in each Local Authority area have a hygiene score of 0?
