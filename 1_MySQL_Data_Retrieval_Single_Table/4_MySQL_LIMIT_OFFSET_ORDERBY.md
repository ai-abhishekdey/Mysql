## MySQL:  LIMIT, OFFSET, ORDERBY


**Author: Abhishek Dey**

**Last modified: 20/06/2024**


## Defn:

* **LIMIT** clause is used to specify the number of records to return.

* **OFFSET** keyword is used to ignore the previous records and start from the next record

* **ORDER BY** keyword is used to sort the result-set in ascending or descending order. The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the **DESC** keyword.


## Examples: 

* Considering **city** table, display first 5 records;

```
mysql> select * from city ORDER BY ID limit 5;

```
```
+----+----------------+-------------+---------------+------------+
| ID | Name           | CountryCode | District      | Population |
+----+----------------+-------------+---------------+------------+
|  1 | Kabul          | AFG         | Kabol         |    1780000 |
|  2 | Qandahar       | AFG         | Qandahar      |     237500 |
|  3 | Herat          | AFG         | Herat         |     186800 |
|  4 | Mazar-e-Sharif | AFG         | Balkh         |     127800 |
|  5 | Amsterdam      | NLD         | Noord-Holland |     731200 |
+----+----------------+-------------+---------------+------------+
5 rows in set (0.00 sec)

```

* Considering **city** table, display last 5 records;

```
mysql> select * from city ORDER BY ID DESC limit 5;

```
```
+------+------------+-------------+------------+------------+
| ID   | Name       | CountryCode | District   | Population |
+------+------------+-------------+------------+------------+
| 4079 | Rafah      | PSE         | Rafah      |      92020 |
| 4078 | Nablus     | PSE         | Nablus     |     100231 |
| 4077 | Jabaliya   | PSE         | North Gaza |     113901 |
| 4076 | Hebron     | PSE         | Hebron     |     119401 |
| 4075 | Khan Yunis | PSE         | Khan Yunis |     123175 |
+------+------------+-------------+------------+------------+
5 rows in set (0.00 sec)

mysql> 

```

* Considering **city** table, display 5 records starting from ID=11;

```

mysql> select * from city ORDER BY ID limit 5 offset 10;

```

```
+----+-----------+-------------+---------------+------------+
| ID | Name      | CountryCode | District      | Population |
+----+-----------+-------------+---------------+------------+
| 11 | Groningen | NLD         | Groningen     |     172701 |
| 12 | Breda     | NLD         | Noord-Brabant |     160398 |
| 13 | Apeldoorn | NLD         | Gelderland    |     153491 |
| 14 | Nijmegen  | NLD         | Gelderland    |     152463 |
| 15 | Enschede  | NLD         | Overijssel    |     149544 |
+----+-----------+-------------+---------------+------------+
5 rows in set (0.00 sec)

mysql> 

```
