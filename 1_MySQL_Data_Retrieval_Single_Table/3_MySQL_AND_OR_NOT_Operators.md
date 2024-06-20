## MySQL:  AND, OR, NOT Operators

**Author: Abhishek Dey**

**Last modified: 20/06/2024**

## Examples: AND Operator

* Considering **country** table, select the countries from the African continent where population is less than 10 lacs 

```
mysql> select Name, Continent, Population from country where Continent="Africa" AND Population<1000000;

```

```
+--------------------------------+-----------+------------+
| Name                           | Continent | Population |
+--------------------------------+-----------+------------+
| Comoros                        | Africa    |     578000 |
| Cape Verde                     | Africa    |     428000 |
| Djibouti                       | Africa    |     638000 |
| Western Sahara                 | Africa    |     293000 |
| Equatorial Guinea              | Africa    |     453000 |
| British Indian Ocean Territory | Africa    |          0 |
| Mayotte                        | Africa    |     149000 |
| Réunion                        | Africa    |     699000 |
| Saint Helena                   | Africa    |       6000 |
| Sao Tome and Principe          | Africa    |     147000 |
| Seychelles                     | Africa    |      77000 |
+--------------------------------+-----------+------------+
11 rows in set (0.00 sec)

mysql> 

```

* Considering **city** table, select all information for Florida district of USA

```
mysql> select * from city where CountryCode="USA" AND District="Florida";

```

```
+------+------------------+-------------+----------+------------+
| ID   | Name             | CountryCode | District | Population |
+------+------------------+-------------+----------+------------+
| 3806 | Jacksonville     | USA         | Florida  |     735167 |
| 3839 | Miami            | USA         | Florida  |     362470 |
| 3849 | Tampa            | USA         | Florida  |     303447 |
| 3860 | Saint Petersburg | USA         | Florida  |     248232 |
| 3867 | Hialeah          | USA         | Florida  |     226419 |
| 3897 | Orlando          | USA         | Florida  |     185951 |
| 3923 | Fort Lauderdale  | USA         | Florida  |     152397 |
| 3928 | Tallahassee      | USA         | Florida  |     150624 |
| 3947 | Hollywood        | USA         | Florida  |     139357 |
| 3951 | Pembroke Pines   | USA         | Florida  |     137427 |
| 3982 | Coral Springs    | USA         | Florida  |     117549 |
| 4027 | Cape Coral       | USA         | Florida  |     102286 |
| 4038 | Clearwater       | USA         | Florida  |      99936 |
| 4042 | Miami Beach      | USA         | Florida  |      97855 |
| 4053 | Gainesville      | USA         | Florida  |      92291 |
+------+------------------+-------------+----------+------------+
15 rows in set (0.01 sec)

mysql> 

```

## Examples: OR Operator


* Considering **city** table, select all information for either Florida or Virginia districts

```
mysql> select * from city where  District="Florida" OR District="Virginia";

```

```
+------+------------------+-------------+----------+------------+
| ID   | Name             | CountryCode | District | Population |
+------+------------------+-------------+----------+------------+
| 3806 | Jacksonville     | USA         | Florida  |     735167 |
| 3830 | Virginia Beach   | USA         | Virginia |     425257 |
| 3839 | Miami            | USA         | Florida  |     362470 |
| 3849 | Tampa            | USA         | Florida  |     303447 |
| 3860 | Saint Petersburg | USA         | Florida  |     248232 |
| 3865 | Norfolk          | USA         | Virginia |     234403 |
| 3867 | Hialeah          | USA         | Florida  |     226419 |
| 3883 | Chesapeake       | USA         | Virginia |     199184 |
| 3887 | Richmond         | USA         | Virginia |     197790 |
| 3897 | Orlando          | USA         | Florida  |     185951 |
| 3905 | Newport News     | USA         | Virginia |     180150 |
| 3909 | Arlington        | USA         | Virginia |     174838 |
| 3923 | Fort Lauderdale  | USA         | Florida  |     152397 |
| 3928 | Tallahassee      | USA         | Florida  |     150624 |
| 3937 | Hampton          | USA         | Virginia |     146437 |
| 3947 | Hollywood        | USA         | Florida  |     139357 |
| 3951 | Pembroke Pines   | USA         | Florida  |     137427 |
| 3960 | Alexandria       | USA         | Virginia |     128283 |
| 3982 | Coral Springs    | USA         | Florida  |     117549 |
| 4027 | Cape Coral       | USA         | Florida  |     102286 |
| 4035 | Portsmouth       | USA         | Virginia |     100565 |
| 4038 | Clearwater       | USA         | Florida  |      99936 |
| 4042 | Miami Beach      | USA         | Florida  |      97855 |
| 4050 | Roanoke          | USA         | Virginia |      93357 |
| 4053 | Gainesville      | USA         | Florida  |      92291 |
+------+------------------+-------------+----------+------------+
25 rows in set (0.01 sec)

mysql> 

```

* Considering **countrylanguage** table, select the countries where German or Spanish language is spoken

```

mysql> select CountryCode, Language from countrylanguage where Language="German" OR Language="Spanish";

```

```
+-------------+----------+
| CountryCode | Language |
+-------------+----------+
| ABW         | Spanish  |
| AND         | Spanish  |
| ARG         | Spanish  |
| AUS         | German   |
| AUT         | German   |
| BEL         | German   |
| BLZ         | Spanish  |
| BOL         | Spanish  |
| BRA         | German   |
| CAN         | German   |
| CAN         | Spanish  |
| CHE         | German   |
| CHL         | Spanish  |
| COL         | Spanish  |
| CRI         | Spanish  |
| CUB         | Spanish  |
----
| URY         | Spanish  |
| USA         | German   |
| USA         | Spanish  |
| VEN         | Spanish  |
| VIR         | Spanish  |
+-------------+----------+
47 rows in set (0.00 sec)

mysql> 

```

## Examples: NOT Operator

* Considering **countrylanguage** table, select all entries where English language is not spoken

```

mysql> select CountryCode, Language from countrylanguage where NOT Language="English";

```

```
+-------------+---------------------------+
| CountryCode | Language                  |
+-------------+---------------------------+
| ABW         | Dutch                     |
| ABW         | Papiamento                |
| ABW         | Spanish                   |
| AFG         | Balochi                   |
| AFG         | Dari                      |
| AFG         | Pashto                    |
| AFG         | Turkmenian                |
------
| ZMB         | Nyanja                    |
| ZMB         | Tonga                     |
| ZWE         | Ndebele                   |
| ZWE         | Nyanja                    |
| ZWE         | Shona                     |
+-------------+---------------------------+
924 rows in set (0.00 sec)

```

### Examples: Combination of AND, OR, NOT Operators

* Considering **country** table, print country name where Year of independence is not null and Population > 100000000

```

mysql> select Name,IndepYear,Population from country where IndepYear is NOT NULL AND Population>100000000 ;

```

```
+--------------------+-----------+------------+
| Name               | IndepYear | Population |
+--------------------+-----------+------------+
| Bangladesh         |      1971 |  129155000 |
| Brazil             |      1822 |  170115000 |
| China              |     -1523 | 1277558000 |
| Indonesia          |      1945 |  212107000 |
| India              |      1947 | 1013662000 |
| Japan              |      -660 |  126714000 |
| Nigeria            |      1960 |  111506000 |
| Pakistan           |      1947 |  156483000 |
| Russian Federation |      1991 |  146934000 |
| United States      |      1776 |  278357000 |
+--------------------+-----------+------------+

```

* Considering **country** table, select countries from Caribbean and Middle East regions exclusing Iraq having Population < 50000000


```

mysql> select Name,Region,Population from country where Region="Caribbean" OR Region="Middle East"  AND Population < 50000000 AND NOT Name="Iraq" ;

```

```
+----------------------------------+-------------+------------+
| Name                             | Region      | Population |
+----------------------------------+-------------+------------+
| Aruba                            | Caribbean   |     103000 |
| Anguilla                         | Caribbean   |       8000 |
| Netherlands Antilles             | Caribbean   |     217000 |
| United Arab Emirates             | Middle East |    2441000 |
| Armenia                          | Middle East |    3520000 |
| Antigua and Barbuda              | Caribbean   |      68000 |
| Azerbaijan                       | Middle East |    7734000 |
| Bahrain                          | Middle East |     617000 |
| Bahamas                          | Caribbean   |     307000 |
| Barbados                         | Caribbean   |     270000 |
| Cuba                             | Caribbean   |   11201000 |
| Cayman Islands                   | Caribbean   |      38000 |
| Cyprus                           | Middle East |     754700 |
| Dominica                         | Caribbean   |      71000 |
| Dominican Republic               | Caribbean   |    8495000 |
| Georgia                          | Middle East |    4968000 |
| Guadeloupe                       | Caribbean   |     456000 |
| Grenada                          | Caribbean   |      94000 |
| Haiti                            | Caribbean   |    8222000 |
| Israel                           | Middle East |    6217000 |
| Jamaica                          | Caribbean   |    2583000 |
| Jordan                           | Middle East |    5083000 |
| Saint Kitts and Nevis            | Caribbean   |      38000 |
| Kuwait                           | Middle East |    1972000 |
| Lebanon                          | Middle East |    3282000 |
| Saint Lucia                      | Caribbean   |     154000 |
| Montserrat                       | Caribbean   |      11000 |
| Martinique                       | Caribbean   |     395000 |
| Oman                             | Middle East |    2542000 |
| Puerto Rico                      | Caribbean   |    3869000 |
| Palestine                        | Middle East |    3101000 |
| Qatar                            | Middle East |     599000 |
| Saudi Arabia                     | Middle East |   21607000 |
| Syria                            | Middle East |   16125000 |
| Turks and Caicos Islands         | Caribbean   |      17000 |
| Trinidad and Tobago              | Caribbean   |    1295000 |
| Saint Vincent and the Grenadines | Caribbean   |     114000 |
| Virgin Islands, British          | Caribbean   |      21000 |
| Virgin Islands, U.S.             | Caribbean   |      93000 |
| Yemen                            | Middle East |   18112000 |
+----------------------------------+-------------+------------+
40 rows in set (0.00 sec)

mysql> 

```

