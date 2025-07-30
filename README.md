# 🎧 Spotify Advanced SQL Analysis & Query Optimization
Project Category : Advanced
[Click Here to get Dataset](https://www.kaggle.com/datasets/sanjanchaudhari/spotify-dataset)

![Spotify Logo](https://github.com/sneha102/spotify_project/blob/main/spotify_logo.jpg)

## Overview
This project focuses on advanced SQL practice using a real-world Spotify dataset containing track-level metadata such as artist, album, danceability, streams, and views. The dataset was originally denormalized, and this project walks through:

- Normalizing the dataset into a structured SQL schema
- Writing SQL queries categorized into easy, medium, and advanced levels
- Optimizing SQL query performance using indexing and EXPLAIN
- Drawing actionable insights using aggregate and analytical functions

## Schema

```sql
-- create table
DROP TABLE IF EXISTS spotify;
CREATE TABLE spotify (
    artist VARCHAR(255),
    track VARCHAR(255),
    album VARCHAR(255),
    album_type VARCHAR(50),
    danceability FLOAT,
    energy FLOAT,
    loudness FLOAT,
    speechiness FLOAT,
    acousticness FLOAT,
    instrumentalness FLOAT,
    liveness FLOAT,
    valence FLOAT,
    tempo FLOAT,
    duration_min FLOAT,
    title VARCHAR(255),
    channel VARCHAR(255),
    views FLOAT,
    likes BIGINT,
    comments BIGINT,
    licensed BOOLEAN,
    official_video BOOLEAN,
    stream BIGINT,
    energy_liveness FLOAT,
    most_played_on VARCHAR(50)
);
```

## Project Steps

### 1. Data Exploration
Before diving into SQL, it’s important to understand the dataset thoroughly. The dataset contains attributes such as:
- `Artist`: The performer of the track.
- `Track`: The name of the song.
- `Album`: The album to which the track belongs.
- `Album_type`: The type of album (e.g., single or album).
- Various metrics such as `danceability`, `energy`, `loudness`, `tempo`, and more.

### 2. Quering The Data
After the data is inserted, various SQL queries can be written to explore and analyze the data. Queries are categorized into **easy**, **medium**, and **advanced** levels to help progressively develop SQL proficiency.

#### Easy Queries
- Simple data retrieval, filtering, and basic aggregations.
  
#### Medium Queries
- More complex queries involving grouping, aggregation functions, and joins.
  
#### Advanced Queries
- Nested subqueries, window functions, CTEs, and performance optimization.

## 3. Practice Questions

### Easy Level
1. Retrieve the names of all tracks that have more than 1 billion streams.
2. List all albums along with their respective artists.
3. Get the total number of comments for tracks where `licensed = TRUE`.
4. Find all tracks that belong to the album type `single`.
5. Count the total number of tracks by each artist.

### Medium Level
1. Calculate the average danceability of tracks in each album.
2. Find the top 5 tracks with the highest energy values.
3. List all tracks along with their views and likes where `official_video = TRUE`.
4. For each album, calculate the total views of all associated tracks.
5. Retrieve the track names that have been streamed on Spotify more than YouTube.

### Advanced Level
1. Find the top 3 most-viewed tracks for each artist using window functions.
2. Write a query to find tracks where the liveness score is above the average.
3. **Use a `WITH` clause to calculate the difference between the highest and lowest energy values for tracks in each album.**

```sql
WITH cte
AS
(SELECT 
	album,
	MAX(energy) as highest_energy,
	MIN(energy) as lowest_energery
FROM spotify
GROUP BY 1
)
SELECT 
	album,
	highest_energy - lowest_energery as energy_diff
FROM cte
ORDER BY 2 DESC
```

## ⚙️ How to Run the Project

1. Clone the repo and download the dataset from Kaggle
2. Set up PostgreSQL and pgAdmin
3. Run the table creation SQL
4. Import data manually or using scripts
5. Execute practice queries
6. Analyze performance and optimize

## Next Steps

- Build Power BI or Tableau Dashboards from final query outputs
- Expand dataset with more tracks and artists for scalability testing
- Write stored procedures for reusable logic
- Optimize more complex joins and window functions

## Findings and Conclusions
After running extensive SQL queries on the Spotify dataset and analyzing metrics such as streams, views, likes, energy, danceability, and more, the following key insights were observed:

### Key Findings
- **High Stream Count Patterns:** Tracks that exceeded 1 billion streams typically had a high danceability score and belonged to popular artists with a consistent brand presence across multiple platforms.
- **Singles Dominate Engagement:** Tracks from album_type = 'single' showed higher average streams and likes compared to full-length albums, indicating strong audience preference for short-form content.
- **Energy and Liveness Trends:**
1. Albums with a high energy range (difference between max and min energy values) often showed genre diversity.
2. Tracks with above-average liveness were frequently live performances or audience-driven tracks, which saw higher engagement.
- **Video Impact:** Tracks with official_video = TRUE gained significantly more views and likes on YouTube, confirming the impact of video presence on visibility.
- **Spotify vs YouTube Disparity:** Several tracks performed better on Spotify in terms of streams than on YouTube views—highlighting platform-based audience behavior.

### 📫 Let's Connect on [LinkedIn](https://www.linkedin.com/in/sneha-gawde)





