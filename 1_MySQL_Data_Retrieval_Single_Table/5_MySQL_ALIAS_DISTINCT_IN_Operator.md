## MySQL:  Alias, Distinct and IN Operator


**Author: Abhishek Dey**

**Last modified: 21/06/2024**


## Defn:

* **Alias** is used as a short form or temporary name of a table field

* **Distint** is used to find the unique entries

* **IN** operator is used to specify selected values

## Examples: Alias

* Considering city table:

1. Display **Name, CountryCode and District** for 5 entries
    
    


```

mysql> select Name, CountryCode, District from city limit 5;

```

```
+----------------+-------------+---------------+
| Name           | CountryCode | District      |
+----------------+-------------+---------------+
| Kabul          | AFG         | Kabol         |
| Qandahar       | AFG         | Qandahar      |
| Herat          | AFG         | Herat         |
| Mazar-e-Sharif | AFG         | Balkh         |
| Amsterdam      | NLD         | Noord-Holland |
+----------------+-------------+---------------+
5 rows in set (0.00 sec)

mysql> 

```

2. Display **Name as Country**, **CountryCode as Code** and **District as Dist** for 5 entries

```

mysql> select Name as Country, CountryCode as Code, District as Dist from city limit 5;

```

```
+----------------+------+---------------+
| Country        | Code | Dist          |
+----------------+------+---------------+
| Kabul          | AFG  | Kabol         |
| Qandahar       | AFG  | Qandahar      |
| Herat          | AFG  | Herat         |
| Mazar-e-Sharif | AFG  | Balkh         |
| Amsterdam      | NLD  | Noord-Holland |
+----------------+------+---------------+
5 rows in set (0.00 sec)

```

## Examples: Disticnt

* Considering **country** table, print the unique **continent** names

```
mysql> select Distinct Continent from country;

```
```
+---------------+
| Continent     |
+---------------+
| North America |
| Asia          |
| Africa        |
| Europe        |
| South America |
| Oceania       |
| Antarctica    |
+---------------+
7 rows in set (0.00 sec)

mysql> 

```

* Considering **country** table, print the unique **Region** names

```
mysql> select Distinct Region from country;

```
```
+---------------------------+
| Region                    |
+---------------------------+
| Caribbean                 |
| Southern and Central Asia |
| Central Africa            |
| Southern Europe           |
| Middle East               |
| South America             |
| Polynesia                 |
| Antarctica                |
| Australia and New Zealand |
| Western Europe            |
| Eastern Africa            |
| Western Africa            |
| Eastern Europe            |
| Central America           |
| North America             |
| Southeast Asia            |
| Southern Africa           |
| Eastern Asia              |
| Nordic Countries          |
| Northern Africa           |
| Baltic Countries          |
| Melanesia                 |
| Micronesia                |
| British Islands           |
| Micronesia/Caribbean      |
+---------------------------+
25 rows in set (0.00 sec)

mysql> 

```

## Examples : IN Operator:


* Considering **country** table, Print the name of the countries which got independence in the following years : 1919, 1975, 1912, 1947,1971,1980

```
mysql> select Name,IndepYear from country where IndepYear in (1919, 1975, 1912, 1947,1971,1980) order by IndepYear;

```

```
+-----------------------+-----------+
| Name                  | IndepYear |
+-----------------------+-----------+
| Albania               |      1912 |
| Afghanistan           |      1919 |
| India                 |      1947 |
| Pakistan              |      1947 |
| United Arab Emirates  |      1971 |
| Bangladesh            |      1971 |
| Bahrain               |      1971 |
| Qatar                 |      1971 |
| Angola                |      1975 |
| Suriname              |      1975 |
| Sao Tome and Principe |      1975 |
| Papua New Guinea      |      1975 |
| Mozambique            |      1975 |
| Cape Verde            |      1975 |
| Comoros               |      1975 |
| Vanuatu               |      1980 |
| Zimbabwe              |      1980 |
+-----------------------+-----------+
17 rows in set (0.00 sec)

mysql> 

```

* Considering **country** table, print all the name of the countries from **'Middle East','Caribbean','Western Europe'** Regions which got independence between 1990 and 2000

```

mysql> select Name,Region,IndepYear from country where Region in ('Middle East','Caribbean','Western Europe') and IndepYear Between 1900 AND 2000 order by IndepYear;

```

```
+----------------------------------+----------------+-----------+
| Name                             | Region         | IndepYear |
+----------------------------------+----------------+-----------+
| Cuba                             | Caribbean      |      1902 |
| Yemen                            | Middle East    |      1918 |
| Austria                          | Western Europe |      1918 |
| Turkey                           | Middle East    |      1923 |
| Saudi Arabia                     | Middle East    |      1932 |
| Iraq                             | Middle East    |      1932 |
| Syria                            | Middle East    |      1941 |
| Lebanon                          | Middle East    |      1941 |
| Jordan                           | Middle East    |      1946 |
| Israel                           | Middle East    |      1948 |
| Oman                             | Middle East    |      1951 |
| Germany                          | Western Europe |      1955 |
| Cyprus                           | Middle East    |      1960 |
| Kuwait                           | Middle East    |      1961 |
| Trinidad and Tobago              | Caribbean      |      1962 |
| Jamaica                          | Caribbean      |      1962 |
| Barbados                         | Caribbean      |      1966 |
| United Arab Emirates             | Middle East    |      1971 |
| Bahrain                          | Middle East    |      1971 |
| Qatar                            | Middle East    |      1971 |
| Bahamas                          | Caribbean      |      1973 |
| Grenada                          | Caribbean      |      1974 |
| Dominica                         | Caribbean      |      1978 |
| Saint Lucia                      | Caribbean      |      1979 |
| Saint Vincent and the Grenadines | Caribbean      |      1979 |
| Antigua and Barbuda              | Caribbean      |      1981 |
| Saint Kitts and Nevis            | Caribbean      |      1983 |
| Azerbaijan                       | Middle East    |      1991 |
| Georgia                          | Middle East    |      1991 |
| Armenia                          | Middle East    |      1991 |
+----------------------------------+----------------+-----------+
30 rows in set (0.00 sec)

mysql> 

```
