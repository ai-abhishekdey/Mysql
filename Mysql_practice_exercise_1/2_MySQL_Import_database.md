## MySQL Import Database

**Author: Abhishek Dey**

**Last modified: 08/06/2024**


### Login to mysql

```

mysql -u abhishek -p

```

### Show all existing databases

```

mysql> show databases;

```

```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.00 sec)

```


### Import movies-db.sql

* syntax

```
mysql> source /path/to/sql/file.sql

```

* example

```

mysql> source movies-db.sql;

```

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| moviesdb           |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.01 sec)
 
```

### Select movies database

```
mysql> use moviesdb;
Database changed
mysql> 

```

### Show tables in the movies database

```

mysql> show tables;

```

```
+--------------------+
| Tables_in_moviesdb |
+--------------------+
| actors             |
| financials         |
| languages          |
| movie_actor        |
| movies             |
+--------------------+
5 rows in set (0.00 sec)

mysql> 

```

### Print all the fields of movies table

```

mysql> describe movies;

```

```
+--------------+------------------+------+-----+---------+----------------+
| Field        | Type             | Null | Key | Default | Extra          |
+--------------+------------------+------+-----+---------+----------------+
| movie_id     | int unsigned     | NO   | PRI | NULL    | auto_increment |
| title        | varchar(150)     | NO   |     | NULL    |                |
| industry     | varchar(45)      | YES  |     | NULL    |                |
| release_year | year             | YES  |     | NULL    |                |
| imdb_rating  | decimal(3,1)     | YES  |     | NULL    |                |
| studio       | varchar(45)      | YES  |     | NULL    |                |
| language_id  | tinyint unsigned | YES  | MUL | NULL    |                |
+--------------+------------------+------+-----+---------+----------------+
7 rows in set (0.09 sec)

mysql> 

```

## DEMONSTRATION: Use of ORDER BY and LIMIT


### Print first 5 entires of movies table ordered by movie_id in ascending order : 101, 102..105

```
mysql> select * from movies order by movie_id limit 5;

```

```
mysql> select * from movies order by movie_id asc limit 5;
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
| movie_id | title                                       | industry  | release_year | imdb_rating | studio         | language_id |
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
|      101 | K.G.F: Chapter 2                            | Bollywood |         2022 |         8.4 | Hombale Films  |           3 |
|      102 | Doctor Strange in the Multiverse of Madness | Hollywood |         2022 |         7.0 | Marvel Studios |           5 |
|      103 | Thor: The Dark World                        | Hollywood |         2013 |         6.8 | Marvel Studios |           5 |
|      104 | Thor: Ragnarok                              | Hollywood |         2017 |         7.9 | Marvel Studios |           5 |
|      105 | Thor: Love and Thunder                      | Hollywood |         2022 |         6.8 | Marvel Studios |           5 |
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
5 rows in set (0.00 sec)

mysql> 


```

### Print first 5 entires of movies table ordered by movie_id in descending order : 105, 104..101

```

mysql> (select * from movies order by movie_id limit 5) order by movie_id desc;

```

```
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
| movie_id | title                                       | industry  | release_year | imdb_rating | studio         | language_id |
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
|      105 | Thor: Love and Thunder                      | Hollywood |         2022 |         6.8 | Marvel Studios |           5 |
|      104 | Thor: Ragnarok                              | Hollywood |         2017 |         7.9 | Marvel Studios |           5 |
|      103 | Thor: The Dark World                        | Hollywood |         2013 |         6.8 | Marvel Studios |           5 |
|      102 | Doctor Strange in the Multiverse of Madness | Hollywood |         2022 |         7.0 | Marvel Studios |           5 |
|      101 | K.G.F: Chapter 2                            | Bollywood |         2022 |         8.4 | Hombale Films  |           3 |
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
5 rows in set (0.01 sec)

mysql> 

```

### Print last 5 entires of movies table ordered by movie_id in descending order : 140, 139..136

```
mysql> select * from movies order by movie_id desc limit 5;

```

```
+----------+-------------------------------------+-----------+--------------+-------------+--------------------+-------------+
| movie_id | title                               | industry  | release_year | imdb_rating | studio             | language_id |
+----------+-------------------------------------+-----------+--------------+-------------+--------------------+-------------+
|      140 | Shershaah                           | Bollywood |         2021 |         8.4 | Dharma Productions |           1 |
|      139 | Race 3                              | Bollywood |         2018 |         1.9 | Salman Khan Films  |           1 |
|      138 | Captain America: The Winter Soldier | Hollywood |         2014 |         7.8 | Marvel Studios     |           5 |
|      137 | Captain America: The First Avenger  | Hollywood |         2011 |         6.9 | Marvel Studios     |           5 |
|      136 | Bajrangi Bhaijaan                   | Bollywood |         2015 |         8.1 | Salman Khan Films  |           1 |
+----------+-------------------------------------+-----------+--------------+-------------+--------------------+-------------+
5 rows in set (0.00 sec)

mysql> 

```

### Print last 5 entires of movies table ordered by movie_id in ascending order : 136, 137..140

```
mysql> (select * from movies order by movie_id desc limit 5) order by movie_id asc;

```

```
+----------+-------------------------------------+-----------+--------------+-------------+--------------------+-------------+
| movie_id | title                               | industry  | release_year | imdb_rating | studio             | language_id |
+----------+-------------------------------------+-----------+--------------+-------------+--------------------+-------------+
|      136 | Bajrangi Bhaijaan                   | Bollywood |         2015 |         8.1 | Salman Khan Films  |           1 |
|      137 | Captain America: The First Avenger  | Hollywood |         2011 |         6.9 | Marvel Studios     |           5 |
|      138 | Captain America: The Winter Soldier | Hollywood |         2014 |         7.8 | Marvel Studios     |           5 |
|      139 | Race 3                              | Bollywood |         2018 |         1.9 | Salman Khan Films  |           1 |
|      140 | Shershaah                           | Bollywood |         2021 |         8.4 | Dharma Productions |           1 |
+----------+-------------------------------------+-----------+--------------+-------------+--------------------+-------------+
5 rows in set (0.00 sec)

mysql> 

```

## DEMONSTRATION: Use of COUNT, MIN, MAX, AVG, GROUPBY



## Exercise:

### 1. Print all movie titles and release year for all Marvel Studios movies

```

mysql> select title, release_year from movies where studio like "%Marvel%";

```

```
+---------------------------------------------+--------------+
| title                                       | release_year |
+---------------------------------------------+--------------+
| Doctor Strange in the Multiverse of Madness |         2022 |
| Thor: The Dark World                        |         2013 |
| Thor: Ragnarok                              |         2017 |
| Thor: Love and Thunder                      |         2022 |
| Avengers: Endgame                           |         2019 |
| Avengers: Infinity War                      |         2018 |
| Captain America: The First Avenger          |         2011 |
| Captain America: The Winter Soldier         |         2014 |
+---------------------------------------------+--------------+
8 rows in set (0.00 sec)

mysql> 

```

### 2. Print all movies that have Avenger in their name

```

mysql> select * from movies where title like "%Avenger%";

```

```
+----------+------------------------------------+-----------+--------------+-------------+----------------+-------------+
| movie_id | title                              | industry  | release_year | imdb_rating | studio         | language_id |
+----------+------------------------------------+-----------+--------------+-------------+----------------+-------------+
|      125 | Avengers: Endgame                  | Hollywood |         2019 |         8.4 | Marvel Studios |           5 |
|      126 | Avengers: Infinity War             | Hollywood |         2018 |         8.4 | Marvel Studios |           5 |
|      137 | Captain America: The First Avenger | Hollywood |         2011 |         6.9 | Marvel Studios |           5 |
+----------+------------------------------------+-----------+--------------+-------------+----------------+-------------+
3 rows in set (0.00 sec)

mysql> 

```
### 3. Print the year when the movie "The Godfather" was released


```

mysql> select release_year from movies where title="The Godfather";

```

```
+--------------+
| release_year |
+--------------+
|         1972 |
+--------------+
1 row in set (0.00 sec)

mysql> 

```

### 4. Print all distinct movie studios in the Bollywood industry

```

mysql> select distinct studio from movies where industry="Bollywood";

```

```
+---------------------------+
| studio                    |
+---------------------------+
| Hombale Films             |
| United Producers          |
| Yash Raj Films            |
| Vinod Chopra Films        |
| Dharma Productions        |
|                           |
| Government of West Bengal |
| Vinod Chopra Productions  |
| Mythri Movie Makers       |
| DVV Entertainment         |
| Arka Media Works          |
| Zee Studios               |
| Salman Khan Films         |
+---------------------------+
13 rows in set (0.14 sec)

mysql>

```

### 5. Print all movies having imdb rating > 9

```

mysql> select * from movies where imdb_rating > 9;

```

```
+----------+--------------------------+-----------+--------------+-------------+---------------------------+-------------+
| movie_id | title                    | industry  | release_year | imdb_rating | studio                    | language_id |
+----------+--------------------------+-----------+--------------+-------------+---------------------------+-------------+
|      111 | The Shawshank Redemption | Hollywood |         1994 |         9.3 | Castle Rock Entertainment |           5 |
|      120 | The Godfather            | Hollywood |         1972 |         9.2 | Paramount Pictures        |           5 |
+----------+--------------------------+-----------+--------------+-------------+---------------------------+-------------+
2 rows in set (0.00 sec)

mysql> 

```

### 6. Print all movies having imdb rating between 6 and 8

```

mysql> select * from movies where imdb_rating between 6 and 8;

```

```
+----------+---------------------------------------------+-----------+--------------+-------------+---------------------+-------------+
| movie_id | title                                       | industry  | release_year | imdb_rating | studio              | language_id |
+----------+---------------------------------------------+-----------+--------------+-------------+---------------------+-------------+
|      102 | Doctor Strange in the Multiverse of Madness | Hollywood |         2022 |         7.0 | Marvel Studios      |           5 |
|      103 | Thor: The Dark World                        | Hollywood |         2013 |         6.8 | Marvel Studios      |           5 |
|      104 | Thor: Ragnarok                              | Hollywood |         2017 |         7.9 | Marvel Studios      |           5 |
|      105 | Thor: Love and Thunder                      | Hollywood |         2022 |         6.8 | Marvel Studios      |           5 |
|      107 | Dilwale Dulhania Le Jayenge                 | Bollywood |         1995 |         8.0 | Yash Raj Films      |           1 |
|      109 | Kabhi Khushi Kabhie Gham                    | Bollywood |         2001 |         7.4 | Dharma Productions  |           1 |
|      110 | Bajirao Mastani                             | Bollywood |         2015 |         7.2 |                     |           1 |
|      115 | The Pursuit of Happyness                    | Hollywood |         2006 |         8.0 | Columbia Pictures   |           5 |
|      117 | Titanic                                     | Hollywood |         1997 |         7.9 | Paramount Pictures  |           5 |
|      119 | Avatar                                      | Hollywood |         2009 |         7.8 | 20th Century Fox    |           5 |
|      132 | Pushpa: The Rise - Part 1                   | Bollywood |         2021 |         7.6 | Mythri Movie Makers |           2 |
|      133 | RRR                                         | Bollywood |         2022 |         8.0 | DVV Entertainment   |           2 |
|      134 | Baahubali: The Beginning                    | Bollywood |         2015 |         8.0 | Arka Media Works    |           2 |
|      137 | Captain America: The First Avenger          | Hollywood |         2011 |         6.9 | Marvel Studios      |           5 |
|      138 | Captain America: The Winter Soldier         | Hollywood |         2014 |         7.8 | Marvel Studios      |           5 |
+----------+---------------------------------------------+-----------+--------------+-------------+---------------------+-------------+
15 rows in set (0.00 sec)

mysql> 

```

### 7. Print all movies released in the year 2022

```

mysql> select * from movies where release_year=2022;

```

```

+----------+---------------------------------------------+-----------+--------------+-------------+-------------------+-------------+
| movie_id | title                                       | industry  | release_year | imdb_rating | studio            | language_id |
+----------+---------------------------------------------+-----------+--------------+-------------+-------------------+-------------+
|      101 | K.G.F: Chapter 2                            | Bollywood |         2022 |         8.4 | Hombale Films     |           3 |
|      102 | Doctor Strange in the Multiverse of Madness | Hollywood |         2022 |         7.0 | Marvel Studios    |           5 |
|      105 | Thor: Love and Thunder                      | Hollywood |         2022 |         6.8 | Marvel Studios    |           5 |
|      133 | RRR                                         | Bollywood |         2022 |         8.0 | DVV Entertainment |           2 |
|      135 | The Kashmir Files                           | Bollywood |         2022 |         8.3 | Zee Studios       |           1 |
+----------+---------------------------------------------+-----------+--------------+-------------+-------------------+-------------+
5 rows in set (0.00 sec)

mysql> 

```

### 8. Print all movies released in the year 2019 and 2022

```

mysql> select * from movies where release_year=2019 or release_year=2022;

```

```
+----------+---------------------------------------------+-----------+--------------+-------------+-------------------+-------------+
| movie_id | title                                       | industry  | release_year | imdb_rating | studio            | language_id |
+----------+---------------------------------------------+-----------+--------------+-------------+-------------------+-------------+
|      101 | K.G.F: Chapter 2                            | Bollywood |         2022 |         8.4 | Hombale Films     |           3 |
|      102 | Doctor Strange in the Multiverse of Madness | Hollywood |         2022 |         7.0 | Marvel Studios    |           5 |
|      105 | Thor: Love and Thunder                      | Hollywood |         2022 |         6.8 | Marvel Studios    |           5 |
|      124 | Parasite                                    | Hollywood |         2019 |         8.5 |                   |           5 |
|      125 | Avengers: Endgame                           | Hollywood |         2019 |         8.4 | Marvel Studios    |           5 |
|      133 | RRR                                         | Bollywood |         2022 |         8.0 | DVV Entertainment |           2 |
|      135 | The Kashmir Files                           | Bollywood |         2022 |         8.3 | Zee Studios       |           1 |
+----------+---------------------------------------------+-----------+--------------+-------------+-------------------+-------------+
7 rows in set (0.00 sec)

mysql> 

```

### 9. Print all movies released between 2015 and 2018 in asceding order

```

mysql> select * from movies where release_year between 2015 and 2018 order by release_year;

```

```
+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
| movie_id | title                    | industry  | release_year | imdb_rating | studio             | language_id |
+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
|      110 | Bajirao Mastani          | Bollywood |         2015 |         7.2 |                    |           1 |
|      134 | Baahubali: The Beginning | Bollywood |         2015 |         8.0 | Arka Media Works   |           2 |
|      136 | Bajrangi Bhaijaan        | Bollywood |         2015 |         8.1 | Salman Khan Films  |           1 |
|      104 | Thor: Ragnarok           | Hollywood |         2017 |         7.9 | Marvel Studios     |           5 |
|      126 | Avengers: Infinity War   | Hollywood |         2018 |         8.4 | Marvel Studios     |           5 |
|      131 | Sanju                    | Bollywood |         2018 |        NULL | Vinod Chopra Films |           1 |
|      139 | Race 3                   | Bollywood |         2018 |         1.9 | Salman Khan Films  |           1 |
+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
7 rows in set (0.00 sec)

mysql> 

```

### 10. Print all movies released between 2015 and 2018 in desceding order

```

mysql> select * from movies where release_year between 2015 and 2018 order by release_year desc;

```

```

+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
| movie_id | title                    | industry  | release_year | imdb_rating | studio             | language_id |
+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
|      126 | Avengers: Infinity War   | Hollywood |         2018 |         8.4 | Marvel Studios     |           5 |
|      131 | Sanju                    | Bollywood |         2018 |        NULL | Vinod Chopra Films |           1 |
|      139 | Race 3                   | Bollywood |         2018 |         1.9 | Salman Khan Films  |           1 |
|      104 | Thor: Ragnarok           | Hollywood |         2017 |         7.9 | Marvel Studios     |           5 |
|      110 | Bajirao Mastani          | Bollywood |         2015 |         7.2 |                    |           1 |
|      134 | Baahubali: The Beginning | Bollywood |         2015 |         8.0 | Arka Media Works   |           2 |
|      136 | Bajrangi Bhaijaan        | Bollywood |         2015 |         8.1 | Salman Khan Films  |           1 |
+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
7 rows in set (0.00 sec)

mysql> 

```

### 11. Print all bollywood movies released between 2013 and 2015 having imdb rating >=8

```

mysql> select * from movies where industry="bollywood" and release_year between 2013 and 2015 and imdb_rating >= 8;

```

```

+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
| movie_id | title                    | industry  | release_year | imdb_rating | studio             | language_id |
+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
|      130 | PK                       | Bollywood |         2014 |         8.1 | Vinod Chopra Films |           1 |
|      134 | Baahubali: The Beginning | Bollywood |         2015 |         8.0 | Arka Media Works   |           2 |
|      136 | Bajrangi Bhaijaan        | Bollywood |         2015 |         8.1 | Salman Khan Films  |           1 |
+----------+--------------------------+-----------+--------------+-------------+--------------------+-------------+
3 rows in set (0.00 sec)

mysql>  

```

### 12. Print all hollywood movies released in the years 2008,2013,2019,2022


```

mysql> select * from movies where industry="hollywood" and release_year in (2008,2013,2019,2022) order by release_year;

```

```
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
| movie_id | title                                       | industry  | release_year | imdb_rating | studio         | language_id |
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
|      121 | The Dark Knight                             | Hollywood |         2008 |         9.0 | Syncopy        |           5 |
|      103 | Thor: The Dark World                        | Hollywood |         2013 |         6.8 | Marvel Studios |           5 |
|      124 | Parasite                                    | Hollywood |         2019 |         8.5 |                |           5 |
|      125 | Avengers: Endgame                           | Hollywood |         2019 |         8.4 | Marvel Studios |           5 |
|      102 | Doctor Strange in the Multiverse of Madness | Hollywood |         2022 |         7.0 | Marvel Studios |           5 |
|      105 | Thor: Love and Thunder                      | Hollywood |         2022 |         6.8 | Marvel Studios |           5 |
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
6 rows in set (0.00 sec)

mysql>

```

### 13. Print all movies from Marvel Studios and Zee Studios released in the year 2022

```

mysql> select * from movies where studio in ("Marvel Studios", "Zee Studios") and release_year=2022;

```

```
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
| movie_id | title                                       | industry  | release_year | imdb_rating | studio         | language_id |
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
|      102 | Doctor Strange in the Multiverse of Madness | Hollywood |         2022 |         7.0 | Marvel Studios |           5 |
|      105 | Thor: Love and Thunder                      | Hollywood |         2022 |         6.8 | Marvel Studios |           5 |
|      135 | The Kashmir Files                           | Bollywood |         2022 |         8.3 | Zee Studios    |           1 |
+----------+---------------------------------------------+-----------+--------------+-------------+----------------+-------------+
3 rows in set (0.00 sec)

mysql> 

```

### 14. Print all records from movies table where imdb rating is null

```

mysql> select * from movies where imdb_rating is null;

```

```
+----------+-------+-----------+--------------+-------------+--------------------+-------------+
| movie_id | title | industry  | release_year | imdb_rating | studio             | language_id |
+----------+-------+-----------+--------------+-------------+--------------------+-------------+
|      131 | Sanju | Bollywood |         2018 |        NULL | Vinod Chopra Films |           1 |
+----------+-------+-----------+--------------+-------------+--------------------+-------------+
1 row in set (0.00 sec)

mysql> 

```

### 15.  Print all bollywood movies in the order of their release year (latest first). Make sure you don't have null imdb rating

```

mysql> select * from movies where industry="Bollywood" and imdb_rating is NOT NULL order by release_year desc;

```

```

+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
| movie_id | title                       | industry  | release_year | imdb_rating | studio                    | language_id |
+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
|      135 | The Kashmir Files           | Bollywood |         2022 |         8.3 | Zee Studios               |           1 |
|      101 | K.G.F: Chapter 2            | Bollywood |         2022 |         8.4 | Hombale Films             |           3 |
|      133 | RRR                         | Bollywood |         2022 |         8.0 | DVV Entertainment         |           2 |
|      140 | Shershaah                   | Bollywood |         2021 |         8.4 | Dharma Productions        |           1 |
|      132 | Pushpa: The Rise - Part 1   | Bollywood |         2021 |         7.6 | Mythri Movie Makers       |           2 |
|      139 | Race 3                      | Bollywood |         2018 |         1.9 | Salman Khan Films         |           1 |
|      136 | Bajrangi Bhaijaan           | Bollywood |         2015 |         8.1 | Salman Khan Films         |           1 |
|      110 | Bajirao Mastani             | Bollywood |         2015 |         7.2 |                           |           1 |
|      134 | Baahubali: The Beginning    | Bollywood |         2015 |         8.0 | Arka Media Works          |           2 |
|      130 | PK                          | Bollywood |         2014 |         8.1 | Vinod Chopra Films        |           1 |
|      108 | 3 Idiots                    | Bollywood |         2009 |         8.4 | Vinod Chopra Films        |           1 |
|      128 | Taare Zameen Par            | Bollywood |         2007 |         8.3 |                           |           1 |
|      129 | Munna Bhai M.B.B.S.         | Bollywood |         2003 |         8.1 | Vinod Chopra Productions  |           1 |
|      109 | Kabhi Khushi Kabhie Gham    | Bollywood |         2001 |         7.4 | Dharma Productions        |           1 |
|      107 | Dilwale Dulhania Le Jayenge | Bollywood |         1995 |         8.0 | Yash Raj Films            |           1 |
|      106 | Sholay                      | Bollywood |         1975 |         8.1 | United Producers          |           1 |
|      127 | Pather Panchali             | Bollywood |         1955 |         8.3 | Government of West Bengal |           7 |
+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
17 rows in set (0.01 sec)

mysql> 

```

### 16. Print name and release year of Hollywood movies released after 2013 (oldest first) 

```

mysql> select title, release_year from movies where industry="Hollywood" and release_year > 2013 order by release_year;

```

```
+---------------------------------------------+--------------+
| title                                       | release_year |
+---------------------------------------------+--------------+
| Interstellar                                |         2014 |
| Captain America: The Winter Soldier         |         2014 |
| Thor: Ragnarok                              |         2017 |
| Avengers: Infinity War                      |         2018 |
| Parasite                                    |         2019 |
| Avengers: Endgame                           |         2019 |
| Doctor Strange in the Multiverse of Madness |         2022 |
| Thor: Love and Thunder                      |         2022 |
+---------------------------------------------+--------------+
8 rows in set (0.00 sec)

mysql>

```

### 17. Print all movies released after the year 2020 that have more than 8 rating

```

mysql> select * from movies where release_year > 2020 and imdb_rating > 8 order by imdb_rating desc;

```

```

+----------+-------------------+-----------+--------------+-------------+--------------------+-------------+
| movie_id | title             | industry  | release_year | imdb_rating | studio             | language_id |
+----------+-------------------+-----------+--------------+-------------+--------------------+-------------+
|      101 | K.G.F: Chapter 2  | Bollywood |         2022 |         8.4 | Hombale Films      |           3 |
|      140 | Shershaah         | Bollywood |         2021 |         8.4 | Dharma Productions |           1 |
|      135 | The Kashmir Files | Bollywood |         2022 |         8.3 | Zee Studios        |           1 |
+----------+-------------------+-----------+--------------+-------------+--------------------+-------------+
3 rows in set (0.00 sec)

mysql> 

```

### 18. Select all THOR movies by their release year

```

mysql> select * from movies where title like "%THOR%" order by release_year;

```

```
+----------+-------------------------+-----------+--------------+-------------+----------------+-------------+
| movie_id | title                   | industry  | release_year | imdb_rating | studio         | language_id |
+----------+-------------------------+-----------+--------------+-------------+----------------+-------------+
|      103 | Thor: The Dark World    | Hollywood |         2013 |         6.8 | Marvel Studios |           5 |
|      104 | Thor: Ragnarok          | Hollywood |         2017 |         7.9 | Marvel Studios |           5 |
|      105 | Thor: Love and Thunder  | Hollywood |         2022 |         6.8 | Marvel Studios |           5 |
+----------+-------------------------+-----------+--------------+-------------+----------------+-------------+
3 rows in set (0.00 sec)

mysql> 

```

### 19. Select all movies that are not from Marvel Studios

```

mysql> select * from movies where studio!= "Marvel Studios";

```
```
+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
| movie_id | title                       | industry  | release_year | imdb_rating | studio                    | language_id |
+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
|      101 | K.G.F: Chapter 2            | Bollywood |         2022 |         8.4 | Hombale Films             |           3 |
|      106 | Sholay                      | Bollywood |         1975 |         8.1 | United Producers          |           1 |
|      107 | Dilwale Dulhania Le Jayenge | Bollywood |         1995 |         8.0 | Yash Raj Films            |           1 |
|      108 | 3 Idiots                    | Bollywood |         2009 |         8.4 | Vinod Chopra Films        |           1 |
|      109 | Kabhi Khushi Kabhie Gham    | Bollywood |         2001 |         7.4 | Dharma Productions        |           1 |
|      110 | Bajirao Mastani             | Bollywood |         2015 |         7.2 |                           |           1 |
|      111 | The Shawshank Redemption    | Hollywood |         1994 |         9.3 | Castle Rock Entertainment |           5 |
|      112 | Inception                   | Hollywood |         2010 |         8.8 | Warner Bros. Pictures     |           5 |
|      113 | Interstellar                | Hollywood |         2014 |         8.6 | Warner Bros. Pictures     |           5 |
|      115 | The Pursuit of Happyness    | Hollywood |         2006 |         8.0 | Columbia Pictures         |           5 |
|      116 | Gladiator                   | Hollywood |         2000 |         8.5 | Universal Pictures        |           5 |
|      117 | Titanic                     | Hollywood |         1997 |         7.9 | Paramount Pictures        |           5 |
|      118 | It's a Wonderful Life       | Hollywood |         1946 |         8.6 | Liberty Films             |           5 |
|      119 | Avatar                      | Hollywood |         2009 |         7.8 | 20th Century Fox          |           5 |
|      120 | The Godfather               | Hollywood |         1972 |         9.2 | Paramount Pictures        |           5 |
|      121 | The Dark Knight             | Hollywood |         2008 |         9.0 | Syncopy                   |           5 |
|      122 | Schindler's List            | Hollywood |         1993 |         9.0 | Universal Pictures        |           5 |
|      123 | Jurassic Park               | Hollywood |         1993 |         8.2 | Universal Pictures        |           5 |
|      124 | Parasite                    | Hollywood |         2019 |         8.5 |                           |           5 |
|      127 | Pather Panchali             | Bollywood |         1955 |         8.3 | Government of West Bengal |           7 |
|      128 | Taare Zameen Par            | Bollywood |         2007 |         8.3 |                           |           1 |
|      129 | Munna Bhai M.B.B.S.         | Bollywood |         2003 |         8.1 | Vinod Chopra Productions  |           1 |
|      130 | PK                          | Bollywood |         2014 |         8.1 | Vinod Chopra Films        |           1 |
|      131 | Sanju                       | Bollywood |         2018 |        NULL | Vinod Chopra Films        |           1 |
|      132 | Pushpa: The Rise - Part 1   | Bollywood |         2021 |         7.6 | Mythri Movie Makers       |           2 |
|      133 | RRR                         | Bollywood |         2022 |         8.0 | DVV Entertainment         |           2 |
|      134 | Baahubali: The Beginning    | Bollywood |         2015 |         8.0 | Arka Media Works          |           2 |
|      135 | The Kashmir Files           | Bollywood |         2022 |         8.3 | Zee Studios               |           1 |
|      136 | Bajrangi Bhaijaan           | Bollywood |         2015 |         8.1 | Salman Khan Films         |           1 |
|      139 | Race 3                      | Bollywood |         2018 |         1.9 | Salman Khan Films         |           1 |
|      140 | Shershaah                   | Bollywood |         2021 |         8.4 | Dharma Productions        |           1 |
+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
31 rows in set (0.00 sec)

mysql> 

```

### 20. Select all movies that are not by Zee studios, Hombale Films and Marvel Studios

```

mysql> select * from movies where studio NOT IN ("Zee Studios", "Hombale Films", "Marvel Studios");

```

```
+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
| movie_id | title                       | industry  | release_year | imdb_rating | studio                    | language_id |
+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
|      106 | Sholay                      | Bollywood |         1975 |         8.1 | United Producers          |           1 |
|      107 | Dilwale Dulhania Le Jayenge | Bollywood |         1995 |         8.0 | Yash Raj Films            |           1 |
|      108 | 3 Idiots                    | Bollywood |         2009 |         8.4 | Vinod Chopra Films        |           1 |
|      109 | Kabhi Khushi Kabhie Gham    | Bollywood |         2001 |         7.4 | Dharma Productions        |           1 |
|      110 | Bajirao Mastani             | Bollywood |         2015 |         7.2 |                           |           1 |
|      111 | The Shawshank Redemption    | Hollywood |         1994 |         9.3 | Castle Rock Entertainment |           5 |
|      112 | Inception                   | Hollywood |         2010 |         8.8 | Warner Bros. Pictures     |           5 |
|      113 | Interstellar                | Hollywood |         2014 |         8.6 | Warner Bros. Pictures     |           5 |
|      115 | The Pursuit of Happyness    | Hollywood |         2006 |         8.0 | Columbia Pictures         |           5 |
|      116 | Gladiator                   | Hollywood |         2000 |         8.5 | Universal Pictures        |           5 |
|      117 | Titanic                     | Hollywood |         1997 |         7.9 | Paramount Pictures        |           5 |
|      118 | It's a Wonderful Life       | Hollywood |         1946 |         8.6 | Liberty Films             |           5 |
|      119 | Avatar                      | Hollywood |         2009 |         7.8 | 20th Century Fox          |           5 |
|      120 | The Godfather               | Hollywood |         1972 |         9.2 | Paramount Pictures        |           5 |
|      121 | The Dark Knight             | Hollywood |         2008 |         9.0 | Syncopy                   |           5 |
|      122 | Schindler's List            | Hollywood |         1993 |         9.0 | Universal Pictures        |           5 |
|      123 | Jurassic Park               | Hollywood |         1993 |         8.2 | Universal Pictures        |           5 |
|      124 | Parasite                    | Hollywood |         2019 |         8.5 |                           |           5 |
|      127 | Pather Panchali             | Bollywood |         1955 |         8.3 | Government of West Bengal |           7 |
|      128 | Taare Zameen Par            | Bollywood |         2007 |         8.3 |                           |           1 |
|      129 | Munna Bhai M.B.B.S.         | Bollywood |         2003 |         8.1 | Vinod Chopra Productions  |           1 |
|      130 | PK                          | Bollywood |         2014 |         8.1 | Vinod Chopra Films        |           1 |
|      131 | Sanju                       | Bollywood |         2018 |        NULL | Vinod Chopra Films        |           1 |
|      132 | Pushpa: The Rise - Part 1   | Bollywood |         2021 |         7.6 | Mythri Movie Makers       |           2 |
|      133 | RRR                         | Bollywood |         2022 |         8.0 | DVV Entertainment         |           2 |
|      134 | Baahubali: The Beginning    | Bollywood |         2015 |         8.0 | Arka Media Works          |           2 |
|      136 | Bajrangi Bhaijaan           | Bollywood |         2015 |         8.1 | Salman Khan Films         |           1 |
|      139 | Race 3                      | Bollywood |         2018 |         1.9 | Salman Khan Films         |           1 |
|      140 | Shershaah                   | Bollywood |         2021 |         8.4 | Dharma Productions        |           1 |
+----------+-----------------------------+-----------+--------------+-------------+---------------------------+-------------+
29 rows in set (0.00 sec)

mysql> 

```
