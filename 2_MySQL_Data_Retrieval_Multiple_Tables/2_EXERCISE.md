## Exercise : JOINS

**Author: Abhishek Dey**

**Date: July 6, 2024**


### Ques: 1

**Show all the movies with their language names**

### Soln:

```

mysql> select movie_id, title, B.name as language from movies A
    -> INNER JOIN languages B
    -> ON A.language_id=B.language_id;

```

```

+----------+---------------------------------------------+----------+
| movie_id | title                                       | language |
+----------+---------------------------------------------+----------+
|      127 | Pather Panchali                             | Bengali  |
|      102 | Doctor Strange in the Multiverse of Madness | English  |
|      103 | Thor: The Dark World                        | English  |
|      104 | Thor: Ragnarok                              | English  |
|      105 | Thor: Love and Thunder                      | English  |
|      111 | The Shawshank Redemption                    | English  |
|      112 | Inception                                   | English  |
|      113 | Interstellar                                | English  |
|      115 | The Pursuit of Happyness                    | English  |
|      116 | Gladiator                                   | English  |
|      117 | Titanic                                     | English  |
|      118 | It's a Wonderful Life                       | English  |
|      119 | Avatar                                      | English  |
|      120 | The Godfather                               | English  |
|      121 | The Dark Knight                             | English  |
|      122 | Schindler's List                            | English  |
|      123 | Jurassic Park                               | English  |
|      124 | Parasite                                    | English  |
|      125 | Avengers: Endgame                           | English  |
|      126 | Avengers: Infinity War                      | English  |
|      137 | Captain America: The First Avenger          | English  |
|      138 | Captain America: The Winter Soldier         | English  |
|      106 | Sholay                                      | Hindi    |
|      107 | Dilwale Dulhania Le Jayenge                 | Hindi    |
|      108 | 3 Idiots                                    | Hindi    |
|      109 | Kabhi Khushi Kabhie Gham                    | Hindi    |
|      110 | Bajirao Mastani                             | Hindi    |
|      128 | Taare Zameen Par                            | Hindi    |
|      129 | Munna Bhai M.B.B.S.                         | Hindi    |
|      130 | PK                                          | Hindi    |
|      131 | Sanju                                       | Hindi    |
|      135 | The Kashmir Files                           | Hindi    |
|      136 | Bajrangi Bhaijaan                           | Hindi    |
|      139 | Race 3                                      | Hindi    |
|      140 | Shershaah                                   | Hindi    |
|      101 | K.G.F: Chapter 2                            | Kannada  |
|      132 | Pushpa: The Rise - Part 1                   | Telugu   |
|      133 | RRR                                         | Telugu   |
|      134 | Baahubali: The Beginning                    | Telugu   |
+----------+---------------------------------------------+----------+
39 rows in set (0.00 sec)

mysql> 

```

### Ques: 2

**Show all Telugu movie names (assuming you don't know the language id for Telugu)**

### Soln:

```

mysql> select movie_id, title, B.name as language from movies A
    -> INNER JOIN languages B
    -> ON A.language_id=B.language_id
    -> WHERE name="Telugu";
    
```

```

+----------+---------------------------+----------+
| movie_id | title                     | language |
+----------+---------------------------+----------+
|      132 | Pushpa: The Rise - Part 1 | Telugu   |
|      133 | RRR                       | Telugu   |
|      134 | Baahubali: The Beginning  | Telugu   |
+----------+---------------------------+----------+
3 rows in set (0.00 sec)

mysql> 

```


### Ques: 3

**Show the language and number of movies released in that language**

### Soln:

```
mysql> select B.name as language, COUNT(A.movie_id) as movie_count from movies A
    -> RIGHT JOIN languages B
    -> ON A.language_id=B.language_id
    -> GROUP BY B.name
    -> ORDER BY movie_count DESC;


```

```
+----------+-------------+
| language | movie_count |
+----------+-------------+
| English  |          21 |
| Hindi    |          13 |
| Telugu   |           3 |
| Bengali  |           1 |
| Kannada  |           1 |
| French   |           0 |
| Gujarati |           0 |
| Tamil    |           0 |
+----------+-------------+
8 rows in set (0.00 sec)

mysql> 

```
