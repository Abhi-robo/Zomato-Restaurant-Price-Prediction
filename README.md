# Zomato-Restaurant-Price-Prediction
Problem Statement To build a regression model to predict the cost of restaurant for two people based on the given indicators in the training data. 

Data Description
Data Description: This dataset predicts the visibility distance based on the different indicators as below:

1.	serial: The index/serial number
2.	URL : The URL for the restaurant 
3.	address:  The address of the restaurant.
4.	name: The name of the restaurant.
5.	online_order: Does the restaurant allow online order(Yes/No)
6.	book_table: Does the restaurant allow table booking(Yes/No)
7.	rate: Restaurant rating out of 5.
8.	votes: The number of votes for the restaurant.
9.	Phone: Resyaurant contact number
10.	Location: Location of the restaurant
11.	rest_type:Type of the restaurant(Casual Dining, Café etc.).
12.	dish_liked: The Most liked dishes in the restaurant(Pasta, Lunch Buffet, Masala Papad etc.)
13.	cuisines: North Indian, Mughlai, Chinese etc.
14.	approx_cost(for two people): In Rupees. (target Column)
15.	reviews_list: The List of reviews
16.	menu_item: Open Dosa', 'Benne Set Dosa' etc.
17.	listed_in(type): Buffet, café etc
18.	listed_in(city): The part of city where restaurant is listed.

Apart from training files, we also require a "schema" file from the client, which contains all the relevant information about the training files such as:
Name of the files, Length of Date value in FileName, Length of Time value in FileName, Number of Columns, Name of the Columns, and their datatype

# Model Training 
1) Data Export from Db - The data in a stored database is exported as a CSV file to be used for model training.
2) Data Preprocessing   
   a) Drop columns not useful for training the model. Such columns were selected while doing the EDA.
   b) Replace the invalid values with numpy “nan” so we can use imputer on such values.
   d) Check for null values in the columns. If present, remove them.
   e) Scale the training and test data separately 
    f) Encode the categorical values.
3) Clustering - KMeans algorithm is used to create clusters in the preprocessed data. The optimum number of clusters is selected by plotting the elbow plot, and for the dynamic selection of the number of clusters, we are using "KneeLocator" function. The idea behind clustering is to implement different algorithms
To train data in different clusters. The Kmeans model is trained over preprocessed data and the model is saved for further use in prediction.
4) Model Selection - After clusters are created, we find the best model for each cluster. We are using two algorithms, "Decision Tree Regressor" and "XGBoost regressor". For each cluster, both the algorithms are passed with the best parameters derived from GridSearch. We calculate the Rsquared scores for both models and select the model with the best score. Similarly, the model is selected for each cluster. All the models for every cluster are saved for use in prediction. 
