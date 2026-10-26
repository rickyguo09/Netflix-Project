# Netflix Content Analysis using SQL & Excel

## Overview
This project analyzes a dataset of Netflix movies and television shows to extract insights on IMDB/TMDB ratings, genre popularity, and release decades using DB Browser for SQLite. 
The raw dataset file ([titles.csv](titles.csv) used for this analysis are uploaded in this repository for reference.
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
SELECT title, 
type, 
imdb_score
FROM titles
WHERE imdb_score >= 8.0
AND type = 'MOVIE'
ORDER BY imdb_score DESC
LIMIT 10;
```
Result:
<img width="450" height="292" alt="image" src="https://github.com/user-attachments/assets/e59186e3-ca60-4d61-8fd6-aaccbaca2246" />

- Top 10 Shows
```SQLite
SELECT title, 
type, 
imdb_score
FROM titles
WHERE imdb_score >= 8.0
AND type = 'SHOW'
ORDER BY imdb_score DESC
LIMIT 10;
```
Result: 
<img width="350" height="289" alt="image" src="https://github.com/user-attachments/assets/f577e684-ab9e-4f04-a8d6-cfbb025c4c5c" />

- Bottom 10 Movies
```SQLite
SELECT title, 
type, 
imdb_score
FROM titles
WHERE type = 'MOVIE'
AND imdb_score IS NOT NULL
ORDER BY imdb_score ASC
LIMIT 10;
```
Result: 
<img width="425" height="281" alt="image" src="https://github.com/user-attachments/assets/81b23ded-d3e1-4d71-a5ab-be79ad413147" />

- Bottom 10 Shows
```SQLite
SELECT title, 
type, 
imdb_score
FROM titles
WHERE type = 'SHOW'
AND imdb_score IS NOT NULL
ORDER BY imdb_score ASC
LIMIT 10;
```
Result: 
<img width="408" height="280" alt="image" src="https://github.com/user-attachments/assets/b344a620-12c4-4c40-8a03-26ad8497ba20" />

## 2. What were the average IMDB and TMDB scores for shows and movies? 
```SQLite
SELECT DISTINCT type, 
ROUND(AVG(imdb_score),2) AS avg_imdb_score,
ROUND(AVG(tmdb_score),2) as avg_tmdb_score
FROM titles
GROUP BY type;
```
Result: 
<img width="267" height="74" alt="image" src="https://github.com/user-attachments/assets/4fcfffe2-4cea-42f4-90f6-0274df527887" />

## 3. How many movies and shows fall in each decade in Netflix's library?
```SQLite
SELECT CONCAT(FLOOR(release_year / 10) * 10, 's') AS decade,
	COUNT(*) AS movies_shows_count
FROM titles
WHERE release_year >= 1940
GROUP BY CONCAT(FLOOR(release_year / 10) * 10, 's')
ORDER BY decade;
```
Result: 
<img width="192" height="262" alt="image" src="https://github.com/user-attachments/assets/d143662c-d926-4c0f-ae95-a47476c19118" />

## 4. What were the average IMDB and TMDB scores for each age certification
```SQLite
SELECT DISTINCT age_certification, 
ROUND(AVG(imdb_score),2) AS avg_imdb_score,
ROUND(AVG(tmdb_score),2) AS avg_tmdb_score
FROM titles
GROUP BY age_certification
ORDER BY avg_imdb_score DESC;
```
Result: 
<img width="333" height="338" alt="image" src="https://github.com/user-attachments/assets/fe9eef79-e762-4f87-8963-f66752e9ce58" />

## 5. What were the 5 most common age certifications for movies?
```SQLite
SELECT age_certification, 
COUNT(*) AS certification_count
FROM titles
WHERE type = 'MOVIE' 
AND age_certification != 'N/A'
GROUP BY age_certification
ORDER BY certification_count DESC
LIMIT 5;
```
Result:
<img width="240" height="165" alt="image" src="https://github.com/user-attachments/assets/e55cd454-ac72-4b32-bbb1-02dfd6b3f1be" />


