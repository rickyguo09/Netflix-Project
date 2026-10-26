# Netflix-Project
# Netflix Content Analysis using SQL & Excel

## Overview
This project analyzes a dataset of Netflix movies and television shows to extract insights on IMDB/TMDB ratings, genre popularity, and release decades using DB Browser for SQLite. 

## Skills Applied
- Relational Database Management
- Complex SQL Queries (JOINs, GROUP BY, Aggregate Functions)
- Data Cleaning and Formatting

## Key Insights
- Content Volume Exploded in the 2010s: The amount of content on the platform grew exponentially over time, jumping from just 121 titles in the 1990s to a massive peak of 3,304 titles in the 2010s.
- Shows Outperform Movies in Ratings: On average, television shows receive higher ratings than movies across both review platforms. Shows average a 6.98 on IMDB and 7.48 on TMDB, whereas movies average 6.25 on IMDB and 6.46 on TMDB.
- Top Titles Peak Above 9.0: The highest-rated show in the dataset is #ABtalks with a 9.6 IMDB score, edging out heavy hitters like Breaking Bad (9.5). The top-rated movies are Chhota Bheem & Krishna vs Zimbara and Major, which both hold a 9.1 IMDB score.
- Teen and Mature TV Ratings Score the Highest: When looking at average IMDB scores by age certification, 'TV-14' (7.22) and 'TV-MA' (7.02) are the highest-rated categories. Conversely, the strictly adult movie rating 'NC-17' has the lowest average IMDB score at 6.15.

  ## Questions I Wanted To Answer From the Dataset:

## 1. Which movies and shows on Netflix ranked in the top 10 and bottom 10 based on their IMDB scores?
- Top 10 Movies
```SQLite
