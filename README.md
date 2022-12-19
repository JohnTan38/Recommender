# Alexa, which movie would you recommend?

![Heading](https://miro.medium.com/fit/c/1838/551/1*YGlG3RmEDn3ZuS10V3rUGg.png)


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

![Python](https://img.shields.io/badge/python-v3.11+-blue.svg?style=for-the-badge)
![Dependencies](https://img.shields.io/badge/dependencies-up%20to%20date-brightgreen.svg?style=for-the-badge)
![Contributions welcome](https://img.shields.io/badge/contributions-welcome-orange.svg?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge)


# Components and Tools

<p align="center">
	<a href="#">
		<img src="https://upload.wikimedia.org/wikipedia/commons/e/ed/Pandas_logo.svg" alt="Pandas Logo" title="Pandas" width=220 hspace=5 />
	</a>
	<a href="#">
		<img src="https://upload.wikimedia.org/wikipedia/commons/0/0a/Python.svg" alt="Python Logo" title="Python" width ="88" hspace=60/>
	</a>
  <a href="#">
    <img src="https://upload.wikimedia.org/wikipedia/commons/8/84/Matplotlib_icon.svg" alt="Matplotlib Logo" title="Matplotlib" width="88" />
  </a>  
</p>

## Problem Statement
Construct a recommendation algorithm capable of accurately predicting how a user will rate a movie they have not viewed based on their past preferences. The models and EDA are based on the 1M MOVIELENS dataset

## Approach
* First glance at the raw data
* Preparing data for better visualization

* EDA
* Explore the datasets using visualization tools (graphs or tables)
  1. User Age Distribution
  2. User rating of the movie “Toy Story”
  3. Top 25 movies by viewership rating
  4. Find the ratings for all the movies reviewed by for a particular user of user id = 2696


## Users' Age Distribution
![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/UserAge_dist.PNG)

## Rating Distribution of Toy Story
![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/ToyStory_dist.PNG)

## Top 25 Movies
![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/Top25.PNG)

## Ratings of movies reviewed by user 2696
![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/Top20_2696.PNG)

## Dramas and Comedies are Popular genres
![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/Genre_freq.PNG)


## Movies Recommended to user 2696 
![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/Top20_predict.PNG)



## Word Cloud of Popular movies
![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/WordCloud.png)


* Feature Engineering
  1. Find out all the unique genres (Hint: split the data in column genre making a list and then process the data to find out only the unique categories of genres)
  2. Create a separate column for each genre category with a one-hot encoding ( 1 and 0) whether or not the movie belongs to that genre.
  3. Determine the features affecting the ratings of any particular movie.
* Building the models
  - Content based 
  - Collaborative Filtering 
  - Hybrid
  
Recommender systems function with two kinds of information:

Characteristic information. This is information about items (keywords, categories, etc.) and users (preferences, profiles, etc.).

User-item interactions. This is information such as ratings, number of purchases, likes, etc.

Based on this, we can distinguish between three algorithms used in recommender systems:
  - Content based systems, which use characteristic information.
  - Collaborative Filtering systems, which are based on user-item interactions.
  - Hybrid systems, whcih combine both types of information with the aim of avoiding issues when working with just one type of system


![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/Recommender_systems.PNG)

# Content based Filtering

Idea: If you like an item then you will also like a “similar” item

Content based recommender systems are based on the similarity of the items being recommended. It generally works well when its easy to determine the context/properties of each item. For instance when we are recommending the same kind of item like a movie recommendation or song recommendation.

In this recommender system the content of the movie (genre, keywords, cast, directors, tags, etc) will be used to find its similarity with other movies. The movies that are most likely to be similar are then recommended.

![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/Content_based.PNG)

# Collaborative based Filtering


Collaborative methods for recommender systems are methods that are based solely on the past interactions recorded between users and items in order to produce new recommendations. These methods do not require item meta-data like their content-based counterparts. This makes them less memory intensive which is a major plus since our dataset is so huge.

## There are 2 collaborative based filtering methods:
**Memory based**<br>
We will investigate 2 two memory based methods: User-user and item-item. The main characteristics of user-user and item-item approaches is that they use only information from the user-item interaction matrix and they assume no model to produce new recommendations.

**Model based**<br>
Model based collaborative approaches only rely on user-item interactions information and assume a latent model supposed to explain these interactions. For example, matrix factorisation algorithms consists in decomposing the huge and sparse user-item interaction matrix into a product of two smaller and dense matrices: a user-factor matrix (containing users representations) that multiplies a factor-item matrix (containing items representations).

# User-user Collaborative based Filtering


This method captures the underlying pattern of interests of like-minded users and uses the choices and preferences of similar users to suggest new items.

In order to make a new recommendation to a user, the user-user method roughly tries to identify users with the most similar “interactions profile” (nearest neighbours) in order to suggest movies that are the most popular among these neighbours (and that are “new” to our user). This method is said to be “user-centred” as it represents users based on their interactions with items and evaluates distances between users.

![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/User_user.PNG)

# Item-item collaborative based filtering
To tackle the issues with user-based collaborative based techniques, item-based collaborative techniques analyze the user-item matrix and identify relationships between different items (Sarwar et al.,2001). The item-based recommendation system then makes recommendations based on the discovered linear relationships (similarities) amongst the items. This method is more stable compared to user based collaborative filtering because the average item has a lot more ratings than the average user. So an individual rating doesn’t impact as much.

The idea of item-item method is to find movies similar to the ones the user already “positively” interacted with. Two items are considered to be similar if most of the users that have interacted with both of them did it in a similar way. This method is said to be “item-centred” as it represents items based on interactions users had with them and evaluates distances between those items.

![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/Item_item.PNG)

# Singular value decomposition (SVD)
Unlike Memory-Based Approaches, Model-Based procedures facilitate machine learning techniques such as Singular Value Decomposition (SVD) and Matrix Factorization models to predict the end user's rating on unrated items.

We will be using SVD to build our recommender engine. We utilize the results of SVD to fill the vacant ratings and then use the item based method to produce the prediction of unrated items.

Formally, **SVD is decomposition of a matrix R which is the utility matrix with m equal to the number of users and m number exposed items (movies) into the product of three matrices:**

 - U is a left singular orthogonal matrix, representing the relationship between users and latent factors (Hopcroft & Kannan, 2012)

 - Σ is a diagonal matrix (with positive real values) describing the strength of each latent factor

 - V(transpose) is a right singular orthogonal matrix, indicating the similarity between items and latent factors.

![Heading](https://github.com/JohnTan38/Recommender/blob/main/dat/SVD.PNG)

 
# Conclusion

The 1M movieLens dataset was used to build our recommender system. This dataset contains movie ratings and movie specific data dating back 50 years. We performed exploratory data analysis to look at users' age distribution, popular movie genres and top movies rated by users. There are 19 unique movie genres in the dataset with Drama, comedy and thriller being the 3 most popular genres.

We explored 3 different methods for building our recommender system. The content based method proved to be too memory intensive and was dismissed as a possible solution.

Collaborative based methods were investigated next since they are based solely on the past interactions recorded between users and items in order to produce new recommendations. These methods do not require item meta-data like their content-based counterparts.

The memory based methods explored were user based and item based. Both these methods performed adequately but have issues with sparsity and scalability.

The final method was singular value decomposition (SVD), a model based collaborative filtering method which addresses the sparsity issue we had with the user-user and item-item based methods as well as having the added benefit of being less memory intensive compared to content based filtering methods.

The SVD model was able to predict new ratings with a RMSE of 0.8

## References 

Keller, J. (2019). Item-Item Recommendation with Surprise. [online] Medium. Available at: https://medium.com/@jmcneilkeller/item-item-recommendation-with-surprise-4bf365355d96.

ai-pool.com. (n.d.). Recommendation Systems by Matrix Factorization and Collaborative Filtering. [online] Available at: https://ai-pool.com/a/s/recommendation-systems-by-matrix-factorization-and-collaborative-filtering.

Kumar, D.V. (2020). Singular Value Decomposition (SVD) In Recommender System. [online] Analytics India Magazine. Available at: https://analyticsindiamag.com/singular-value-decomposition-svd-application-recommender-system/.

Maher Malaeb (2016). Singular Value decomposition (SVD) in recommender systems for Non-math-statistics-programming…. [online] Medium. Available at: https://medium.com/@m_n_malaeb/singular-value-decomposition-svd-in-recommender-systems-for-non-math-statistics-programming-4a622de653e9.

Bhattacharyya, M. (2020). Beginner’s Guide to Creating an SVD Recommender System. [online] Medium. Available at: https://towardsdatascience.com/beginners-guide-to-creating-an-svd-recommender-system-1fd7326d1f65.
