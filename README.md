# Alexa, which movie would you recommend?

![Heading](https://miro.medium.com/fit/c/1838/551/1*YGlG3RmEDn3ZuS10V3rUGg.png)

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
* Feature Engineering
  1. Find out all the unique genres (Hint: split the data in column genre making a list and then process the data to find out only the unique categories of genres)
  2. Create a separate column for each genre category with a one-hot encoding ( 1 and 0) whether or not the movie belongs to that genre.
  3. Determine the features affecting the ratings of any particular movie.
* Building the models
  - Content based 
  - Collaborative based 
  - Collaborative Filtering
* Conclusion 
* References 
