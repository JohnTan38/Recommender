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

* Conclusion 
* References 
