### MySql installation in Ubuntu 22.04

---

### Installing MySQL-Server:

```
sudo apt update

sudo apt install mysql-server

sudo systemctl start mysql.service

```

### Creating NEW_USER: 

* Syntax:

```
mysql> create user 'user_name@'localhost' identified by 'user_password';

```
* Example:

```
mysql> create user 'abhishek'@'localhost' identified by 'abhi1234';

```

### Granting All Privileges to the user:

* Syntax:

```
mysql> grant all privileges on *.* to 'user_name@'localhost';

```
* Example:

```

mysql> grant all privileges on *.* to 'abhishek'@'localhost';

```

### Login with NEW_USER:

* Syntax:

```
mysql -u user_name -p

```
* Example:

```

mysql -u abhishek -p

```

### Installing MySQL-Workbench

## References:

1. https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-22-04
