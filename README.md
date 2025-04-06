# IMDB 5000 Movie Analysis 

## 📊 SQL Queries & Visualizations

### 1. Top Grossing Movies
```sql
SELECT 
    movie_title, 
    gross - budget AS profit 
FROM movie_metadata 
WHERE gross IS NOT NULL AND budget IS NOT NULL 
ORDER BY profit DESC 
LIMIT 10;
```
### 2. Best-Rated Directors
```sql 
SELECT 
    director_name,
    AVG(imdb_score) AS avg_rating,
    COUNT(*) AS movies_directed
FROM movie_metadata
WHERE director_name IS NOT NULL
GROUP BY director_name
HAVING COUNT(*) >= 5
ORDER BY avg_rating DESC
LIMIT 10;
```

### 3. Genre Profitability
```sql
SELECT 
    genres,
    AVG(gross - budget) AS avg_profit,
    COUNT(*) AS movie_count
FROM movies
WHERE genres IS NOT NULL 
  AND budget > 0 
  AND gross > 0
GROUP BY genres
ORDER BY avg_profit DESC
LIMIT 10;
```
