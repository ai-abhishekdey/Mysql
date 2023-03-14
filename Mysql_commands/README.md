## Mysql commands:

**Author: Abhishek Dey**

**Last Modified: 14/03/2023**



### Login to mysql

* root user

```

mysql -u root -p

```

### Grant all permisions to non-root user

```

mysql> GRANT ALL PRIVILEGES ON * . * TO 'abhishek'@'localhost';


```


* Non-root user (abhishek)

```

mysql -u abhishek -p

```

### Show number of users: (Need to login in root mode)


```

mysql> select user from mysql.user;

```

```

+------------------+
| user             |
+------------------+
| abhishek         |
| debian-sys-maint |
| mysql.infoschema |
| mysql.session    |
| mysql.sys        |
| root             |
+------------------+
6 rows in set (0.00 sec)


```

### Show all existing databases:

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


### Creating a  new database (Eg. database name: calculator_database) 

```

mysql> create database calculator_database;

```

### Selecting a database (Eg. database name: calculator_database) 

```

mysql> use calculator_database;

```

### Show tables in the database in use:

```
mysql> show tables;

```

### Creating a table:


```

mysql> create table calculator_table (
    -> 
    -> sl_no int AUTO_INCREMENT,
    -> operation varchar(10),
    -> num1 float,
    -> num2 float,
    -> result float,
    -> PRIMARY KEY(sl_no)
    -> );
Query OK, 0 rows affected (0.65 sec)


```

### Check table properties:


```

mysql> describe calculator_table;

```

```

+-----------+-------------+------+-----+---------+----------------+
| Field     | Type        | Null | Key | Default | Extra          |
+-----------+-------------+------+-----+---------+----------------+
| sl_no     | int         | NO   | PRI | NULL    | auto_increment |
| operation | varchar(10) | YES  |     | NULL    |                |
| num1      | float       | YES  |     | NULL    |                |
| num2      | float       | YES  |     | NULL    |                |
| result    | float       | YES  |     | NULL    |                |
+-----------+-------------+------+-----+---------+----------------+
5 rows in set (0.03 sec)


```


### Insert data into table:


```

mysql> insert into calculator_table(sl_no,operation,num1,num2,result) values(1,'addition',10,20,30);

```

### Alter data type length varchar(10) to varchar(30):


```

mysql> alter table calculator_table change column operation operation varchar(30);

```

### Display the contents of the table:


```

mysql> select * from calculator_table;

```

```

+-------+----------------+------+------+--------+
| sl_no | operation      | num1 | num2 | result |
+-------+----------------+------+------+--------+
|     1 | addition       |   10 |   20 |     30 |
|     2 | division       |   40 |    5 |      8 |
|     3 | multiplication |   25 |    4 |    100 |
|     4 | substraction   |   38 |   10 |     28 |
|     5 | addition       |   27 |   20 |     47 |
|     6 | division       |   70 |   10 |      7 |
|     7 | substraction   |  520 |  300 |    220 |
|     8 | multiplication |   20 |   30 |    600 |
+-------+----------------+------+------+--------+
8 rows in set (0.00 sec)

```


### Display only selected columns from table:


```

mysql> select num1,num2,result  from calculator_table;

```


```

+------+------+--------+
| num1 | num2 | result |
+------+------+--------+
|   10 |   20 |     30 |
|   40 |    5 |      8 |
|   25 |    4 |    100 |
|   38 |   10 |     28 |
|   27 |   20 |     47 |
|   70 |   10 |      7 |
|  520 |  300 |    220 |
|   20 |   30 |    600 |
+------+------+--------+
8 rows in set (0.00 sec)


```


### Conditional queries: 

* select all entries from calculator table having addition opertation

```

mysql> select * from calculator_table where operation='addition';

```

```
+-------+-----------+------+------+--------+
| sl_no | operation | num1 | num2 | result |
+-------+-----------+------+------+--------+
|     1 | addition  |   10 |   20 |     30 |
|     5 | addition  |   27 |   20 |     47 |
+-------+-----------+------+------+--------+
2 rows in set (0.00 sec)


```

* select all entries from calculator table having result greater than equal to 50

```

mysql> select * from calculator_table where result >=50;

```

```

+-------+----------------+------+------+--------+
| sl_no | operation      | num1 | num2 | result |
+-------+----------------+------+------+--------+
|     3 | multiplication |   25 |    4 |    100 |
|     7 | substraction   |  520 |  300 |    220 |
|     8 | multiplication |   20 |   30 |    600 |
+-------+----------------+------+------+--------+
3 rows in set (0.00 sec)


```


### Update entries in a table:


```
mysql> update calculator_table set num1 = 30, num2 = 20 where sl_no = 8;

```


```

mysql> select * from calculator_table;
+-------+----------------+------+------+--------+
| sl_no | operation      | num1 | num2 | result |
+-------+----------------+------+------+--------+
|     1 | addition       |   10 |   20 |     30 |
|     2 | division       |   40 |    5 |      8 |
|     3 | multiplication |   25 |    4 |    100 |
|     4 | substraction   |   38 |   10 |     28 |
|     5 | addition       |   27 |   20 |     47 |
|     6 | division       |   70 |   10 |      7 |
|     7 | substraction   |  520 |  300 |    220 |
|     8 | multiplication |   30 |   20 |    600 |
+-------+----------------+------+------+--------+


```

### Delete a row from a table:


```

mysql> delete from calculator_table where sl_no=8;

```

```

mysql> select * from calculator_table;
+-------+----------------+------+------+--------+
| sl_no | operation      | num1 | num2 | result |
+-------+----------------+------+------+--------+
|     1 | addition       |   10 |   20 |     30 |
|     2 | division       |   40 |    5 |      8 |
|     3 | multiplication |   25 |    4 |    100 |
|     4 | substraction   |   38 |   10 |     28 |
|     5 | addition       |   27 |   20 |     47 |
|     6 | division       |   70 |   10 |      7 |
|     7 | substraction   |  520 |  300 |    220 |
+-------+----------------+------+------+--------+
7 rows in set (0.00 sec)


```
