Install Mysql Server and MySQL Client in Ubuntu 16.04
======================================================

#### What is the difference between MySQL Server and MySQL Client?
<b>MySql Client :</b>
The mysql-client package allows you to connect to a MySQL server. It will give you the "mysql" command-line program.

<b>MySql Server :</b>
The mysql-server package allows to run a MySQL server which can host multiple databases and process queries on those databases.

#### Update Ubuntu
```
sudo apt update
```

#### Upgrade Ubuntu
```
sudo apt upgrade
```

#### Install MySQL Server
```
sudo apt install mysql-server
```

#### Enter root user password when asked

#### Install MySQL Client
```
sudo apt install mysql-client
```

#### Configure MySQL
```
mysql_secure_installation
```

#### Test MySQL service
```
systemctl status mysql.service
```

#### Test connecting to database
```
mysqladmin -p -u root version
```

#### Open Mysql Console
```
mysql -p -u root
```

#### In case the MySQL is not running, start it with
```
sudo systemctl start mysql
```

#### In case you need to restart MySQL, restart it with
```
sudo systemctl restart mysql
```

#### Create database in MySQL console
```
create database cp_intrafish;
```

#### Install `mysql-config`
```
sudo apt-get install libmysqlclient-dev
```

#### Load Database dump to the newly created database. Here `cp_intrafish` is the database name and `myifm_dump.sql` is the SQL dump file.
```
mysql -p -u root cp_intrafish<myifm_dump.sql
```

#### Pretty output in MySQL console. Add `\G` at the end of your command. This will change the output just for that command, without changing the default output. 
```
SELECT * FROM product_price\G;
```