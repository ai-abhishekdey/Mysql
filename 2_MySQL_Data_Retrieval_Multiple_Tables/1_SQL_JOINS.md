## MySQL JOINS

**Author: Abhishek Dey**

**Last Modified : July 6, 2024**

## SQL JOINS - BY EXAMPLE QUERIES

![sql_join_queries](images/sql_join_by_queries.png)


## Movies Database


* Show databases;

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
| world              |
+--------------------+
6 rows in set (0.00 sec)

mysql> 

```

* Use moviesdb

```

mysql> 
mysql> use moviesdb;
Database changed
mysql>

```

* Show tables

```

mysql> show tables;
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

* Fields in movies table **[ TABLE A]**

```

mysql> describe movies;
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
7 rows in set (0.00 sec)

mysql> 

```

* Fields in financials table **[TABLE B]**

```
mysql> describe financials;
+----------+-------------------------------------------------+------+-----+---------+-------+
| Field    | Type                                            | Null | Key | Default | Extra |
+----------+-------------------------------------------------+------+-----+---------+-------+
| movie_id | int unsigned                                    | NO   | PRI | NULL    |       |
| budget   | decimal(10,2)                                   | YES  |     | NULL    |       |
| revenue  | decimal(10,2)                                   | YES  |     | NULL    |       |
| unit     | enum('Units','Thousands','Millions','Billions') | YES  |     | NULL    |       |
| currency | char(3)                                         | YES  |     | NULL    |       |
+----------+-------------------------------------------------+------+-----+---------+-------+
5 rows in set (0.00 sec)

mysql> 


```
