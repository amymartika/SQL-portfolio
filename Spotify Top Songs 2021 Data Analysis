--Dataset: Spotify top 50 songs in 2021
--Source: Kaggle https://www.kaggle.com/datasets/equinxx/spotify-top-50-songs-in-2021
--Queried using: SQLite 3

SELECT * FROM BIT_DB.Spotifydata;

--What is the average danceability by artist? 
SELECT 
    artist_name, 
    ROUND(avg(danceability), 3) as average_danceability
FROM BIT_DB.Spotifydata
GROUP BY artist_name
ORDER BY average_danceability DESC; 

--Who are the top 10 artists based on popularity, and what are their tracks' average danceability and energy?
SELECT
    artist_name,
    ROUND(avg(popularity), 3) AS average_popularity,
    ROUND(avg(danceability), 3) AS average_danceability,
    ROUND(avg(energy), 3) AS average_energy
FROM BIT_DB.spotifydata
GROUP BY artist_name 
ORDER BY average_popularity DESC
LIMIT 10;

--What artist released the longest song?
SELECT 
    artist_name,
    track_name, 
    duration_ms
FROM BIT_DB.Spotifydata
ORDER BY duration_ms DESC
LIMIT 1;

--What is the average danceability of the top 12 most popular songs?
--I'm selecting the top 12 because songs 9-12 share the same popularity score.
SELECT  
    AVG(danceability) AS average_danceability
FROM BIT_DB.Spotifydata
WHERE popularity >= 92;

--In what key is each track from the dataset?
--Using pitch-class integer notation: https://smbutterfield.github.io/ibmt17-18/22-intro-to-non-diatonic-materials/b2-tx-pcintnotation.html
SELECT
    track_name,
    artist_name,
    CASE
        WHEN song_key = 0 AND song_mode = 1 THEN 'C Major'
        WHEN song_key = 0 AND song_mode = 0 THEN 'C Minor'
        WHEN song_key = 1 AND song_mode = 1 THEN 'C#/Db Major'
        WHEN song_key = 1 AND song_mode = 0 THEN 'C#/Db Minor'
        WHEN song_key = 2 AND song_mode = 1 THEN 'D Major'
        WHEN song_key = 2 AND song_mode = 0 THEN 'D Minor'
        WHEN song_key = 3 AND song_mode = 1 THEN 'D#/Eb Major'
        WHEN song_key = 3 AND song_mode = 0 THEN 'D#/Eb Minor'
        WHEN song_key = 4 AND song_mode = 1 THEN 'E Major'
        WHEN song_key = 4 AND song_mode = 0 THEN 'E Minor'
        WHEN song_key = 5 AND song_mode = 1 THEN 'F Major'
        WHEN song_key = 5 AND song_mode = 0 THEN 'F Minor'
        WHEN song_key = 6 AND song_mode = 1 THEN 'F#/Gb Major'
        WHEN song_key = 6 AND song_mode = 0 THEN 'F#/Gb Minor'
        WHEN song_key = 7 AND song_mode = 1 THEN 'G Major'
        WHEN song_key = 7 AND song_mode = 0 THEN 'G Minor'
        WHEN song_key = 8 AND song_mode = 1 THEN 'G#/Ab Major'
        WHEN song_key = 8 AND song_mode = 0 THEN 'G#/Ab Minor'
        WHEN song_key = 9 AND song_mode = 1 THEN 'A Major'
        WHEN song_key = 9 AND song_mode = 0 THEN 'A Minor'
        WHEN song_key = 10 AND song_mode = 1 THEN 'A#/Bb Major'
        WHEN song_key = 10 AND song_mode = 0 THEN 'A#/Bb Minor'
        WHEN song_key = 11 AND song_mode = 1 THEN 'B Major'
        WHEN song_key = 11 AND song_mode = 0 THEN 'B Minor'
    END AS key
FROM BIT_DB.Spotifydata
ORDER BY key;

--What are the most common song keys for the 12 most popular songs?
--Using pitch-class integer notation: https://smbutterfield.github.io/ibmt17-18/22-intro-to-non-diatonic-materials/b2-tx-pcintnotation.html
--Note: The 9th-12th most popular songs share the same popularity score.
SELECT
    COUNT(*) AS total,
    CASE
        WHEN song_key = 0 AND song_mode = 1 THEN 'C Major'
        WHEN song_key = 0 AND song_mode = 0 THEN 'C Minor'
        WHEN song_key = 1 AND song_mode = 1 THEN 'C#/Db Major'
        WHEN song_key = 1 AND song_mode = 0 THEN 'C#/Db Minor'
        WHEN song_key = 2 AND song_mode = 1 THEN 'D Major'
        WHEN song_key = 2 AND song_mode = 0 THEN 'D Minor'
        WHEN song_key = 3 AND song_mode = 1 THEN 'D#/Eb Major'
        WHEN song_key = 3 AND song_mode = 0 THEN 'D#/Eb Minor'
        WHEN song_key = 4 AND song_mode = 1 THEN 'E Major'
        WHEN song_key = 4 AND song_mode = 0 THEN 'E Minor'
        WHEN song_key = 5 AND song_mode = 1 THEN 'F Major'
        WHEN song_key = 5 AND song_mode = 0 THEN 'F Minor'
        WHEN song_key = 6 AND song_mode = 1 THEN 'F#/Gb Major'
        WHEN song_key = 6 AND song_mode = 0 THEN 'F#/Gb Minor'
        WHEN song_key = 7 AND song_mode = 1 THEN 'G Major'
        WHEN song_key = 7 AND song_mode = 0 THEN 'G Minor'
        WHEN song_key = 8 AND song_mode = 1 THEN 'G#/Ab Major'
        WHEN song_key = 8 AND song_mode = 0 THEN 'G#/Ab Minor'
        WHEN song_key = 9 AND song_mode = 1 THEN 'A Major'
        WHEN song_key = 9 AND song_mode = 0 THEN 'A Minor'
        WHEN song_key = 10 AND song_mode = 1 THEN 'A#/Bb Major'
        WHEN song_key = 10 AND song_mode = 0 THEN 'A#/Bb Minor'
        WHEN song_key = 11 AND song_mode = 1 THEN 'B Major'
        WHEN song_key = 11 AND song_mode = 0 THEN 'B Minor'
    END AS key
FROM BIT_DB.Spotifydata
WHERE popularity >= 92
GROUP BY key
ORDER BY total DESC
LIMIT 2;

--What are the most common song keys for the entire dataset?
--Using pitch-class integer notation: https://smbutterfield.github.io/ibmt17-18/22-intro-to-non-diatonic-materials/b2-tx-pcintnotation.html
SELECT
    COUNT(*) AS total,
    CASE
        WHEN song_key = 0 AND song_mode = 1 THEN 'C Major'
        WHEN song_key = 0 AND song_mode = 0 THEN 'C Minor'
        WHEN song_key = 1 AND song_mode = 1 THEN 'C#/Db Major'
        WHEN song_key = 1 AND song_mode = 0 THEN 'C#/Db Minor'
        WHEN song_key = 2 AND song_mode = 1 THEN 'D Major'
        WHEN song_key = 2 AND song_mode = 0 THEN 'D Minor'
        WHEN song_key = 3 AND song_mode = 1 THEN 'D#/Eb Major'
        WHEN song_key = 3 AND song_mode = 0 THEN 'D#/Eb Minor'
        WHEN song_key = 4 AND song_mode = 1 THEN 'E Major'
        WHEN song_key = 4 AND song_mode = 0 THEN 'E Minor'
        WHEN song_key = 5 AND song_mode = 1 THEN 'F Major'
        WHEN song_key = 5 AND song_mode = 0 THEN 'F Minor'
        WHEN song_key = 6 AND song_mode = 1 THEN 'F#/Gb Major'
        WHEN song_key = 6 AND song_mode = 0 THEN 'F#/Gb Minor'
        WHEN song_key = 7 AND song_mode = 1 THEN 'G Major'
        WHEN song_key = 7 AND song_mode = 0 THEN 'G Minor'
        WHEN song_key = 8 AND song_mode = 1 THEN 'G#/Ab Major'
        WHEN song_key = 8 AND song_mode = 0 THEN 'G#/Ab Minor'
        WHEN song_key = 9 AND song_mode = 1 THEN 'A Major'
        WHEN song_key = 9 AND song_mode = 0 THEN 'A Minor'
        WHEN song_key = 10 AND song_mode = 1 THEN 'A#/Bb Major'
        WHEN song_key = 10 AND song_mode = 0 THEN 'A#/Bb Minor'
        WHEN song_key = 11 AND song_mode = 1 THEN 'B Major'
        WHEN song_key = 11 AND song_mode = 0 THEN 'B Minor'
        ELSE 'No key detected'
    END AS key
FROM BIT_DB.Spotifydata
GROUP BY key
HAVING total >= 3
ORDER BY total DESC;

--Create a table with the popularity rankings for each song key.
--Using song keys ranked by popularity database: https://www.hooktheory.com/cheat-sheet/key-popularity
CREATE TABLE BIT_DB.PopularSongKeys (
    id integer PRIMARY KEY,
    song_key varchar NOT NULL,
    popularity integer NOT NULL );

INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('C Major', 1);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('C Minor', 8);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('C#/Db Major', 17);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('C#/Db Minor', 20);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('D Major', 2);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('D Minor', 10);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('D#/Eb Major', 11);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('D#/Eb Minor', 21);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('E Major', 5);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('E Minor', 9);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('F Major', 7);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('F Minor', 16);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('F#/Gb Major', 18);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('F#/Gb Minor', 15);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('G Major', 3);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('G Minor', 12);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('G#/Ab Major', 22);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('G#/Ab Minor', 24);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('A Major', 4);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('A Minor', 6);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('A#/Bb Major', 13);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('A#/Bb Minor', 23);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('B Major', 19);
INSERT INTO BIT_DB.PopularSongKeys (song_key, popularity)
VALUES ('B Minor', 14);

--Rank the song keys in the dataset by popularity.
SELECT 
    song_key,
    popularity
FROM BIT_DB.PopularSongKeys
ORDER BY popularity ASC;

--Create column combining song key and mode in a more readable way
ALTER TABLE BIT_DB.Spotifydata
ADD tonality varchar;

--Add data for new tonality column
UPDATE BIT_DB.Spotifydata
SET tonality = 'A Major'
WHERE id = 4;

UPDATE BIT_DB.Spotifydata
SET tonality = 'A Minor'
WHERE id = 44;

UPDATE BIT_DB.Spotifydata
SET tonality = 'A#/Bb Major'
WHERE id
IN (1, 38);

UPDATE BIT_DB.Spotifydata
SET tonality = 'A#/Bb Minor'
WHERE id = 13;

UPDATE BIT_DB.Spotifydata
SET tonality = 'B Major'
WHERE id 
IN (9, 37);

UPDATE BIT_DB.Spotifydata
SET tonality = 'B Minor'
WHERE id
IN (10, 14, 26, 41);

UPDATE BIT_DB.Spotifydata
SET tonality = 'C Major'
WHERE id
IN (6, 15, 24, 27, 28, 31, 48);

UPDATE BIT_DB.Spotifydata
SET tonality = 'C#/Db Major'
WHERE id
IN (3, 8, 23, 32, 34, 40);

UPDATE BIT_DB.Spotifydata
SET tonality = 'C#/Db Minor'
WHERE id
IN (42, 45);

UPDATE BIT_DB.Spotifydata
SET tonality = 'D Major'
WHERE id
IN (18, 25);

UPDATE BIT_DB.Spotifydata
SET tonality = 'D#/Eb Major'
WHERE id = 29;

UPDATE BIT_DB.Spotifydata
SET tonality = 'D#/Eb Minor'
WHERE id = 19;

UPDATE BIT_DB.Spotifydata
SET tonality = 'E Major'
WHERE id = 49;

UPDATE BIT_DB.Spotifydata
SET tonality = 'E Minor'
WHERE id
IN (11, 12, 50);

UPDATE BIT_DB.Spotifydata
SET tonality = 'F Major'
WHERE id = 17;

UPDATE BIT_DB.Spotifydata
SET tonality = 'F Minor'
WHERE id = 43;

UPDATE BIT_DB.Spotifydata
SET tonality = 'F#/Gb Major'
WHERE id = 35;

UPDATE BIT_DB.Spotifydata
SET tonality = 'F#/Gb Minor'
WHERE id
IN (5, 22, 39);

UPDATE BIT_DB.Spotifydata
SET tonality = 'G Major'
WHERE id
IN (30, 36);

UPDATE BIT_DB.Spotifydata
SET tonality = 'G Minor'
WHERE id = 20;

UPDATE BIT_DB.Spotifydata
SET tonality = 'G#/Ab Major'
WHERE id
IN (7, 16, 33, 46, 47);

UPDATE BIT_DB.Spotifydata
SET tonality = 'G#/Ab Minor'
WHERE id
IN (2, 21);

--Compare the most popular song keys with song keys most represented in the top 50 tracks of 2021.
SELECT 
    COUNT(top_tracks.track_name) AS total,
    top_tracks.tonality,
    popular_keys.popularity AS popular_song_keys
FROM BIT_DB.Spotifydata AS top_tracks
LEFT JOIN BIT_DB.PopularSongKeys AS popular_keys
ON top_tracks.tonality = popular_keys.song_key
GROUP BY top_tracks.tonality
ORDER BY total DESC;

--Calculate the average popularity for the artists in the Spotify data table. Then, for every artist with an average popularity of 90 or above, show their name, their average popularity, and label them as a “Top Star."
WITH average_popularity_CTE AS (
    SELECT 
        top_tracks.artist_name,
        AVG(top_tracks.popularity) AS artist_popularity
    FROM Spotifydata AS top_tracks
    GROUP BY top_tracks.artist_name
    )
    
SELECT 
    artist_name, 
    artist_popularity,
    'Top Star' AS tag
FROM average_popularity_CTE
WHERE artist_popularity >= 90
ORDER BY artist_popularity DESC;
