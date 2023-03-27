## Project Overview  

#### The following is an exploration of a dataset on Netflix titles between 2008 to 2019. I load the dataset into an ipynb and perform some EDA and visualisations on it.  

Dataset file: [netflix titles dataset](netflix_titles.csv)  
Python notebook: [EDA Notebook](netflix.ipynb)  

## Metadata  
The dataset has 12 columns with 1 column being a unique identifier, and the remaining columns pertaining to a Netflix title as follows:  

type: movie/tv series  
title: title of the Netflix show  
director: director name of the title  
cast: cast involved in the title   
country: country that published the title   
date_added: date the title was added to Netflix  
release_year: the title's year of release  
rating: US's TV Parental Guidelines rating system, i.e. TV-PG, TV-MA, R, etc.  
duration: duration of the title in minutes/seasons  
listed_in: genres the title falls under  
description: a short description of the title  

## Data Cleaning/Exploration/Visualisation
There are some null values. I look to clean them up before exploring/visualizing.    
![Null Values](imgs/null_values.png)  

### Duration:  
Before:  
![Duration](imgs/null_duration_before.png)    
I take the rating column values and replace the missing values in duration, and set the rating values to null.  
After:  
![Duration after imputation](imgs/null_duration_after.png)

We note that duration across the <ins>type</ins> column differs between Movies and TV Shows:  
![Duration distribution](imgs/duration_distribution.png)  

Title by type:   
![Type distribution](imgs/movie_tv_show_distribution.png)  

#### Movie duration distribution  
![Duration movie distribution](imgs/duration_movie_distribution.png)  
The most common duration for movies are within 90-100 minutes.  

#### TV Show duration distribution  
![Duration TV show distribution](imgs/duration_tv_distribution.png)  
Most TV shows have only 1 Season.  

### Ratings
![Null Values](imgs/null_values.png)   
We note the 4 null values + 3 additional rows from cleaning the duration column up earlier.  
![Titles by Rating](imgs/rating_before.png)  
As there are many ratings, we categorize them into simpler forms according to the Netflix's guidelines at https://help.netflix.com/en/node/2064/us:  

Kids  
TV-Y: Designed to be appropriate for all children  
TV-Y7: Suitable for ages 7 and up  
G: Suitable for General Audiences  
TV-G: Suitable for General Audiences  
PG: Parental Guidance suggested  
TV-PG: Parental Guidance suggested  

Teens    
PG-13: Parents strongly cautioned. May be Inappropriate for ages 12 and under.  
TV-14: Parents strongly cautioned. May not be suitable for ages 14 and under.  
  
Adults  
R: Restricted. May be inappropriate for ages 17 and under.  
TV-MA: For Mature Audiences. May not be suitable for ages 17 and under.  
NC-17: Inappropriate for ages 17 and under  

Zip to Dictionary and Map to Dataframe column  
![Zip/Map](imgs/zip_dictionary_map.png)  

#### Ratings after categorizing  
![New Ratings](imgs/rating_after.png)    
About 23% of shows on Netflix are for Children, (30+23)% to Teenagers, and (47+30+23)% to Adults.  

#### Rating by title type    
![Rating by type](imgs/rating_by_type.png)      
Adult Movies are 48% of all movies in Netflix, followed by 31% being Teenager movies, and lastly 21% being Children movies.  
Adult TV Shows are 43% of all TV shows in Netflix, followed by 29% being Teenager TV shows, and lastly 27% being Children TV shows.  


### Genres
Genres are grouped together for each title.
![Genres being grouped together](imgs/genre_grouping.png)      

Expand the grouped up genres per row into individual rows for each genre associated with each title.    
Look at all unique genres.    
![Unique Genres](imgs/unique_genre_after_expand.png)  
There are overlapping genres, i.e. ('Movies', 'Horror Movies') but this is how Netflix has classified them so we will leave it be  

#### Genre distribution across all titles (Movies & TV Shows)    
![Genre Distribution All](imgs/genre_distribution.png)  
International content, Dramas and Comedies are the most popular genres of content on Netflix.  
Movies and TV Shows have their own respective genres, i.e Romantic Movies, Romantic TV Shows, so I will be exploring them by their type next.  

#### Rating Category by Movies  
![Rating category by Movie type](imgs/rating_movie_norm.png)  
  
#### Rating Category by TV Shows  
![Rating category by TV Show type All](imgs/rating_tv_norm.png)  

TV Shows have a higher weightage in the Kids rating_category as compared to Movies.  
But since genres can overlap for a single TV show/Movie, we should look at the genre numbers against the total number of TV shows/movies for a more accurate representation of the genre distribution.  

#### Kids Rating Category by TV Show Genres  
![TV Show Genres in Kids Category Rating](imgs/kid_category_TV_genres.png)  
About 57% of TV Shows with rating_category: "Kids" are of the "Kids' TV" genre.  
TV Comedies, International TV Shows, Docuseries follow after with only about half as many shows as the Kids' TV genre.  
<br>
These may not be genres that have a high appeal factor to children although they have been categorically rated as "Kids" TV Shows in the rating_category column. It could just mean that it is safe for Children to watch.  
<br>
However, as the genres are rather generic sounding, it is hard to ascertain that they definitely do not appeal to children, e.g. "International TV Shows" could also refer to a highly rated/popular children's show in another country.  
<br>
Under the assumption that these shows rated "Children" solely mean that they are safe for children to watch, only 57% of 789 TV Shows are meant to appeal to Netflix children audiences, which is not a very wide variety of shows.  

#### Kids Rating Category by Movie Genres  
![Movie Genres in Kids Category Rating](imgs/kid_category_Movies_genres.png)  
About 50% of movies with rating_category = 'Kids' are of the Children & Family Movies genre.  
This means about 50-57% of tv shows/movies under rating_category = 'Kids' are definitively meant to appeal to Children viewers.  

This number would amount to:  
(1269 x 50%)Movies + (789 x 57%)TV Shows = 1092~ netflix children content.  
Out of 8807 total netflix content, 12.39% is truly targeted at children.  

#### 
![TV Show Genres in Teens Category Rating](imgs/kid_category_TV_genres.png)  

![Movie Genres in Teens Category Rating](imgs/kid_category_Movies_genres.png)  



































### Visitor count per museum by date from Jan 2014 to Nov 2018    
![Visitor count before imputation](imgs/visitor_count_per_museum_before_impute.png)    
Notice the visitor count for Firehouse Museum in Sep 2014 is particularly high. Under the assumption the visitor count is incorrectly recorded and not the result of any event/season/marketing effort, I imputed the visitor count for Firehouse Museum in September 2014.    
<br>  
__Assessing the seasonality of the Firehouse Museum visitors across the years.__  
![Firehouse Museum annual visitors](imgs/firehouse_museum_annual_visitors.png)  
Although there is doesn't seem to be a consistent pattern for visitors in September each year, looking at the average of June to August for each year could be a decent approximation of September's visitor numbers.  
Years 2016 and 2017 have September's visitor count at the end of a downtrend whereas for 2015 and 2018, the visitor count ticks upwards. With heavier emphasis on 2015 for being more recent to 2014 as compared to other years, I simply used the mean visitors of June to August.  




