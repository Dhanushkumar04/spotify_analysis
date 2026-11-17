![Spotify logo](https://github.com/Dhanushkumar04/spotify_analysis/blob/main/spotify-logo.png)

# Spotify Data Analysis Using PostgreSQL

## Project Overview

This project focuses on analyzing Spotify music data using **PostgreSQL** to explore track performance, artist popularity, album characteristics, and listener engagement across Spotify and YouTube.

The analysis uses SQL queries to extract meaningful insights from music-related data, identify highly streamed tracks, evaluate audio characteristics, and compare platform performance. It demonstrates practical SQL skills through data exploration, data cleaning, aggregation, filtering, subqueries, Common Table Expressions (CTEs), and window functions.

## Project Objectives

- Analyze music streaming data to understand track and artist performance.
- Identify tracks with more than one billion streams.
- Evaluate album characteristics such as average danceability and energy levels.
- Analyze audience engagement through views, likes, and comments.
- Compare track streaming performance across Spotify and YouTube.
- Identify top-performing tracks for each artist.
- Apply SQL techniques to solve real-world analytical questions.

## Tools & Technologies

| Tool | Purpose |
|---|---|
| PostgreSQL | Database management and SQL analysis |
| pgAdmin 4 | Database administration and query execution |
| SQL | Data exploration, cleaning, transformation, and analysis |
| Git & GitHub | Project version control and documentation |

## Dataset Description

The project uses a Spotify music dataset containing information about artists, tracks, albums, audio features, and platform engagement metrics.

The dataset includes the following columns:

| Column Name | Description |
|---|---|
| artist | Name of the artist |
| track | Name of the music track |
| album | Album associated with the track |
| album_type | Type of album, such as album or single |
| danceability | Measure of how suitable a track is for dancing |
| energy | Measure of the intensity and activity of a track |
| loudness | Overall loudness of the track |
| speechiness | Detects the presence of spoken words in a track |
| acousticness | Confidence measure of whether a track is acoustic |
| instrumentalness | Predicts whether a track contains vocals |
| liveness | Detects the presence of an audience in the recording |
| valence | Measure of the musical positivity conveyed by a track |
| tempo | Estimated tempo of the track in BPM |
| duration_min | Track duration in minutes |
| title | Video or content title |
| channel | YouTube channel associated with the track |
| views | Total video views |
| likes | Total likes received |
| comments | Total comments received |
| licensed | Indicates whether the content is licensed |
| official_video | Indicates whether the video is official |
| stream | Total streaming count |
| energy_liveness | Combined energy and liveness metric |
| most_played_on | Platform where the track is most played, such as Spotify or YouTube |

## Project Workflow

### 1. Database and Table Creation

Created a PostgreSQL database and designed a table named `spotify` to store the dataset.

The table includes artist details, track information, audio features, streaming metrics, and platform engagement data.

### 2. Data Exploration

Performed initial data exploration to understand the dataset structure, volume, and unique values.

Key operations included:

- Displaying the first five records.
- Counting the total number of records.
- Identifying the number of unique artists and albums.
- Exploring distinct album types.
- Identifying minimum and maximum track durations.
- Exploring unique YouTube channels and streaming platforms.

### 3. Data Cleaning

Identified records containing zero track duration and removed them to avoid including invalid duration values in subsequent analysis.

```sql
SELECT *
FROM spotify
WHERE duration_min = 0;

DELETE FROM spotify
WHERE duration_min = 0;
```

### 4. Business Analysis Using SQL

Developed SQL queries to answer analytical questions related to streaming performance, artist popularity, album characteristics, and platform engagement.

## Business Questions & SQL Analysis

### A. Dataset Exploration

**1. Retrieve the total number of records in the dataset.**

Used `COUNT()` to understand the dataset size.

**2. Identify the number of unique artists and albums.**

Used `COUNT(DISTINCT)` to determine the diversity of artists and albums.

**3. Explore the different types of albums available.**

Used `DISTINCT` to identify unique album categories.

**4. Find the longest and shortest tracks.**

Used `MAX()` and `MIN()` to analyze track duration.

**5. Identify distinct YouTube channels and streaming platforms.**

Used `DISTINCT` to explore the platforms and channels represented in the dataset.

### B. Track & Artist Performance Analysis

**6. Retrieve tracks that have more than one billion streams.**

Identified highly streamed tracks using conditional filtering.

**7. List all albums along with their respective artists.**

Retrieved unique album and artist combinations to understand artist-album relationships.

**8. Find all tracks belonging to the single album type.**

Used `WHERE` filtering to identify tracks categorized as singles.

**9. Calculate the total number of tracks released by each artist.**

Used `GROUP BY` and `COUNT()` to analyze artist-level track distribution.

**10. Identify the top five tracks with the highest energy values.**

Used `MAX()`, `GROUP BY`, `ORDER BY`, and `LIMIT` to identify tracks with high energy scores.

### C. Audio Features Analysis

**11. Calculate the average danceability of tracks in each album.**

Used `AVG()` and `GROUP BY` to evaluate the average danceability score across albums.

**12. Retrieve tracks with liveness scores above the overall average.**

Used a subquery with `AVG()` to identify tracks whose liveness scores exceed the dataset average.

**13. Calculate the difference between the highest and lowest energy values for each album.**

Used a Common Table Expression (CTE) with `MAX()` and `MIN()` to calculate the energy range for every album.

### D. Audience Engagement Analysis

**14. Calculate the total number of comments received by licensed tracks.**

Used `SUM()` with a conditional filter to analyze comments on licensed content.

**15. Retrieve tracks with official videos along with their total views and likes.**

Used filtering and aggregation to evaluate engagement on official videos.

**16. Calculate the total views associated with tracks in each album.**

Used `SUM()` and grouping to analyze album-level video views.

### E. Platform Performance Comparison

**17. Identify tracks that have received more streams on Spotify than YouTube.**

Used conditional aggregation with `CASE WHEN` and `COALESCE()` to compare streaming counts across platforms.

The analysis also filters out tracks with zero YouTube streams to focus on tracks with comparable platform data.

### F. Advanced SQL Analysis

**18. Identify the top three most-viewed tracks for each artist.**

Used the `DENSE_RANK()` window function with `PARTITION BY` to rank tracks based on total views within each artist.

This approach helps identify the best-performing tracks for every artist rather than only returning the top three tracks overall.

## SQL Concepts Applied

The project demonstrates the following PostgreSQL concepts:

| SQL Concept | Application |
|---|---|
| CREATE TABLE | Creating the Spotify dataset table |
| DROP TABLE IF EXISTS | Managing table creation safely |
| SELECT | Retrieving records |
| DISTINCT | Identifying unique values |
| WHERE | Filtering records based on conditions |
| ILIKE | Case-insensitive text matching |
| ORDER BY | Sorting analytical results |
| GROUP BY | Performing grouped analysis |
| COUNT() | Counting records and unique values |
| SUM() | Calculating total streams, views, likes, and comments |
| AVG() | Calculating average audio feature values |
| MIN() and MAX() | Finding minimum and maximum values |
| CASE WHEN | Performing conditional aggregation |
| COALESCE() | Handling NULL values in calculations |
| Subqueries | Comparing individual values against overall averages |
| Common Table Expressions (CTEs) | Organizing complex analytical queries |
| Window Functions | Ranking tracks within individual artists |
| DENSE_RANK() | Identifying top-performing tracks by artist |
| DELETE | Removing invalid records |

## Key Analytical Outcomes

The SQL analysis enables the following insights:

- Identifies highly streamed tracks that have crossed one billion streams.
- Reveals artist-level track distribution and album information.
- Highlights albums with higher average danceability and varying energy levels.
- Identifies tracks with above-average liveness scores.
- Evaluates engagement on official music videos using views and likes.
- Measures audience interaction through comments on licensed tracks.
- Compares streaming performance between Spotify and YouTube.
- Ranks the top three most-viewed tracks for each artist.

*Note: These are the analytical outcomes supported by the queries. Specific numerical findings should be added after reviewing the actual query results.*

## Key Learnings

Through this project, I gained practical experience in:

- Working with structured datasets in PostgreSQL.
- Writing SQL queries to solve business-oriented analytical questions.
- Cleaning datasets by identifying and handling invalid records.
- Performing aggregations to understand track and artist performance.
- Analyzing audio features and audience engagement metrics.
- Comparing platform-level performance using conditional aggregation.
- Applying CTEs, subqueries, and window functions to solve advanced SQL problems.
- Translating raw data into meaningful analytical insights.

## Project Structure

```text
Spotify-Data-Analysis/
│
├── Dataset/
│   └── spotify.csv
│
├── SQL/
│   └── spotify_analysis.sql
│
└── README.md
```

*The folder and file names above are a suggested structure. Update them to match the actual files in your GitHub repository.*

## How to Run the Project

Follow these steps to reproduce the analysis:

1. Install PostgreSQL and pgAdmin 4.
2. Create a new database in PostgreSQL.
3. Download or clone this GitHub repository.
4. Import the Spotify dataset into PostgreSQL.
5. Execute the table creation script.
6. Run the SQL queries in sequence to perform data exploration, cleaning, and analysis.
7. Review the query outputs to understand the findings.

## Conclusion

This project demonstrates my ability to use PostgreSQL to explore, clean, and analyze real-world music streaming data. By working through business-oriented SQL questions, I developed a better understanding of track performance, artist popularity, audio characteristics, and audience engagement across digital platforms.

It strengthened my practical SQL skills, particularly in data aggregation, conditional analysis, CTEs, subqueries, and window functions, while helping me develop an analytical approach to solving data-driven problems.

## Author

**Dhanush Kumar**

Aspiring Data Analyst | PostgreSQL | SQL | Python | Power BI

GitHub: [Dhanushkumar04](https://github.com/Dhanushkumar04)
