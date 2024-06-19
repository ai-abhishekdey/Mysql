## MySQL SELECT & WHERE


**Author: Abhishek Dey**

**Last modified: 19/06/2024**

## Defn:

* The **SELECT** statement is used to select data from a database.

* The **WHERE** clause is used to filter records

### Operators in WHERE clause:

| **Operator** |                  **Description**                 |
|:------------:|:------------------------------------------------:|
|       =      | Equal                                            |
|       <      | Greater than                                     |
|     &lt;     | Less than                                        |
|     &gt;=    | Greater than or equal                            |
|     &lt;=    | Less than or equal                               |
|      !=      | Not equal                                        |
|    BETWEEN   | Between a certain range                          |
|     LIKE     | Search for a pattern                             |
|      IN      | To specify multiple possible values for a column |

## Examples:

* Select all from **country** table

```
mysql> select * from country;

```

* Select Name, Continent, Population fields from **country** table

```
mysql> select Name, Continent, Population from country;

```

```

+----------------------------------------------+---------------+------------+
| Name                                         | Continent     | Population |
+----------------------------------------------+---------------+------------+
| Aruba                                        | North America |     103000 |
| Afghanistan                                  | Asia          |   22720000 |
| Angola                                       | Africa        |   12878000 |
| Anguilla                                     | North America |       8000 |
| Albania                                      | Europe        |    3401200 |
| Andorra                                      | Europe        |      78000 |
| Netherlands Antilles                         | North America |     217000 |
| United Arab Emirates                         | Asia          |    2441000 |

----
| Vanuatu                                      | Oceania       |     190000 |
| Wallis and Futuna                            | Oceania       |      15000 |
| Samoa                                        | Oceania       |     180000 |
| Yemen                                        | Asia          |   18112000 |
| Yugoslavia                                   | Europe        |   10640000 |
| South Africa                                 | Africa        |   40377000 |
| Zambia                                       | Africa        |    9169000 |
| Zimbabwe                                     | Africa        |   11669000 |
+----------------------------------------------+---------------+------------+
239 rows in set (0.00 sec)

mysql> 

```

* Select countries and population of North America continent only

```

mysql> select Name,Population,Continent from country where Continent="North America";

```

```

+----------------------------------+------------+---------------+
| Name                             | Population | Continent     |
+----------------------------------+------------+---------------+
| Aruba                            |     103000 | North America |
| Anguilla                         |       8000 | North America |
| Netherlands Antilles             |     217000 | North America |
| Antigua and Barbuda              |      68000 | North America |
| Bahamas                          |     307000 | North America |
-----
| Saint Pierre and Miquelon        |       7000 | North America |
| Turks and Caicos Islands         |      17000 | North America |
| Trinidad and Tobago              |    1295000 | North America |
| United States                    |  278357000 | North America |
| Saint Vincent and the Grenadines |     114000 | North America |
| Virgin Islands, British          |      21000 | North America |
| Virgin Islands, U.S.             |      93000 | North America |
+----------------------------------+------------+---------------+
37 rows in set (0.00 sec)

```

* Select countries where population is less than 10000. Print Country name, population and continent

```
mysql> select Name,Population,Continent from country where Population < 10000;

```

```
+----------------------------------------------+------------+---------------+
| Name                                         | Population | Continent     |
+----------------------------------------------+------------+---------------+
| Anguilla                                     |       8000 | North America |
| Antarctica                                   |          0 | Antarctica    |
| French Southern territories                  |          0 | Antarctica    |
| Bouvet Island                                |          0 | Antarctica    |
| Cocos (Keeling) Islands                      |        600 | Oceania       |
| Christmas Island                             |       2500 | Oceania       |
| Falkland Islands                             |       2000 | South America |
| Heard Island and McDonald Islands            |          0 | Antarctica    |
| British Indian Ocean Territory               |          0 | Africa        |
| Norfolk Island                               |       2000 | Oceania       |
| Niue                                         |       2000 | Oceania       |
| Pitcairn                                     |         50 | Oceania       |
| South Georgia and the South Sandwich Islands |          0 | Antarctica    |
| Saint Helena                                 |       6000 | Africa        |
| Svalbard and Jan Mayen                       |       3200 | Europe        |
| Saint Pierre and Miquelon                    |       7000 | North America |
| Tokelau                                      |       2000 | Oceania       |
| United States Minor Outlying Islands         |          0 | Oceania       |
| Holy See (Vatican City State)                |       1000 | Europe        |
+----------------------------------------------+------------+---------------+
19 rows in set (0.00 sec)

```

* Select countries where population is between 1000 and 5000. Print Country name, population and continent

```

mysql> select Name, Population, Continent from country where Population BETWEEN 1000 and 5000;

```

```
+-------------------------------+------------+---------------+
| Name                          | Population | Continent     |
+-------------------------------+------------+---------------+
| Christmas Island              |       2500 | Oceania       |
| Falkland Islands              |       2000 | South America |
| Norfolk Island                |       2000 | Oceania       |
| Niue                          |       2000 | Oceania       |
| Svalbard and Jan Mayen        |       3200 | Europe        |
| Tokelau                       |       2000 | Oceania       |
| Holy See (Vatican City State) |       1000 | Europe        |
+-------------------------------+------------+---------------+
7 rows in set (0.00 sec)

```

* Select countries from North/South America continent 

```

mysql> select Name, Continent from country where Continent LIKE "%America%";

```

```
+----------------------------------+---------------+
| Name                             | Continent     |
+----------------------------------+---------------+
| Aruba                            | North America |
| Anguilla                         | North America |
| Netherlands Antilles             | North America |
| Argentina                        | South America |
| Antigua and Barbuda              | North America |
| Bahamas                          | North America |
| Belize                           | North America |
| Bermuda                          | North America |
| Bolivia                          | South America |
| Brazil                           | South America |
---
| Virgin Islands, British          | North America |
| Virgin Islands, U.S.             | North America |
+----------------------------------+---------------+
51 rows in set (0.00 sec)

```
