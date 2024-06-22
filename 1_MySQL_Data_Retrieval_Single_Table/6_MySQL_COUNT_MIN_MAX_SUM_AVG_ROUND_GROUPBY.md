## MySQL:  COUNT,MIN,MAX,AVG,SUM,ROUND,GROUPBY


**Author: Abhishek Dey**

**Last modified: 22/06/2024**

## Defn:

* **COUNT()** function returns the number of rows that matches a specified criterion.

* **MIN()** function returns the **smallest** value of the selected column.

* **MAX()** function returns the **largest** value of the selected column.

* **AVG()** function returns the **average** value of a numeric column. 

* **SUM()** function returns the **total sum** of a numeric column

* **ROUND()** function is used to Round off the decimal places

* **GROUP BY()** function is used to Group the result-set by one or more columns.

## Examples: COUNT()

* Considering **country** table, print the no. of rows in Region column

```

mysql> select count(Region) as Region_Count from country;

```

```
+--------------+
| Region_Count |
+--------------+
|          239 |
+--------------+
1 row in set (0.00 sec)

mysql> 

```

* Considering **country** table, print the **unique** no. of rows in Region column

```

mysql> select count(Distinct Region) as Distinct_Region_Count from country;

```

```
+-----------------------+
| Distinct_Region_Count |
+-----------------------+
|                    25 |
+-----------------------+
1 row in set (0.00 sec)

mysql> 

```

## Examples : MIN(), MAX(), AVG(), ROUND()

* MIN()

```
mysql> select MIN(LifeExpectancy) as Minimum from country;

+---------+
| Minimum |
+---------+
|    37.2 |
+---------+
1 row in set (0.00 sec)

```

* MAX()

```
mysql> select MAX(LifeExpectancy) as Maximum from country;

+---------+
| Maximum |
+---------+
|    83.5 |
+---------+
1 row in set (0.00 sec)

```

* AVG()

```
mysql> select AVG(LifeExpectancy) as Average from country;

+----------+
| Average  |
+----------+
| 66.48604 |
+----------+

1 row in set (0.01 sec)

```

* ROUND()

```
mysql> select ROUND(AVG(LifeExpectancy),2) as Average from country;

+---------+
| Average |
+---------+
|   66.49 |
+---------+
1 row in set (0.00 sec)

mysql>

```

## Example : SUM () & GROUP BY ()

* Considering **country** table, print the total population of **Europe**

```

mysql> select SUM(Population) from country where Continent="Europe";
+-----------------+
| SUM(Population) |
+-----------------+
|       730074600 |
+-----------------+
1 row in set (0.00 sec)

```

* Considering **country** table, print the total population of all the continents using Groupby()

```
mysql> select Continent, SUM(Population) as Total_Population from country GROUP BY Continent;

+---------------+------------------+
| Continent     | Total_Population |
+---------------+------------------+
| North America |        482993000 |
| Asia          |       3705025700 |
| Africa        |        784475000 |
| Europe        |        730074600 |
| South America |        345780000 |
| Oceania       |         30401150 |
| Antarctica    |                0 |
+---------------+------------------+
7 rows in set (0.00 sec)

```

## Example : Combination

```
mysql> select Continent, SUM(Population) as Total_Population, MIN(LifeExpectancy) as MIN_LE, MAX(LifeExpectancy) as MAX_LE, AVG(LifeExpectancy) as AVG_LE from country GROUP BY Continent;

```

```
+---------------+------------------+--------+--------+----------+
| Continent     | Total_Population | MIN_LE | MAX_LE | AVG_LE   |
+---------------+------------------+--------+--------+----------+
| North America |        482993000 |   49.2 |   79.4 | 72.99189 |
| Asia          |       3705025700 |   45.9 |   81.6 | 67.44118 |
| Africa        |        784475000 |   37.2 |   76.8 | 52.57193 |
| Europe        |        730074600 |   64.5 |   83.5 | 75.14773 |
| South America |        345780000 |   62.9 |   76.1 | 70.94615 |
| Oceania       |         30401150 |   59.8 |   79.8 | 69.71500 |
| Antarctica    |                0 |   NULL |   NULL |     NULL |
+---------------+------------------+--------+--------+----------+
7 rows in set (0.00 sec)

mysql> 

```

