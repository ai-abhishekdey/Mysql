### MySql installation in Ubuntu 22.04

---

### Installing MySQL:

```
sudo apt update

sudo apt install mysql-server

sudo systemctl start mysql.service

```

### Configuring MySQL:

```
sudo mysql

mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

mysql> exit

sudo mysql_secure_installation

mysql -u root -p

mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH auth_socket;

```

### Creating a Dedicated MySQL User and Granting Privileges:

```

sudo mysql

mysql -u root -p

mysql> CREATE USER 'myuser'@'localhost' IDENTIFIED BY '*Mypassword1234#';

mysql> exit

```

### Login with non-root user:

```

mysql -u myuser -p

```

## References:

1. https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-22-04
