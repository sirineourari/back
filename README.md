# recommendation_system
Due to the rapid growth of the internet in conjunction with the information overload problem the use of recommender systems has started to become necessary for both e-businesses and customers.

In fact, these systems suggest the most relevant items to buy and, as a result, increase a company’s revenue.
The suggestions are based on user's behavior and history that contain information on their past preferences.

The goal of this project is to build a recommendation system to recommend products to customers based on the their previous ratings for other products.

# Background
The recommendation system will be based on Amazon dataset.
In fact, Online e-commerce sites like Amazon, Flipkart use different recommendation models to provide different suggestions to different users.

Amazon currently uses item-to-item collaborative filtering, which spans big data sets and produces high-quality recommendations in real time.

In this project we will use the Amazon dataset named 'ratings Electronics'.
link: https://www.kaggle.com/saurav9786/amazon-product-reviews 

Attribute Information:
•userId: Each user identified by a unique identifier.This attribute is a dicrete variable.
•productId: Each product identified by a unique identifier.This attribute is a dicrete variable.
• Rating: evaluation of the corresponding product by the corresponding user;This attributeis a categorical variable.
• timestamp: time of the evaluation.This attribute is a discrete numeric variable.

#Data description 
First, we need to discover our data by reviewing its shape and the and the five-number sum-mary of the data.
Using df.shape we get to know the size of our data which is (7824482, 4)
Using  df.columns  we  get  to  know  the  columns  of  our  data  :  ’userId’,  ’productId’,  ’Rating’,’timestamp’
Using df.head() we get to have an idea of our data .

Second, we need to look for missing values using the function isna of pandas.
Our data doesn’t contain missing values.

The next step is to visualize our variables.We start with the categorical variables.
The variable ’ratings’ is a categorical variable. Its values are : [ 1. 2. 3. 4. 5.]
After visualizing the categorical variable, we visualize the discrete variables.
The next step is to measure the correlation between the two attributes ’Rating’ and ’times-tamp'

# Filtering the data
Here we will only consider products that have received at least 10 reviews. 
Because there maybe cases where the review count is 1 or 2 but the values are 5, in this case these kinds of productswill appear at the top for the recommendation which would not be a good recommendationtechnique.
Also, we will only keep users who have given 50 or more number of ratings.
We can only keep users who have given 50 or more number ofratings.And we will only consider products that have received at least 10 reviews.

# Grouping sparce categories 
After removing the products that have received less than 10 reviews and removing users whohave given less than 50 number of ratings,
we found out that our new data contain outliers. We will use feature enginerring techniques to group sparcing data.

We finally transform the ordered categorical attribute ’Rating’ into numeric attribute usingLabel encoding imported from the sklearn library.

# Building the filtering system
There are two main recommendation routes:
•Content-based filtering  models:  Content-based  filtering  models  are  based  on  item  de-scription and user history preference, 
and we don’t need other users’ feedback to makerecommendations.  
Example:  User likes three products designed by a certain company,so we recommend a fourth product designed by that company.
•Collaborative filtering (CF) : Collaborative filtering (CF) is a popular recommendationalgorithm that bases its predictions and recommendations on the rating or behavior of other users of the system.  
We will use the collaborative filtering (CF) approach.  CF is based on the idea that the best recommendations come from people with similar interests.
In other words, it uses the ratings of historical items from people with similar ratings to predict how someone would rate an item.
we are going to use collaborative filtering (CF) because our dataset only contains the evaluation of the product and it does not include product characteristics (price, weight, size, color...)
In the group of collaborative filtering, the two most well-known distinct approaches are:
•  Memory-based models calculate similarities between users items based on pairs of scoresassigned by the user.
•  The  models  based  on  models  (Model-based  models)  use  a  kind  of  automatic  learningalgorithm to estimate the evaluations.
A typical example is the singular value decomposition of the user’s article ranking matrix.
