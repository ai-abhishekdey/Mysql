## MySQL Import Database

**Author: Abhishek Dey**

**Last modified: 19/06/2024**


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

### Download publicly available world database from the below link

* https://dev.mysql.com/doc/index-other.html

### Import world.sql

* syntax

```
mysql> source /path/to/sql/file.sql

```

* example

```

mysql> source /path/to/world.sql;

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
| world              |
+--------------------+

5 rows in set (0.01 sec)
 
```

### Select world database

```
mysql> use world;
Database changed
mysql> 

```

### Show tables in the world database

```

mysql> show tables;

```

```
+-----------------+
| Tables_in_world |
+-----------------+
| city            |
| country         |
| countrylanguage |
+-----------------+
3 rows in set (0.00 sec)


mysql> 

```

### Check the fields of each table

* describe **city** table

```

mysql> describe city;

```

```
+-------------+----------+------+-----+---------+----------------+
| Field       | Type     | Null | Key | Default | Extra          |
+-------------+----------+------+-----+---------+----------------+
| ID          | int      | NO   | PRI | NULL    | auto_increment |
| Name        | char(35) | NO   |     |         |                |
| CountryCode | char(3)  | NO   | MUL |         |                |
| District    | char(20) | NO   |     |         |                |
| Population  | int      | NO   |     | 0       |                |
+-------------+----------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

```

* describe **country** table

```
mysql> describe country;

```

```
+----------------+---------------------------------------------------------------------------------------+------+-----+---------+-------+
| Field          | Type                                                                                  | Null | Key | Default | Extra |
+----------------+---------------------------------------------------------------------------------------+------+-----+---------+-------+
| Code           | char(3)                                                                               | NO   | PRI |         |       |
| Name           | char(52)                                                                              | NO   |     |         |       |
| Continent      | enum('Asia','Europe','North America','Africa','Oceania','Antarctica','South America') | NO   |     | Asia    |       |
| Region         | char(26)                                                                              | NO   |     |         |       |
| SurfaceArea    | decimal(10,2)                                                                         | NO   |     | 0.00    |       |
| IndepYear      | smallint                                                                              | YES  |     | NULL    |       |
| Population     | int                                                                                   | NO   |     | 0       |       |
| LifeExpectancy | decimal(3,1)                                                                          | YES  |     | NULL    |       |
| GNP            | decimal(10,2)                                                                         | YES  |     | NULL    |       |
| GNPOld         | decimal(10,2)                                                                         | YES  |     | NULL    |       |
| LocalName      | char(45)                                                                              | NO   |     |         |       |
| GovernmentForm | char(45)                                                                              | NO   |     |         |       |
| HeadOfState    | char(60)                                                                              | YES  |     | NULL    |       |
| Capital        | int                                                                                   | YES  |     | NULL    |       |
| Code2          | char(2)                                                                               | NO   |     |         |       |
+----------------+---------------------------------------------------------------------------------------+------+-----+---------+-------+
15 rows in set (0.00 sec)

```

* describe **countrylanguage** table

```
mysql> describe countrylanguage;

```

```
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| CountryCode | char(3)       | NO   | PRI |         |       |
| Language    | char(30)      | NO   | PRI |         |       |
| IsOfficial  | enum('T','F') | NO   |     | F       |       |
| Percentage  | decimal(4,1)  | NO   |     | 0.0     |       |
+-------------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

```

