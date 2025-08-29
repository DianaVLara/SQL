# For this project, I downloaded Spotify data from Kaggle.
# Then I created a table to insert Spotify data into.
# Finally, I performed analytics on the data using SQL. 

#Creating the table: 
CREATE TABLE BIT_DB.Spotifydata (
id integer PRIMARY KEY,
artist_name varchar NOT NULL,
track_name varchar NOT NULL,
track_id varchar NOT NULL,
popularity integer NOT NULL,
danceability decimal(4,3) NOT NULL,
energy decimal(4,3) NOT NULL,
key integer NOT NULL,
loudness decimal(5,3) NOT NULL,
mode integer NOT NULL,
speechiness decimal(5,4) NOT NULL,
acousticness decimal(6,5) NOT NULL,
instrumentalness text NOT NULL,
liveness decimal(5,4) NOT NULL,
valence decimal(4,3) NOT NULL,
tempo decimal(6,3) NOT NULL,
duration_ms integer NOT NULL,
time_signature integer NOT NULL 
)

#Then I inserted the Spotify Data .csv into the table.

#Next, I explored the data using the following SQL. 


#1. Get a visual of the columns and data for this table.
SELECT * FROM Spotifydata;

#2. What is the average danceability by artist? 
SELECT artist_name, AVG(danceability)
FROM Spotifydata
GROUP BY artist_name
ORDER BY AVG(danceability) DESC
LIMIT 10;

#3. Who are the top 10 artists based on popularity?
SELECT artist_name, AVG(Popularity)
FROM Spotifydata
GROUP BY artist_name
ORDER BY AVG(Popularity) DESC
LIMIT 10;

#4. What artist released the longest song?
SELECT artist_name, duration_ms
 FROM Spotifydata
 ORDER BY duration_ms DESC
 LIMIT 1;
 
#5. What's the average danceability for the 10 most popular songs?
SELECT AVG(danceability) 
FROM Spotifydata
WHERE id>=1
AND id<=10;

#6. Which top 5 artists appear more frequently? 
SELECT artist_name, COUNT(artist_name) as frequency
FROM Spotifydata
GROUP BY artist_name
ORDER BY frequency DESC 
LIMIT 5;

#7. Which artist has on average the shortest songs?
SELECT artist_name, AVG(duration_ms)
FROM Spotifydata
GROUP BY artist_name
ORDER BY AVG(duration_ms) ASC 
LIMIT 10;

#8. Are shorter or longer songs more popuar?
SELECT 
   CASE 
      WHEN duration_ms < 150000 THEN '< 2.5 min'
      WHEN duration_ms BETWEEN 150000 AND 210000 THEN '2.5–3.5 min'
      WHEN duration_ms BETWEEN 210001 AND 270000 THEN '3.5–4.5 min'
      ELSE '> 4.5 min'
   END AS length_category,
   AVG(popularity) AS avg_popularity,
   COUNT(*) AS num_songs
FROM Spotifydata
GROUP BY length_category
ORDER BY avg_popularity DESC;

#9. What are the top 10 most popular tracks and by which artists?
SELECT track_name, artist_name, popularity
FROM spotifydata
ORDER BY popularity DESC
LIMIT 10;
